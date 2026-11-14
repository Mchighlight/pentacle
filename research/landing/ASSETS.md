# Pentacle intro page: assets

Every asset uses **invented fixture data**: no real names, emails, phone
numbers, machine names, file paths, tokens or real conversations. Run the privacy
check at the bottom on each file before it goes anywhere.

Two capture rigs already exist:

- **Web:** the built web renderer fed by a fixture through its normal browser
  IPC transport, no live daemon (`docs/screenshots.md`, fixture
  `onboarding-single-host-v1`; headless Chrome 1440x900). Add fixtures for the
  scenes below the same way.
- **Phone:** the mobile screenshot harness renders the real Expo Router screens
  under react-native-web with an offline seed
  (`EXPO_PUBLIC_SCREENSHOT_HARNESS=1 npm run web`, then seed via
  `window.__pentacleHarness.seed(...)`; `docs/SCREENSHOT_HARNESS.md`). For OS
  UI (notifications, Face ID sheet) use the iOS Simulator with a test identity.

Already in the repos (reusable as-is after a fresh privacy check):

| File | Repo | Use on page |
| --- | --- | --- |
| `docs/images/onboarding-chat.png` | pentacle | A1 left panel, or A2 fallback |
| `docs/images/onboarding-new-chat.png` | pentacle | How it works step 3 (optional) |
| `docs/images/onboarding-terminal.png` | pentacle | "What's inside" (optional) |
| `docs/images/kitv2-reports-showcase.png` | pentacle | A6 report |
| `docs/images/mobile-assistant-home.png` | pentacle-mobile | A1 phone, A5 |
| `docs/images/mobile-assistant-questions.png` | pentacle-mobile | A4 left phone |
| `docs/images/mobile-assistant-sessions.png` | pentacle-mobile | spare |
| `docs/images/mobile-lanes-list.png` / `-map` / `-specs` | pentacle-mobile | A3 / A5 |
| `docs/images/mobile-session-status-card.png` | pentacle-mobile | A5 |
| `renderer/assets/pentacle-logo-source.png` | pentacle | A0 (derive sizes with Lanczos per docs/branding.md) |

## Needed assets

| Id | What | Format / size | Section | How to capture |
| --- | --- | --- | --- | --- |
| A0 | Logo mark + wordmark | SVG preferred; PNG 64/180/512 | Nav, footer, favicon | Derive from the logo source; trace a simple SVG ring + star for small sizes |
| A1 | **Hero composite**: web chat (left, ~70% width) + phone in front (right) showing the assistant tab with lane cards | PNG/WebP 2400x1350 (@2x of 1200x675), dark and light variants | 1 Hero | Web: new fixture "solo-company-v1" (one assistant chat: "Research three competitors and draft a pricing page", reply with a started lead). Phone: harness assistant tab seeded with 4 lane cards (research, job search, ops, build). Compose in Figma or a small HTML page, export @2x |
| A2 | Assistant chat: ask → "Started a lead on Desktop, I'll report back" | PNG 1600x1000 | 3a | Web fixture "solo-company-v1", Chat view, cropped to the conversation |
| A3 | Lead at work: lane with plan steps ticking + helper rows | GIF/MP4 ≤8s, ≤1.5 MB, 1200x800; poster PNG | 3b | Web fixture with a scripted lane timeline (step 1→3 done, one helper reports). Record with headless Chrome screencast, encode with ffmpeg (`-vf fps=15,scale=1200:-1`); loop; also export a still |
| A4 | Two phones: Questions card (left) + Face ID approval sheet (right) | 2 PNGs 1179x2556 (iPhone frame added in layout) | 3c | Left: harness `/pentacle/questions` seeded with 2 invented questions. Right: iOS Simulator, test daemon sends a consent offer, capture **Approve with Face ID** screen (Features → Face ID → Enrolled) |
| A5 | Phone: lane update cards + one status card | PNG 1179x2556 | 3d | Harness assistant tab + session status card fixture (reuse existing images if fresh) |
| A6 | Report with a comment thread | PNG 1600x1000 | 3d | Reuse `kitv2-reports-showcase.png`, or re-capture with an invented "Market scan" report |
| A7 | **Fleet diagram**: phone → assistant → leads/helpers on 3 machines (Laptop, Desktop, Linux box), providers as tags | SVG, inline, theme-aware | 3e | Hand-drawn SVG (draft already in the prototype). Generic machine names only |
| A8 | Lock-screen notification "An agent needs your answer" | PNG 1179x2556 | 3c (optional) | iOS Simulator; send a test push with generic text from a test daemon. Mark actionable push as **coming** — only show the plain alert |
| A9 | Schedule list (nightly / weekdays / weekly) | HTML mock (in prototype) | 3f | No capture; it's CLI-only today. Keep it as a simple styled list, not a fake web screen |
| A10 | Social / Open Graph image | PNG 1200x630 | `<head>` | Hero H1 + logo + a crop of A1 |
| A11 | Final band ring art | CSS/SVG | 10 | Drawn in the prototype (concentric rings + star) |

## Privacy check (each asset)

1. Data is from a fixture or a throwaway test identity, never a live session.
2. Zoom to 200% and read every string: no personal names, emails, phone numbers,
   real host names, file paths, tokens, account ids, repo names other than
   `pentacle` / `pentacle-mobile`.
3. No third-party product UI or logos other than provider names as plain text.
4. Strip EXIF / metadata (`exiftool -all= file`).
5. Record source commit + fixture name in a capture note next to the file, like
   `docs/screenshots.md` does.
