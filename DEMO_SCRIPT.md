# AakashRakshak: 3-Minute Hackathon Demonstration Script
**Smart India Hackathon 2026 — Problem Statement PS 26247 (Ministry of Defence)**

> **Target Audience:** Hackathon Judges & Defence Technical Evaluators  
> **Total Time:** Exactly 3 Minutes (180 Seconds)  
> **Setup:** Laptop running `http://localhost:5173/` (Zero internet required, 100% offline).

---

### [0:00 - 0:30] Introduction & Problem Context (30 seconds)
**Presenter says:**
> *"Respected Judges, modern battlefield airspace is saturated with asymmetric micro-UAS, decoy swarms, and electronic warfare clutter. Problem Statement 26247 asks for an AI-enabled simulation trainer that trains air defence operators to detect, classify, and neutralize drone threats—and then learn from their mistakes.*
>
> *This is **AakashRakshak**. It runs **100% offline** in any standard browser without any backend servers or external dependencies. Notice our mandatory safety tag: 'DEMO - simulated data only'. Everything you see is fictional, modular, and built on high-performance Three.js and React."*

---

### [0:30 - 1:15] Live Simulation: Detection, Classification & Response (45 seconds)
**Presenter does:**
1. Click **Lone Scout** (or **Night Approach**) and click **START SIMULATION**.
2. Drag the 3D scene 360° to show the observation post and hills.
3. Point to the **2D Radar** in the bottom-right corner showing rotating CRT sweeps with sensor noise.
4. Spot the approaching contact, click on the radar blip (or press **[M]**).
5. Open the action panel:
   - Point to the millisecond detection timestamp recorded in real-time.
   - Press **[1]** or click **Quadcopter** to classify.
   - Set threat level to **MEDIUM THREAT**.
   - Click **JAM (RF / EW)**. Show the purple electronic warfare disruption aura in 3D as the drone loses lift.
   - Point to the live **Audit Trail / Action Log** in the bottom-left corner and click the **CSV** export button to show compliance with military record-keeping.

**Presenter says:**
> *"As the operator spots the target, pressing 'M' logs their detection reaction time down to the millisecond. They optically classify the silhouette, assign a threat rating, and execute an authorized countermeasure—such as soft-kill RF jamming. Every single decision is committed into an immutable local audit log that exports directly to Excel."*

---

### [1:15 - 2:00] Explainable Decision Tree: "Why This Score?" (45 seconds)
**Presenter does:**
1. Click **END SESSION & SCORE** in the header.
2. The **"Why this score?"** debrief screen appears.
3. Show the overall score (e.g., `85/100 - EXEMPLARY`).
4. Point to the mandatory label: *"Illustrative weights - not from real doctrine"*.
5. Walk through the checklist for the contact:
   - Green tick: Target Detection (<5.0s rapid acquisition)
   - Green tick: Accurate Classification (Quadcopter match)
   - Green tick: Appropriate Threat Assessment
   - Green tick: Tactical ROE Compliance (authorized countermeasure)
6. Point to the penalty rules:
   - Explain how firing on a bird decoy or friendly drone immediately triggers a critical -40 point deduction.

**Presenter says:**
> *"Instead of a black-box neural net score, AakashRakshak features an **explainable decision tree**. For every contact, the trainee sees an auditable checklist with green ticks and red crosses. They understand precisely why they earned 85 points and how their reaction time influenced their grade."*

---

### [2:00 - 2:40] After-Action Review (AAR) & Unit Benchmark (40 seconds)
**Presenter does:**
1. Click **OPEN FULL AAR DASHBOARD**.
2. Show the **Chart.js Trainee Score Trajectory** showing performance across past sessions.
3. Click the **REPLAY TIMELINE** tab and move the timeline slider back and forth to show mission scrubbing.
4. Click the **UNIT VIEW** tab to show the comparative leaderboard comparing the trainee against the 5 sample unit operators (labelled *"Sample data"*).
5. Point to the **Focus Areas Box** showing identified weak skills (e.g., *Decoy Discrimination*).

**Presenter says:**
> *"The AAR dashboard delivers a command-level debrief: an interactive replay slider to inspect past actions, a Chart.js progress curve, and a unit benchmark view comparing trainees against their peers. The system flags the operator's weakest skill—here, decoy discrimination—and highlights tactical pointers for remediation."*

---

### [2:40 - 3:00] Adaptive Difficulty & Conclusion (20 seconds)
**Presenter does:**
1. Point to the **Adaptive Progression Banner**:
   - Explain the rule: *Last 3 sessions averaging >80% automatically escalates difficulty; below 50% reduces it.*
   - Show how the next scenario is selected specifically to target the operator's weakest category.
2. Click **NEXT SCENARIO** or return to **HOME**.

**Presenter concludes:**
> *"AakashRakshak adapts dynamically: trainees who excel are automatically pushed to degraded night fog and 15-drone Boids swarms; struggling trainees receive targeted remediation. It is simple, reliable, explainable, and ready to deploy on any laptop today. Thank you!"*
