# AakashRakshak: User Tutorial & Operator Guide

Welcome to **AakashRakshak** (आकाश रक्षक), an offline simulation trainer designed for operators learning drone and counter-drone (C-UAS) threat management.

---

## 1. How to Start the App

1. Open your terminal in the project folder:
   ```bash
   npm install
   npm run dev
   ```
2. Open your browser and go to `http://localhost:5173/`.
3. The app is completely offline. It does not need internet access, user logins, or server setups.
4. On the main screen, you will see your Operator Profile, Current Difficulty Level, and Scenario choices.

---

## 2. Step-by-Step: Your Very First Session

Follow these simple steps for a comfortable first run:

### Step A: Choose "Practice Range" or "Lone Scout"
- Click on **Practice Range** (1 slow drone, no scoring rush) or **Lone Scout** (1 commercial quadcopter approaching in clear daytime).
- Click the large blue **START SIMULATION** button at the bottom.

### Step B: Look Around & Scan Your Sector
- You are standing at the observation post.
- **Click and drag** anywhere on the 3D screen to look left, right, up, or down.
- **Scroll your mouse wheel** to zoom in and examine targets closely.
- Look at the circular **2D Radar** in the bottom-right corner. The rotating sweep line reveals incoming radar contacts. The blue wedge indicates where your 3D view is currently pointed.

### Step C: Mark the Contact (Detection Time)
- When you see a blip on radar or a drone in the sky, click on the blip or the 3D drone. You can also press the **[M]** key.
- The simulator immediately records your detection reaction time down to the millisecond. Faster reaction times earn higher scores.

### Step D: Classify the Target (Keys 1 to 6)
An action window will open on the right. Look through your optical zoom to identify the drone:
- Press **[1]** for **Quadcopter** (4 arms with spinning rotor discs).
- Press **[2]** for **Fixed-Wing UAV** (aerodynamic swept wings, higher speed).
- Press **[3]** for **Loitering Type** (canard front wings and rear wings).
- Press **[4]** for **Bird Decoy** (flapping wings, natural movement).
- Press **[5]** for **Friendly Drone** (bright blue identification beacon).
- Press **[6]** for **Unknown** (if you cannot yet verify).

### Step E: Designate Threat Level
Choose one of three levels:
- **LOW:** Birds, friendly drones, or harmless observation.
- **MEDIUM:** Standard commercial quadcopters.
- **HIGH:** Armed fixed-wing or loitering munitions.

### Step F: Choose Your Tactical Response
- Click **OBSERVE** to keep monitoring without intervention.
- Click **REPORT UP CHAIN** to send telemetry to headquarters.
- Click **JAM (RF / EW)** to disrupt the drone's radio frequency (you will see a purple disruption aura and the drone will lose control).
- Click **ENGAGE** to simulate a kinetic/directed intercept (simulated beam neutralizes the drone).
- *Warning:* Firing upon a friendly drone or a bird is a critical safety violation!

### Step G: Finish & Debrief
- Click **END SESSION & SCORE** in the top bar (or wait for the timer to reach zero).

---

## 3. How to Read Your Score ("Why This Score?")

After ending a session, the **"Why This Score?"** screen walks you through an explainable decision tree:

- **Overall Score (0 to 100):**
  - **85 - 100 (Exemplary):** Outstanding target detection, accurate classification, and flawless Rules of Engagement (ROE).
  - **70 - 84 (Proficient):** Solid operational standard. Combat ready.
  - **50 - 69 (Qualified):** Basic pass; slight delays or minor classification mistakes.
  - **Below 50 (Needs Remedial):** Missed targets or critical safety violations.
- **Green Ticks (✓) and Red Crosses (✗):**
  - Every contact shows individual breakdown cards. Click on any contact to see exactly whether your detection was fast, standard, or slow, whether your classification was correct (+30 or -15), and whether your tactical response was authorized.
- **Illustrative Weights:** The weights are instructional guidelines, not classified doctrine.

---

## 4. How to Read the After-Action Review (AAR)

Click **OPEN FULL AAR DASHBOARD** to explore three deep-dive tabs:

1. **Performance Summary:**
   - Shows key metrics: Average Detection Time (seconds), Classification Accuracy (%), False Alarms count, and Missed Targets count.
   - **Score Trajectory (Chart.js):** A clean line graph tracking your score over your last sessions so you can see your improvement over time.
   - **Focus Areas Box:** Highlights your weakest category (e.g., *Swarm Target Prioritization* or *Decoy Discrimination*) with tactical tips to fix it.
2. **Replay Timeline:**
   - Use the interactive slider at the top to scrub backwards and forwards through the mission.
   - You can see exactly what actions you took at each second of the exercise.
3. **Unit View:**
   - Displays a comparative leaderboard comparing your performance against sample unit operators (clearly labelled *"Sample data"*).

---

## 5. How Difficulty Changes (Adaptive Engine)

The simulation uses an explainable rule-based system to adapt to you:
- **Rule 1 (Escalation):** If your average score across your last 3 sessions is **above 80%**, the difficulty level automatically increases (introducing fog, night lighting, swarms, or decoys).
- **Rule 2 (De-escalation):** If your average score across your last 3 sessions is **below 50%**, the system reduces difficulty to help you build fundamental skills.
- **Targeting Weaknesses:** The simulator reads your weakest category from the AAR (e.g., night detection) and selects next scenarios that give you extra practice in that specific skill.
- **Instructor Override:** Instructors can easily override the adaptive system on the home page by selecting **AUTO**, **EASY**, **MED**, or **HARD**.

---

## 6. Five Common Mistakes & How to Fix Them

### Mistake 1: Forgetting to Mark the Contact First
- **Problem:** You classified and jammed the drone, but received a "Target Undetected / Missed" penalty.
- **Fix:** Always click the contact or press **[M]** as soon as you spot it. Marking records your detection reaction time, which is the foundational step of the air defence kill chain.

### Mistake 2: Engaging Friendly Drones or Bird Decoys
- **Problem:** You fired at a bird decoy or friendly surveillance asset, receiving a severe -40 point deduction.
- **Fix:** Before choosing "ENGAGE" or "JAM", check for the **flashing blue identification light** (friendly drone) or **flapping organic wings** (bird). Set response to "OBSERVE" or "REPORT" instead.

### Mistake 3: Tunnel Vision (Ignoring the Radar)
- **Problem:** Looking in only one direction in the 3D view and missing drones sneaking in from behind.
- **Fix:** Keep an eye on the **2D Radar** in the bottom-right corner. It shows the full 360-degree sector. The blue cone shows where you are looking; if you see a red/amber blip outside your cone, drag your mouse to turn toward it!

### Mistake 4: Guessing Before Zooming
- **Problem:** Misidentifying a fixed-wing UAV as a quadcopter and losing 15 points.
- **Fix:** Scroll your mouse wheel up to zoom in optically. Look at the wing structure: 4 horizontal propellers = quadcopter; swept triangular wings = fixed-wing; canards on nose = loitering munition.

### Mistake 5: Panicking in Swarm Scenarios
- **Problem:** Getting overwhelmed when 8 to 15 drones appear simultaneously in "Swarm Raid".
- **Fix:** You can press **[Space]** to pause the simulation at any time while you assess priorities. Prioritize the closest and fastest incoming threats first!
