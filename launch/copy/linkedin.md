# LinkedIn Post

I shipped v1.0.0 of **strongsuit** today: a CLI for Claude Code that treats customization like a wardrobe.

Claude Code warns when skills inflate token usage. The only available fix: disable one at a time or delete and reinstall later. Neither works at scale.

**What it does:**
- Define named groups (suits) of skills, MCP servers, plugins, hooks
- Switch between them atomically: `suit up coding` (global) or `suit run writing` (one session only)
- Review pipeline for remote suits: every component shown, risk-classed, individually approved
- Per-session isolation measured (not assumed) with codeword probes

**Why it matters:**
- Nothing is ever deleted. Switching is instant and reversible.
- Remote content is quarantined until reviewed. Drift blocks with a diff.
- Measured per-session isolation, 30+ mutation-tested guards, 348 tests.

**Honest limits (stated first):**
- Per-session skills are additive (layer on ambient set)
- Token figures are estimates (bytes ÷ 4)
- Bare `claude --resume` bypasses MCP isolation

MIT open-source. This solves a problem Claude Code itself surfaced.

GitHub: https://github.com/xooxoxxo/strongsuit

Feedback welcome.
