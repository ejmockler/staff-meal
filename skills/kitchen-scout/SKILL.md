---
name: kitchen-scout
description: Find the delivery kitchen most likely to cook a Taste Brief faithfully. It applies hard filters first (delivers to this address, open now, orderable, membership perks), then checks who actually runs the kitchen (provenance OSINT), whether it matches the regional tradition, and whether each anchor dish's menu description matches its home version. Use after taste-brief, or whenever someone asks for "the best/most authentic X near me" on any delivery app, driven in the user's browser (field notes exist for Uber Eats). For an end-to-end order, staff-meal calls this as a stage.
---

# Kitchen Scout

Input: a Taste Brief (from `taste-brief`). Output: a ranked shortlist of 1–3 kitchens with evidence, plus a dish map for the winner.

Rank by **"will this kitchen cook the brief?"**, not by "is this kitchen X-run?". Provenance is evidence. It is not the goal: an Indian-owned Punjabi kitchen is still the wrong answer for a Maharashtrian brief if a Maharashtrian kitchen delivers.

## Pipeline (in this order; never research a kitchen you haven't hard-filtered)

### 1. Hard filters (cheap, eliminating). Do these FIRST.
- **Delivers to the brief's address right now.** Check it on the platform for the actual address, not the city. Doing this last wastes the whole research effort; it happened with a Maharashtrian kitchen 15 km away.
- `isOrderable` / open now, or open in the scheduled window.
- Membership: verify it's actually active (Uber One / DashPass). Don't assume it from what the user says. Note which stores get the $0-fee or promo perks.
- Dietary hard constraints (halal, veg-only kitchen, Jain).

### 2. Candidate generation
Search with native-language and regional terms, not only the cuisine name:
- the regional name (e.g. "Maharashtrian", "Isan", "Oaxaqueño")
- 2–3 anchor dishes (e.g. "misal", "som tam", "tlayuda") — a dish search finds specialists a cuisine search buries
- the local-language term (e.g. 南インド, イサーン, メキシカン タコス)

### 3. Provenance OSINT (per surviving candidate, about 5 min each)
Strong signals:
- the owner or chef's name and origin, from press, the company registry, or "about us"
- reviews written in the cuisine's language, praising home-likeness ("ghar jaisa", "como en casa", "เหมือนที่บ้าน")
- community ties: embassy caterer, temple or mosque events, diaspora groups, halal certifier
- regional dishes on the menu that a generic kitchen wouldn't bother with

Weak or negative signals:
- a menu of the standard export greatest hits
- the market's proxy-cuisine tells (see `markets/<market>.md`)

**Flip the proxy.** "Proxy" is relative to the brief. A kitchen eliminated as a stand-in for cuisine A is often the *in-culture* kitchen for cuisine B (a Nepali-run "Indian" shop for a Nepali brief; a Tamil-run "Indien" for Sri Lankan; a Pakistani-run "Indian" for karahi). Before eliminating, ask: whose home food could this kitchen cook? The market file's `Proxy flips` section lists known cases.
- a sibling-brand chain under several names with the same address (ghost kitchen)

### 4. Regional match
Score how well the kitchen's tradition matches the brief: exact match > neighboring tradition with the same heat or technique (e.g., Chettinad/Andhra for a Maharashtrian chili brief) > generic pan-cuisine.

### 5. Dish-fidelity read
For each anchor dish, read the menu **description**, not just the name. Flag a mismatch with the `home_version` (e.g., "Paneer Bhurji — cooked in rich gravy" vs a `must: [dry]` brief). Classify each one:
- ✅ matches
- 🛠 likely fixable with a chef note (simple changes at the pass: gravy→dry, sauce on the side, more chili; less sugar only if it isn't already in a pre-made base). A note is a request, not a guarantee: for a `must:` item, prefer a ✅ item or an app option, and tell the user when a must rests on a note.
- ❌ structurally different (a different dish under the same name). Choose a substitute or another kitchen.

### 6. Rank and report
```
1. <Kitchen> — ★4.7 (1,000+) · ETA 35–50 min · fee ¥300 · Uber One ✔ · promo: ¥1,500 off ≥¥10,000
   Provenance: Indian owner (press: ...), Hindi reviews "ghar jaisa"
   Regional: Punjabi/North (neighbor to brief; heat achievable via notes)
   Dishes: paneer bhurji 🛠 (menu says gravy → note: dry) · misal ❌ not on menu → sub: Chicken 65 ✅ dry-hot
   Risk: naan follows the local palate vector by default → note
2. ...
Eliminated: <Kitchen> (doesn't deliver to address), <Kitchen> (export greatest-hits menu, no regional dishes; would suit a Nepali brief)
```
Show the eliminated list. It tells the user the search was real.

## References
- `markets/INDEX.md` routes the delivery address to ONE market file (palate vector, counter/line languages, platforms, proxy map, flips, gaps). Read only that file. No file for the market? Follow the INDEX's derive-a-market procedure and say so. Market files are leads, not facts: verify per kitchen.
- `platforms/_browser.md` is the app-agnostic browser loop (always read it). `platforms/<app>.md` holds optional field notes on one app's quirks. The live page beats the notes.
- Field notes so far: `platforms/ubereats.md` (from real runs); `platforms/doordash.md` (DoorDash web; Wolt/Deliveroo ownership and footprint) and `platforms/swiggy-zomato.md` (India; veg/non-veg/egg markers as a hard filter), both research-based and not yet run. App-only platforms: see `_browser.md`.
