<div align="center">
  <img src="docs/banner.svg" width="100%" alt="Mayank Bhaskar — 3D portfolio, paper schematic banner"/>

  # 🧭 qtjg.github.io

  **A 3D portfolio drawn like a paper schematic — ink, grid paper and one loud signal-orange.**
  One HTML file. Zero build. A real Three.js scene inside.

  [**🚀 LIVE → qtjg.github.io**](https://qtjg.github.io)

  ![three.js](https://img.shields.io/badge/three.js-0.158-161310?style=flat-square&logo=three.js&logoColor=ff4d00&labelColor=ece7dd)
  ![single file](https://img.shields.io/badge/size-one%20HTML%20file-161310?style=flat-square&labelColor=ece7dd)
  ![build](https://img.shields.io/badge/build-none-ff4d00?style=flat-square&labelColor=ece7dd)
  ![deps](https://img.shields.io/badge/deps-0-161310?style=flat-square&labelColor=ece7dd)
  ![pages](https://img.shields.io/badge/hosted%20on-GitHub%20Pages-161310?style=flat-square&logo=github&logoColor=161310&labelColor=ece7dd)

</div>

---

## ⚡ What is this

Most portfolios are a screenshot of a person pretending to be a company. This one is a
**living schematic**: every section is rendered like an engineering drawing — monospaced
annotations, hairline rules, index numbers, and a hand-drawn 3D scene that floats behind
the hero. The palette is strict on purpose: `#ece7dd` paper, `#161310` ink, `#ff4d00`
signal orange. Nothing else is allowed in.

Everything ships in a **single `index.html`** (~50 KB) with zero dependencies and zero
build steps. Fonts and Three.js come from CDN; everything else — the scroll engine, the
3D carousel, the reveal choreography — is hand-rolled vanilla JS in one file.

## 🧊 The 3D layer

Three genuinely 3D things live in this site:

| # | Element | What it does |
|---|---------|--------------|
| 01 | **Schematic hero scene** | A Three.js wireframe assembly — grid plane, ink-solid geometry and an orange beacon — floating in perspective, parallaxing against scroll |
| 02 | **3D ring carousel** | All 10 original builds arranged on a real 3D ring (`rotateY` + `translateZ`). Drag to spin, inertia decays, front card focuses, arrows kick it |
| 03 | **Isometric ghost layer** | Every redesigned section carries an outlined ghost word (CRAFT / GREATS) with scroll parallax, plus a scanline sweep on entry |

The ring, from the inside out:

```text
             ╱▔▔▔▔▔▔▔╱▎
            ╱  ▶ 01 ╱ ╱▎      10 cards · rotateY(i·36°) · translateZ(520px)
           ╱▁▁▁▁▁▁▁╱ ╱▎      drag → velocity → decay ·.94 per frame
           ▏ card  ▏╱        front-focus dims faces > 52° off-axis
           ▏▁▁▁▁▁▁▁▏
```

## 🗺️ Architecture

One request, one file, one `requestAnimationFrame` loop driving everything:

```mermaid
flowchart TD
    A["index.html (~50 KB)"] --> B["intro veil wipe"]
    B --> C["HERO — Three.js schematic scene + typewriter"]
    C --> D["SCROLL ENGINE — one rAF tick"]
    D --> D1["scroll progress bar"]
    D --> D2["hero parallax + fade"]
    D --> D3["velocity skew"]
    D --> D4["scroll-reactive marquee"]
    D --> D5["ring micro-spin (visibility-gated)"]
    D --> D6["ghost watermark parallax ×2"]
    A --> E["IntersectionObserver choreography"]
    E --> F["02 SKILLS — SIGNAL MATRIX<br/>meters fill · ink-sweep hover · scanline"]
    E --> G["03 PROJECTS — 3D ring<br/>drag · inertia · front-focus"]
    E --> H["04 FORKS — GREATS INDEX<br/>sweep rows · ghost · orange indices"]
    E --> I["05 CONTACT — channel buttons"]
```

## ✨ Feature matrix

- **Scroll engine** — one rAF loop: progress bar, hero parallax, velocity-based skew,
  marquee that speeds up and reverses with your scroll, nav scroll-spy + auto-hide
- **SIGNAL MATRIX** — every skill row carries a 5-tick signal meter that fills bar-by-bar
  on reveal; hovering sweeps a full ink band across the row and flips it paper-white
- **Cursor spec-tag** — a terminal readout follows the mouse over skills and forks
  (`SIG 5/5 · TYPESCRIPT`, `FORK 04 · GITHUB/QTJG/TRIVY`)
- **Back-to-top pointer** — 56 px button with a circular SVG progress ring that fills
  with scroll percentage and springs in after 560 px
- **Intro veil** — ink + orange double-panel wipe on load, hero children stagger in behind it
- **Magnetic buttons** — CTA and nav buttons attract toward the cursor
- **Reduced-motion safe** — every animation degrades to a calm static layout via
  `prefers-reduced-motion`

## 🧱 Tech stack

| Layer | Choice | Why |
|-------|--------|-----|
| Rendering | Three.js 0.158 (CDN, ES module) | the only heavy dep; powers hero + ring |
| Type | Bebas Neue · Cormorant Garamond · Jost · IBM Plex Mono | display / serif / body / schematic |
| Motion | hand-rolled rAF engine + IntersectionObserver | no GSAP, no Lenis, no bloat |
| Hosting | GitHub Pages | commit = deploy |

## 📜 Version log

| Ver | Codename | What landed |
|-----|----------|-------------|
| v1 | Starfield | first Three.js hero |
| v2 | Ember Editorial | rose/amber editorial layout (retired — too "AI slop") |
| v3 | Paper Schematic | paper + ink + orange, 3D ring, terminal covers |
| v3.1 | Scroll Engine | parallax, skew, marquee, scroll-spy, reveals |
| v3.2 | Pointer | back-to-top button with circular progress ring |
| v3.3 | Motion Pass | intro veil, magnetic buttons, nav auto-hide, card hover pop |
| v3.4 | Signal Matrix | skills section: meters, ink-sweep, scanline, ghost, spec-tag |
| v3.5 | Greats Index | forks section gets the same signal treatment |
| v3.6 | Channels | YouTube + Discord wired into contact + footer |

## 🚀 Run locally

```bash
git clone https://github.com/qtjg/qtjg.github.io
cd qtjg.github.io
python3 -m http.server 8899
# open http://localhost:8899
```

…or just open `index.html` directly in a browser. There is nothing to install.

## 📡 Channels

<div align="center">

[![YouTube](https://img.shields.io/badge/YouTube-%40indiancybersecurity-ff4d00?style=flat-square&logo=youtube&logoColor=ff4d00&labelColor=161310)](https://www.youtube.com/@indiancybersecurity/videos)
[![Discord](https://img.shields.io/badge/Discord-join%20server-5865F2?style=flat-square&logo=discord&logoColor=5865F2&labelColor=161310)](https://discord.gg/Rk66PWavc)
[![GitHub](https://img.shields.io/badge/GitHub-%40qtjg-161310?style=flat-square&logo=github&labelColor=ece7dd)](https://github.com/qtjg)
[![Twitter](https://img.shields.io/badge/Twitter-%40mayankbhaskarr-161310?style=flat-square&logo=x&labelColor=ece7dd)](https://twitter.com/mayankbhaskarr)

</div>

---

<div align="center">
  <sub><b>DRAWN BY HAND · RENDERED BY THREE.JS · NO AI SLOP</b></sub>
</div>
