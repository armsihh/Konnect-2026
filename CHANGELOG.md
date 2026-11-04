# Changelog

Newest first. Add a line here for every change you make.

## 2026-11-04 (session 3): Part A items, wireframe update, two build fixes

- Added the `part-a/` folder: README index, information architecture (card sort), wireframes write-up, accessibility audit (AI pre-check only; manual K and S logs left blank), critique record (AI reviewer, rounds 1 and 2), AI-use note, reflection (blank for the team).
- Wireframes: added row 3 to the draw.io file (P1 Placing, P2 Checking, P3 Found for tap-to-place) and exported `part-a/wireframes.svg` (simplified rendering; the .drawio is the master).
- Build fix: on the live camera the success text said "Found the …", which overclaimed because recognition is simulated. It now says "Ring placed on the …. Check it matches what you see." (English and AI-drafted Urdu).
- Build fix: `scroll-padding-bottom` so the sticky Back/Next bar does not cover a focused control.
- Updated `CONTEXT.md` (repo layout, Part A pointers, open work) and `README.md`.
- Not tested: manual keyboard/screen-reader walkthroughs, live camera on a phone, Urdu layout.

## 2026-11-04 (session 2b): new palette and UI restyle

**Why:** the team supplied a 4-colour palette and an inspiration screenshot (not to be copied 1:1).

- New palette: pink `#F9B1B6`, mauve `#AD7099`, violet `#8A6499`, indigo `#3F3D8A` (sampled by eye from the swatch image; confirm exact hex values if the team has them). Indigo is brand/buttons/headings; pink is accent surfaces; **mauve is decorative only** (white on mauve is 3.8:1). Success green, error red and caution amber are kept separate so state is never confused with decoration.
- Indigo hero header with a 4-band palette stripe; white sheet with rounded top; "Is this normal?" is a pink pill (dark indigo text, about 5.3:1).
- Pill buttons with a raised shadow (signifier of pressable); radius 16 px cards; bottom action bar (Back / Next) now sticky so it is always visible.
- Step header is a pink card with a circular progress ring (n/6) replacing the segmented bar. The ring is decorative (`aria-hidden`); the "Step n of 6" text remains.
- Home: icon card plus task button with a chevron (flips in RTL); the disabled task is visibly muted.
- Done screen: large green check (decorative).
- Dialog: pink top edge and tinted empty state. Info status boxes use pink-soft with an indigo icon.
- Focus ring is indigo on light surfaces and white on the indigo header.
- Behaviour, text, focus management and ARIA are unchanged. **Contrast of the new pairs has been checked by calculation only; re-run the manual accessibility checks.**
- Not yet checked: Urdu/RTL layout with the new styles, live camera on a phone.

## 2026-11-04 (session 2): tap-to-place on the live camera

**Why:** the old overlay used fixed screen positions. On a real machine the rings would not line up with the real tray or panel.

- Added **tap-to-place**: on the live camera the user taps the real part once; the ring moves there. Everything else in that step group (MAIN WASH / SOFTENER compartments, "Full to here" line, tags) moves with it.
  - Anchor groups: tray (steps 1 and 2), drum (3), display (4), control panel (5).
  - Step 2 reuses the tray placement from step 1. Going back to a placed step keeps its ring.
  - Offsets are clamped so the ring stays inside the view.
  - Step 6 on the live camera shows only the "Click = lid locked. Normal." tag (no ring).
- **Keyboard and non-pointer access for placing:** the camera view is focusable. Arrow keys move the ring, Enter places it. A "Place ring at the marked spot" button does the same.
- Added a **"Move ring"** button once a part is found (live camera, steps 1 to 5).
- Added a new recognition state, **checking** ("Checking the …", loading style), using the mock recognition service (700 ms).
- Drawing mode is unchanged: fixed positions and the 2 s auto-recognise.
- Added a **mock backend in the page**:
  - `mockRecognise()` returns a simulated result.
  - `log()` stores events in `localStorage` (`konnect_log`, last 300).
  - Facilitator panel: **Make next check fail** (triggers error a, part not recognised) and **Download session log**.
- Facilitator buttons raised from 40 px to 44 px (fixes deferred accessibility item D3).
- Added four new strings in English and Urdu: `place`, `placeHere`, `checking`, `moveRing`. **The Urdu is AI-drafted and needs a native-reader check.**
- Created `site/index.html` (copy for GitHub Pages) and this documentation.

**Tested** (headless-style, in a desktop browser with a fake camera stream): placing by tap and by keyboard; forced "not recognised" error and recovery; softener error keeps Next disabled; overfill error and "Check again"; no JavaScript errors up to step 4.
**Not tested:** steps 5 and 6 on the live camera, Urdu mode with placement, a real phone over HTTPS.

## 2026-11-04 (session 1): initial D4 build

- Built the single-file web app: Home, 6 steps, Done, "Is this normal?" dialog, English/Urdu with RTL.
- Built the three error paths: (a) part not recognised, (b) load above the line, (c) detergent in SOFTENER; plus a camera-blocked path with a drawing fallback.
- Built the design system (palette tokens, 3-level type scale, 4/8/16/24/32 spacing, components, 8 states).
- Wizard-of-Oz facilitator panel with auto-recognise after 2 s.
- Produced the card sort (24 cards, 5 AI-simulated participants, 93% closed-check agreement), the draw.io wireframes, and the Word report.
- Automated accessibility pre-check (AI-run, not the manual walkthrough): fixed drawing symbols being read aloud, bare "⚠" announcement, and duplicated overlay controls.

## Earlier project stages (not in this repo)

D0 assumption, D1A research plan, D1B fieldwork (5 sessions), D2 synthesis, D3 concept selection (M4-E Camera overlay). Summary in [CONTEXT.md](CONTEXT.md).
