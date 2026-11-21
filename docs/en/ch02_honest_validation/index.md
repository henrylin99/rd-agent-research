---
title: "Chapter 2 · Honest Validation"
---

# Chapter 2 · Honest Validation

> Lecture notes for Chapter 2 (Lectures 4–6) of "When AI Mines Factors, How Not to Be Fooled — by Yourself or by the AI".
> This chapter is the core of the whole course: pre-registration, DSR, one-shot OOS verdicts, and the execution of three kinds of judgments.

| Lecture | File | Topic | Core case |
|---|---|---|---|
| 4 | [E04_独立验证与预注册.md](E04_独立验证与预注册.md) | The four components of the validation institution; first principles of multiple testing | Overview of the three verdicts |
| 5 | [E05_全军覆没复盘.md](E05_全军覆没复盘.md) | The four-layer audit stack: DSR/attribution/net-of-cost/benchmark | A-share three candidates all FAIL DSR |
| 6 | [E06_一次预注册实验的完整生命周期.md](E06_一次预注册实验的完整生命周期.md) | The full pre-registered workflow; executing the three verdicts | Earnings forecast REJECTED (−0.49%); index rebalancing INCONCLUSIVE (+1.00%, p=0.062) |

## Data facts for this chapter (sources for reference)

- A-share three candidates all FAIL DSR under the honest convention; residual attribution: 92% of the portfolio with OOS IC 0.043 explained by industry + low-vol + liquidity, residual t=0.14
- Earnings forecast event window: OOS spread −0.49%, discovery period also ineffective, REJECTED as a one-shot verdict (2026-09-24)
- Index rebalancing flow: assembly PASS → discovery period +0.95% → OOS +1.00% (p=0.062, insufficient power) INCONCLUSIVE, OOS frozen and moved to a forward round
- funding carry: OOS SUPPORTED +2.37%/yr (p<0.0001), detailed in Chapter 4
- Futures r1: 136 trials, postloop pre-registered validation all FAIL (rdagent_import/20260924/futures_postloop/)
