# Konnect master context

Read this before changing anything. It covers the project, the decisions made, how the app works, and what is still open.

**Rules for anyone building on this**
- **Do not make assumptions.** If something is not written here, ask the team.
- **Do not invent** fieldwork, critique notes, accessibility findings, user-test results or machine facts (e.g. Panasonic error codes, exact button layout). Label anything simulated or AI-run as such.
- **Keep Part A's structure and accessibility fixes** in anything you change. Re-check keyboard and focus behaviour after edits.
- Keep the IDs consistent: F-01…, T1–T5, R1–R5, W1–W8, E0–E3, N1–N2, C01–C24, SP-x.
- No names, student IDs or participant data in this repo.

## 0. Repo layout

| Path | What |
|---|---|
| `konnect-prototype.html` | Part B app (single file) |
| `site/index.html` | Copy for GitHub Pages. Re-copy after every edit |
| `part-a/` | Part A items as markdown: IA, wireframes, accessibility audit, critique record, AI-use note, reflection. Start at `part-a/README.md` |
| `Konnect_D4_PartA_Wireframes.drawio` | Master wireframes (draw.io). Export: `part-a/wireframes.svg` |
| `README.md`, `CHANGELOG.md`, `CONTEXT.md` | Run steps, every change, this file |

Word documents, PDFs and earlier submissions are git-ignored (they hold names and student IDs).

## 1. Quick facts

| Item | Value |
|---|---|
| Course | CS3014 Applied Human-Computer Interaction (FAST NUCES, Islamabad), Dr. Javeria Imtiaz, BSCS-7B |
| Team | No. 05, "Konnect" (4 members) |
| Deliverable | **D4: Prototype, Structure, Function and Accessibility** (9%, CLO 2). Due 4 Nov 2026 |
| Next | D5A expert evaluation (Nielsen's heuristics, Shneiderman's rules) is applied **to this D4 build**. D5B is user testing |
| Topic | Usability of household-appliance manuals when setting up and starting an unfamiliar appliance for the first time |
| Concept (D3) | **M4-E Camera overlay**: phone camera view of the real machine with labelled parts, one step at a time |
| D4 scope | **Panasonic NA-F135A1** top-load washer only; one task: "First wash: set up and start a heavy load" |
| Tech | One self-contained HTML file (plain HTML, CSS, JS). Static, runs on GitHub Pages |

## 2. Project history (D0 to D3)

**D0 assumption:** users struggle to set up or troubleshoot appliances because manuals fail to visually map components to where they are and what they do.

**D1A research question:** how do adult householders locate, identify and understand appliance components and operational steps when setting up or maintaining using a manual? Participants 18 to 60, purposive sampling, contextual inquiry then a short interview, verbal consent, anonymised as "Participant X". **No identifiable data or raw audio goes to any AI tool.**

**D1B fieldwork (5 sessions).**
- Washing machine (Participants F, H, G): Panasonic fully automatic top-load **NA-F135A1**, 13.5 kg.
  - **Detergent tray is inside the lid area, inside left, with two compartments.** The machine shows symbols only; the manual shows words only.
  - Control panel: push buttons with icons and a digital display. **No timer knob.** The display shows a number ("32") before the cycle starts.
  - Program used: **Heavy/Bedding**, water level **Auto**. **The lid locks with an audible click when the cycle starts.**
  - Manual: printed, multi-language. English pp. 25 to 48; parts and control panel p. 30; load capacity p. 31; programs p. 34; **detergent p. 36**.
  - Task: "Show me how you would set the machine up and start a wash for a heavy load, using the manual if you want. Think out loud."
- Air fryer (Participants I, J): **out of D4 scope.**

| ID | Appliance | Profile | Outcome |
|---|---|---|---|
| F | Washer | Student; family uses twin-tub | Done 7 min; overfilled drum; guessed tray symbol; YouTube ~4 min before Start |
| H | Washer | Student; never operated any washer; reads from page one | Done 7 min; wrong compartment, self-corrected; messaged family |
| G | Washer | Postgrad; owns front-loader | Done 5 min; unsure about water level |
| I | Air fryer | Student | Done 7 min; unsure preheat and guard |
| J | Air fryer | Student; tries first | Partly done; preheat skipped, overfilled, near-drop |

**D2 themes.**

| Theme | Name | Strength |
|---|---|---|
| T1 | Can't find part | 15 notes, 5/5 participants |
| T2 | Machine signal misread | 14 notes, 5/5 |
| T3 | Manual is last resort | 14 notes, 5/5 |
| T4 | Numbers that can't be acted on | 8 notes, 4/5 (supporting) |
| T5 | Steps buried in the booklet | 8 notes, 3/5 (supporting) |

**Key evidence used in the design:** F-08 "the picture's tiny… I'm just guessing they are the same"; H-11 "Why is [the tray] here? I would put it in the drum"; H-12 poured into the small compartment by size; G-07 never would have looked inside the lid; F-03 / H-08 "32 what? Minutes? There's no knob here"; H-14 lid click "Did I break it?"; F-07 hovered over Start, "what if it's wrong?"; H-05 / H-06 "Max 13.5 kg. How many kilos is this?", loaded half.

**Personas.**
- **A, Careful First-Timer** (H, I): reads from page one, afraid of breaking it. **Primary persona.**
- **B, Lookup User** (F, G): machine first, then one table or number.
- **C, Try-First Fixer** (J): tries first, YouTube, manual only after something goes wrong.

**HTA Plan 0 (washing machine):** 1 find instructions; 2 identify parts and controls; 3 prepare (3.1 locate tray, 3.2 choose compartment and add detergent); 4 load (4.1 judge amount vs limit); 5 set controls (5.1 power on and read display, 5.2 Heavy/Bedding with water Auto); 6 start and interpret (6.1 press Start, 6.2 interpret lid lock and countdown).

**Requirements.**

| Req. | Target |
|---|---|
| R1 | Identify each named part, control and symbol first time, no help. 0 wrong-compartment pours |
| R2 | Reach the instruction for the current step in ≤ 60 s and ≤ 3 page turns |
| R3 | Correct order, no cautioned action (no overfill; **detergent in main wash before Start**) |
| R4 | Understand normal responses when they happen; finish alone; confidence ≥ 6/7; 0 fault readings; ≤ 1 of 5 seek outside help |
| R5 | Markings perceivable regardless of print size, eyesight, language: symbols paired with words, contrast ≥ 4.5:1, English reachable without paging |

**D3 selection.** M4-E scored R1=2, R2=1, R3=1, R4=2, R5=1, passed the scope gate (can be prototyped without changing hardware or firmware), and won the tie on R1. Refined to: opens on a task, one step per screen with cautions, names and rings parts in the machine's own words, tags normal responses ("32 = wash minutes. Normal."), draws a "full to here" line on the drum.

**D3 promises:** large part names with symbols paired with words; enlarged close-ups of tiny symbols; **English first, optional Urdu**.

**D3 risks carried forward.**
1. Persona A may stay on paper; test whether a printed fallback is needed.
2. Hands may be full or wet: big buttons, one step per screen.
3. **Live part recognition can't be built at low fidelity.** Test flow and wording, not recognition accuracy.
4. Printed markings stay small.
5. The overlay can't stop a try-first user acting early.
6. Pictured limits may not match real loads.
7. Model-specific content must be correct (D1B model only).
8. Baselines for R2 timing and R4 confidence are incomplete (finish in D5B).

## 3. D4 brief summary

One submission in two parts.
- **Part A** (structure and accessibility, low fidelity): card-sort IA with navigation pattern; grayscale wireframes with arrows, an alternate or error path, visual hierarchy and a named Gestalt principle; keyboard-only and screen-reader walkthrough logs organised by WCAG POUR with fixed vs deferred; critique record.
- **Part B** (functional, checked live by an instructor): vertical slice of the core task, with built vs Wizard-of-Oz stated; minimal design system (semantic palette, 2 to 3 level type scale, spacing, one styled version of each component); visible feedback for every action; at least one deliberately handled specific error; as many of the 8 states as apply (default, focus/hover, active, disabled, loading, empty, error, success); implementation docs; accessibility re-check.
- **Video:** MP4 ≤ 5 min, AI narration with captions, named `05-Konnect-D4-Prototype.mp4`. Segments: 0:00 user/task/problem; 0:30 requirement and design response; 1:00 complete core workflow; 3:00 alternate/error path and recovery; 4:00 accessibility evidence and limitation; 4:40 one focused feedback question. Show actual behaviour, say what is simulated, don't infer usability from a demo.
- Also required: AI-use note and a reflection (graded for completion).

## 4. Team decisions

| # | Question | Decision |
|---|---|---|
| 1 | Appliance scope | One model: Panasonic NA-F135A1 |
| 2 | Tools | Part A wireframes in draw.io; Part B a web app |
| 3 | Machine imagery | Live camera plus a labelled grayscale drawing fallback. Team may add own photos (no faces) |
| 4 | Wizard-of-Oz style | Live camera with pre-placed overlay. **Updated in session 2 to tap-to-place** (user places the ring on the real part) |
| 5 | Error paths | All three: (a) part not recognised, (b) overfill, (c) detergent in softener |
| 6 | Card sort | Open sort then closed check, AI-simulated participants |
| 7 | Critique record | AI-reviewer critique, labelled honestly as such |
| 8 | Accessibility walkthrough | **Not decided.** Manual logs are blank; do not fill in findings |
| 9 | Language | English and Urdu (both built). Urdu is AI-drafted, needs native-reader check |
| 10 | Backend | Static only. Mock recognition and event log in JS (works on GitHub Pages) |
| 11 | Hosting | GitHub Pages (camera needs HTTPS) |
| 12 | Video | Later, once the build is final |

## 5. Information architecture (card sort)

24 cards (C01 to C24) sorted by 5 AI-simulated participants (SP-F, SP-H, SP-G, SP-I, SP-J, each grounded in one D1B participant), then a closed check with **93% average agreement**.

| IA category | Cards |
|---|---|
| Home: choose a task | C01 Choose a task (First wash) |
| Settings (header) | C02 Confirm machine model, C20 Switch English/Urdu |
| Step: Detergent | C03 Find tray, C04 Main-wash compartment, C05 Softener compartment, C06 How much detergent |
| Step: Load | C07 Full-to-here line, C08 Is my load too much? |
| Step: Set controls | C09 Power on, C11 Heavy/Bedding, C12 Water level Auto |
| Step: Start | C13 Press Start |
| **Is this normal? (global)** | C10 What does "32" mean, C14 Lid-lock click, C15 Countdown, C16 Point at anything |
| Camera view tools | C17 Part names on camera, C18 Enlarge a tiny symbol |
| Recovery (inside error a) | C21 Camera can't see the part, C22 Show a drawing instead |
| Step frame (every step) | C19 Cautions, C23 Step progress, C24 Go back |

Changes from the closed check: "32" explained inline on the power-on step and in the global dialog; the detergent caution is repeated on the Start step; recovery actions live inside each error box.

**Navigation pattern:** hub-and-spoke at the top (task choice), **sequential/linear inside the task**, plus one **global utility** ("Is this normal?").

## 6. Wireframes (Part A, draw.io, grayscale)

`Konnect_D4_PartA_Wireframes.drawio`; full write-up in `part-a/02-wireframes.md`; static export `part-a/wireframes.svg`. **Row 3 (added in session 3): P1 Placing, P2 Checking, P3 Found for the live-camera tap-to-place flow** (P2 fails to E1; P3 "Move ring" returns to P1).
- **Core path:** W1 Home, W2 Find tray, W3 MAIN WASH, W4 Load to line, W5 Power on and "32", W6 Heavy/Bedding and water Auto, W7 Start and lid click, W8 Done.
- **Alternate and error paths:** E0 camera blocked → drawing; E1 part not recognised; E3 softener; E2 overfill; N1/N2 "Is this normal?" list and answer (reachable from any screen).
- **Gestalt and hierarchy notes:** figure-ground (ring on camera view); proximity (label under its part); similarity (all "Normal" tags one style, all errors one style); common region (step frame, caution and status regions); visual hierarchy (title, instruction, camera, caution, status, Back/Next; only the primary action is filled); error hierarchy (error directly under the cause, recovery inside the box).

## 7. The app (`konnect-prototype.html`)

### Structure
Header (app name and model, language button, "Is this normal?") / `main` (rendered by `render()`) / footer with the Facilitator toggle / Wizard panel (dashed yellow top border). `max-width: 520px` column. Native `<dialog>` for "Is this normal?". An `aria-live` region announces changes. Errors use `role="alert"` and take focus.

### Flow

| Screen | Behaviour |
|---|---|
| Home | "What do you want to do?"; **First wash** active; **Other tasks** disabled ("Not in this prototype") |
| Step 1 | Find the detergent tray (inside the lid, left, not a drawer). Needs the tray found. Caution: don't pour detergent on clothes |
| Step 2 | Pour detergent into MAIN WASH. Choose **MAIN WASH** or **SOFTENER**. SOFTENER → error (c) and Next stays disabled |
| Step 3 | Load up to the dashed "Full to here" line. "Where is the top of your load?" Below → success. Above → error (b) with **Check again** |
| Step 4 | Power on and read the display. "32 = wash time in minutes. Normal." |
| Step 5 | Choose Heavy/Bedding, water Auto. Two checkboxes must be ticked |
| Step 6 | Close lid and press Start. **I pressed Start** → loading → "Click = lid locked. Normal." |
| Done | "Your wash has started"; Start again / Home |

### Navigation and focus rules
- Next uses `aria-disabled` (not `disabled`) until the step is done. Pressing it moves focus to the message or hint saying what is missing.
- Back is always available. On each new step focus moves to the step title (`h2`).
- Dialog: Esc closes it and focus returns to the opener.

### Tap-to-place (how the camera overlay works)
- All overlay positions are percentages of a 3:4 stage (the `G` table in the script).
- Each step has an **anchor** (`STEP_ANCH`: step 1,2 tray; 3 drum; 4 display; 5 panel). The user taps the real part; the app stores an offset `S.off[anchor]` from the default centre. `Gs(key)` returns a geometry shifted by that offset, so compartments, the full line and tags move with it.
- While placing (`S.recog === "searching"` on live camera) a crosshair-style dashed ring sits at `S.cursor`. Tap/click, Enter, or the **Place ring** button calls `placeAt()`.
- `placeAt()` → recog `checking` → `mockRecognise()` (700 ms) → `found` or `miss`.
- In drawing mode offsets are 0 and recognition is a 2 s timer (checkbox in the facilitator panel).

### Recognition states
`idle` → `searching` → `checking` → `found` | `miss`. The tag and ring classes follow these (dashed pulse = searching/checking, green = found, red = bad).

### Error messages (exact)
- (a) "Can't see the {part}. Lift the lid fully, hold the phone about 40 cm away, and make sure the area is well lit." Actions: Try again, Show a drawing instead.
- (b) "Too much for one wash. Take some items out until the top of the load is below the dashed line, then check again." Action: Check again.
- (c) "That is SOFTENER (flower symbol). Detergent goes in MAIN WASH, the compartment ringed on the left. Choose again."
- Camera blocked: "Camera is off or blocked. Allow camera access in your browser settings, or use the drawing of your machine." Action: Show a drawing instead.

### "Is this normal?"
Empty state, then three known signals (display shows 32; lid click; number going down), plus "Something else" (honest limit: the prototype only knows those three).

### Wizard-of-Oz (simulated)
Part recognition (mock check, forced result buttons), lid click (timer or button), forced drawing mode, reset. See README for the panel controls.

### Mock backend
- `mockRecognise()` simulated recognition service.
- `log(event, data)` appends to `localStorage["konnect_log"]` (last 300). Download from the facilitator panel.

### Fallback drawing
Inline SVG of the machine from above with the lid up (control strip, two-compartment tray on the left, drum). **A labelled stand-in, not a photo or the real panel layout.**

### Language
Full EN/UR string tables `T.en` / `T.ur`. Switching sets `<html lang="ur" dir="rtl">`. **Urdu is AI-drafted and unchecked by a native reader.** To add a string, add it to both tables.

## 8. Design system

Palette (team-supplied 4 swatches, sampled by eye; confirm exact hex): pink `#F9B1B6`, mauve `#AD7099`, violet `#8A6499`, indigo `#3F3D8A`.

| Token | Hex | Role and contrast |
|---|---|---|
| indigo (brand, focus) | #3F3D8A | Buttons, headings, focus. White on indigo about 9:1 |
| indigo-dark | #2E2C6B | Heading text, hover |
| pink | #F9B1B6 | Accent surface and header pill; dark indigo text on it about 5.3:1 |
| pink-soft | #FDEBED | Cards, info/loading status backgrounds |
| violet | #8A6499 | Gradient and decoration; white on violet about 4.8:1 |
| mauve | #AD7099 | **Decorative only** (white on mauve 3.8:1) |
| ink / muted | #1F1D3D / #55527A | Text; muted about 7.3:1 on white |
| success | #14692F on #E3F4E8 | Semantic, kept apart from brand |
| caution | #7A5200 / #3D2900 on #FFF4D1 | Semantic |
| error | #B42318 on #FDE8E6 | Semantic |
| disabled | #5E5A73 on #E6E3EC | About 4.6:1 |

Contrast values are calculated, not tool-verified. Re-check with a contrast tool after changing colours.

**UI concepts applied (Norman and Gestalt):**

| Concept | Where |
|---|---|
| Signifiers and affordances | Raised pill buttons; chevron on the task button; crosshair cursor and dashed ring on the camera view |
| Constraints | Next greyed until the step is done; SOFTENER and "above the line" block progress |
| Feedback | Every action gives a status box and a screen-reader announcement; loading states for camera, checking, waiting |
| Mapping | Label sits under the part it names; ring and compartments move together |
| Conceptual model | One progress ring "n/6" plus one step per screen |
| Visibility | Sticky Back/Next bar; "Is this normal?" always in the header |
| Proximity and common region | Ring, step count and title grouped in one card; caution and status boxes |
| Similarity | All primary actions indigo; all "Normal" tags and all errors one style each |
| Figure-ground | White sheet over the indigo hero; white ring on the camera view |
| Closure and continuity | Circular progress; 4-band palette stripe |
| Hierarchy | Title, instruction, camera, caution, status, nav |

- Type: 26 px bold heading, 20 px bold sub/label, 18 px body, 16 px minimum.
- Spacing: 4/8/16/24/32. Radius 12. Touch targets 48 px (44 px for small).
- Meaning is never carried by colour alone (✓ / ! icons plus words plus border).
- Components: button (primary, secondary, wrong), step frame and progress, camera stage (video or drawing, mode badge, rings, tags, full line), caution box, status message (info, loading, ok, err), choice pair, checkbox row, dialog.

**Component states:** default (all controls); focus/hover (3 px `#0B5CAD` outline); active (pressed buttons, `aria-pressed`); disabled (Next, Other tasks); loading (starting camera, looking, checking, waiting for machine; respects `prefers-reduced-motion`); empty (dialog); error (a, b, c, camera blocked); success (found ring, ✓ messages, Done).

## 9. Accessibility status

Done by an AI automated pre-check (this does **not** replace the manual walkthrough):

| # | Finding | Status |
|---|---|---|
| P1 | Drawing symbols were read aloud | Fixed (SVG text `aria-hidden`) |
| P2 | Bare "⚠" announced | Fixed (icon hidden, "Caution:" text) |
| P3 | Overlay rings duplicated the MAIN WASH/SOFTENER buttons | Fixed (`aria-hidden`, `tabindex=-1`) |
| P4 | Home tab order: Language, Is this normal?, First wash, Facilitator | As intended |
| P5 | Focus management and lang/dir | Verified |

Full log (P1 to P13, D1 to D5, blank K and S tables) is in `part-a/03-accessibility-audit.md`. New in session 3: P9 sticky bar no longer hides focused controls (scroll padding), P11 live-camera wording changed from "Found the …" to "Ring placed on the …. Check it matches what you see." because recognition is simulated.

Deferred (earlier list): D1 no text description of the live camera scene (mitigated: every step gives instruction and result as text); D2 Urdu unchecked; ~~D3 facilitator buttons 40 px~~ fixed to 44 px in session 2.

**New in session 2 (needs manual check):** the focusable camera view (`tabindex=0`, arrow keys + Enter) and the "Place ring" button are new keyboard paths and have not had a manual keyboard or screen-reader walkthrough.

## 10. Open work

**Part A status (session 3):** IA, wireframes (updated), critique record (AI reviewer, re-run on the current UI), AI-use note and the audit pre-check are written in `part-a/`. **Still open for Part A:** the manual keyboard and screen-reader walkthroughs (K and S tables), team confirmation of the critique, and the reflection.

1. **Manual accessibility walkthroughs** (tables ready in `part-a/03-accessibility-audit.md`; include the new camera-view arrow-key placing and the sticky bar) (keyboard-only; screen reader: NVDA, TalkBack or VoiceOver). Method not yet decided. Log screen, expected vs actual, and POUR category. Then update fixed vs deferred, and re-check after later changes.
2. **Test the live camera on a phone over HTTPS** (GitHub Pages). Steps 5 and 6 on the live camera have not been tested.
3. **Urdu review** by a native reader.
4. **Team confirmation** of the AI-reviewer critique record.
5. **Reflection:** the team writes it in their own words.
6. **Report** (Word, D2-style cover): paste Part A from `part-a/*.md` and update Part B for tap-to-place, the mock backend and the new palette.
7. **Video:** after the build is final; six segments, AI narration with captions, one focused feedback question (e.g. "When the lid clicks, can you tell 'lid locked, normal' apart from 'something went wrong'?" or one about the Step 5 checkboxes).
8. Optional: add the team's own photos of the NA-F135A1 (no people) to replace the drawn stand-in.
9. Known open critique points: Step 5's two checkboxes may annoy persona C (test in D5B); printed fallback for persona A deferred to D5.

## 11. Contributing

- Edit `konnect-prototype.html`, test it on `http://127.0.0.1:8765` (see README), then copy to `site/index.html`.
- Add a line to `CHANGELOG.md` for every change.
- Keep all new text in both `T.en` and `T.ur`.
- Do not claim anything is accessible, tested or user-validated unless a person did it. State plainly what is simulated.
