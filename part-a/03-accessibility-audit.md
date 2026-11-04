# 3. Accessibility audit log

> **Status: AI pre-check only.** The manual keyboard-only and screen-reader walkthroughs have **not been done** by a person yet (team decision: left for later). Nothing here is a conformance claim. The brief allows AI to say what to check, but a person must do the walkthroughs and the re-check.

Findings are organised under **WCAG POUR** (Perceivable, Operable, Understandable, Robust).

## 3.1 What the AI pre-check covered

- An automated accessibility-tree dump of Step 1 and focus/ARIA checks in a headless browser (earlier session; Playwright script not kept in this repo).
- A code read of the current build (this session) for focus management, labelling, target size, colour contrast by calculation, and the new tap-to-place interaction.
- It did **not** use a real screen reader, a real keyboard session on a phone, or a contrast tool.

## 3.2 AI pre-check findings (by POUR)

| # | POUR | Finding | Status |
|---|---|---|---|
| P1 | Robust / Perceivable | Drawing symbols were read aloud by screen readers | **Fixed** (SVG text `aria-hidden`; the drawing has one `aria-label`) |
| P2 | Perceivable | A bare "⚠" icon was announced with no meaning | **Fixed** (icon hidden; "Caution:" / "احتیاط:" text instead) |
| P3 | Operable / Robust | Overlay rings duplicated the MAIN WASH / SOFTENER buttons | **Fixed** (`aria-hidden`, `tabindex=-1`; the real buttons are the only controls) |
| P4 | Operable | Home tab order: Language → Is this normal? → First wash → Facilitator; disabled task is skipped | As intended |
| P5 | Operable / Understandable | Focus moves to the step title on each step; errors use `role="alert"` and take focus; dialog returns focus to its opener; Esc closes it | Verified in code |
| P6 | Understandable | `lang` and `dir` switch to `ur` / `rtl` with the language button | Verified |
| P7 | Operable | Next uses `aria-disabled`, so it stays focusable; pressing it moves focus to the message saying what is missing | By design |
| P8 | Operable | Facilitator buttons were 40 px (below the 44 px target) | **Fixed** in session 2 (now 44 px) |
| P9 | Operable | New: the sticky bottom bar could cover a focused element (focus not obscured, WCAG 2.4.11) | **Fixed** (`scroll-padding-bottom` on `html`); needs a manual check |
| P10 | Operable | New: placing the ring needed a pointer. Added keyboard (focusable camera view, arrow keys, Enter) and a "Place ring at the marked spot" button | **Fixed in code; not manually tested** |
| P11 | Understandable | New: on the live camera the app said "Found the …", which overclaimed (recognition is simulated). Now reads "Ring placed on the … Check it matches what you see." | **Fixed** |
| P12 | Perceivable | New palette: contrast checked by calculation (white on indigo about 9:1; dark indigo on pink about 5.3:1; mauve is decorative only) | Re-check with a contrast tool |
| P13 | Perceivable | The new circular progress ring is `aria-hidden`; "Step n of 6" text carries the meaning | By design |

## 3.3 Deferred

| # | POUR | Issue | Why deferred |
|---|---|---|---|
| D1 | Perceivable | No text description of the live camera scene for blind users | Out of scope at this fidelity. Mitigated: every step gives the instruction and the result as text |
| D2 | Understandable | Urdu text is AI-drafted and unchecked by a native reader | Needs a teammate |
| D3 | Operable | Tap-to-place on the camera needs sight to place the ring on the real part | The keyboard path moves the ring but cannot verify the part; a blind user would need a different design (D5 or later) |
| D4 | Robust | No testing with TalkBack / VoiceOver / NVDA | Needs a person and a device |
| D5 | Perceivable | Layout and contrast in Urdu / RTL with the new styles not checked | Needs a person |

## 3.4 Keyboard-only walkthrough log (to be completed by a person)

Method (suggested): Chrome or Edge on a laptop, mouse unplugged or untouched. Use Tab, Shift+Tab, Enter, Space, arrow keys and Esc through the whole core task and each error path. Record every point where focus is lost, illogical or unreachable.

| # | Screen | Action | Expected | Actual | POUR | Fixed / deferred |
|---|---|---|---|---|---|---|
| K1 | | | | | | |
| K2 | | | | | | |
| K3 | | | | | | |

Checklist to cover: Home; Steps 1 to 6 (including the camera view arrow-key placing); error (a), (b), (c); "Is this normal?" open, answer, back, close; language switch; facilitator panel; Done.

## 3.5 Screen-reader walkthrough log (to be completed by a person)

Method (suggested): NVDA with Chrome on Windows, or TalkBack on Android. Listen to the whole core task and each error. Record meaningless announcements and illogical reading order.

| # | Screen | What was announced | Problem | POUR | Fixed / deferred |
|---|---|---|---|---|---|
| S1 | | | | | |
| S2 | | | | | |
| S3 | | | | | |

## 3.6 Fixed vs deferred (summary)

- **Fixed:** P1, P2, P3, P8, P9, P10, P11.
- **Deferred:** D1 to D5 above, plus the manual walkthrough logs.
- **Needs a manual re-check before submission:** P9, P10, P12 and all the "Fixed" items after any further change (this is the Part B accessibility re-check).
