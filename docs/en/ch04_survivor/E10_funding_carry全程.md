---
title: "Lecture 10 · funding carry: What a Surviving Strategy Looks Like"
---

# Lecture 10 · funding carry: What a Surviving Strategy Looks Like

> Chapter 4 · What a Surviving Strategy Looks Like (first lecture)
> Learning objectives: using the course's only SUPPORTED case as a specimen, understand the distance between "passing validation" and "worth deploying"; master return-source decomposition and magnitude-expectation management.
> Prerequisites: Chapter 2 (the verdict system), Lecture 7 (the futures version of carry died of double adjustment).

## 1. The case: crypto perpetual funding-rate carry

**Strategy**: under the funding-rate mechanism of crypto perpetual contracts, when the rate is positive longs pay shorts, and when negative shorts pay longs. The strategy shorts high-rate instruments (collecting funding) and longs low/negative-rate instruments — returns come from the funding rate itself, with the price legs roughly hedged.

**Verdict** (pre-registered, one-shot OOS):

> **SUPPORTed: OOS annualized +2.37%, p < 0.0001. All eight sub-tests (F1–F8) passed.**

This is the only all-green verdict since the two chapters of the validation system went live. But the point of this lecture is precisely that **all green does not mean the story is over**. After the verdict come three questions: where does the money come from, how much is there, and how long will it keep coming.

## 2. First question: where does the money come from — return-source decomposition

The validation pipeline decomposed the strategy's returns by source:

> Funding-rate contribution = **109%**.

Translation: the price legs contribute **−9%** — the strategy loses a little on price, and all of the net return (and more) comes from the accrual of funding fees. This structure is **good news**: the funding rate is a mechanical cash flow (payment enforced by protocol rules), not a price prediction; a negative price leg means the hedge is slightly overdone, but it decouples the strategy from price direction.

Contrast with the Lesson-5 lesson (the "pseudo alpha" whose 92% of returns were explained by style beta): this 109% is a **legitimate return structure**: the source is clear, the mechanism is explainable, and its relation to known risk premiums is clean (a carry-type return, in the same family as commodity carry and currency carry). The point of the orthogonalization adversary test here is to confirm "it isn't earning momentum/value/low-vol money" — and source decomposition answers that question more thoroughly.

But note that a deeper question surfaces: **if 109% of returns come from funding, this strategy is by nature not a "prediction strategy" but a "fee-collection strategy"**. It predicts no prices; it simply stands on the receiving side of the funding payment stream. This determines all of its subsequent properties — magnitude, risk, monitoring focus — which are completely different from those of a prediction-type strategy.

## 3. Second question: how much — magnitude and the "cash-management grade" positioning

Annualized 2.37%. When the fake carry of Lecture 7 claimed 18%, it nearly fooled everyone; this real carry yields only 2.37% — the course returns for the third time to the same law:

> **Real alpha is small and ugly; fake alpha is big and plausible.**

The correct handling of 2.37% is not disappointment but **reclassification**: this magnitude belongs not to "strategy returns" but to "cash-management enhancement" — it benchmarks against interest income on idle margin, not against the main strategy's return target. The actual positioning decision was made exactly that way: a satellite return stream of the portfolio, occupying a small share of capital, not playing the main-assault role.

Another dimension of magnitude expectation: **volatility**. The funding rate is regime-dependent — rates run high during bull-market mania (a harvest for the strategy) and hug the ground in quiet periods (returns near zero). 2.37% is the sample-period average; it is not an annuity arriving evenly every month, but feast-or-famine years that follow market sentiment. This property directly determines what the next lecture's shadow monitoring should watch.

## 4. Third question: how long will it last — pre-designing decay monitoring

The ultimate risk of a fee-collection strategy is that **the reason for the fee disappears**: the funding-rate mechanism changes, or market participants arbitrage high-rate instruments back to equilibrium (crowding). For this reason, the monitoring plan was pre-registered at the moment of the verdict, not improvised after trouble:

- **Continuous decomposition of return composition**: the funding contribution share is the primary monitoring metric — if it starts sliding from 109% (the price legs beginning to dominate), that is an early warning of mechanism decay
- **Rate-regime tracking**: the historical percentile of the cross-sectional rate level, to judge whether the current period is feast or famine, rather than misreading a quiet period as "strategy failure"
- **The variant ban**: taking effect simultaneously with the verdict — it is forbidden to derive new variants around it (changing the instrument pool, adding leverage, altering hedge ratios) and apply for validation again. The rationale is isomorphic to Lecture 6's hypothesis-family embargo: **a variant is a disguised retest of the same OOS data**; every variant derived dilutes the statistical power of the original verdict

The variant ban deserves one more sentence because it is counterintuitive: the strategy passed validation, so why not let it "evolve"? Because the choice of evolution direction is guided by impressions from the same dataset — you keep feeling "it would be better if we swapped those two instruments", and that feeling itself comes from memory of in-sample performance. Deriving variants along that feeling means repeatedly overdrawing the same stretch of OOS with in-sample intuition. To genuinely evolve, go forward: new data, new pre-registration.

## 5. The complete dossier of a strategy

Laid out here is the complete dossier of funding carry, as the standard template of "a surviving strategy":

| Dimension | Content |
|---|---|
| Hypothesis | Mechanical (funding payment stream), non-predictive |
| Verdict | Pre-registered one-shot OOS: SUPPORTED (+2.37%/yr, p<0.0001, F1–F8 all passed) |
| Return structure | Funding contribution 109%, price legs −9%, decoupled from price direction |
| Positioning | Cash-management-grade satellite return stream, not a main strategy |
| Risk profile | Rate is regime-dependent (feast-or-famine years); mechanism-change risk; crowding risk |
| Pre-registered monitoring | Funding contribution share + rate percentile; decay-trigger conditions written in advance |
| Variant ban | In effect; evolution only via forward new pre-registration |
| Next step | 30-day shadow monitoring (next lecture) |

Contrast with the treatment of those 290 factors in Lecture 5 — not one of them made it to the second row of this table. **Passing validation is not the endpoint; it is the starting point of being qualified to be taken seriously.**

## 6. Lecture summary

- Return-source decomposition (109% from funding) is a more thorough "new money vs old money" test than orthogonalization; fee-collection strategies and prediction strategies require completely different risk frameworks
- The correct positioning of 2.37% annualized is cash-management grade — magnitude-expectation management is an extension of the validation system
- Decay monitoring is pre-registered at verdict time: watch return composition, not NAV
- The variant ban: derivative improvements after passing validation are disguised OOS retests; evolution goes forward only

**Reflection question**: suppose the funding contribution share falls to 60% in some future quarter (the price-leg contribution turns positive), while the strategy's NAV is unchanged. Under this lecture's monitoring logic, is that good news or bad news? (Hint: a rising price-leg contribution means the strategy is drifting from "collecting fees" toward "predicting prices" — its source of risk has changed, and the original SUPPORTED verdict did not cover this form.)
