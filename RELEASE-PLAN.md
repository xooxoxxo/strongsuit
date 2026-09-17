# strongsuit 1.0.0 — release plan

Status on 2026-09-18: code, docs, website, imagery and launch copy are prepared. Four human-only gates remain (accounts, secrets, the tag, and posting). This file is the checklist; `RELEASING.md` holds the mechanics; `launch/GTM.md` holds the channel plan.

Legend: **[H]** human only · **[C]** Claude can do it on request · **[A]** already done.

## Gate 0 — code freeze

- [A] Main is green: 348 tests, 5 CI legs, mutation record intact.
- [H] Decide on the uncommitted work in the root checkout: `suit run --auto` and `suit resume --wearing` (spec `docs/superpowers/specs/2026-08-08-suit-swap-and-auto-select-design.md`, six modified files, two new). The suite passes with it (369 tests). Either ship it in 1.0.0 through its own PR, or move it to a branch and ship 1.0.0 without it. Do not tag with a dirty tree.
- [C] If it ships: PR, review, merge, then add it to `RELEASE-NOTES.md` under Highlights and to `launch/copy/github-release.md`.
- [H] Final holistic pass on your own machine: `suit init` on a copy of your real config, `suit up`, `suit run`, `suit install` of a real remote suit, `suit restore`.

## Gate 1 — accounts and secrets

- [H] npm: create a granular automation token with publish scope on npmjs.com. Add it as the repository secret `NPM_TOKEN`. Confirm `npm view strongsuit` still returns 404 (checked 2026-09-18: free).
- [H] Ko-fi: create the page. Then fill the handle in three places and open one PR:
  1. `.github/FUNDING.yml` — uncomment `ko_fi:`.
  2. `README.md` — the Support section's link.
  3. `website/.vitepress/config.ts` — the `SUPPORT_URL` constant (footer link appears when non-empty).
- [H] GitHub Sponsors is optional. The `xooxoxxo` organization has no listing today; a personal listing on `oytuneyucel` works too. Add `github:` to FUNDING.yml when approved.
- [H] Social accounts ready to post: Hacker News (account older than a few days, some karma), Reddit (account with history in r/ClaudeAI or r/ClaudeCode), X, LinkedIn, Product Hunt (maker profile with the avatar at `assets/brand/social-avatar.png`).
- [H] Upload `assets/brand/og.png` as the repository social preview (GitHub → Settings → General → Social preview). The API cannot do this.

## Gate 2 — publish

Follow `RELEASING.md`. In short:

```bash
git checkout main && git pull
npm version 1.0.0 --no-git-tag-version   # already 1.0.0; skip if unchanged
git tag v1.0.0
git push origin main --tags
```

- [H] Watch the `release` workflow. It refuses if the tag and `package.json` disagree.
- [H] Cold verify on macOS and on Windows: `npx --ignore-existing -y strongsuit@latest --version`, then `npm install -g strongsuit && suit --version`.
- [H] Brew tap: add the formula to `xooxoxxo/homebrew-tap` (steps in `RELEASING.md`), then `brew install xooxoxxo/tap/strongsuit`.
- [C] Publish the GitHub release with `launch/copy/github-release.md` as the body: `gh release create v1.0.0 -F launch/copy/github-release.md`.

## Gate 3 — flip the site and docs to npm

One PR, right after the cold verify passes:

- [C] `website/index.md` Availability section: replace the clone block with `npm install -g strongsuit` and change "Made to order, from source. The npm boutique opens with v1.0.0." to "Ready to wear. `npm install -g strongsuit`."
- [C] `website/guide/getting-started.md`: rename the code-group tabs to "npm" and "from source"; drop "(after 1.0.0 ships)" and "(works today)".
- [C] `README.md` quick start already leads with npm. Remove the "until 1.0.0 ships" note under it.
- [C] Add the npm version badge target (already wired to `npm/v/strongsuit`; it renders once the package exists).
- [H] Confirm the Pages deploy, then open the landing in a fresh browser: favicon, title, Open Graph card (paste the URL into a Slack or X composer to see the card).

## Gate 4 — launch (T-0)

The calendar, posting windows and hour-by-hour runbook are in `launch/GTM.md`. Copy per channel is in `launch/copy/`. Sequence on the day:

1. Show HN at 08:00–10:00 ET, Tuesday to Thursday (`launch/copy/show-hn.md`). Post the maintainer comment within five minutes.
2. r/ClaudeCode, then r/ClaudeAI, mid-morning US (`launch/copy/reddit.md`). Read each sub's self-promo rules first; they could not be fetched by script.
3. X thread with the shots (`launch/copy/x-thread.md`), LinkedIn post.
4. Reply to every comment within the hour for the first six hours. Honest answers; the objection FAQ is in GTM.md.
5. T+1: newsletters (`launch/copy/newsletters.md`), T+3: awesome-list PRs (`launch/copy/awesome-lists.md`), T+7: Dev.to long-form (`launch/copy/devto-post.md`), Product Hunt on a Tuesday or Wednesday at 00:01 PT (`launch/copy/producthunt.md`).

## Gate 5 — after launch

- [H] Triage issues daily for two weeks. A bug from a stranger is the best signal the launch reached anyone.
- [C] Patch releases: bump `package.json`, add a section to `RELEASE-NOTES.md`, tag `v1.0.x`, push tags. Same pipeline.
- [C] Mark XO-145 and XO-148 Done in Linear (the Linear connector was disconnected during this session).
- [H] Optional analytics: a privacy-friendly counter (Plausible, GoatCounter) needs a script tag in `website/.vitepress/config.ts` `head`. Not required for launch.

## Imagery and identity index

| Asset | Path | Use |
|---|---|---|
| Open Graph card | `website/public/og.png` (copy of `assets/brand/og.png`) | link previews, repo social preview |
| Favicons | `website/public/favicon.ico`, `favicon.svg`, `apple-touch-icon.png` | site |
| Avatar | `assets/brand/social-avatar.png` | X, Product Hunt, npm, Ko-fi |
| README banner | `assets/brand/readme-banner.png` | README header |
| X header | `assets/brand/x-header.png` | X profile |
| Terminal shots | `assets/shots/*.png` | README, posts, Product Hunt gallery |
| Animated demo | `assets/shots/suit-up.gif` | README, X, Reddit |
| Identity sheet | `BRAND.md` | anyone writing about it |
| Origin story | `STORY.md` | long-form posts |
| Press kit | `launch/press-kit.md` | anyone asking for facts |

All terminal shots are real output from a sandboxed `STRONGSUIT_HOME`, framed in the site's palette. Nothing in them is mocked.
