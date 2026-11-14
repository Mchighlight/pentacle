# Pentacle intro page: section plan

**Positioning:** Pentacle is your one-person company: you plus
an AI team that fills the roles, across your own machines, steered from your
phone. Outcome first ("get your job done, control all your stuff"); feature
names go low on the page. Contrast with coding-agent apps without naming any.

**Reader:** a solo founder, freelancer or power user who already pays for an
AI coding agent and is drowning in everything that isn't code.

**One job for the page:** make them think "I could hand off half my week", then
send them to the setup guide.

Inputs: FEATURE-MAP.md (what's true), COPY.md (all words), ASSETS.md
(visuals). Prototype: prototype/index.html. The section pattern comes from a
study of public agent-tool front pages; those notes stay private.

## Page order

| # | Section | Purpose (what gets done for the reader) | Layout | Visual |
| --- | --- | --- | --- | --- |
| 0 | Sticky nav | Get back to the CTA from anywhere | Wordmark left; 4 anchors; GitHub + solid "Get started" right; translucent blur | Logo mark (A0) |
| 1 | Hero | Say the whole idea in one look: one person, a full team, steered from the phone | Centered H1 (2 lines), one-line sub, 3 CTAs; visual below spanning container | **A1 hero composite**: web chat on the left, phone in front showing lane cards. Prototype draws an HTML phone mock |
| 2 | Hand it off | Prove "not just code" before any feature talk | H2 + 7 compact cards (job → what you get back) in a wrapping grid | Icons only (line icons, accent color). Replaces the logo wall: we show work, not logos |
| 3a | Say it once | One place to ask; you never chase agents | Text left, visual right | **A2** chat: you ask, assistant replies "Started a lead on Desktop…" |
| 3b | Big jobs get a lead | Projects run themselves | Visual left, text right | **A3** lead lane: plan steps ticking, helper rows (short GIF, ≤8s) |
| 3c | Decide from anywhere | You stay the boss, from your pocket | Text left, visual right | **A4** phone: question card + Face ID approval sheet (two phones, slight overlap) |
| 3d | Know where things stand | No status meetings | Visual left, text right | **A5** phone lane cards + **A6** report with a comment |
| 3e | All your computers, one team | Use every machine you own | Text left, visual right | **A7 fleet diagram** (SVG; drawn in the prototype) |
| 3f | Keeps going (optional) | Work continues while you sleep | Compact full-width row | Small schedule list (HTML mock) |
| 4 | How it works | Show it's reachable tonight | 3 numbered columns | Step icons; tiny terminal line under step 1 |
| 5 | A team, not another tool | Answer "isn't this just another agent app?" | H2 + 1 line + 2-column comparison table (Pentacle column highlighted) | None |
| 6 | Your stuff stays yours | Trust: self-hosted, your accounts, Face ID | Eyebrow + H2 + 5 small cards (3+2), fine-print line under | Line icons |
| 7 | What's inside | Feature names for the curious, low on the page | Wrapped "chip" list | None |
| 8 | Coming next | Honest roadmap; shows momentum | 7-item list with "coming" tags | None |
| 9 | FAQ | Kill the last doubts | H2 left, accordion right (native details/summary) | None |
| 10 | Final CTA | Ask once more | Big 5-word line + 2 buttons; faint pentacle ring art behind | Ring line art (CSS/SVG) |
| 11 | Footer | Links + license | 3 short columns + one-line tagline | Wordmark |

## Deliberately left out

- **Logo wall, user counts, testimonials:** none exist. Add real quotes later as a
  small strip after section 3 (2-3 cards, real names only with permission).
- **Pricing tiers / enterprise form:** Pentacle is free, MIT, self-hosted. One FAQ line covers cost.
- **Audit badges (SOC 2 etc.):** we have none; never imply one.

## Visual system

- **Dark first, light supported** (prefers-color-scheme + a toggle).
- **Palette from the logo:** near-black `#0a0e0d` background, panel `#111816`,
  mint accent `#3ee6a8` (logo green), soft text `#e8f1ee`, muted `#8fa39c`,
  amber `#f5b14c` only for "blocked / needs you". Light: `#f6f8f7` bg, `#0d7a55`
  accent (AA on white), `#0f1714` text.
- **Type:** system sans for headings and body (weight 600 H1, tight tracking);
  monospace for eyebrows, chips and mock UI, letter-spaced uppercase like the
  phone app's lane cards. Optional Google Fonts upgrade: "Space Grotesk" +
  "JetBrains Mono".
- **Shape:** cards with one clipped corner (echo the phone app's notched lane
  cards); 1px borders; small radii (6px).
- **Texture:** very faint starfield dots in the hero and final band (echo the
  in-app cosmic theme). No heavy video. Motion only: a blinking status dot, a
  typing caret, and GIFs in feature blocks. Respect `prefers-reduced-motion`.
- **Spacing:** 96px section padding desktop / 64px mobile, max width 1120px.

## CTA placement

"Get started" (→ setup guide in the GitHub repo) appears in nav, hero and final
band. GitHub is the secondary CTA in the same three places. No other asks.

## Build notes for the real page

- Static, single page. No analytics or trackers. If analytics is ever added,
  use self-hosted, cookie-free, and say so in the footer.
- Real assets replace the `ASSET Ax` placeholder boxes 1:1 (sizes in ASSETS.md).
- Every screenshot uses invented fixture data (see ASSETS.md privacy check).
- Re-check FEATURE-MAP.md before launch; flip "coming" items that have shipped.
