<div align="center">

<img src="assets/readme/banner.png" alt="Roomify — Space Performance Index" width="100%">

<br>

**Scan your room once. Every furniture listing then tells you whether it _actually_ fits.**

Floor, wall and storage — measured, capped, and scored against the category benchmark.

<br>

![Status](https://img.shields.io/badge/status-MVP-6D5DF6?style=flat-square)
![Stack](https://img.shields.io/badge/stack-vanilla%20JS%20%2B%20three.js-111827?style=flat-square)
![3D](https://img.shields.io/badge/models-120%20GLB%20(CC0)-0E9F6E?style=flat-square)
![Catalog](https://img.shields.io/badge/catalog-229%20real%20listings-2E7CF6?style=flat-square)
![Deploy](https://img.shields.io/badge/deploy-Netlify%20ready-00C7B7?style=flat-square)
![Build](https://img.shields.io/badge/build%20step-none-B45309?style=flat-square)

<br>

[What is SPI?](#-what-is-spi) · [Product tour](#-product-tour) · [Launch film](#-the-launch-film) · [Design system](#-figma-wireframes) · [Run it](#-run-it-locally) · [Deploy](#-deploy-to-netlify)

</div>

---

## 🎬 Roomify in twelve seconds

<div align="center">
<img src="assets/readme/film-demo.gif" alt="Roomify product demo" width="620">
</div>

---

## 🧩 The problem

You can filter furniture by price, by colour, by brand, by delivery date.

You cannot filter it by **"will this still leave me a room I can walk through?"**

So people measure once, forget the number, buy the wardrobe anyway, and end up with a bedroom where the door only opens 60°. The information that matters — *how much of my space does this consume, and what do I get back for it* — exists nowhere in the buying flow.

## 💡 The idea

Roomify puts the room **before** the catalogue.

1. **Scan** your space once. Roomify builds a 3D twin — floor area, wall area, ceiling height, existing pieces.
2. The room is **saved to your account**, not to a browser tab.
3. Every listing — in Roomify, or on any retail site running Roomify — is then re-scored **against your room**: does it fit, what does it cost you in floor and wall, and how much usable storage do you get back.

That score is the **Space Performance Index**.

---

## 📐 What is SPI

<div align="center">
<img src="assets/readme/figma/16-spi-card-anatomy.png" alt="Anatomy of an SPI listing card" width="880">
</div>

```
SPI  =  ( usable storage m³  ÷  room space consumed m² )  ÷  category benchmark  ×  100
```

* **Room space consumed** = floor footprint + wall area taken.
* **Storage is weighted by room profile** — closed volume counts double in a bedroom, reachable-height volume counts double in a kitchen.
* **100 = the category median.** A number above 100 means the piece earns its footprint better than the average item of its kind.

### Reading the benchmark bar

| State | Bar | Means |
| --- | --- | --- |
| **Before you sign in** | grey bar, black benchmark tick | Generic score — no room to compare against yet |
| **Good fit** | 🟢 green bar extending **past** the tick | Beats the category benchmark *and* fits your scanned room |
| **Tight fit** | 🟠 amber bar stopping **short** of the tick | Will not fit — or pushes you over your free-space cap |

<div align="center">
<img src="assets/readme/figma/18-fit-verdicts.png" alt="Fit verdicts — good, neutral, blocked" width="880">
</div>

---

## 🚀 Product tour

### 1 · Create an account — the room lives with you

<img src="assets/readme/app/01-welcome.png" alt="Roomify sign-up" width="100%">

One account, every surface. The room you scan on your phone is the room that re-scores listings on a partner retailer's site later.

<br>

### 2 · Scan the room

Roomify's capture screen is a hand-rolled canvas LiDAR simulation — a rotating sweep ray lays down a point cloud, walls draw up with live dimension labels, furniture is bracketed and named, and the whole thing consolidates into a solid 3D twin.

<div align="center">
<img src="assets/readme/scan-demo.gif" alt="Room scanning animation" width="680">
</div>

| Locating the floor plane | Recognising furniture | Room captured |
| --- | --- | --- |
| <img src="assets/readme/app/02-scan-floor.png" width="100%"> | <img src="assets/readme/app/03-scan-objects.png" width="100%"> | <img src="assets/readme/app/04-scan-complete.png" width="100%"> |

> **No tape measure.** Manual dimension entry exists in the MVP as an optional fallback — in the product, capture is purely a scan.

<br>

### 3 · Your rooms

<img src="assets/readme/app/05-dashboard.png" alt="Room dashboard" width="100%">

Every scanned space, with its dimensions, item count and a live 3D thumbnail. Rooms persist per account.

<br>

### 4 · The 3D editor

<img src="assets/readme/app/06-editor-3d.png" alt="Roomify 3D room editor" width="100%">

A real `three.js` scene — not a floor-plan sketch. Walls fade as you orbit past them, items drop in with physics-ish easing, and the HUD keeps three numbers honest at all times:

* **Floor space** — consumed / available, against your free-space cap
* **Wall space** — consumed / available
* **Storage space** — usable m³ you've actually gained

<br>

### 5 · Add furniture — ranked for *your* room

<img src="assets/readme/app/07-catalog-drawer.png" alt="Add furniture drawer" width="100%">

Three sources in one drawer:

| Source | What it is |
| --- | --- |
| **Amazon Furniture** | 229 real listings with true mm dimensions, brand and price |
| **Basic Furniture** | 120 low-poly GLB pieces (Kenney Furniture Kit, CC0) sized to real-world dimensions |
| **Custom Shapes** | Parametric boxes with modelled internal cavities — build the thing you already own |

Every card is ranked by the recommendation engine before it is drawn: `RECOMMENDED` pills on the best space-earners, an `Over cap` badge on anything that will not fit, and a 0–100 space score in the corner.

<br>

### 6 · Select, move, rotate, replace, sell

<img src="assets/readme/app/08-item-selected.png" alt="Item selected with action toolbar" width="100%">

<br>

### 7 · Bird's eye and locked wall views

| Bird's eye | Wall view |
| --- | --- |
| <img src="assets/readme/app/09-aerial-view.png" width="100%"> | <img src="assets/readme/app/10-wall-view.png" width="100%"> |

Wall views lock the camera square to one wall so wall-mounted pieces — mirrors, shelves, cabinets — can be placed and height-adjusted precisely. Wall colours are editable per wall.

<br>

### 8 · Resell straight out of the room

<img src="assets/readme/app/11-sell-listing.png" alt="List an item for sale" width="100%">

Selecting any placed item exposes **Sell**. Listing it frees its floor and wall allocation immediately and pushes it into the marketplace — the loop that makes the index worth having.

<br>

### 9 · The SPI marketplace

<img src="assets/readme/app/12-marketplace-spi.png" alt="Marketplace with SPI scores" width="100%">

Signed out, a listing shows only its benchmark line and storage. Signed in with a scanned room, the same listing re-scores against *your* floor, *your* walls, *your* cap — and picks up a verdict.

<img src="assets/readme/app/13-marketplace-custom.png" alt="Custom shapes marketplace" width="100%">

<br>

### 10 · Dark mode

<img src="assets/readme/app/14-dark-mode.png" alt="Roomify in dark mode" width="100%">

---

## 🎞 The launch film

A 2½-minute launch film walks the whole flow end to end: scan → account → editor → space caps → resell → SPI marketplace → a partner retailer's site re-scoring its own catalogue once you sign in with Roomify.

<div align="center">
<a href="assets/readme/Roomify-Launch-Film.mp4">
<img src="assets/readme/film-thumbnail.jpg" alt="Roomify launch film — click to play" width="760">
</a>

<b><a href="assets/readme/Roomify-Launch-Film.mp4">▶ Watch the full film</a></b> · 24 fps · 2 min 32 s · original score
</div>

**How it was made** — every frame is deterministic. A `three.js` room is pre-rendered offline to image sequences with per-item screen-space anchor data; a DOM "film page" plays those sequences back behind the real UI chrome; Playwright steps a `window.__frame(scene, t, globalSeconds)` function and pipes JPEG screenshots straight into `ffmpeg`. The soundtrack is synthesised in Python from the same cut list, so risers, booms and side-chain ducks land exactly on the cuts.

---

## 🎨 Figma wireframes

The full SPI product was wireframed before a line of app code moved. Twenty screens, one board.

<div align="center">
<img src="assets/readme/figma/Roomify-SPI-Wireframes-BOARD.png" alt="Roomify SPI wireframe board" width="100%">
</div>

<details>
<summary><b>All 20 screens — click to expand</b></summary>

<br>

| | |
| --- | --- |
| **01 · Welcome**<br><img src="assets/readme/figma/01-welcome.png" width="100%"> | **02 · Add your room**<br><img src="assets/readme/figma/02-add-your-room.png" width="100%"> |
| **03 · Room profile**<br><img src="assets/readme/figma/03-room-profile.png" width="100%"> | **04 · Free-space cap**<br><img src="assets/readme/figma/04-free-space-cap.png" width="100%"> |
| **05 · Room editor**<br><img src="assets/readme/figma/05-room-editor.png" width="100%"> | **06 · Add furniture**<br><img src="assets/readme/figma/06-add-furniture.png" width="100%"> |
| **07 · Item selected**<br><img src="assets/readme/figma/07-item-selected.png" width="100%"> | **08 · Move and snap**<br><img src="assets/readme/figma/08-move-and-snap.png" width="100%"> |
| **09 · View switcher**<br><img src="assets/readme/figma/09-view-switcher.png" width="100%"> | **10 · Wall view locked**<br><img src="assets/readme/figma/10-wall-view-locked.png" width="100%"> |
| **11 · Aerial view**<br><img src="assets/readme/figma/11-aerial-view.png" width="100%"> | **12 · Replace item**<br><img src="assets/readme/figma/12-replace-item.png" width="100%"> |
| **13 · Sell item**<br><img src="assets/readme/figma/13-sell-item.png" width="100%"> | **14 · Floor cap reached**<br><img src="assets/readme/figma/14-floor-cap-reached.png" width="100%"> |
| **15 · Marketplace ranked**<br><img src="assets/readme/figma/15-marketplace-ranked.png" width="100%"> | **16 · SPI card anatomy**<br><img src="assets/readme/figma/16-spi-card-anatomy.png" width="100%"> |
| **17 · Listing detail**<br><img src="assets/readme/figma/17-listing-detail.png" width="100%"> | **18 · Fit verdicts**<br><img src="assets/readme/figma/18-fit-verdicts.png" width="100%"> |
| **19 · Added to room**<br><img src="assets/readme/figma/19-added-to-room.png" width="100%"> | **20 · Recommendation engine**<br><img src="assets/readme/figma/20-recommendation-engine.png" width="100%"> |

</details>

---

## 🏗 How it works

```
┌──────────────────────────────────────────────────────────────────────┐
│  SCAN                                                                │
│  canvas 2D lidar sim  →  floor m²  ·  wall m²  ·  height  ·  objects  │
└───────────────────────────────┬──────────────────────────────────────┘
                                ▼
┌──────────────────────────────────────────────────────────────────────┐
│  ROOM MODEL            rooms.js · persistence.js                      │
│  dims · wall colours · free-space cap % · placed items · checklist     │
└───────────────┬──────────────────────────────┬───────────────────────┘
                ▼                              ▼
┌──────────────────────────────┐  ┌───────────────────────────────────┐
│  3D EDITOR   scene.js         │  │  SPACE LEDGER      space.js        │
│  three.js r128 · OrbitControls│  │  footprint · wall area · storage   │
│  GLTFLoader · GSAP            │  │  live caps · collision · snapping  │
└──────────────┬────────────────┘  └──────────────┬────────────────────┘
               │                                  ▼
               │                   ┌───────────────────────────────────┐
               │                   │  RECOMMENDATION   recommendation.js│
               │                   │  fits? · efficiency · SPI · rank   │
               │                   └──────────────┬────────────────────┘
               ▼                                  ▼
┌──────────────────────────────────────────────────────────────────────┐
│  CATALOGUES                                                          │
│  market-catalog.js  229 real listings                                │
│  kenney-catalog.js  120 CC0 GLB models                               │
│  catalog.js         parametric custom shapes with modelled cavities  │
└──────────────────────────────────────────────────────────────────────┘
```

No framework, no bundler, no build step. Classic scripts, one global scene, and every file readable on its own.

### Front-end modules

| File | Responsibility |
| --- | --- |
| `js/scene.js` | three.js scene, room geometry, camera presets, wall fading |
| `js/scan-animation.js` | the capture animation — point cloud, sweep ray, dimension labels, object brackets |
| `js/space.js` | the space ledger: footprints, wall area, storage volume, caps, collisions |
| `js/recommendation.js` | fit evaluation, efficiency, SPI scoring, catalogue ranking |
| `js/furniture.js` | spawning, GLB loading + caching, placeholders, surface placement |
| `js/catalog.js` | parametric custom shapes with modelled internal cavities |
| `js/kenney-catalog.js` | 120 CC0 pieces with real-world dimensions and storage volumes |
| `js/market-catalog.js` | 229 real furniture listings with mm dimensions and prices |
| `js/rooms.js` · `js/persistence.js` | room CRUD and local persistence |
| `js/walls.js` · `js/input.js` | wall selection/colouring, pointer picking, drag and snap |
| `js/ui.js` · `js/animations.js` | screens, drawers, modals, micro-interactions |
| `js/profile.js` | account, stats, listings |

---

## 📁 Project structure

```
Roomify_Package/
├── frontend/
│   └── RoomCustomizerWeb/        # the app — open index.html and it runs
│       ├── index.html
│       ├── css/styles.css
│       ├── js/                   # 16 classic scripts, no build step
│       └── assets/kenney/        # 120 GLB furniture models (CC0)
├── backend/
├── data/                         # catalogue + dataset sources
├── notebooks/                    # catalogue preparation
├── kenney_furniture-kit/         # upstream CC0 model kit
├── netlify/                      # ready-to-drop Netlify bundle
│   └── Roomify-Netlify.zip
├── docs/                         # design docs + Figma exports
├── 3D-MODEL-FLOW.md              # how models get from kit to catalogue
└── assets/readme/                # banner, screenshots, wireframes, film
```

---

## 💻 Run it locally

No install, no build, no dependencies. The app is static — but it loads `.glb` models over `fetch`, so it needs a server rather than `file://`.

```bash
git clone https://github.com/yakesh199/roomify.git
cd roomify/frontend/RoomCustomizerWeb

# any static server works
python3 -m http.server 8080
#   or:  npx serve .
```

Then open <http://localhost:8080>.

Sign up with any name and email — accounts and rooms are stored locally in the browser.

---

## 🌐 Deploy to Netlify

A self-contained bundle lives in `netlify/` — **all CDN dependencies vendored**, all 120 GLB models bundled as real files, `index.html` at the zip root.

**Drag and drop**

1. Go to [app.netlify.com/drop](https://app.netlify.com/drop)
2. Drag `netlify/Roomify-Netlify.zip` onto the page
3. Done — it's live.

**From Git**

| Setting | Value |
| --- | --- |
| Build command | *(leave empty)* |
| Publish directory | `frontend/RoomCustomizerWeb` |

`netlify.toml` and `_headers` ship with the bundle — correct MIME type for `.glb`, long-lived caching for models, no caching for `index.html`.

---

## 🗺 Roadmap

- [x] 3D room editor with live floor / wall / storage ledger
- [x] Free-space caps and collision-aware placement
- [x] 120 CC0 GLB models + 229 real listings + parametric custom shapes
- [x] Recommendation engine ranking every catalogue by room fit
- [x] Resell loop — list a placed item, free its space instantly
- [x] Professional capture animation
- [x] Netlify-ready static bundle
- [ ] Real device capture (LiDAR / ARKit / ARCore) replacing the simulation
- [ ] Hosted accounts so a room follows you across devices
- [ ] `roomifyai` embed — partner retailers re-score their own listings
- [ ] Pilot retailer integration
- [ ] Per-category benchmark calibration from live catalogue data

---

## 🙏 Credits

| | |
| --- | --- |
| **3D models** | [Kenney Furniture Kit](https://kenney.nl/assets/furniture-kit) — CC0 1.0 Universal |
| **Catalogue metadata** | Public Amazon furniture dataset — dimensions, brand and price used for research and prototyping |
| **3D engine** | [three.js](https://threejs.org) r128 · OrbitControls · GLTFLoader |
| **Animation** | [GSAP](https://gsap.com) 3.12 |
| **Type** | Fraunces · Inter |
| **Launch film** | Original score, original animation — rendered with Playwright + ffmpeg |

Product photography used during film production comes from research datasets licensed for **non-commercial use**; it is not part of the shipped app.

---

<div align="center">

**Roomify** — because the room should pick the furniture.

<sub>Built by Yakesh · MVP, actively in development</sub>

</div>
