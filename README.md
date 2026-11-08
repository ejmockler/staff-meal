# staff meal

**Your agent orders what the cooks eat. Yes, including home spicy.**

Most restaurants keep two versions of a dish: the one adjusted for local customers, and the one people who grew up eating it would recognize. Staff meal is a set of agent skills that gets you the second one, whether that means spicier, milder, less sweet, more sour, or just cooked the way it's cooked at home. Heat is calibrated to the dish's native level by default; ask for more and it says so in the cook's language.

## Skills

| Skill | What it does |
|---|---|
| `staff-meal` | The whole flow: brief → kitchen → meal → notes → your confirmation → order. |
| `taste-brief` | Turns "real Indian" or "something spicy like back home" into a precise spec: regional tradition, anchor dishes and their home preparation, calibrated heat and sweetness. 24 cuisine profiles. |
| `kitchen-scout` | Finds the kitchen most likely to cook it right: delivery and hard filters first, then who actually runs the kitchen and whether each dish matches its home version. Market files for the US, Canada, Europe, Japan, Korea, India, the Gulf, Latin America and more. |
| `chef-notes` | Writes per-item kitchen notes in the counter language and the cook's own language, as one person texting the kitchen, not repeated boilerplate. |

## Where it knows the food

24 cuisines × 12 markets. Each cell answers one question: if you order this cuisine here, who's likely cooking it?

🏠 home turf  ·  🟢 in-culture kitchens are easy to find  ·  🟠 **the usual place under that sign is a stand-in**; the skill knows who's really cooking and what to order instead  ·  ⚪ thin  ·  blank: not mapped yet (the skill still works from first principles)

| | [🇺🇸](skills/kitchen-scout/markets/us.md)<br><sub>US</sub> | [🇨🇦](skills/kitchen-scout/markets/canada.md)<br><sub>CA</sub> | [🇬🇧](skills/kitchen-scout/markets/uk.md)<br><sub>UK</sub> | [🇪🇺](skills/kitchen-scout/markets/europe.md)<br><sub>EU</sub> | [🇯🇵](skills/kitchen-scout/markets/japan.md)<br><sub>JP</sub> | [🇰🇷](skills/kitchen-scout/markets/south-korea.md)<br><sub>KR</sub> | [🇹🇼🇭🇰](skills/kitchen-scout/markets/taiwan-hongkong.md)<br><sub>TW·HK</sub> | [🇸🇬🇲🇾](skills/kitchen-scout/markets/singapore-malaysia.md)<br><sub>SG·MY</sub> | [🇮🇳](skills/kitchen-scout/markets/india.md)<br><sub>IN</sub> | [🇦🇪](skills/kitchen-scout/markets/gulf.md)<br><sub>Gulf</sub> | [🇦🇺🇳🇿](skills/kitchen-scout/markets/australia-nz.md)<br><sub>AU·NZ</sub> | [🌎](skills/kitchen-scout/markets/latin-america.md)<br><sub>LatAm</sub> |
|:--|:-:|:-:|:-:|:-:|:-:|:-:|:-:|:-:|:-:|:-:|:-:|:-:|
| <sub>**SOUTH ASIA**</sub> | | | | | | | | | | | | |
| [Indian](skills/taste-brief/cuisines/indian.md) | 🟠 | 🟢 | 🟠 | 🟠 | 🟠 | 🟠 | 🟠 | 🟢 | 🏠 | 🟢 | 🟢 | ⚪ |
| [Pakistani](skills/taste-brief/cuisines/pakistani.md) | 🟢 | 🟢 | 🟢 | 🟢 | 🟢 | 🟢 | 🟢 |   |   | 🟢 |   |   |
| [Bangladeshi](skills/taste-brief/cuisines/bangladeshi.md) | 🟢 | 🟢 | 🟢 |   | 🟢 |   |   | 🟢 |   | 🟢 |   |   |
| [Nepali](skills/taste-brief/cuisines/nepali.md) | 🟢 |   | 🟢 |   | 🟢 | 🟢 | 🟢 | 🟢 | 🟢 | 🟢 | 🟢 |   |
| [Sri Lankan](skills/taste-brief/cuisines/sri-lankan.md) |   | 🟢 | 🟢 |   | 🟢 | 🟢 |   |   |   | 🟢 | 🟢 |   |
| <sub>**EAST ASIA**</sub> | | | | | | | | | | | | |
| [Chinese](skills/taste-brief/cuisines/chinese.md) | 🟠 | 🟢 | 🟠 |   | 🟢 | 🟢 | 🏠 | 🟢 | 🟠 | 🟢 | 🟢 | 🟠 |
| [Japanese](skills/taste-brief/cuisines/japanese.md) | 🟠 | 🟠 | 🟠 | 🟠 | 🏠 |   | 🟢 | 🟢 | 🟠 | 🟠 |   | 🟠 |
| [Korean](skills/taste-brief/cuisines/korean.md) | 🟢 | 🟢 | 🟢 | 🟢 | 🟢 | 🏠 | 🟢 | 🟢 | 🟠 | 🟠 | 🟢 | 🟢 |
| <sub>**SOUTHEAST ASIA**</sub> | | | | | | | | | | | | |
| [Thai](skills/taste-brief/cuisines/thai.md) | 🟢 | ⚪ | 🟢 | 🟠 | 🟢 | 🟠 | 🟠 | 🟢 |   | 🟠 | 🟢 |   |
| [Vietnamese](skills/taste-brief/cuisines/vietnamese.md) | 🟢 | 🟢 | 🟢 | 🟢 | 🟢 | 🟢 | 🟢 | 🟢 |   |   | 🟢 |   |
| [Indonesian · Malaysian](skills/taste-brief/cuisines/indonesian-malaysian.md) | ⚪ |   | 🟢 | 🟢 | 🟢 | 🟢 | 🟢 | 🏠 |   | 🟢 | 🟢 |   |
| [Filipino](skills/taste-brief/cuisines/filipino.md) | 🟢 | 🟢 | 🟢 |   |   | 🟢 | 🟢 | 🟢 |   | 🟢 | 🟢 |   |
| <sub>**MIDDLE EAST · NORTH AFRICA**</sub> | | | | | | | | | | | | |
| [Levantine · Arab](skills/taste-brief/cuisines/levantine-arab.md) | 🟢 |   | 🟢 | 🟢 |   | 🟢 | ⚪ |   | 🟢 | 🏠 | 🟢 | 🟢 |
| [Turkish](skills/taste-brief/cuisines/turkish.md) |   |   | 🟢 | 🟠 | 🟢 | 🟢 | ⚪ |   |   |   | 🟢 |   |
| [Persian](skills/taste-brief/cuisines/persian.md) | 🟢 | 🟢 | 🟢 | 🟢 | ⚪ | ⚪ |   |   |   | 🟢 |   |   |
| [Maghrebi](skills/taste-brief/cuisines/maghrebi.md) |   |   |   | 🟢 |   |   |   |   |   |   |   |   |
| <sub>**AFRICA**</sub> | | | | | | | | | | | | |
| [Ethiopian · Eritrean](skills/taste-brief/cuisines/ethiopian-eritrean.md) | 🟢 | 🟢 | 🟢 |   | ⚪ | ⚪ | ⚪ | ⚪ |   | 🟢 | 🟢 | ⚪ |
| [West African](skills/taste-brief/cuisines/west-african.md) | 🟢 |   | 🟢 | 🟢 | ⚪ | ⚪ | ⚪ | ⚪ |   |   | ⚪ | ⚪ |
| <sub>**AMERICAS**</sub> | | | | | | | | | | | | |
| [Mexican](skills/taste-brief/cuisines/mexican.md) | 🟢 | ⚪ | ⚪ | ⚪ | 🟠 | 🟠 | ⚪ | ⚪ | 🟠 | 🟠 | ⚪ | 🏠 |
| [Central American](skills/taste-brief/cuisines/central-american.md) | 🟢 |   |   |   |   |   |   |   |   |   |   | 🏠 |
| [Peruvian](skills/taste-brief/cuisines/peruvian.md) | 🟢 |   | 🟢 | 🟢 | 🟢 | ⚪ | ⚪ |   |   |   |   | 🏠 |
| [Caribbean](skills/taste-brief/cuisines/caribbean.md) | 🟢 | 🟢 | 🟢 | 🟢 | ⚪ | ⚪ |   | ⚪ |   |   | ⚪ |   |
| <sub>**EUROPE**</sub> | | | | | | | | | | | | |
| [Italian](skills/taste-brief/cuisines/italian.md) | 🟠 |   |   | 🏠 | 🟢 | 🟠 |   | 🟠 | 🟠 | 🟠 | 🟢 |   |
| [Greek](skills/taste-brief/cuisines/greek.md) |   | 🟢 |   | 🏠 |   |   |   |   |   |   | 🟢 |   |

### The sign isn't the cook

- 🇯🇵 🇰🇷 **"Indian" is mostly Nepali-run.** Skip the sweet naan set; order dal bhat and momo.
- 🇬🇧 **The curry house is usually Bangladeshi (Sylheti).** The kitchen note goes in Bangla, and the "Bangladeshi specials" section is the real food.
- 🇫🇷 🇮🇹 **"Japanese" sushi is usually Chinese-run.** The Japanese-run places cluster in a few streets, and the skill knows which.
- 🇩🇪 **"Asia / Thai" is very often Vietnamese-run.** Order phở or bún bò Huế from the Vietnamese section.
- 🇵🇪 **"Chinese" is chifa**, and 🇮🇳 **"Chinese" is Indo-Chinese.** Both are cuisines in their own right; the skill judges them as that, not as Cantonese.

Click a flag for that market's full map (sign → who's cooking → what to order), or a cuisine for its regional traditions, home-vs-export tells and kitchen vocabulary.

## Install

Four plain-markdown skills in the open [Agent Skills](https://agentskills.io) format (`skills/<name>/SKILL.md`), so they work in any agent that loads skills. Install all four: they reference each other by name and by sibling path.

**Any agent** (Claude Code, Codex, Cursor, OpenCode, and others) via the [`skills`](https://github.com/vercel-labs/skills) CLI:
```
npx skills add ejmockler/staff-meal
```

**Claude Code** plugin:
```
/plugin marketplace add ejmockler/staff-meal
/plugin install staff-meal@staff-meal
```

**Gemini CLI:**
```
for s in staff-meal taste-brief kitchen-scout chef-notes; do
  gemini skills install https://github.com/ejmockler/staff-meal --path skills/$s
done
```

**Anything else:** copy or symlink `skills/*` into your agent's skills folder (for Codex, `~/.agents/skills/`).

Then: "order me real Isan food", or "what should we eat tonight?"

### What your agent needs
- **To suggest a meal and write the notes:** nothing extra. `taste-brief` and `chef-notes` work in any chat; paste the notes into the app yourself.
- **To scout kitchens and place the order:** a tool that drives your own logged-in browser (Claude in Chrome, a built-in browser pane, or a Playwright MCP server), plus web search for checking who runs a kitchen.

## Safety

- Nothing is ordered until you confirm the item list and total.
- Only a payment method already saved on the platform is used; the agent never enters card details or passwords.
- A note is a request, not a guarantee. For serious allergies you must confirm ingredients and cross-contact with the restaurant yourself.

## Status

Native-language lines have not all been checked by native speakers.
