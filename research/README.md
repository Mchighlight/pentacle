# Pentacle research

Research and proposals for [HJK6/pentacle](https://github.com/HJK6/pentacle),
written against `main` `f369bc7f`. Nothing here changes product code.

## Feature requests filed

Filed on HJK6/pentacle after comparing Pentacle with other agent workspace apps.

| # | Area | Request |
| --- | --- | --- |
| [#542](https://github.com/HJK6/pentacle/issues/542) | Web | Read-only terminal view of a seat (daemon snapshot/stream + watch-only web mode) |
| [#543](https://github.com/HJK6/pentacle/issues/543) | Mobile | Read-only live terminal view of a seat |
| [#544](https://github.com/HJK6/pentacle/issues/544) | Mobile | Composer redesign: + opens an attach sheet, mic on the right |
| [#545](https://github.com/HJK6/pentacle/issues/545) | Web | Exact seat state from Claude Code hooks (working / done / failed / needs answer) |
| [#546](https://github.com/HJK6/pentacle/issues/546) | Web | "Done, not seen yet" state per seat |
| [#547](https://github.com/HJK6/pentacle/issues/547) | Web | Alerts with sound when a seat finishes, fails or needs an answer |
| [#548](https://github.com/HJK6/pentacle/issues/548) | Mobile | Actionable push: answer or open a seat from the notification |
| [#549](https://github.com/HJK6/pentacle/issues/549) | Web | One standup board: Needs you / In flight / Blocked / Stale |
| [#550](https://github.com/HJK6/pentacle/issues/550) | Web | Waiting asks between seats that resume with the answer |
| [#551](https://github.com/HJK6/pentacle/issues/551) | Web | `agent-orch explain <seat>` and `send --wait-until-settled` |
| [#552](https://github.com/HJK6/pentacle/issues/552) | Web | Bug: detect and avoid seats stuck at startup |
| [#553](https://github.com/HJK6/pentacle/issues/553) | Web | `agent-orch doctor`: symptom → fix checks |
| [#554](https://github.com/HJK6/pentacle/issues/554) | Mobile | Live Activity / lock screen: seats that need you |
| [#555](https://github.com/HJK6/pentacle/issues/555) | Web | Worktree lifecycle scripts and crash-safe cleanup (closed) |
| [#556](https://github.com/HJK6/pentacle/issues/556) | Web | Schedules: create, Run now and run history in the web UI |
| [#557](https://github.com/HJK6/pentacle/issues/557) | Web | Ports / preview links per seat |
| [#558](https://github.com/HJK6/pentacle/issues/558) | Mobile | Polish: message cache, haptics, machine grouping, iPad layout |
| [#559](https://github.com/HJK6/pentacle/issues/559) | Web | Wake an offline host; online state in the new-session picker |
| [#560](https://github.com/HJK6/pentacle/issues/560) | Web | Per-seat agent config instead of the shared global agent folder |
| [#561](https://github.com/HJK6/pentacle/issues/561) | Web | Smaller ideas: command palette, rich prompt, token alerts, handoff |
| [#562](https://github.com/HJK6/pentacle/issues/562) | Mobile | Smoothness stack (libraries + Expo upgrade) |
| [#563](https://github.com/HJK6/pentacle/issues/563) | Meta | Labels for #542–#562 |
| [#564](https://github.com/HJK6/pentacle/issues/564) | Mobile | App Store install, easy pairing and first-run onboarding |
| [#565](https://github.com/HJK6/pentacle/issues/565) | Web | Task-first docs site (quickstart, concepts, pairing, troubleshooting, llms.txt) |
| [#566](https://github.com/HJK6/pentacle/issues/566) | Demo | Feature tour of another agent workspace app |

## Docs proposal

Branch [`docs-proposal`](https://github.com/Mchighlight/pentacle/tree/docs-proposal/docs-proposal):
a task-first docs structure with sample pages (quickstart, concepts, mobile
pairing, troubleshooting, `llms.txt`). Goes with #565.

## Intro page (this branch)

[`research/landing/`](landing/): everything needed to build a Pentacle intro
page that leads with outcomes: "your one-person company, fully staffed".

| File | What it is |
| --- | --- |
| [LANDING-PLAN.md](landing/LANDING-PLAN.md) | Section-by-section plan: purpose, layout and visual for each section; visual system |
| [COPY.md](landing/COPY.md) | All page copy: hero, outcome blocks, how it works, comparison, trust, FAQ, footer |
| [FEATURE-MAP.md](landing/FEATURE-MAP.md) | What Pentacle does today vs. what's coming, with evidence; claims to avoid |
| [ASSETS.md](landing/ASSETS.md) | Screenshots, GIFs and diagrams needed, with sizes and how to capture each |
| [prototype/index.html](landing/prototype/index.html) | Single-file static prototype, dark + light, placeholder boxes for assets |
