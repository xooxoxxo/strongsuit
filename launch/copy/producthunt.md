# Product Hunt Launch

## Basic Info

**Name:** strongsuit

**Tagline (≤60 chars):** Named skill sets and atomic switching for Claude Code.

**Description (≤260 chars):** Dress your agent for the occasion. Switch between named groups of Claude Code customization (skills, MCP servers, plugins, hooks) with one atomic command. Per-session wear with zero global mutation. Review pipeline gates everything remote.

**Website URL:** https://xooxoxxo.github.io/strongsuit/

**Repository URL:** https://github.com/xooxoxxo/strongsuit

---

## Maker Introduction Comment (Post Within 1 Hour of Launch)

I'm Oytun, the maintainer. Built this because Claude Code itself warns when skills inflate token usage, and the only stock remedies are clumsy.

**What it does:**
- `suit up coding` activates that suit globally (skills, MCP, hooks, atomically)
- `suit install owner/repo` fetches through a review pipeline (every component shown, risk-classed, individually approved)
- `suit run writing` launches one session in that suit, global config untouched
- Per-session MCP isolation is measured, not assumed (probes in docs)

**Honest limits (stated first):**
- Per-session skills are additive (layer on ambient set, not exclusive)
- Token figures are estimates (bytes ÷ 4)
- Bare `claude --resume` bypasses MCP isolation

**Why this matters:**
- 348 tests on 5 CI legs
- 30+ mutation-tested safety guards
- Review pipeline guards the remote boundary
- Everything reversible; nothing deleted

MIT licensed. Feedback welcome on the review design, isolation measurement, or anything else.

---

## Five PH Maker Answers (Pre-drafted)

### 1. What problem does this solve?

Claude Code warns when installed skills inflate token usage. The only available solutions are awful: disable one at a time, or delete and re-download. There is no concept of named groups, no atomic switching, no way to bundle MCP servers or hooks with skills. This tool adds all three.

### 2. How is this different from [competitor]?

The dormant andydbc/skillset handles skills only, no MCP or hooks, no review pipeline. Claude Code's native `/skills` panel toggles one at a time with no grouping. The feature request for native grouping is still open (anthropics/claude-code#43928). strongsuit fills that gap today, with measured per-session isolation and a review pipeline that gates everything remote.

### 3. Why should I trust the safety claims?

Every safety guard is mutation-tested: guards were deliberately broken and the suite verified to go red. 30+ named kills. 348 tests on five CI platforms. Per-session isolation is measured with codeword probes (not assumed), method published in docs. The review pipeline prevents drift silently: it blocks and diffs, never updates without human re-approval.

### 4. What are the honest limits?

Per-session skills layer on top of your global set (not exclusive, because Claude Code does not support per-session skills natively). Token figures are estimates (bytes ÷ 4), good for comparing skills, not measurements. Bare `claude --resume` silently bypasses per-session MCP isolation (MCP is not sticky). All three are in the README care label.

### 5. What's the roadmap?

Today: v1.0.0 with measured isolation, atomic switching, and a review pipeline. Next: `suit use <set> --add` (layer sets instead of replacing), set composition / inheritance, auto-switching by directory (`.suitrc`). Not planned: team/shared suits (feature request, not a current commitment). The tool is intentionally manual, not automatic, because implicit switching would be unpredictable.

---

## Gallery Order

1. Landing page hero (masthead + tagline + CTA) — [assets/brand/og.png]
2. Before/after token comparison (list output) — list-before.png → list-after.png
3. Per-session launch (`suit run` output) — [run.png]
4. Review pipeline (component approval flow) — [install-review.png]
5. Tailor / edit interface — [tailor.png]
6. Animation: switching between suits — [assets/shots/suit-up.gif]

---

## Product Hunt Topics

- Developer Tools
- CLI Tools
- Open Source
- Claude AI
- Productivity

---

## Submission Strategy

Post at **12:01am PT (3:01am ET)** on Tuesday or Wednesday. This is when PH's algorithm favors new launches. Maker comment must post within 1 hour. Monitor for questions and reply within 15 minutes for the first 6 hours.
