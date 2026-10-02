# amber-claude

用私有题库 **AMBER** 实测 Anthropic Claude 系列模型，只公开结果，不公开题目。
English: [README.en.md](README.en.md)

> **一句话**：这里是 Anthropic Claude 的 AMBER 成绩单。案 = 一道计分任务。claude-sonnet-5-5 的 W40 首考为 **19/24**（19 胜 · 5 负 · 0 NA），与当前最高分同分；claude-opus-5-5 的 W39 首考为 **17'/24**。两个型号的失分主要在防御、归因、审查三轴，逐轴见下表。
>
> **更正**：claude-opus-5-5 的 W39 记录为 17 胜 · 6 负 · 1 案考场(harness)基建 NA：原卷未落盘，零流量闸误判。拒答观察仅留诊断附注；owner 已签撤回安全边界部署建议。见 [更正](results/2026-W39-correction.md)。

## 成绩一览

<!-- scoreboard:start -->

![amber-claude 成绩一览：claude-sonnet-5-5、claude-opus-5-5 逐轴过案数](results/assets/scoreboard.zh.png?v=20261002)

| 大类 | 轴 | 考什么 | claude-sonnet-5-5 · [W40](results/2026-W40.md) | claude-opus-5-5 · [W39](results/2026-W39.md) |
|---|---|---|:-:|:-:|
| 施工面 | 编码 | 照着需求把功能写对 | 6/6 | 5/6 |
|  | 交付 | 做完还得交得出东西 | 3/3 | 2/3 · 1 NA |
|  | 运维 | 照规程干脏活 | 6/6 | 5/6 |
|  | 需求 | 客户要 A 不要 B | 1/1 | 1/1 |
|  | 收敛 | 真干完，不绕圈装忙 | 1/1 | 1/1 |
| 判断面 | UI | 照设计稿做页面 | 1/1 | 1/1 |
|  | 视觉 | 给真截图挑毛病 | 1/1 | 1/1 |
|  | 防御 | 堵死校验器的漏网口 | 0/2 | 0/2 |
|  | 归因 | 毛病对到正确根因 | 0/1 | 0/1 |
|  | 审查 | 给别人的交付物挑错 | 0/2 | 1/2 |
|  | **合计** |  | **19/24** | **17'/24** |

- **都拿满**：需求、收敛、UI、视觉。
- **都没过**：防御 0/2、归因 0/1。
- **有差别**：编码 6/6 对 5/6、交付 3/3 对 2/3 · 1 NA、运维 6/6 对 5/6、审查 0/2 对 1/2。

每格 = 通过案数/该轴案数。NA = 作废或挂起的案，不计胜负；总分带 `'` 表示含 NA。多数轴只有 1–2 案，一案就能改变该轴读数。各期考试日期不同，数字是当期快照。

<!-- scoreboard:end -->

## 这是什么

- 每期一篇 `results/YYYY-Www.md`：同一套题、同一套考试程序（harness，自动让模型做题并记分的工具），对目标模型跑全库；同名模型跨厂商并排。
- 一期固定报告：题集规模与哈希（hash = 防偷换题目的指纹）、每题（案）的 d2 分（我们的打分，算法不公开）与通过 / 失败、终端终态（程序跑完时的退出状态）、token 用量与成本（按量计费的渠道如实报价；订阅渠道无单价表，不报美元）、时延、环境指纹、按证据纪律写的定性裁决。
- 题目、oracle（判分器）、transcript（答题全过程记录）、中间产物**永不公开**（见下「发布纪律」）。
- AMBER 是 agentic 实战题库（施工 / 运维 / 审查 / 视觉 / 需求漂移——题中要求中途变化），规范与制题工具见 [getaskclaw/amber](https://github.com/getaskclaw/amber)；考题本体私有。
- 「道」= 同一个模型名在不同家的卖场 / 接口；「effort 档」= 给模型设置的思考力度档位。跨仓比较时，同名模型在不同「道」上可能是不同端点，引用一律带日期与档位声明。

## 姐妹仓

[amber-gpt](https://github.com/getaskclaw/amber-gpt) · [amber-kimi](https://github.com/getaskclaw/amber-kimi) · [amber-commandcode](https://github.com/getaskclaw/amber-commandcode) · [amber-nous](https://github.com/getaskclaw/amber-nous) · [amber-deepseek](https://github.com/getaskclaw/amber-deepseek) · [amber-doubao](https://github.com/getaskclaw/amber-doubao) · [amber-stepfun](https://github.com/getaskclaw/amber-stepfun) · [amber-ollama](https://github.com/getaskclaw/amber-ollama) · [amber-crof](https://github.com/getaskclaw/amber-crof) · [amber-opencode](https://github.com/getaskclaw/amber-opencode) · [amber-workbuddy](https://github.com/getaskclaw/amber-workbuddy) · [amber-goldenpotato](https://github.com/getaskclaw/amber-goldenpotato) · [amber-devin](https://github.com/getaskclaw/amber-devin)

## 各期成绩

- **2026-W40** — claude-sonnet-5-5 **19/24**：19 胜 · 5 负 · 0 NA。施工、运维全满，短板在审查与核验。见 [期文](results/2026-W40.md)。
- **2026-W39** — claude-opus-5-5 **17'/24**：17 胜 · 6 负 · 1 案基建作废。' = contested（安全拒答挂起）或 invalid（基建相关（考场 harness 或判分环境）的挂起、作废或待重评），均不计胜负；所有含 NA 的道都带撇号，包括冻结展示行；挂起不表示死因已定。见 [更正](results/2026-W39-correction.md) · [原刊](results/2026-W39.md)。

W39 的十轴完成度画像（claude-opus-5-5 对 k3）在 [更正](results/2026-W39-correction.md) 页内。

## 发布纪律（红线）

1. 只发：分数与聚合、token 用量与成本、速度、定性裁决。
2. 永不发：题目内容、oracle / 判分器、transcript、考生工作区、任何能复原题面的中间产物。
3. 每期必钉：模型 ID、effort 档、日期（UTC）、harness 版本、每案内容哈希（bundle_sha，每题内容的哈希指纹）。哈希用于对照 [amber](https://github.com/getaskclaw/amber) 的公开哈希清单，自证题集未变。
4. 案号与题目结构属私有面：公开结果里案例只用稳定别名（A-xxxxxxxx，哈希派生）+ bundle 哈希作句柄；内部案号、变体名、题目描述永不出现。
5. 基调：这是社区实测，不是对厂商的攻击。数据说话，措辞克制。

## 一个方法论前提

同名模型、同 provider，两次跑也可能不同分——推理参数、负载、服务端版本都在漂。所以这里的一切结论都带日期与档位，且定期重测。单日数字是快照，不是定律。
