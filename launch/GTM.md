# Go-to-Market Plan: strongsuit

## Positioning Statement

strongsuit solves the problem Claude Code itself surfaced: skill inflation. The token warning exists; the stock remedies (disable one at a time, delete and re-download) are clumsy. strongsuit offers the missing tool: named groups you switch between with one command, plus a review pipeline that gates everything remote.

Positioning: control the context your agent runs in, without deleting anything ever.

## Audience

**For:** Claude Code power users (developers who have accumulated 8+ skills across multiple domains, feel the token cost, and want per-task switching without friction).

**Secondary (later):** Teams sharing suits — not a current commitment.

**Not for:** Beginners just installing Claude Code. Anthropic customers seeking an official tool. Users who want automatic detection.

## Three Core Messages

### Message 1: Control

**Claim:** You dress your agent for the task, atomically, without deleting anything.

**Proof:** The tool switches via symlinks only; real files never leave the library. Activation failures roll back. Documentation shows the whole mechanism (`~/.claude/` tree layout). Users test this day one: a `suit off` reverses every switch.

**Where:** README, landing page, first sentence of copy.

### Message 2: Trust

**Claim:** Remote suits are shown in full and approved before any bytes touch your machine.

**Proof:** The review pipeline is demonstrated end-to-end on the website (Look 02). Every component is printed, risk-classed (prompt-surface / process/network / code-executing), and individually approved. Approvals pin content by sha256 hash; drift blocks with a diff. Documentation: docs/review.md. Verification: nine mutations, all killed by named tests.

**Where:** "Before and after" screenshots on landing, safety guide, every install post.

### Message 3: No Deletion

**Claim:** Nothing you own ever gets deleted, by this tool or by accident.

**Proof:** `suit init` snapshots the active directory first. `suit restore` returns it exactly. Deactivating a suit moves symlinks only. Foreign symlinks are never touched. Documentation: README (§ Safety section).

**Where:** README, every "reversible" claim, the care label on the landing page.

## Channel Plan (Ranked)

### Tier 1 (Highest Leverage)

**1. Show HN** (post first, then cross-promote)
- **Rationale:** HN's audience overlaps perfectly — power users of dev tools, skeptics of marketing, readers who value honesty and evidence.
- **Posting window:** Tuesday–Thursday, 8–10am ET (peak HN visibility).
- **Timeline:** T-0 (launch day morning).
- **Copy:** Technical narrative from STORY.md, with honest limits called out.

**2. Reddit r/ClaudeCode**
- **Rationale:** Direct Claude Code community. Highest conversion to actual users.
- **Posting window:** Weekday mornings (US time), 9–11am.
- **Timeline:** T-0 afternoon (after HN momentum).
- **Copy:** From STORY.md, open-source positioning, invite for feedback.

### Tier 2 (Sustained Reach)

**3. Reddit r/ClaudeAI**
- **Rationale:** Broader Claude user base; lower specificity than r/ClaudeCode but larger audience.
- **Timeline:** T+1 (day after launch).
- **Copy:** Product summary + link, invite questions.

**4. Reddit r/commandline**
- **Rationale:** CLI tool appreciation. Emphasize the mechanism and no-nonsense design.
- **Timeline:** T+2.
- **Copy:** CLI-focused angle; less about Claude, more about symlink elegance.

**5. X (Twitter) thread**
- **Rationale:** Real-time reach, threading allows depth without noise.
- **Timeline:** T-0 morning (parallel with HN, then update throughout day).
- **Copy:** 8-post thread, built from launch/copy/x-thread.md.
- **Images:** One per post (from assets/shots/).
- **Strategy:** Lead with tagline, then three messages (control/trust/no-delete), then one command example, then launch link, then GitHub link.

### Tier 3 (Secondary Legs)

**6. Product Hunt** (optional, quality bar high)
- **Rationale:** Vetted audience, product-focused. Worth it only if full polish can land.
- **Timeline:** T+3 (Wednesday, if launch is Monday).
- **Posting window:** 12:01am PT (first thing when day rolls over).
- **Copy:** From launch/copy/producthunt.md.
- **Caveat:** Skip if README or landing is not complete by T-3.

**7. Dev.to long-form**
- **Rationale:** SEO reach, blog-friendly audience, narrative depth.
- **Timeline:** T+7 (first full week).
- **Copy:** From launch/copy/devto-post.md (~1400 words).

**8. Hashnode long-form** (if capacity allows)
- **Rationale:** Overlaps Dev.to, worth cross-posting if writing is already done.
- **Timeline:** T+10.
- **Copy:** Same as Dev.to with Hashnode frontmatter.

### Tier 4 (Communities and Async)

**9. Anthropic Discord #show-and-tell**
- **Rationale:** Direct-to-team visibility, community interest.
- **Timeline:** T+1 (day after launch).
- **Copy:** From launch/copy/communities.md (short).
- **Tone:** Honest, not seeking validation, inviting technical questions.

**10. Claude Code GitHub Discussions (Show and tell)**
- **Rationale:** Where Claude Code users gather. Signal to Anthropic about demand.
- **Timeline:** T+1.
- **Copy:** From communities.md, ask for feedback on the review design.

**11. Awesome-lists PRs**
- **Rationale:** Long-tail SEO and discoverability.
- **Timeline:** T+5 through T+20 (batch over two weeks, space them).
- **Lists:** See launch/copy/awesome-lists.md for verified entries.

**12. Newsletter submissions**
- **Rationale:** Press reach, passive discovery.
- **Timeline:** T+5 to T+14.
- **Submissions:** Console.dev, TLDR, Bytes, Changelog News, JavaScript Weekly (see launch/copy/newsletters.md for pitches).
- **Turnaround:** Most newsletters publish 1-3 weeks after submission.

## Launch Calendar (T-7 to T+14)

| Day | Task | Owner | Success Looks Like |
|---|---|---|---|
| **T-7** (Monday, week before) | README and landing finished. No typos. Site deployed. | maintainer | `git log` shows "v1.0.0 ready for release"; site renders, no 404s |
| **T-5** (Wed) | Assets finalized: banner, og-image, social avatar. GitHub topics/description polished. | maintainer | assets/ folder complete; GitHub repo tagline ≤100 chars |
| **T-3** (Fri) | Show HN + Reddit copy finalized. Honest limits called out. | maintainer | launch/copy/ files have zero typos; read by 3+ eyes |
| **T-1** (Sun night) | npm publish queued but not yet released. GitHub release drafted (not published). | maintainer | v1.0.0 tag exists, waiting on `npm publish` |
| **T-0 (Tue, 8am ET)** | npm publish executed. GitHub release published (v1.0.0). | maintainer | `npm install -g strongsuit` works; GitHub shows "Latest release" |
| **T-0 (8:15am)** | Show HN post goes live with title and first comment. | maintainer | Post appears on "New" page within 3 min; first comment is the maintainer's |
| **T-0 (Tue, 2pm)** | Reddit r/ClaudeCode post goes live. | maintainer | Post is live, pinned top of subreddit 1hr; auto-reply is the call to action |
| **T-0 (Tue, evening)** | X thread begins (all 8 posts queued, posted 1 per hour). | maintainer | All 8 posts visible by 10pm ET; images render; engagement tracked |
| **T+1 (Wed, 9am)** | Reddit r/ClaudeAI post goes live. | maintainer | Post live; crosslink to r/ClaudeCode in comments visible |
| **T+1 (Wed, 2pm)** | Anthropic Discord #show-and-tell message posted. | maintainer | Message gets 5+ reactions within 1hr; replies are questions (not spam) |
| **T+1 (Wed, 3pm)** | Claude Code GitHub Discussions "Show and tell" post goes live. | maintainer | Post in correct category; GitHub notifications send to Anthropic team |
| **T+2 (Thu, 9am)** | Reddit r/commandline post goes live. | maintainer | Post live; top-level comment links to GitHub with one sentence of context |
| **T+3 (Fri, 12:01am PT)** | Product Hunt goes live (if quality bar met; otherwise skip). | maintainer | #1 or top-3 by 9am PT; maker comments within 15min of each question |
| **T+5 (Sun)** | First awesome-list PR submitted (staggered over 10 days). | maintainer | GitHub PR shows merged within 24-72hrs for responsive lists |
| **T+7 (Tue)** | Dev.to post published. | maintainer | Post appears on platform; "Edit" link confirms publication |
| **T+5-T+14** | Newsletter submissions sent (batch 5 at a time). | maintainer | Submission confirmations received; no bounced emails |
| **T+14 (Mon)** | Review launch metrics and triage feedback issues. | maintainer | Dashboard open showing stars, npm downloads, GitHub issues opened |

## Launch-Day Runbook (T-0, by Hour)

| Time (ET) | Action | Owner | Decision Point |
|---|---|---|---|
| **7:45am** | Confirm npm token is valid. GitHub release draft is finalized. | maintainer | Test: `npm whoami` succeeds. Release body has correct asset links. |
| **8:00am exact** | Publish npm. Monitor for success (check npm registry in 30 seconds). | maintainer | `npm view strongsuit` shows v1.0.0 published. If fails, revert and diagnose. |
| **8:05am** | Publish GitHub release (v1.0.0). Confirm tag is visible. | maintainer | GitHub shows "Latest release" badge. CLI `github release list` shows it. |
| **8:10am** | Post Show HN title + comment. First comment is the maintainer's. | maintainer | Post on HN "New" page visible. Comment contains honest limits section. |
| **8:20am** | Monitor HN post for first vote momentum (should hit ~5 points in 5min). | maintainer | If flat after 10min, check: typo in title? Did post go to wrong section? Do not re-post. |
| **9:00am** | Post r/ClaudeCode. Include top-level comment with the story. | maintainer | Post visible in subreddit. Do not cross-link to HN yet; let them find it. |
| **10:00am** | Monitor both posts; reply to top-level technical questions within the hour. | maintainer | HN and Reddit both have replies from maintainer to first 5 questions. |
| **2:00pm** | Post r/ClaudeAI (acknowledge it is cross-posted, give it a different angle). | maintainer | Post visible. Comment mentions r/ClaudeCode for deeper technical dive. |
| **2:30pm** | Queue X thread (8 posts, post one per hour starting at 3pm). | maintainer | First post scheduled; images render in preview. |
| **3:00pm onward** | X posts automated, one per hour. Monitor replies 3-6pm, then spot-check. | maintainer | Each post appears on timeline. Engagement trending (likes, retweets, replies). |
| **6:00pm** | Final check: HN post rank, Reddit votes, X impressions, npm downloads (should see 50–200 by now). | maintainer | Metrics dashboard open. If HN is past top 30, celebrate; if not, that is fine. |
| **End of day** | Collect all feedback from posts, sort by actionable vs. questions vs. compliments. | maintainer | Issues/questions logged; replies drafted for next day. Sleep. |

## Reply-Within-the-Hour Rule

**On HN, Reddit, X:** Respond to every question, concern, or bug report within one hour of publication, for the first 6 hours. After that, daily check-in is sufficient.

**What to reply with:**
- Questions about the mechanism: link to the relevant README section.
- Concerns about safety: link to docs/review.md or the mutation-test evidence.
- Honest limits (skills additive, MCP reset on bare resume): confirm and cite the README care label.
- Feature requests: thank them, add to GitHub issues, say "backlog note."
- Bug reports: triage immediately, ask for reproduction steps, link to GitHub issues.

**What never to argue about:**
- "Why not built-in to Claude Code?" → State the facts: the per-skill enable/disable request (anthropics/claude-code#43928) was closed as not planned in June 2026; Claude Code has per-skill toggles in the `/skills` panel, which strongsuit respects. strongsuit adds named groups across every component type, one atomic switch, review for remote content, and per-session wear. Then stop.
- "Can I use this on Windows?" → See README Limitations section; it is in the honest limits list.
- "Is this official?" → No, independent open-source, MIT licensed. Made to work with Claude Code, not by Anthropic.

## Objection Handling FAQ

### "Why not just disable skills in Claude Code settings?"

**Honest answer:** Claude Code's UI lets you disable skills one at a time. Re-enabling them later means finding each one and toggling again. No concept of groups. No way to bundle MCP servers and hooks with those skills. strongsuit adds all three: named groups (suits), atomic switching, and one command for the whole bundle. You can ignore it if disabling one at a time works for you.

### "Is this security software?"

**Honest answer:** It is not a security tool for your machine. Review gates the remote boundary: everything you fetch is shown and approved before landing. Everything you create locally activates without gating (you wrote it). The pipeline is designed to stop drift — if a suit you approved is updated, activation blocks with a diff. Think of it as "approval attaches to content, not names."

### "Does it modify my Claude Code config?"

**Honest answer:** `suit init` snapshots your active skills directory first, so you can restore. Afterwards, switching moves symlinks in that directory only. JSON surfaces (MCP, plugins, hooks) go through an ownership ledger: we only modify keys we wrote, detect foreign edits by hash, back up before first touch. Per-session (`suit run`) leaves your global config untouched entirely.

### "What happens if I uninstall?"

**Honest answer:** `suit off` deactivates all managed entries. Your library (skills and their history) stays in `~/.claude/strongsuit/` unless you delete it manually. `suit restore` puts the active directory back to its pre-init state. If you `rm -rf ~/.claude/strongsuit/`, you lose the library but your active skills directory is unchanged.

### "Does this work on Windows?"

**Honest answer:** Symlinks on Windows require either Developer Mode or elevation, depending on your setup. The tool uses junctions for directories and file symlinks where needed. It is untested on Windows. See README Limitations for workarounds. If this blocks you, GitHub issues are the right place to flag it.

### "Is this Anthropic-affiliated?"

**Honest answer:** No. Independent open-source, MIT licensed. I built it to solve a problem Claude Code itself surfaced. It is in the ecosystem, not of the team.

### "What about token savings?"

**Honest answer:** Token figures are estimates (file bytes ÷ 4), useful for comparing which skills are bloated, never measurements. The real savings appear in your session context — you will see it yourself when a tool runs in a smaller suit. If you want precise numbers, measure before and after in your own conversation. This tool does not measure for you.

### "Can multiple people share one suit?"

**Honest answer:** Not yet. Each person installs strongsuit on their own machine. You can publish your suits to GitHub (or anywhere), and others can `suit install your/repo` to fetch and review them. Shared/team suits are in the roadmap but not a current feature.

### "Does this slow down Claude Code?"

**Honest answer:** Switching suits is O(number of skills) filesystem operations, typically sub-second. Launching a session with `suit run` materializes an ephemeral plugin, which adds a few milliseconds. The actual model latency dominates; this tool does not change Claude's performance.

## Success Metrics (Honest for OSS Launch)

Track these starting T-0:

### Immediate (T-0 to T+7)

- **GitHub stars:** Aim for 150+ by T+7. Reflects initial interest.
- **npm weekly downloads:** Should see 50–300 installs in first week. (Published on T-0, so data lags by 1 week initially.)
- **Show HN rank:** Top 100 is solid; top 30 is great. Reflects technical audience alignment.
- **Reddit upvotes + comments:** r/ClaudeCode post at 50+ points, 20+ meaningful comments (technical questions, not spam).
- **Issues opened:** 5–15 genuine issues (bug reports, feature requests, questions) is healthy. Zero issues suggests zero adoption.

### First Month (T+14 to T+30)

- **npm cumulative installs:** 500–2000 indicates real adoption beyond launch day.
- **GitHub forks:** 10–30 forks in month one is solid for a dev tool.
- **Repeat mentions on Reddit, HN:** Evidence that the tool is staying in conversation.
- **Open issues trend:** Should stabilize around 3–5 open issues per day (healthy velocity).

### Honest Interpretation

- **Strong launch:** 200+ stars, 500+ npm installs, top-30 on HN, 10+ forks by T+30. → audience exists, credibility established.
- **Moderate launch:** 100+ stars, 300+ npm installs, top-100 on HN, 5+ forks. → tool works, some adoption, needs word-of-mouth.
- **Flat launch:** <100 stars, <150 npm installs, not on HN front page, <3 forks. → audience may not exist; revisit positioning or ship more docs.

**Metrics NOT to track:** downloads from other sources, testimonials, claims about how many "active" users (we will not know), projected growth curves. Those numbers invite fiction. Track what is observable and honest.

## Sponsor-Link Placement Rules

Ko-fi and GitHub Sponsors links go in these places only:

1. **README:** One line in "About" section: "Support development: [GitHub Sponsors](link) · [Ko-fi](link)"
2. **Website footer:** Paired link in footer nav.
3. **GitHub repository:** FUNDING.yml with GitHub and Ko-fi links.
4. **Never:** Launch posts, Reddit/HN copy, X thread, newsletter submissions, awesome-list PRs, or any promotional channel. Those are for the product, not the maintainer's wallet.

Rationale: Sponsors are for people already interested enough to click through. Launch copy is for conversion, not monetization.

## Risks and Failure Scenarios

### Risk 1: Unclear Messaging

**If:** First 24 hours show confusion (comments like "I don't understand what this does").

**Then:** The landing page or README intro is too jargon-heavy. Update README opening paragraph to start with the problem statement: "Claude Code warns when skills inflate tokens, but the only remedy is delete-and-re-download. strongsuit solves this: one command to switch between named groups."

### Risk 2: Windows Symlink Failure Goes Unnoticed

**If:** Launch happens and Windows users do not report issues until weeks later, by which time it is "known broken."

**Then:** Mention Windows explicitly in launch copy ("Symlinks on Windows require Developer Mode; see README for workarounds"). Set the expectation upfront rather than having users discover it.

### Risk 3: Safety/Review Pipeline Underestimated

**If:** Someone breaks a review guard and the tool silently approves code it should not.

**Then:** That mutation escaped testing (unlikely, but possible). Triage as blocker. Fix and patch-release v1.0.1 same day. Post a notice "security fix" on all channels.

### Risk 4: npm Publish Fails or Gets Delayed

**If:** npm registry is down or the package name is taken.

**Then:** Have a contingency: GitHub release + install-from-source instructions go live immediately. A few hours of `npm link` only is acceptable; 24+ hours is a problem. Keep the install instructions in README updated.

### Risk 5: Low Engagement, Few Stars

**If:** T+7 arrives and stars are under 100, npm installs under 200.

**Then:** The problem may not be acute enough for the audience, or messaging is missing something. Do not re-launch. Instead: gather feedback from issues and Reddit comments, write a follow-up blog post addressing the most common question, and let word-of-mouth compound over the next month. Some tools grow slowly and are still successful.

### Risk 6: Anthropic Releases a Native Skills-Grouping Feature

**If:** Within weeks of launch, Claude Code adds groups to the UI.

**Then:** strongsuit still has review and per-session isolation, both of which are not trivial. Acknowledge the native feature, reposition around the higher-value gaps (control + trust + measured isolation), and keep the tool maintainable for the users who want it.

### What to Never Do if Launch Underperforms

- Do not invent testimonials or fake users.
- Do not overstate adoption or claim "thousands" without numbers.
- Do not blame the audience ("they do not get it").
- Do not spam additional channels to pump metrics.
- Do not remove honest caveats to make the pitch cleaner.

Own the results, learn from feedback, and iterate. A slow launch that leads to a sustainable community is better than a hyped launch that collapses.
