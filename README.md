# Impact Lab Starter

A starter kit for the **Claude Impact Lab Hackathon** (Seattle AI Week). It gets your team into Claude Code in about 10 minutes, then walks you from "we have an idea" to "we have a demo we can finish by the submission deadline."

You get three guided steps that run inside Claude Code:

| Step | Type this in Claude Code | What you get | Time |
|---|---|---|---|
| 1. Canvas | `/canvas` | `CANVAS.md`: who you help, their problem, why they'd care | ~30 min |
| 2. Scope | `/scope` | `SCOPE.md`: the smallest demo worth building, and a plan for the day | ~15 min |
| 3. Ship | `/ship` | A README another business can follow, plus your demo script | ~30 min |

The canvas is modeled on the Business Model Canvas, a one-page map of how a business creates value. This version is tuned for one-day tools that any small business can pick up and use.

---

## The 10-minute quickstart

You need a laptop, a terminal, a GitHub account, and a way to pay for Claude (your event API credits, or a Claude Pro or Max plan).

### 1. Install Claude Code (2 min)

Open a terminal and run the line for your computer.

macOS, Linux, or WSL:

```bash
curl -fsSL https://claude.ai/install.sh | bash
```

Windows PowerShell:

```powershell
irm https://claude.ai/install.ps1 | iex
```

Windows Command Prompt (CMD):

```bat
curl -fsSL https://claude.ai/install.cmd -o install.cmd && install.cmd && del install.cmd
```

Then **open a new terminal window** and check it worked:

```bash
claude --version
```

You should see a version number followed by `(Claude Code)`. If it says `claude` isn't found, see [Fix your PATH](https://code.claude.com/docs/en/troubleshoot-install).

Never used a terminal? Start with the official [terminal guide](https://code.claude.com/docs/en/terminal-guide).

### 2. Get your own copy of this repo (3 min)

Only one person per team does this, then invites the others.

1. On this repo's GitHub page, click **Use this template**, then **Create a new repository**. (No button? Click **Fork** instead.)
2. Name it after your idea, and set it to **Public**. Every submission needs a public repo.
3. Invite teammates: your repo's **Settings**, then **Collaborators**, then **Add people**.

Everyone then copies the team repo to their laptop. Swap in your own repo's address, from the green **Code** button:

```bash
git clone https://github.com/YOUR-TEAM/YOUR-REPO.git
cd YOUR-REPO
```

### 3. Start Claude Code and sign in (3 min)

From inside the repo folder:

```bash
claude
```

The first time, it asks you to sign in through your browser.

- **Using event API credits?** Pick the **Claude Console** account, the one your credits went to.
- **Have Claude Pro or Max?** Sign in with that account instead.

To switch accounts later, type `/login` inside Claude Code.

### 4. Say hello (2 min)

Try these, one at a time:

```text
what does this project do?
```

```text
/canvas
```

That's it. You're building.

---

## How the day runs

Building starts at 10:30. The public event listing puts the submission deadline at 5:30 pm; confirm it at the 9:45 kickoff, because organizers have the final word. A plan that works:

| Time | What to do |
|---|---|
| 10:30 | `/canvas` together, with your small business owner talking first |
| 11:00 | `/scope`, then pick who builds what |
| 11:20 | Get a "hello world" version running with sample data by noon |
| 12:00 | Build the one core flow. Commit every time something works |
| 1:00 | Lunch. Show a teammate what works so far |
| 3:30 | Fix what's broken |
| 4:00 | Feature freeze. `/ship`: write the README and record the demo |
| 5:30 | Submit your repo link and demo recording (or whatever time organizers confirm) |

**What you submit:** a public GitHub repo link plus a demo recording. Build something any small business can use, not a custom tool for one shop.

---

## Five habits that save your day

1. **Talk to Claude like a teammate.** Say what you want and why: "add a button that turns this list into a printable prep sheet for a bakery."
2. **Commit when it works.** Type `commit what we have with a clear message`. If something breaks later, you can go back.
3. **Fake data is fine.** A good demo uses a realistic sample spreadsheet, not a live connection you fight with all afternoon.
4. **Never paste secrets into files.** API keys go in a `.env` file, which this repo already keeps out of GitHub.
5. **Stuck for 15 minutes? Ask a mentor.** That's what we're here for.

## Handy Claude Code commands

| Type this | What it does |
|---|---|
| `/help` | Lists commands (type it inside Claude Code) |
| `/clear` | Starts a fresh conversation (your files stay) |
| `Shift+Tab` | Changes how often Claude asks before acting |
| `claude -c` | Type it in the terminal, not inside Claude Code: picks up your last conversation |
| `/exit` | Leaves Claude Code |

## What's in this repo

```
CLAUDE.md                     Instructions Claude reads every session
.claude/skills/canvas/        The /canvas guided canvas
.claude/skills/scope/         The /scope cut-it-down step
.claude/skills/ship/          The /ship submission step
templates/CANVAS.template.md  The canvas layout /canvas fills in
examples/ideas.md             Starter ideas if your team is stuck
examples/sample-canvas.md     A finished canvas and scope, for reference
docs/github-basics.md         GitHub in plain words
```

## Learn more

- [Claude Code quickstart](https://code.claude.com/docs/en/quickstart), the official guide
- [Claude Code 101](https://academy.claude.com/courses/claude-code-101), a free course

---

Made by Kyle Tabor, a mentor at the hackathon, with Claude. MIT licensed: copy it, change it, share it.
