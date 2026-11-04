# 1. Information architecture (card sort)

## Method

- **Open sort, then a closed check**, both by **AI-simulated participants (SP)**, each grounded in one D1B participant's behaviour. The brief allows AI-simulated participants for this step; this is disclosed here and in the AI-use note.
- 24 content and function cards, derived from the D2 themes (T1 to T5), the HTA sub-goals and the D3 concept.
- Open sort: each SP groups the 24 cards and names the groups. We built a co-occurrence matrix and clustered it (average linkage on 1 − agreement, cut at 0.55).
- The team named the IA categories from the clusters, then each SP ran a closed sort into those categories.

| SP | Grounded in | Persona | Behaviour reflected in the sort |
|---|---|---|---|
| SP-F | Participant F | B (lookup) | Machine first, then one number or table |
| SP-H | Participant H | A (careful first-timer) | Reads warnings first, linear thinker |
| SP-G | Participant G | B (lookup) | Owns a front-loader, fine-grained piles |
| SP-I | Participant I | A | Makes a separate "Safety" pile |
| SP-J | Participant J | C (try-first) | One "do the wash" pile and one "help" pile |

## The 24 cards

| Card | Content | Card | Content |
|---|---|---|---|
| C01 | Choose a task (First wash) | C13 | Press Start |
| C02 | Confirm my machine model | C14 | Lid-lock click |
| C03 | Find the detergent tray | C15 | Countdown on the display |
| C04 | Main-wash compartment | C16 | Is this normal? (point at anything) |
| C05 | Softener compartment | C17 | Part names on the camera view |
| C06 | How much detergent | C18 | Enlarge a tiny symbol |
| C07 | Full-to-here line on the drum | C19 | Cautions for this step |
| C08 | Is my load too much? | C20 | Switch English / Urdu |
| C09 | Power on | C21 | Camera can't see the part |
| C10 | What does "32" mean? | C22 | Show a drawing instead of camera |
| C11 | Choose Heavy/Bedding program | C23 | Step progress (step 3 of 6) |
| C12 | Water level Auto | C24 | Go back a step |

## Open-sort clusters

| Cluster | Cards |
|---|---|
| K1 | C01, C02, C20 |
| K2 | C03, C04, C05, C06 |
| K3 | C07, C08 |
| K4 | C09, C11, C12, C13 |
| K5 | C10, C14, C15, C16 |
| K6 | C17, C18, C21, C22 |
| K7 | C23, C24 |
| K8 | C19 |

## From clusters to the IA

| Cluster | Decision |
|---|---|
| K1 | Becomes **Home** (task choice) and **Settings in the header** (model, language) |
| K2 | One step: **Detergent** |
| K3 | One step: **Load** |
| K4 | Split. Power on, program and water level become **Set controls**; **Start** is its own step because participants hesitated at Start (F-07, H-10) |
| K5 | Pulled out of the steps into one **global "Is this normal?"** utility, because the same signals appear at several moments (T2) |
| K6 | Camera tools (C17, C18) apply to every step; recovery (C21, C22) lives **inside the error box** |
| K7, K8 | Belong to the **step frame** shown on every step (progress, back, cautions) |

## Final IA

| Category | Cards |
|---|---|
| Home: choose a task | C01 |
| Settings (header) | C02, C20 |
| Step: Detergent (tray, then compartment) | C03, C04, C05, C06 |
| Step: Load | C07, C08 |
| Step: Set controls | C09, C11, C12 |
| Step: Start | C13 |
| **Is this normal? (global)** | C10, C14, C15, C16 |
| Camera view tools (every step) | C17, C18 |
| Can't see it? (recovery, inside the error) | C21, C22 |
| Step frame (every step) | C19, C23, C24 |

```
Home (hub)
 ├─ First wash ─▶ Step 1 ─▶ 2 ─▶ 3 ─▶ 4 ─▶ 5 ─▶ 6 ─▶ Done      (sequential inside the task)
 │                   each step: progress, cautions, Back, camera tools
 │                   errors: a (not recognised), b (overfill), c (softener)
 └─ Other tasks (disabled, "Not in this prototype")
Header, always reachable: Language (EN / UR), Is this normal? (dialog, global)
```

## Closed check

| SP | Agreement with the IA |
|---|---|
| SP-F | 92% |
| SP-H | 92% |
| SP-G | 96% |
| SP-I | 96% |
| SP-J | 88% |
| **Average** | **93%** |

Changes made after the closed check:
- "32" is explained inline on the power-on step **and** in the global dialog.
- The detergent caution is repeated on the Start step.
- Recovery actions live inside each error box.

## Navigation pattern

**Hub-and-spoke at the top, sequential (linear) inside the task, plus one global utility.**

- The task is one ordered procedure (HTA Plan 0: 1 to 6), so a **sequential** pattern matches the structure and the "one step at a time" requirement (T5).
- The hub keeps room for more tasks later without changing the step pattern.
- The global "Is this normal?" is outside the sequence so it can be used at any moment (T2).
- Back is always available (C24); Next is disabled until the step is done (error prevention).

## Limits

- Five simulated sorters, grounded in five real observations, are not five real card sorters. Treat 93% as a consistency check on our reasoning, not as user validation. Real card sorting with participants is a candidate for D5B.
