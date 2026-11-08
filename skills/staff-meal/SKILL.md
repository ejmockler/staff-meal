---
name: staff-meal
description: End-to-end food ordering that gets you what the cooks would eat. It turns "order me real X" or "what should we eat tonight" into a placed delivery order that tastes the way the cuisine's home audience eats it. It chains taste-brief (precise spec), kitchen-scout (right kitchen, hard filters first), meal composition, promos, and chef-notes (multilingual per-item kitchen instructions), then confirms with the user before placing. Use for any food delivery or ordering request where authenticity, heat, regional style, or "not adjusted for locals" matters, or when an American (or anyone) wants an agent to suggest and order a meal from an unfamiliar cuisine precisely.
---

# Staff Meal (orchestrator)

This skill exists because one Tokyo Indian order took 9 corrections to converge. The pipeline below front-loads each of those corrections:

| Correction we had to make late | Stage that now catches it |
|---|---|
| "Indian" ≠ "Maharashtrian"; a Goan accent was taken to mean Goan cuisine | 1 Brief: tradition, never just the country; an accent is not a cuisine |
| The Kerala kitchen was a mismatch | 1 Brief + 2 Scout regional match |
| The best match didn't deliver | 2 Scout hard filters FIRST |
| Uber One was assumed, not verified | 2 Scout hard filters |
| The bhurji came in gravy | 2 Scout dish-fidelity read → 4 notes |
| "Do we have enough to eat this with?" | 3 Composition |
| Too much roti / naan swap / the naan must be legit | 3 Composition + 4 notes on the bread |
| Notes needed on every item | 4 Chef notes, per item |
| Checkout flipped to Priority | 5 Pre-flight |

## Stages

### 0. Setup
- Check memory for the user's saved taste briefs, addresses, platform, and past orders/misses. Reuse them.
- **Execution is an agent driving the user's own logged-in browser**, with whatever browser tool is available (Claude in Chrome, the built-in browser, Playwright). There are no platform adapters. Follow `kitchen-scout/platforms/_browser.md` for the loop, robustness rules, untrusted page content and spend guards. Open a new tab and decline non-essential cookies.

### 1. Brief → `taste-brief`
Produce the Taste Brief in ONE question batch (≤4 questions). Don't start searching until the tradition, the anchor dishes plus their home versions, the heat anchor and the headcount are known or explicitly inferred.

### 2. Scout → `kitchen-scout`
Hard filters → candidates → provenance → regional match → dish-fidelity. Present the ranked shortlist plus the eliminated list. For Explorers, let the user pick; for Homecoming, recommend one and move on unless they object.

### 3. Compose the meal
For the chosen kitchen, propose ONE coherent meal:
- **Mains**: about 1 per person + 1 to share. Cover the anchor dishes first; mix textures (dry + gravy, fried + fresh) per the cuisine's norms.
- **Carbs**: use the cuisine profile's ratio (Indian: 2–3 breads per person or 1 rice; tacos: 3–5 per person; Thai: rice per person, sticky rice for Isan). Split the breads between the daily base (roti) and the treat (naan) instead of maxing one.
- **Condiments/sides** that the home table always has (onion salad + green chutney, salsa + lime, raw veg with som tam).
- **Skip** dishes the kitchen is unlikely to execute well, based on fidelity ❌ or user distrust (e.g., "no faith in their dal makhani").
- **Promos**: if a store promo threshold is within about 15% of the subtotal, close the gap with something useful (an extra bread, a side), not filler.
Show it as a table: item · why · fidelity flag · qty · price.

### 4. Chef notes → `chef-notes`
Write a note for EVERY item, breads included, using the language stack and levers from the skill. Show the user the notes (with English lines) alongside the meal table.

### 5. Pre-flight and confirm (mandatory; the single source for order safety)
Before placing, re-read the checkout:
- delivery tier (Standard vs Priority), fees, promo applied, membership benefits actually showing
- address and ETA
- every item, its quantity and its note present
- the notes read top to bottom as one message in one voice: greeting once, thanks once, no repeated talk; each ticket read alone still states its own heat, sugar and dietary requirements
- serious allergy: the user has confirmed ingredients and cross-contact with the restaurant; otherwise drop the affected items

Then ask the user: **"Ready to place: <items> — subtotal, fees, tip, promo, total <amount> on <saved method> · <Standard/Priority> · to <address> · ETA <x>. Confirm?"** Place the order only on a clear yes. If anything changes after the yes (total, tier, item swapped, promo dropped), re-confirm. Never enter payment credentials; use only a saved method.

### 6. After
- Verify the notes on the confirmation page; report the order ID and ETA.
- Write memory: the brief, the kitchen, what was ordered, any default the kitchen got wrong (e.g., "DIYA bhurji defaults to gravy"), and later the user's verdict. Next time's brief starts there.

## Explorer mode (e.g., an American guiding the agent)
The user may only say "I want real Thai". The agent does the cultural work. Default to each dish's native level (see taste-brief, "Calibration principle"), and move away from it only on what the user states:
- If they state a tolerance, translate it (Buffalo hot → heat 6; habanero salsa → 8) with the ladder, and use it to *choose dishes* whose native level fits, before asking any kitchen to change a dish.
- Pick one regional tradition and explain why in a line ("Isan: grilled meats, sticky rice, lime-and-chili salads; natively hot" or "Central: curries balanced sweet-salty-sour, medium heat"). Don't pick the hottest tradition by default.
- Suggest a 3–4 dish meal with a one-line "what it's like" bridge for each ("larb: a warm, limey minced-pork salad, think a carnitas lettuce wrap with toasted rice crunch").
- Chef notes do the rest. The English line says what they want; the native line asks for the home version in the kitchen's own words (without claiming the user is from the culture).

## Failure modes to avoid
- Optimizing a proxy (owner nationality, star rating) instead of the brief
- Researching kitchens before the delivery check
- Accepting the menu name as the dish spec
- One order-level note when the platform has per-item notes
- Asking questions one at a time across many turns
- Placing the order without the final confirm
