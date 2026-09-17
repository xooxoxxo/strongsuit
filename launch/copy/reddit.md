# Reddit Posts

## r/ClaudeCode

**Title:** strongsuit — named skill sets and atomic switching for Claude Code (MIT open-source, v1.0.0)

**Body:**

Claude Code warns when skills inflate token usage. The only remedies are clumsy: disable one at a time, delete and re-download later.

I built strongsuit to solve this. Named groups (suits) switch atomically with one command. Nothing is deleted. Everything is reversible.

**What it does:**
- `suit up coding` activates exactly that suit's skills + MCP servers + hooks
- `suit install owner/repo` fetches remote suits through a review pipeline (every component shown, risk-classed, individually approved)
- `suit run writing -- -p "draft"` launches one session wearing that suit, leaving global config untouched
- Per-session skills are additive (layer on ambient set); MCP is exclusive

**The honest limits (printed first, not buried):**
- Token figures are estimates (bytes ÷ 4), good for comparing skills, not measurements
- Per-session skills inherit your global set too (not exclusive unless you want a bare API-key mode)
- Bare `claude --resume` bypasses per-session MCP isolation (MCP is not sticky)

**Why I trust it:**
- 348 tests on 5 CI legs
- 30+ mutation-tested safety guards (guards were broken and suite verified to go red)
- Per-session isolation measured with codeword + tool-count probes (method and dates in docs)
- Review pipeline guards the remote boundary: drift always blocks with a diff

MIT licensed. Code: https://github.com/xooxoxxo/strongsuit. Docs: https://xooxoxxo.github.io/strongsuit/

What questions do you have? What would make this more useful?

---

## r/ClaudeAI

**Title:** strongsuit — organize Claude Code skills into named, atomic groups (open-source, MIT)

**Body:**

If you use Claude Code and have installed 8+ skills across different domains, you probably feel the token inflation. Claude Code warns you about it, but the only tools are: disable one at a time, or delete and reinstall later.

I built a CLI that treats your skills like a wardrobe: named groups that switch with one command.

**Quick example:**
```
suit up coding              # activate exactly docx, pptx, xlsx
suit run writing            # launch one session with writing-focused skills only
suit install github/remote  # review + approve everything before it lands
```

Reversible. Nothing deleted. Full source open. MIT.

https://github.com/xooxoxxo/strongsuit

---

## r/commandline

**Title:** suit — symlink-based atomic skill switching for Claude Code (v1.0.0, MIT)

**Body:**

For anyone who uses Claude Code: a CLI for switching between named groups of skills and configurations atomically.

The mechanism is clean: Claude Code reads directories; it does not care whether entries are symlinks. A library holds everything you own; switching is O(N) symlink operations, instant and reversible.

Remote installs go through a review pipeline: every component printed, risk-classed, individually approved, pinned by content hash. Drift blocks with a diff.

Per-session isolation measured with codeword probes (docs/session-isolation.md).

GitHub: https://github.com/xooxoxxo/strongsuit

**Verification notes per r/commandline rules:**
- This is a dev tool for managing Claude Code customization; not spam.
- Author is the maintainer (oytun / xooxoxxo on GitHub).
- Open-source (MIT), no commercial angle.
- Published today; seeking feedback from CLI practitioners.

---

## Verification of Subreddit Rules

**r/ClaudeCode:** No explicit self-promo rule in sidebar; community norm is OK for tools directly for Claude Code, especially if they solve a documented problem (the token-inflation warning is real). Post openly as maintainer.

**r/ClaudeAI:** Broader Claude community, some self-promo OK if tool is useful to the audience. Mention it is open-source and cross-link to deeper technical discussion (r/ClaudeCode).

**r/commandline:** Rule: self-promo allowed if tool is genuinely useful and author is transparent about it. Keep tone technical, not marketing. Verification section required per community norms.

All three posts should include GitHub link, note MIT license, and invite genuine technical questions in comments.
