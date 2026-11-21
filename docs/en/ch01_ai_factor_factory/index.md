---
title: "Chapter 1 · The AI Factor Factory"
---

# Chapter 1 · The AI Factor Factory

> Lecture notes for Chapter 1 of "When AI Mines Factors, How Not to Be Fooled — by Yourself or by the AI".
> All three lectures are complete, directly teachable documents; all data comes from real campaign results, with conventions labeled as either "factory self-reported" or "independently validated".

| Lecture | File | Topic | Core conclusion |
|---|---|---|---|
| 1 | [E01_loop五步.md](E01_loop五步.md) | The five-step loop and the human-machine division of labor | AI replaces the hands, not the judgment |
| 2 | [E02_看懂排行榜.md](E02_看懂排行榜.md) | IC/ICIR/excess return, multiple testing | The leaderboard is a multiple-testing generator; the top names cannot be trusted |
| 3 | [E03_AI的研究品味.md](E03_AI的研究品味.md) | Anatomy of three factor case types | Code is more honest than intuition; silent logical errors are invisible to the loop itself |

## Data facts used in this chapter (sources for reference)

- A-share campaign factor pool of 290 factors; leaderboard top self-reported excess +26.5% (asset_growth_neg / low_beta_rank / turn_of_month_rank); momentum_20d and reversal_5d each with 23 evaluations and 33 versions (pulled live from Console /api/research/factors, 2026-10-04)
- Futures round one: 13 instruments, 136 trials, postloop pre-registered validation all FAIL (rdagent_import/20260924/futures_postloop/)
- Futures round two: 23 instruments, EQWI-23 benchmark, first window 40 loops; a glm server-side outage ate roughly half of capacity
- Carry double-adjustment erratum: discovery period +18% → after correction +3.18% (t=0.66, not significant), D-9 revision
- Crypto two rounds: after independent validation, the real signals were vol_20d / reversal_5d (textbook factors)
- A-share honest convention: three candidates all FAIL DSR, benchmark with limit-up artifact removed
