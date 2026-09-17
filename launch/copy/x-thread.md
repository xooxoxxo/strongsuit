# X (Twitter) Thread: strongsuit

**8 posts, ≤280 chars each, one image per post**

---

### Post 1

Claude Code warns when your skills inflate tokens. The only fix: disable one at a time or delete and re-download. Neither scales.

I built strongsuit: named groups you switch with one command. One suit for coding. One for writing. One for legal work.

[assets/brand/og.png]

---

### Post 2

How it works: Claude Code reads a directory; it doesn't care if entries are symlinks.

A library holds everything you own forever. Switching moves symlinks only. Safe. Atomic. Instant. Reversible.

[assets/shots/status.png]

---

### Post 3

The token drop from switching:

Before: 5 skills active, ~154 tokens of descriptions loaded every session.

After: 3 skills active, ~77 tokens.

Run it for one session only. Global config untouched.

[list-before.png]
[list-after.png]

---

### Post 4

Remote suits fetch into quarantine. Every component (skills, MCP servers, hooks, plugins) is printed in full. Risk-classed. Individually approved.

Approvals pin content by hash. If upstream changes, activation blocks with a diff.

[install-review.png]

---

### Post 5

Three honest limits (stated first, not buried):

1. Per-session skills are additive (layer on ambient set)
2. Token figures are estimates (bytes ÷ 4), good for comparing, not measuring
3. Bare `claude --resume` bypasses MCP isolation

Real limits convert better than polish that hides them.

---

### Post 6

Why I trust the code:

• 348 tests on 5 CI legs
• 30+ mutation-tested safety guards (guards were broken, suite goes red)
• Per-session isolation measured with codeword + tool-count probes
• Every review decision is recorded and pinned by content hash

[show.png]

---

### Post 7

Built in the open. MIT licensed. One command to install:

```
npm install -g strongsuit
```

Then:

```
suit up coding        # your default outfit
suit run writing      # one meeting only
```

[run.png]

[up.png]

[tailor.png]

---

### Post 8

Live now: https://github.com/xooxoxxo/strongsuit

Docs: https://xooxoxxo.github.io/strongsuit/

MIT. 348 tests. Measured isolation. Honest limits.

Feedback on anything welcome. This solves a problem Claude Code itself surfaced.

[assets/shots/suit-up.gif]

---

## Posting Strategy

- Space posts 1 per hour starting 3pm ET on launch day (T-0)
- First post at 3pm, last at 10pm
- Pin post #1 to profile for 24 hours
- Like/reply to every mention in the first 6 hours
- No hashtags; let retweets compound
- Thread together so they appear in sequence on timeline
