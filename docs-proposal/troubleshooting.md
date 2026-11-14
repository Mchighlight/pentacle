# Troubleshooting

Find your symptom, then work through the checks in order.

## Pentacle Web can't connect to the daemon

The page loads, but sessions and hosts don't appear, or it shows a connection error.

1. Is the daemon running? Its terminal should show a line with
   `listening on 127.0.0.1:7791` (or your port).
2. Does `chatStream.url` in your `pentacle.config.js` match that host and port?
3. Does the token file in `chatStream.tokenPath` exist, with mode `0600`, in a
   folder with mode `0700`?

**Fix:** start the daemon, fix the URL or recreate the token
([Quickstart step 2](quickstart.md#2-create-the-web-credential)), then reload the page.

## `agent-orch: command not found`

The CLI is installed inside the Python venv.

**Fix:** `. .venv/bin/activate` from the `pentacle` folder, then
`command -v agent-orch`. For agent panes, make sure that `bin` folder is on the
`PATH` the daemon starts seats with.

## `unknown_local_host` or `unsupported_host`

The host name you used is not in the machines file.

**Fix:** the CLI's host id (`local_host_id` or `AGENT_ORCH_HOST_ID`) must match
a `name` in the machines file. Add the host, or fix the name. See
[machines file](../docs/agent_orchestration_setup.md#machines-file).

## `host_offline`, or a host shows offline on the phone

Pentacle can't reach that machine.

Check, in order:

1. Is the machine awake? A laptop with the lid closed sleeps, and its seats
   pause with it.
2. Is it online and reachable over SSH from the daemon host?
3. Are the `tmux_bin`, `claude_bin` and `codex_bin` paths in the machines file
   correct for that machine?

**Fix:** wake the machine, fix the path, then run `agent-orch list` again.

## A new seat never starts working

The agent CLI may be waiting on a first-run screen in its pane, such as a
"trust this folder" prompt or a sign-in.

**Fix:** open the seat in **Terminal** view, answer the prompt once, and try
again. Signing in to the agent CLI once in a normal terminal on that host
prevents most of these.

## A question never shows up on my phone

1. Did the agent use `agent-orch prompt ask`? Questions asked only in chat text
   are not saved as questions.
2. Is the phone paired with the same daemon? Open **Settings** on the phone and
   check the host list.
3. Open **Questions** (the **?** button in the Assistant header).

## The phone pairing link doesn't work

Pairing links work once and expire after 10 minutes.

**Fix:** make a new one. See [Pair your phone](mobile-pairing.md).

## A seat says it's done, but nothing arrived

Completion is a **report**, not a chat message.

**Fix:** open the seat and ask it to file its report with `agent-orch report`.
A seat that only wrote "done" in chat did not file one. A parent can wait for
reports with `agent-orch await`.

## Still stuck?

- Search [open issues](https://github.com/HJK6/pentacle/issues).
- Open a new issue with the symptom, the command you ran and its exact output.
  Remove tokens, enrollment links and private paths first.
