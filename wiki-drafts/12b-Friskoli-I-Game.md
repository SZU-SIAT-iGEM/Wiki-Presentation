# friskoli-I · 月轨三十日 / Lunar Orbit: 30 Days

> **状态：内容待商酌 (Draft, Pending Review)**
> 本页面描述项目的人类实践/教育传播组成部分——一部互动叙事游戏。内容结构和表述仍在对齐中。

---

## 这是什么 / What This Is

**friskoli-I** 是一部为 iGEM 2026 Space Track 设计的**互动叙事游戏**（interactive narrative game）。玩家扮演月球先遣队的生物系统技术员，在 30 天的月轨航程中操作一台搭载工程菌的生物反应器。

**friskoli-I** is an interactive narrative game designed for the iGEM 2026 Space Track. The player assumes the role of a biosystem technician on a lunar orbit mission, operating a bioreactor carrying engineered bacteria over a 30-day voyage.

---

## 设计目的 / Design Purpose

这部游戏服务于项目的三个目标：

1. **公共传播**：将抽象的合成生物学概念——微重力传质限制、PTS 趋化、表面展示、趋化招募正反馈循环——翻译为直观的、可感知的游戏体验。

2. **教育工具**：通过"第一轮带普通菌失败→第二轮带 friskoli 重新出发"的双轮结构，让玩家亲身体验工程迭代的逻辑。不是被告知"friskoli 更好"，而是自己**发现**它在哪里更好（事件 1、7、8、9、10）、在哪里和普通菌一样平凡（事件 3、4、5、6）。

3. **诚实叙事**：游戏刻意区分了 friskoli 的**设计原理**（趋化、表面展示、趋化招募正反馈）和**未来展望**（PETase、RecA、受控生物膜、通用平台）。前者是当前项目的工程目标，在事件结果中直接生效，且在 friskoli 真正擅长的场景（事件 1、7、8、9、10）中展现定向优势，在 friskoli 没有理由更好的场景（事件 3、4、5、6）中坦然表现平庸；后者只通过"未来展望卡"呈现，明确标注「我们尚未达到」。

The game serves three project goals:

1. **Public communication**: Translate abstract synthetic biology concepts — microgravity mass-transfer limitation, PTS chemotaxis, surface display, chemotactic recruitment feedback loop — into intuitive, perceptible gameplay experiences.

2. **Educational tool**: Through a two-round structure (first round fails with normal bacteria → second round redeems with friskoli), players personally experience the logic of engineering iteration — discovering where friskoli genuinely excels (Events 1, 7, 8, 9, 10) and where it is honestly no better than wild-type (Events 3, 4, 5, 6).

3. **Honest narrative**: The game deliberately distinguishes friskoli's **design principles** (chemotaxis, surface display, chemotactic recruitment loop) from **future visions** (PETase, RecA, controlled biofilm, universal platform). The former are the project's current engineering goals — they drive outcomes in events where friskoli is genuinely advantaged (Events 1, 7, 8, 9, 10) and show honest parity with normal MG1655 where friskoli has no engineered reason to outperform (Events 3, 4, 5, 6). Future visions appear only through "Vision Cards" explicitly labeled "we have not yet achieved this."

---

## 游戏结构 / Game Structure

### 双轮设计 / Two-Round Design

| 轮次 | 菌株 | 核心体验 |
|------|------|---------|
| **Round 1** | E. coli MG1655（表面展示纤维素酶，无趋化模块） | 玩家在微重力下遭遇传质瓶颈、毒性、辐射、丝状化、生物膜——每一项都超出普通菌的能力边界。玩家带回的"失败数据"成为 friskoli 存在的理由。 |
| **Round 2** | friskoli（AscF 趋化 + INP 表面展示 + 趋化招募正反馈循环） | 同样的 10 个事件，趋化系统在"绝对静息""纤维素风暴""幽灵重力""终局的余烬"中展现出定向优势；在"毒性逼迫""辐射风暴""形态变化""膜的叛乱"中与普通菌表现一致——friskoli 只在它被设计来擅长的事上更好。"信号致盲"是只有趋化菌才会遇到的问题。 |

### 10 个事件 / Ten Events

游戏沿 30 天月轨航程安排 10 个核心事件，每个事件对应 friskoli 科学叙事中的一个关键概念：

| # | Day | 事件 | 对应的科学概念 | friskoli 的表现 |
|---|-----|------|--------------|---------------|
| 1 | 3 | 绝对静息 | 微重力液相停滞、扩散限制 | 关闭搅拌后出现定向运动 |
| 2 | 6 | 包装危机 | PET 塑料不在 friskoli 菜单上 | 和普通菌一样无能为力 → 解锁 PETase 展望 |
| 3 | 9 | 毒性逼迫 | MCP 与 PTS 趋化通路的分工 | friskoli 和普通菌表现一致——毒物应激走 MCP 通路，friskoli 没动那一侧 |
| 4 | 13 | 辐射风暴 | 深空辐射与质粒丢失 | 质粒丢失，工程性状退化。「它没死，但它不再是 friskoli」→ 解锁 RecA 展望 |
| 5 | 16 | 形态变化 | 微重力下丝状化（Zea 2017） | friskoli 也丝状化了。FtsZ 装配紊乱不是工程改造能影响的事 |
| 6 | 19 | 膜的叛乱 | 群体感应与生物膜 | friskoli 和普通菌一样形成生物膜——curli/QS 调控不在改造范围内 |
| 7 | 22 | 纤维素风暴 | **趋化招募正反馈循环** | 核心展示：一次性投入纤维素 → 正反馈启动 → 产出飙升 |
| 8 | 25 | 信号致盲 | PTS 线性趋化的动态范围限制 | 只有趋化菌才会遇到的问题——但代谢消耗天然去饱和 |
| 9 | 27 | 幽灵重力 | 对流独立性 | 重力消失后趋化接管，切换平滑 |
| 10 | 29 | 终局的余烬 | 启动子扫描与灵敏度极限 | 在死角中感知微弱梯度 → 穿越反应器 → 完美结局 |

### 未来展望卡 / Vision Cards

五张展望卡，每张对应 friskoli 未来可扩展的方向。它们只通过游戏中的特定条件解锁，且明确标注为"我们尚未达到"：

| 卡 | 触发条件 | 核心设想 |
|----|---------|---------|
| **PETase 降解模块** | 携带 PET 样本盒并遭遇包装危机 | INP 表面展示系统扩展到 PET 塑料降解 |
| **RecA 修复强化** | 携带紫外灯并在辐射风暴中选择硬扛 | 引入 Deinococcus radiodurans 的 RecA 系统应对深空辐射 |
| **受控生物膜** | Round 2 遭遇生物膜事件 | 群体感应输出接到工程化启动子，生物膜从"叛乱"变成可指挥的基础设施 |
| **通用降解平台** | Round 2 纤维素风暴选 A | PTS + 表面展示的模块化：friskoli 的核心不是「一种菌吃掉一切」，而是降解产物必须能变成 PTS 趋化信号。几丁质方向最近（E. coli 编码 ChbBCA）；木质素/塑料/角蛋白则需要完全不同的信号输入设计。我们设想的不是万能菌，而是一组经过分别验证的 friskoli 变体 |
| **friskoli-Ω** | 集齐前四张 | 所有展望的组合：一台可在深空长期工作的活体反应器 |

---

## 设计原则 / Design Principles

### 诚实性承诺 / Honesty Commitment

本游戏遵循以下约束：

1. **用词谨慎**：游戏中使用条件语气——"似乎""看起来""数据显示可能"——而非断言。
2. **明确区分设计原理与未来展望**：friskoli 的设计原理（趋化、表面展示、趋化招募正反馈循环）在事件结果中直接生效——在 friskoli 该赢的地方大赢（事件 1、7、8、9、10），在没理由赢的地方坦然平庸（事件 3、4、5、6）。未实现的能力只出现在展望卡中，明确标注「我们尚未达到」。
3. **不下没有依据的结论**：丝状化？「FtsZ 装配紊乱不是工程改造能影响的事」。毒性？「毒物应激走 MCP 通路，friskoli 没动那一侧」。辐射？「它没死，但它不再是 friskoli」。
4. **没有错误答案**：每个选项都有代价。游戏不鼓励最优策略，鼓励玩家理解 trade-off。

### 叙事立场 / Narrative Stance

游戏不把自己定位为"模拟器"——它不声称准确模拟了微重力生物反应器的物理过程。它的定位是**互动叙事**：让你在 30 天的虚构航程中，感受工程迭代的逻辑、合成生物学的思维方式、以及"在微重力下搅拌可能是错误的问题"这一核心洞察。

The game does not position itself as a "simulator" — it does not claim to accurately model the physics of a microgravity bioreactor. It positions itself as **interactive narrative**: a 30-day fictional voyage that conveys the logic of engineering iteration, the mindset of synthetic biology, and the core insight that "in microgravity, stirring may be the wrong question."

---

## 技术实现 / Technical Implementation

- **平台**：单文件 HTML5 + CSS3 + Vanilla JavaScript
- **渲染**：SVG 动画反应器可视化 + Canvas 星空粒子背景
- **持久化**：localStorage / 可选云端存储，记录 friskoli 解锁状态
- **响应式**：适配 340px–1200px+ 视口
- **无外部依赖**：纯浏览器端运行

---

## Wiki 集成 / Wiki Integration

本游戏计划嵌入 friskoli 的 iGEM Wiki 的 Education & Communication 页面（或作为独立子页面）。嵌入方式：`<iframe>` 或直接托管在 iGEM GitLab Pages 上并通过 Wiki 链接。

游戏中的"科学注解"（Science Notes）与 Wiki 的 Design / Model / Engineering Success 页面交叉引用，形成闭环。

---

## 待商酌事项 / Items Pending Review

{{placeholder:game_review_items}}

待讨论的问题包括但不限于：
- HTML 游戏文件中 BioMicroStir → 趋化招募 / Chemotactic Recruitment Loop 的全文替换（约 7-8 处，详见 narrative-review.md）
- HTML 游戏文件中事件 1"10 公里 / 5 倍快"数字 → "几公里 / 约一个数量级"
- HTML 游戏文件中事件 8 Gobek et al. 2016 → Somavanshi et al. 2016, *PLoS Biology*
- 事件 3/4/5/6 的数值和叙事已在本设计文档中修正（friskoli 不再享有不应有的优势）——需同步至 HTML
- 展望卡 platform 的"漆酶/角蛋白酶"需限定在 PTS 耦合范围
- RecA 展望卡：辐射抗性写成多因素而非只靠 RecA
- PETase 展望卡：加"设想中 / 需要验证"
- 完美结局"优质生物质"→"可处理的菌体生物量 / 降解数据"
- 全员审核科学注解措辞

---

> **关联页面**: [Education & Communication](12-Education-Communication.md) · [Human Practices](11-Human-Practices.md) · [Proposed Implementation](14-Proposed-Implementation.md)
> **版本**: v3.1 · BUILD 2026.05
