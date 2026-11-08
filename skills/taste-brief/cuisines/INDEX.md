# Cuisine index

Route the eater's words to a profile. Read ONLY the matched profile(s), not the whole directory.

| Profile | Covers / aliases |
|---|---|
| indian.md | Indian, desi, Punjabi, Maharashtrian, Gujarati, Bengali (West Bengal), Goan, Kerala, Tamil, Chettinad, Andhra, Hyderabadi, Indo-Chinese |
| pakistani.md | Pakistani, Lahori, Karachi, Sindhi, Peshawari, Pashtun, Balochi, karahi, nihari |
| sri-lankan.md | Sri Lankan, Sinhala, Jaffna Tamil, kottu, hoppers |
| nepali.md | Nepali, Newari, Thakali, momo, dal bhat, Himalayan |
| chinese.md | Chinese, Sichuan, Hunan, Cantonese, dim sum, Dongbei, Xinjiang, Uyghur, Shanghai, Yunnan, Taiwanese, Chinese-American |
| korean.md | Korean, K-BBQ, jjigae, Busan |
| japanese.md | Japanese, sushi, ramen, izakaya, yoshoku, Okinawan |
| vietnamese.md | Vietnamese, phở, bún bò Huế, bánh mì |
| thai.md | Thai, Isan, Lanna/Northern Thai, Southern Thai, Lao-adjacent |
| indonesian-malaysian.md | Indonesian, Padang, Javanese, Manado, Balinese, Malaysian, Penang, mamak, Singaporean hawker |
| filipino.md | Filipino, Kapampangan, Bicolano, Cebuano, Ilocano |
| levantine-arab.md | Lebanese, Syrian, Palestinian, Jordanian, Iraqi, Egyptian, Yemeni, Gulf, shawarma, mezze, "Middle Eastern" |
| turkish.md | Turkish, kebab, döner, Adana, Gaziantep, lahmacun |
| persian.md | Persian, Iranian, kabab, tahdig |
| ethiopian-eritrean.md | Ethiopian, Eritrean, Habesha, injera, kitfo |
| west-african.md | Nigerian, Ghanaian, Senegalese, jollof, suya, egusi |
| caribbean.md | Jamaican, Trinidadian, Haitian, Guyanese, Puerto Rican, Dominican, Cuban |
| mexican.md | Mexican, Tex-Mex, Oaxacan, Yucatecan, birria, tacos |
| peruvian.md | Peruvian, ceviche, Nikkei, chifa, pollo a la brasa |
| italian.md | Italian, Roman, Neapolitan pizza, Bolognese, Sicilian, Calabrian, Italian-American |
| greek.md | Greek, Cretan, Cypriot (Greek and Turkish Cypriot), gyros, souvlaki, nistisima / Orthodox fasting |
| maghrebi.md | North African, Moroccan, Algerian, Tunisian, Libyan, tagine, couscous, harissa, merguez |
| bangladeshi.md | Bangladeshi, Sylheti, Chittagonian, Dhaka/Old Dhaka, kacchi, bhorta, British curry house (phall, vindaloo, tikka masala) |
| central-american.md | Salvadoran, Guatemalan, Honduran, Nicaraguan, Costa Rican, Panamanian, pupusas, baleadas (not Mexican) |

## Umbrella words, filters and missing profiles
These words don't name one profile. Ask which, or route as below.

| Eater says | Route |
|---|---|
| Mediterranean | Umbrella, not a cuisine: ask which. levantine-arab.md (mezze, shawarma, falafel), turkish.md (kebab, döner, meze), italian.md, greek.md, maghrebi.md |
| Central American, "Latino" | Ask which: central-american.md, mexican.md, caribbean.md (Spanish Caribbean), peruvian.md; Colombian/Venezuelan has no profile yet. |
| Halal | A **hard filter, not a cuisine.** Keep the cuisine the eater named and apply halal as a confirmed hard filter (pork-free ≠ halal). If no cuisine is named, ask. |
| momo | nepali.md (also Tibetan-run kitchens; see its language routing) |
| arepa, Colombian, Venezuelan | **no profile yet → build from `_template.md`** (colombian-venezuelan; not mexican.md or peruvian.md) |
| curry house, "Indian takeaway" | Ask which. indian.md, pakistani.md, bangladeshi.md (its curry-house rows cover the British-style menu). Many curry houses are Bangladeshi- or Pakistani-run: check provenance before choosing note language. |
| Bengali | Ask which: West Bengal → indian.md; Bangladesh → bangladeshi.md. |
| Sudanese | **no profile yet → build from `_template.md`** |

No profile? Build a brief from first principles using `_template.md` as the checklist (traditions, home-vs-export markers, vocabulary, composition, provenance), and tell the user the brief is unbacked by a profile.

## Vocabulary confidence
Native-language phrases were written by the model, not verified by native speakers. Before a note ships:
- keep native lines short and literal to the English line;
- prefer dish-vocabulary (tere, sookha, 特辣, heavy pepper) over full sentences when confidence is lower (flagged in-profile);
- the English line must stand alone.
Corrections from real eaters/kitchens → edit the profile and note the source.
