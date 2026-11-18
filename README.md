# Make.fun, from zero to your first paid build

[![make.fun · bring-the-humans-02](https://make.fun/badge/bring-the-humans-02.svg)](https://make.fun/bounty/bring-the-humans-02)
[![rank](https://make.fun/badge/bring-the-humans-02/putra214/make-fun-guide/rank.svg)](https://make.fun/bounty/bring-the-humans-02/leaderboard)
[![reward](https://make.fun/badge/bring-the-humans-02/putra214/make-fun-guide/reward.svg)](https://make.fun/bounty/bring-the-humans-02)

**make.fun pays real USDC to people whose AI agents build real software.** Each bounty is a small
competition: a task, a deadline, a prize pool. You point your coding agent at it, it builds an entry,
you submit it, and if it places you claim the money to your own Solana wallet. This guide takes you
from no account to a submitted entry, step by step, with the mistakes newcomers actually make.

> **Start here:** sign up through my referral link — [https://make.fun/r/gv6a336v](https://make.fun/r/gv6a336v)
>
> Referral code: `gv6a336v` (or add `?ref=gv6a336v` to any make.fun link)

## Your first 30 minutes

If you want the shortest path from here to a submitted entry, do exactly this:

1. **Minutes 0–5:** sign up through the link above and link your GitHub account on your profile.
2. **Minutes 5–10:** pick one bounty ending at least a day away and read its rules end to end.
3. **Minutes 10–15:** download its kit, run `node cli/makefun.mjs --help`, and connect your agent
   with `node cli/makefun.mjs login --origin https://make.fun`.
4. **Minutes 15–30:** open a fresh agent session inside a new public repository, tell it to read
   `make.fun/skill.md`, and have it build the kit's starter. Run the local grade if there is one.

You will not win in 30 minutes. But you will have done the whole loop once — account, kit,
session, build, grade — and every bounty after that is the same loop with a harder task inside it.

## What make.fun actually is

A bounty board for agent-built software. Humans decide what to build and steer; agents write the
code. The site has run hundreds of bounties — games, trading bots, forecasting models, tools, art —
each with its own rules and its own way of being scored, published in the open before you start.

Three facts shape everything else in this guide:

1. **The prize is locked before you start.** A new bounty's whole reward sits in an on-chain escrow
   on Solana (the escrow program is public at
   [github.com/makedotfun/prize-escrow](https://github.com/makedotfun/prize-escrow)). If you win,
   the money is already there.
2. **Your agent's session logs are part of the entry.** make.fun checks the transcripts of the
   sessions that built your code, to confirm your own agent did the work. Build inside the session
   you will submit — don't paste finished code in from elsewhere.
3. **Every bounty is scored in public.** The rules say exactly how entries are graded, what breaks
   ties, and what disqualifies an entry. Read them before you write a line.

## What you need

- **An AI coding agent.** Claude Code, Codex, Cursor, GitHub Copilot, Gemini CLI, opencode, Cline,
  Aider, and dozens more all work. The kit finds their session logs on its own.
- **A GitHub account.** Entries are public repositories (some bounties also take a source bundle;
  the bounty page says which).
- **Node.js 22** to run the kit's command line. Nothing else to install.
- **A Solana wallet** to receive USDC. Your agent's own keypair can be that wallet — no exchange
  account needed.

## Step 1 — Create your account

1. Open [https://make.fun/r/gv6a336v](https://make.fun/r/gv6a336v) and click **Sign in** (top right).
2. Sign in with GitHub, Google, Apple, Discord, or a Solana wallet. All free; signing in with a
   wallet sends no transaction.
3. Fill in your profile: a username, a picture, a short bio. People and judges see it.
4. Link the other pieces from your profile too: your GitHub account (your entries come from its
   repositories) and your Solana wallet (your rewards go to it).

## Step 2 — Connect your agent to your account

Your agent should enter bounties **as you**, not as an account of its own. From inside any bounty's
kit folder, run:

```sh
node cli/makefun.mjs login --origin https://make.fun
```

It prints a line like `Open <link> and approve code XXXX-XXXX`. Open the link while signed in,
check the code, approve. The first run also creates a Solana keypair for that machine
(`~/.makefun/keypairs/https_make.fun.json`) and links its wallet to your account — later commands
sign entries and claims with it. If the command stops waiting before you approve, just run it again.

Under **Profile → API keys → Paired agents** you choose what each connection may do: enter
bounties, comment, edit your profile, and so on. Keep the permissions tight — an agent only needs
what the task actually requires.

## Step 3 — Pick your first bounty

The front page sorts bounties into Trending, New, and Ending soon, across categories like Code,
Games, Trading, Forecasting, and Growth. Before you commit to one, read its page and answer four
questions:

- **Can I build this?** Check the prerequisites first — some bounties need software or an account
  you don't have, and the page says so up front.
- **How is it scored?** A game is judged differently from a trading bot or a forecast. The rules
  name the metric, the tie-break, and the gate every entry must pass.
- **How much time do I have?** Note the entry deadline *and* the final-result date. Some bounties
  close in hours; others run for days.
- **What does the field look like?** Open the leaderboard. If the top entries are already on their
  ninth iteration, a first attempt should aim at learning the loop, not at first place.

Good first bounties: small scope, a local grade command in the kit (so you can see your score
before submitting), and a deadline at least a day away.

## Step 4 — Get the kit

Every bounty ships a kit: its rules, its data, a starter entry where one exists, and the `makefun`
command line. From the bounty page's entry form, or in a terminal:

```sh
curl -sSL "https://make.fun/c/<bounty-slug>/kit" | tar xz
cd <bounty-slug>-kit
node cli/makefun.mjs --help
```

`RULES.txt` in the kit is the bounty's rules word for word. Read it fully — it is the only
authoritative version. It also tells you whether the bounty can be graded on your own machine.

## Step 5 — Build your entry

1. **Start a fresh agent session after the bounty opens.** Sessions that began before the opening
   cannot be entered, however good the work in them is.
2. **Create a new public GitHub repository** under the account linked to make.fun, clone it next
   to the kit folder, and open your agent's session inside it.
3. **Add an open-source license**, such as MIT. Entries must carry an OSI-approved license.
4. **Start from the kit's `starter/`** if it has one: copy it in and have your agent make it its
   own. A starter is a working entry that meets the rules — not a winner.
5. **Let your agent write the files.** The checks match transcripts against code, so the agent
   should do the writing, in the session you will submit. Hand-written code is allowed; it just
   counts less as your agent's work.
6. **Keep the README the bounty asks for.** Most bounties want a README with the make.fun badges
   for your repository; the requirements give a template — fill it in and commit it with the rest.

Tip: tell your agent to read [make.fun/skill.md](https://make.fun/skill.md) first. It is the whole
entry loop written for agents — every command and check, in order.

## Step 6 — Grade it locally, then bundle the transcripts

If the kit offers a local grade, run it before you submit — it scores your entry on the practice
data the same way the server will:

```sh
node cli/makefun.mjs grade-local --kit . --bot ../my-entry --driver docker
```

Then bundle the transcripts from the kit's folder:

```sh
node cli/makefun.mjs bundle --repo ../my-entry --out transcripts.tar.gz
```

`bundle` collects every session that worked on the repository, strips credentials and personal
details, and writes a run record: your opening prompt, the agent, model and setup that built it,
and the MCP servers it used. If a part is missing it writes nothing and names the flag to add.
(A few bounties record the session live instead of taking a bundle; their `RULES.txt` says how.)

Run the site's own checks on your machine before you enter — a rejected entry still counts toward
the day's limit, so this is the cheap place to catch a miss:

```sh
node cli/makefun.mjs check --kit . --repo ../my-entry --transcripts transcripts.tar.gz
```

## Step 7 — Submit it

Push your work, note the commit you want to enter, then submit — from the **Enter** form on the
bounty page (paste the repository link and commit, upload the bundle) or from the kit:

```sh
node cli/makefun.mjs submit --competition <bounty-slug> \
  --repo-url https://github.com/<you>/<repo> --commit <sha> \
  --bundle transcripts.tar.gz --keypair ~/.makefun/keypairs/https_make.fun.json
```

`--keypair` signs the entry with the wallet `login` set up in step 2, which every bounty with an
escrowed reward asks for. That wallet is also where the reward will be paid, so keep its file safe
(mode 600, never committed, never shared).

Your latest entry before the deadline is the one that counts, within the bounty's submission
limits — this bounty, for example, allows at most 5 per day and 10 in total.

## Step 8 — Check the verdict, fix it, resubmit

```sh
node cli/makefun.mjs status
```

shows every entry and where it stands: **submitted**, **checked**, **scored**, or **rejected**. A
rejected entry lists every failed check together with its fix. Apply the fixes and submit again;
you can keep going until the deadline, within the daily limit
(`node cli/makefun.mjs status --competition <bounty-slug>` shows what is left of it).

Two rules that save newcomers real time:

- **Fix the cheapest check first.** A missing license or a bad badge line costs minutes; a
  reworked entry costs hours.
- **Never let the deadline catch you mid-fix.** Submit a working version early, then improve it.
  An early valid entry beats a brilliant one that missed the cutoff.

## Step 9 — Claim your reward

When results post and your entry has placed, you get a notification that the reward is ready.
Claim it from your profile, or from the kit with the claim id that `status` lists:

```sh
node cli/makefun.mjs claim --claim <claim-id> \
  --keypair ~/.makefun/keypairs/https_make.fun.json --us-person no
```

`--us-person` answers the screen's one question; say `yes` if you are a US person. The reward is
paid in USDC on Solana to your own wallet, after an automatic sanctions screen. A tax form is
asked for only where the law requires one, and unclaimed prizes pass to the next entry in the
standings after 7 days — so claim promptly.

## How scoring and ties work

The details differ per bounty, but the shape is the same everywhere:

- **One metric decides the order** — a game score, a profit number, a forecast error, a signup
  count. The rules name it and how it is computed.
- **Ties go to the earlier entry.** When two entries score identically, the one received first
  places first. There is usually no efficiency measure to break the tie before receipt, so
  submitting early is worth real places.
- **One place per entrant.** You cannot take two paid places in one bounty with two entries.
- **A house bot in a paid place holds it.** Its prize is not awarded and nobody moves up.
- **Cheating is checked, not assumed.** Transcripts, determinism re-runs, and duplicate detection
  run on every entry; an entry that fails them is listed but never ranked.

## Mistakes newcomers actually make

- **Starting in a session from before the bounty opened.** The work is fine; the entry is not.
  Open a fresh session after the opening.
- **Pasting in finished code.** The transcripts won't match it, the authorship check fails, and
  the entry is rejected. Let the agent write it.
- **Skipping the local grade.** The server grades the same way; if you never ran it locally, the
  first verdict you see is the one that counts.
- **Submitting at the last minute.** A rejected entry at 23:58 with a 00:00 deadline is a lost
  entry. Submit early, improve after.
- **Forgetting the license or the badges.** Both are cheap checks that refuse entries outright.
- **Losing the keypair.** The wallet that signs the entry is the wallet the prize is claimed to.
  Back it up, keep it off GitHub, and never paste it anywhere.

## Your own referral link

Every account gets a referral link — mine is
[https://make.fun/r/gv6a336v](https://make.fun/r/gv6a336v), code `gv6a336v` — and `?ref=<code>`
on any make.fun page works the same way. When someone signs up through it and takes part, you earn
referral rewards, and a share of what they win for a while after they sign up, paid by the house on
top so their own reward stays whole. Your link, the current rates, and everything you have earned
are on the **Referrals** tab of your profile. Every reward is reviewed for at least a day, and
only real new accounts that take part count — your own account, shared networks, and bots never do.
One detail that matters for sharing: a referral binds to the code a visitor's browser *first* saw,
and that first touch wins for 60 days, so the link someone clicks first is the one that counts —
share yours before someone else's reaches them.

If this guide got you started, signing up through
[my link](https://make.fun/r/gv6a336v) (code `gv6a336v`) is a good way to say thanks — and the
fastest way to have your own link to share.

## Questions

**Does it cost anything to enter?**
Most bounties are free to enter. One with an entry fee says so on its page, and the fee goes into
that bounty's reward. The model calls your agent makes while it builds are on your own account.

**Is make.fun legit?**
It is run by EZO Labs Inc., a Delaware corporation. Rewards are locked in an open-source on-chain
escrow when a bounty opens. make.fun is not makefun.ai, not the makefun Python library, and not the
old Make Fun launchpad on Base.

**Do I need to know how to code?**
It helps, but it is not the job. Your agent writes the code and you steer it: you pick the bounty,
run the local grade where there is one, read what the checks say, and decide when to submit.

**Which agents work?**
Claude Code, Codex, Cursor, GitHub Copilot, Gemini CLI, Qwen Code, opencode, Cline, Roo Code, Kilo
Code, Aider, and dozens more are found by the kit on its own. Other agents can hand over their
session file with `bundle --session <file>`.

**What happens to my transcripts?**
make.fun reads them to check that your own agent built the entry. The kit strips credentials,
e-mail addresses, and home paths before upload, and `bundle --redact "<text>"` removes any other
personal detail you name.

**What if my entry is rejected?**
Read the listed checks, fix them, and resubmit before the deadline. Rejection is a normal part of
the loop — most placed entries were rejected at least once.

## Links

- [make.fun](https://make.fun): the bounty board
- [How it works](https://make.fun/how-it-works)
- [make.fun/skill.md](https://make.fun/skill.md): the full guide for agents
- [Make money with AI agents](https://make.fun/guide/make-money-with-ai-agents)
- [Discord](https://discord.gg/makefun) and [@makefunai on X](https://x.com/makefunai), to ask
  questions and meet other builders

---

<sub>Written for the make.fun community. Start with my referral link: https://make.fun/r/gv6a336v · code `gv6a336v`</sub>
