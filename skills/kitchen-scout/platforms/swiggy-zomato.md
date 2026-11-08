# Field notes (partly observed: guest cart run 2026-11-07, no order placed): Swiggy and Zomato

Apply `_browser.md` first, and read `markets/india.md` for kitchens, languages and proxy maps. Mostly drawn from public pages and press; the web-vs-app section includes a logged-out browser run on 2026-11-07 (a Mumbai restaurant, one item added, no checkout). The visible UI is authoritative. Replace these notes with observed quirks after the first real order.

Both apps cover India only. Zomato is owned by Eternal Ltd. Zomato's international food ordering is gone (UAE ended 24 Nov 2022, with users sent to Talabat; the Philippines in Feb 2023).

## Web vs app (as of 2026-11)
- **Zomato: web menus and ADD buttons work (checkout not yet run).** On 2026-11-07, a zomato.com city delivery page (`/<city>/delivery`) listed delivery restaurants with ETAs, and a restaurant's `/order` page showed the full menu with **ADD** buttons, a "Delivering to: … CHANGE" address bar and veg/non-veg/egg markers. The page also shows a banner: "Save more with offers when you order on the app". Some offers may be app-only, so compare the web total with what the user sees in the app before ruling out a cheaper route. Observed 2026-11-07, logged out: ADD puts the item in a guest cart ("Your Order (1) · Subtotal" bar), and **Continue opens a login wall** (+91 phone OTP, email or Google). The note field and checkout sit behind login, so they're still unverified; the user must be signed in in their own tab.
- **Swiggy: web ordering exists.** Swiggy's own guide says you can order on swiggy.com without installing the app. Observed 2026-11-07, logged out: search returns nothing until an Indian delivery locality is set (top-left picker; a foreign IP shows "Other"). After that, restaurant pages show the menu with ADD buttons and a **Pure Veg** filter chip, and `/checkout` asks to log in or sign up before showing address and payment. Note field unverified (behind login). If the web cart won't open in the user's logged-in tab, follow `_browser.md` → App-only platforms.
- **Official AI connectors exist.** Swiggy (Jan 2026) and Zomato (late 2025) both offer MCP ordering connectors for ChatGPT, Claude and others; Zomato's official manifest repo whitelists Claude's redirect URIs (claude.ai and the desktop app); a full login-to-order run is untested. This suite's rule is the user's own browser. Don't switch to a connector unless the user asks. If they do, it's still staff-meal step 5 before placing. Swiggy's documented cart call carries item IDs and quantities only, with no instruction field, so notes may not survive that route.

## Where cooking notes go
- Both apps appear to take one note per restaurant cart, not one per item (unverified for the current web UI; seen as a cart-level "cooking instructions" / "special instructions" field). Zomato has publicly asked users to stop writing "bhaiya accha banana" (make it well) in cooking instructions, which confirms the field existed then; it doesn't prove kitchens read it.
- So the chef-notes go in as **one numbered block keyed by the exact menu item name**:
  ```
  1) Paneer Bhurji: कृपया सूखी बनाइए, ग्रेवी नहीं। (kripaya sookhi banaiye, gravy nahin.) Dry, no gravy please.
  2) Misal: कृपया कट वेगळ्या डब्यात द्या. (kripaya kat veglya dabyat dya.) Kat/tarri in a separate container please.
  ```
  Put the item name first so the line cook can match it to the ticket. Keep it short. The field may have a character limit (unverified). When space runs out, follow the length rule in `chef-notes/SKILL.md`: cut pleasantries first, never a dietary constraint.
- If an item has its own option groups (spice level, half/full, gravy/dry), use the option first and the note only for what the options can't say.
- Notes are requests, not guarantees. There are documented cases of "Jain, no onion/garlic" notes being ignored. **A note never substitutes for a hard dietary filter** (next section).

## Veg / non-veg / egg markers: a hard filter
- Indian menus use the FSSAI mark: a **green** square-with-dot for veg, and **brown/red** for non-veg. Zomato's web menu tags every item `veg`, `non-veg` or `egg` (an egg mark of its own, seen on "Egg Omelette", "Egg Sholay" on 2026-11-07). Swiggy's egg handling isn't verified: it may mark egg items as non-veg, or with a distinct mark (unverified).
- **Treat the markers as a hard filter, applied before the dish-fidelity read**:
  - Vegetarian brief: veg-marked items only. **Egg is excluded unless the eater has said eggs are fine.** Many Indian vegetarians don't eat egg.
  - Strict veg (shared fryers and utensils matter): use a pure-veg restaurant. Zomato's **Pure Veg** filter and Swiggy's **Veg Mode** limit results to veg-only kitchens. The item marker alone doesn't promise a separate kitchen.
  - **Jain** is narrower than veg: no onion, garlic, potatoes or other root vegetables, and often no eating after sunset. The veg mark doesn't capture this. Look for a "Jain" variant or section on the menu, or a Jain/pure-veg kitchen. Don't rely on a note.
  - **Halal:** the veg mark says nothing about it, and pork-free is not halal. Verify per kitchen (`markets/india.md`), and never infer it from the cuisine or the owner's name.
- The markers are restaurant-declared. A mismatch between the marker and the description ("veg" next to "chicken stock") means drop the item and tell the user.

## Memberships (as of 2026-11; re-verify)
- **Swiggy One:** free food deliveries on eligible orders, plus extra discounts. A cheaper **One Lite** has a capped number of free deliveries over a minimum order. There's also an invite-only **One BLCK** tier. Prices change often, so don't quote them from these notes.
- **Zomato Gold:** free delivery from restaurants within about 7 km over a minimum order value (₹99 since Aug 2025 per news reports, earlier ₹199; check the app), plus dining discounts (current terms unverified). Restaurants that deliver with their own fleet are excluded. Since 16 May 2025, Gold no longer waives the rain surge fee, and Swiggy One dropped the same waiver a day later.
- Neither membership waives the **platform fee**.
- Verify that the membership is active on the checkout page (a "Join Gold / Get One" prompt means it isn't). Don't start or renew a membership unless the user asks.

## Fees and upsells to watch
- **Platform fee:** a fixed per-order charge on both apps, paid by members too. As of March 2026 it was about **₹17.58 per order including GST** on both (latest report found; varies by city and day) (Zomato ₹14.90 plus GST; Swiggy ₹17.58 including GST). It changes often, so read it on the checkout page.
- **Other fee lines:** restaurant **packaging charges** (set by the restaurant and can't be turned off; count them in the total), GST on food, delivery fee, **rain/surge** fee, and small-order or long-distance fees where they apply (unverified for the current names).
- **Donation:** Zomato has shown a "Donate ₹… to Feeding India" line at checkout (seen on bills; whether it's pre-ticked is unverified). Zomato also reportedly added an "Edit" slider beside the platform fee that invites paying more than required. **Untick any donation, and leave the platform fee at its minimum, unless the user asked otherwise.**
- **Delivery-partner tip:** both apps offer tip chips (₹20/₹30/₹50-style) and may remember the last tip (unverified). Set the user's chosen amount, and show it in the confirmation.
- **Cutlery:** Zomato made cutlery opt-in in August 2021, so leave it off unless asked. Check the toggle on Swiggy (unverified).
- Faster-delivery tiers and "add for ₹X more" bundles: turn them off unless asked.

## Payment
COD exists on both, but not at every restaurant or in every city. Pay with the method the user chose and saved. Don't switch to COD, and don't enter UPI PINs, OTPs or card details. The user approves any UPI collect request on their own phone.

## Safety
See staff-meal step 5 (the single source).
