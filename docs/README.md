# SmartDesk AI

**Your intelligent workplace wellness companion**

A privacy-first AI assistant that uses only your laptop camera to monitor posture, eye strain, screen distance, ambient lighting, and focus level — and delivers real-time, personalized recommendations instead of generic rule-based alerts.

![Status](https://img.shields.io/badge/status-in%20development-yellow)
![Phase](https://img.shields.io/badge/phase-1%20%7C%20sensing%20layer-blue)
![License](https://img.shields.io/badge/license-MIT-green)

---

## Table of contents

- [Overview](#overview)
- [Why SmartDesk AI](#why-smartdesk-ai)
- [Market opportunity](#market-opportunity)
- [Competitive landscape](#competitive-landscape)
- [Architecture](#architecture)
- [Tech stack](#tech-stack)
- [Repository structure](#repository-structure)
- [Roadmap](#roadmap)
- [Privacy by design](#privacy-by-design)
- [Getting started](#getting-started)
- [Project status](#project-status)
- [License](#license)
- [Acknowledgments](#acknowledgments)

---

## Overview

SmartDesk AI analyzes how you sit, look at your screen, and work — using nothing but the camera already built into your laptop. No wearables, no extra hardware. Every frame is processed **on-device**; nothing is ever sent to a server or stored as raw video.

This project started as a graduation project for an AI Engineering training program, grounded in a full market and competitive analysis (see [`docs/`](./docs)) before any code was written.

## Why SmartDesk AI

Most posture apps stop at "you're slouching, sit up." SmartDesk AI's core bet is different: **the value isn't in catching the mistake, it's in understanding the user well enough to help them build a sustainably healthy work environment.**

Key differentiators identified in our competitive research:

- **Breadth in one model** — posture, eye strain, screen distance, lighting, and focus, where most competitors cover only one or two dimensions.
- **Long-term personalization** — a "Digital Wellness Profile" that adapts to individual patterns over weeks/months, a layer no current competitor offers.
- **Zero extra hardware** — camera-only, unlike wearable posture correctors that suffer from poor long-term adherence.
- **Privacy by design** — fully on-device processing, positioned as a requirement, not a marketing add-on.
- **Clear path to B2B** — architected from day one to extend into an anonymized, aggregated wellness dashboard for HR teams.

## Market opportunity

Sized at the intersection of three overlapping markets (2025–2026 estimates):

| Market segment | Size | Annual growth |
|---|---|---|
| Corporate wellness (overall) | $55.1B – $72.7B | 3.1% – 7.4% |
| Corporate wellness **software** | $1.4B – $3B+ | 7.6% – 14.2% |
| AI-powered wellness platforms | $3.68B (2026) | 7.1% |

Supporting signals: 58% of companies have already adopted AI-driven health analytics, and 53% of deployed platforms include mental-health features — indicating the market is culturally ready for this category. On the caution side, 35% of companies delay wellness platform rollouts over biometric data-misuse concerns, which is why on-device processing is treated as a first-class requirement rather than a nice-to-have.

## Competitive landscape

| Competitor | Posture | Eye/blink | Screen distance | Adaptive learning | Enterprise (B2B) |
|---|:---:|:---:|:---:|:---:|:---:|
| **BLiiNK** (closest competitor) | ✅ | ✅ | ✅ | Limited | ✅ |
| SitApp | ✅ | ❌ | ❌ | Moderate | ❌ |
| Slouch Sniper | ✅ | ❌ | ❌ | Low | ❌ |
| Upright Go / Zikto (wearable) | ✅ | ❌ | ❌ | Low | ❌ |
| Vantage Fit (general wellness) | ❌ | ❌ | ❌ | Low | ✅ |
| **SmartDesk AI (this project)** | ✅ | ✅ | ✅ | **High (digital twin)** | Planned |

BLiiNK is the one direct competitor covering most of the "sensing layer." SmartDesk AI's differentiation is built on the layer above it: long-term adaptive learning and contextual recommendations, not sensing alone.

## Architecture

The system is built in modular layers so each capability can be developed, tested, and improved independently:

1. **Sensing layer** *(Phase 1 — current focus)* — captures camera frames and extracts raw signals: posture, eye strain, and screen distance.
2. **Context layer** *(Phase 2)* — adds ambient lighting and focus estimation, and begins building the adaptive Digital Wellness Profile.
3. **Enterprise layer** *(Phase 3)* — aggregated, anonymized reporting for HR/B2B use cases.

## Tech stack

| Component | Approach |
|---|---|
| Posture estimation | Pose estimation models (MediaPipe / MoveNet) |
| Eye strain / blink detection | Facial landmarks + Eye Aspect Ratio (EAR) |
| Screen distance | Approximated from face size in frame |
| Lighting analysis | Direct camera/screen pixel analysis |
| Focus estimation | Gaze direction + fixation duration + usage patterns |
| Adaptive learning (digital twin) | Per-user sequential model, on-device fine-tuning |

## Repository structure

```
smartdesk-ai/
├── docs/              # Market analysis, roadmap, and research sources
├── src/
│   ├── sensing_layer/ # Phase 1 — posture, eye strain, screen distance
│   ├── phase2_context/# Phase 2 — lighting, focus, digital wellness profile
│   └── phase3_enterprise/ # Phase 3 — B2B reporting dashboard
├── notebooks/         # Model experimentation notebooks
├── models/            # Trained model artifacts
├── tests/             # Unit tests
├── requirements.txt
├── README.md
└── LICENSE
```

## Roadmap

- [ ] **Phase 1 — MVP (0–3 months):** posture + eye strain + screen distance, fully on-device.
- [ ] **Phase 2 — Differentiation (3–6 months):** lighting + focus, first version of the Digital Wellness Profile, limited beta.
- [ ] **Phase 3 — Enterprise expansion (6–12 months):** B2B dashboard with anonymized, aggregated HR reporting.

**Success metrics (KPIs):** 30-day user retention, model accuracy vs. published benchmarks, number of pilot companies in the first 6 months of the B2B program.

## Privacy by design

- All video processing happens **on-device**. No raw frames are ever uploaded or stored.
- Only derived metrics (e.g. a posture score) are persisted, never images.
- For any future enterprise (B2B) version, employee consent will be explicit and separate from general company policy — addressing the ~48% of employees who report discomfort sharing health data with employers.

## Getting started

> This project is in early development (Phase 1). Setup instructions will be added here as the sensing layer becomes runnable.

```bash
git clone https://github.com/<your-username>/smartdesk-ai.git
cd smartdesk-ai
pip install -r requirements.txt
```

## Project status

🚧 **Actively in development — Phase 1 (Sensing Layer).**

## License

Distributed under the MIT License. See [`LICENSE`](./LICENSE) for details.

## Acknowledgments

Market and competitive research compiled from Grand View Research, Precedence Research, Coherent Market Insights, Tracxn, and direct competitor analysis (BLiiNK, SitApp, Slouch Sniper, Upright Go). Full source list available in [`docs/`](./docs).
