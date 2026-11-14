# HEALTH-E · Bio-Orbit Telemetry & Space Physiology Explorer

[![NASA Space Apps Cairo 2026](https://img.shields.io/badge/NASA_Space_Apps-Cairo_2026-C14424?style=for-the-badge)](https://www.spaceappschallenge.org/)
[![Live Demo](https://img.shields.io/badge/Live_Demo-Vercel-0f0a08?style=for-the-badge&logo=vercel)](https://nasa-health-e-sable.vercel.app/)
[![License: MIT](https://img.shields.io/badge/License-MIT-D3BBA0?style=for-the-badge)](LICENSE)

> **Your body was built for Earth. Space has other plans.**  
> Built by **Team MYTHs** for the **NASA Space Apps Cairo 2026 — Astronauts Health Challenge**.

🌐 **Live Deployment:** [https://nasa-health-e-sable.vercel.app/](https://nasa-health-e-sable.vercel.app/)

---

## Overview

**HEALTH-E** is a zero-build, browser-native web application that translates dense spaceflight biomedical research into an interactive, dual-audience experience. With a single global **Curious / Researcher** toggle, every page adapts live between accessible analogies for students and citation-backed physiological metrics for researchers.

### Core Modules

| Module | File | Description |
| :--- | :--- | :--- |
| **Landing & 3-Act Storytelling** | [`index.html`](index.html) | Interactive 3D astronaut hero (`Astronaut.glb` via Three.js), a 7-stage physiological simulator, and a three-act scrollytelling journey (*Terrestrial Harmony*, *The Making of an Astronaut*, *Body in Freefall*). |
| **Crew Health Monitor** | [`Monitoring.html`](Monitoring.html) | Real-time ECLSS crew diagnostics dashboard tracking cardiovascular, neuro-ocular (SANS), musculoskeletal, and circadian biomarkers with autonomous **NASA-STD-3001** countermeasure protocols. |
| **Telemetry Anomaly Analysis** | [`Analysis.html`](Analysis.html) | 100% client-side CSV telemetry parser and live anomaly scanner combining a rolling-window **Z-score** detector with physiological threshold guards for `heart_rate`, `spo2`, `body_temp`, and `co2_ppm`. |

---

## Repository Structure

```text
health-e-nasa-space-apps/
├── index.html             # Landing, 3D astronaut hero, 7-stage simulator & 3-act story
├── Monitoring.html        # Crew health & ECLSS diagnostic dashboard
├── Analysis.html          # Local CSV telemetry upload & Z-score anomaly detection
├── Astronaut.glb          # Custom 3D astronaut asset (GLB)
├── docs/
│   └── ARCHITECTURE.md    # Technical architecture, detection rules & data sources
├── vercel.json            # Static hosting & clean URL configuration
├── package.json           # Local dev script convenience wrapper
├── CONTRIBUTING.md        # Contribution & code style guidelines
├── .gitignore             # Ignored OS, editor, and build artifacts
├── LICENSE                # MIT License
└── README.md              # Project documentation
```

---

## Getting Started

Because HEALTH-E uses **Vanilla HTML, CSS, and ES Modules** (with Three.js loaded via import map), no bundler or build step is required. However, because `GLTFLoader` fetches `Astronaut.glb` over HTTP, you should serve the folder with a local static server rather than opening `index.html` via `file://`.

### Option 1: Using Node.js (`npx serve`)

```bash
git clone https://github.com/<MoeSalah020>/health-e-nasa-space-apps.git
cd health-e-nasa-space-apps
npm run dev
```

### Option 2: Using Python

```bash
python3 -m http.server 8080
```

Then open [http://localhost:8080](http://localhost:8080) in your browser.

---

## Key Features

- **Dual-Audience Reading Mode (`Curious` / `Researcher`):** Synchronized across all pages via `localStorage` (`healthEMode`), switching copy and clinical terminology in real time without page reloads.
- **Interactive 3D & Canvas Visualizations:**
  - Three.js `0.160.0` hero scene with custom Fresnel rim-light shader, hover vibration, and scroll choreography.
  - Custom HTML5 Canvas physiological overlays, bar charts, and animated telemetry scrubbers.
- **Privacy-First Local CSV Analysis:** Drag-and-drop any telemetry CSV onto `Analysis.html` (or download the built-in 96-row sample CSV) — all parsing and Z-score calculations run locally in the browser.

---

## Scientific References

- **NASA Human Research Program (HRP):** Cardiovascular, Musculoskeletal, Fluid Shifts / SANS, and Sensorimotor risk roadmaps.
- **NASA-STD-3001:** Space Flight Human-System Standard operational thresholds.
- **NASA GeneLab & ISS Life Sciences:** Gut microbiome drift, ARED resistive countermeasures, and Veggie / APH crop studies.

---

## Team MYTHs

Built for **NASA Space Apps Cairo 2026** — *Astronauts Health Challenge*.

## License

This project is licensed under the [MIT License](LICENSE).
