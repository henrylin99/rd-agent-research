# rd-agent研究结果

基于 RD-Agent 量化研究战役（2026-09~10，A 股 / 期货两轮 / crypto 两轮）真实留痕写成的 13 讲讲义 + 2 篇番外：AI 挖因子时，如何不被自己和 AI 骗到。

**在线阅读**：https://henrylin99.github.io/rd-agent-research/

- 第一章 · AI 因子工厂（E1–3）：工厂替代的是手，不是判断
- 第二章 · 诚实的验证（E4–6）：预注册、DSR、OOS 一次性判定
- 第三章 · 数据口径的暗雷（E7–9）：双重复权、基准伪影、五层审计栈
- 第四章 · 活下来的策略（E10–11）：funding carry 与影子模式
- 第五章 · 方法沉淀（E12–13）：机会筛选纪律与负结果的复利
- 番外：crypto 头名鉴定、HITL 侦察屏

讲义源文件：`quant_space/rd-agent-sd/course`（本仓库为发布副本）。

## 本地构建

```bash
pip install mkdocs-material
mkdocs serve   # 本地预览
mkdocs gh-deploy --force   # 部署（CI 自动执行）
```
