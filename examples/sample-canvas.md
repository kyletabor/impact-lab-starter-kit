# Sample: a finished canvas and scope

This is what `/canvas` and `/scope` produced in a test run, for a made-up Thai restaurant owner on a hackathon team. Use it to see what "good" looks like. Your answers will be different.

---

## Small Business Impact Canvas: Review replies for small businesses

_Answers marked (guess) still need an owner to confirm them._

> **One-liner:** We help small business owners answer every review in their own voice so they keep customers coming back, without 3 hours of late-night writing.

### 1. Customer: who exactly?
- **The person:** Owner of a 40-seat Thai restaurant, who answers Google and Yelp reviews themselves at night.
- **Three-business test:** Hair salon, dentist office, auto repair shop. All get online reviews and the owner replies.

### 2. The chore and what it costs
- **The chore:** Answering about 25 Google and Yelp reviews a week, about 3 hours, after close.
- **How it's done today:** Reads reviews on their phone, writes every reply from scratch. Input data = the review text and star rating.
- **Why it isn't solved already:** Bad reviews sting, so they reply angry or not at all. Canned-reply tools sound fake and customers can tell.

### 3. The value: before and after
- **Before:** 3 hours a week, every reply written from scratch at night. Bad reviews get an angry reply or none.
- **After:** About 1 hour a week. The owner reads a draft in their own voice, tweaks it, posts. Bad reviews get a calm draft held for the next morning.
- **SUTAM (shut up and take my money)?** Likely yes: 2 hours back every week, plus no more angry replies. Still needs owner confirmation on price (see Block 7).
- **Hell Yeah bullets:**
  1. Replies that sound like me.
  2. Never angry.
  3. Done in 1 hour a week.
- **Hero check:** The owner approves every reply, and the tool learns the owner's phrases from replies they have approved or edited, so the voice stays theirs. (How the "learning" works is a guess to settle in `/scope`.)

### 4. Why you, and what could go wrong
- **Why our team:** The owner has run a 40-seat Thai restaurant for 9 years and answers reviews themselves every week, so they know which complaints are fair and what a good reply sounds like.
- **Biggest risks:** (1) Drafts sound generic instead of like the owner. (2) Claude invents facts or promises, like a refund or comp the business never offered.

### 5. Getting it
- **Who already reaches them:** Restaurant associations and POS sellers. (Other trades: local business associations, review-site reps `(guess)`.)
- **Steps to first result:** Clone the repo, paste 3 of your old replies so it learns your voice, paste new reviews, get drafts. Under 10 minutes.

### 6. Trust
- **What the owner approves:** Every reply. Nothing is posted without the owner's approval. Any draft that mentions money or refunds is flagged.
- **When Claude is wrong:** When unsure, it leaves a blank for the owner to fill in instead of guessing. It never offers refunds or comps the owner hasn't listed.
- **Report or told what to do?** Told what to do: "reply to these 3 first" (priority order, bad reviews first).

### 7. Napkin math
- **Worth per week:** 2 hours saved x $30 an hour = $60 a week, about $260 a month. Angry replies avoided not counted.
- **Cost to run:** About a penny per reply (guess). 25 replies a week is about $0.25 a week, roughly $1 a month. Setup under 10 minutes.
- **Would they pay?** The owner would pay $10 a month.

### 8. How it works
- **In:** Pasted reviews (text and star rating) plus 3 of the owner's old replies. A short facts list (hours, policies, what is and isn't offered) `(guess)`.
- **Claude does:**
  1. Sorts reviews by urgency.
  2. Drafts a reply in the owner's voice.
  3. Flags anything that mentions money or refunds.
  4. Leaves a blank where it's unsure `(from Block 6)`.
  5. Holds bad-review drafts for the next morning `(from Block 3)`.
- **Out:** A list of drafts in "reply to these first" order, ready to approve.
- **Plugs into:** Copy and paste into Google and Yelp. No logins or connections.
- **Demo sample data:** 12 fake Thai-restaurant reviews in `sample-data/` (mix of 5-star, 3-star and angry, including a refund demand) `(guess on the mix)`, plus 3 sample past replies for the voice.

### 9. One metric and the riskiest guess
- **Metric (a count, not dollars):** Replies posted without edits.
- **Guardrail (do no harm to):** Never promise money (no refunds, comps or discounts the owner hasn't listed).
- **Riskiest guess:** It really sounds like the owner, from just 3 old replies.
- **The demo proves it by:** The owner reads drafts blind, mixed in with their real past replies, and tries to tell which are which.

---

## Scope: Review replies for small businesses

_Built from the canvas above. Build only what is on the "Build today" list._

### The demo screen

**In:** 12 fake Thai-restaurant reviews pasted in, plus 3 of the owner's old replies and a short facts box.
**Out:** A list of reply drafts, angriest reviews first. Each draft is in the owner's voice, has a Copy button, and is flagged if it mentions money. Blanks are left where Claude is unsure. Bad-review drafts are marked "hold until morning".

A judge should get it in 30 seconds: a pile of reviews goes in, calm ready-to-approve replies come out, and the refund demand is flagged and not promised.

### Red-flag swaps

| Original idea | Swapped for |
|---|---|
| Auto-post to Google | A Copy button. The owner pastes into Google themselves. |
| Login for multiple restaurants | One restaurant, no login |
| Dashboard of trends | A one-line summary (e.g. "12 reviews: 7 positive, 3 mixed, 2 angry") |
| Learning the owner's voice over time | Copy the style of the 3 pasted replies |

### Build spec

1. **Goal:** Turn a pile of pasted reviews into reply drafts in the owner's own voice, so they spend about 1 hour a week and not 3.
2. **Trigger:** After close, once or twice a week, whenever reviews have piled up.
3. **Inputs:**
   - `sample-data/reviews.txt`: 12 fake reviews (text and star rating). A mix of 5-star, 3-star and angry, including one refund demand.
   - `sample-data/past-replies.txt`: 3 of the owner's old replies, for the voice.
   - `sample-data/facts.txt`: hours, policies, and what is and isn't offered (e.g. "no refunds or comps unless I say so").
4. **Output:** Drafts in "reply to these first" order. Each shows the review, the draft, a Copy button, and a red flag if it mentions money or refunds. Blanks show as `[FILL IN: ...]`. Bad-review drafts are marked "hold until morning". A one-line summary sits at the top. Good means calm, specific to what the reviewer said, and sounding like the owner's 3 old replies.
5. **Approval:** The tool never posts anything. The owner reads, edits, copies, and pastes into Google or Yelp themselves. Anything mentioning money or refunds is flagged in red.
6. **What could go wrong, and what the tool does:**
   - A review asks for a refund or comp: the draft offers none, flags it, and leaves a blank for the owner's decision.
   - A review mentions a detail Claude can't know (a dish, a date, a staff name): leave a blank, don't guess.
   - Drafts sound generic: the owner sees it right away. This is our riskiest guess, so we test it.
   - Claude or the server fails: show a plain error message and keep the owner's pasted text.
7. **How we'll know it worked** (test with the sample data):
   1. All 12 reviews get a draft, in urgency order, with the angriest first.
   2. The refund-demand review is flagged and its draft contains no refund, comp or discount.
   3. No draft promises anything that isn't in the facts box.
   4. Bad-review drafts are marked "hold until morning".
   5. Blind test: the owner reads 3 drafts mixed with their 3 real replies and can't reliably tell which are which.

### Cut list

**Build today** (ranked by impact × confidence ÷ effort)
1. Paste reviews and old replies, get drafts in the owner's style
2. Flag money and refunds, never promise any, leave blanks when unsure (uses the facts box)
3. Urgency order, with bad reviews marked "hold until morning"
4. Copy button and a one-line summary

**Fast-follow** (goes in the README's "What's next")
- Dropdown to switch to a salon, dentist or auto shop
- Real voice learning from replies the owner approves or edits
- Saved history and trend dashboard
- Yelp-specific formatting, such as length limits

**Not doing**
- Auto-posting to Google or Yelp (breaks "owner approves everything")
- Logins and accounts for multiple restaurants
- Pulling reviews straight from Google or Yelp

### Plan for the day

| Time | Goal |
|---|---|
| 10:30 to 12:00 | Scope locked. A "hello world" page and tiny server running. Sample data in `sample-data/` |
| 12:00 to 3:30 | The one core flow works end to end. Commit every time something works |
| 3:30 to 4:00 | Fix what's broken. Run the 5 pass checks. No new features after 4:00 |
| 4:00 to 5:15 | `/ship`: README, demo script, record the demo |
| 5:30 | Submit the repo link and demo recording (or the time organizers confirm) |

**Who does what** (adjust to your strengths)
- **Owner:** writes the sample data (12 reviews, 3 past replies, the facts box), checks every output, and runs the blind test. Also owns the demo story.
- **Student or recent grad:** builds the web page (paste boxes, draft cards, Copy button, summary line).
- **Experienced professional:** builds the tiny server and the Claude instructions (voice, flagging, blanks, urgency order).
- **README owner (pick one person now):** starts the README at 10:30 and adds to it as things work, so it isn't left to 5:00.

### The first prompt

> Make a simple web app that takes a pile of pasted customer reviews (text and star rating), 3 of the owner's old replies, and a short facts box, and uses Claude to produce reply drafts in the owner's voice for a small restaurant owner. Use one web page plus a tiny local server that reads the API key from `.env`, so the key never reaches the browser. Use the sample data in `sample-data/`. Keep it simple enough to run with one command, and write the README as you go.
>
> Rules for the drafts: sort reviews angriest first. Mark drafts for bad reviews "hold until morning". Never offer a refund, comp or discount that isn't in the facts box. Flag any draft that mentions money or refunds. Where a detail is unknown, write `[FILL IN: ...]` and don't guess. Show a Copy button on each draft and a one-line summary at the top. The tool never posts anything.
