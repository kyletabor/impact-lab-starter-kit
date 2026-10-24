# Project instructions for Claude

This is a one-day hackathon project at the Claude Impact Lab Hackathon. A team of 3 to 5 people is building a tool that **any small business** can pick up and use. Building starts at 10:30, and the team submits a public GitHub repo plus a demo recording by the deadline: 5:30 pm on the public event listing. If the team says organizers gave a different time, use theirs.

## Who you're working with

- Mixed teams: a small business owner, a student or recent grad, and an experienced professional. Some have never coded.
- Explain things in plain words. When you use a technical term for the first time, add a short everyday explanation.
- Keep replies short. Say what you did, then what to do next.
- Don't guess anyone's gender from a name or a role. Say "the owner" or "they" unless someone tells you their pronouns.

## Start of every session

1. If `SCOPE.md` exists, read it. It is the plan. Build only what is on its "Build" list.
2. If only `CANVAS.md` exists, suggest running `/scope` before building anything.
3. If neither exists, suggest running `/canvas` first. Building before you know who it's for wastes the day.

## How to build here

- **Smallest thing that works.** One happy path first: one user, one input, one useful output. Polish later.
- **Simple stack.** Prefer a single web page (HTML, CSS, JavaScript) or one small Python or Node script. Avoid databases, logins, and deployment unless `SCOPE.md` says they're required.
- **Sample data first.** Create realistic fake data in a `sample-data/` folder so the demo never depends on a live account.
- **Commit after each working step** with a clear message, so the team can always go back.
- **Ask before** installing large dependencies, deleting files, or changing how the app is structured.
- **Never put secrets in files you commit.** API keys go in `.env` (already in `.gitignore`); document them in `.env.example`.
- **Keep the API key off the web page.** If the app calls Claude, do it from a tiny local server or script that reads `.env`, never from browser JavaScript.
- **Keep the owner in charge.** Anything that writes to a customer or spends money should be a draft the owner approves.

## Done means

- It runs from a fresh clone by following the README.
- The demo path works with the sample data.
- The README tells a stranger who it's for, what it does, and how to run it in under 5 minutes.

## Guided steps

- `/canvas`: fill in the Small Business Impact Canvas, one block at a time, into `CANVAS.md`.
- `/scope`: cut the idea to a one-day demo and a build plan, into `SCOPE.md`.
- `/ship`: check the repo is ready, write the README, and draft the demo script.
