---
title: "Chapter 3 · Hidden Mines in Data Conventions"
---

# Chapter 3 · Hidden Mines in Data Conventions

> Lecture notes for Chapter 3 (Lectures 7–9) of "When AI Mines Factors, How Not to Be Fooled — by Yourself or by the AI".
> Theme: the foundation audit beneath the validation institution — data construction, the definition of quantities, convention agreements.

| Lecture | File | Topic | Core case |
|---|---|---|---|
| 7 | [E07_双重复权.md](E07_双重复权.md) | Adjustment mechanics, plausibility bias, the four-piece erratum downstream | carry +18% → +3.18% (t=0.66), D-9 |
| 8 | [E08_基准伪影.md](E08_基准伪影.md) | Benchmark degrees of freedom, quantity-definition-layer audit, differences vs levels | Benchmark excludes-limit-up artifact; dividend double deduction (1+r)/f_ratio² |
| 9 | [E09_期货面板五坑.md](E09_期货面板五坑.md) | Six-step convention audit process, five failure types | Night-session date stamps / roll gaps / $oi erratum / end-of-panel overrun |

## Data facts for this chapter (sources for reference)

- D-9 erratum (2026-10-01): carry discovery-period +18% was double adjustment; after correction +3.18%, t=0.66; protocol versioned as v1.0+D-9 revision; power withdrawal (350-day window, normal approximation ~7%); L2 downgraded to a watch line, deployment investment suspended
- A-share benchmark erratum (2026-09-23): benchmark excluding limit-ups caused an excess artifact; under the honest convention the biweekly top200 had zero excess; excess_honest adopted as the sole convention going forward
- A-share panel dividend double deduction: true total return = (1+r)/f_ratio², verified with zero error against tushare; relative-quantity conclusions unchanged
- Futures panel date stamps (2026-09-28): 918 days contained 180 Sunday rows; the vendor stamps by the night session's actual clock time at open; the return series is correct, cross-source joins misalign by one day, returns computed by per-instrument row order
- Roll detection heuristic: |Δoi| ≥ 30% or open gap |gap| ≥ 3%
- qlib backtest end `calendar[i+1]` overrun: the test window's end must precede the panel's last day by ≥1 trading day
