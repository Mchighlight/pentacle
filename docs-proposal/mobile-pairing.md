# Pair your phone

Connect Pentacle Mobile to your daemon so you can read seats and answer
questions from your phone. About 5 minutes once the app is installed.

## Before you start

- The daemon is running. See the [Quickstart](quickstart.md).
- Pentacle Mobile is installed on your phone. Today you build it yourself; see
  the [Pentacle Mobile README](https://github.com/HJK6/pentacle-mobile#manual-quick-start).
- Your phone can reach the daemon's computer, for example on the same network,
  a VPN such as Tailscale, or a tunnel. Note the address the phone will use,
  such as `ws://<computer-address>:7791`.

## 1. Make a pairing link

On the computer that runs the daemon, as the same user, with the venv active,
from the `pentacle` folder:

```sh
python services/chat-stream-v2/tools/mobile_enrollment_cli.py \
  --ws-url ws://<computer-address>:7791 --label phone
```

It prints JSON with a `url` that starts with `pentacle://enroll`.

- The link works **once**.
- It expires after **10 minutes**.
- Treat it like a password. Don't paste it into chats, issues or screenshots.

## 2. Open the link on your phone

Get the link to your phone privately, for example:

- AirDrop or a note to yourself, then tap it, or
- Make a QR code from it on your computer and scan it with the phone camera.

The phone opens Pentacle Mobile.

**Check:** the app may ask for Face ID. Then it opens the **Assistant** tab.

## 3. Try it

1. Tap the left header button to open **Sessions**.
2. Tap **+**, pick the host (for example `local`) and start a session.
3. Send a short message.

**Check:** the reply appears on the phone and in Pentacle Web.

## What the phone shows

- **Assistant**: your front desk's conversation and lane updates.
- **Sessions** (left header button): every seat on every host.
- **Questions** (**?** button): open questions from agents. Answer here.
- **Settings**: hosts, limits and app options.

## If it doesn't work

| What you see | What to do |
| --- | --- |
| Link opens nothing | Pentacle Mobile is not installed on this phone, or it was built with a different app id. |
| "Expired" or "already used" | Make a new link (step 1). Each link works once, for 10 minutes. |
| App opens but can't connect | The phone can't reach `--ws-url`. Open that address's host and port from the phone's network, or use your VPN address. |
| Host shows offline | The computer is asleep or the daemon stopped. Wake it and check `agent-orch list` on it. |

## Next

- [Concepts](concepts.md): seats, front desk, prompt ask
- [Troubleshooting](troubleshooting.md)
