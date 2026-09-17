# Show HN Post: strongsuit

## Title Options (≤80 chars)

1. `Show HN: strongsuit – named skill sets for Claude Code`
2. `Show HN: strongsuit – dress your agent for the occasion`
3. `Show HN: strongsuit – reviewed, atomic agent customization`

## Maintainer's First Comment

Claude Code warns when installed skills inflate token usage. The only stock remedies are brutal: disable one at a time in settings, or delete a folder and re-download it later. Neither works at scale.

I built strongsuit to solve this: named groups (suits) that switch atomically. One command dresses your agent for the task. Nothing is deleted. Everything is reversible.

Three things about how it works:

1. **Mechanism is simple.** Claude Code reads a directory; it does not care whether entries are symlinks. A library holds all your skills forever; switching moves symlinks only. Safe, atomic, instant.

2. **Review gates the remote boundary.** `suit install owner/repo` fetches into quarantine. Every component (skills, MCP servers, hooks, plugins) is printed in full and risk-classed before approval. Approvals pin content by sha256 hash. If upstream changes or anything tampers locally, activation blocks with a diff.

3. **Per-session isolation is measured, not claimed.** `suit run` launches one session wearing exactly that suit, with zero global mutation. I measured this: built a probe that asks the session to quote a codeword from a marker skill, confirmed MCP isolation survives, and documented the method in docs/session-isolation.md. Skills are additive (session inherits ambient set); MCP is exclusive. Both findings are in the honest-limits section of the README.

Honest limits: per-session skills layer on top of your global set (not exclusive); bare `claude --resume` bypasses MCP isolation (MCP is not sticky); token figures are estimates (bytes ÷ 4, good for comparing skills, not measurements).

Every safety guard is mutation-tested: 30+ mutants named and killed. 348 tests on five CI legs. MIT licensed.

Code: https://github.com/xooxoxxo/strongsuit

I want feedback on: the review design (is the three-tier risk classification useful?); whether the per-session isolation measurement convinces or leaves gaps; and whether the honest-limits-first voice reads as trustworthy or as defensive.

---

## Six Likely HN Questions + Answers

### 1. "Why not just use the `/skills` panel in Claude Code?"

**Answer:** Claude Code's panel lets you toggle skills one at a time. Re-enabling them later means finding each and toggling again. No groups. No way to bundle MCP servers and hooks with skills, and no atomic switching. If disabling one at a time works for your workflow, the panel is fine. strongsuit is for people who have 10+ skills across unrelated domains and want to switch between whole coherent sets.

### 2. "Is this official? Is it affiliated with Anthropic?"

**Answer:** No. Independent open-source, MIT licensed. I built it because Claude Code itself surfaced the problem (the token-inflation warning). The tool works with Claude Code, not as part of it. The feature request for native skill grouping is still open (anthropics/claude-code#43928).

### 3. "Doesn't the review pipeline add friction? Who approves components?"

**Answer:** You approve them. `suit install` fetches into quarantine and prints every component in full. You review and approve each one interactively, or use `--yes` to approve everything except code-executing components (hooks take a separate `--approve-code-execution` flag). Approvals are recorded per content hash. If upstream changes, activation blocks with a diff rather than silently updating. The point is: drift always requires a human, but initial approval is yours and it is informed.

### 4. "How is this different from the dormant andydbc/skillset?"

**Answer:** andydbc/skillset handles skills only, no MCP servers or hooks. No review pipeline. No per-session isolation. strongsuit adds all three. Also not dormant: shipping v1.0.0 this week with 348 tests, measured per-session probes, and mutation-tested safety guards.

### 5. "Per-session skills are additive. Why not make them exclusive?"

**Answer:** Because Claude Code does not support per-session skills natively. The mechanism is to deliver skills via `--plugin-dir` (ephemeral plugin), and plugins merge with the global set. That is a Claude Code limitation, not a design choice. I could strip skills with `--bare`, but that requires an API key and breaks OAuth (the default install). Instead, `suit run` prints what the baseline set contributes. You can keep your global set lean if exclusivity matters.

### 6. "Is the review pipeline real security?"

**Answer:** No, it is approval-for-drift. Review gates the remote boundary: everything fetched from the internet is shown and approved before landing. Everything you create locally (hand-written manifests, imports) activates without gating. The point is: if a suit drifts upstream (whether update or tamper), you see a diff before it activates. It is not designed to stop a user's own malicious intent; it is designed to give you visibility and control over what changes.

---

## Asset Slots

- **Above the fold:** [assets/brand/og.png] — Open Graph image
- **Mechanism explanation:** [assets/shots/status.png] — `suit status` output showing current wear
- **Before/after savings:** [list-before.png] vs [list-after.png] — token count drop
- **Review pipeline:** [install-review.png] — component approval in action
- **Per-session launch:** [run.png] — `suit run` output example
