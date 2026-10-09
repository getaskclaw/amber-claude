[English](README.md) · 简体中文

# amber-claude

> ⚠️ **更正（2026-10-02，另一项）**：防御轴的一案 A-d511f9e8 在所有车道上改记 NA（考场判的不是考生交付的文件，判分还要求了题面没写的事）。分母不变，**过案数不变**，每条道的总分都带 `'`。本仓各期成绩表里这一格请按 NA 读，其余内容保留原样，以[更正声明](https://github.com/getaskclaw/amber/blob/main/docs/corrections-2026-10-02-a-d511f9e8.md)为准。

> **2026-10-07 更新**：claude-fable-5-1 的品牌题 A-d9b79b46（UI）由 NA（挂起）改记为负：2026-10-07 该案题面修改后，只重考了这一格，判分器 11/12，未过。过案数不变（16），负案 5→6，NA 3→2，总分仍是 16'/24。claude-opus-5-5 和 claude-sonnet-5-5 这一案的格子是旧题面下的成绩，不变。见 [2026-W40 期文](results/2026-W40.md)。

> **2026-10-07 更新（第二次）**：运维案 A-24bcf707：判分器要求被指的移除提交在功能自身的文件上有删除行，题面没有写这个要求；claude-fable-5-1 只挂了这一项检查，这一格由负改记 NA（挂起）。过案数不变（16），负案 6→5，NA 2→3，总分仍是 16'/24；运维轴 5/6 · 1 NA。Opus、Sonnet 这一案的格子是过，不变。见[规范仓 2026-10-07 的更正](https://github.com/getaskclaw/amber/blob/main/docs/corrections-2026-10-07-a-24bcf707.md)和 [2026-W40 期文](results/2026-W40.md)。

> **2026-10-07 更新（第三次）**：审查案 A-cdc3d11a 在所有车道上改记 NA（挂起），分母仍是 24：在一道审查案上，判分器把一条格式正确的发现里的每个子点都算作一条各自未被证实的断言，又把短答案清单之外的真实缺陷当作误报，所以一份正确、格式良好的审查达不到及格线。本仓三个模型这一格原来都是负，现在都是 NA，过案数不变（claude-opus-5-5 19'/24、claude-sonnet-5-5 19'/24、claude-fable-5-1 16'/24）。没有重考任何卷。见[规范仓 2026-10-07 的更正（A-cdc3d11a）](https://github.com/getaskclaw/amber/blob/main/docs/corrections-2026-10-07-a-cdc3d11a.md)和 [2026-W40 期文](results/2026-W40.md)。

给 Anthropic 的 Claude 模型做同一套**私有**实战考试（题库叫 **AMBER**，共 24 道题）。只公开结果，不公开题目。

> **一句话**：三个 Claude 模型各做一遍 24 道实战题（写代码、做运维、挑别人的错等），过题数是 **claude-sonnet-5-5 19'/24 · claude-opus-5-5 19'/24 · claude-fable-5-1 16'/24**。动手干活的题（写代码、运维、交付）基本都过；丢分主要在防御、归因、审查这三类判断题（其中审查有一案 2026-10-07 起挂起，不计分）。claude-fable-5-1 的品牌题 2026-10-07 题面修改后重考，改记负；运维案 A-24bcf707 因判分器比题面严改记 NA（挂起）；过案数都不变。
>
> 分数后的 `'` 表示其中有几题暂不计分（NA），既不算过也不算没过，原因见下。claude-opus-5-5 是重考，W39 首考是 17'/24；两次并列看，不据此判断它变强或变弱。
>
> **更正**：claude-opus-5-5 的 W39 记录为 17 胜 · 6 负 · 1 案考场(harness)基建 NA：原卷未落盘，零流量闸误判。拒答观察仅留诊断附注；owner 已签撤回安全边界部署建议。见 [更正](results/2026-W39-correction.md)。

## 成绩一览

<!-- scoreboard:start -->

![amber-claude 成绩一览：claude-opus-5-5、claude-sonnet-5-5、claude-fable-5-1 逐轴过案数](results/assets/scoreboard.zh.png?v=20261009)

| 大类 | 轴 | 考什么 | claude-opus-5-5 · [W40](results/2026-W40.md) | claude-sonnet-5-5 · [W40](results/2026-W40.md) | claude-fable-5-1 · [W40](results/2026-W40.md) |
|---|---|---|:-:|:-:|:-:|
| 施工面 | 编码 | 照着需求把功能写对 | 5/6 | 6/6 | 5/6 |
|  | 交付 | 做完还得交得出东西 | 3/3 | 3/3 | 3/3 |
|  | 运维 | 照规程干脏活 | 6/6 | 6/6 | 5/6 · 1 NA |
|  | 需求 | 客户要 A 不要 B | 1/1 | 1/1 | 1/1 |
|  | 收敛 | 真干完，不绕圈装忙 | 1/1 | 1/1 | 1/1 |
| 判断面 | UI | 照设计稿做页面 | 1/1 | 1/1 | 0/1 |
|  | 视觉 | 给真截图挑毛病 | 1/1 | 1/1 | 1/1 |
|  | 防御 | 堵死校验器的漏网口 | 0/2 · 2 NA | 0/2 · 1 NA | 0/2 · 2 NA |
|  | 归因 | 毛病对到正确根因 | 0/1 · 1 NA | 0/1 | 0/1 |
|  | 审查 | 给别人的交付物挑错 | 1/2 · 1 NA | 0/2 · 1 NA | 0/2 · 1 NA |
|  | **合计** |  | **19'/24** | **19'/24** | **16'/24** |

- **都拿满**：交付、需求、收敛、视觉。
- **都没过**：防御、归因（一道都没过；NA 不算没过）。
- **有差别**（数字依次对应上表各列）：编码 5/6 对 6/6 对 5/6、运维 6/6 对 6/6 对 5/6 · 1 NA、UI 1/1 对 1/1 对 0/1、审查 1/2 · 1 NA 对 0/2 · 1 NA 对 0/2 · 1 NA。

每格 = 过了几案/该轴共几案（案 = 一道计分题）。NA = 这一案作废或暂停计分，不算过也不算没过；总分带 `'` 表示其中有 NA。多数轴只有 1–2 案，差一案读数就变，所以别把小差距当结论。各列考试周次相同（W40），具体日期可能不同，数字是当期快照。

<!-- scoreboard:end -->

## 这是什么

- **AMBER** 是一套私有的实战题库：让模型像工程师一样做事（写功能、照规程运维、审查别人的交付、看截图找问题、应对中途改需求……），再按预设的检查项打分。规范与制题工具见 [getaskclaw/amber](https://github.com/getaskclaw/amber)，题目本身不公开。
- **每期一篇** `results/YYYY-Www.md`：同一套题、同一套考试程序（harness，自动让模型做题并记分的工具），对目标模型考全部题目。报告写明题集规模与哈希（防偷换题目的指纹）、每题通过或失败和得分（我们自己的打分，算法不公开）、token 用量与成本（订阅渠道没有单价表，不报美元）、用时、环境信息，以及按证据写的文字结论。
- 题目、判分器、答题全过程记录、中间产物**永不公开**（见下「发布纪律」）。

几个词：

- **案**：一道计分题。**NA**：这一案作废或暂停计分，不算过也不算没过。
- **道**：同一个模型名在某一家渠道（卖场 / 接口）上的一次测评；同名模型在不同渠道可能是不同端点，所以跨仓比较一律带日期和档位。
- **档（effort 档）**：给模型设定的思考力度。

## 姐妹仓

[amber-gpt](https://github.com/getaskclaw/amber-gpt) · [amber-kimi](https://github.com/getaskclaw/amber-kimi) · [amber-commandcode](https://github.com/getaskclaw/amber-commandcode) · [amber-nous](https://github.com/getaskclaw/amber-nous) · [amber-deepseek](https://github.com/getaskclaw/amber-deepseek) · [amber-doubao](https://github.com/getaskclaw/amber-doubao) · [amber-stepfun](https://github.com/getaskclaw/amber-stepfun) · [amber-ollama](https://github.com/getaskclaw/amber-ollama) · [amber-crof](https://github.com/getaskclaw/amber-crof) · [amber-opencode](https://github.com/getaskclaw/amber-opencode) · [amber-workbuddy](https://github.com/getaskclaw/amber-workbuddy) · [amber-goldenpotato](https://github.com/getaskclaw/amber-goldenpotato) · [amber-devin](https://github.com/getaskclaw/amber-devin)

## 各期成绩

- **2026-W40** — claude-sonnet-5-5 **19'/24**（19 胜 · 3 负 · 2 NA）· claude-opus-5-5 重考 **19'/24**（19 胜 · 1 负 · 4 NA；W39 首考为 17'/24）· claude-fable-5-1 **16'/24**（16 胜 · 4 负 · 4 NA）。动手类的题都强，防御、归因、审查是共同短板。本期的 NA 有三种原因：
  1. 防御案 A-d511f9e8 在所有车道上暂停计分（考场判分有问题，见[更正声明](https://github.com/getaskclaw/amber/blob/main/docs/corrections-2026-10-02-a-d511f9e8.md)），三个模型各有这 1 个 NA；
  2. 审查案 A-cdc3d11a 在所有车道上挂起（判分器在这个题的格式下达不到及格线，见[规范仓 2026-10-07 的更正（A-cdc3d11a）](https://github.com/getaskclaw/amber/blob/main/docs/corrections-2026-10-07-a-cdc3d11a.md)），三个模型各有这 1 个 NA（原来都是负）；
  3. 两次作答都撞到考场时间上限，按当时成文规则记 NA，不计负（Opus 2 案、Fable 1 案）。

  此外，Fable 的品牌题 A-d9b79b46 曾因题面与考场不一致记 NA（挂起）；2026-10-07 题面修改后只重考了这一格（11/12，未过），改记负，不再是 NA。Opus、Sonnet 这一案的格子是旧题面下的成绩，不变。

  还有 Fable 的运维案 A-24bcf707：判分器对移除提交的检查比题面严，Fable 只挂这一项，这一格记 NA（挂起），不计负；Opus、Sonnet 这一案是过，不变。见[规范仓 2026-10-07 的更正](https://github.com/getaskclaw/amber/blob/main/docs/corrections-2026-10-07-a-24bcf707.md)。

  见 [期文](results/2026-W40.md)。
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
