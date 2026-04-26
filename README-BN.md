# ✅ GridX Core Website (Live Sheet Driven)

প্রজেক্ট ফোল্ডার:

`modvault-site/`

মূল ফাইল:
- `index.html` → home + category grid + app library
- `dl.html` → single app details + direct download page
- `config.js` → Sheet ID / Tab / Brand config

---

## Google Sheet Structure (exact)
Header row এ এই কলামগুলো দাও:

`name | description | icon | version | platform | downloadUrl | features | category`

> `smartLink` কলাম ব্যবহার করা হবে না।

---

## Sheet Setup
1. Google Sheet → Share → **Anyone with the link (Viewer)**
2. `config.js` এ values বসাও:

```js
window.APP_CONFIG = {
  SHEET_ID: "1CEHLo22Sm6TJ9ng4EphXSYf7ywgfr5PN6KQle1Dv_Mc",
  SHEET_TAB: "পত্রক1",
  BRAND: "GridX Core",
  COPYRIGHT: "© 2026 GridX Core"
};
```

---

## Deploy
- GitHub repo push করো
- Vercel project এ auto-deploy হবে

Live routes:
- Home: `/index.html`
- Details: `/dl.html?id=ROW_NUMBER`
