# Brand Guidelines: strongsuit

## Identity

**Name:** strongsuit (lowercase, always). Binary: `suit`. Repository: https://github.com/xooxoxxo/strongsuit. Not Anthropic-affiliated; it is an independent open-source CLI.

## Tagline Hierarchy

**6 words:** Named skill sets for Claude Code.

**20 words:** Dress your agent for the occasion. Skills, MCP servers, plugins, and hooks kept as named, atomically-switchable suits.

**60 words:** Named skill sets for Claude Code. One command dresses your agent for the task. Everything is reversible; nothing is deleted. Remote suits go through a review pipeline where every component is shown and approved before it touches your machine.

## Boilerplate Paragraph

strongsuit turns Claude Code customization into named, atomically-switchable **suits** — bundles of skills, MCP servers, plugins, hooks, CLAUDE.md fragments, agents, commands, and rules. One command dresses your agent for a task; switching is instant and reversible. The library keeps everything you own, forever. Remote suits go through a review pipeline where every component is shown and individually approved before any bytes land on your machine. `suit run` launches one session in a suit with zero global mutation. 348 tests, measured per-session isolation, 30+ mutation-tested safety guards, MIT licensed.

## Voice and Metaphor

**Metaphor:** closet (the library), tailor (edit suits), wear (activate). `up` = your default outfit (global activation). `run` = one meeting (per-session launch).

**The one pun:** "tailor" as both command name and fashion meaning. Do not pile on wardrobe humor; it is off-brand.

**On-brand examples:**
- "Switch suits, then start a fresh session."
- "The library keeps everything you own, forever."
- "A suit names the subset a task needs."

**Off-brand examples:**
- "Suit up for success!" (cheerleading)
- "Time to dress to impress." (pun overload)
- "Your wardrobe of agent superpowers." (hyperbole)

## Voice Do/Don't Table

| Do | Don't |
|---|---|
| State limits plainly and early ("token figures are estimates") | Use words like "automatic," "intelligent," or "magic" |
| Say measured or cited facts ("348 tests on 5 CI legs") | Invent users, testimonials, benchmarks, or download counts |
| Use active voice and short sentences (max 20 words) | Write in corporate polish; sound like a person |
| Assume the reader is a power user and direct | Explain what "tokens" are; assume knowledge |
| Acknowledge tradeoffs ("skills are additive, not exclusive") | Paper over limits with reassurance |
| Cite sources ("docs/session-isolation.md" for measured probes) | Make claims without proof; say "verified" without evidence |

## Positioning Against Competitors

Claude Code's own `/skills` panel lets users toggle skills one at a time. Existing dormant tools (e.g., andydbc/skillset) handle skills only, never MCP or hooks, and lack a review pipeline. strongsuit fills the gap: named groups (suits), atomic switching, full component scope, content-pinned review, and per-session isolation measured and documented. Say this plainly without dunking; the value speaks.

## Palette and Type

**Color Palette** (from DESIGN.md):
- Primary accent: Bullion Gold (#e0a82e, ~10% of surface)
- Ground: Near-Black (#0d0c0a)
- Text: Cream (#efe9db)
- Spec strips: Cream Paper (#f3ecdc) on Dark

**Typography**:
- Display: Bodoni Moda (serif, Didone)
- Body: Archivo (sans-serif, geometric)
- Mono: ui-monospace (SF Mono, Menlo, Consolas)

**Voice:** Bodoni Moda carries editorial authority. Archivo is the workhorse. Mono is for code only.

## Logo and Asset Usage

**Logo:** `assets/logo.png` (gold on dark, 180×180 nominal size).

| Asset | Intended Use | Path |
|-------|----------|------|
| assets/brand/og.png (1200×630) | Open Graph / social sharing | og-image tag for site |
| assets/brand/social-avatar.png | Twitter / GitHub profile image | Twitter, GitHub, dev.to |
| assets/brand/readme-banner.png | README hero | top of GitHub README |
| assets/brand/x-header.png | Twitter header | X/Twitter profile |
| assets/shots/status.png | `suit status` output example | landing page, docs |
| list-before.png, list-after.png | token reduction before/after | blog post, compare view |
| up.png, show.png, run.png | command output examples | website guide |
| install-review.png | review pipeline screenshot | trust section, docs |
| tailor.png | interactive edit example | tailor command guide |
| assets/shots/suit-up.gif | animation of switching | landing, README |

## Claim Guard (Binding)

Never claim or invent:
- User counts, download numbers, or adoption metrics.
- Testimonials or endorsements.
- Automatic detection or implicit switching (it is manual by design).
- Benchmarks or performance comparisons.
- Affiliate, endorsement, or partnership with Anthropic.

Always state these limits up front:
- Per-session skills are **additive** (layered on ambient set, not exclusive).
- Bare `claude --resume` bypasses MCP isolation (MCP is not sticky; skills are).
- Token figures are **estimates** (bytes ÷ 4, for comparing skills, not measurements).
- Review guards the remote boundary (local content activates without review).

Real, citable facts on hand:
- 348 tests on 5 CI legs.
- 30+ named killed mutants (mutation testing of every safety guard).
- Measured per-session isolation probes (docs/session-isolation.md with method and dates).
- Content-pinned sha256 review (approval attaches to content, not names).
- Prior art (andydbc/skillset) is dormant and skills-only.
