# HEALTH-E Architecture

## 1. Visual System
All pages share a unified warm-space palette:
- **Background:** `#1a1310` / `#0f0a08`
- **Primary Accent (Mars Rust):** `#C14424`
- **Secondary Accent (Sand):** `#D3BBA0`
- **Text (Cream):** `#F0E7D4`
- **Typography:** `Fraunces` (display), `Inter` (UI/body), `JetBrains Mono` (telemetry/markers)

## 2. Anomaly Detection Engine (`Analysis.html`)
The telemetry scanner evaluates each metric using a 15-sample rolling window (`WINDOW = 15`) combined with physiological threshold guards:

| Metric | Low Threshold | High Threshold | Z-Score Cutoff |
| :--- | :--- | :--- | :--- |
| `heart_rate` (bpm) | `< 45` | `> 120` | `|z| >= 2.5` |
| `spo2` (%) | `< 92` | `—` | `|z| >= 2.5` |
| `body_temp` (°C) | `< 35.5` | `> 38.0` | `|z| >= 2.5` |
| `co2_ppm` (ppm) | `—` | `> 2500` | `|z| >= 3.0` |

A 3-sample cooldown (`i - lastIndex <= 3`) prevents duplicate alerts on sustained spikes.

## 3. Crew Diagnostic Rules (`Monitoring.html`)
Evaluates crew metrics against NASA-STD-3001 operational thresholds across four domains:
1. **Neuro-Ocular (SANS):** `ONSD > 6.0 mm` or `retinal > 50 µm`
2. **Hemodynamic / Fluid:** `HR > 90 bpm` or `mass Δ < -2.0%`
3. **Musculoskeletal / Renal:** `urinary calcium > 250 mg/day`, `CTX > 100%`, or `ARED < 85%`
4. **Circadian / Cognitive:** `sleep < 5.0 hrs`, `PVT > 350 ms`, or `cortisol > 12.0 ng/mL`
