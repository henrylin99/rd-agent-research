---
title: "Chapter 4 · What a Surviving Strategy Looks Like"
---

# Chapter 4 · What a Surviving Strategy Looks Like

> Lecture notes for Chapter 4 (Lectures 10–11) of "When AI Mines Factors, How Not to Be Fooled by Yourself and the AI".

| Lecture | File | Topic | Core case |
|---|---|---|---|
| 10 | [E10_funding_carry全程.md](E10_funding_carry全程.md) | Three questions after the verdict (where the money comes from / how much / for how long), the variant ban | funding carry SUPPORTED +2.37%/yr (p<0.0001, F1–F8 all passed), funding-fee contribution 109% |
| 11 | [E11_影子模式.md](E11_影子模式.md) | Shadow-mode design, monitoring metrics, the meta-question of monitoring systems | K2 false-positive recurrence; alert tiering; 30-day pipeline validation |

## Data facts for this chapter (sources on file)

- funding carry: single one-shot OOS verdict of SUPPORTED on 2026-09-24; +2.37%/yr, p<0.0001; source decomposition FUNDING 109%; F1–F8 all passed; magnitude = cash-management grade; variant ban in effect
- Shadow mode: 30-day frozen monitoring starting 2026-09-25; after the reconciliation loop was restored on 10-04, the K2 false positive re-entered DEGRADED (the settlement had in fact been booked; the detector's judgment logic was flawed; an earlier retest had been wrongly deemed passed because the 30-min window had not yet elapsed)
