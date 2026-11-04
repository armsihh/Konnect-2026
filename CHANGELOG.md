# Changelog

Newest first. Add a line here for every change you make.

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
