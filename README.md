# �� Hospital Simulation 2D
&gt; A realistic, fast-paced 2D side-scrolling medical management and diagnostic game. Manage a
bustling UK hospital, perform examinations and minigames, prescribe treatments, and save lives
floor-by-floor.
---
## �� Project Overview
Hospital Simulation 2D blends *Terraria*-style 2D side-scrolling navigation with deep, medically
accurate clinical decision-making based on UK healthcare guidelines (BNF / NICE). Players step into
the shoes of a hospital doctor balancing triage, diagnostics, procedures, and patient deterioration
in real-time.
* **Target Platform:** Windows PC (Steam)
* **Target Hardware:** GTX 1060 Ti equivalent or better
* **Target Audience:** Casual-to-hardcore simulation fans &amp; medical enthusiasts
* **Target Rating:** PEGI 7 / 12
* **Build Size:** &lt; 2 GB
---
## �� Core Gameplay Loop (FR-22)
```
[1. Arrival] ➔ [2. Triage] ➔ [3. Examination] ➔ [4. Investigations] ➔ [5. Diagnosis] ➔ [6.
Treatment] ➔ [7. Disposition]
```
### Step-by-Step Encounter Flow:
1. **Arrival:** A patient walks into the waiting room clutching their chest. An icon above them
shows severity (`Green` / `Amber` / `Red`). Active ambulance bay running.
2. **Triage (5s, Click-Based):** Card pops up. Check vitals (`HR 110`, `BP 150/90`, `SpO2 94%`) and
chief complaint (*&quot;Chest pain, started 2 hours ago, radiating to left arm&quot;*). Auto-tagged �� **Red
Critical**. Deterioration timer starts.
3. **Examination (Click-to-Examine Panel):** Body diagram appears. Click regions (Auscultate chest:
*&quot;mild crackles at bases&quot;*; Palpate abdomen: *&quot;no tenderness&quot;*; Inspection: *&quot;diaphoretic, pale,
anxious&quot;*). Each click takes 1-2s game time.
4. **Investigations (Physical Travel):** Escort patient to equipment rooms for minigames:
* **ECG Room:** Trace minigame ➔ *&quot;ST elevation in leads II, III, aVF&quot;*
* **Blood Lab:** Pipette minigame ➔ *&quot;Troponin elevated&quot;*
* **X-Ray Room:** Contrast/exposure minigame ➔ *&quot;Mild pulmonary oedema&quot;*

5. **Diagnosis (Multiple Choice):** Select diagnosis (*Pulmonary Embolism*, *Heart Attack (STEMI)*,
*Panic Attack*). Correct choice gives XP and pauses timer. Wrong pick incurs penalty and timer keeps
running.
6. **Treatment:**
* **Prescription Minigame:** Drag correct medications (*Aspirin ✅*, *Nitroglycerin ✅*, *Morphine
✅*; avoid *Metformin ❌*).
* **Procedure Minigame:** IV Cannulation timing minigame to hit the vein window as needle moves
across arm.
7. **Disposition (Final Decision):** Select action (*Admit to Cardiology Ward*). Patient wheeled
through ward doors. Case closed, XP awarded, and next patient difficulty scales subtly.
---
## ��️ Functional Requirements (FR)
### 2.1 Player Character &amp; Movement
| ID | Requirement | Priority | Details |
| :--- | :--- | :--- | :--- |
| **FR-01** | 2D Side-Scrolling Movement | **MUST (V1)** | Walk, run, and jump mechanics controlled
via WASD/Arrow keys using Terraria-style gravity physics. |
| **FR-02** | Multi-Floor Navigation | **MUST (V1)** | Hospital layout spanning multiple floors
(A&amp;E, Wards, Pharmacy, Radiology) via stairs and lifts. |
| **FR-03** | Interaction System | **MUST (V1)** | Proximity-based interaction key (`E` or
`Spacebar`) for patients, equipment, and NPCs with dynamic UI prompts. |
### 2.2 Patient System
| ID | Requirement | Priority | Details |
| :--- | :--- | :--- | :--- |
| **FR-04** | Admission &amp; Queuing | **MUST (V1)** | Dynamic patient arrivals with color-coded
urgency: �� Green (Low), �� Amber (Medium), �� Red (Critical). Untreated patients deteriorate
leave/crash. |
| **FR-05** | Chart &amp; History | **MUST (V1)** | Dynamic patient medical records tracking symptoms,
vitals, active medications, allergies, and history. |
| **FR-06** | Deterioration System | **MUST (V1)** | Real-time health decline for
untreated/mismanaged cases. Visible health bar; zero health results in a negative/fatal outcome. |
| **FR-07** | Outcome Tracking | **MUST (V1)** | Shift logging for cases: *Recovered*, *Stabilised*,
*Deteriorated*, or *Critical*. Displayed at end of shift. |
| **FR-08** | Procedural Generation | **SHOULD (V1)** | Case templates with randomized age, gender,
severity, and chief complaint to prevent repetition. |
### 2.3 Treatment &amp; Diagnosis
| ID | Requirement | Priority | Details |
| :--- | :--- | :--- | :--- |
| **FR-09** | Investigation Actions | **MUST (V1)** | Physical traversal to equipment nodes (Blood
Analyser, ECG, X-Ray, Pharmacy) with real-time processing delays. |
| **FR-10** | Prescribing System | **MUST (V1)** | Formulary selection. Incorrect dosage, wrong
drug, or ignoring allergies triggers adverse events and score penalties. |
| **FR-11** | Drug Interaction Detection | **MUST (V1)** | Automated warnings for drug interactions.
Overriding warnings causes cascading clinical complications. |
| **FR-12** | Hands-On Procedures | **SHOULD (V1)** | Precision/timing minigames for IV Cannulation,
Venepuncture, and CPR. Success influences patient satisfaction score. |
| **FR-13** | Referral System | **COULD (V2)** | Refer to specialties (Cardiology, Surgery,
Psychiatry) via physical interaction with specialist rooms. Reduces workload but costs time. |
### 2.4 Hospital World
| ID | Requirement | Priority | Details |
| :--- | :--- | :--- | :--- |

| **FR-14** | Persistent World | **MUST (V1)** | Hospital state persists between shifts with auto-
save enabled. |
| **FR-15** | Interactable Equipment | **MUST (V1)** | World-anchored physical equipment (Blood
Analyser, ECG, X-Ray, Medication Trolley, Defibrillator) with position and queues. |
| **FR-16** | NPC Staff | **SHOULD (V1)** | Autonomous Nurses, Porters, Receptionists providing
hints/updates. Future update: Staff hiring system. |
| **FR-17** | Personal Upgrade System | **SHOULD (V2)** | Earn points per shift to spend on faster
machines, more beds, and new departments. Upgrades visible in-world. |
### 2.5 Shift Structure &amp; Progression
| ID | Requirement | Priority | Details |
| :--- | :--- | :--- | :--- |
| **FR-18** | Shift System | **MUST (V1)** | Day / Evening / Night shifts with defined duration and
patient load. Night = harder, fewer staff, rarer cases. |
| **FR-19** | End-of-Shift Debrief | **MUST (V1)** | Summary covering patients treated, outcomes,
correct vs incorrect decisions, score, and mistake explanations. |
| **FR-20** | Specialty Progression | **SHOULD (V2)** | Unlock departments (Cardiology, Oncology,
Psychiatry, Paediatrics), adding new cases and drugs. |
| **FR-21** | Save &amp; Load System | **MUST (V1)** | Auto-save after each shift, manual saves, and
multiple save slots. |
---
## �� Non-Functional Requirements (NFR)
### 3.1 Performance
* **Target GPU:** GTX 1060 Ti or equivalent
* **Framerate:** Minimum 60 FPS at 1080p
* **Load Time:** &lt; 10 seconds
* **Transitions:** Scene transitions &lt; 3 seconds
* **Stability:** No frame drops during peak load spikes
### 3.2 Visual Style
* **Layout:** 2D side-scrolling (Terraria-inspired layout)
* **Art Style:** Pixel art or stylized 2D with parallax backgrounds
* **Resolution:** 1080p (scalable to 4K)
* **UI/UX:** Clean, readable UI with color-coded urgency (�� Green / �� Amber / �� Red)
### 3.3 Engine &amp; Technology
* **Engine:** Unity 2D (C#) or Godot 4 (GDScript)
* **Version Control:** Git (GitHub / GitLab)
* **Platform:** Windows PC (Steam)
* **Future-Proofing:** Must support future 3D upgrade path
### 3.4 Data &amp; Content
* **Storage:** Cases stored as JSON or ScriptableObjects/Resources
* **Modifiability:** Drug database and cases editable outside engine (no code required to add new
cases)
* **Minimum V1 Content:** 50 cases, 80 generic drugs
* **Review:** Reviewed by at least one practicing UK F1 doctor
### 3.5 Medical Accuracy
* **Practice Standard:** Based on UK NHS practice
* **Drug Names:** BNF generic
* **Guidelines:** NICE / BNF aligned
* **Quality Assurance:** All cases reviewed pre-launch

* **Disclaimer:** Educational / entertainment use only; no harmful real-world misinformation
### 3.6 Usability &amp; Accessibility
* Accessible to non-medical players
* **Tutorial:** First shift fully guided
* **Language:** Plain English by default with medical tooltips
* **Controls:** Remappable controls with optional controller support
* **Onboarding Time:** &lt; 5 minutes
### 3.7 Reliability
* Stable for 4+ hour play sessions
* Auto-save at shift end
* Crash recovery enabled
* In-game bug reporting (F12 screenshot)
* Steam achievements function correctly
### 3.8 Steam &amp; Distribution
* Minimum 10 Steam Achievements at launch
* Steam Cloud saves required
* Trading cards optional (post-launch)
* **Target Rating:** PEGI 7 or 12
* **Install Size:** &lt; 2 GB
---
## �� Assumptions
* At least one team member can code (Unity/Godot).
* Medical content written/reviewed by UK F1 doctors.
* V1 uses asset packs (transitioning to custom art in V2).
* Steam fee ($100) is budgeted.
* **Timeline:** 6–12 months (weekend development, team of 3–5).
---
## �� License &amp; Disclaimer
*Disclaimer: This game is a work of fiction intended strictly for entertainment and educational
illustration. It does not constitute real-world medical advice or clinical instruction.*
