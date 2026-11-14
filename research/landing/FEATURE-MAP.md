# What Pentacle does today (truth table for the page)

Checked 2026-11-14 against `HJK6/pentacle` main `f369bc7f` (README + docs/) and
`HJK6/pentacle-mobile` main `001ca44` (README + docs/), plus the live
`agent-orch` CLI. Planned work = open issues #542–#566 → say **coming**.

Rule for copy: if a line on the page is not backed by a row marked **today**,
it must say "coming" or be cut.

| Outcome on the page | Feature behind it | Status | Evidence |
| --- | --- | --- | --- |
| Talk to one assistant; it routes the work | Always-on front-desk assistant (triage, delegation, follow-ups, durable questions) | today | README principle 6; docs/assistant.md |
| Big jobs get a lead with helpers | Agents spawn, message, commission and report to other agents | today | README principle 5; `agent-orch spawn/tell/report` |
| All your computers work as one | Multi-host fleet: macOS, Linux, Windows via WSL; spawn on a chosen host | today | README quick start; hosts config; `agent-orch ssh` |
| Wake a sleeping machine from the picker | Wake offline host + online state | coming (#559) | issue #559 |
| Use the agents you already pay for | Claude, Codex, Cursor, Gemini CLIs; ChatGPT "Dot" agent via adapters | today | README; docs/cursor_provider.md, gemini_provider.md, connect-a-dot-agent.md |
| Spread work across several accounts | Pooled provider accounts + usage accounting | today | docs/provider_accounts.md, usage_accounting.md |
| Agents ask you, you answer from the phone | Durable questions (`agent-orch prompt ask`) + mobile Questions deck | today | mobile docs/QUESTIONS_OVERLAY.md |
| Risky actions wait for your face | Face ID approvals: Secure Enclave P-256 key on iPhone signs the daemon challenge | today (iPhone) | mobile docs/PRIVILEGED_CONSENT.md; docs/REMOTE_AUTH.md |
| Your phone buzzes when you're needed | Push via Expo → APNs (generic notification for approvals) | today | mobile docs/PRIVILEGED_CONSENT.md |
| Answer straight from the notification | Actionable push | coming (#548) | issue #548 |
| Lock-screen view of who needs you | Live Activity | coming (#554) | issue #554 |
| Desktop alert + sound when something finishes | Web alerts | coming (#547) | issue #547 |
| Know where everything stands | Work lanes, lane update cards, session status cards, specs dashboard | today | docs/web_work_lanes.md; mobile docs/assistant_and_lanes.md |
| One standup board (needs you / in flight / blocked / stale) | Standup board | coming (#549) | issue #549 |
| Read the result, comment, send it back | Reports and assets with per-block comments | today | docs/reports_showcase.md, report_assets.md |
| It runs while you're away | Recurring schedules (nightly / weekdays / weekly, IANA time zone) from the CLI | today (CLI) | `agent-orch schedule recurring` |
| Manage schedules in the web app | Schedules UI: create, Run now, history | coming (#556) | issue #556 |
| Talk instead of type | Voice to the assistant on mobile; web voice answers; optional room microphone | today | mobile docs/voice_everywhere.md; docs/web_voice_answers.md, room_mic_conversation.md |
| Nothing is forgotten between chats | Shared memory, work specs and procedures synced to every host | today | README principle 2; PROCESS.md |
| "Done" means checked | Specs with status, evidence and independent QA; rules enforced by the daemon | today | README principles 3–4; governance_tripwires.md |
| Watch an agent's terminal live from web/phone | Read-only live terminal | coming (#542, #543) | issues |
| Install from the App Store, pair in a minute | App Store + pairing + onboarding | coming (#564) | issue #564 (today: build from source) |
| Docs site | Task-first docs site | coming (#565) | issue #565 |
| Runs on your computers | Daemon + Pentacle Web are self-hosted; remote access via your own private network (Tailscale identity) | today | README; server/README.md |
| Open source | MIT (both repos) | today | LICENSE |

## Things we must not claim

- No hosted/cloud Pentacle, no sign-up, no pricing tiers, no SOC 2 or audits.
- Not "no third parties at all": model calls go to your AI provider and phone
  alerts go through Apple's push service via Expo. Say exactly that.
- Not "one-click install" or "in the App Store" (both coming).
- Not Android support (iPhone is what's tested; Face ID is iPhone-only).
- No customer logos, user counts or testimonials (none exist yet).
- Market research, vendor search, meeting prep, CRM work etc. are *examples of work agents do
  inside Pentacle*, not special built-in features. Copy must frame them that way.
