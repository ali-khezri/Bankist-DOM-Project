# Bankist — Minimalist Banking Landing (HTML / CSS / JS)

A beautiful, modern landing page / demo site for a minimalist banking product.  
This repository contains a static frontend (HTML, CSS, vanilla JS) with a few progressive features:

- sticky navigation, reveal-on-scroll, lazy images (Intersection Observer)
- modal window, tabbed operations, slider (testimonials)
- small build-aware image helper (script uses `import` for assets if you build with a bundler)

> ⚠️ **Important** — the provided `script.js` contains `import` statements for images:
> ```js
> import digital from './img/digital.jpg';
> import grow from './img/grow.jpg';
> import card from './img/card.jpg';
> ```
> Those imports require a bundler (Parcel / Vite / webpack). If you just open `index.html` in the browser (file://), the imports will fail. See **Run / Dev** below for two ways to run this project.

---

## Demo
You can add a hosted demo URL here (replace the placeholder):

**Live demo:** `https://bankist-dom-project-ali-khezri.netlify.app/`  

(Or use the steps below to run locally.)

---

## Features
- Fully responsive landing page layout
- Smooth scrolling, sticky header and menu fade animation
- Lazy-loading images with blur-up effect
- Testimonials slider with keyboard support & dots
- Modal signup form
- Accessible-friendly design considerations (mostly presentational demo)

---

## Repo structure
````

.
├── index.html        # Main HTML
├── style.css         # All styles
├── script.js         # App logic (modal, slider, lazy-load, sticky nav, etc.)
├── img/              # Images (digital.jpg, grow.jpg, card.jpg, hero.png, user-*.jpg, icons.svg, ...)
└── README.md

````

---

## Quick start

Choose one of the two recommended ways to run the project:

### Option A — Plain static (no bundler)
If you want to run the site as a simple static site (open `index.html` or serve files), you must **remove the ES module imports** from `script.js` and use static image paths. Replace the top of `script.js`:

```js
// Remove or comment out these lines:
// import digital from './img/digital.jpg';
// import grow from './img/grow.jpg';
// import card from './img/card.jpg';

// Add a static map (relative to index.html):
const imagesMap = {
  digital: '/img/digital.jpg',
  grow: '/img/grow.jpg',
  card: '/img/card.jpg',
};
````

Save and then either:

* Open `index.html` in your browser (double-click), or
* Start a tiny static server (recommended) to avoid `file://` issues:

```bash
# using npx serve (no install)
npx serve .

# or using Python 3
python -m http.server 8000
# then open http://localhost:8000
```

### Option B — Run with a bundler (recommended if you want the original script with imports)

This keeps the `import` lines (so image imports are resolved and you get a nicer dev workflow).

**Using Parcel**

```bash
# 1. initialize
npm init -y

# 2. install parcel
npm install --save-dev parcel

# 3. update package.json scripts:
#    "scripts": {
#       "dev": "parcel index.html",
#       "build": "parcel build index.html --public-url ./"
#    }

# 4. run dev server
npm run dev
# open the URL printed by parcel (usually http://localhost:1234)
```

**Using Vite** (alternative):

```bash
npm init @vitejs/app
# choose vanilla (or vanilla-js) when prompted
# move files into the Vite project, then:
npm install
npm run dev
```

---

## Deploy to GitHub Pages

1. Build (if using a bundler): `npm run build`
2. Push the generated `dist` (Parcel) or `build` folder to the `gh-pages` branch, or configure GitHub Actions to deploy.
3. Or, simply push the repo and enable **GitHub Pages** from `main` / `gh-pages` branch in repository settings if you serve static root files.

A quick automatic deploy example (using `gh-pages` package):

```bash
npm install --save-dev gh-pages
# add to package.json scripts:
# "predeploy": "npm run build",
# "deploy": "gh-pages -d dist"
# then
npm run deploy
```

---

## Customization & notes

* The script uses `IntersectionObserver` for lazy loading and revealing sections. You can tweak thresholds / root margins in `script.js`.
* To replace demo images, put your files in `img/` and ensure names match those expected (or update `imagesMap`).
* If you prefer not to use any bundler, use **Option A** above and change `script.js` to reference static paths.

---

## Author

**Ali Khezri** — [Ali Khezri](https://github.com/ali-khezri) | [LinkedIn](https://www.linkedin.com/in/ali-khezri)

---
