# AakashRakshak (आकाश रक्षक)
### AI-Enabled Drone & Counter-Drone Threat Simulation Trainer
**Smart India Hackathon 2026 — Problem Statement PS 26247 (Ministry of Defence)**

[![Vite](https://img.shields.io/badge/Vite-6.2-646CFF?logo=vite&logoColor=white)](#)
[![React](https://img.shields.io/badge/React-19.0-61DAFB?logo=react&logoColor=black)](#)
[![Three.js](https://img.shields.io/badge/Three.js-3D_WebGL-black?logo=three.js)](#)
[![Chart.js](https://img.shields.io/badge/Chart.js-4.4-FF6384?logo=chart.js&logoColor=white)](#)
[![TypeScript](https://img.shields.io/badge/TypeScript-5.7-3178C6?logo=typescript&logoColor=white)](#)
[![Tests](https://img.shields.io/badge/Tests-5%20Passed-10B981)](#)
[![Offline Ready](https://img.shields.io/badge/Deployment-100%25_Offline-00E5FF)](#)

> **MANDATORY NOTICE: DEMO - simulated data only.**  
> Fictional, generic models and illustrative algorithms. All unit designations and operational parameters are synthetic for simulation and training purposes.

---

## 1. Overview & System Goal

**AakashRakshak** is a zero-latency, offline tactical counter-unmanned aerial systems (C-UAS) simulation trainer built for laptops and training workstations. It provides an end-to-end training pipeline for operators:

1. **Target Acquisition:** Trainee watches a simulated 3D operational airspace and 2D sweep radar, acquires approaching drone contacts, and marks them (recording millisecond-accurate detection reaction time).
2. **Visual & Sensor Classification:** Trainee zooms in with optical optics to inspect aerodynamic silhouettes, classifying contacts into:
   - **Quadcopter** (commercial rotary-wing)
   - **Fixed-Wing UAV** (high-speed delta/swept wings)
   - **Loitering Type** (canards and seeker nose)
   - **Bird Decoy** (avian decoy with flapping motion)
   - **Friendly Drone** (blue IFF strobe beacon)
   - **Unknown / Unverified**
3. **Threat Assessment:** Trainee designates threat severity (`LOW`, `MEDIUM`, `HIGH`).
4. **Tactical Response:** Trainee selects an appropriate operational response (`OBSERVE`, `REPORT UP CHAIN`, `JAM (RF / EW)`, `ENGAGE (SIMULATED)`).
5. **Explainable Scoring Debrief:** Trainee audits a transparent decision tree walk-through showing why each point was awarded or deducted.
6. **After-Action Review (AAR):** Comprehensive review with replay timeline slider, Chart.js progress graph, identified focus areas, and unit benchmark table.
7. **Rule-Based Adaptive Progression:** Evaluates trainee trajectory (average score >80% escalates difficulty; <50% lowers difficulty; targets weakest skill category).

---

## 2. Quick Start & Execution Commands

### Prerequisites
- Node.js (v18+ or v20+ recommended)
- Modern web browser (Chrome, Edge, Firefox, Brave)
- Runs **100% OFFLINE** without any runtime internet calls or external CDNs.

### Installation
```bash
# Clone the repository
git clone https://github.com/chetan563-Data/Akash-Rakshak.git
cd Akash-Rakshak

# Install bundled dependencies
npm install
```

### Run Locally (Development Dev Server)
```bash
npm run dev
```
Open [http://localhost:5173/](http://localhost:5173/) in your web browser.

### Run Unit Tests (5 Scoring Decision Tree Test Cases)
```bash
npm test
```
All 5 decision tree rules and adaptive escalation test cases execute and validate via `vitest`.

### Production Build
```bash
npm run build
```
Generates an optimized, self-contained offline production bundle in `dist/`.

To preview the production build locally:
```bash
npm run preview
```

### Deployment (e.g. Vercel)
- Framework Preset: **Vite**
- Build Command: `npm run build`
- Output Directory: `dist`
- Install Command: `npm install`

---

## 3. Modular Architecture & Folder Map

The application follows a strictly modular architecture across 7 core functional domains:

```
akashrakshak/
├── src/
│   ├── types.ts                      # Universal domain interfaces & data contracts
│   ├── index.css                     # Tactical Military Dark Vanilla CSS design system
│   ├── main.tsx                      # React root mounter
│   ├── App.tsx                       # State machine (Home -> Sim -> Debrief -> AAR)
│   │
│   ├── scenario/                     # SCENARIO ENGINE
│   │   ├── scenarios.ts              # 3 Scripted Scenarios + Practice Range
│   │   └── ScenarioGenerator.ts      # Deterministic Mulberry32 PRNG Procedural Generator
│   │
│   ├── simulation/                   # SIMULATION CORE
│   │   ├── SceneManager.ts           # Three.js 3D world, day/night lighting, hills, raycaster
│   │   ├── DroneModelFactory.ts      # Procedural 3D models (Quadcopter, Fixed-Wing, etc.)
│   │   ├── RadarView.tsx             # 2D CRT tactical sweep radar with sensor degradation
│   │   ├── BoidsSwarm.ts             # Separation, Alignment, Cohesion & Goal pursuit flocking
│   │   └── SimulationContainer.tsx   # Central simulation container & time management
│   │
│   ├── scoring/                      # SCORING ENGINE
│   │   ├── scoringConfig.ts          # Plain configuration file with illustrative weights
│   │   ├── ScoringEngine.ts          # Decision tree evaluator & adaptive recommendations
│   │   └── ScoringEngine.test.ts     # Vitest unit tests for 5 hand-made test cases
│   │
│   ├── logger/                       # AUDIT TRAIL & DECISION LOGGER
│   │   └── ActionLogger.ts           # Event logging, LocalStorage persistence & Excel CSV export
│   │
│   ├── aar/                          # AFTER-ACTION REVIEW (AAR) DASHBOARD
│   │   ├── AARDashboard.tsx          # Replay timeline, Chart.js progress graph, unit view
│   │   └── SampleData.ts             # 5 Seeded unit benchmark profiles ("Sample data")
│   │
│   ├── tutorial/                     # TUTORIAL & CHEAT SHEET
│   │   ├── TutorialOverlay.tsx       # 6-step interactive first-run tour
│   │   └── CheatSheetModal.tsx       # 1-page quick reference (controls, silhouettes, grades)
│   │
│   └── ui/                           # USER INTERFACE
│       ├── HomeView.tsx              # Scenario selection, adaptive status, instructor override
│       ├── SimHeader.tsx             # Tactical HUD header, clock, time controls (pause, 1x, 2x)
│       ├── ContactActionModal.tsx    # Mark, Classify [1-6], Threat, and Response controls
│       ├── ActionLogPanel.tsx        # Live audit trail feed with direct CSV download
│       └── ScoreModal.tsx            # "Why this score?" decision tree debrief screen
│
├── package.json
├── vite.config.ts
├── tsconfig.json
├── USER_TUTORIAL.md                  # Plain-English trainee guide
├── DEMO_SCRIPT.md                    # 3-Minute demonstration script for Hackathon judges
└── README.md                         # This file
```

---

## 4. Scenarios & Procedural Generator

### 3 Scripted Scenarios
1. **"Lone Scout" (SCEN-01):** 1 commercial quadcopter conducting low-level sector reconnaissance. Daytime, rural outpost, clear visibility. (Duration: 45s, Difficulty: Easy).
2. **"Night Approach" (SCEN-02):** 2 hostile drones (fixed-wing and loitering) plus 1 bird decoy approaching under night cover with light fog degrading electro-optical sensors. (Duration: 60s, Difficulty: Medium).
3. **"Swarm Raid" (SCEN-03):** Coordinated 10-drone swarm with Boids flocking rules attacking urban airspace, plus 1 friendly drone in sector. (Duration: 75s, Difficulty: Hard).
4. **"Practice Range" (PRACTICE):** 1 slow drone for beginner drills with guidance hints and zero scoring rush.

### Deterministic Procedural Generator
- Takes any integer seed (e.g. `#4242`) and generates a reproducible scenario using the **Mulberry32 PRNG**.
- Randomizes: time of day, fog/visibility, terrain (urban or rural), number of drones (1 to 15), drone types, approach direction, speed, and decoys (birds, friendly drones).
- **Reproducibility Guarantee:** The exact same seed always produces the exact same scenario for repeatable comparison between trainees.

---

## 5. Scoring Engine & Configurable Weights

All scoring weights and rules are stored in a single, transparent, and auditable configuration file:  
**[`src/scoring/scoringConfig.ts`](file:///c:/Users/Chetan/Downloads/akashrakshak/src/scoring/scoringConfig.ts)**

### Configuration Preview
```typescript
export const SCORING_CONFIG: ScoringWeightsConfig = {
  disclaimer: 'Illustrative weights - not from real doctrine',

  detection: {
    maxPoints: 25,
    fastThresholdMs: 5000,   // Benchmark: < 5.0 seconds (+25 pts)
    okThresholdMs: 12000,    // Acceptable: 5.0 - 12.0 seconds (+18 pts)
    slowPoints: 10,          // Delayed: > 12.0 seconds (+10 pts)
    missedPenalty: 25,       // Penalty if target crosses airspace unmarked
  },

  classification: {
    correctPoints: 30,       // Points for accurate identification
    wrongPenalty: 15,        // Penalty for misidentifying contact
  },

  threatLevel: {
    correctPoints: 20,
    reasonablePoints: 10,
    unreasonablePenalty: 10,
    groundTruthExpectations: {
      quadcopter: ['medium', 'high'],
      fixed_wing: ['high'],
      loitering: ['high'],
      bird: ['low'],
      friendly: ['low'],
    },
  },

  response: {
    correctPoints: 25,
    acceptablePoints: 12,
    friendlyOrDecoyEngagementSeverePenalty: 40, // Severe penalty for firing on friendlies/birds
    appropriateResponses: {
      quadcopter: { recommended: ['jam', 'report'], acceptable: ['observe'], prohibited: [] },
      fixed_wing: { recommended: ['report', 'jam', 'engage'], acceptable: ['observe'], prohibited: [] },
      loitering:  { recommended: ['jam', 'engage', 'report'], acceptable: ['observe'], prohibited: [] },
      bird:       { recommended: ['observe'], acceptable: ['report'], prohibited: ['engage', 'jam'] },
      friendly:   { recommended: ['observe', 'report'], acceptable: [], prohibited: ['engage', 'jam'] },
    },
  },

  gradeBands: {
    exemplary: 85,  // >= 85
    proficient: 70, // >= 70
    qualified: 50,  // >= 50
    remedial: 0,    // < 50
  },
};
```

---

## 6. Controls & Keyboard Shortcuts

| Shortcut | Action | Description |
|---|---|---|
| **Left Click + Drag** | Look / Pan / Tilt | 360° horizontal azimuth and -30° to +60° vertical elevation |
| **Mouse Wheel** | Optical Zoom | Adjusts camera field of view (FOV 60° down to 18° 3x magnification) |
| **Space** | Pause / Resume | Toggle simulation clock between paused and running |
| **M** | Mark Contact | Instantly marks selected contact and logs detection timestamp |
| **1** | Quadcopter | Classifies contact as commercial quadcopter |
| **2** | Fixed-Wing | Classifies contact as fixed-wing UAV |
| **3** | Loitering | Classifies contact as loitering munition |
| **4** | Bird Decoy | Classifies contact as avian bird decoy |
| **5** | Friendly | Classifies contact as friendly drone (blue IFF strobe) |
| **6** | Unknown | Classifies contact as unverified |
| **Esc** | Close Panel | Dismisses active contact action panel |

---

## 7. Known Limits & Disclaimers

In accordance with Hackathon specifications (PS 26247, Ministry of Defence):

1. **Simulated Data & Content:** All data, 3D meshes, unit designations, and scenarios are fictional and generic. No real unit names, real coordinates, real weapon models, or classified military data are used.
2. **Simplified Sensor Physics:** The 2D radar and 3D vision simulate degraded sensors (optical fog attenuation, radar noise clutter, and blip dropouts) using heuristic mathematical models rather than true electromagnetic wave propagation or radar cross-section (RCS) solver equations.
3. **Illustrative Doctrine Weights:** The decision tree scoring weights and response recommendations represent educational training benchmarks for hackathon demonstration, not certified Indian Armed Forces doctrine.
4. **Simplified Boids Flocking:** Swarm dynamics employ standard Reynolds Boids algorithms (Separation, Alignment, Cohesion, Goal Pursuit) tuned for 60 fps laptop performance, rather than military-grade multi-agent autonomous swarm communications.
5. **No Internet / Backend Dependency:** The simulator is engineered to run completely offline in the user's browser using localStorage and client-side processing. No telemetry or audio-video feeds leave the machine.
