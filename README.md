# staff meal

**Your agent orders what the cooks eat. Yes, including home spicy.**

Most restaurants keep two versions of a dish: the one adjusted for local customers, and the one people who grew up eating it would recognize. Staff meal is a set of Claude Code skills that gets you the second one, whether that means spicier, milder, less sweet, more sour, or just cooked the way it's cooked at home. Heat is calibrated to the dish's native level by default; ask for more and it says so in the cook's language.

## Skills

| Skill | What it does |
|---|---|
| `staff-meal` | The whole flow: brief → kitchen → meal → notes → your confirmation → order. |
| `taste-brief` | Turns "real Indian" or "something spicy like back home" into a precise spec: regional tradition, anchor dishes and their home preparation, calibrated heat and sweetness. 24 cuisine profiles. |
| `kitchen-scout` | Finds the kitchen most likely to cook it right: delivery and hard filters first, then who actually runs the kitchen and whether each dish matches its home version. Market files for the US, Canada, Europe, Japan, Korea, India, the Gulf, Latin America and more. |
| `chef-notes` | Writes per-item kitchen notes in the counter language and the cook's own language, as one person texting the kitchen, not repeated boilerplate. |

## Install

```
/plugin marketplace add ejmockler/staff-meal
/plugin install staff-meal@staff-meal
```

Then: "order me real Isan food", or "what should we eat tonight?"

## Safety

- Nothing is ordered until you confirm the item list and total.
- Only a payment method already saved on the platform is used; the agent never enters card details or passwords.
- A note is a request, not a guarantee. For serious allergies you must confirm ingredients and cross-contact with the restaurant yourself.

## Status

Early. Ordering is driven in your own browser (Claude in Chrome). Uber Eats is exercised end to end; Swiggy, Zomato and DoorDash notes are partly observed. Native-language lines have not all been checked by native speakers, and no note has been tested for kitchen compliance.
