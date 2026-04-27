# GridX Core — Full Project Guide (Handover)

_Last updated: 2026-04-27_

এই গাইডটা এমনভাবে লেখা যাতে তুমি **new tab খুলে যেকোনো সময়** website edit/update করতে পারো।

---

## 1) Project Summary

- **Project name:** GridX Core
- **Repository:** `lmd867758-crypto/modvault-site`
- **Live site:** `https://modvault-site.vercel.app/`
- **Stack:** HTML + CSS + Vanilla JavaScript
- **Deployment:** GitHub `main` branch push হলে Vercel auto-deploy

---

## 2) Folder & File Map

Project root: `modvault-site/`

### Core files
- `index.html` → Home page, category filters, card grid, search, latest-first ordering
- `dl.html` → App details page, 2-step download flow (smart link + final link)
- `config.js` → Brand name + Google Sheet config
- `README-BN.md` → Basic setup notes
- `PROJECT_GUIDE.md` → (এই ফাইল) full maintenance guide

---

## 3) Data Source (Google Sheet)

Website data Google Sheet থেকে আসে।

### Required columns (header row)
`name | description | icon | version | platform | downloadUrl | features | category`

### Important rules
1. **`icon` must be direct image URL**
   - ✅ valid: `https://i.ibb.co.../image.jpg`
   - ❌ invalid: `https://ibb.co/...` (page link)
   - ❌ invalid: `https://gemini.google.com/...` (web page)

2. `downloadUrl` must be real file/page download link
3. Sheet must be shared as Viewer (public link)

---

## 4) Config (Brand + Sheet)

File: `config.js`

```js
window.APP_CONFIG = {
  SHEET_ID: "YOUR_SHEET_ID",
  SHEET_TAB: "পত্রক1",
  BRAND: "GridX Core",
  COPYRIGHT: "© 2026 GridX Core"
};
```

---

## 5) Home Page Behavior (`index.html`)

### Current key behavior
- Responsive mobile/desktop UI
- Card thumbnails in **16:9** frame
- Card image centered
- Platform + rating visible
- Card action button removed
- Smooth scrolling enabled
- **Latest uploads appear first** (most recent row at top)
- Search results also follow latest-first order

### Latest-first logic
Data loaded from sheet, mapped, then reversed:

- `latestAppsCache = trimmed.reverse();`

So new rows added at bottom of sheet will show at top on site.

---

## 6) Details Page Behavior (`dl.html`)

### Current key behavior
- Full redesigned details UI (matching site style)
- App icon/logo frame is **16:9**
- Feature chips + highlights list
- **2-step download flow**:
  1. First click opens smart link
  2. Return and click again for actual download

### Smart link currently used
`https://www.profitablecpmratenetwork.com/th4iq4cz?key=da8ba8716ee7c214e9decd3ec3f0f3dd`

### Gate logic
- Gate state stored in browser `localStorage`
- Per-app key format: `gx_smart_gate_<appId>`
- Gate validity window: 30 minutes

---

## 7) Edit Anytime from New Tab (No local setup needed)

যদি তুমি local terminal ছাড়া সরাসরি browser থেকেই edit করতে চাও:

1. New tab খুলে GitHub repo open করো  
   `https://github.com/lmd867758-crypto/modvault-site`
2. যে file edit করতে চাও (`index.html`, `dl.html`, `config.js`) open করো
3. ✏️ Edit button (pencil) চাপো
4. Change করে **Commit directly to `main`**
5. 1–2 min wait → Vercel auto-deploy
6. Live site hard refresh (`Ctrl + F5`)

### Faster method
- GitHub repo page এ `.` (dot) press করলে web editor (github.dev) খুলে যায়
- সেখান থেকে multiple file edit করা সহজ

---

## 8) Common Edit Tasks (Quick Reference)

### A) Home card layout change
- File: `index.html`
- Area: CSS sections (`.grid`, `.card`, media queries)

### B) Category color/headline/icon style
- File: `index.html`
- Functions/classes:
  - `headClass(category)`
  - `toneClass(category)`
  - `.h-games`, `.h-apps`, etc.

### C) Latest-first on/off
- File: `index.html`
- In `fetchApps()` cache build area:
  - current: `latestAppsCache = trimmed.reverse();`
  - oldest-first চাইলে `.reverse()` remove করো

### D) Change smart link
- File: `dl.html`
- Constant: `SMART_LINK`

### E) Change 2-step button text / download instruction
- File: `dl.html`
- Function: `setupDownloadFlow(app)`
- How-to block: HTML section `.howto`

---

## 9) Troubleshooting

### Problem: New icon না দেখাচ্ছে
- Check if icon URL direct image কিনা
- Test by opening icon link in browser directly
- Cache clear + hard refresh

### Problem: Latest item top এ আসছে না
- Confirm row actually sheet-এর শেষে add হয়েছে
- Hard refresh (`Ctrl + F5`)
- Check that `latestAppsCache = trimmed.reverse();` still আছে

### Problem: Deploy update দেখতে পাচ্ছো না
- Vercel deploy complete হয়েছে কিনা check
- URL এ version query দাও: `?v=10`
- Browser cache clear

---

## 10) Safe Update Checklist (Every Change)

1. File edit
2. Save/commit
3. Push to `main`
4. Wait for Vercel deploy
5. Test:
   - Home page
   - Search
   - Details page (`dl.html?id=1`)
   - Mobile + desktop
6. Hard refresh

---

## 11) Recommended Workflow for Future

- Big UI edit → first desktop, then mobile polish
- Keep `index.html` and `dl.html` design language consistent
- Use direct image links only in sheet
- After each major update, add a short note in this guide

---

## 12) Final Notes

তুমি এখন **new tab থেকে যেকোনো সময়** project maintain করতে পারবে:
- GitHub web edit
- Auto deploy
- Sheet-based data updates

If needed later, this file can be expanded with:
- SEO checklist
- ad placement map
- release log table
- rollback command list
