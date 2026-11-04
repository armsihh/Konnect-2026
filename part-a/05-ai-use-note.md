# 5. AI-use note

Tool used throughout: **Claude** (Claude Code, Anthropic). Team members directed the work, made the scope decisions, and review the output.

| Step | Tool | What the AI did | What the team did |
|---|---|---|---|
| Card sort | Claude | Simulated five card-sort participants grounded in the D1B observations; built the co-occurrence matrix and clusters; drafted the closed check | Chose the cards' source themes, named the IA categories, decided open sort then closed check |
| IA and navigation pattern | Claude | Proposed hub-and-spoke then sequential plus a global utility | Accepted it; to be explained by the team |
| Wireframes | Claude | Generated the draw.io geometry and the P1 to P3 screens; exported an SVG; wrote the Gestalt notes | Chose one appliance, one task, three error paths; reviews every screen |
| Accessibility audit | Claude | Said what to check; ran an automated pre-check; read the code against POUR | **Not yet done by a person**: manual keyboard and screen-reader walkthroughs are pending |
| Critique record | Claude | Acted as the reviewer (rounds 1 and 2) | To confirm or edit the points |
| Functional build (Part B) | Claude | Wrote the HTML, CSS and JS (tap-to-place, mock backend, design system, palette restyle, English/Urdu text) | Gave the palette and the inspiration image; chose live camera with pre-placed then tap-to-place overlay; tests on a phone; must be able to explain every part |
| Urdu text | Claude | Drafted all Urdu strings | A native reader on the team must check them |
| Accessibility re-check | Claude | Fixed issues found by code review | **Must be checked manually**: generated code is not accepted as accessible without a human check |
| Documentation | Claude | Wrote the README, changelog, master context and these files | Review for accuracy |

## What the AI did not do

- It did not run real user sessions, a real card sort, a studio critique, or a manual accessibility walkthrough.
- No identifiable participant data or raw audio was given to the AI (D1A data plan). Participants appear only as letters (F, H, G, I, J).
