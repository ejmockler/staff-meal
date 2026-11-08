---
name: taste-brief
description: Turn a vague food desire ("real Indian", "authentic Mexican", "something spicy like back home", "what should I eat tonight") into a precise, machine-usable Taste Brief — regional cuisine, anchor dishes with their HOME preparation, calibrated heat/sweetness, adaptation tolerance, headcount, carbs, budget. Use standalone for meal suggestions without ordering; for an actual order, staff-meal calls it as its first stage. Also use whenever someone says "authentic", "real", "like home", "how locals eat it", or can't name dishes. Works for diaspora eaters dialing in home food AND for Americans (or anyone) exploring a cuisine they don't have vocabulary for.
---

# Taste Brief

The single biggest failure mode in food ordering is optimizing a **proxy** ("is the kitchen Indian?") instead of the **target** ("does this taste like what this eater means?"). A cuisine name is not a spec. This skill produces the spec.

Output: a Taste Brief (schema below), written to the conversation. `staff-meal` calls this skill first; `kitchen-scout` and `chef-notes` consume the brief.

## Step 1 — Classify the eater (silently, from what they said)

| Mode | Signal | What precision means |
|---|---|---|
| **Homecoming** | "like back home", "real", "cooked by X people", names dishes in native terms | Match a specific regional HOME preparation. Zero adaptation tolerance by default. |
| **Explorer** | "authentic", "how locals eat it", "I want to try real X" — often an American | Pick ONE regional tradition and commit; deliver the dish as its home audience eats it, with heat calibrated to what this eater can actually enjoy. |
| **Craving** | "something spicy", "comfort food", "I don't know, surprise me" | Map the craving to 2–3 candidate cuisines/dishes, then proceed as Explorer. |

## Step 2 — Elicit in ONE batch (max 4 questions in one message; use the client's multiple-choice question tool if it has one)

Only ask what you can't infer. Priority order:

1. **Which tradition?** Never accept a country as a region. "Indian" → Punjabi? Maharashtrian? Kerala? Hyderabadi? Offer the 3–4 most likely from `cuisines/<cuisine>.md` plus "not sure — pick for me". For Explorers, never ask "which tradition?" bare: offer them as experiences ("Oaxaca: smoky moles, tlayudas" vs "Yucatán: citrus-achiote pork, habanero").
2. **Anchor dishes + how they're made at home.** "Which 1–3 dishes would make this a win? Anything about how they should be made (dry vs gravy, corn vs flour, sticky rice)?" The home preparation is the spec; the menu name is not.
3. **Heat & sweetness**: ask only if the eater hasn't signaled it. The default answer is "as it's normally eaten" (native). Use the anchor ladder below to translate any stated tolerance, never a bare 1–10.
4. **Headcount, budget, timing** (delivery vs pickup, now vs scheduled).

**Always ask about allergies and hard dietary rules** (fold it into question 4 if needed). Never infer them from the cuisine or the person (halal, vegetarian, Jain). Record them in `dietary:` as confirmed, not assumed.

Also check memory for this person's prior taste briefs; reuse instead of re-asking.

## Calibration principle: native default, not maximum
The target for every flavor axis (heat, sweetness, sourness, salt, oil, richness, funk) is **what's usual for that dish in its home tradition**, as taken from the cuisine profile. "Authentic" means *un-adapted for the local market*. It does **not** mean hotter, less sweet or more intense.
- **No stated preference → `native`.** Don't add heat or strip sugar on the eater's behalf. A dish that is sweet at home (Gujarati dal, Shanghai hong shao rou, Thai palm-sugar curries, mole, Persian sweet-sour stews) stays sweet. A dish that is mild at home (korma, Cantonese, Persian chelo kabab, Japanese) stays mild.
- **Correct only the local drift.** If the market's palate vector pushes a dish milder, sweeter or creamier than its home version, the note restores the native level. That is the main job of the notes.
- **Deviate only on the eater's explicit word** ("make it hotter than usual", "I can't do much heat", "less sweet"). Record it as `level: <n> (user)`.
- **Explorers with low tolerance:** pick dishes whose *native* level fits them, rather than asking a kitchen to tone down a dish that's meant to be hot. Say so ("som tam is natively hot; try gai yang + sticky rice, or ask phet nit noi, a level Thais order too").
- **Explorers with high tolerance:** native is still the default. Offer native-hot dishes, and don't push a mild dish past its home level.

## Heat calibration ladder (American anchors → global)

Ask "which of these is *enjoyable*, not survivable?":

| Level | US anchor | Global equivalent |
|---|---|---|
| 0 | ketchup / no heat | — |
| 2 | Taco Bell mild, black pepper | Japanese "amakuchi" curry |
| 4 | jalapeño, Sriracha, Buffalo medium | many restaurants' "medium" (not all: Japanese 中辛 is about 2) |
| 6 | fresh serrano salsa, Buffalo hot, Nashville medium | Punjabi home cooking, Sichuan mala (moderate) |
| 8 | habanero salsa, Nashville hot | Kolhapuri / Chettinad / Isan som tam "phet" / Yucatecan habanero / southern Thai dry curries |
| 10 | ghost-pepper wings, "Thai hot" as Thais order it | Andhra/Guntur-hot |

Record both the number AND the anchor phrase. The anchor is what goes in the chef note. With no stated preference, record `heat: native` and let the profile's per-tradition default fill in the number `(inferred)`.

## Decode "authentic" (it means one of these — find out which)

- **Regional**: as made in a specific place (most common real meaning)
- **Home vs restaurant vs street**: e.g., Indian *home* bhurji is dry; Indian *restaurant* paneer dishes are creamy gravies
- **Un-adapted**: not toned down for the LOCAL market's palate (sweeter, milder, creamier, bigger) — see `kitchen-scout/markets/`
- **Provenance**: cooked by people from that culture (a filter, not the goal)

## Taste Brief schema

```yaml
eater_mode: homecoming | explorer | craving
eater_context: "Maharashtrian, grew up on home food in Pune"   # or "American, Tex-Mex fan, first time with Oaxacan"
cuisine: Indian
tradition: Maharashtrian            # region / sub-tradition; never just the country
anchor_dishes:
  - name: paneer bhurji
    home_version: "DRY scramble — onion, tomato, green chili, haldi; no gravy, no cream"
    must: [dry]
  - name: misal pav
    home_version: "spicy matki usal + kat/tarri, farsan, pav"
    optional: true
acceptable_substitutes: ["dry, chili-forward dishes from any Indian region"]
heat: {level: 8 (user), anchor: "Kolhapuri-level teekha"}   # this eater asked for it; default is native
sweetness: none (user)              # native (default) | less | none | fine. 'none' only on the eater's word
adaptation_tolerance: zero          # zero | light | welcome
avoid:
  - "local-market adaptations: sweet/oversized naan, sugar in gravies"
  - "proxy kitchens per kitchen-scout/markets/<market>.md, unless explicitly fine"
diners: 2
carbs: {per_person: "2-3 breads or 1 rice", preferred: [tandoori roti, tandoor naan]}
dietary: []
budget: "~¥10,000 total"
logistics: {mode: delivery, when: now, address: "<saved address label>"}
```

Fields the eater didn't specify: fill from the cuisine profile's defaults and mark `(inferred)` so the confirmation step can surface them.

## Cuisine profiles

`cuisines/` holds per-cuisine knowledge: regional traditions, the dishes that define each, home-vs-restaurant fidelity markers, insider vocabulary for chef notes. Route via `cuisines/INDEX.md` (aliases → file) and read ONLY the matched profile(s). To add a cuisine, copy `cuisines/_template.md` and add an INDEX row.

## Bridging for Explorers (meal *suggestions*)

When an eater can't name dishes, bridge from what they know: "If you like carne asada tacos → try cochinita pibil (Yucatán) or tlayuda (Oaxaca)". Suggest ONE coherent regional meal (mains + carb + condiment/side), not a sampler across regions; a cross-region sampler is how restaurants end up generic.
