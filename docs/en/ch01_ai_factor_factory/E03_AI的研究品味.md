---
title: "Lecture 3 · What LLM-Written Factors Look Like: The AI's Research Taste"
---

# Lecture 3 · What LLM-Written Factors Look Like: The AI's Research Taste

> Chapter 1, Lecture 3 (chapter finale)
> Learning objectives: build judgment on the quality of LLM factor hypotheses from real cases; recognize the hallmarks of "pseudo-logic hypotheses"; understand the asymmetry between code quality and logic quality.

## 1. Opening

In the first two lectures we watched the factory through glass: how the loop turns (Lecture 1), how to read the report card (Lecture 2). This lecture opens the door and puts the AI's factors on the dissection table. All material comes from real campaign output (the A-share 290-factor pool, two futures rounds, two crypto rounds).

The chapter's conclusion first, then verified case by case:

> **The AI's code is far more honest than its financial intuition.** Code bugs are explicit — a failure errors out, feedback is immediate; logical hollowness is implicit — however empty the hypothesis, the backtest still spits out a number, and that number then enters the leaderboard and competes in selection.

## 2. Case One: The Decent Ones — But Look Closely at Where the "Decency" Comes From

The factors on the futures panel with genuine industrial logic cluster on the two special data columns supplied by humans: **basis (cash-futures spread)** and **open interest**. For example, a term-structure-based hypothesis: deep discount (distant months far below near months) usually reflects delivery pressure or pessimistic expectations; construct a basis z-score for mean reversion or directional exposure.

These factors deserve credit — but note how they were produced: **the data boundary was drawn by humans**. Humans put `$basis` and `$oi` into the panel, and only then did the AI have material to think in that direction; without those columns, its hypothesis space degenerates to pure price-volume. This pattern recurred across all three campaigns: the "most financially flavored" hypotheses the AI proposed almost always hovered near the special data humans had prepared.

> Conclusion one: the ceiling of the AI's research taste is determined by the quality of the data panel. What it does is "efficient search within a given space of raw material", not "opening up new raw-material space".

## 2.1 A Necessary Negative Footnote: The carry Factor's +18% Was Fake

In the basis/term-structure direction, the factory once produced a carry strategy with a discovery-period annualized **+18%** — the most dazzling number of the entire campaign. A later audit found it was a **double-adjustment bug**: returns were deducted twice at roll-over during panel construction. Recomputed after the fix: **+3.18%, t=0.66, not significant**.

Between a number going from "nearly deployable" to "statistical noise" lies just one convention audit. Lecture 9 expands this story into a full lecture (five pitfalls of the futures panel); here we first set up a tombstone:

> **Before the data conventions have been verified, the most plausible-looking numbers are often the most dangerous.** The +18% nearly fooled everyone precisely because it "looked so reasonable" — term-structure carry is supposed to earn a return, and the bug-amplified number landed within expectations.

## 3. Case Two: The Mediocre Ones — Recognizing Pseudo-Logic

The middle of the leaderboard is full of this type. Represented by `turn_of_month_rank` (turn-of-month effect) and `overlay_reversal_liquidity` (reversal × liquidity overlay) — self-reported excess +26.5% and +14.9%.

Three hallmarks of a pseudo-logic hypothesis, using the reversal × liquidity overlay as the example:

1. **Too many degrees of freedom**: two known phenomena (short-term reversal, liquidity premium) multiplied or intersected, with all parameters (lookback window, filter threshold, quantile boundary) tunable. The larger the parameter space, the easier the backtest finds a good-looking cell.
2. **A good story but a vague mechanism**: "illiquid stocks reverse harder because arbitrage capital can't get in" — sounds plausible, but it equally explains the opposite result ("illiquid stocks have stronger momentum because information diffuses slowly"). **A mechanism that can explain any result is no mechanism at all.**
3. **Many evaluations**: `turn_of_month_rank` with 15 evaluations and 14 versions — the loop touching it repeatedly is itself a signal that "the number was ground out through many attempts" (the combos/versions principle from Lecture 2).

Contrast with a positive example: after two crypto rounds, the real signals confirmed by independent validation were `vol_20d` (volatility) and `reversal_5d` (5-day reversal) — note that these two are **phenomena validated repeatedly in the literature for decades**. The AI loop went around in a big circle, and what survived in the end were still textbook factors. This is no coincidence: textbook factors have passed decades, dozens of markets, and countless researchers' "multiple testing", while the loop's newly minted overlay factors passed only this one leaderboard selection.

> Conclusion two: for novel composite factors generated by an LLM, the default assumption is "products of parameter search"; the burden of proof is on the factor. Classic phenomena tested across markets and eras get a naturally higher prior.

## 4. Case Three: The Crashes — And What Happened After

Failures in the loop come in two kinds, both instructive.

**The error-out kind**: code throws errors (alignment mistakes, missing columns, boundary overflows). The AI handles these well: read the error → locate → auto-fix → rerun. Engineering-wise beyond reproach.

**The silent-crash kind (far more dangerous)**: the code runs, the backtest numbers are perfect, but the logic uses future data (lookahead bias) or mismatched conventions. The factory has **no alarm mechanism whatsoever** for this kind — on the leaderboard it looks identical to a good factor, and only independent validation can expose it. Part of the 136 trials of futures round one that died wholesale under pre-registered validation were of this kind: nothing looked wrong in the factory's convention, but the independent pipeline's recomputation revealed them for what they were.

Hence this lecture's most important asymmetry:

> Code errors: explicit, immediate feedback, the AI can self-fix.
> Logic errors: silent, no feedback, the AI is oblivious, and humans won't know either unless they validate.
> **The loop accelerates the extinction of the first kind of error while accelerating the breeding of the second.**

## 5. Chapter Summary

Combining the three lectures, an honest portrait of the "AI factor factory":

| Dimension | Assessment |
|---|---|
| Code implementation | Strong. High quality, self-fixing, production speed humans cannot match |
| Hypothesis generation | Middling. Efficient search within given data material; re-discovery of classic phenomena is reliable; novel hypotheses are mostly high-degree-of-freedom recombinations |
| Data conventions | Weak. Completely oblivious to problems like double adjustment and benchmark artifacts |
| Result credibility | No built-in mechanism. The leaderboard is a multiple-testing generator; the top names cannot be trusted |
| The real bottleneck | Not "whether the AI can think up factors" but "whether humans can validate" |

290 factors, top self-reported excess +26.5%, zero survivors under independent validation — that is the endpoint of Chapter 1 and the starting point of Chapter 2. The next chapter covers the validation pipeline itself: pre-registration, the DSR threshold, primary/secondary referees — how the "total wipeout" conclusion was reached honestly and reproducibly.

**Discussion question**: If you were to design a mechanism for the loop to automatically filter out high-degree-of-freedom pseudo-logic hypotheses at generation time, which features would you check? (Hints: number of tunable parameters, whether the hypothesis could be falsified by an opposite result, whether it references special data columns)
