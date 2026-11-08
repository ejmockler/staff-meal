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
