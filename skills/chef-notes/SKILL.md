---
name: chef-notes
description: Write per-item kitchen instructions (special-instructions notes) that get a dish cooked the way its home audience eats it. Each note carries its own dish's levers plus a two-word restatement of any shared requirement, so every ticket works alone, and the set reads as one person texting the kitchen, in the voice someone from that food culture would type on their phone, never as repeated boilerplate. The notes are multilingual (the cook's language, the local counter language, English), use the right register and insider vocabulary, and name only concrete levers the line can pull (chili quantity, dry vs gravy, no sugar, char, garnish, sauce on the side). Called by staff-meal for a full order; use standalone whenever adding notes to a food delivery or restaurant order, or when someone says "tell them to make it spicy / real / like home / not adjusted for locals".
---

# Chef Notes

A delivery note gets a glance of a few seconds (an estimate, not a measurement) from a busy person at the pass, often not the cook. Tickets can print separately per station, so each one must work alone. It works when it:
1. **Gets read.** It's short, in the language of whoever reads the ticket first, and the key word comes first.
2. **Gets believed.** Insider vocabulary signals that the customer knows the home version and wants it, so the "make it for locals" default should be off. Never claim to be from the culture; ask for the home version honestly ("I love it the way you cook it at home"). This is the main lever. Kitchens keep two versions of many dishes, and a note in the kitchen's own language is the best lever for getting the home one (a widely reported pattern, not a measured effect).
3. **Gets executed.** It asks only for things the line can still change when the ticket arrives: more or fewer chilies, skip the sugar or cream, cook it dry, char the bread, put sauce on the side. A note can't take sugar out of premade dough or a batch sauce; pick another item instead. Paid extras (a fried egg, double tortillas where they're charged) go through the app's options, not the note. It doesn't say "make it authentic".

## The order is one voice
The notes are written per dish, but the kitchen reads them together, often on one printed ticket, and the set as a whole is what tells them how to cook the meal. Write it like one regular texting the kitchen from their phone, not like a form filled in four times.

**Write the whole set first, then split it across the items.**
- **Say the talk once.** The greeting, the "like home" framing and any explanation go on the first item only, usually the anchor dish. The thanks goes on the last item. No sentence appears in two notes.
- **Each note leads with its own dish's lever**: the bhurji is dry, the naan is charred, the tacos skip the cheese. A dish with nothing to fix gets no note.
- **Shared requirements travel short, but every ticket names the target.** If the eater wants a non-native heat or no sugar on every dish, explain it once on the first note; on each later dish restate just the target in two or three words ("Kolhapuri teekha yahan bhi", "no sugar"). Never write only "same heat": that ticket may print alone at another station. Never paste the explanation four times.
- **Dietary and allergy constraints: first, identical wording, on every affected item.** They are safety, not voice.
- **Polite endings repeat naturally** (お願いします, ครับ/ค่ะ, please). That isn't repetition.
- **Flow.** Later notes can lean on the earlier ones the way texts do ("aur naan…", "y el elote…"). Vary the openings. The set should read as one message broken into pieces.
- **One-note platforms** (one cart-level field, as on Swiggy and Zomato): write it as one short message going dish by dish in the same voice, dish names first.

**The voice is the eater's, in the script the community really types.** Many communities text their own language in Latin script, mixed with English: Hinglish or Roman Hindi and Urdu, Banglish, Taglish, Arabizi (3, 7 for ع, ح), Spanish without accents and with "porfa". Others text in native script (Thai, Japanese, Korean, Chinese). Use the cuisine profile's romanization when that is how people type it, and native script when that is. Allowed: lowercase, light code-mixing, a fond nickname for the dish, at most one emoji in the whole set (🙏 or 😋), optional, never carrying a request. Not allowed: slang you can't gloss for the user, fake intimacy, texting-speak that hides a request, or voice in front of the lever: in every line the key word comes first, and a greeting goes after it or nowhere.
- **Homecoming eater**: match how they write to you (their mix of languages, their warmth).
- **Explorer**: a warm, informed customer. Never imply prior visits, shared background, or "like my mom makes"; "the way you'd eat it at home" is honest.
- **The counter line stays plain and polite** (e.g. Japanese です/ます). Casual voice goes only to the cook in their own language; casual Japanese to a Tokyo counter reads as rude.

## Inputs
- Taste Brief (heat level and anchor phrase, sweetness, `must:` constraints, avoid list)
- Kitchen profile from `kitchen-scout` (who cooks there, their language, the local counter language)
- Cuisine profile `taste-brief/cuisines/<cuisine>.md` (insider vocabulary, polite address)
- Dish-fidelity flags (🛠 items need a corrective lever in the note)

## Language stack (order matters)
1. **Line 1: the counter language**, the first reader's, plain and polite (English in the US, Japanese in Japan). Take the counter and line-cook languages from `kitchen-scout/markets/<market>.md`; they can differ from the cuisine's language (e.g., Spanish-speaking line cooks in US kitchens, South Asian and Filipino crews in the Gulf).
2. **Line 2: the cook's native language**, in the script the community actually types (Roman Hinglish or Devanagari for most North Indian kitchens, Thai script, Spanish...). This is the believability lever and where the voice lives.
3. **Line 3: English** (or the user's language) when the counter language isn't English: the fallback and the user's audit trail.

Every submitted line carries every requirement. Skip a line where two readers share a language. Skip line 2 if provenance is uncertain: a Hindi note to a Nepali cook still mostly works (Nepali speakers commonly read Devanagari and Hindi), but a Thai note to a Lao cook is less certain.

**Script check:** if the platform's printer may not render a script, move the English line to the top; it still carries the order.

## Register
- Follow the cuisine profile's **Address default** (usually no term, or a neutral one like "Namaste ji"). Use a familial or gendered term (bhaiya, anna, phi) only when the profile allows it and the user uses it or the cook's gender is known. Warmth comes from the wording, not kinship terms.
- Thanks once, in their language, on the last note.
- No ALL-CAPS paragraphs. One capitalized keyword (DRY, NO SUGAR) is fine.

## Content rules
- **One note per item** where the platform allows it; per-item notes travel with each dish's ticket. The set follows "The order is one voice" above.
- **Lead with the dish-specific lever**, then heat, then the "no local adjustment" line.
- **Name the heat by anchor, not a number**: "Kolhapuri-level", "phet baep khon Thai kin", "con chile de árbol como allá". For Americans, add the US anchor in English ("habanero-salsa hot").
- **The corrective lever for every 🛠 flag**: "dry, no gravy", "no sugar/honey", "corn tortillas, not flour", "holy basil + fried egg on top".
- **Check breads and rice too.** In some markets the bread is where the local adaptation is worst; add a note when there's a concrete lever.
- **Avoid asks that trigger surcharges or refusals**: "extra meat", "make a different dish". Swap to a different item instead.
- **Length**: ≤ 500 characters per note (platform limits vary; Uber Eats is generous, others cap around 150). If capped, cut greetings, thanks and authenticity phrasing first, never a dietary or allergy constraint. Keep every essential request in both the native line and a short standalone English line. If the essentials still don't fit, use an app option for that item, move the rest to an order-level note, or pick another item.
- **Allergy and dietary needs** go first, in all languages. A note alone isn't enough for a serious allergy, and neither is a dish whose usual recipe lacks the allergen (house recipes and shared equipment vary). The user must confirm ingredients and cross-contact with the restaurant before ordering (the agent can't call). Without that confirmation, don't order the affected items for that eater.

## Templates
These are building blocks for the FIRST note and for single fixes, not text to paste into every item.

**Native level, no local adaptation (the set's opener: first note only)**
```
<Address, if the profile allows one>, please make it the way it's normally eaten at home: usual spice and seasoning, not adjusted for <local market> taste.
```
Add an explicit heat or sweetness line ONLY if (a) the brief deviates from native on the eater's word, or (b) the market drift is known to undercut this dish's native level (e.g., a market that sweetens gravies or mutes chili). Never write "no sweetness" for a dish that is traditionally sweet.
```
<native line: same, with insider words>
<local-counter line>
```

**Structure fix (dish served differently in this market)**
```
<KEYWORD: DRY / NO GRAVY / CORN TORTILLAS> please — <home description in 6–10 words>. <heat line>.
```

## Worked example: one order as a set (Tokyo, Indian-run kitchen)
This eater EXPLICITLY asked for Kolhapuri-level heat on the curries and no sugar on everything. That's a user override, not the default. Line order: Japanese counter (plain, polite), Hinglish for the cook, English fallback. (Rewritten from a real 2026-11-07 order, whose first version pasted the same heat paragraph into every note. Kitchen compliance wasn't recorded; this illustrates the style, it isn't a tested result.)

1) Paneer bhurji (anchor; menu said "in gravy", brief said dry). The explanation lives here:
```
パニールブルジはグレービーなしのドライでお願いします。カレーは全部かなり辛め、どの料理も砂糖は入れないでください。
bhurji ekdum sukhi banana, gravy bilkul nahi, ghar jaisi 🙏 aaj saari curries Kolhapuri teekhi chahiye, cheeni kisi mein mat daalna
DRY bhurji, no gravy, scrambled like home. All curries Kolhapuri-hot; no added sugar in anything.
```
2) Chicken mirch: the target restated in a few words:
```
チキンミルチも、かなり辛め・青唐辛子多め・砂糖なしでお願いします。
chicken mirch bhi Kolhapuri teekha, hari mirch zyada, cheeni nahi
Kolhapuri-hot here too, extra green chilli, no sugar.
```
3) Chole: its own lever first:
```
チャナマサラはとろみ強め、酸味を効かせて、かなり辛め・砂糖なしでお願いします。
chole gaadhe aur khatte banana, mirchi wahi Kolhapuri wali, meetha nahi
Chole thick and tangy, Kolhapuri heat, no sugar.
```
4) Naan (Japan's naan drift is sweet, huge and fluffy; a note can't take sugar out of the dough, so if that matters, order tandoori roti instead). Thanks closes the set:
```
ナンは薄めで焼き目しっかり、はちみつ・砂糖のトッピングなし、にんにくとパクチー多めでお願いします。ありがとうございます！
aur naan patli, tandoor mein achhi kadak seki hui, upar honey/cheeni nahi, lehsun dhaniya zyada. shukriya ji!
Thin naan, well charred, no honey or sugar on top, plenty of garlic and coriander. Thank you!
```
Read top to bottom, it's one person texting four lines; read alone, each ticket still says its heat and no sugar. Swap the Japanese line for your market's counter language.

## Sketch sets (other cuisines; adapt the vocabulary from the cuisine profile)

Thai, US market, an American explorer who explicitly asked for heat 8 (above Central Thai home heat, so เผ็ดมาก, not เผ็ดแบบคนไทยกิน), 2 items:
```
1) Kaphrao: holy basil (not sweet basil), fried egg on top, no onion or bell peppers. Very spicy, not sweet.
   กะเพรา ใช้ใบกะเพรา ไม่ใช้โหระพา ไข่ดาวด้านบน ไม่ใส่หอมใหญ่กับพริกหวาน ขอเผ็ดมาก ไม่หวานนะครับ
2) Som tam: NO CRAB. Lao style with pla ra, very spicy too. Thanks!
   ส้มตำไม่ใส่ปู ขอแบบลาวใส่ปลาร้า เผ็ดมากเหมือนกัน ขอบคุณครับ
```
(Particle ครับ assumes the user uses it; use ค่ะ/คะ per the Thai profile otherwise, and never infer it from a name. If the fried egg is a priced option, add it in the app.)

Mexican, US market, native heat, 2 items:
```
1) Pastor tacos: double corn tortillas, with everything (pineapple, onion, cilantro), no cheese or cream. House salsas on the side.
   los de pastor con doble tortilla de maiz, con todo (piña, cebolla, cilantro), sin queso ni crema. las salsas de la casa aparte porfa
2) Elote preparado: mayo, cotija, chile powder. Thanks!
   y el elote preparado con mayonesa, cotija y chile en polvo. gracias!!
```

## Verify
Before submitting, check each item's options and note. After placing the order, read the confirmation or tracking page and check that every item's note is present; a note shown there still doesn't prove the kitchen saw it. If an essential one is missing, use the app's edit or chat route if it has one, or ask the user to call the restaurant (the agent can't call).

Native-language lines: you are writing in languages the user may not read. They carry the same requests as the English line, plus only greeting, thanks and warmth: no extra requests, no claims about the eater. Show the user the full set, with a back-translation of each non-English line, before submitting. Read the set top to bottom once: cut any repeated greeting, thanks, framing or explanation. Keep requirements (heat target, no sugar, dietary constraints) and polite endings on every dish they apply to. Then read each ticket alone: it must still say everything that dish needs.
