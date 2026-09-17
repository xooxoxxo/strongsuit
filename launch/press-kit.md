# Press Kit: strongsuit

**Contact:** GitHub issues https://github.com/xooxoxxo/strongsuit/issues

---

## Facts Sheet

**Name:** strongsuit  
**Binary:** `suit`  
**Repository:** https://github.com/xooxoxxo/strongsuit  
**Website:** https://xooxoxxo.github.io/strongsuit/  
**License:** MIT  
**Install:** `npm install -g strongsuit` (v1.0.0, published [release date])  
**Platform:** macOS, Linux. Windows support documented with caveats (junctions + file symlinks).  

**Maintainer:** Oytun (they/them)  
**Affiliation:** Independent; not Anthropic-affiliated.  

**Code:** TypeScript, ES modules, strict mode. Compiles to standalone binary. 348 tests on five CI legs. 30+ mutation-tested safety guards.

---

## Boilerplate (Can be Used in Press)

strongsuit turns Claude Code customization into named, atomically-switchable **suits** — bundles of skills, MCP servers, plugins, hooks, CLAUDE.md fragments, agents, commands, and rules. One command dresses your agent for a task; switching is instant and reversible. The library keeps everything you own forever. Remote suits go through a review pipeline where every component is shown and individually approved before any bytes touch your machine. Per-session wear is measured via codeword probes (method published). 348 tests, 30+ mutation-tested safety guards, MIT licensed.

---

## Asset Index

All assets available in `/assets` directory of the repository.

| Asset | Dimensions | Use Case | File Path |
|-------|-----------|----------|-----------|
| Logo (gold on dark) | 180×180 (nominal) | Favicon, README, GitHub profile | assets/logo.png |
| Open Graph image | 1200×630 | Social sharing, card preview | assets/brand/og.png |
| Social avatar | 400×400 | Twitter, GitHub, dev.to profile | assets/brand/social-avatar.png |
| README banner | 1200×400 (approx) | Top of GitHub README | assets/brand/readme-banner.png |
| X/Twitter header | 1500×500 | Twitter profile header | assets/brand/x-header.png |
| `suit status` example | 800×600 (approx) | Landing page, docs | assets/shots/status.png |
| Before/after comparison | N/A (two images side-by-side) | Blog posts, case studies | list-before.png, list-after.png |
| Switching animation | 800×450 (video) | Landing page hero, README | assets/shots/suit-up.gif |
| `suit up` output | 800×400 | Command reference, docs | up.png |
| `suit show` output | 800×400 | Command reference, docs | show.png |
| `suit run` output | 800×400 | Session guide, docs | run.png |
| `suit tailor` interactive | 800×600 | Editing guide | tailor.png |
| Review pipeline flow | 1000×700 (approx) | Safety/trust section | install-review.png |

**All asset downloads:** https://github.com/xooxoxxo/strongsuit/tree/main/assets

---

## Three Quotable Statements (From the Maintainer)

### On the Problem

"Claude Code warns when skills inflate tokens. The only fix it offers is to disable one at a time or delete and re-download later. Neither scales when you have ten skills across unrelated domains. strongsuit solves this: one command to switch between named groups. Nothing is ever deleted."

### On the Solution

"I built a tool that does three things: atomic switching of all component types (not just skills), a review pipeline that gates everything remote, and per-session isolation that is measured, not assumed. Everything is reversible; nothing is deleted. 348 tests, 30+ mutation-tested guards."

### On the Philosophy

"Honest limits convert better than polish that hides them. I state the constraints up front: skills are additive per session, token figures are estimates, bare resuming bypasses MCP isolation. A user who reads those and chooses strongsuit anyway is the user who will find real value in it."

---

## Key Statistics for Press

- **Test coverage:** 348 tests on 5 CI platforms
- **Safety verification:** 30+ named killed mutants (mutation-tested every guard)
- **Measured isolation:** Per-session MCP isolation confirmed via codeword probes with published method (docs/session-isolation.md)
- **Code review:** Mutation testing record, test suite, GitHub Actions CI
- **Launch day:** [date], npm registry, GitHub releases
- **Community:** MIT open-source; issues are the contact channel

---

## Positioning for Different Outlets

**For tech press / blogs:**
"A CLI that solves Claude Code's token inflation problem by adding named skill groups with atomic switching and measured per-session isolation."

**For dev-focused outlets (Dev.to, Hashnode, Medium):**
"One developer's response to Claude Code's token warning: a tool that treats agent customization like a wardrobe, with a review pipeline for remote suits and probed isolation guarantees."

**For open-source / community channels:**
"Measured-first open-source CLI for Claude Code skill set management. 348 tests, mutation-tested safety guards, published isolation probes."

**For product / tool sites:**
"Atomic switching of Claude Code customization (skills, MCP, plugins, hooks) with zero global mutation. Named suits, review pipeline, reversible activation."

---

## Honest Caveats for Press

Never claim:
- User counts, download numbers, adoption metrics (not yet known)
- Testimonials or endorsements
- Partnership with Anthropic (independent project)
- Automatic detection or implicit switching (intentionally manual)
- Performance benchmarks or token savings (only estimates and direction)

Always include:
- MIT license
- Independent / not Anthropic-affiliated
- Per-session skills are additive (not exclusive)
- Bare `claude --resume` bypasses MCP isolation
- Token figures are estimates

---

## Reproduction for Reviewers

**To verify the claims:**

1. Install: `npm install -g strongsuit`
2. Run help: `suit --help`
3. Read the README honest-limits section
4. Read docs/session-isolation.md for measured isolation method
5. Review test suite in `test/` and CI logs for 348 tests and mutation testing record
6. Clone repo and run locally: `npm install && npm run build && npm run test`

---

## Contact for Questions

GitHub issues: https://github.com/xooxoxxo/strongsuit/issues  
No email provided; all communication through GitHub.

---

## Media Files

All brand assets (logo, OG images, banners, screenshots, animations) are in the `/assets` folder of the GitHub repository. Free to use with attribution (MIT license; no formal attribution required, but appreciated).

---

## Timeline

- **v1.0.0 launch:** [date]
- **Roadmap:** Set composition, directory-level `.suitrc`, git URL imports, `doctor` command
- **Future (not committed):** Team/shared suits, version history rollback

---

End of press kit.
