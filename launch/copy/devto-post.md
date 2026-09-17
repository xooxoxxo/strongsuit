# Dev.to Long-Form Post

---

```yaml
title: "strongsuit: Named Skill Sets and Atomic Switching for Claude Code"
description: "A CLI to switch between named groups of Claude Code customization with zero global mutation."
tags: claude, productivity, open-source, devtools
canonical_url: "https://xooxoxxo.github.io/strongsuit/story"
```

---

## Claude Code's Token Problem Has a Solution

Claude Code warns when your installed skills inflate token usage. But the fix it offers is brutal: disable one at a time in settings, or delete a skill and re-download it later. Neither scales when you have ten skills across unrelated domains.

I built **strongsuit** to solve this: a CLI that treats your skills like a wardrobe. Named groups (suits) switch atomically with one command. Your library keeps everything forever. Nothing is ever deleted.

## The Problem, Concrete

Every skill's description loads into your Claude Code context on every turn, whether you need it or not. Legal templates, brand voice enforcement, spreadsheet editing — all live in that context, even when you are debugging infrastructure.

Claude Code itself surfaces this problem. The token counter warns you. But then what? The `/skills` panel lets you disable one at a time. If you have twenty skills, that is twenty clicks. And if you want to re-enable them later, that is twenty more.

There is no concept of groups. No way to say: "for coding, I want docx, pptx, and xlsx. For writing, I want brand-voice enforcement. For legal work, I want three legal templates and a contract analyzer."

And as your setup grows past skills into MCP servers, plugins, and hooks, "what is my agent wearing right now?" stops having an answer.

## How strongsuit Works

The mechanism is simple. Claude Code reads a directory (`~/.claude/skills`). It does not care whether the entries are real folders or symlinks.

So:
- A **library** holds an entry for every skill you own (real folders for skills the tool copied in, symlinks for externally-owned skills that stay updated at their source).
- The **active directory** holds nothing but symlinks pointing into the library, one per currently-active skill.
- A **suit** is just a named list of skills in a JSON file.
- **Activating a suit** means: delete every symlink in the active directory, then create symlinks for exactly the skills that suit names.

Consequences:
- **Deactivating is not deleting.** The library entry is untouched. Switching moves symlinks only.
- **Links the tool does not own are never removed.** Foreign symlinks are left in place and reported, because the tool has no record of where they pointed.
- **Switching is O(number of skills) filesystem operations** — effectively instant.
- **Only symlink unlinks are ever destructive**, and the code refuses to unlink anything not managed.

## The Review Pipeline

Remote suits are dangerous. Code you download and run should be reviewed before landing on your machine. strongsuit gates the remote boundary.

`suit install owner/repo` fetches into quarantine. Nothing leaves it until reviewed. Every component — skills, MCP servers, plugins, hooks, CLAUDE.md fragments — is printed in full and risk-classed:

- **prompt-surface** (skills, commands, agents, rules, CLAUDE.md) — instructions the agent will follow
- **process/network** (MCP servers, plugins) — things that start processes or talk to the network
- **code-executing** (hooks) — commands that run on their own at the moment an event fires

You approve each component individually. Approvals are recorded and pinned by content hash. If upstream changes, activation blocks with a diff rather than silently updating. Upstream updates and local tampering look identical to code, so the tool treats them the same: "drift detected, human re-approval needed."

## Per-Session Wear

You need a suit for one meeting. One session wearing exactly that suit's configuration, leaving your global setup untouched.

`suit run writing -- -p "draft the launch post"` materializes the suit as an ephemeral plugin directory and launches Claude with it. Skills, MCP servers, hooks, all exclusive to that session. On exit, the temporary directory is cleaned up. Your global `~/.claude` is untouched.

Two measured mechanics (stated plainly, not papered over):

- **Skills are additive per session.** The session gets the suit *plus* the ambient global/project set. If you want sessions close to exclusive, keep your global set lean.
- **MCP isolation survives `suit run`, but not bare resume.** Skills replay with the conversation prefix and stick on resume. MCP flags must be re-applied. So use `suit resume` or `suit run --continue` for resumed conversations; a bare `claude --resume` gets the ambient MCP set back.

Per-session isolation is measured, not claimed. I built a probe that asks a session to quote a codeword from a marker skill's description, run the session with and without the `--strict-mcp-config` flag, and watched the results. Full documentation of the method, findings, and reproduction steps lives in `docs/session-isolation.md`.

## Honest Limits

These are stated up front in the README care label, and they belong here:

1. **Token figures are approximations.** The tool estimates each skill's cost as file bytes divided by four. Directionally useful for comparing skills ("this one is bloated"), never a precise measurement. Do not present token numbers as measured data.

2. **Per-session skills are additive, not exclusive.** A `suit run` session inherits your global and project skill sets, then layers on the suit's skills. This is because Claude Code does not support per-session skills natively; the mechanism is to deliver skills via a plugin directory that merges with the ambient set. Full details in `docs/session-isolation.md`.

3. **Bare `claude --resume` bypasses MCP isolation.** Skills replay with the conversation prefix and survive resume. MCP servers are live connections that must be re-established from flags at process start. A bare resume re-attaches every MCP server you have configured globally. Always resume suit-launched conversations with `suit resume` or `suit run --continue` to keep the outfit intact.

4. **Windows symlink behavior varies.** Directory symlinks are created as junctions (no Developer Mode needed). Single-file components use file symlinks, which may require Developer Mode or elevation on some setups.

5. **Review guards the remote boundary only.** Content you create locally (init-adopted skills, imports, hand-written manifests) activates without gating. You wrote it. Remote content is always reviewed.

## Why I Trust the Code

Every safety guard is mutation-tested. Mutations are deliberate breaks of the guard logic — removing a symlink check, ignoring a hash comparison, deleting the rollback on failure. For every mutation, I verified that the test suite went red. 30+ named kills. The guards hold.

Test coverage: 348 tests on five CI platforms. Not tests written to look good, but tests that exercise the real user flow (init → tailor → up/run → resume) and failure modes (network fail, permission denied, drift detected).

Per-session isolation is measured. The probe method, results, and reproduction steps are published in the docs. This is not an assumption. The codeword technique (asking the model to quote text from a marker skill) avoids false negatives better than presence questions (e.g., "is skill X available?"), because a session can answer from its own conversation history rather than from live context.

## Getting Started

Install:

```bash
npm install -g strongsuit
```

One-time setup:

```bash
suit init                  # migrate your existing skills into the library (backup taken first)
```

Define a suit:

```bash
suit tailor coding --skills docx,pptx,xlsx
```

Activate globally:

```bash
suit up coding
suit list                  # now showing only the coding suit's skills
```

Or wear it for one session:

```bash
suit run writing -- -p "draft the proposal"
```

Resume a conversation in its original suit:

```bash
suit resume <session-id>   # re-dresses in the suit it was born with
```

Full documentation: https://xooxoxxo.github.io/strongsuit/

## What's Not Included

- **Automatic detection.** The tool does not watch what you are doing and adjust. Manual switching is intentional.
- **Team/shared suits.** Not a current feature. You can publish suits to GitHub and others can install them, but there is no first-class shared suit model yet.
- **Version history rollback.** You can reject a new version of a suit on `sync`, but you cannot ask the tool to serve you an older library copy.

## The Roadmap

Before release (done): full test coverage, measured per-session isolation, review pipeline with mutation testing.

Plausible next: set composition / inheritance, `.suitrc` for directory-level defaults, import directly from git URLs, a `doctor` command to find orphaned symlinks.

## In Closing

This tool exists because Claude Code surfaced the problem (the token warning), and the stock remedies were insufficient. The solution is intentionally simple: the library mechanism is just symlinks. Switching is just filesystem operations. Review is just showing you what you approved. Measured isolation is probes that prove the claim.

I built it in the open. 348 tests. MIT licensed. Code, docs, and the measurement method are on GitHub.

If you have accumulated skills across unrelated domains, try it. If the three honest limits (additive skills, estimated tokens, non-sticky MCP) do not fit your workflow, that is fine. The tool is for the case where they do.

Feedback welcome. The GitHub repo is the right place for issues, feature requests, or questions about the design.

---

## About the Author

The maintainer is Oytun (they/them). Built this to solve a personal problem and open-sourced it because the problem is real for Claude Code power users. Not affiliated with Anthropic. All questions go to GitHub issues.
