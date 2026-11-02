# 3 Little Sparks

How to work on this project. **Part A** is the owner's standard way of working, the same in every repo. **Part B** is about this project only.

## Part A: Working with the owner

> Standard Part A, **v1 (2026-11-02)**, identical in every repo. The master copy is `docs/CLAUDE_TEMPLATE.md` in `truthytruth/Flip-Toolkit`. To change it, change the master first, bump the version, then copy it into every repo's `CLAUDE.md`.

**Start of every session:** read `docs/HANDOFF.md` (what's live, what's open) before doing anything else.

### Who I am and how I work
- I'm the sole owner and developer. I work **from an iPhone**, usually in the Claude app, and don't have a Mac.
- Give setup steps **one at a time** and wait for me to confirm each one before the next.
- Put anything I need to copy (names, URLs, short values) in its own code block. For long code or SQL, publish a page with a **Copy** button (a claude.ai artifact). The file viewer can't copy text.
- When a website is awkward on a phone and the service has an iOS app (GitHub, App Store Connect, Cloudflare, Render, Stripe…), point me to the app first.
- Never ask me to paste passwords, API keys, signing keys or other secrets into chat. Tell me where to enter them (dashboard, GitHub secret, environment variable) instead.

### What you can do without asking, and what needs my OK
**Go ahead (no need to ask):**
- Read anything, make a branch, commit to it, push the branch, run tests and local checks.
- Push changes that are **only docs** (plans, HANDOFF, SPEC, notes, this file) straight to `main`. Tell me afterwards.

**Ask me first, every time (an earlier yes doesn't carry over to the next change):**
- Merging or pushing anything else to `main`, or anything else that changes the live app. That includes over-the-air/live updates to installed phone apps.
- Changes to the live database, and deleting real data.
- Anything that **costs money**: macOS/iOS builds on GitHub Actions (they count ×10 against the free minutes), paid APIs or AI, new subscriptions or paid tiers. Say roughly what it will cost.
- Submitting to the App Store / TestFlight, sending emails or posts to real people, or anything else public.
- Deleting or renaming repos, services, domains or environment variables.

**Never:**
- Force-push `main`, rewrite its history, or skip/disable tests to get something passing.
- Put secrets in the repo or in chat.
- Guess at a third-party format or API (bulk-upload files, API fields, fee rates). Check the real docs, or ask me for a sample.

### Workflow for every change
1. Work on a branch named `claude/<short-topic>`. No pull request unless I ask for one.
2. Verify it: the checks under **Testing** in Part B, plus a **phone-width (390×844) browser check** for anything I'll see on screen.
3. Tell me what changed **in plain English** (see below) and what you checked.
4. Ask whether to merge. On a yes, merge to `main` and push. Then tell me what I need to do, if anything.
5. Update `docs/HANDOFF.md` if what's live or what's open changed.

### Plain English (a real bar, not a formality)
When work wraps up, describe it the way you'd explain it on the phone: what I or my users will now see or be able to do. No file names, function names or diff recaps. ("Players now see an Upgrade button when their trial runs out", not "added `trial_expired()` to auth.py".) A short technical note can follow, but it never replaces the plain-English part.

### Reporting status honestly
Report each step separately, and only once it's actually verified: committed → pushed → merged → deployed → build started → build passed → uploaded → available in TestFlight → tested on my phone. A green GitHub Action alone doesn't mean "it's done". If something wasn't checked, say so.

### Design defaults
- **Mobile first.** My users are on phones, often in the middle of a live game or sale. Design for a narrow screen first. Avoid wide tables, multi-column layouts, hover-only controls and tiny tap targets.
- **Taps over typing:** short lists are tap buttons, not dropdowns or text boxes. Long lists use a bottom sheet.
- **Keep running costs at zero where possible.** Paid AI or paid APIs are optional add-ons only, and need my OK.
- **Money matters.** These apps handle real payouts and real sales. Treat money math like it matters: exact rounding, tests for it, and no silent fallbacks (a failed price fetch says so; it doesn't quietly use zero).
- **Multi-user from day one.** Every user's, business's or group's data is scoped and isolated, even while I'm the only user. If a change would make that harder later, tell me before doing it.

### Where things live (same layout in every repo)
| File | What it's for |
| --- | --- |
| `CLAUDE.md` | This file: the rules and lasting facts. Read automatically. Keep it short. |
| `docs/HANDOFF.md` | **Current state:** what's live, what's in progress, open items, owner decisions with dates. Read it at the start of every session; update it at the end. |
| `docs/SPEC.md` | The design record: how the app is meant to work and why. |
| `docs/plans/<NAME>_PLAN.md` | **New** plans, one file per feature, starting with a **Status:** line (planned / in progress / live / parked). Older plan files may sit elsewhere because code comments point to them by name. Part B lists them; don't move them. |
| `.claude/settings.json` + `.claude/hooks/session-start.sh` | Gets a cloud session ready to run the tests. |

When a plan, doc or comment no longer matches the code, fix the doc in the same change.

## Part B: This project

### What it is
The link page for 3 Little Sparks (https://3littlesparks.com): bamboo pajamas and 3D-printed
creations. A single static page linking to the shops on Whatnot and Vinted. This is the owner's
wife's business, so ask before changing wording, shops or branding.

### Stack and hosting
One static `index.html` (inline CSS, brand colors from the logo) with `logo.jpg`, `robots.txt`,
`sitemap.xml` and structured data for Google. Hosted on **GitHub Pages**: merging to `main`
publishes it at once. Custom domain via `CNAME`.

### Testing (run before asking to merge)
Open `index.html` in a headless browser at 390×844 and check the links, the logo and that
nothing scrolls sideways. Keep the structured data (`application/ld+json`) and `sitemap.xml` in
step with any shop change.
