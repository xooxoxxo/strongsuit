# Community Channels

## Claude Developers Discord

Channel names change; find the current show-and-tell or projects channel before posting. Post once. Answer replies in the thread, not in new messages.

**Message:**

I shipped strongsuit v1.0.0: a CLI for switching between named groups of Claude Code customization (skills, MCP, plugins, hooks) with one atomic command.

It solves a problem Claude Code itself warns about: skills inflate tokens, but the only fix is delete/re-download.

The tool: atomic switching, reversible, review pipeline for remote suits, measured per-session isolation (not assumed).

GitHub: https://github.com/xooxoxxo/strongsuit

I want feedback on the review design. Is the three-tier risk classification useful? Anything that would make it stronger?

---

## Claude Code GitHub

Discussions are not enabled on anthropics/claude-code (checked 2026-09-18: the Discussions URL returns 404). Two low-key options remain:

1. One comment on the feature request for per-skill enable/disable (anthropics/claude-code#43928). It was closed as "not planned" on 2026-06-05 with three comments, so the thread is quiet; a comment there reaches few people. Two sentences at most: what strongsuit does about the request today, and the link. No repeat comments.
2. Your own repo: pin an issue titled "Launch feedback" and point every channel at it.

The body below is written for the feature-request comment or a Discussions post elsewhere (for example the Claude Developers Discord). Trim to two paragraphs for a GitHub issue comment.

**Title:** strongsuit: Named skill sets and atomic switching (v1.0.0 open-source)

**Body:**

I shipped v1.0.0 of a CLI that addresses a problem Claude Code itself warns about: skill inflation. Named groups (suits) switch atomically with one command. Nothing is deleted. Per-session isolation is measured.

**What it does:**
- Define suits (groups of skills, MCP servers, plugins, hooks)
- Switch globally: `suit up coding` (atomic)
- Switch per-session: `suit run writing` (zero global mutation)
- Install remote suits through a review pipeline (every component shown, approved, pinned by hash)

**Why it matters:**
- Reversible. Nothing deleted.
- Review gates the remote boundary. Drift always blocks with a diff.
- Per-session MCP isolation measured with codeword probes (method published).

**Honest limits (stated first):**
- Per-session skills are additive (layer on ambient set, not exclusive)
- Token figures are estimates (bytes ÷ 4)
- Bare `claude --resume` bypasses MCP isolation

**Verification:**
- 348 tests on 5 CI legs
- 30+ mutation-tested safety guards (guards broken, suite goes red)
- Per-session isolation probes with method documented

MIT licensed. Feedback welcome on the review design, the isolation measurement, or anything else.

GitHub: https://github.com/xooxoxxo/strongsuit
Docs: https://xooxoxxo.github.io/strongsuit/

---

## On Responding to "Why Isn't This Built Into Claude Code?"

**Standard response (use on Discord, Reddit, HN if the question comes up):**

The feature request for per-skill enable/disable via settings and session flags (anthropics/claude-code#43928) was closed as not planned in June 2026. Claude Code offers per-skill toggles in the `/skills` panel; strongsuit respects those toggles and adds what they do not cover: named groups across every component type, one atomic switch, review for remote content, and per-session wear. I built it because the problem is real today and this works now. strongsuit also adds three things the built-in UI would not: atomic switching across all component types (not just skills), a review pipeline that gates remote content, and per-session isolation that is measured and documented. If Anthropic adds native grouping, that is great for users who want just that. strongsuit will still have value for people who want the review pipeline and isolation.

(Keep this factual and calm. Do not position it as "better" — position it as "solves the problem today while native features are considered.")

---

## Key Talking Points for All Channels

When defending or explaining the design choices:

1. **Manual switching is intentional.** Implicit switching would be unpredictable. Users appreciate that it does not surprise them.

2. **Additive per-session skills is a Claude Code limitation, not a design flaw.** Claude Code does not support per-session skills natively. The mechanism is `--plugin-dir` (ephemeral plugin), and plugins merge. Documented. Users can keep their global set lean if they want closer-to-exclusive sessions.

3. **Review is not security, it is approval-for-drift.** We are not protecting users from their own malice. We are giving them visibility and control over what changes when they sync a remote suit.

4. **Mutation testing proves the guards work.** Not just "guards exist" — the guards were broken and the suite failed. That is the proof standard. 30+ specific named mutants.

5. **Measured isolation matters.** We did not claim isolation. We measured it. Codeword probes, method published, reproducible.

All five talking points should be in your arsenal for any channel where the tool is discussed.
