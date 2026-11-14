# Docs proposal: task-first Pentacle docs

**Status:** draft for discussion. Nothing in `docs/` is changed. The pages in this
folder are samples written against `HJK6/pentacle` `f369bc7f`.

## Why

Pentacle has a lot of documentation (91 files in `docs/`, plus long READMEs for
the daemon, the CLI and the web host). Most of it is accurate and detailed. The
problem is finding the right page and knowing where to start:

- `docs/` is one flat folder. User guides sit next to wire contracts, test
  harness notes and governance records. Nothing tells a new reader which is which.
- There is no short path from "I cloned the repo" to "an agent did something for me".
- Core words (seat, front desk, lead, lane, spec, tell, prompt ask, status card)
  are used everywhere but never defined in one place.
- Phone pairing is only written for agents doing the setup.
- There is no symptom-first troubleshooting page.
- The `agent-orch` CLI has about 60 subcommands, and most have no one-line help.
- There is no `llms.txt`, even though setup is meant to be done by an agent.

Other agent tools' docs solve this with a small, fixed structure: a short
"start here" path, one concepts page, task pages named by outcome, a symptom ->
fix troubleshooting page, a reference section, and an index made for agents.

## Proposed nav tree

```text
Start here
  What is Pentacle?            one page, 60 seconds
  Quickstart                   install -> first agent -> first answer (sample: quickstart.md)
  Concepts                     the 8 words everything else uses (sample: concepts.md)
  Let an agent set it up       today's AGENT_SETUP.md

Use Pentacle
  Talk to your assistant       front desk, triage, lanes
  Start and manage agents      spawn, tell, close, hand off
  Answer questions             prompt ask, Updates, phone
  Track work                   specs, lanes, status cards, reports
  Use it from your phone       pairing (sample: mobile-pairing.md), what the phone shows
  Voice                        voice answers, room mic
  Add more machines            machines file, remote hosts, SSH/WSL
  Provider accounts and usage  accounts, limits, usage accounting

Recipes (named by outcome)
  Hand a task to a lead and get a report back
  Ask the owner a question from an agent
  Check your whole fleet from your phone
  Connect a friend's or a ChatGPT agent

Help
  Troubleshooting              symptom -> check -> fix (sample: troubleshooting.md)
  What happens when...         daemon restart, laptop sleep, seat dies, phone offline
  FAQ

Reference
  agent-orch CLI               one page per command group, generated from --help
  Configuration                pentacle.config.js, machines file, env vars
  Daemon and web host          today's service READMEs
  Process workspace            PROCESS.md, spec templates

Internals (for contributors)
  Architecture, contracts, governance, test harness, release
  (today's design and contract docs move here unchanged)
```

## Page rules

1. One page = one task or one idea. Title says the outcome.
2. First line under the title: one sentence on what the page gets you.
3. Numbered steps. After each command, say what you should see.
4. Define a Pentacle word the first time a page uses it, or link to Concepts.
5. End with "Next" links.
6. Short sentences. No internal words ("authority", "fail closed") on user pages.
7. Internals live in Internals. User pages link to them, never the other way round.
8. Every page also builds as Markdown at a stable path and is listed in `llms.txt`.

## Sample pages in this folder

| File | What it shows |
| --- | --- |
| [quickstart.md](quickstart.md) | Install to first answer, with checks after each step |
| [concepts.md](concepts.md) | The 8 core words, each in a few sentences |
| [mobile-pairing.md](mobile-pairing.md) | Pair a phone, written for a person, not an agent |
| [troubleshooting.md](troubleshooting.md) | Symptom headings, ordered checks, fixes |
| [llms.txt](llms.txt) | Index for agents: one line per page |

## Smallest useful version

1. Add `docs/index.md` with the nav tree above, linking existing pages. No moves yet.
2. Add Quickstart, Concepts and Troubleshooting (the samples here, reviewed).
3. Add `llms.txt` at the repo root.
4. Later: move contract and test docs under `docs/internals/`, and generate
   the CLI reference from `agent-orch <group> --help`.
