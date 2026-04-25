# ✅ তোমার ওয়েবসাইট রেডি (ModVault Style)

আমি তোমার জন্য website files বানিয়ে দিয়েছি এই folder-এ:

`modvault-site/`

ফাইলগুলো:
- `index.html` → home/app list page
- `dl.html` → single app details/download page
- `config.js` → শুধু এখানে Sheet ID বদলাবে

---

## ১) Google Sheet বানাও
Header row (line 1) এ exactly এটা দাও:

`name | description | icon | version | platform | downloadUrl | smartLink | features`

তারপর data row গুলো add করো।

### Example row
- name: Among Us Mod Apk
- description: game description
- icon: https://...jpg
- version: 4.7
- platform: Android
- downloadUrl: https://...apk
- smartLink: https://... (optional)
- features: Mod Apk, Unlimited, No Ads

---

## ২) Sheet public করো
Google Sheet → Share → General access → **Anyone with the link (Viewer)**

---

## ৩) Sheet ID copy করো
Sheet URL example:
`https://docs.google.com/spreadsheets/d/1ABCxyz1234567890/edit#gid=0`

এখানে `/d/` আর `/edit` এর মাঝে যেটা আছে সেটাই Sheet ID.

---

## ৪) config.js এ বসাও
`modvault-site/config.js` file open করে:

```js
window.APP_CONFIG = {
  SHEET_ID: "PASTE_YOUR_SHEET_ID_HERE",
  BRAND: "ModVault",
  COPYRIGHT: "© 2026 ModVault"
};
```

`PASTE_YOUR_SHEET_ID_HERE` এর জায়গায় তোমার আসল ID বসাও।

---

## ৫) Vercel deploy (easy)
1. `modvault-site` folder GitHub-এ upload করো
2. Vercel → New Project → তোমার repo import
3. Deploy

Done ✅

---

## URL format
- Home: `https:// তোমার-domain /index.html`
- App page: `https:// তোমার-domain /dl.html?id=2`

`id=2` মানে Sheet-এর 2nd row app.

---

## দরকার হলে
চাইলে আমি next step এ তোমাকে **live deploy** করতেও guide করতে পারি (তুমি শুধু GitHub/Vercel login করবে, বাকিটা আমি বলে দিবো exact click-by-click)।
