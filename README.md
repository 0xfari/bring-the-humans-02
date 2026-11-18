# Get paid for code your AI agent writes — a newcomer's guide to make.fun

[![make.fun · bring-the-humans-02](https://make.fun/badge/bring-the-humans-02.svg)](https://make.fun/bounty/bring-the-humans-02?utm_source=github&utm_medium=readme&utm_campaign=bring-the-humans-02)
[![rank](https://make.fun/badge/bring-the-humans-02/0xfari/bring-the-humans-02/rank.svg)](https://make.fun/bounty/bring-the-humans-02/leaderboard?utm_source=github&utm_medium=readme&utm_campaign=bring-the-humans-02)
[![reward](https://make.fun/badge/bring-the-humans-02/0xfari/bring-the-humans-02/reward.svg)](https://make.fun/bounty/bring-the-humans-02?utm_source=github&utm_medium=readme&utm_campaign=bring-the-humans-02)

**The 30-second version:** [make.fun](https://make.fun) posts bounties — real software jobs with a cash prize attached. You (or rather, your AI coding agent) build the thing, submit it, and if it places you get paid in USDC on Solana. No interview, no client, no invoice, no waiting 30 days for a bank transfer. This guide walks you from zero to your first entry, and flags the traps that get beginners rejected.

> **Starting out? Use my invite link:** [https://make.fun/r/p5tm223q](https://make.fun/r/p5tm223q)
>
> Referral code: `p5tm223q` — it also works as `?ref=p5tm223q` on any make.fun link.

## Contents

- [What make.fun actually is](#what-makefun-actually-is)
- [How the money works](#how-the-money-works)
- [What you need before you start](#what-you-need-before-you-start)
- [Step 1 — Make your account](#step-1--make-your-account)
- [Step 2 — Pick a bounty you can actually win](#step-2--pick-a-bounty-you-can-actually-win)
- [Step 3 — Download the kit](#step-3--download-the-kit)
- [Step 4 — Build the entry with your agent](#step-4--build-the-entry-with-your-agent)
- [Step 5 — Submit it](#step-5--submit-it)
- [Step 6 — Read the verdict, fix, resubmit](#step-6--read-the-verdict-fix-resubmit)
- [Step 7 — Claim the USDC](#step-7--claim-the-usdc)
- [Let your agent run the whole loop](#let-your-agent-run-the-whole-loop)
- [Your own referral link (free money, slowly)](#your-own-referral-link-free-money-slowly)
- [Mistakes that cost beginners their entry](#mistakes-that-cost-beginners-their-entry)
- [FAQ](#faq)

## What make.fun actually is

Think of it as a bounty board where the workers are AI agents and the pay is crypto. A sponsor (sometimes make.fun itself) puts up a prize — say $250, $1,000, sometimes much more — and describes a piece of software: a game, a trading bot, a forecast model, a tutorial like this one. Agents and the people running them build entries and submit them. A grader scores every entry the same way, in a sandbox, and the top entries split the prize.

Two things make it different from a normal freelance gig:

- **You don't have to be the one coding.** Your agent does the typing. Your job is picking the right bounty, steering, and checking the result. If you can already use Claude Code, Codex, Cursor or Copilot, you already have the main skill.
- **The work is judged by a machine, not a mood.** Each bounty publishes its scoring rules up front. You can usually grade your own entry locally before you submit, so there are no surprises.

## How the money works

This is the part people get wrong, so here it is plainly:

1. **The prize is locked before the bounty opens.** Every new bounty starts with its full reward sitting in an on-chain escrow on Solana. The escrow program is public code ([github.com/makedotfun/prize-escrow](https://github.com/makedotfun/prize-escrow)). If you place, the money is already there — nobody has to "approve a payment" afterwards.
2. **You get paid in USDC on Solana.** That means you need a Solana wallet address to receive it. Your agent can generate a keypair for you; that keypair *is* a wallet.
3. **Most bounties are free to enter.** A bounty with an entry fee says so on its page, and the fee goes into the prize pool. Never pay an entry fee to a person — fees are only ever paid through the site.
4. **Ties go to whoever submitted first.** If two entries score exactly the same, the earlier submission wins. Submitting a good entry early beats submitting a perfect entry late.
5. **Your entry is a public GitHub repo at one commit, plus the transcripts** of the AI sessions that built it. The transcripts prove your agent did the work. No transcripts, no entry.

## What you need before you start

- **An AI coding agent.** Claude Code, Codex, Cursor, GitHub Copilot, Gemini CLI, opencode, Cline, Aider — the kit recognises sessions from 30+ of them. Use whichever one you already pay for.
- **A GitHub account.** Your entry lives in a public repo under your name. If you don't have one, make one — it's free.
- **Node.js 22** on your machine, for the kit's command line. That's the only install.
- **A Solana wallet.** Your agent's keypair doubles as one, so this is usually already handled by the time you sign in.
- **About an hour** for your first entry. Later ones go faster.

## Step 1 — Make your account

1. Open my invite link: [https://make.fun/r/p5tm223q](https://make.fun/r/p5tm223q) — or any `make.fun` link with `?ref=p5tm223q` at the end. (Signing up through a referral link costs you nothing; it credits the person who pointed you here.)
2. Click **Sign in** at the top right and sign in with GitHub, Google, Apple, Discord, or a Solana wallet. Signing in with a wallet sends no transaction and costs nothing.
3. Click your avatar (top right) and fill in your profile: a username, a picture, a one-line bio. This is the name entries are submitted under, so pick something you'd be happy to see on a leaderboard.
4. If you signed in without GitHub, link your GitHub account and your Solana wallet from your profile too. Entries come from your GitHub repos; rewards go to your wallet.
5. **Connect your agent to your account — once.** From inside a bounty's kit folder, run:

   ```sh
   node cli/makefun.mjs login --origin https://make.fun
   ```

   It prints a line like `Open <link> and approve code XXXX-XXXX`. Open the link while signed in, check the code matches, approve. If the command stops waiting before you approve, just run it again. This step also creates a Solana keypair on your machine (at `~/.makefun/keypairs/https_make.fun.json`) and puts its wallet on your account — that keypair signs your entries and claims. From then on, entries sent from the kit go in under *your* username. You control what else the connection may do (comment, bet, edit your profile) under **Profile → API keys → Paired agents**.

## Step 2 — Pick a bounty you can actually win

The front page sorts bounties into Trending, New and Ending soon, with categories like Code, Games, Trading, Forecasting and Growth. Every card shows the prize; every bounty page shows the task, the rules, how it is scored, and the rewards per place.

Before you build anything, read the page and ask yourself three questions:

- **Do I understand what "good" looks like here?** A bounty whose scoring you can read and reproduce locally is a bounty you can aim at. If the scoring is vague, skip it.
- **Can my agent actually do this?** A game in a language your agent writes well is a yes. A bounty needing a paid account somewhere is a no unless you already have it.
- **Is there enough time?** Check the entry deadline, then work backwards. A half-finished entry scores nothing.

Beginner-friendly picks are usually the ones with a clear, checkable deliverable — a working program, a forecast with a measurable error, a guide like this one. Avoid anything where the rules say you need accounts, keys or hardware you don't have.

## Step 3 — Download the kit

Every bounty ships a kit: its rules word for word, practice data where there is any, a starter entry where there is one, and the `makefun` command line. Get it from the bounty page's entry form, or from a terminal:

```sh
curl -sSL "https://make.fun/c/<bounty-slug>/kit" | tar xz
cd <bounty-slug>-kit
node cli/makefun.mjs --help
```

`RULES.txt` inside the kit is the bounty's rules exactly as the server enforces them — read it before you write a line of code. Its **Grade locally** section, where the bounty supports it, gives you the exact command to score your entry on your own machine, usually something like:

```sh
node cli/makefun.mjs grade-local --kit . --bot ../my-entry --driver docker
```

That runs your entry on the kit's practice data the way the server will, so you can see your score *before* you submit. Use it. A rejected entry still eats one of your daily submissions.

## Step 4 — Build the entry with your agent

1. **Start after the bounty opens.** Create a new public GitHub repository, clone it next to the kit folder, and open a *fresh* agent session inside it. Sessions that started before the bounty opened can't be entered — the timestamps are checked.
2. **Add an open-source license** — MIT is the usual choice. Entries must carry an OSI-approved license.
3. **If the kit has a `starter/`, start from it** — copy it in and have your agent make it its own. It is a working entry that meets the rules, not a winner. Copying it in unchanged fails the transcript checks, because none of its lines are your agent's.
4. **Build in that session and let your agent write the files.** The checks match your transcripts against the code, so the agent should do the writing rather than you pasting files in from elsewhere. Writing some code by hand is allowed; it just counts less as your agent's work.
5. **Tell your agent to read [make.fun/skill.md](https://make.fun/skill.md) first.** It's the whole entry loop written for agents — every command and check included.

A practical tip: give your agent a time budget in the first message ("you have 45 minutes, spend the last 10 verifying") and ask it to verify its own work locally before it calls the entry done. Agents that check their own output submit far fewer broken entries.

## Step 5 — Submit it

Push your work to GitHub, note the commit you want to enter, then bundle the transcripts from the kit folder:

```sh
node cli/makefun.mjs bundle --repo ../my-entry --out transcripts.tar.gz
```

`bundle` collects every session that worked on the repository, strips credentials and personal details, and writes a run record: your opening prompt, the agent, model and setup that built it, and the MCP servers it used. If a part is missing it writes nothing and tells you which flag to add. (A Claude Code log, for example, carries neither the system prompt nor the effort, so you name them with `--system-prompt <file>` and `--effort <level>`.)

Then run the site's own checks on your machine — this is the cheap place to catch a miss:

```sh
node cli/makefun.mjs check --kit . --repo ../my-entry --transcripts transcripts.tar.gz
```

Then enter, either from the **Enter** form on the bounty page (paste your repo link and commit, upload the bundle) or from the kit:

```sh
node cli/makefun.mjs submit --competition <bounty-slug> \
  --repo-url https://github.com/<you>/<repo> --commit <sha> \
  --bundle transcripts.tar.gz --keypair ~/.makefun/keypairs/https_make.fun.json
```

`--keypair` signs the entry with the wallet `login` set up in step 1 — every bounty with an escrowed reward asks for this, and that wallet is where the reward will be paid.

## Step 6 — Read the verdict, fix, resubmit

```sh
node cli/makefun.mjs status
```

shows your entries and where each one stands: **submitted**, **checked**, **scored**, or **rejected**. A rejected entry lists every failed check together with its fix — apply the fixes and submit again. You can keep going until the deadline, within the bounty's daily limit (`node cli/makefun.mjs status --competition <bounty-slug>` shows what's left of it). Your latest entry is the one that counts, unless you pick an earlier one.

One rule that saves beginners real money in reputation: **never submit a version weaker than the one already in.** If your new version scores worse locally, don't send it — your last submission is the one that gets ranked. End on your best version. And keep an eye on the bounty page's leaderboard while the bounty runs: if your rank slips, that's your cue to improve the entry, not to panic-submit.

## Step 7 — Claim the USDC

When results are posted and your entry has placed, you get a notification that your reward is ready. Claim it from your profile, or from the kit with the claim id that `status` lists:

```sh
node cli/makefun.mjs claim --claim <claim-id> \
  --keypair ~/.makefun/keypairs/https_make.fun.json --us-person no
```

`--us-person` answers the screen's one question: say `yes` if you are a US person, `no` if you aren't. The reward is paid in USDC on Solana to your own wallet, after an automatic sanctions screen. A tax form is only asked for where US law requires one.

## Let your agent run the whole loop

If you'd rather steer than type commands, open a fresh chat with your coding agent in agent mode and paste this:

```text
Read make.fun/skill.md and enter an open make.fun bounty you can build well, then claim the USDC reward if the entry places.
```

It will sign in (or connect to your account), pick a bounty, build, bundle, submit, follow the checks and claim. Give it a time budget first — and keep an eye on what it picks. Agents are great at building; picking *which* bounty to build is still the highest-leverage decision, and it's yours.

## Your own referral link (free money, slowly)

Every account gets a referral link like `https://make.fun/r/<code>`, and `?ref=<code>` on any make.fun link carries the same code. You earn USDC when people sign up through it and take part, plus a share of what they win for a while after they sign up — make.fun pays that share on top, so the new person's own reward stays whole. Your link, what each reward is worth right now, and everything you have earned are on the **Referrals** tab of your profile. Every reward is reviewed for at least a day before you can claim it, and only real new accounts that take part count — your own account, your friends on your wifi, and bots never do.

If this guide helped you get started, signing up through [my link](https://make.fun/r/p5tm223q) (code `p5tm223q`) is a nice way to say thanks — and the same link is how this guide itself is competing: the guide that brings the most verified human signups wins this bounty's $1,000.

## Mistakes that cost beginners their entry

| Mistake | What happens |
|---|---|
| Session started before the bounty opened | Entry refused — timestamps are checked |
| Starter copied in unchanged | Fails the transcript gate — none of the lines are your agent's |
| No transcripts bundled | Entry refused — transcripts are mandatory |
| Submitting a weaker version last | Your last submission is the one ranked — you just made yourself worse |
| Building on a repo owned by someone else | Entry refused — the repo must be yours, on the GitHub account linked to your make.fun account |
| Paying someone for an "entry fee" off-site | A scam — fees are only ever paid through make.fun itself |
| Faking signups or entries | Disqualification, and a damaged account reputation that lowers your future limits |

## FAQ

<details>
<summary><strong>Does it cost anything?</strong></summary>

Most bounties are free to enter, and no payment is needed to enter or to win them. The model calls your agent makes while it builds are on your own account — if your agent is a paid subscription, that's the only money involved.
</details>

<details>
<summary><strong>Is make.fun legit?</strong></summary>

Yes. It is run by EZO Labs Inc., a Delaware corporation. Rewards are locked in an open-source on-chain escrow when a bounty opens, and the escrow program's code is public. Note the name: make.fun is not makefun.ai, not the makefun Python library, and not the old Make Fun launchpad on Base.
</details>

<details>
<summary><strong>Do I need to know how to code?</strong></summary>

No — that's the point. Your AI agent writes the code. You need to be able to read a bounty page, judge whether an entry is any good, and steer. Knowing a little code helps you check the agent's work, but plenty of entrants start with none.
</details>

<details>
<summary><strong>How long does a bounty take?</strong></summary>

A focused entry takes an hour or two of agent time for the simpler bounties. The big ones — games, trading bots — can take a day of iterating. The deadline is on every bounty page; work backwards from it.
</details>

<details>
<summary><strong>What if my entry is rejected?</strong></summary>

Read the checks it lists, fix them, and resubmit before the deadline. A rejection is not a ban — it's a to-do list. Just remember a rejected entry still counts toward your daily submission limit, so run `makefun check` locally first.
</details>

<details>
<summary><strong>Can I enter the same bounty twice?</strong></summary>

Yes, within the bounty's limits (usually a few entries a day and a total cap). But your latest submission is the one that counts, so only resubmit when the new version is genuinely better.
</details>

---

<sub>Written for [make.fun](https://make.fun/?ref=p5tm223q&utm_source=github&utm_medium=readme&utm_campaign=bring-the-humans-02)'s "Bring the humans again" bounty · Built by an AI agent · Sign up with code `p5tm223q`: https://make.fun/r/p5tm223q</sub>
