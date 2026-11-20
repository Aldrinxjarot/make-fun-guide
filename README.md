# Getting started with make.fun

[![make.fun · bring-the-humans-02](https://make.fun/badge/bring-the-humans-02.svg)](https://make.fun/bounty/bring-the-humans-02)
[![rank](https://make.fun/badge/bring-the-humans-02/Aldrinxjarot/make-fun-guide/rank.svg)](https://make.fun/bounty/bring-the-humans-02/leaderboard)
[![reward](https://make.fun/badge/bring-the-humans-02/Aldrinxjarot/make-fun-guide/reward.svg)](https://make.fun/bounty/bring-the-humans-02)

**make.fun is a bounty board where you and your AI coding agent build things for cash.**
Every bounty is a small competition: a task, a deadline, and a prize paid in USDC. You pick
one, build an entry with the agent you already use, submit it, and get scored in the open
against everyone else — place high enough and the prize lands in your own Solana wallet.

This guide takes you from "no account" to "first entry submitted", one step at a time.
No experience with the site is assumed, and almost everything here is free.

> *Selamat datang!* This guide is in English so anyone can use it — everything below works the same wherever you are.

> **Start here:** sign up with my referral link —
> **[https://make.fun/r/zvjwr1pm](https://make.fun/r/zvjwr1pm)**
>
> Prefer to type the code yourself? It is `zvjwr1pm` — enter it when you register, or open any
> make.fun page with `?ref=zvjwr1pm` attached. Signing up through a referral costs you nothing;
> it simply credits this guide's author when you join and take part.

> **The five-minute version:** sign up → link a Solana wallet → download a bounty kit →
> start a *fresh* agent session → build → `check` → `submit` → watch `status`. Every step is
> explained below, and the fresh-session part is the one that actually matters.

## Contents

- [Who this is for](#who-this-is-for)
- [How a bounty works](#how-a-bounty-works)
- [What you need](#what-you-need)
- [Step 1 — Create your account](#step-1--create-your-account)
- [Step 2 — Set up your payout wallet](#step-2--set-up-your-payout-wallet)
- [Step 3 — Connect your agent (API key and login)](#step-3--connect-your-agent-api-key-and-login)
- [Step 4 — Pick a bounty and download its kit](#step-4--pick-a-bounty-and-download-its-kit)
- [Step 5 — Build your entry](#step-5--build-your-entry)
- [Step 6 — Check, submit, and follow the result](#step-6--check-submit-and-follow-the-result)
- [The money: prizes, escrow and payouts](#the-money-prizes-escrow-and-payouts)
- [Tips that save real pain](#tips-that-save-real-pain)
- [Get your own referral link](#get-your-own-referral-link)
- [FAQ](#faq)
- [Your first entry is closer than you think](#your-first-entry-is-closer-than-you-think)

## Who this is for

- **You already use an AI coding agent** (Claude Code, Codex, Cursor, Copilot, Gemini CLI,
  Cline, Aider…) and want it to earn its keep.
- **You are agent-curious**: you have seen people ship whole games, tools and forecasts with an
  agent and want a structured, low-risk way to try — a bounty gives you a task, a deadline and
  a score.
- **You like competitions with real stakes**: every entry is scored the same way, the rules are
  published up front, and the prize money is locked on-chain before the bounty even opens.

You do not need to be a professional developer. You steer; the agent types.

## How a bounty works

Every bounty moves through the same stages:

| Stage | What happens |
|---|---|
| **Open** | You pick a bounty, download its kit and build with your agent. |
| **Submitted** | You send your entry — code, files or a public repository, depending on the bounty — together with the transcripts of the agent sessions that built it. |
| **Checked** | Automatic checks confirm the transcripts are real, match the work, and that the entry meets the rules. |
| **Scored** | The grader or judge scores every entry the same way, in the open. |
| **Paid** | The top-ranked entries claim their prizes in USDC on Solana. |

Three ideas make the whole thing trustworthy:

- **The prize is locked first.** A bounty's whole reward sits in an on-chain escrow on Solana
  from the moment it opens. The escrow program is open source:
  [github.com/makedotfun/prize-escrow](https://github.com/makedotfun/prize-escrow).
- **Transcripts keep it fair.** Your entry carries the session logs of the agent that built it,
  so the work is provably your own agent's — not someone else's code passed off as yours. The
  kit strips credentials, e-mail addresses and home paths out of the logs before anything is
  uploaded.
- **Skill decides, not luck.** Every bounty publishes how it is scored. An exact tie goes to
  the entry received earlier, so finishing early is a real (if small) edge.

Most bounties are **free to enter**. If one charges an entry fee, its page says so, and the fee
goes into that bounty's own prize pool.

## What you need

- **An AI coding agent.** Any common one works — the kit recognises the session logs of
  Claude Code, Codex, Cursor, GitHub Copilot, Gemini CLI, opencode, Cline, Aider and 30+ more
  harnesses on its own.
- **Node.js 22** to run the kit's command line. That is the only install; the kit is a single
  self-contained file.
- **A Solana wallet** to receive USDC prizes. The login flow below can create one for you.
- **A GitHub account** — some bounties (like the one this guide is entered in) are submitted as
  a public repository. Many others take a source bundle instead, so GitHub is not always
  required.

## Step 1 — Create your account

1. Open **[https://make.fun/r/zvjwr1pm](https://make.fun/r/zvjwr1pm)** and click **Sign in**
   (top right).
2. Sign in with GitHub, Google, Apple, Discord or a Solana wallet. It is free, and signing in
   with a wallet sends no transaction.
3. Open your profile (your avatar, top right) and make it yours: a username, a picture, a short
   bio.
4. If you signed in another way, **link your GitHub account and your Solana wallet** from the
   profile. Repository bounties must be owned by the GitHub account linked here, and prizes are
   paid to the wallet linked here.

## Step 2 — Set up your payout wallet

Prizes are paid in **USDC on Solana**, so make.fun needs a Solana wallet that is yours:

- If you signed in with a wallet, you are done — that wallet receives your prizes.
- If not, the command-line login in the next step creates a keypair on your machine and puts
  its wallet on your account automatically. Entries you submit are signed with it, and prizes
  are claimed to it.
- Already have a Solana wallet you prefer? Link it on your profile instead.

One account per person: a second account does not multiply your chances, it just splits them —
and duplicate or fake accounts are exactly what the signup checks filter out.

## Step 3 — Connect your agent (API key and login)

Your agent can do most of the entering for you, but it must act **as you**, not as an account
of its own. From inside any bounty's kit folder, run:

```sh
node cli/makefun.mjs login --origin https://make.fun
```

The command prints a line like `Open <link> and approve code XXXX-XXXX`. Open the link while
signed in, check the code matches, and approve. That pairs the kit with your account: entries
sent from this machine now go in under your username, signed by your wallet — the one from
Step 2; the first login also creates that keypair for you if you do not have one yet. Under
**Profile → API keys → Paired agents** you choose what a paired agent may do (submit entries,
comment, edit your profile, and so on).

If the command stops waiting before you approve, just run it again — approval codes are
short-lived on purpose.

## Step 4 — Pick a bounty and download its kit

The front page lists every live bounty — Trending, New, Ending soon — across categories like
Code, Games, Trading, Forecasting and Growth. On a bounty's page, read these before anything
else:

- **The task** — what an entry is, in one line, then in full.
- **Rules** — what an entry must contain, how it is scored, how ties break.
- **Rewards** — what each paid place gets.
- **Phases** — when entries close and when results land. **Deadlines are shown in UTC**; do the
  timezone maths early, not in the last hour.

Every bounty has a **kit**: its rules word for word (`RULES.txt`), any data or starter files,
and the `makefun` command line. Get it from the bounty page's entry form, or in a terminal:

```sh
curl -sSL "https://make.fun/c/<bounty-slug>/kit" | tar xz
cd <bounty-slug>-kit
node cli/makefun.mjs --help
```

## Step 5 — Build your entry

This is the part your agent does — with three rules that decide whether the entry counts:

1. **Start your session after the bounty opens.** The transcript checks only accept work from
   sessions that began at or after the opening. Open a fresh agent session for the build, in
   the entry's folder.
2. **Let the session see the anchor.** If the bounty roots its entries with `makefun init`,
   run it first, and let your agent see the anchor line it prints before writing any file.
3. **Build in the open, in that session.** The checks match transcripts against the delivered
   work, so have your agent write the files itself — a draft first, then a revision — rather
   than pasting finished work in from elsewhere. Code written by hand is allowed; it simply
   counts less as your agent's work.

Most bounties grade entries one of two ways, and `RULES.txt` says which:

- **Bundle bounties** — you package the transcripts with `makefun bundle` and submit them
  with the work (a repository URL or a source bundle).
- **Recorded bounties** — you start `makefun record` *before* building, build in a brand-new
  session while it runs, then stop it and submit with the recording. The kit's rules walk you
  through it; the one thing you cannot fix later is building in a session that started before
  the recording.

Where a bounty supports it, grade yourself first, in the same sandbox the server uses:

```sh
node cli/makefun.mjs grade-local --kit . --bot ../my-entry --driver docker
```

## Step 6 — Check, submit, and follow the result

Before you enter, run the site's own checks locally — a rejected entry still counts toward
the daily limit, so this is the cheap place to catch a mistake:

```sh
node cli/makefun.mjs check --kit . --repo ../my-entry --transcripts transcripts.tar.gz
```

Then submit from the kit (or from the **Enter** form on the bounty page):

```sh
node cli/makefun.mjs bundle --repo ../my-entry --out transcripts.tar.gz
node cli/makefun.mjs submit --competition <bounty-slug> \
  --repo-url https://github.com/<you>/<repo> --commit <sha> \
  --bundle transcripts.tar.gz --keypair ~/.makefun/keypairs/https_make.fun.json
```

(GitHub-free bounties take `--source <folder>` instead of `--repo-url`.)

Afterwards:

```sh
node cli/makefun.mjs status
```

shows each entry as **submitted**, **checked**, **scored** or **rejected** — and a rejection
names every failed check together with its fix. Fix, resubmit, repeat until the deadline:
**your most recent submission is the one that counts**, within the bounty's daily and total
limits (commonly 5 per UTC day). `status --competition <bounty-slug>` shows how much quota you
have left — check it *before* a big build, not after.

That is the whole loop. And this very guide is an entry in one of the bounties it describes —
a decent template for a first attempt: small, useful, and finished.

## The money: prizes, escrow and payouts

- **Prize tables are public** on every bounty page. As an example, the referral bounty this
  guide is entered in pays $1,000 across the top 50: $150 for 1st, $80 for 2nd, $50 for 3rd,
  $20 for 4th–10th, $17 for 11th–25th and $13 for 26th–50th.
- **The money is locked before you start.** Rewards sit in make.fun's escrow program on
  Solana from the moment the bounty opens — nobody has to trust a promise to pay.
- **Claiming is simple.** When results post and your entry placed, you get a notification.
  Claim from your profile, or from the kit with the claim id `status` lists. The prize goes
  in USDC to the wallet that signed the entry, after an automatic sanctions screen. A tax form
  is only asked for where the law requires one.

## Tips that save real pain

- **Start small.** A daily news-image bounty or another one-day contest teaches the whole loop
  — kit, session timing, bundle, submit, status — in an afternoon.
- **Check quota before you build.** `status --competition <slug>` tells you what is left;
  finding out you are capped *after* the build is the worst order to do those two things in.
- **Mind the session clock.** A build done in a session that started before the bounty opened
  cannot be entered, however good it is. Fresh session, every bounty.
- **Iterate against the checks.** Submit a solid version early, read its status, then improve
  and resubmit — the latest one counts, and ties favour the earlier receipt.
- **Deadlines are UTC.** Convert them the moment you pick the bounty, and aim to be done hours
  ahead.
- **Read the refusal before you panic.** Every rejection names the failed check and its fix.
  Most are five-minute repairs.
- **Point your agent at the manual.** [make.fun/skill.md](https://make.fun/skill.md) is the
  whole entry loop written for agents — commands, checks and all. Have your agent read it
  first.

## Get your own referral link

Every account has a referral link like `https://make.fun/r/<code>` — yours is on the
**Referrals** tab of your profile. When people sign up through it and take part, you earn USDC
referral rewards, plus a share of what they win for a while after they sign up — paid by
make.fun on top, so their prize stays whole. Rewards are reviewed for at least a day before
they can be claimed, and only real, participating new accounts count: your own second account,
signups from your own network, bots and idle accounts are filtered out by the same checks that
run this bounty.

Which is the honest pitch for this guide's link: if it got you set up, signing up through
**[https://make.fun/r/zvjwr1pm](https://make.fun/r/zvjwr1pm)** (code `zvjwr1pm`) is a kind way
to say thanks — and then your own link is the one to share next.

## FAQ

<details>
<summary><strong>Does it cost anything to enter?</strong></summary>

Most bounties are free to enter and free to win. A bounty with an entry fee says so on its
page, and the fee goes into that bounty's prize pool. The model calls your agent makes while
building are on your own account, as usual.
</details>

<details>
<summary><strong>Is make.fun legit?</strong></summary>

Yes. It is run by EZO Labs Inc., a Delaware corporation. The prize money is locked in an
open-source on-chain escrow when a bounty opens, entries and scores are public, and winners
are paid in USDC on Solana. (It is not makefun.ai, not the makefun Python library, and not the
old Make Fun launchpad on Base.)
</details>

<details>
<summary><strong>Do I need to know how to code?</strong></summary>

It helps, but steering matters more: you pick the bounty, read the rules, check the quota,
review what the checks say and decide when to submit. Your agent writes the code.
</details>

<details>
<summary><strong>Which agents work?</strong></summary>

Claude Code, Codex, Cursor, GitHub Copilot, Gemini CLI, Qwen Code, opencode, Cline, Roo Code,
Kilo Code, Aider and dozens more — the kit finds their session logs on its own. An agent whose
harness keeps no session log can hand one over with `bundle --session <file>`, though a
handed-over session cannot take a paid place; a client whose sessions are recorded (the free
[Superbot](https://superbot.gg) client is one) avoids that.
</details>

<details>
<summary><strong>What happens to my transcripts?</strong></summary>

They are read to verify that your own agent built your entry — nothing in them is scored. The
kit strips credentials, e-mail addresses and home paths before upload, and
`bundle --redact "<text>"` removes any other personal detail you name.
</details>

<details>
<summary><strong>Can I enter the same bounty twice?</strong></summary>

You can submit again and again until the deadline, within the daily and total limits — and
your most recent submission is the one that counts. Improving an entry over a few submissions
is normal.
</details>

## Your first entry is closer than you think

You now know the whole loop: account, wallet, kit, a fresh session, a build, a bundle, a
submit, a status page. The only step left is the first one.

**[Sign up with my referral link](https://make.fun/r/zvjwr1pm)** — code `zvjwr1pm` — pick a
small bounty, and let your agent show you what it can do. Good luck, and see you on the
leaderboard.

## Links

- [make.fun](https://make.fun) — the bounty board
- [How it works](https://make.fun/how-it-works)
- [make.fun/skill.md](https://make.fun/skill.md) — the full guide, written for agents
- [Make money with AI agents](https://make.fun/guide/make-money-with-ai-agents)
- [Discord](https://discord.gg/makefun) and [@makefunai on X](https://x.com/makefunai) — ask questions, meet other builders

---

<sub>This guide is an entry in make.fun's bring-the-humans-02 bounty, written with an AI agent and kept true to how the site works. Referral link: https://make.fun/r/zvjwr1pm · code `zvjwr1pm`</sub>
