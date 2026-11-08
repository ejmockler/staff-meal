# Field notes: Uber Eats (web, driven in the user's browser)

Apply `_browser.md` first. These are quirks seen on real runs (Tokyo, 2026-11). The visible UI is authoritative; anything below may go stale.

## UI quirks
- **Special instructions are per item.** Open the item modal and use its textarea. There's no reliable order-level note field.
- Open an item via JS (more reliable than clicking at coordinates, which can open the wrong item):
  ```js
  const el=[...document.querySelectorAll('li')].find(l=>/ITEM NAME/.test(l.innerText)&&l.innerText.length<200);
  el.scrollIntoView({block:'center'}); (el.querySelector('a')||el.firstElementChild).click();
  ```
  Wait about 2 s, then `document.querySelector('textarea').focus()`.
- `computer type` often reports a CDP `Input.insertText` timeout even though the text went in. Verify with `document.querySelector('textarea').value` before retrying, or you'll double-type.
- To find the "Add N to order" / "Update order" button, use `find` and click by ref.
- Quantity: the combobox in the modal, via `form_input`, or the cart drawer's Increment/Decrement. Wait about 3 s between clicks or they get dropped.
- Editing an item from the **checkout** page navigates to the store. Edit from the store page's cart drawer instead.
- `/checkout` sometimes renders blank or redirects. Re-navigate and wait 4 s.
- **Checkout may silently flip to Priority delivery (extra fee).** Re-check the delivery tier right before placing and select Standard by ref.
- Store promos ("¥1,500 off ≥ ¥10,000") apply automatically once the subtotal crosses the threshold. Check the checkout breakdown.
- An Uber One upsell banner on checkout or the order page suggests the membership isn't active on this account. Tell the user.
- The order confirmation/tracking page echoes the per-item notes. Use it to verify every note landed.

## Optional accelerator: in-tab endpoint calls
Calling the endpoints the site uses itself, from inside the logged-in tab, can batch the hard-filter and menu reads across many candidates. They're undocumented and can change without notice. Use them only to speed up reads. Cross-check one result against the UI. If a call errors or looks wrong, fall back to the UI. Never use them for cart or checkout actions.

Change `localeCode` to match the market (jp-en, en-US, ...).

```js
// Search: stores matching a query
const r = await fetch('/_p/api/getSearchSuggestionsV1?localeCode=jp-en', {
  method:'POST', headers:{'content-type':'application/json','x-csrf-token':'x'},
  body: JSON.stringify({userQuery:q, date:'', startTime:0, endTime:0, sortAndFilters:[], vertical:'ALL'})
}).then(r=>r.json());
// → stores with uuid, slug, title, isOrderable
```

```js
// Store detail: menu, fees, ETA, orderable, relative to the CURRENT delivery address
const s = await fetch('/_p/api/getStoreV1?localeCode=jp-en', {
  method:'POST', headers:{'content-type':'application/json','x-csrf-token':'x'},
  body: JSON.stringify({storeUuid:uuid, diningMode:'DELIVERY', time:{asap:true}, cbType:'EATER_ENDORSED'})
}).then(r=>r.json());
// s.data.title, .isOrderable, .etaRange.text, .rating, .fareInfo (serviceFee reflects delivery fee),
// .catalogSectionsMap (items with descriptions → dish-fidelity read)
```
- Store URL IDs are 22-char base64url encodings of the UUID.
- **Hard filter (ASAP orders only)**: `isOrderable` false, or a missing ETA, for the current address means it doesn't deliver now. Set the address in the UI first. For a scheduled order, don't eliminate on this; check the store in the UI with the scheduled time selected.
- Batch: run getStoreV1 over every candidate in one javascript_tool call and print a compact table.

## Safety
See staff-meal step 5 (the single source).
