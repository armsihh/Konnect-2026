# 4. Critique record

> **This is an AI-reviewer critique, not a studio session with classmates.** Claude reviewed the wireframes and the current build against the D2 themes, requirements and Norman / Gestalt principles. The team has not yet confirmed or edited these points.
>
> **Team confirmation:** ☐ Reviewed by ____________  ☐ Date ____________

Two rounds. Round 1 (earlier session) reviewed the wireframes W1 to W8 and E0 to E3. Round 2 (this session) re-ran the critique on the updated UI: tap-to-place, the new palette and layout, and the sticky action bar.

## Round 1 (wireframes)

| # | Screen | Point | Status |
|---|---|---|---|
| 1 | W3 | The compartments show symbols only (the T1 problem) | Fixed: words under each symbol |
| 2 | W4 | The "where is your load?" self-check could be skipped | Fixed: Next is disabled until answered |
| 3 | W6 | Two checkboxes may annoy the try-first user (persona C) | **Open: test in D5B** |
| 4 | W1 | A disabled task looks broken | Fixed: labelled "Not in this prototype" |
| 5 | E1 | The error must say what to do, not only what went wrong | Fixed |
| 6 | W7 | The app cannot hear the click | Disclosed as Wizard-of-Oz |
| 7 | All | T2 signals appear at many moments | Fixed: global "Is this normal?" |
| 8 | All | Persona A may stay on paper; a printed fallback may be needed | **Deferred to D5** |
| 9 | W1→W2 | No path for a blocked camera | Fixed: added E0 |

## Round 2 (current UI)

| # | Screen | Principle | Point | Status |
|---|---|---|---|---|
| 10 | Live steps | Honesty / feedback | "Found the …" claimed recognition the app does not do. A careful first-timer (persona A) could trust a ring on the wrong part | **Fixed**: now "Ring placed on the …. Check it matches what you see." |
| 11 | P1 | Signifier | The camera view needed a clearer cue that it is tappable | Fixed: dashed ring, crosshair cursor, instruction text under the camera |
| 12 | P1 | Accessibility | Placing needed a pointer | Fixed: keyboard path and "Place ring at the marked spot" button; **not manually tested** |
| 13 | P2 | Feedback | The tap needed immediate feedback | Fixed: "Checking…" at once, announced |
| 14 | All | Visibility | The sticky bottom bar can hide a focused control | Fixed: scroll padding; needs a manual keyboard check |
| 15 | Header | Consistency | The "Is this normal?" pill is pink while the other header controls are outlined; the contrast is fine but this is the only filled pink item | Kept deliberately: it is the global help, and the pink marks it as special |
| 16 | W1 | Signifier | The disabled "Other tasks" shows an empty grey circle that can look like a loading spinner | **Open**: replace with a lock icon or remove the circle |
| 17 | W3, W4 | Common region | Error boxes use red; the caution box is amber and sits next to it. Colour-blind users depend on the "!" icon and the words | Mitigated: icons and words are always present |
| 18 | All | Gestalt (proximity) | The ring progress "n/6" and the "Step n of 6" text repeat each other | Kept: the ring is decorative, the text is the accessible one |
| 19 | P3 | Control | After placing a ring there was no way to adjust it | Fixed: "Move ring" button |
| 20 | Step 5 | Efficiency | Two checkboxes for one outcome (see point 3) | **Open: D5B** |
| 21 | All | Language | Urdu not checked with a native reader; RTL layout not checked with the new styles | **Open** |
| 22 | Live camera | Limitation | A user cannot be stopped from acting before reading the step (D3 risk 5) | Known limit |

## Reflection on the critique itself

- The AI reviewer found issues the earlier design missed (point 10 was the most important), but it can only judge against principles and the evidence we gave it. It cannot tell us how real users react.
- The open points (3, 8, 16, 20, 21) go into D5A / D5B planning.
