---
title: "Extra 1 · The Two Crypto Campaigns: The Triple Persona of a Leaderboard Top"
---

# Extra 1 · The Two Crypto Campaigns: The Triple Persona of a Leaderboard Top

> Extras (independent of the mainline order, but Lectures 2 and 5 are recommended reading first)
> Learning objective: through the complete story of the two crypto campaigns, demonstrate the three faces of "the same number" under three kinds of scrutiny.

## 1. Case overview

The crypto campaign ran two rounds. The first round's leaderboard top: **+10.85%** — a number exciting enough for anyone. The final conclusion: **not robust; the top was a pure baseline**. The real signals confirmed after restarting validation in the second round: `vol_20d` (20-day volatility) and `reversal_5d` (5-day reversal).

The value of this extra lies in this: the number +10.85% never changed from start to finish; what changed was **the lens looking at it**. The same number showed three faces under triple scrutiny.

## 2. The first face: the star on the leaderboard

Looked at in isolation: +10.85%, self-consistent strategy logic, a beautiful backtest curve. This is its most dangerous moment — Lecture 5 said that a human's default logic for checking numbers is "audit the absurd, wave through the plausible", and 10.85% is a "believably restrained" number for crypto (two orders of magnitude below the 100% scams, one order above the boring 2%). A textbook case of the plausibility bias (Lecture 7).

## 3. The second face: a baseline under forensic examination

The first layer of dissection: **the two top factors on the leaderboard (9ebd7fdc / cfa700d4) were identified as pure baselines** — the code audit found their "factor logic" was actually a degenerate form: equivalent to holding the equal-weight benchmark, or applying an uninformative ranking across all instruments. Their +10.85% was not alpha but **the beta of the market itself over that period**.

The teaching point of this layer is "how it was found": not by statistics (statistically it looked great), but by **reading the code**. Auditing the factor-implementation layer is the most easily skipped link of the validation pipeline — everyone assumes "the code that produced the numbers is the code it claims to be". LLM-generated factors need this checkpoint all the more: Lecture 2 noted the versions column holds 33 versions — **each additional version adds a further burden of proof that "the code is still doing what it claims"**.

## 4. The third face: the survivors under the honest convention

Re-validated after stripping the fake top: the only real signals left are `vol_20d` and `reversal_5d`. Lecture 3's conclusion two receives its cleanest empirical proof here: after two full rounds of the loop and hundreds of factors, the two survivors are both **textbook factors** — the volatility effect and short-term reversal are phenomena validated for decades in cross-sectional research.

The corollary deserves its own line: **the reasonable expectation of an AI loop is "efficiently rediscovering the classics", not "inventing novelty"**. If you hired a research assistant and after a year his conclusion was "momentum and reversal also work in crypto" — would you think the year was worth it? In the new world of near-zero hypothesis cost, the answer is yes: he ruled out everything else, and exclusion is itself output (Lecture 5's "compounding of negative results").

## 5. Extra summary

- The three faces of +10.85%: leaderboard star → baseline under code audit → noise after stripping
- The factor-implementation audit (reading the code) cannot be skipped; statistical testing cannot cover "the code doesn't do what it claims"
- The reasonable output expectation of loop mining: rediscover the classics + exclude the rest

**Reflection question**: in what market environment is a baseline masquerading as a factor most likely to reach the top of a leaderboard? (Hint: periods of high equal-weight-benchmark returns — bull markets. Then can "leaderboard tops clustering in a certain period" itself serve as an audit clue?)
