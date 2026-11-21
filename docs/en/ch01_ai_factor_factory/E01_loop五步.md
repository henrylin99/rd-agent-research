---
title: "Lecture 1 · How the AI Factor Factory Runs"
---

# Lecture 1 · How the AI Factor Factory Runs

> Chapter 1, Lecture 1 of "When AI Mines Factors, How Not to Be Fooled — by Yourself or by the AI"
> Learning objectives: understand the five steps of the RD-Agent-style factor-mining loop and the boundary of the human/AI division of labor; be able to read the execution record of a single loop.

## 1. Opening: A Machine That Actually Ran

All the material for this course comes from one real campaign: in September 2026, on a 23-instrument futures panel (2022-12 to 2026-09, roughly 918 trading days), factors were mined automatically with the RD-Agent loop. Round one (13 instruments) produced 136 trials; by the close of the first window of round two, 40 loops had run, producing 200+ workspaces.

The conclusion first — every subsequent lecture of this course argues for it:

> **The AI factor factory replaces the "hands", not the "judgment".** It really can write code for dozens of factors overnight and finish the backtests; but whether the proposed hypotheses hold, and whether the results can be trusted — the judgment at every step remains human. And "whether the results can be trusted" is precisely the step most easily gotten wrong.

## 2. The Five Steps of the Loop

```
构思(gen) → 写码(coding) → 回测(running) → 反馈(feedback) → 记录(record)
     ↑____________________ 记忆在循环间传递 ____________________|
```

**Step one: ideation (direct_exp_gen).** The LLM reads the feedback records of historical factors ("the previous momentum factor failed in the 2024 segment") and proposes a new factor hypothesis: a motivation statement, a draft formula, an expected direction. The input to this step also includes the data panel defined by humans — 23 instruments × 21 columns (OHLC, volume, settlement price, basis, open interest, etc.).

**Step two: coding.** Translate the hypothesis into executable pandas code, compute the factor on the panel, and persist it. This is the most "engineering" step and the one where the LLM is most stable — the code either runs or errors, and the feedback is immediate.

**Step three: backtesting (running).** The factor is sent into the qlib backtest, producing metrics such as excess return and the IC series. Note: the backtest conventions (what the benchmark is, whether shorting is allowed, how costs are computed) are hard-coded in advance by humans in the config — the AI cannot change them. The benchmark for this campaign was the 23-instrument equal-weight index (EQWI-23), with long-short evaluation in a vectorized convention.

**Step four: feedback.** The LLM reads the backtest results and writes "experiment notes": why it worked/failed, what to try next. This is the most interesting step of the loop — the AI writes its own retrospective.

**Step five: record.** Archive to the workspace, to be read by the next round of ideation.

**The key mechanism: memory.** Round N's ideation reads round N-1's feedback, so it is not independent random scattering — it accumulates. But note: **having taken notes ≠ having learned the lesson** — Lecture 3 will show that its "evolution" is largely recombination of known price-volume phenomena.

## 3. What a Single Loop's Execution Record Looks Like

Open the Console's run-records page, pick the 40-loop session from the first window of futures round two, and expand any loop — the five step directories line up in order. Two places worth lingering:

- **The ideation step's output**: a complete factor hypothesis document — "a term-structure-based hypothesis: when the basis is deeply discounted... expected short-direction returns...". Read it aloud and you'll notice: it sounds like a junior researcher's thesis proposal.
- **The feedback step's output**: a self-summary written after reading the backtest numbers — "this factor failed after adding a volatility filter, presumed cause is..., suggest trying... next round".

Flip forward quickly: the ideation content of Loop_15 and Loop_30 clearly responds to earlier feedback. That is memory at work.

## 4. The Factory's Daily Life: Half the Time Fighting Infrastructure

The real execution records also contain plenty of "unglamorous" parts. Right after the second window started, it hit an LLM server-side outage: HTTP 200 but empty responses, intermittently for over 24 hours, eating about half of one window's capacity. The response was engineering-grade: a resumable-run supervisor, 30 retries with backoff, session recovery.

The point of this section is not the specific techniques but expectation management:

> The AI factory in the promo video is a perpetual money printer; the AI factory in the execution records spends half its days erroring and retrying. **The correct unit for evaluating this system is not "how smart it is", but "after deducting failures, how many testable hypotheses it produces per unit cost".**

## 5. Where the Human Stands

| Decision | Owner | This campaign's actual choice |
|---|---|---|
| Data panel (instruments, columns, adjustment method) | Human | 23 instruments, settlement-price-splice adjustment, includes basis/open interest |
| Backtest conventions (benchmark, costs, shortability) | Human | EQWI-23 equal-weight benchmark, vectorized long-short |
| Time budget, when to start/stop | Human | 6-hour windows, supervisor closes them out |
| The factor hypotheses themselves | **AI** | 40 loops × several factors per loop |
| Code implementation | **AI** | Auto-generated, self-debugging |
| **Whether to trust results, how to validate** | **Human** | Independent validation pipeline (the protagonist of Chapter 2) |

Note the last row: it is the hardest cell in the whole table, and the easiest to skip. The factory's built-in backtest will report each factor's excess return — a leaderboard of 290 factors, with the highest self-reported excess at 26%. **Not one of these numbers can be trusted directly.** Why, and how to validate, is Chapter 2's content.

## 6. Lecture Summary

- Five-step loop: ideation → coding → backtest → feedback → record, with memory carried across loops
- The AI's strength is coding (immediate feedback, clear right/wrong); its weakness is the financial logic of hypotheses (expanded in Lecture 3)
- Humans own the data, the conventions, the budget, and **validation**; the AI owns hypotheses and implementation
- 290 factors, top self-reported excess 26% — remember this number; Lecture 2 takes it apart

**Discussion question**: If the loop ran 1000 rounds instead of 40, would the leaderboard's #1 self-reported excess be more or less credible? Why? (Answer direction in Lecture 2)
