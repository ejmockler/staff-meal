# Market: Japan

## Local palate vector
Sweeter, milder, umami/dashi-forward. Less chili and fewer whole spices, sweeter sauces (sugar, mirin, honey or fruit in curry), oversized sweet naan, mayo and cheese add-ons. Rice portions are normal to generous (大盛り is often free). Default heat is often 甘口 (amakuchi). Kitchens usually have a spice selector (辛さ 1–5, or 甘口 / 中辛 / 辛口 / 激辛). Map the level to the brief's heat, which is the dish's home default unless the user asked for more or less. The top level is calibrated to Japanese tolerance, so pick it (and add a note) only when the brief's heat is at or above what that top level delivers (roughly 6+ on the brief scale). Otherwise pick the matching level, never above the brief. Scales are shop-specific: "top level" means the top regular tier, never a challenge tier (e.g. CoCo Ichibanya's highest levels are restricted to people who have finished lower extreme tiers).

## Counter and line languages
Japanese counter staff often read the ticket first, and the cook reads it second. Notes: English + the cook's language + Japanese. Japanese notes should be polite (〜でお願いします).

## Platforms (as of 2026-11; re-verify after 6 months)
Uber Eats (field notes: `platforms/ubereats.md`) leads on active users. 出前館 Demae-can is second and has the widest regional coverage; outside big cities it is often the only option. Rocket Now (ロケットナウ, run by Coupang, launched in Tokyo in 2025) is growing fast with low or zero delivery fees. It now covers all 23 wards and many major prefectures (Hokkaido, Miyagi, Kanto, Aichi, Shizuoka, Kansai, Hiroshima, Fukuoka and others), but coverage changes by shop, so check the address in the app. Dead: Wolt (consumer app closed 2026-03-04 when DoorDash left Japan), menu (KDDI ended it on 2026-09-30), foodpanda and DiDi Food (both exited earlier). Do not route orders to any of these. All apps are driven via `platforms/_browser.md`.

## Proxy map
| Sign says | Typically run by | Drift to undo | In-culture tells / hubs |
|---|---|---|---|
| インドカレー / Indian | **Nepali** (インネパ, the majority) | huge sweet fluffy naan, sweet butter chicken, cheese naan, one curry base across dishes | regional menu (misal, Kolhapuri, dosa, appam, Chettinad), Indian owner named in press or Tabelog, Hindi/Marathi/Telugu/Tamil reviews, a thali with no naan-set framing; Nishikasai (西葛西, Edogawa) is the Indian residential hub; Kobe has an old Indian merchant community. Generic 'ナン・カレーセット' plus 'ネパール' in the shop description means インネパ. |
| 南インド / South Indian | mixed: Indian-run (Tamil, Kerala, Andhra/Telugu), Japanese chefs devoted to the cuisine (often faithful), and Nepali shops that added dosa | milder, less sour sambar and rasam | banana-leaf meals, sambar or rasam refills, regional naming (Chettinad, Andhra meals); Indian-language reviews; Nishikasai for the Indian community |
| パキスタン / halal | Pakistani | — | halal kitchens in Saitama and Chiba, karahi by weight |
| 中華 / ガチ中華 | Japanese-Chinese (町中華, its own cuisine) or mainland-run (ガチ中華) | sweet ebi chili, mild, starchy mapo | search 'ガチ中華'; Ikebukuro North Exit, Nishi-Kawaguchi, Okachimachi/Ueno, Takadanobaba; simplified-character menus, Chinese-only reviews, regional names (東北, 四川, 湖南, 西安) |
| 台湾料理 (cheap izakaya type) | often mainland-Chinese-run, not Taiwanese | Japanese-izakaya mains, 台湾ラーメン (a Nagoya invention) | for a real Taiwanese brief look for 魯肉飯, 牛肉麵, 鹽酥雞, Taiwanese owners or traditional-character menus |
| 韓国料理 | Korean or Zainichi | milder, sweeter tteokbokki | Shin-Okubo (新大久保), Korean-script menu |
| タイ料理 | often Thai-run | sweeter, milder | Isan dishes, Thai-script menu |
| ベトナム料理 | increasingly Vietnamese-run (large community) | milder | Vietnamese-language menu, bún bò Huế |
| イタリアン | many Japanese chefs trained in Italy (often excellent), plus chains | cream carbonara; yōshoku (Napolitan) is a separate cuisine | VPN pizza certification, regional menus |
| メキシカン | Japanese-run, US-influenced | Tex-Mex, cheese, flour tortillas | nixtamal corn tortillas, Mexican owner |
| ペルー料理 | Peruvian (often Nikkei) | — | Tsurumi (Yokohama), Isesaki and Oizumi (Gunma), Aichi/Shizuoka factory towns; few deliver, so plan for pickup; Spanish-language menus, pollo a la brasa, ceviche, lomo saltado |
| トルコ料理 / ケバブ | Turkish- or Kurdish-run (the Kurdish community centres on Warabi and Kawaguchi, Saitama); kebab stands also South Asian-run | sweet yogurt or 'hot' sauces tuned for Japan, cabbage filler | charcoal grill, yaprak döner, lahmacun, Turkish- or Kurdish-language reviews; Warabi and Kawaguchi for Kurdish or Anatolian home cooking |
| ブラジル料理 | Nikkei-Brazilian | — | Oizumi (Gunma), Hamamatsu (Shizuoka), Homi Danchi Toyota (Aichi), Gifu; Portuguese menus, churrasco, coxinha, Brazilian supermarkets with delis |
| ミャンマー料理 | Burmese (Bamar, Shan, Kachin) | — | Takadanobaba 'Little Yangon'; mohinga, tea-leaf salad |
| スリランカ料理 | Sri Lankan | Japanese-spice-curry framing | Tokyo and Chiba, Osaka spice-curry scene; rice and curry, kottu, hoppers |
| Korean (Osaka) | Zainichi Korean | — | Tsuruhashi and Ikuno Koreatown, Osaka (Zainichi yakiniku, horumon, kimchi shops) |
| ハラール / South Asian (Tokyo) | Bangladeshi, Pakistani, Nepali | — | Shin-Okubo 'Islam Yokocho'; Yashio (Saitama) for Pakistani |
| インドネシア料理 | Indonesian (growing, halal) | — | Indonesian-language reviews |

## Proxy flips
- **Nepali-run インドカレー shops**: they're a weak stand-in for Indian home food, but often the best Nepali kitchens available. Look for ダルバート (dal bhat), momo with achar, sekuwa or choila, sometimes off-menu. For a Nepali brief, search these first.
- **町中華 (Japanese-Chinese diners)**: poor for a mainland Chinese brief, but the real thing for Japanese-Chinese (gyoza, chāhan, ramen, レバニラ, 天津飯). Use them when the brief is 町中華 itself.
- **イタリアン chains / cafés**: poor for Italian, but in-culture for yōshoku (Napolitan, doria, omurice, hayashi rice) when that is the brief.
- **Japanese curry houses (カレーライス, e.g. CoCoIchi)**: poor for Indian, but the home version of Japanese curry rice. Its native default is mild-to-medium and sweet-leaning; that is correct for this dish, not drift.
- **Cheap 台湾料理 izakaya (mainland-run)**: poor for Taiwanese, but some cook mainland home dishes (Fujian, Dongbei) from a separate Chinese-language menu. Check reviews before relying on it.
- **Halal grocery delis (Pakistani, Bangladeshi, Indonesian)**: not restaurants on the app, but often the best source of home-style biryani, nihari or Indonesian lauk. Usually pickup.
- **Brazilian / Peruvian supermarket delis**: poor for a generic "Latin American" brief, but in-culture for Brazilian or Peruvian home food (coxinha, feijoada, pollo a la brasa). Usually pickup.

## Hard-filter notes
- **Pork** is everywhere and often hidden: tonkotsu and many other ramen broths, gyoza filling, chāshū, lard in 町中華 frying, ポークエキス in curry roux and sauces, gelatin. "Chicken" ramen can still use pork fat. For a no-pork filter, ask the shop or pick a certified halal kitchen.
- **Halal**: there is no government standard. Private bodies (e.g. Japan Muslim Association, Japan Halal Association, NAHA) certify. Many South Asian shops self-declare halal; "Muslim-friendly" means no pork or alcohol in some dishes, not certification. Look for the certifier's name in the listing or the shop photo.
- **Alcohol**: mirin and sake are standard in Japanese cooking (teriyaki, nimono, tare, many dressings), and soy sauce has trace alcohol. "No alcohol" in Japanese food is hard to guarantee; South Asian halal kitchens are the safer route.
- **Fish / vegetarian**: dashi (bonito, sometimes niboshi) is in most soups, noodle broths and simmered vegetables, so "vegetable" dishes are often not vegetarian. Shōjin ryōri and labeled ヴィーガン shops are the exception.
- **Labeling**: packaged food must list 9 major allergens (egg, milk, wheat, shrimp, crab, peanut, buckwheat, walnut, and cashew since 1 Apr 2026, with a transition to 31 Mar 2028, so older stock may omit cashew). Restaurants are not required to, and delivery-app allergen info is inconsistent. For a serious allergy, confirm with the shop.

## Kansai (Osaka, Kobe, Kyoto)
The user is Kobe-based, so for most orders start with Kobe hubs and widen to Osaka (the bigger, denser foreign-food scene). Kyoto is usually out of delivery range from Kobe, so treat it as pickup. Platforms are the same as above. Check the address in each app, because Rocket Now and Demae-can coverage differs shop by shop.

### Kansai palate
- **Dashi-light, not salt-light.** Kansai cooking is kombu-forward, and soups and simmered dishes look pale because they use 薄口醤油 (usukuchi). Usukuchi is lighter in color but saltier than Kanto's koikuchi, so a pale Kansai broth is not a weak one. When a Kanto-trained eater says "this udon tastes bland", the kombu-and-usukuchi balance is the native level. Don't add a "stronger" note.
- **Sweeter in places, not across the board.** Osaka "sauce culture" (okonomiyaki, takoyaki, kushikatsu sauce) and Kansai sukiyaki (sugar straight into the pan) lean sweet. Kyoto's white miso (西京味噌) is sweet. On the other hand, Kansai だし巻き is less sweet than Kanto's sweet 卵焼き. Judge each dish by its own home version.
- **肉 means beef.** In Kansai, 肉じゃが, カレー and 肉うどん default to beef, and steamed pork buns are sold as 豚まん, not 肉まん. This matters for a no-beef brief, and it doesn't clear a no-pork brief either (curry roux can still contain ポークエキス).
- **Kyoto-style Chinese (京都中華)** is a Cantonese-based local style that uses little garlic or strong spice and adds kombu to the stock. The usual explanation is the geiko and maiko districts, where food odor mattered. It is mild by design.
- Foreign-food drift is the same as Japan as a whole (sweeter, milder, big naan). Osaka diners are known for liking value and big portions, and Kobe has a long yōshoku and beef culture, so expect extra-large sets and demi-glace or cheese add-ons on non-Japanese menus.

### Kansai proxy rows
These rows extend the national table. The Zainichi Korean row (Tsuruhashi and Ikuno) and the Osaka Sri Lankan note above still apply.

| Sign says | Typically run by | Drift to undo | In-culture tells / hubs |
|---|---|---|---|
| 中華 / 南京町 (Kobe) | old-established 華僑 (overseas Chinese) families with Guangdong, Taiwan, Sanjiang (Zhejiang and Jiangsu) and Fujian roots (Guangdong about 30%, Taiwan about 20% in a 1993 survey), plus newer mainland-run shops | the Nankinmachi street stalls are tuned for tourists (sweet sauces, Japanese-style 豚まん and 小籠包 sold as souvenirs) | for Cantonese home cooking, look for old 華僑-run restaurants in Motomachi and Sannomiya with traditional-character menus, Cantonese dish names (煲仔飯, 腸粉, 叉焼) and a long history; Kobe Kanteibyo (関帝廟) and the Kobe Chinese school mark the old community; for mainland regional food, check Chinese-language reviews |
| インド / ハラール (Kobe) | Indian trading families settled in Kobe since before the war, plus newer Indian, Pakistani, Bangladeshi and Indonesian residents; many "Indian" shops are still Nepali-run | the usual インネパ drift (sweet naan, one curry base) | Kitano and Nakayamate-dori (Chūō-ku): the **Kobe Muslim Mosque** (Japan's first mosque, opened 1935, funded by Indian, Tatar and Turkish traders), halal groceries and South Asian restaurants along Nakayamate-dori, and the Kobe Jain Temple in Kitano; Sannomiya for most of the Indian-run dining rooms; Hindi or Gujarati reviews and a vegetarian or Jain menu are strong tells |
| ベトナム料理 (Kobe / Osaka) | Vietnamese, from a refugee-era community and the more recent wave of technical interns and students | sweeter phở, mild bún | Kobe Nagata-ku (a long-standing Vietnamese community; Catholic church groups); Osaka Imazato (Ikuno-ku), which has more Vietnamese than Chinese residents; Yao (confirmed) and Himeji (plausible); Vietnamese-language menus, bún bò Huế, cơm tấm |
| ネパール料理 (Osaka) | Nepali | the インネパ menu (naan sets) hides the Nepali dishes | Momodani shōtengai (桃谷, Ikuno-ku) has several Nepali shops serving ダルバート (often listed as タカリセット); Nishinakajima-Minamigata and Higashiyodogawa also have Nepali kitchens |
| ガチ中華 (Osaka) | mainland-run, kitchens largely staffed by people from Dongbei | — (or sweeter and less numbing in the more tourist-facing shops) | Namba to Nipponbashi and Shimanouchi, especially around Sōemon-chō (宗右衛門町) north of Dōtonbori: Dongbei, Sichuan, mala hotpot, Xi'an and Wuhan noodles; Imazato (Ikuno) has Dongbei shops too; simplified-character menus and Chinese-only reviews |
| 中国系カラオケ居酒屋 (Osaka, Nishinari) | Chinese-run (about 100 opened in the Kamagasaki shopping streets after 2013) | these are drinking and karaoke bars first; the food is mostly Japanese izakaya snacks | not a kitchen source for a Chinese brief; a few cook home dishes for regulars (unverified), but almost none deliver; use Namba–Nipponbashi instead |
| 韓国料理 (Osaka trendy) | Korean-run or Japanese-run hallyu shops around Tsuruhashi and Ikuno Korea Town | sweet, cheesy hallyu snacks (cheese hotdogs, rose tteokbokki) | this is the Kansai equivalent of Shin-Okubo. For Zainichi home food (horumon, kimchi by weight, チヂミ, Zainichi-style yakiniku) use the old shops on Miyuki-dōri and around Tsuruhashi Station (the national row above). Kobe Nagata-ku also has a Zainichi community with horumon and ぼっかけ shops; Kyoto's Higashikujo is a historic Zainichi area (unverified for current restaurant scene) |
| 中華 (Kyoto) | Japanese-run 京都中華 lineages (e.g. ハマムラ, 鳳舞楼-style からしそば shops) | — (low garlic and mild is native here) | not a stand-in for mainland Chinese; for mainland food in Kyoto check Chinese-language reviews near the universities (unverified) |
| ハラール (Kyoto) | mixed: Japanese-run halal-certified restaurants, Turkish and Kurdish kebab, South Asian | — | the Kyoto Muslim Association runs the Kyoto Mosque (north-central Kyoto, near the Imperial Palace) and, with the Kyoto Council for Sharia and Halal Affairs, lists "Halal" (halal-only) and "Muslim Friendly" (halal menu) restaurants; check the category, not just the logo |

### Kansai proxy flips
- **Nankinmachi stalls (Kobe):** a poor stand-in for a Cantonese meal, but in-culture for Kobe's own Chinatown snack tradition (豚まん, 焼売, 角煮まん). Use them when the brief is "Kobe Chinatown".
- **京都中華:** a poor stand-in for Sichuan or any mainland brief, but the home version of Kyoto's local Chinese (からしそば, 春巻, 酢豚). Don't add garlic or heat notes, because that would remove the style.
- **Ikuno hallyu snack shops:** a poor stand-in for Korean or Zainichi home food, but in-culture for Korean street-snack trends. For a Zainichi brief, go to the old horumon and kimchi shops.
- **インネパ shops in Momodani:** order the Nepali menu (dal bhat, momo, sekuwa) as in the national flip; Momodani is the best Kansai search area for a Nepali brief.
- **Osaka kona-mon and kushikatsu shops:** their sweet-savory sauce is the native level, not drift. Don't write "less sweet sauce" unless the eater asks.

### Kansai hard-filter notes
- **Halal:** in Kobe, start with the Nakayamate-dori shops near the Kobe Muslim Mosque, and look for a certifier's name rather than a "halal" sticker. In Kyoto, use the Kyoto Muslim Association's halal and Muslim-friendly lists. Many Osaka South Asian shops self-declare halal (same caveat as the national note).
- **Vegetarian and Jain:** Kobe's Jain community means a few Indian kitchens understand "no onion, no garlic, no root vegetables". Ask; don't assume. Kansai kombu dashi is often fish-free, but many shops mix in katsuobushi, so the national dashi warning still applies.

## Gaps
Rare or absent: Ethiopian (a few in Tokyo), West African, Caribbean, Persian (a handful in Tokyo). Sri Lankan exists in Kanto and Osaka (see proxy map). Widen the radius or plan for pickup.
