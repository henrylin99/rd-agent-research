---
title: 课程总览
---

# AI 挖因子时，如何不被自己和 AI 骗到

> 基于 2026-09~10 真实量化战役（A 股 / 期货两轮 / crypto 两轮）的完整留痕写成的讲义。
> 定位：AI 是背景板，诚实验证是主角。所有数字取自真实结果，出处见各章 README 的"数据事实备查"。

## 从这里开始

| 我要… | 直接点这里 |
|------|------|
| 系统地从头读 | **[第一讲 · AI 因子工厂是怎么运转的 →](ch01_ai_factor_factory/E01_loop五步.md)** |
| 看最扎心的实战复盘 | **[第五讲 · 三候选 DSR 全 FAIL 复盘 →](ch02_honest_validation/E05_全军覆没复盘.md)** |
| 看最经典的踩坑案例 | **[第七讲 · D-9 勘误：双重复权 →](ch03_data_traps/E07_双重复权.md)** |
| 看活下来的策略长什么样 | **[第十讲 · funding carry →](ch04_survivor/E10_funding_carry全程.md)** |
| 看方法论收束与总结 | **[第十三讲 · 全课程收束 →](ch05_discipline/E13_课程总结与战役矩阵复盘.md)** |

> 📖 **全部 13 讲 + 2 篇番外在顶部导航**，按章组织，可按顺序读也可按需跳读。

## 全书结构（13 讲）

| 章 | 目录 | 讲次 | 一句话 |
|---|---|---|---|
| 一 · AI 因子工厂 | [ch01_ai_factor_factory/](ch01_ai_factor_factory/index.md) | E1–3 | 工厂替代的是手，不是判断 |
| 二 · 诚实的验证 | [ch02_honest_validation/](ch02_honest_validation/index.md) | E4–6 | 预注册、DSR、OOS 一次性判定 |
| 三 · 数据口径的暗雷 | [ch03_data_traps/](ch03_data_traps/index.md) | E7–9 | 双重复权、基准伪影、五层审计栈 |
| 四 · 活下来的策略 | [ch04_survivor/](ch04_survivor/index.md) | E10–11 | funding carry +2.37%/yr 与影子模式 |
| 五 · 方法沉淀 | [ch05_discipline/](ch05_discipline/index.md) | E12–13 | 机会筛选纪律与负结果的复利 |
| 番外 | [extras/](extras/index.md) | EX1–2 | crypto 头名鉴定、HITL 侦察屏 |

## 贯穿数字

- 290 个因子，自报超额最高 +26.5%，独立验证 **0 存活**
- 假 carry +18%（双重复权 bug）→ 纠错 +3.18%（t=0.66）；真 carry **+2.37%/yr**（资金费贡献 109%）
- 三种判决实例：REJECTED −0.49% / INCONCLUSIVE +1.00%（p=0.062）/ SUPPORTED +2.37%
- 主线：**真 alpha 又小又难看；假 alpha 又大又合理**

## 讲义使用说明

- 每讲自成一体：开头有学习目标与前置，结尾有思考题（多数在讲内或下一讲有回收方向）
- 每章 README 附"数据事实备查"：本讲引用的每个数字的来源与口径，备课时被追问可兜底
- 全书口径纪律：区分"工厂自报"（工厂内置回测）与"独立验证"（预注册管线）两种来源，讲课时不得混用

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