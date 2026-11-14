# Quickstart

Go from a fresh clone to your first agent answering you in Pentacle Web.
About 10 minutes on one Mac or Linux machine.

> **Prefer to let an agent do it?** Give a coding agent
> [AGENT_SETUP.md](../AGENT_SETUP.md). It follows the same steps and stops when
> it needs you for a sign-in.

## Before you start

You need:

- macOS or Linux (on Windows, use WSL)
- Node.js 22.12+ and Python 3.11+
- tmux
- At least one agent CLI that is already signed in: `claude` or `codex`

Check:

```sh
node --version && python3 --version && tmux -V && command -v claude codex
```

You should see four version lines and at least one path.

## 1. Install

From the `pentacle` folder:

```sh
npm ci
python3 -m venv .venv
. .venv/bin/activate
python -m pip install -r services/chat-stream-v2/requirements.txt -e services/agent-orch
mkdir -p "$HOME/.config/pentacle" "$HOME/workspace"
chmod 700 "$HOME/.config/pentacle"
cp pentacle.config.example.js "$HOME/.config/pentacle/pentacle.config.js"
```

**Check:** `command -v agent-orch` prints a path inside `.venv`.

## 2. Create the web credential

Pentacle Web needs a key to talk to the daemon. This writes it to a private
file without printing it:

```sh
python services/chat-stream-v2/tools/operator_auth_cli.py issue --client-kind pentacle --label web |
  python -c 'import json,os,pathlib,sys; p=pathlib.Path.home()/".config/pentacle/desktop.token"; fd=os.open(p,os.O_WRONLY|os.O_CREAT|os.O_TRUNC,0o600); os.write(fd,json.load(sys.stdin)["code"].encode()); os.close(fd); p.chmod(0o600)'
```

**Check:** `ls -l ~/.config/pentacle/desktop.token` shows `-rw-------`.

## 3. Start the daemon

The daemon runs your agents. Leave this terminal open.

```sh
python services/chat-stream-v2/main.py --host 127.0.0.1 --port 7791 \
  --local-host local --db "$HOME/.config/pentacle/sessions.db" \
  --claude-bin "$(command -v claude)" --codex-bin "$(command -v codex)" \
  --spawn-cwd "$HOME/workspace" --projects-root "$HOME/.claude/projects"
```

`local` is the name of this machine inside Pentacle.

**Check:** the terminal prints `listening on 127.0.0.1:7791`. In a second
terminal, with the venv active, `agent-orch list` returns without an error.

## 4. Open Pentacle Web

In the second terminal:

```sh
npm run build:web
PENTACLE_CONFIG="$HOME/.config/pentacle/pentacle.config.js" node server --port 7795
```

Open `http://127.0.0.1:7795`.

**Check:** the page loads, and **New Chat** offers the host `local`.

## 5. Start your first agent

1. Click **New Chat**.
2. Pick the host `local`, then a provider and a model.
3. Type: `List the files in this folder and tell me what this project is.`

**Check:** the new session appears in the sidebar as working, then the agent
answers in the chat.

Each agent session is a **seat**. See [Concepts](concepts.md).

## 6. Get your first question

Agents in Pentacle ask you questions through **prompt ask**, so the question is
saved and shows up on every screen. Ask your agent:

```text
Use agent-orch prompt ask to ask me one yes/no question, then wait for my answer.
```

**Check:** a question card appears in **Updates**. Answer it. The agent
continues with your answer.

## You now know the core loop

Start a seat, give it work, answer its questions. Everything else in Pentacle
builds on this.

## Next

- [Concepts](concepts.md): the 8 words used across the docs
- [Pair your phone](mobile-pairing.md)
- Set up an always-on assistant: [docs/assistant.md](../docs/assistant.md)
- Add another machine: [docs/agent_orchestration_setup.md](../docs/agent_orchestration_setup.md)
- Something wrong? [Troubleshooting](troubleshooting.md)
