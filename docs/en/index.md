---
title: Home
---

# When AI Mines Factors, How Not to Be Fooled — by Yourself or by the AI

!!! tip "Click the link to switch to the 中文版"
    🇨🇳 本教程有中文版 → [切换到中文教程](/rd-agent-research/)

> A lecture series written from the complete records of real quant campaigns (A-shares / two futures rounds / two crypto rounds) conducted in 2026-09~10.
> Positioning: AI is the backdrop; honest validation is the protagonist. All numbers come from real results; sources are in each chapter README's "data facts for reference" section.

## Start Here

| I want to... | Click here |
|------|------|
| To read systematically from the beginning | **[Lecture 1 · How the AI Factor Factory Runs →](ch01_ai_factor_factory/E01_loop五步.md)** |
| The most painful battle retrospective | **[Lecture 5 · Three Candidates All FAIL DSR Retrospective →](ch02_honest_validation/E05_全军覆没复盘.md)** |
| The most classic pitfall case | **[Lecture 7 · The D-9 Erratum: Double Adjustment →](ch03_data_traps/E07_双重复权.md)** |
| What a surviving strategy looks like | **[Lecture 10 · funding carry →](ch04_survivor/E10_funding_carry全程.md)** |
| Methodology convergence and wrap-up | **[Lecture 13 · Full-Course Wrap-Up →](ch05_discipline/E13_课程总结与战役矩阵复盘.md)** |

> 📖 **All 13 lectures + 2 extras are in the top navigation**, organized by chapter — read in order or jump as needed.

## Book Structure (13 Lectures)

| Chapter | Directory | Lectures | In one sentence |
|---|---|---|---|
| 1 · The AI Factor Factory | [ch01_ai_factor_factory/](ch01_ai_factor_factory/index.md) | E1–3 | The factory replaces the hands, not the judgment |
| 2 · Honest Validation | [ch02_honest_validation/](ch02_honest_validation/index.md) | E4–6 | Pre-registration, DSR, one-shot OOS verdicts |
| 3 · Hidden Mines in Data Conventions | [ch03_data_traps/](ch03_data_traps/index.md) | E7–9 | Double adjustment, benchmark artifacts, a five-layer audit stack |
| 4 · Strategies That Survived | [ch04_survivor/](ch04_survivor/index.md) | E10–11 | funding carry +2.37%/yr and shadow mode |
| 5 · Method Consolidation | [ch05_discipline/](ch05_discipline/index.md) | E12–13 | Opportunity-screening discipline and the compounding of negative results |
| Extras | [extras/](extras/index.md) | EX1–2 | Crypto top-name forensics, HITL scout screen |

## Numbers That Run Through the Book

- 290 factors, self-reported excess as high as +26.5%, **0 survivors** under independent validation
- Fake carry +18% (double adjustment bug) → corrected +3.18% (t=0.66); real carry **+2.37%/yr** (funding rate contribution 109%)
- Three verdict examples: REJECTED −0.49% / INCONCLUSIVE +1.00% (p=0.062) / SUPPORTED +2.37%
- The main thread: **real alpha is small and ugly; fake alpha is big and plausible**

## How to Use These Lectures

- Each lecture is self-contained: learning objectives and prerequisites at the top, discussion questions at the end (most are picked up later within the same lecture or the next one)
- Each chapter README includes a "data facts for reference" section: the source and convention behind every number cited in that lecture, as backup for when you get challenged while teaching
- Book-wide convention discipline: distinguish between "factory self-reported" (the factory's built-in backtest) and "independently validated" (the pre-registered pipeline) — the two must never be mixed when teaching

```bash
# web页面启动
PYTHONPATH=/Users/henrylin/quant_space/rd-agent-sd \
RDAgent_UI_LOG_DIRS=/Users/henrylin/quant_space/rd-agent-sd/log,/Users/henrylin/quant_space/rd-agent-sd/log\ copy/futures_r1,/Users/henrylin/quant_space/rd-agent-sd/git_ignore_folder/RD-Agent_workspace \
nohup /Users/henrylin/anaconda3/envs/rdagent/bin/python -m rdagent.log.server.app_v2 --port 27181 \
> /tmp/rdagent_console_27181.log 2>&1 &

# streamlit启动
PYTHONPATH=/Users/henrylin/quant_space/rd-agent-sd \
nohup /Users/henrylin/anaconda3/envs/rdagent/bin/rdagent ui --port 19899 \
> /tmp/rdagent_streamlit_19899.log 2>&1 &
```
