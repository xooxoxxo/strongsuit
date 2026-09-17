# GitHub v1.0.0 Release

## Release Title

strongsuit v1.0.0 · Atomic skill switching and review pipeline for Claude Code

---

## Release Body

Dress your agent for the occasion.

strongsuit turns Claude Code customization into named, atomically-switchable **suits** — bundles of skills, MCP servers, plugins, hooks, CLAUDE.md fragments, agents, commands, and rules. One command switches between them; nothing is ever deleted. Per-session isolation is measured and documented. Remote suits are quarantined and reviewed: every component shown, risk-classed, individually approved.

### What's Included

**Global switching:**
- `suit up coding` activates exactly that suit's components (skills, MCP, plugins, hooks, rules, agents, commands)
- File surfaces switch via symlinks; JSON surfaces go through an ownership ledger that never touches keys it did not write
- Atomic activation with rollback on failure
- `suit off` reverses everything

**Per-session wear:**
- `suit run writing -- -p "draft proposal"` launches one session in that suit
- Zero global mutation; temporary files cleaned on exit
- MCP isolation verified by measured probes (method published in docs)
- `.suitrc` names a directory's default suit; `suit resume` re-dresses conversations in their original suit

**Remote suits with review:**
- `suit install owner/repo` fetches into quarantine
- Every component printed in full and risk-classed (prompt-surface / process/network / code-executing)
- Individual approval per component with content-hash pinning
- On drift: activation blocks with a diff; re-approval required
- `suit sync` re-fetches and delta-reviews only what changed

**Library management:**
- `suit init` snapshots your active directory first; `suit restore` returns it exactly
- `suit tailor <suit>` edits suits interactively or via flags (`--skills a,b,c`)
- `suit list` shows every skill with on/off state and token estimates
- Nothing in the library is ever deleted; deactivating is moving symlinks only

### Honest Limits

These are stated up front in the README care label:

- **Per-session skills are additive.** A `suit run` session inherits your global and project skill sets, then layers on the suit's skills. Claude Code does not support per-session skills natively; the mechanism is ephemeral plugins that merge. Full details: [docs/session-isolation.md](https://github.com/xooxoxxo/strongsuit/blob/main/docs/session-isolation.md)
- **Bare `claude --resume` bypasses MCP isolation.** Skills replay with the conversation prefix (sticky). MCP servers must be re-established from flags at process start (not sticky). Always resume with `suit resume` or `suit run --continue`.
- **Token figures are estimates.** Calculated as file bytes ÷ 4, useful for comparing skills, never measurements.

### Evidence

**348 tests** on five CI platforms (GitHub Actions, CircleCI, Travis, Appveyor, Codecov).

**30+ mutation-tested safety guards.** Every safety guard was deliberately broken; the test suite verified to go red. Named, specific kills. Examples: symlink ownership check (verify first-hop target is in library), content-hash validation (confirm approval matches current bytes), rollback on failure (restore previous state).

**Per-session isolation measured, not claimed.** Probes ask sessions to quote a codeword from a marker skill's description. Method, results, and reproduction steps documented in [docs/session-isolation.md](https://github.com/xooxoxxo/strongsuit/blob/main/docs/session-isolation.md).

**Review pipeline verified end-to-end.** Nine mutations tested against review logic: `--yes` approving code-executing components, risk classification demoted, no-TTY path deciding instead of refusing, rejected components surviving, content hash ignored, rejection counted as approval, components decided without printing, hook commands truncated. All nine killed.

### Install

```bash
npm install -g strongsuit
suit init
suit tailor coding --skills docx,pptx
suit up coding
```

See [Getting Started](https://xooxoxxo.github.io/strongsuit/guide/getting-started.html).

### License

MIT

### Links

- **GitHub:** https://github.com/xooxoxxo/strongsuit
- **Website:** https://xooxoxxo.github.io/strongsuit/
- **npm:** https://www.npmjs.com/package/strongsuit

---

## Repository Description (≤100 chars)

Named skill sets and atomic switching for Claude Code. Review pipeline, per-session isolation, nothing deleted.

---

## Repository Topics (8–12 tags)

- claude-ai
- claude-code
- productivity
- developer-tools
- cli
- open-source
- agent-customization
- typescript
- skills
- mcp-servers
- token-optimization
- mit-license
