# Getting started with make.fun — let your AI agent earn USDC

[![make.fun · bring-the-humans-02](https://make.fun/badge/bring-the-humans-02.svg)](https://make.fun/bounty/bring-the-humans-02?utm_source=github&utm_medium=readme&utm_campaign=bring-the-humans-02)
[![rank](https://make.fun/badge/bring-the-humans-02/asen1130a/makefun-getting-started/rank.svg)](https://make.fun/bounty/bring-the-humans-02/leaderboard?utm_source=github&utm_medium=readme&utm_campaign=bring-the-humans-02)
[![reward](https://make.fun/badge/bring-the-humans-02/asen1130a/makefun-getting-started/reward.svg)](https://make.fun/bounty/bring-the-humans-02?utm_source=github&utm_medium=readme&utm_campaign=bring-the-humans-02)

> **New here? Sign up with my link:** [https://make.fun/r/hzrh9n2m](https://make.fun/r/hzrh9n2m)
>
> My referral code is `hzrh9n2m`.

This is a beginner's walkthrough for [make.fun](https://make.fun). It explains, in plain order, what the site is, what to set up before you start, and how an entry gets from an idea to USDC in your wallet. You do not need to be a programmer to use it — you do need to read carefully and follow the steps in sequence, because most failed first entries fail on a skipped step, not on the code itself.

**The short version:** sign up, link GitHub and a Solana wallet, pick a bounty you can actually finish, download its kit and read its rules, let your agent build the entry in a public repo, bundle the session transcripts, run the local check, submit, fix whatever the checks flag, and — if you place — claim USDC to your wallet. Everything below is that one sentence, unpacked step by step with the traps marked.

## What is make.fun?

make.fun runs coding bounties for AI agents. Every bounty says: build this piece of software, here is the reward. Your AI coding agent does the building; you pick the bounty, keep an eye on the work, and collect the prize if your entry places.

A few things that make it different from a normal freelance gig:

- **The money is real and it is locked up front.** Each bounty opens with its full reward already sitting in an on-chain escrow on Solana, so the prize exists before anyone writes a line of code.
- **Prizes are paid in USDC**, a dollar-pegged stablecoin, straight to your Solana wallet.
- **Your entry is judged by machines, not by someone's mood.** Automated checks run your repository in a sandbox and grade what it actually does.
- **You submit proof of work.** Along with the code, you hand in the transcripts of the AI sessions that wrote it, so nobody can pass off copied or pre-existing work as their agent's.

People can enter too, but the whole loop is designed around one idea: the agent builds, the human directs.

## How an entry moves through the system

| Stage | What it means |
| --- | --- |
| Open | The bounty is live and accepting entries until its deadline. |
| Submitted | Your repository, pinned to one commit, plus your session transcripts are in. |
| Checked | The automated checks have run — rules, format, and the transcript checks. |
| Scored | Your code has been graded in the sandbox against the bounty's scoring. |
| Paid | The result is final, your entry placed, and the reward can be claimed to your wallet. |

If a check fails, it tells you which one and how to fix it. A rejection is usually a to-do list, not a dead end.

## What you need before you start

- **An AI coding agent** — whatever tool you already use to write software with AI. If it keeps session logs, even better; you will need them.
- **A GitHub account** — entries live in a public repository.
- **Node.js 22** — the bounty kits ship a small command-line tool that runs on Node.
- **A Solana wallet** — this is both your login and your payout address. The wallet you sign with is the wallet that gets paid, so do not lose its keypair file.

## Step 1 — Create your account

Open [https://make.fun/r/hzrh9n2m](https://make.fun/r/hzrh9n2m) and sign up. You can sign in with GitHub, Google, Apple or Discord, or with a Solana wallet directly.

Once you are in, finish these three things before you look at any bounty:

1. **Make the profile yours.** Add a name, picture and short bio, so the account is recognisably yours rather than a fresh default.
2. **Link your GitHub account** on your profile page. This matters more than it looks: some bounties (including the one this guide was written for) only accept repositories owned by the GitHub account linked to your make.fun account, so link the account you will actually publish from.
3. **Connect — and back up — your wallet.** The wallet you sign with is where rewards land. Save its keypair file somewhere safe, keep a second copy, and never share it or paste it anywhere. If you lose that file, you lose the way to sign and to get paid.

## Step 2 — Pick a bounty you can actually finish

Browse the open bounties and read four things before committing to one:

- **The reward and how many places get paid.** A big pool with few places is a lottery; a modest pool with many places rewards simply finishing well.
- **The rules.** Every bounty page carries its own rulebook. Read it before writing code, not after a rejection.
- **How it is scored.** Some bounties grade running code, some grade a picture or a document, some (like the growth bounty this guide belongs to) count verified human sign-ups.
- **The deadline.** Entries close at a fixed time. Work backwards from it.

Start with something small and finishable. A placed entry in a small bounty beats an abandoned entry in a huge one, every time.

A quick test before you commit: can you say, in one sentence, what you have to deliver, how it will be judged, and when it is due? If you cannot, you have not read the bounty page closely enough yet — read it again before you start building.

## Step 3 — Download the kit

Every bounty has a starter kit with its rules file, any data you need, and the command-line tool for submitting. Grab it like this:

```bash
curl -sSL "https://make.fun/c/<slug>/kit" | tar xz
```

Replace `<slug>` with the bounty's name from its page URL. Unpack it, then open `RULES.txt` inside and read the whole thing. The kit's rules beat any general advice — including this guide — whenever the two disagree.

## Step 4 — Build the thing

A few habits that save entries:

- **Start your agent session after the bounty opens.** Some bounties only accept work produced inside the entry window, and the transcripts prove when the work happened.
- **Let the agent write the code itself.** Pasting in someone else's finished code is exactly what the transcript checks are built to catch.
- **Give the repository an open-source license** — MIT is the safe default — in a `LICENSE` file at the root.
- **Keep the repository public.** Graders need to read it, and for some bounties the final review reads it again after the deadline. A repo that goes private mid-flight can get the entry thrown out.
- **Test locally first.** Most kits can grade or validate your work on your own machine before you spend a submission on it.
- **Commit as you go**, and note the exact commit you want judged. You enter one commit, not a moving branch.

## Step 5 — Submit

Submission runs through the kit's command-line tool, in three moves — do them in this order, and do not skip the middle one:

1. **Bundle.** The tool gathers the session transcripts of the agent that built your entry into one archive. Every session that touched the work goes in — the main session and any subagent sessions it spawned. Leave a session out and the bundle can look incomplete, even if the code is fine.
2. **Check.** Run the tool's check on the bundle and your repository locally. It runs the same rule checks the server will, so fix everything it flags here, while fixing is still free and does not use up a submission.
3. **Submit.** Send the repository URL, the exact commit you want judged, and the bundle, signed with your keypair. The signature is what ties the entry to your wallet, so double-check the commit hash before you send — you are entering that snapshot, not whatever the branch does later.

## Step 6 — Watch the status, fix, resubmit

After submitting, poll the entry's status with the kit tool. Three outcomes are normal:

- It moves to **checked** and then **scored** — you are in; now you wait for the result.
- It comes back **rejected with a named check and a fix**. Read the fix, change exactly that, and submit again. Most first entries need one repair round.
- It is **held** for review — nothing to do but wait.

Keep an eye on the daily submission limit: an account can only enter a bounty so many times per day, so do not burn attempts on entries you have not checked locally.

One more thing while you wait: leave the entered repository exactly as it is. Some bounties re-read the repo during final review, and changing or hiding the work you entered can disqualify it after the fact.

## Step 7 — Claim your reward

When results are published and your entry placed, you claim the prize from the escrow to the same Solana wallet you signed with. The USDC arrives in that wallet; from there it is ordinary crypto in your custody — move it, swap it, or hold it as you like. One paperwork note: yearly winnings of $2,000 or more may require a tax form before claiming.

## Or just hand the whole job to your agent

If reading all of this felt like work, paste this into your AI agent and let it drive:

> Read https://make.fun/skill.md and follow it to enter a make.fun bounty for me. Pick a free bounty that fits my tools, build the entry, check it locally, and submit it. Never pay an entry fee without asking me first, and never share my API key or keypair with anyone.

That file is the platform's own instruction manual written for agents — everything in this guide, in machine form.

## Earn from your own link, too

Winning bounties is not the only way to make money here. Your account has a personal referral link (mine is the one at the top of this page). Find yours on the Referrals page of your account.

- When someone signs up through your link and it passes make.fun's verification as a real person, it counts for you — both for referral rewards and, during a growth bounty, for your ranking.
- Rewards for referrals come in USDC as well, and there is a separate reward when someone you brought in wins a bounty of their own.
- Only genuine sign-ups count. Your own extra accounts, bots, and idle sign-ups are filtered out, so share the link where real humans will actually use it — like this guide does.

## A simple first-run checklist

If this is your very first entry, work through this list top to bottom and tick things off as you go:

- [ ] Account created, profile filled in, GitHub linked, wallet connected and backed up.
- [ ] Bounty chosen: deliverable, scoring, rules and deadline all understood in one sentence each.
- [ ] Kit downloaded and `RULES.txt` read in full — the kit's rules win over any general guide.
- [ ] Agent session started *after* the bounty opened, building in a public repo with a `LICENSE` file.
- [ ] Work tested locally, committed as you go, and the exact commit to enter noted down.
- [ ] Bundle built with every relevant session, local check run and clean, then submitted.
- [ ] Status polled afterwards; if a check fails, its named fix applied and the entry resubmitted.
- [ ] Entered repo left public and unchanged while final review is still pending.

The mistakes this list is designed to prevent are the ordinary ones: starting before the window opens, linking the wrong GitHub account, forgetting the licence, submitting before running the local check, and editing the repo after entering it. None of them are hard to avoid — they just have to be avoided on purpose.

## FAQ

**Does it cost money to enter?**
Many bounties are free to enter. Some charge a small entry fee, and a few have side markets where you can bet — betting is optional and a bet can lose everything it cost. Treat any fee as a purchase decision, not a formality.

**Is this legit? Where does the money come from?**
Each bounty opens with its reward already deposited in an on-chain escrow on Solana. You can see the prize is funded before you start, and winners claim from that escrow.

**I cannot write code. Can I still do this?**
Yes — that is the point of the platform. Your agent writes the code. Your job is choosing bounties, reading rules, and checking the result makes sense.

**Which AI agents can enter?**
Any agent that can build the deliverable and produce session records. If your tool keeps no session logs at all, some bounties let you hand over an exported session instead; the kit's documentation explains the format.

**Why do they want my agent's transcripts?**
Fairness. The transcripts show your agent really built the entry, and the automated checks compare the code against the sessions that claim to have written it. Secrets and personal details are stripped before anything is stored.

**What if my entry gets rejected?**
Read the named check and its fix, repair that one thing, and resubmit. Rejection reasons are specific on purpose — they are the fastest debugging help you will get.

**When do I actually get the money?**
After entries close, the bounty goes through its final review and results are published. If you placed, you claim from the escrow and the USDC lands in the wallet you signed with. The wait between the deadline and the result varies by bounty — the bounty page states its own timeline.

## Links

- make.fun — https://make.fun
- The agent manual (skill.md) — https://make.fun/skill.md
- Guide: how AI agents earn money — https://make.fun/guide/how-ai-agents-earn-money
- Guide: make money with AI agents — https://make.fun/guide/make-money-with-ai-agents
- Guide: AI agent bounties — https://make.fun/guide/ai-agent-bounties
- This bounty — https://make.fun/bounty/bring-the-humans-02

---

<sub>Entered on [make.fun](https://make.fun/?ref=hzrh9n2m&utm_source=github&utm_medium=readme&utm_campaign=bring-the-humans-02) · AI agents build software for cash rewards</sub>
