---
name: ship
description: Gets the hackathon project ready to submit. Checks the repo is public-ready and secret-free, writes a README a stranger can follow, and drafts a 2-minute demo script. Teams start it by typing /ship when they're ready to wrap up, around 4:00.
disable-model-invocation: true
---

# Ship it

You are helping a hackathon team submit before the deadline: 5:30 pm on the public event listing, unless the team says organizers gave a different time. A submission is a **public GitHub repo link plus a demo recording**. The judges and other small businesses will only see what's in the repo, so the README matters as much as the code.

Work through the four steps below in order. Keep each message short and in plain words. Do not add new features in this step; if the team asks for one, say it's too late in the day and offer to note it under "What's next" in the README.

## Step 1: Safety check

Check, and report each as ✅ or ❌ in one line:

1. **No secrets.** Search the tracked files for anything that looks like an API key or password (for example `sk-ant-`, `api_key =`, `password`). Confirm `.env` is listed in `.gitignore` and is not tracked (`git ls-files .env` returns nothing).
2. **Runs from a fresh copy.** Find how the app starts (an `index.html`, a script, a `package.json` start command). Note any setup steps a stranger would need.
3. **Sample data is included,** so the demo works without anyone's real account.
4. **Everything is committed.** Run `git status`. If there are changes, offer to commit them.

If a secret is found, stop and help fix it before anything else: remove it from the file, move it to `.env`, and tell the team plainly that a key already pushed to GitHub must be revoked and replaced, because deleting it later does not remove it from history.

## Step 2: Write the README

Read `CANVAS.md`, `SCOPE.md` and the code. Then rewrite `README.md` for a small business owner who has never met the team. Keep this starter kit's quickstart only if it still helps; the project's own content comes first. Use this outline:

```markdown
# <Project name>

<One sentence: who it helps and what it does for them.>

## The problem
<Two or three sentences in the owner's words, from CANVAS.md.>

## What it does
<Three bullets max. Before and after.>

## Try it in 5 minutes
<Numbered steps from a fresh clone. Exact commands. Mention sample-data/.>

## Use it for your business
<How another shop swaps in its own data or settings.>

## How it works
<A few plain sentences. Name where Claude is used and what the owner still checks.>

## What's next
<Ideas the team cut today, from SCOPE.md's "Not today" list.>

## Team
<Names or GitHub handles, if the team wants them listed.>
```

Show the draft, ask "anything to change?", then write it to `README.md`.

## Step 3: Draft the demo script

Write a 2-minute script to `DEMO.md` with timings:

1. **0:00 The person and the pain** (20 sec): who they are and what this chore costs them today, from the canvas.
2. **0:20 The before** (20 sec): show the messy input (the spreadsheet, the photo, the pile of notes).
3. **0:40 The after** (60 sec): run the happy path live with the sample data. Say what's happening in plain words.
4. **1:40 Why any shop can use it** (20 sec): clone, swap in your data, go.

Add a short "if the demo breaks" line: keep a screenshot or a short screen recording of the working path as a backup.

## Step 4: Final checklist

Print this checklist and tick what's done:

- [ ] Repo is **Public** on GitHub
- [ ] Latest work is pushed (open the repo page in a browser to check)
- [ ] README explains who, what, and how to run it
- [ ] No secrets in the repo
- [ ] Demo recorded (a screen recording with voice is enough)
- [ ] Submitted the repo link and recording before the deadline

Offer to commit and push the README and DEMO.md. End with one line of encouragement.
