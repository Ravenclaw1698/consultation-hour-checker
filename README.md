# 📅 BRACU CSE – Faculty Consultation Hours

A lightweight, single-file web app that lets students quickly look up **BRAC University CSE faculty consultation hours** by searching with initials or full name.

> **Built by:** Sabbir Ahmed Shishir — BRAC University, Computer Science

---

## ✨ Features

- 🔍 **Search** by faculty initials (e.g. `AAR`) or full name (e.g. `Annajiat`)
- ⌨️ **Autocomplete dropdown** with name, initials, and designation
- 👥 **Full faculty directory** on the homepage — filterable, tabbed by Full-Time / Contractual
- 📋 **Schedule popup modal** — shows the weekly timetable with class slots highlighted
- 📱 **Mobile-friendly** — responsive layout, touch-scrollable table, optimized for all screen sizes
- ⚡ **Live data** — fetches directly from the official Google Spreadsheet (no manual updates needed)
- 🚫 **No backend, no build step** — pure HTML, CSS, and vanilla JavaScript

---

## 🖥️ Preview

| Homepage | Search & Autocomplete | Schedule Modal |
|---|---|---|
| Faculty directory grid with initials, name, room | Dropdown with matching faculty | Weekly timetable in a popup |

---

## 🚀 Getting Started

### Option 1 — Open directly in browser
Just double-click `index.html` — it works straight from the filesystem.

> ⚠️ Some browsers block cross-origin `fetch()` requests when opening local files directly. If the faculty list doesn't load, use Option 2.

### Option 2 — Local dev server (recommended)

**Using Python:**
```bash
cd faculty-hours
python3 -m http.server 8080
```
Then open [http://localhost:8080](http://localhost:8080)

**Using VS Code:**
Install the [Live Server](https://marketplace.visualstudio.com/items?itemName=ritwickdey.LiveServer) extension and click **Go Live**.

**Using Node.js:**
```bash
npx serve .
```

### Option 3 — Deploy (free hosting)
| Platform | Steps |
|---|---|
| **GitHub Pages** | Push to a repo → Settings → Pages → Deploy from branch |
| **Netlify** | Drag and drop the `faculty-hours/` folder at [netlify.com/drop](https://app.netlify.com/drop) |
| **Vercel** | `npx vercel` in the project folder |

---

## 📁 Project Structure

```
faculty-hours/
└── index.html      ← Entire app (HTML + CSS + JS in one file)
└── README.md       ← This file
```

No dependencies. No `node_modules`. No build process.

---

## 📊 Data Source

All data is pulled live from the official BRACU CSE faculty planner spreadsheet using the **Google Sheets CSV API**:

```
https://docs.google.com/spreadsheets/d/{SHEET_ID}/gviz/tq?tqx=out:csv&sheet={SheetName}
```

- **`FacultyList` sheet** — loads all faculty names, initials, designations, rooms, emails
- **Individual sheets** (named by initials, e.g. `AAR`) — loads each faculty's weekly schedule

Since data is fetched live, the app always reflects the **latest version** of the spreadsheet without any manual updates.

---

## 🗓️ How to Read the Schedule

| Color | Meaning |
|---|---|
| 🟡 Yellow cell | Faculty has a class in that time slot |
| ⬜ Blank cell | Faculty is free — available for consultation |

Each time slot is **1 hour 20 minutes** long.

**Time slots:** 8:00 AM · 9:30 AM · 11:00 AM · 12:30 PM · 2:00 PM · 3:30 PM · 5:00 PM · 6:00 PM · 7:30 PM

---

## 🔧 Customisation

To point the app at a different spreadsheet, change the `SHEET_ID` constant at the top of the `<script>` tag in `index.html`:

```js
const SHEET_ID = 'your_google_sheet_id_here';
```

The spreadsheet must be **published to the web** (File → Share → Publish to web) for the CSV API to work without authentication.

---

## 📱 Mobile Support

The app is fully mobile-optimised:

- Responsive grid that adapts from 4 columns → 2 columns → 1 column
- Horizontal scroll on the schedule table with iOS momentum scrolling
- Modal popup sized to fit any screen height
- Touch-friendly tap targets throughout

---

## 📄 License

MIT — free to use, modify, and share.

---

*Data sourced from the official BRACU CSE faculty planner. This tool is built for student convenience and is not an official university product.*