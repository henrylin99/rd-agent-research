---
title: "Extra 2 · The HITL Reconnaissance Screen: Another Way of Putting the Human in the Loop"
---

# Extra 2 · The HITL Reconnaissance Screen: Another Way of Putting the Human in the Loop

> Extras (Lectures 6 and 12 recommended reading first)
> Learning objective: understand the design logic of the Human-In-The-Loop (HITL) reconnaissance mode, and its complementary relationship with the fully automated loop.

## 1. Background: why a "screen filled in by humans"

The main course's full pipeline (factory → validation → shadow) has an implicit scope of applicability: **the hypothesis can be fully formalized and backtested on historical data**. But one class of opportunities fails this premise:

- The signals are **unstructured** (qualitative judgments on news, announcements, rumors)
- Low frequency (only a few dozen effective events a year); the historical sample is too small to backtest
- The judgment itself depends on human contextual understanding and can hardly be written as rules in advance

For such opportunities, forcing them into a backtest framework is cutting the foot to fit the shoe; abandoning them is a waste. The third option: a **reconnaissance screen** — the system scans and records; the human judges and fills in; the judgments settle into forward data.

## 2. Design: freeze first

Key design decisions of the HITL scanner as actually deployed (online 2026-09-27, verdict date 2026-12-26):

**① Pre-registration discipline applies equally.** The verdict metrics (precision ≥ 30%, fill rate ≥ 50%) and the verdict date were frozen before going live — Lecture 12's gate institution applied verbatim. The human-in-the-loop is not a discipline-exemption zone: precisely because humans participate, the temptation to "just tweak the standard a bit" is greater.

**② Human judgment is structured.** The entry interface accepts only discrete fields (direction, confidence tier, reason code), not free-text scoring — guaranteeing the data is statistically analyzable after 90 days. Freestyle judgment cannot be aggregated.

**③ The verdict date covers a real event round.** The screen monitors index-rebalance events, and the verdict date is set after the 2026-12 rebalance round — so that the verdict happens after "the screen has seen at least one complete round of real events", rather than merely accumulating calendar days.

**④ 90 days of observation, no peeking at results midway.** Isomorphic to the one-shot OOS verdict: peek midway → learn which signal types perform well → unconsciously change entry behavior → data contaminated. With a human in the loop, the human is the biggest source of degrees of freedom, so the lock must be even tighter.

## 3. The division of labor between HITL and the fully automated loop

| | Fully automated loop | HITL reconnaissance screen |
|---|---|---|
| Hypothesis form | Formalizable, backtestable | Qualitative, low-frequency, context-dependent |
| Human's role | Sets panel/convention/thresholds | Judges inside the loop |
| Data output | Historical backtests | A forward-accumulating structured stream of judgments |
| Verdict | Pre-registered one-shot OOS verdict | Pre-registered metrics + frozen verdict date |
| Main risk | Multiple testing | Human behavioral drift contaminating the data |

What the two share is not technology but the discipline skeleton: **frozen criteria, accumulating forward data, a one-shot verdict**. The only difference is where the data comes from (backtests vs the stream of human judgments).

## 4. Extra summary

- HITL's zone of applicability: opportunities that cannot be formalized for backtesting, are low-frequency, and context-dependent
- Structured entry + frozen criteria + coverage of a complete event round + no peeking midway — this four-piece set locks the human's degrees of freedom within what data quality allows
- Fully automated and HITL are two data sources of the same validation discipline

**Reflection question**: why is "fill rate ≥ 50%" among the verdict metrics a necessary condition? (Hint: if only 10% of signals get a filled-in judgment, however high the precision, what is the screen's value as a data asset? — selective entry is itself a form of post-hoc selection bias.)
