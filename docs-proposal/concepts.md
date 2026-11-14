# Concepts

The words used everywhere in Pentacle, in one place.

Pentacle has one idea: **you talk to one assistant; it hands work to agents on
your machines, tracks it, and asks you only when it needs you.** Eight words
make that work.

## Host

A machine that runs agents: your laptop, a desktop, a server, or WSL on a PC.
Each host has a short name, such as `local`. The **daemon** runs on one host and
reaches the others over SSH. Hosts are listed in the machines file.

## Seat

One agent session: a Claude, Codex or other agent CLI running in its own tmux
pane on a host. A seat has an id like `local:v2-1a2b3c4d`, a title, and a
transcript you can read in Web or on your phone. Seats are cheap. Start one per
task and close it when the task is done.

## Front desk (your assistant)

The always-on seat you talk to. It triages what you ask, starts other seats,
follows up, and tells you what happened. You give it a name. It is optional;
without it you talk to seats directly. See [docs/assistant.md](../docs/assistant.md).

## Roles: lead, worker, QA

A seat can have a role.

- **Lead**: owns one goal end to end. It plans, starts helpers, and reports back.
- **Worker**: does one bounded job for a lead and reports.
- **QA**: checks someone else's work independently before it counts as done.

A seat started by another seat has a **parent**. Reports go to the parent.

## Spec

A work item written down: goal, status, evidence and next step. Specs live in
the process workspace under `process/work/<status>/`, for example
`ready_for_dev`, `in_progress`, `needs_qa`, `completed`. A spec outlives any
seat, so another agent can pick up where the last one stopped.

## Lane

A stream of work for one product area, such as "mobile" or "dashboards". A lane
groups related specs and seats, and is `active`, `paused` or `blocked`. Your
assistant posts lane updates (started, blocked, done) so you can follow the big
picture without reading every seat.

## Tell, send and report

How seats talk to each other.

- **tell**: a one-way message. The sender keeps going.
- **send**: a task for another seat. The sender expects a report back.
- **report**: a seat's structured "I'm done" with a summary and evidence. Its
  parent can wait for it.

```sh
agent-orch tell <seat-id> "I changed the parser; reload before testing."
```

## Prompt ask (questions for you)

When an agent needs you, it runs `agent-orch prompt ask`. The question is saved
with an id and shows up in **Updates** on Web and on your phone. Your answer
goes back to the agent, even if you answer hours later or from another device.

```sh
agent-orch prompt ask --title "Deploy now?" --body "Tests pass." \
  --response-mode single_choice --option Yes --option "Not yet"
```

## Status card

A seat's short public summary: goal, plan steps, and latest update. Seats
update it as they work, so you can see progress without opening the transcript.

```sh
agent-orch status --goal "Fix login bug" --plan "Reproduce" --plan "Fix" --update "Reproduced"
```

## How they fit together

You ask the **front desk** for something. It opens a **lane** or adds to one,
writes a **spec**, and starts a **lead** seat on a **host**. The lead keeps its
**status card** current, starts **workers**, and sends you a **prompt ask** if
it needs a decision. When it finishes, it files a **report**, a **QA** seat
checks the work, and the lane update tells you it's done.

## Next

- [Quickstart](quickstart.md)
- [Troubleshooting](troubleshooting.md)
- Full CLI: [services/agent-orch/README.md](../services/agent-orch/README.md)
