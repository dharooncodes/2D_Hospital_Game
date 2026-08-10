2. Functional Requirements
2.1 Player Character & Movement
FR-01: 2D Side-Scrolling Movement (MUST – V1)
 The player controls a doctor character in a 2D side-scrolling hospital environment.
Movement: Walk, run, jump
Controls: WASD or arrow keys
Physics: Terraria-style (gravity, jumping between floors)
FR-02: Multi-Floor Navigation (MUST – V1)
 Hospital includes multiple floors: A&E, wards, pharmacy, radiology
Movement via stairs or lifts
Each floor has distinct layout and patient types
FR-03: Interaction System (MUST – V1)
Interaction key: E or Spacebar
Used for patients, equipment, NPCs
On-screen prompts when in range

2.2 Patient System
FR-04: Patient Admission & Queuing (MUST – V1)
Patients arrive over time in A&E
Each has complaint + urgency level:
Green (low)
Amber (medium)
Red (critical)
Untreated patients deteriorate or leave/crash
FR-05: Patient Chart & History (MUST – V1)
Contains symptoms, vitals, medications, allergies, history
Updates dynamically as player gathers information
FR-06: Patient Deterioration System (MUST – V1)
Real-time health decline if untreated/incorrectly treated
Visible health bar
Zero health = negative outcome
FR-07: Patient Outcome Tracking (MUST – V1)
 Outcomes:
Recovered
Stabilised
Deteriorated
Critical
Logged and displayed at end of shift
FR-08: Procedural Patient Generation (SHOULD – V1)
Case templates with randomised:
Age
Gender
Severity
Complaint
Prevents repetition

2.3 Treatment & Diagnosis
FR-09: Investigation Actions (MUST – V1)
Player must physically go to equipment:
Blood machine
ECG
X-ray
Pharmacy
Results take real time
FR-10: Prescribing System (MUST – V1)
Select drug from formulary
Correct treatment improves outcome
Errors (wrong drug/dose/allergy):
Trigger adverse events
Apply score penalties
FR-11: Drug Interaction Detection (MUST – V1)
Warnings for drug interactions
Ignoring warnings → cascading adverse events
FR-12: Hands-On Procedures (SHOULD – V1)
 Mini-games for:
Cannulation  (inserting needle into a vein)
CPR
Blood taking
Skill-based (timing/precision)
Failure → retry or complication
These would influence “patient satisfaction score”
FR-13: Referral System (COULD – V2)
Refer to specialties (cardiology, surgery, psychiatry)
Requires physical interaction with specialist room
Reduces workload but costs time

2.4 Hospital World
FR-14: Persistent World (MUST – V1)
Hospital state persists between shifts
Auto-save enabled
FR-15: Interactable Equipment (MUST – V1)
All equipment exists physically in the world
Includes:
Blood analyser
ECG
X-ray
Medication trolley
Defibrillator
Each has position and queue
FR-16: NPC Staff (SHOULD – V1)
Nurses, porters, receptionists
Autonomous movement
Provide hints or updates
Future update -> staff hiring system
FR-17: Personal Upgrade System (SHOULD – V2)
Earn points per shift
Spend on:
Faster machines
More beds
New departments
Upgrades visible in-world

2.5 Shift Structure & Progression
FR-18: Shift System (MUST – V1)
Day / Evening / Night shifts
Defined duration + patient load
Difficulty scaling:
Night = harder, fewer staff, rarer cases
FR-19: End-of-Shift Debrief (MUST – V1)
Summary includes:
Patients treated
Outcomes
Correct vs incorrect decisions
Score
Explanations for mistakes
FR-20: Specialty Progression (SHOULD – V2)
 Unlock departments:
Cardiology
Oncology
Psychiatry
Paediatrics
 Each adds new cases + drugs
FR-21: Save & Load System (MUST – V1)
Auto-save after each shift
Manual saves available
Multiple save slots
FR-022: Core gameplay loop (MUST – V1)
Patient Arrives → Triage → Examination → Investigation → Diagnosis → Treatment → Disposition 
1. ARRIVAL — A patient walks into the waiting room clutching their chest. An icon above them shows severity (green/yellow/red). You have 3 patients waiting, one ambulance bay active. You click this patient to begin.
2. TRIAGE (5 seconds, click-based) A card pops up. You click to perform:
✅ Check vitals → shown instantly: HR 110, BP 150/90, O2 94%
✅ Chief complaint → "Chest pain, started 2 hours ago, radiating to left arm" Severity auto-tags as 🔴 Red — Critical. Timer starts.
3. EXAMINATION (click-to-examine panel) A body diagram appears. You click body regions:
👂 Auscultate chest → "Heart sounds normal, mild crackles at lung bases"
🤚 Palpate abdomen → "No tenderness"
👀 General inspection → "Diaphoretic, pale, anxious"
Each click takes 1-2 seconds of game time. You choose which ones matter — doing all of them wastes time on a red patient.
4. INVESTIGATIONS (you walk patient to the room) Based on what you found, you decide which tests to order. You pick from a menu:
ECG Room → Rhythm minigame — trace appears, you identify the abnormal segment by clicking it. Correct = "ST elevation in leads II, III, aVF"
Blood Lab → Pipette minigame — quick, simple. Result: Troponin elevated
X-Ray Room → Contrast/exposure minigame — Result: mild pulmonary oedema
Ordering the wrong test (e.g. skipping ECG on chest pain) = time lost, score penalty.
5. DIAGNOSIS (multiple choice, 3 options) Game presents 3 options based on your findings:
○ Pulmonary Embolism
● Heart Attack (correct)
○ Panic Attack
You pick. Correct = green flash, XP tick, timer pauses briefly. Wrong pick = you're sent back to investigations with a hint. Timer keeps running. Patient deteriorates slightly.
6. TREATMENT (split based on what's needed)
Some conditions → Prescription minigame A drug card tray slides in. You drag the right medications into the "given" tray:
Aspirin ✅
Nitroglycerin ✅
Morphine ✅
Metformin ❌ (wrong, penalty if chosen)
Some conditions → Procedure minigame For this patient, you also need to place an IV:
Simple timing/click minigame — hit the vein window as a needle moves across the arm
7. DISPOSITION (final decision, multiple choice)
○ Send home with prescription
● Admit to Cardiology (correct)
○ Discharge with follow-up
Correct → patient is wheeled through the ward doors. ✅ Case closed. XP awarded. Difficulty of next patient subtly increases.

3. Non-Functional Requirements
3.1 Performance
Target GPU: GTX 1060 Ti or equivalent
Minimum: 60 FPS at 1080p
Load time: <10 seconds
Scene transitions: <3 seconds
No frame drops during peak load

3.2 Visual Style
2D side-scrolling (Terraria-inspired layout)
Pixel art or stylised 2D
Resolution: 1080p (scalable to 4K)
Parallax backgrounds
Clean, readable UI
Colour-coded urgency (green/amber/red)
Consistent art style

3.3 Engine & Technology
Engine: Unity 2D or Godot 4
Language:
Unity → C#
Godot → GDScript
Version control: Git (GitHub/GitLab)
Platform: Windows PC (Steam)
Must support future 3D upgrade path

3.4 Data & Content
Cases stored as JSON or ScriptableObjects
Drug database editable outside engine
Minimum V1 content:
50 cases
80 drugs (perhaps too many)
No code required to add new cases
Reviewed by at least one F1 doctor

3.5 Medical Accuracy
Based on UK practice
Drug names: BNF generic
Guidelines: NICE / BNF aligned
All cases reviewed pre-launch
Disclaimer: Educational use only
No harmful real-world misinformation

3.6 Usability
Accessible to non-medical players
Tutorial: First shift guided
Plain English by default
Remappable controls
Optional controller support
Onboarding time: <5 minutes

3.7 Reliability
Stable for 4+ hour sessions
Auto-save at shift end
Crash recovery enabled
In-game bug reporting (F12 screenshot)
Steam achievements function correctly

3.8 Steam & Distribution
Minimum 10 achievements at launch
Steam Cloud saves required
Trading cards optional (post-launch)
Target rating: PEGI 7 or 12
Install size: <2GB

4. Assumptions
At least one team member can code (Unity/Godot)
Medical content written by F1 doctors
V1 uses asset packs (custom art in V2)
Steam fee ($100) is budgeted
Timeline: 6–12 months (weekend development, team of 3–5)

