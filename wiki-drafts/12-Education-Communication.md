# Education & Communication — friskoli

> **Team:** SZU-SIAT-China | **Track:** Space Track 2026 | **Section:** Education & Communication / 教育与传播

---

## 0. Table of Contents / 目录

| Section | English Title | 中文标题 |
|---------|--------------|----------|
| 1 | Overview: Why Education Matters | 概述：教育为何重要 |
| 2 | 12a: Chemotaxis Simulator — Learning by Seeing | 12a: 趋化性模拟器——通过视觉学习 |
| 3 | 12b: friskoli-I — Interactive Narrative Game | 12b: friskoli-I——互动叙事游戏 |
| 4 | Technical Architecture of the Simulator | 模拟器的技术架构 |
| 5 | Simulator Features and Use Cases | 模拟器功能与用例 |
| 6 | The Time Acceleration Anecdote — A Learning Moment | 时间加速器轶事——一个学习时刻 |
| 7 | Science Communication Strategy | 科学传播策略 |
| 8 | The "Finding Food" Narrative | "寻找食物"叙事 |
| 9 | Social Media and Digital Outreach | 社交媒体与数字传播 |
| 10 | Explainer Video Concept | 科普视频概念 |
| 11 | Planned Educational Activities | 计划中的教育活动 |
| 12 | Workshop and Event Plans | 工作坊与活动计划 |
| 13 | Collaborations with Other iGEM Teams | 与其他 iGEM 团队的合作 |
| 14 | Open Educational Resources | 开放教育资源 |
| 15 | Measuring Impact | 影响力评估 |
| 16 | Reflections and Lessons Learned | 反思与经验教训 |

---

## 1. Overview: Why Education Matters / 概述：教育为何重要

**English:**

Synthetic biology sits at an uncomfortable boundary between the familiar and the alien. On one hand, we are working with living cells — objects that every student has seen in a microscope, that every person intuitively recognizes as "alive." On the other hand, we are manipulating those cells at a molecular scale — swapping promoters, rewiring signaling pathways, redirecting metabolism — in ways that feel abstract, invisible, and frankly difficult to visualize.

For friskoli, this gap between the visible and the invisible is especially pronounced. Bacterial chemotaxis is a process that occurs at the nanoscale, involves phosphorylation cascades that nobody can see, and produces macroscopic effects (bacteria swimming toward food) only when thousands of cells are observed over minutes to hours. Explaining this to a non-specialist audience — or even to team members from different disciplines — is a genuine communication challenge.

Our approach to education and communication begins with a simple principle: **show, don't just tell.** When words fail, simulation succeeds. When a diagram is static, an interactive model can breathe. This page documents our educational and communication efforts — the tools we built, the stories we told, and the lessons we learned along the way.

**中文：**

合成生物学坐落在熟悉与陌生之间的一个令人不安的边界上。一方面，我们在与活细胞打交道——每个学生在显微镜下都见过的东西，每个人直觉上都认知为"活的"东西。另一方面，我们正在以分子尺度操纵这些细胞——交换启动子、重新布线信号通路、重定向代谢——以一种感觉抽象、不可见、且坦白说很难可视化的方式进行。

对于 friskoli 而言，可见与不可见之间的这条鸿沟尤为显著。细菌趋化性是一个发生在纳米尺度上的过程，涉及无人能见的磷酸化级联反应，只有当成千上万个细胞在数分钟到数小时内被观察时才会产生宏观效应（细菌游向食物）。向非专业受众——甚至向来自不同学科的团队成员——解释这一点，是一个真正的沟通挑战。

我们的教育与传播方法始于一个简单的原则：**展示，而非仅仅讲述。** 当语言不够用时，模拟能够成功。当图表是静态的时，交互式模型能够呼吸。本页面记录了我们的教育和传播努力——我们构建的工具、讲述的故事以及一路学到的经验。

---

## 2. 12a: The Chemotaxis Simulator — Learning by Seeing / 12a: 趋化性模拟器——通过视觉学习

**English:**

### 2.1 The Problem That Drove Us to Build

In the early weeks of the friskoli project, we encountered a persistent communication problem. Our modeling team understood the Barkai-Leibler equations and could talk fluently about CheA autophosphorylation rates. Our wet-lab team understood the asc operon and could describe how AscF transports cellobiose. But when it came time to explain to the rest of the team — and to ourselves — what the *combined* system would actually look like at the population level, we had nothing but words and equations.

"How fast would the bacteria swim toward the cellulose?"

"What does 'chemotactic aggregation' actually look like?"

"If we increase AscF expression, does the effect saturate, or does it keep getting stronger?"

"What difference does gravity make — really?"

These were not questions that a static diagram could answer. They demanded a dynamic, visual, interactive representation. So our modeling team built one.

### 2.2 The Simulator Concept

The friskoli Chemotaxis Simulator is an interactive, web-based tool that visualizes bacterial chemotaxis toward cellulose in both 1g and microgravity conditions. It is designed to be embedded directly in the iGEM wiki, accessible to anyone with a web browser — no installation, no coding required.

The simulator shows:

- **Individual bacteria** as motile agents displaying run-and-tumble behavior
- **Cellulose fibers** as distributed substrate sources that release cellobiose
- **Chemoattractant gradients** as color-coded concentration fields
- **Swimming trajectories** as visible trails showing biased random walks
- **Degradation zones** where bacteria have reached and are breaking down cellulose

### 2.3 What the Simulator Teaches

The educational value of the simulator lies in its ability to make abstract concepts tangible:

| Concept | How the Simulator Makes It Visible |
|---------|-----------------------------------|
| **Run-and-tumble motility** | Bacteria alternate between straight runs (visible as directed line segments) and tumbles (visible as random reorientations) |
| **Chemotactic bias** | In the presence of a cellobiose gradient, run lengths become visibly longer when swimming up-gradient |
| **Adaptation** | Over time, the bias adjusts — the bacteria do not stay "locked on" to the gradient but adapt and re-sample |
| **Diffusion limitation** | In the 0g mode, color gradients spread slowly, making it visually obvious why passive diffusion fails |
| **Surface aggregation** | Engineered bacteria visibly accumulate around cellulose sources while wild-type bacteria remain dispersed |
| **Saturation effects** | Users can adjust AscF expression level and observe that beyond a certain point, aggregation no longer improves |
| **Speed of response** | The time course of aggregation (minutes to hours) becomes intuitively graspable |

**中文：**

### 2.1 推动我们构建的问题

在 friskoli 项目的最初几周，我们遇到了一个持续的沟通问题。我们的建模团队理解 Barkai-Leibler 方程，能够流利地讨论 CheA 自磷酸化速率。我们的湿实验团队理解 asc 操纵子，能够描述 AscF 如何运输纤维二糖。但是当需要向团队其他成员——以及向自己——解释*组合*系统在群体水平上会是什么样子时，我们除了文字和方程外什么都没有。

"细菌游向纤维素的速度有多快？"

"'趋化性聚集'实际上看起来是什么样子？"

"如果我们增加 AscF 表达，效果会饱和，还是会持续增强？"

"重力到底有什么不同——真正的影响是什么？"

这些不是静态图表能够回答的问题。它们要求一种动态的、视觉化的、互动式的呈现。所以我们的建模团队构建了这样一个工具。

### 2.2 模拟器概念

friskoli 趋化性模拟器是一个交互式、基于网络的工具，可视化展示细菌在 1g 和微重力条件下朝向纤维素的趋化行为。它被设计为可直接嵌入 iGEM Wiki，任何有网页浏览器的人都可以访问——无需安装，无需编程。

模拟器展示：

- **单个细菌**作为展示 run-and-tumble 行为的运动智能体
- **纤维素纤维**作为释放纤维二糖的分布底物源
- **化学吸引物梯度**作为色彩编码的浓度场
- **游泳轨迹**作为显示偏向随机游走的可见路径
- **降解区域**其中细菌已到达并正在分解纤维素

### 2.3 模拟器教什么

模拟器的教育价值在于其将抽象概念变为具体可感的能力：

| 概念 | 模拟器如何使其可见 |
|------|------------------|
| **Run-and-tumble 运动** | 细菌在直线奔跑（可见为定向线段）和翻转（可见为随机重定向）之间交替 |
| **趋化偏向** | 在纤维二糖梯度的存在下，向上游梯度游泳时奔跑长度可见延长 |
| **适应** | 随着时间推移，偏向调整——细菌不会保持"锁定"在梯度上，而是适应并重新采样 |
| **扩散限制** | 在 0g 模式下，颜色梯度缓慢扩散，使被动扩散为何失败在视觉上显而易见 |
| **表面聚集** | 工程化细菌在纤维素源周围可见地聚集，而野生型细菌保持分散 |
| **饱和效应** | 用户可以调整 AscF 表达水平，观察超越某一点后聚集不再改善 |
| **响应速度** | 聚集的时间过程（数分钟到数小时）变得直观可感 |

---

## 3. 12b: friskoli-I · 月轨三十日 — 互动叙事游戏 / 12b: Interactive Narrative Game

> **📄 完整设计文档**：[`12b-Friskoli-I-Game.md`](12b-Friskoli-I-Game.md) — 内容仍在团队内部商酌中。

我们教育传播工作的核心交付物是一部名为 **friskoli-I** 的互动叙事游戏。玩家扮演月轨任务中的生物系统技术员，在 30 天的航程中管理一台搭载工程菌的生物反应器。游戏通过双轮结构（第一轮带普通菌、第二轮带 friskoli）传达工程迭代的核心逻辑——不是被告知"friskoli 更好"，而是自己发现它在哪里更好、在哪里也同样无力。

游戏包含 10 个事件、5 张未来展望卡、以及全程双语科学注解。详见独立设计文档。

The centerpiece of our education and communication work is an interactive narrative game called **friskoli-I**. The player assumes the role of a biosystem technician on a lunar orbit mission, managing a bioreactor over 30 days. Through a two-round structure (Round 1 with normal E. coli, Round 2 with friskoli), the game conveys the core logic of engineering iteration — not telling the player "friskoli is better," but letting them discover where it excels and where it is equally powerless.

The game contains 10 events, 5 future vision cards, and bilingual science notes throughout. See the standalone design document for details.

---

## 4. Technical Architecture of the Simulator / 模拟器的技术架构

**English:**

### 3.1 Design Philosophy

The simulator was built with three priorities:

1. **Accuracy to the biology:** The underlying model respects the Barkai-Leibler robust adaptation framework and uses experimentally measured parameters (swimming speed ~25 μm/s, run duration distribution from Berg & Brown 1972).
2. **Accessibility to the non-specialist:** The interface uses intuitive controls (sliders, toggles, dropdown menus) rather than requiring parameter files or code. Visual design prioritizes clarity over photorealism.
3. **Embeddability in the wiki:** The simulator is built as a self-contained web component that can be iframe-embedded into the iGEM wiki without dependencies on external servers or databases.

### 3.2 Technical Stack

| Component | Technology | Rationale |
|-----------|-----------|-----------|
| **Simulation engine** | JavaScript / WebAssembly | Runs in-browser; no server required |
| **Rendering** | HTML5 Canvas or WebGL | Hardware-accelerated graphics for smooth animation of thousands of agents |
| **UI controls** | Vanilla JS + CSS | Minimal dependencies; fast loading |
| **Deployment** | Static HTML/CSS/JS bundle | Can be served from any static host or embedded as iframe |
| **Responsive design** | CSS Grid / Flexbox | Works on desktop, tablet, and mobile |

### 3.3 Agent-Based Model Overview

Each bacterium is represented as an autonomous agent with:

- **Position** (x, y in 2D cross-section of the bioreactor)
- **Velocity vector** (magnitude drawn from Berg & Brown speed distribution)
- **Internal state** (CheA activity, CheY-P level, adaptation level — implementing the Barkai-Leibler model in simplified form)
- **Cellobiose sensing** (local concentration sampled at agent position + Gaussian noise)

The environment consists of:

- **Cellobiose field** — a diffusion grid updated via finite-difference solution of the diffusion equation
- **Cellulose sources** — fixed regions that degrade over time proportional to bacterial contact
- **Boundary conditions** — reflecting walls (bioreactor vessel)

Gravity effect is modeled by adding a convective term to the diffusion equation in 1g mode (small but non-zero drift) and removing it in 0g mode (pure diffusion).

### 3.4 Open Source

The complete source code of the simulator is available at {{placeholder:simulator_repo_url}}. We release it under an open-source license (MIT) so that future iGEM teams and educators can adapt, improve, and reuse it for their own chemotaxis or agent-based modeling projects.

**中文：**

### 3.1 设计理念

模拟器围绕三个优先级构建：

1. **对生物学的准确性：** 底层模型遵循 Barkai-Leibler 鲁棒适应框架，并使用实验测量的参数（游泳速度约 25 μm/s，run 持续时间分布来自 Berg & Brown 1972）。
2. **对非专业人士的可及性：** 界面使用直观的控件（滑块、开关、下拉菜单），无需参数文件或代码。视觉设计优先考虑清晰性而非真实感。
3. **在 Wiki 中的可嵌入性：** 模拟器作为自包含网页组件构建，可通过 iframe 嵌入 iGEM Wiki，无需依赖外部服务器或数据库。

### 3.2 技术栈

| 组件 | 技术 | 理由 |
|------|------|------|
| **模拟引擎** | JavaScript / WebAssembly | 在浏览器内运行；无需服务器 |
| **渲染** | HTML5 Canvas 或 WebGL | 硬件加速图形，实现数千个智能体的流畅动画 |
| **用户界面控件** | 原生 JS + CSS | 最小依赖；加载迅速 |
| **部署** | 静态 HTML/CSS/JS 包 | 可从任何静态主机提供服务或作为 iframe 嵌入 |
| **响应式设计** | CSS Grid / Flexbox | 适用于桌面、平板和手机 |

### 3.3 基于智能体的模型概述

每个细菌被表示为一个自主智能体，具有：

- **位置**（生物反应器 2D 横截面中的 x, y）
- **速度向量**（大小取自 Berg & Brown 速度分布）
- **内部状态**（CheA 活性、CheY-P 水平、适应水平——以简化形式实现 Barkai-Leibler 模型）
- **纤维二糖感知**（在智能体位置采样的局部浓度 + 高斯噪声）

环境包括：

- **纤维二糖场**——通过扩散方程的有限差分解更新的扩散网格
- **纤维素源**——随时间降解的固定区域，降解速率与细菌接触成正比
- **边界条件**——反射壁（生物反应器容器）

重力效应通过在 1g 模式下向扩散方程添加对流项（小但非零的漂移）并在 0g 模式下去除它（纯扩散）来建模。

### 3.4 开源

模拟器的完整源代码可在 {{placeholder:simulator_repo_url}} 获取。我们以开源许可（MIT）发布，以便未来的 iGEM 团队和教育者可以适配、改进并重用于他们自己的趋化性或基于智能体的建模项目。

---

## 5. Simulator Features and Use Cases / 模拟器功能与用例

**English:**

### 4.1 Core Features

| Feature | Description | Educational Purpose |
|---------|-------------|---------------------|
| **Strain Selector** | Toggle between wild-type, ΔcheA (chemotaxis-deficient), ascF-engineered, and ascF+INP-cellulase | Compare behaviors; understand which genetic changes produce which effects |
| **Gravity Toggle** | Switch between 1g (Earth) and 0g (microgravity) | Visualize the convection/diffusion difference |
| **AscF Expression Slider** | Adjust expression level from 0% to 200% of native promoter strength | Explore saturation and optimal expression |
| **Time Controls** | Play, pause, speed up (2x, 5x, 10x, 100x) | Watch slow processes unfold; connect real time to simulation time |
| **Data Overlay** | Toggle concentration field, velocity vectors, or degradation heatmap | See the "invisible" variables |
| **Export Frame** | Save current view as PNG for presentations | Support communication beyond the wiki |

### 4.2 Use Cases

**For team members:**
- Build intuition about how chemotaxis works before designing experiments
- Test hypotheses about expression level optimization
- Prepare figures and animations for presentations

**For other iGEM teams:**
- Learn about chemotaxis as a chassis behavior
- Adapt the agent-based model for their own projects (different chemotactic systems, different substrates)
- Use as a template for building their own educational simulators

**For educators:**
- Demonstrate bacterial behavior in classroom settings without requiring lab equipment
- Introduce concepts of diffusion, gradient sensing, and adaptation interactively
- Connect molecular biology (signaling pathways) to population-level phenomena

**For the general public:**
- Make the invisible world of bacterial behavior visible and engaging
- Provide an intuitive understanding of why microgravity matters for biology
- Spark curiosity about synthetic biology and space research

**中文：**

### 4.1 核心功能

| 功能 | 描述 | 教育目的 |
|------|------|---------|
| **菌株选择器** | 在野生型、ΔcheA（趋化性缺陷型）、ascF 工程化型和 ascF+INP-纤维素酶型之间切换 | 比较行为；理解哪些遗传改变产生哪些效果 |
| **重力开关** | 在 1g（地球）和 0g（微重力）之间切换 | 可视化对流/扩散差异 |
| **AscF 表达滑块** | 将表达水平从天然启动子强度的 0% 调整至 200% | 探索饱和与最优表达 |
| **时间控制** | 播放、暂停、加速（2x、5x、10x、100x）| 观察缓慢过程的展开；将真实时间与模拟时间相联系 |
| **数据叠加** | 切换浓度场、速度向量或降解热力图 | 看到"不可见"的变量 |
| **导出帧** | 将当前视图保存为 PNG 用于展示 | 支持 Wiki 之外的传播 |

### 4.2 用例

**对于团队成员：**
- 在设计实验之前建立对趋化性如何工作的直觉
- 测试关于表达水平优化的假设
- 为展示准备图表和动画

**对于其他 iGEM 团队：**
- 了解趋化性作为一种底盘行为
- 为自己的项目（不同的趋化系统、不同的底物）适配基于智能体的模型
- 将其用作构建自己的教育模拟器的模板

**对于教育者：**
- 在课堂环境中展示细菌行为而无需实验设备
- 互动式引入扩散、梯度感应和适应概念
- 将分子生物学（信号通路）与群体水平现象联系起来

**对于公众：**
- 使细菌行为这一不可见的世界变得可见且引人入胜
- 提供为什么微重力对生物学重要的直观理解
- 激发对合成生物学和空间研究的好奇心

---

## 6. The Time Acceleration Anecdote — A Learning Moment / 时间加速器轶事——一个学习时刻

**English:**

Every iGEM project has moments that seem, in retrospect, almost comically instructive. Ours came during the first test run of the chemotaxis simulator.

Our modeling manager had spent several days implementing the agent-based model. The bacteria moved. The gradients diffused. The cellulose degraded. Everything looked correct. So we set up a simulation scenario — engineered bacteria, cellulose source, 0g conditions — and pressed "Run."

And waited.

And waited.

After about five minutes, someone asked: "How long is this supposed to take?"

The modeling manager checked the parameters. The simulation was set to cover 30 minutes of simulated biological time. Running at approximately one-to-one wall-clock speed.

There was a pause. Then someone said: "So... it will take 30 actual minutes to see what happens after 30 simulated minutes?"

The modeling manager had forgotten to set the time acceleration ratio. The simulation was running in real time.

We laughed — at ourselves, not at the mistake. But then something interesting happened. We realized that this "mistake" was actually illuminating. Thirty minutes of real time to simulate thirty minutes of bacterial behavior is only absurd in a computational context. But for the actual bacteria in an actual bioreactor, thirty minutes *is* thirty minutes. The fact that it felt unbearably slow to us — staring at a screen, waiting for pixels to move — was itself a lesson about the timescale of biological processes.

This became a teaching moment that we have shared in every presentation and workshop since. The anecdote does several things at once:

1. **It humanizes the team.** We made a mistake. It was funny. We admit it.
2. **It teaches a real concept.** The relationship between simulation time and real time is not trivial — it is central to understanding what models can and cannot do.
3. **It connects scale.** Thirty minutes feels like nothing in a laboratory experiment (you set up the culture, you go get coffee, you come back). But in a simulation where you are *actively watching*, it feels like an eternity. This contrast helps audiences understand why computational models need to run faster than reality — and why biological processes that seem "slow" are actually remarkably efficient given the physical constraints.

We have since, of course, implemented proper time acceleration (1x, 2x, 5x, 10x, 100x, and "as fast as possible"). But we kept the "real time" mode as an option — labeled with a small note: "This is how long the bacteria actually need."

**中文：**

每个 iGEM 项目都有一些事后回想起来几乎滑稽但极具启发性的时刻。我们的时刻出现在趋化性模拟器的第一次试运行中。

我们的建模经理花了几天时间实现了基于智能体的模型。细菌移动了。梯度扩散了。纤维素降解了。一切看起来都正确。于是我们设置了一个模拟场景——工程化细菌、纤维素源、0g 条件——然后按下了"运行"。

然后等。

继续等。

大约五分钟后，有人问："这需要多长时间？"

建模经理检查了参数。模拟被设定为覆盖 30 分钟的模拟生物时间。以大约一比一的挂钟速度运行。

一阵沉默。然后有人说："所以……要看到 30 分钟模拟时间后的结果，需要实际 30 分钟？"

建模经理忘了设置时间加速比。模拟正在实时运行。

我们笑了——笑自己，而非笑错误。但随后发生了一些有趣的事情。我们意识到这个"错误"实际上很有启发性。用三十分钟的真实时间去模拟三十分钟的细菌行为，只有在计算语境下才是荒谬的。但对于实际生物反应器中的实际细菌来说，三十分钟*就是*三十分钟。这件事对我们来说——盯着屏幕、等待像素移动——感到难以忍受地缓慢，本身就是一堂关于生物过程时间尺度的课。

这成为了一个教学时刻，我们从那时起在每次展示和工作坊中分享。这个轶事同时实现了几个目的：

1. **使团队人性化。** 我们犯了一个错误。这很好笑。我们承认它。
2. **它教了一个真正的概念。** 模拟时间与真实时间之间的关系不是微不足道的——它是理解模型能做什么和不能做什么的核心。
3. **它连接了尺度。** 在实验室实验中，三十分钟感觉不算什么（设置好培养，去喝杯咖啡，回来）。但在你*主动观看*的模拟中，它感觉像是永恒。这种对比帮助受众理解为什么计算模型需要比现实运行得更快——以及为什么看起来"缓慢"的生物过程在物理约束下实际上是相当高效的。

此后我们当然实现了合适的时间加速（1x、2x、5x、10x、100x 以及"尽可能快"）。但我们保留了"实时"模式作为一个选项——标注了一行小字："这是细菌实际需要的时间。"

---

## 7. Science Communication Strategy / 科学传播策略

**English:**

### 7.1 Communication as Translation

Science communication for friskoli operates on the principle of translation — not simplification. We do not believe that public audiences need to be shielded from complexity. They need complexity to be translated into a language they can access. The difference is crucial: simplification removes content; translation preserves content while changing its form.

Our communication strategy rests on three pillars:

1. **Narrative:** Every scientific concept is embedded in a story. People remember stories; they forget facts presented in isolation.
2. **Visualization:** The chemotaxis simulator, diagrams, animations — seeing is understanding.
3. **Interaction:** We do not broadcast; we invite participation. The simulator is interactive. Social media is conversational. Workshops are collaborative.

### 7.2 Audience Segments

| Audience | What They Need | How We Communicate |
|----------|---------------|-------------------|
| **Fellow iGEMers and synthetic biologists** | Technical depth, reproducibility | Wiki, Model page, GitHub repository, Jamboree presentation |
| **Undergraduate biology students** | Conceptual clarity, connection to curriculum | Simulator, explainer videos, classroom workshops |
| **High school students** | Inspiration, basic concepts, excitement | Simulator (guided mode), social media, school visits |
| **General public** | Why it matters, what it means | Social media, "Finding Food" narrative, short videos |
| **Space community** | Technical credibility, relevance to mission | Expert interviews, white paper, conference abstract |
| **Chinese-language audiences** | Fully equivalent content in Chinese | All materials are bilingual; Chinese social media (WeChat, Bilibili) |

**中文：**

### 7.1 作为翻译的传播

friskoli 的科学传播基于翻译原则——而非简化。我们不认为公众受众需要被屏蔽复杂度。他们需要复杂度被翻译成一种他们可以理解的语言。这种区别至关重要：简化移除内容；翻译在保留内容的同时改变其形式。

我们的传播策略建立在三个支柱上：

1. **叙事：** 每个科学概念都嵌入一个故事中。人们记住故事；他们忘记孤立呈现的事实。
2. **可视化：** 趋化性模拟器、图表、动画——看见即是理解。
3. **互动：** 我们不广播；我们邀请参与。模拟器是互动的。社交媒体是对话式的。工作坊是协作性的。

### 7.2 受众细分

| 受众 | 他们需要什么 | 我们如何传播 |
|------|------------|------------|
| **iGEM 同仁及合成生物学家** | 技术深度、可重复性 | Wiki、模型页面、GitHub 仓库、Jamboree 展示 |
| **本科生生物学生** | 概念清晰、与课程关联 | 模拟器、科普视频、课堂工作坊 |
| **高中生** | 启发、基本概念、兴奋感 | 模拟器（引导模式）、社交媒体、学校访问 |
| **公众** | 为什么重要、意味着什么 | 社交媒体、"寻找食物"叙事、短视频 |
| **航天社群** | 技术可信度、与任务的相关性 | 专家访谈、白皮书、会议摘要 |
| **中文受众** | 完全对等的中文内容 | 所有材料均为双语；使用中国社交媒体（微信、B站）|

---

## 8. The "Finding Food" Narrative / "寻找食物"叙事

**English:**

### 8.1 The Narrative Hook

We have found that the most effective public engagement hook for friskoli is a simple, relatable question:

> **"In a world without gravity — without up or down, without floating or sinking — how would you find your next meal?"**

This question works because it is:

- **Immediately graspable.** Everyone understands hunger. Everyone understands the challenge of finding food.
- **Physically intuitive.** The absence of gravity is imaginable (if not directly experienced). The idea that "things don't float to the top or sink to the bottom" connects to common knowledge.
- **Scale-transcending.** The question applies equally to an astronaut on a space station (where does the food come from?) and a bacterium in a bioreactor (where does the cellobiose come from?).
- **Emotionally engaging.** It frames the problem not as an abstract engineering challenge but as a fundamentally biological one — the ancient, universal problem of finding sustenance.

### 8.2 The Narrative Arc

The core narrative we communicate to public audiences follows this arc:

1. **The familiar:** On Earth, finding food is easy. It floats, it sinks, it mixes. Gravity does the work.
2. **The unfamiliar:** In space, gravity is gone. Food doesn't come to you. You have to go to it.
3. **The microbial parallel:** Bacteria face the same problem. In a bioreactor on Earth, gravity stirs their world. In space, they sit in a still pool of their own waste, starving next to a mountain of food just millimeters away.
4. **The engineering intervention:** What if we gave bacteria a "nose" for their food? What if we taught them to swim toward it?
5. **The payoff:** A bioreactor where the bacteria go and find their food — no motors, no paddles, just millions of tiny swimmers locating cellulose by smell and degrading it on contact.

This narrative has tested well in informal conversations with non-scientist friends and family. It will form the backbone of our social media content and explainer videos.

**中文：**

### 8.1 叙事钩子

我们发现，friskoli 最有效的公众参与钩子是一个简单的、能引起共鸣的问题：

> **"在一个没有重力的世界——没有上下、没有沉浮——你将如何找到你的下一顿饭？"**

这个问题有效是因为它：

- **即刻可理解。** 每个人都理解饥饿。每个人都理解寻找食物的挑战。
- **物理上直观。** 重力的缺失是可以想象的（即使没有直接体验）。"东西不会浮到顶部或沉到底部"这个概念与常识相连接。
- **超越尺度。** 这个问题同样适用于空间站的宇航员（食物从哪里来？）和生物反应器中的细菌（纤维二糖从哪里来？）。
- **情感上引人入胜。** 它把问题框定为一个根本的生物学问题——而非一个抽象的工程挑战——那个古老而普遍的求食问题。

### 8.2 叙事弧

我们向公众受众传播的核心叙事遵循以下弧线：

1. **熟悉之物：** 在地球上，寻找食物很容易。食物漂浮、沉降、混合。重力做了这项工作。
2. **陌生之境：** 在太空中，重力不见了。食物不会来找你。你必须去找它。
3. **微生物的平行：** 细菌面临同样的问题。在地球上的生物反应器中，重力搅动着它们的世界。在太空中，它们栖息在自己排泄物的静止池中，在仅数毫米外堆积如山的食物旁挨饿。
4. **工程干预：** 如果我们给细菌一个"鼻子"来嗅闻食物呢？如果我们教会它们游向食物呢？
5. **回报：** 一个细菌主动去找食物的生物反应器——没有电机，没有桨叶，只有数百万个微小的游泳者通过嗅闻定位纤维素并就地降解。

这一叙事在与非科学家朋友和家人的非正式对话中测试效果良好。它将构成我们社交媒体内容和科普视频的骨干。

---

## 9. Social Media and Digital Outreach / 社交媒体与数字传播

**English:**

### 9.1 Platform Strategy

| Platform | Audience | Content Type | Frequency |
|----------|---------|-------------|-----------|
| **WeChat (微信)** | Chinese academic community, peers, families | Behind-the-scenes lab photos, team updates, Chinese-language explainers | Weekly |
| **Bilibili (哔哩哔哩)** | Chinese students, science enthusiasts | Explainer videos, simulator demos, lab vlogs | Bi-weekly |
| **Twitter/X** | International iGEM community, synthetic biology researchers | Project updates, literature highlights, simulator demos | 2-3x/week |
| **Instagram** | International students, general public | Visual content: microscopy images, simulator screenshots, team photos | Weekly |
| **GitHub** | Developers, computational biologists, other iGEM teams | Simulator source code, model documentation, issue tracking | As needed |

### 9.2 Content Calendar (Planned)

| Month | Theme | Key Content |
|-------|-------|-------------|
| **March–April 2026** | "Getting Started" | Team formation, project ideation, the Space Track decision |
| **May–June 2026** | "Deep Dive" | asc operon explainer, PTS chemotaxis mechanism, simulator launch |
| **July–August 2026** | "Lab Life" | Experimental progress, protocols, troubleshooting, team behind-the-scenes |
| **September 2026** | "Results & Reflection" | Key findings, Human Practices insights, simulator user stories |
| **October 2026** | "Countdown to Jamboree" | Presentation prep, project summary, thank-you to supporters |

**中文：**

### 9.1 平台策略

| 平台 | 受众 | 内容类型 | 频率 |
|------|------|---------|------|
| **微信** | 中国学术界、同行、家人 | 实验室幕后照片、团队更新、中文科普 | 每周 |
| **哔哩哔哩** | 中国学生、科学爱好者 | 科普视频、模拟器演示、实验室 vlog | 每两周 |
| **Twitter/X** | 国际 iGEM 社群、合成生物研究者 | 项目更新、文献亮点、模拟器演示 | 每周 2-3 次 |
| **Instagram** | 国际学生、公众 | 视觉内容：显微图像、模拟器截图、团队照片 | 每周 |
| **GitHub** | 开发者、计算生物学家、其他 iGEM 团队 | 模拟器源代码、模型文档、问题跟踪 | 按需 |

### 9.2 内容日程（计划）

| 月份 | 主题 | 主要内容 |
|------|------|---------|
| **2026 年 3-4 月** | "起步" | 团队组建、项目构思、太空赛道选择 |
| **2026 年 5-6 月** | "深入" | asc 操纵子科普、PTS 趋化机制、模拟器发布 |
| **2026 年 7-8 月** | "实验室生活" | 实验进展、方案、排错、团队幕后 |
| **2026 年 9 月** | "成果与反思" | 关键发现、人类实践洞察、模拟器用户故事 |
| **2026 年 10 月** | "Jamboree 倒计时" | 展示准备、项目总结、致谢支持者 |

---

## 10. Explainer Video Concept / 科普视频概念

**English:**

We are planning a short (3–5 minute) animated explainer video that communicates the core friskoli concept to a general audience. The video will follow the "Finding Food" narrative arc and use a visual style consistent with our wiki design.

**Planned structure:**

| Scene | Duration | Content | Visual Style |
|-------|----------|---------|-------------|
| 1. Earth vs. Space | 0:30 | Side-by-side: tea leaves sinking in a cup (Earth) vs. tea leaves suspended in a droplet (space) | Clean vector animation |
| 2. The Bacterial Problem | 0:45 | A single bacterium in a depletion zone, showing the ~5 mm radius | Microscopic-scale rendering |
| 3. The asc Operon | 1:00 | Molecular animation: AscF transporter, CheA signaling, flagellar motor | Simplified molecular visualization |
| 4. The Feedback Loop | 0:45 | Bacteria → cellulose → cellobiose → more bacteria (cyclic diagram coming to life) | Animated flowchart becoming a scene |
| 5. Functional Equivalence | 0:30 | Side-by-side: traditional bioreactor with stirrer vs. friskoli bioreactor with swimming bacteria — same outcome, different mechanism | Schematic comparison |
| 6. The Vision | 0:30 | A space habitat with a bioreactor module, Earth in the background | Inspirational wide shot |

**Production status:** {{placeholder:video_production_status}}

**中文：**

我们计划制作一个简短（3-5 分钟）的动画科普视频，向公众受众传达 friskoli 的核心概念。视频将遵循"寻找食物"叙事弧，使用与我们的 Wiki 设计一致的视觉风格。

**计划结构：**

| 场景 | 时长 | 内容 | 视觉风格 |
|------|------|------|---------|
| 1. 地球 vs. 太空 | 0:30 | 并排对比：茶叶在杯中下沉（地球）vs. 茶叶悬浮在液滴中（太空）| 清晰矢量动画 |
| 2. 细菌的困境 | 0:45 | 耗尽区中的单个细菌，展示约 5 mm 半径 | 微观尺度渲染 |
| 3. asc 操纵子 | 1:00 | 分子动画：AscF 转运蛋白、CheA 信号、鞭毛马达 | 简化的分子可视化 |
| 4. 反馈循环 | 0:45 | 细菌 → 纤维素 → 纤维二糖 → 更多细菌（循环图生动起来）| 动画流程图变为场景 |
| 5. 功能等效性 | 0:30 | 并排对比：传统带搅拌器的生物反应器 vs. 带游泳细菌的 friskoli 生物反应器——相同的结果，不同的机制 | 示意图比较 |
| 6. 愿景 | 0:30 | 带生物反应器模块的空间栖息地，背景中的地球 | 鼓舞人心的广角镜头 |

**制作状态：** {{placeholder:video_production_status}}

---

## 11. Planned Educational Activities / 计划中的教育活动

**English:**

Our educational activities are designed to reach different age groups and knowledge levels, always using the simulator as the central interactive element.

### 11.1 University-Level Activities

- **Department seminars** at Shenzhen University and SIAT: Presenting friskoli as a case study in synthetic biology design-build-test-learn cycles.
- **Interdisciplinary workshops** connecting biology students with engineering and computer science students: The simulator as a meeting point — biology students explain the model, CS students explain the implementation.
- **iGEM information sessions** for prospective future team members: Using friskoli as an example of what a first-year team can accomplish.

### 11.2 High School Outreach

- **"Bacteria in Space" classroom workshops:** A 45-minute session including:
  - A 10-minute interactive demonstration using the simulator
  - A 15-minute hands-on activity (simulating diffusion with food coloring in water vs. gel)
  - A 20-minute discussion: "What would YOU engineer bacteria to do in space?"
- **Science fair mentorship:** Supporting high school students interested in synthetic biology projects.

### 11.3 Public Events

- **Open Day demonstrations** at Shenzhen University: Simulator kiosk with team members explaining the science.
- **Science museum collaboration:** Exploring placement of the simulator as an interactive exhibit ({{placeholder:museum_collaboration_status}}).

**中文：**

我们的教育活动旨在覆盖不同年龄段和知识水平，始终以模拟器作为核心互动元素。

### 11.1 大学层面活动

- **深圳大学和 SIAT 的系内研讨会：** 将 friskoli 作为合成生物学设计-构建-测试-学习周期的案例研究进行展示。
- **跨学科工作坊**连接生物专业学生与工程和计算机科学学生：模拟器作为交汇点——生物学生解释模型，CS 学生解释实现。
- **iGEM 宣讲会**面向未来的潜在团队成员：以 friskoli 为范例说明首年团队能够达成的成就。

### 11.2 高中外展

- **"太空中的细菌"课堂工作坊：** 一个 45 分钟的课程，包括：
  - 10 分钟使用模拟器的互动演示
  - 15 分钟动手活动（用水和凝胶中的食用色素模拟扩散）
  - 20 分钟讨论："你会工程改造细菌在太空中做什么？"
- **科学展指导：** 支持对合成生物学项目感兴趣的高中生。

### 11.3 公共活动

- **深圳大学开放日演示：** 模拟器互动站，团队成员讲解科学原理。
- **科学馆合作：** 探索将模拟器作为互动展品进行布置（{{placeholder:museum_collaboration_status}}）。

---

## 12. Workshop and Event Plans / 工作坊与活动计划

**English:**

{{placeholder:workshops_events}}

**Planned workshop structure (template):**

| Workshop Element | Duration | Activity |
|-----------------|----------|----------|
| **Introduction** | 10 min | "Finding Food in Space" — the core narrative |
| **Simulator Demo** | 15 min | Guided exploration: wild-type vs. engineered, 1g vs. 0g |
| **Hands-on Activity** | 20 min | Participants design their own "what-if" scenarios and test them |
| **Discussion** | 15 min | Results sharing, Q&A, "what would you engineer?" brainstorm |

**中文：**

{{placeholder:workshops_events}}

**计划工作坊结构（模板）：**

| 工作坊要素 | 时长 | 活动 |
|-----------|------|------|
| **导论** | 10 分钟 | "在太空中寻找食物"——核心叙事 |
| **模拟器演示** | 15 分钟 | 引导式探索：野生型 vs. 工程化、1g vs. 0g |
| **动手活动** | 20 分钟 | 参与者设计自己的"如果……会怎样"场景并测试 |
| **讨论** | 15 分钟 | 结果分享、问答、"你会工程改造什么？"头脑风暴 |

---

## 13. Collaborations with Other iGEM Teams / 与其他 iGEM 团队的合作

**English:**

We are actively seeking educational collaborations with other iGEM teams, particularly:

- **Teams working on chemotaxis:** Joint workshops comparing different chemotactic systems.
- **Teams in the Space Track:** A shared "Space Synthetic Biology" educational package that aggregates multiple projects' educational tools.
- **Teams with complementary modeling projects:** Cross-testing each other's simulators and providing user feedback.
- **Teams in China:** Joint outreach events, shared Chinese-language educational content.

**Current collaboration status:** {{placeholder:team_collaborations}}

**中文：**

我们正在积极寻求与其他 iGEM 团队的教育合作，特别是：

- **从事趋化性研究的团队：** 比较不同趋化系统的联合工作坊。
- **太空赛道团队：** 一个共享的"太空合成生物学"教育包，聚合多个项目的教育工具。
- **具有互补建模项目的团队：** 交叉测试彼此的模拟器并提供用户反馈。
- **中国地区的团队：** 联合外展活动、共享的中文教育内容。

**当前合作状态：** {{placeholder:team_collaborations}}

---

## 14. Open Educational Resources / 开放教育资源

**English:**

We are committed to making our educational materials freely available beyond the iGEM competition cycle. Our open educational resources include:

| Resource | Format | License | Status |
|----------|--------|---------|--------|
| **Chemotaxis Simulator** | Web application (HTML/CSS/JS) | MIT License | {{placeholder:simulator_status}} |
| **Simulator User Guide** | PDF + Wiki page (bilingual) | CC BY 4.0 | In progress |
| **Classroom Workshop Kit** | Slide deck + activity instructions (bilingual) | CC BY 4.0 | {{placeholder:workshop_kit_status}} |
| **"Finding Food in Space" Explainer** | Short video + script (bilingual) | CC BY 4.0 | {{placeholder:video_status}} |
| **Model Documentation** | Jupyter notebooks + equations | MIT License | In progress |

**中文：**

我们致力于在 iGEM 竞赛周期之外免费提供我们的教育材料。我们的开放教育资源包括：

| 资源 | 格式 | 许可 | 状态 |
|------|------|------|------|
| **趋化性模拟器** | 网页应用（HTML/CSS/JS）| MIT 许可 | {{placeholder:simulator_status}} |
| **模拟器用户指南** | PDF + Wiki 页面（双语）| CC BY 4.0 | 进行中 |
| **课堂工作坊套件** | 幻灯片 + 活动说明（双语）| CC BY 4.0 | {{placeholder:workshop_kit_status}} |
| **"在太空中寻找食物"科普** | 短视频 + 脚本（双语）| CC BY 4.0 | {{placeholder:video_status}} |
| **模型文档** | Jupyter notebooks + 方程 | MIT 许可 | 进行中 |

---

## 15. Measuring Impact / 影响力评估

**English:**

We plan to measure the impact of our educational and communication efforts through:

| Metric | Method | Target |
|--------|--------|--------|
| **Simulator users** | Web analytics (page views, unique visitors, session duration) | {{placeholder:simulator_analytics_target}} |
| **Workshop participants** | Attendance counts, pre/post surveys | {{placeholder:workshop_attendance_target}} |
| **Social media reach** | Impressions, engagement rate, follower growth | {{placeholder:social_media_targets}} |
| **Learning outcomes** | Pre/post knowledge quiz for workshop participants | {{placeholder:learning_outcome_target}} |
| **User feedback** | Simulator feedback form, workshop exit tickets | Qualitative improvement |

**中文：**

我们计划通过以下方式衡量教育和传播工作的影响：

| 指标 | 方法 | 目标 |
|------|------|------|
| **模拟器用户** | 网页分析（页面浏览量、独立访客、会话时长）| {{placeholder:simulator_analytics_target}} |
| **工作坊参与者** | 参与人数统计、事前/事后调查 | {{placeholder:workshop_attendance_target}} |
| **社交媒体覆盖** | 曝光量、互动率、粉丝增长 | {{placeholder:social_media_targets}} |
| **学习成果** | 工作坊参与者的事前/事后知识测验 | {{placeholder:learning_outcome_target}} |
| **用户反馈** | 模拟器反馈表、工作坊离场小票 | 定性改进 |

---

## 16. Reflections and Lessons Learned / 反思与经验教训

**English:**

Building the simulator and developing our communication strategy taught us several lessons that we believe are worth sharing with the iGEM community:

### 16.1 Build the Tool Your Team Needs First

The simulator was originally built to solve our own communication problem — helping team members understand chemotaxis. Because we were our own first users, we built something genuinely useful. If we had started by asking "what do the judges want to see?", we would probably have built something less authentic and less effective. The lesson: **solve your own problem first, then share the solution.**

### 16.2 Mistakes Are Teachable Moments

The time acceleration oversight was embarrassing in the moment but became one of our most effective educational tools. Audiences remember the anecdote, and through it, they remember the concept. The lesson: **when you make a mistake, don't hide it — turn it into a teaching tool.**

### 16.3 Bilingual Is Hard, and Worth It

Maintaining full bilingual content doubles the writing and review workload. But it also doubles our potential audience — and, more importantly, ensures that Chinese-speaking audiences have access to content that is equivalent in quality, not a simplified afterthought. The lesson: **if your team is bilingual, your outreach should be too.**

### 16.4 Interactive Beats Static Every Time

When we have shown the simulator alongside static diagrams in informal testing, the simulator wins decisively — people spend more time engaging, ask more questions, and retain more information. This has reinforced our commitment to interactive educational tools. The lesson: **if you can make it interactive, do.**

**中文：**

构建模拟器和制定传播策略的过程教会了我们一些我们认为值得与 iGEM 社群分享的经验：

### 16.1 首先构建你的团队需要的工具

模拟器最初是为解决我们自己的沟通问题而构建的——帮助团队成员理解趋化性。因为我们是自己的第一批用户，所以我们构建了真正有用的东西。如果我们一开始就问"评委想看什么？"，我们可能会构建出一些不那么真实也不太有效的东西。教训是：**先解决你自己的问题，然后分享解决方案。**

### 16.2 错误是可教时刻

时间加速的疏忽在当下令人尴尬，但成了我们最有效的教育工具之一。受众记住了轶事，通过它，他们记住了概念。教训是：**当你犯错时，不要隐藏它——把它变成教学工具。**

### 16.3 双语很难，但值得

维护完全双语的内容使写作和审阅工作量加倍。但它也使我们的潜在受众加倍——更重要的是，确保中文受众获得的內容在质量上是同等的，而非简化的事后附加。教训是：**如果你的团队是双语的，你的外展也应该是双语的。**

### 16.4 互动总是击败静态

当我们在非正式测试中将模拟器与静态图表并排展示时，模拟器决定性地获胜——人们花更多时间参与，提出更多问题，保留更多信息。这强化了我们对互动教育工具的承诺。教训是：**如果你能把它做成互动的，就去做。**

---

> **friskoli — Finding food in a world without gravity.**
> **friskoli — 在没有重力的世界里寻找食物。**
>
> Team SZU-SIAT-China | Space Track 2026 | iGEM
