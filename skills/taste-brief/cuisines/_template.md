# <Cuisine> — profile

## Traditions (never treat the country as one cuisine)
| Tradition | Signature dishes | Flavor signature | Native defaults | Staple carb |
|---|---|---|---|---|

**Native defaults** = the dish **as cooked at home**, in the form `heat N (side: X) · sweet · sour · rich`:
- **heat** 0–10 on the taste-brief ladder. It means the plate, not the hottest condiment; table or side heat goes in `(side: …)`.
- **sweet / sour / rich** each take one of `none · low · med · high`.
- If one tradition's dishes span more than 3 heat points, split the row (e.g., Chettinad meat vs Tamil tiffin).
- These are what a brief uses when the eater says nothing. The agent never exceeds them unless the eater asks.

## Hard-filter terms (mandatory)
Dietary and religious terms that must never be inferred, and confusions that cause harm, for example: pork-free ≠ halal; ghee/butter in "veg" or fasting (tsom) dishes; Jain (no root vegetables); fish sauce or shrimp paste in "vegetarian"; dishes containing meats many eaters don't expect (gloss them). How to ask for each in the cook's language.

## Home vs restaurant fidelity markers
Dishes whose restaurant/export version differs from the home version, and how. These become `must:` constraints and chef-note content. **State the home baseline before the change.** If a dish is sweet or rich at home, ask for "less", never "none".
- **<dish>**: home = ...; restaurant/export = ...
- If one dish name covers two different preparations (across regions or countries), split it and say "name which".

## Export drift (generic; no named markets)
How kitchens cooking for outsiders typically alter this cuisine (sweeter, milder, creamier). Name a market here and it belongs in `kitchen-scout/markets/<market>.md` instead.

## Insider vocabulary (for chef notes)
**Language routing:** pick the cook's language from the kitchen's provenance, not from the cuisine label. One lingua franca must not stand in for several languages. Fallback: English plus dish names. Sensitive pairs, where the wrong language offends: Tamil/Hindi, Uyghur/Mandarin, Tigrinya/Amharic, Kurdish/Turkish, Lao/Thai, Ukrainian/Russian.

**Rows are complete polite requests**, not fragments. The romanization must match the script.

**Address default:** no address term, or "Hi Chef / kitchen team", or the language's plural or neutral form. Use gendered or familial terms only when the cook's gender is known. Never use a term that marks the cook as junior.

| Intent | Language | Native phrase | Script | Notes |
|---|---|---|---|---|
| as it's normally made at home (native level) | | | | |
| a bit hotter than usual (only on the eater's word) | | | | |
| less sweet (dishes sweet at home) | | | | |
| no sugar (dishes not sweet at home) | | | | |
| dry / no gravy | | | | |
| polite opener (neutral) | | | | register caveats |

## Meal composition norms
Typical ratio of mains : carbs : sides/condiments per person; what's always on the table.

## In-culture tells (market-agnostic)
Signals that hold anywhere: native-language menu or reviews, identity dishes and ingredients. Who runs these kitchens in a specific market, and where the hubs are, goes in `kitchen-scout/markets/`.
