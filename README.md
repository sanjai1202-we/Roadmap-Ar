# 🎯 Annai Mira AR Roadmap

> **Augmented Reality career roadmap explorer** — point your phone at a department logo and instantly watch an immersive video roadmap appear in AR.

[![Live Demo](https://img.shields.io/badge/Live%20Demo-GitHub%20Pages-black?style=for-the-badge&logo=github)](https://your-github-username.github.io/Roadmap-Ar/)
[![PWA Ready](https://img.shields.io/badge/PWA-Ready-5A0FC8?style=for-the-badge&logo=pwa)](https://web.dev/progressive-web-apps/)
[![AR Powered](https://img.shields.io/badge/AR-MindAR%20%2B%20A--Frame-00D8FF?style=for-the-badge)](https://hiukim.github.io/mind-ar-js-doc/)
[![No Backend](https://img.shields.io/badge/Backend-None%20Required-brightgreen?style=for-the-badge)](https://github.com/)

---

## 📸 What It Does

Annai Mira AR Roadmap is a **100% browser-based Augmented Reality web app** that transforms physical department logos into interactive career guides. Students simply scan a logo with their phone camera and a department-specific career roadmap video overlays in AR — no app install needed.

| Feature | Details |
|---|---|
| 📷 Image target recognition | Detects 6 department logos in real-time |
| 🎬 AR video overlay | Plays roadmap video anchored to the physical logo |
| 📱 Full-screen player | Custom controls — seek, speed (0.5×–2×), mute |
| 🌐 Zero-install | Runs entirely in the browser via WebAR |
| 🎨 Premium UI | Bebas Neue + Outfit typography, gold dark-mode aesthetic |

---

## 🏫 Supported Departments

| Department | Abbreviation | Color |
|---|---|---|
| Information Technology | IT | Purple |
| Artificial Intelligence | AI | Orange |
| Computer Science Engineering | CSE | Indigo |
| Electrical & Electronics | EEE | Green |
| Electronics & Communication | ECE | Red |
| Master of Business Administration | MBA | Blue |

---

## 🛠️ Tech Stack

```
MindAR.js (v1.2.5)   →  Image-target AR tracking
A-Frame (v1.4.2)      →  3D/AR scene rendering  
Vanilla JS            →  App logic, UI, page navigation
CSS Custom Properties →  Theming & responsive layout
GitHub Pages          →  Zero-cost static hosting
```

**No React. No Node. No backend. No app store.** Just a single HTML file deployed statically.

---

## 🚀 Getting Started

### Run Locally

```bash
git clone https://github.com/sanjai1202-we/Roadmap-Ar.git
cd Roadmap-Ar

# Serve with any static server (HTTPS required for camera access)
npx serve .
# or
python -m http.server 8080
```

> ⚠️ **HTTPS is mandatory** for camera/WebXR APIs. Use `localhost` or deploy to HTTPS.

### Deploy to GitHub Pages

1. Push repo to GitHub
2. Go to **Settings → Pages → Source: main branch / root**
3. Visit `https://your-username.github.io/Roadmap-Ar/`

---

## 📁 Project Structure

```
Roadmap-Ar/
├── index.html        # Entire app — single HTML file
├── targets.mind      # Compiled AR image targets (MindAR format)
├── it.mp4            # IT department roadmap video
├── ai.mp4            # AI department roadmap video
├── cse.mp4           # CSE department roadmap video
├── eee.mp4           # EEE department roadmap video
├── ece.mp4           # ECE department roadmap video
└── mba.mp4           # MBA department roadmap video
```

---

## 🏗️ Architecture & Key Decisions

### Why a Single HTML File?
- **Zero deployment complexity** — works on any static host (GitHub Pages, Netlify, Vercel)
- **No build step** — iterate and ship instantly
- **Offline-capable** — assets cached by browser after first load

### AR Pipeline
```
Camera feed (getUserMedia)
    ↓
MindAR image tracker (WASM-powered neural net)
    ↓
Target match → A-Frame entity show/hide
    ↓
Overlay video anchored to physical marker
    ↓
User taps "OPEN VIDEO" → full-screen custom player
```

### UI Architecture — 3-Page SPA
| Page | Description |
|---|---|
| **Home** | College branding, department pills, CTA |
| **Scanner** | Live AR camera view with target detection |
| **Video Player** | Full-screen playback with custom controls |

Page transitions use CSS `opacity` + `transform` with no framework overhead.

---

## ✨ Features in Detail

### AR Scanner
- Real-time logo detection using MindAR's neural image tracker
- Department badge appears on recognition with color-coded indicator
- Preview panel shows department name before opening full video
- Animated scan-line + corner-frame UI for camera guidance

### Custom Video Player
- **Seek bar** with touch-drag support
- **Playback speed** cycling: 0.5× → 0.75× → 1× → 1.25× → 1.5× → 2×
- **±10s skip** buttons
- **Mute/unmute** toggle
- Tap-to-play/pause on video area
- Live time display (current / duration)

### UI/UX Highlights
- `--gold: #f5c842` accent system throughout
- Bebas Neue display font for headings
- Outfit variable font for body text
- Responsive via `clamp()` — works from 320px to desktop
- `env(safe-area-inset-*)` for iPhone notch/home bar

---

## 🔧 How to Add a New Department

**Step 1 — Add your logo** to the `targets.mind` file  
*(Regenerate using [MindAR image target compiler](https://hiukim.github.io/mind-ar-js-doc/tools/compile))*

**Step 2 — Add video** as `deptname.mp4` to the root directory

**Step 3 — Register in `index.html`**:
```javascript
// Add to TARGETS array
{idx: 6, id: 'target-mech', src: 'mech.mp4', name: 'Mechanical Engineering', color: '#f59e0b'},
```

**Step 4 — Add a pill** in the Home page HTML:
```html
<span class="pill pill-mech">MECH</span>
```

---

## 📱 Browser Support

| Browser | AR Support |
|---|---|
| Chrome Android | ✅ Full |
| Safari iOS (16.4+) | ✅ Full |
| Chrome Desktop | ✅ (webcam) |
| Firefox | ⚠️ Limited WebXR support |

**Minimum requirements:** HTTPS, camera permission, WebGL 2.0

---

## 🎨 Design System

```css
/* Color Tokens */
--gold:   #f5c842   /* Primary accent */
--dark:   #0a0a0f   /* Background */
--card:   #12121a   /* Surface */
--text:   #f0eee8   /* Body text */
--muted:  rgba(240,238,232,0.45)

/* Typography */
font-family: 'Bebas Neue'   /* Display headings */
font-family: 'Outfit'       /* Body & UI */
```

---

## 🙋 Built By

**Sanjai** — B.Tech IT, Annai Mira College of Engineering & Technology, Ranipet, Tamil Nadu

> This project was built as part of real-world AR application development exploring **no-install WebAR**, computer-vision-driven UI, and performance-optimized single-file web apps.

**Connect:**
- 🔗 [LinkedIn](https://linkedin.com/in/your-profile)
- 💻 [GitHub](https://github.com/your-username)
- 🌐 [Portfolio](https://nimble-clafoutis-b9bef2.netlify.app)

---

## 📄 License

MIT License — free to use, modify, and deploy.

---

<div align="center">
  <sub>Built with MindAR · A-Frame · Vanilla JS · Deployed on GitHub Pages</sub>
</div>
