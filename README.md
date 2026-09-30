# HomePilot — Alexa+ Simulated Experience

HomePilot is a browser-based simulated Alexa+ experience built for the **Build, Ship, Shape: Amazon Developer Hackathon (2026)** Alexa+ track.

## Problem
Household requests are deceptively complex: people mix outcomes, deadlines, competing tasks, fatigue constraints, and consequential actions in one sentence. Typical assistants either answer conversationally or execute too eagerly. HomePilot turns a request into an explicit, inspectable plan with conflict detection and confirmation gates.

## What it demonstrates
- Natural-language household planning in a conversational interface.
- Deterministic task extraction and time-window reasoning.
- Conflict detection when requested work does not fit the available window.
- Explainable agent trace showing the planning stages.
- Confirmation gates for spending, messaging, account changes, and safety-sensitive device actions.
- Responsive web UI suitable for a simulated Alexa+ experience demo.

## Run locally
No build step and no paid API are required.

```bash
python3 -m http.server 8080
# open http://localhost:8080
```

## Test
```bash
node tests/agent.test.js
```

## Demo prompts
1. `Plan my evening: dinner by 7:30, laundry, 30 minutes of study, and lights out by 10:30.`
2. `I have 45 minutes before guests arrive. Prioritize the kitchen, living room, and a quick snack without overloading me.`
3. `Create a calm morning routine from 6:30 to 8:00 with breakfast, packing, and 20 minutes of exercise.`

## Design principles
**Transparent over magical.** Users see assumptions, conflicts, and the resulting plan.

**Safe by default.** HomePilot does not claim to have performed external actions. Consequential actions require explicit confirmation.

**Useful without hardware.** The project follows the hackathon's permitted simulated Alexa+ web-experience path; the simulation source is contained in this repository.

## Architecture
`index.html` provides the simulated conversational surface. `app.js` implements the planning agent: intent parsing → task extraction → constraint normalization → schedule generation → conflict checks → confirmation policy. `styles.css` provides the responsive UI. `tests/agent.test.js` validates parsing and non-overlapping schedule invariants.

## Product feedback for Amazon
The simulated-experience route makes Alexa+ experimentation accessible to builders who do not have preview access to the gated Alexa+ Add-on tools. A useful next step would be a public compatibility harness that lets builders validate conversational flows against Alexa+ interaction conventions before gaining preview access.

## Hackathon status
Working prototype. Registration, final Devpost submission, public demo-video upload, and any entrant attestations must be completed by the entrant.
