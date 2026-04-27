# GridX Core — AI Agent Operation Guide

_Last updated: 2026-04-27_

এই গাইডটা **manual edit করার জন্য না**।
এটা এমনভাবে লেখা যাতে তুমি **new tab থেকে GPT/AI agent দিয়ে** project edit করাতে পারো।

---

## 1) Project Identity (AI-কে সবসময় দেবে)

- **Repo:** `https://github.com/lmd867758-crypto/modvault-site`
- **Live:** `https://modvault-site.vercel.app/`
- **Main branch:** `main`
- **Core files:**
  - `index.html` (home/grid/search)
  - `dl.html` (details + 2-step download)
  - `config.js` (sheet + brand)

---

## 2) AI Agent-কে দেয়ার Master Prompt (copy/paste)

নিচের template copy করে AI-কে দাও (প্রতি কাজে):

```text
You are editing my live website repo.
Repo: https://github.com/lmd867758-crypto/modvault-site
Branch: main

Rules:
1) Change ONLY what I ask.
2) Do NOT refactor unrelated code.
3) Do NOT rename IDs/classes/functions unless required.
4) Keep Google Sheet data mapping unchanged unless I explicitly ask.
5) After change: show exact diff summary, commit hash, and what to test.
6) Push to main.

Now do this task:
[এখানে তোমার specific কাজ লিখো]
```

---

## 3) Critical Rules (AI যেন ভাঙচুর না করে)

AI-কে সবসময় বলবে:

1. **Unrelated CSS/JS touch করবে না**
2. `renderGrid()`, `fetchApps()`, `setupDownloadFlow()` accidental change করবে না
3. `id` attributes change করবে না (`grid`, `search`, `download-step-btn`, etc.)
4. `config.js` format break করবে না
5. Commit করার আগে ছোট diff maintain করবে

---

## 4) Current Live Logic (AI must preserve)

### Home (`index.html`)
- Card UI responsive (mobile + desktop)
- Thumbnails: 16:9
- Latest uploads first (home + search)
- Search works over loaded + indexed data

### Details (`dl.html`)
- New UI style aligned with home
- 2-step download:
  1) smart link click
  2) second click = final download
- Smart link stored in code constant
- App data from Google Sheet row by `id`

---

## 5) Sheet Structure (must not break)

Header row:

`name | description | icon | version | platform | downloadUrl | features | category`

### Icon note
- Must be **direct image URL** (e.g. `i.ibb.co...jpg`)
- `ibb.co/...` page links are invalid for image rendering

---

## 6) Ready-to-use Task Prompts (copy/paste)

### A) UI tweak prompt
```text
Edit only index.html styles.
Task: [describe change].
Keep grid logic unchanged.
No JS logic edits.
Commit and push main.
```

### B) Latest-first issue prompt
```text
Fix latest content ordering in index.html.
Requirement: latest row must appear first on home and search.
Do not change card layout.
After fix, explain exactly which function/line behavior changed.
Commit and push main.
```

### C) Details page change prompt
```text
Edit only dl.html.
Task: [describe change].
Keep 2-step download flow intact.
Do not change sheet mapping.
Commit and push main.
```

### D) Smart link update prompt
```text
Edit dl.html only.
Change SMART_LINK constant to:
[NEW_LINK]
Do not modify other logic.
Commit and push main.
```

---

## 7) Required Output Format from Any AI

AI-কে বলবে response এ অবশ্যই দেবে:

1. What changed (max 5 bullet)
2. Files changed
3. Commit hash
4. Live test checklist

---

## 8) Quick Test Checklist (AI অথবা তুমি)

After every change test:

1. Home opens (`/index.html`)
2. Search works
3. Latest item appears first
4. Details opens (`/dl.html?id=1`)
5. Step-1 smart link works
6. Step-2 final download works
7. Mobile + desktop layout okay

---

## 9) Rollback Prompt (emergency)

যদি AI খারাপ change করে:

```text
Revert last commit on main for this repo.
Then push main.
Report reverted commit hash and new revert commit hash.
```

---

## 10) BrowserOS/New Tab Workflow (your exact use case)

তুমি যেহেতু new tab এ agent দিয়ে কাজ করাও:

1. New tab open
2. AI chat এ Master Prompt paste
3. Task line লিখে send
4. AI commit hash দিলে save করে রাখো
5. Live site `?v=timestamp` দিয়ে check

Example:
`https://modvault-site.vercel.app/?v=1710000000`

---

## 11) Project Ownership Notes

- তুমি manual code edit না করলেও সমস্যা নেই
- এই guide follow করলে যে কোনো AI agent consistent change করতে পারবে
- সবসময় small scoped prompt দাও (একবারে একটাই কাজ)

---

## 12) Current Important Constants/Behaviors

- `SMART_LINK` in `dl.html`
- Latest-first ordering logic in `index.html`
- Google Sheet live fetch + mapping in both pages

এগুলো change করতে চাইলে prompt-এ explicitly লিখবে।
