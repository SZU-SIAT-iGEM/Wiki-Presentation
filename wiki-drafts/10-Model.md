# 建模与理论 / Modeling & Theory

> **项目：** friskoli — SZU-SIAT-China, iGEM 2026
> **赛道：** 太空赛道 (Space Track)
> **最后更新：** 2026年5月

---

## 目录 / Table of Contents

1. [引言 / Introduction](#1-引言--introduction)
2. [模型架构概述 / Model Architecture Overview](#2-模型架构概述--model-architecture-overview)
3. [行为建模：趋化轨道 / Behavior Modeling: The Chemotaxis Track](#3-行为建模趋化轨道--behavior-modeling-the-chemotaxis-track)
4. [形态建模：膜轨道 / Morphology Modeling: The Membrane Track](#4-形态建模膜轨道--morphology-modeling-the-membrane-track)
5. [扩散-反应系统 / Diffusion-Reaction System](#5-扩散-反应系统--diffusion-reaction-system)
6. [增益因子 G 与优化 / Gain Factor G and Optimization](#6-增益因子-g-与优化--gain-factor-g-and-optimization)
7. [正反馈模块 / Positive Feedback Module](#7-正反馈模块--positive-feedback-module)
8. [验证计划 / Validation Plan](#8-验证计划--validation-plan)
9. [计划输出 / Planned Outputs](#9-计划输出--planned-outputs)
10. [参数汇总表 / Parameter Summary Table](#10-参数汇总表--parameter-summary-table)
11. [建模趣事 / A Modeling Anecdote](#11-建模趣事--a-modeling-anecdote)
12. [未来方向 / Future Directions](#12-未来方向--future-directions)
13. [参考文献 / References](#13-参考文献--references)

---

## 1. 引言 / Introduction

### 1.1 为什么建模：我们的故事 / Why We Model: Our Story

**中文**

建模工作的起点，来自一个坦诚的认知：我们并不真正理解趋化性。

"趋化"这个词听起来很直观——细菌感知化学物质，然后向它游过去。几乎像"寻路"一样。但当我们真正开始思考一个纳米尺度的生物如何在一个三维、扩散主导的环境中检测一个浓度梯度时，直觉塌陷了。

细菌没有神经系统。它们没有"方向感"。它们不会"朝某个东西游过去"。它们做的事情要简单得多：它们执行一种称为"游动-翻转"（run-and-tumble）的随机行走，而趋化性仅仅是在统计上偏置这种随机行走中游动与翻转的概率。你无法从单个细菌的行为中理解趋化性——你必须从群体的统计行为中观察。

这就是为什么我们决定构建模型。不是为了生成漂亮的图表，而是为了让自己理解系统。我们选择了一个**基于智能体的模型（Agent-Based Model, ABM）**：每个细菌是一个独立的智能体，遵循游动-翻转随机行走。通过改变状态概率（游动 vs 翻转），趋化性从群体的统计行为中涌现出来。这正是我们想要捕捉的东西——涌现（emergence）。

**English**

The modeling effort began with an honest admission: we didn't really understand chemotaxis.

The word "chemotaxis" sounds intuitive — a bacterium senses a chemical and swims toward it. Almost like pathfinding. But when you actually think about how a nanometer-scale organism detects a concentration gradient in a three-dimensional, diffusion-dominated environment, intuition collapses.

Bacteria have no nervous system. They have no "sense of direction." They don't "swim toward something." What they do is far simpler: they execute a random walk called "run-and-tumble," and chemotaxis is nothing more than a statistical bias in the probability of running versus tumbling within that random walk. You cannot understand chemotaxis from the behavior of a single bacterium — you must observe it from population-level statistics.

This is why we decided to build a model. Not to generate pretty figures, but to make the system understandable to ourselves. We chose an **Agent-Based Model (ABM)**: each bacterium is an independent agent following a run-and-tumble random walk. By altering state probabilities (run vs. tumble), chemotaxis emerges from the statistical behavior of the population. This is exactly what we wanted to capture — emergence.

---

### 1.2 两条轨道，一个连接 / Two Tracks, One Connection

**中文**

我们的建模工作分为两条轨道，它们通过一个共同的物理量——**膜表面积**——连接在一起：

1. **行为建模（Behavior Modeling）**：细菌如何感知纤维二糖、产生趋化信号、并将其转化为运动偏倚？这条轨道关注信号转导通路和智能体层面的运动规则，最终输出种群层面的趋化行为。

2. **形态建模（Morphology Modeling）**：细胞膜上能装下多少工程蛋白？PTS 转运蛋白和 INP-展示蛋白竞争同一块膜资源。这条轨道从细菌的几何形状出发，计算膜面积预算，并推导膜占用率对细胞健康和生长的影响。

两条轨道之间的桥梁是**膜表面积**——它既是形态建模的输出，又是行为建模中蛋白质分配的约束输入。没有足够的膜面积，再精妙的趋化信号通路也无处落脚。

**English**

Our modeling work is organized into two tracks, connected through a single physical quantity — **membrane surface area**:

1. **Behavior Modeling**: How do bacteria sense cellobiose, generate a chemotactic signal, and convert it into a motile bias? This track focuses on the signal transduction pathway and agent-level motion rules, ultimately yielding population-level chemotactic behavior.

2. **Morphology Modeling**: How many engineered proteins can fit on the cell membrane? PTS transporters and INP-display proteins compete for the same membrane real estate. This track starts from bacterial geometry, computes the membrane area budget, and derives the impact of membrane occupancy on cell health and growth.

The bridge between the two tracks is **membrane surface area** — it is simultaneously the output of the morphology model and the constraining input for protein allocation in the behavior model. Without sufficient membrane area, even the most elegant chemotactic signaling pathway has nowhere to land.

---

### 1.3 建模目标 / Modeling Objectives

**中文**

本项目 "friskoli" 旨在构建一种对纤维二糖（cellobiose）具有趋化响应能力并在外膜表面展示内切葡聚糖酶的大肠杆菌 MG1655 工程菌株，用于在微重力条件下实现纤维素的靶向降解。数学模型在本项目中扮演着关键角色，主要用于：

1. **理解信号转导机制**：阐明 PTS（磷酸转移酶系统）介导的趋化信号通路如何将细胞外纤维二糖浓度转化为鞭毛马达行为的调控信号。
2. **预测系统行为**：预测不同 AscF 表达水平（增益因子 G）下的趋化响应强度和梯度检测能力。
3. **优化设计参数**：确定最佳的 AscF 表达水平以最大化趋化灵敏度。
4. **模拟微重力效应**：比较 1g 与微重力条件下的扩散-反应动力学差异，评估太空应用的可行性。
5. **量化膜资源约束**：建立膜面积预算模型，确保工程蛋白的表达水平在膜健康的可行范围内。

在获得实验数据之前，本模型作为一个理论框架，将指导我们的实验设计和参数选择。模型预测将通过与毛细管趋化实验和纤维素降解实验的结果进行比对来验证。

**English**

The "friskoli" project aims to engineer an *Escherichia coli* MG1655 strain that exhibits chemotactic response to cellobiose and displays endoglucanase on its outer membrane surface, enabling targeted cellulose degradation under microgravity conditions. Mathematical modeling plays a critical role in this project, serving to:

1. **Understand signal transduction mechanisms**: Elucidate how the PTS (phosphotransferase system)-mediated chemotactic signaling pathway converts extracellular cellobiose concentration into flagellar motor control signals.
2. **Predict system behavior**: Forecast chemotactic response intensity and gradient detection capacity at different AscF expression levels (gain factor G).
3. **Optimize design parameters**: Determine the optimal AscF expression level to maximize chemotactic sensitivity.
4. **Simulate microgravity effects**: Compare diffusion-reaction kinetics under 1g versus microgravity conditions to assess feasibility for space applications.
5. **Quantify membrane resource constraints**: Build a membrane area budget model to ensure engineered protein expression levels remain within feasible bounds for membrane health.

Prior to the availability of experimental data, this model serves as a theoretical framework guiding our experimental design and parameter selection. Model predictions will be validated by comparison with capillary chemotaxis assays and cellulose degradation experiments.

---

### 1.4 趋化信号转导的独特性 / Uniqueness of the Chemotactic Signal Transduction

**中文**

本项目的趋化系统与大肠杆菌经典的甲基化趋化受体蛋白（MCP）趋化系统有本质区别。经典趋化系统采用甲基化适应机制（Barkai-Leibler 完美适应模型），而 PTS 介导的趋化则是非甲基化的、线性的信号转导通路。

关键区别：

| 特征 | MCP 趋化（经典） | PTS 趋化（本项目） |
|-----------|-------------------------|-------------------------|
| 信号受体 | 跨膜 MCP 受体（如 Tar, Tsr） | PTS 通透酶（如 AscF） |
| 适应机制 | 甲基化/去甲基化（Barkai-Leibler 完美适应） | PTS 层面无明显内在脱敏（近线性）；下游适应可经趋化通路发生 |
| 信号协同性 | 高度协同（Hill 系数 ~10-12） | 无协同性（线性 Hill 系数 ~1） |
| 增益 | 信号放大 ~35 倍 | 直接的代谢信号传递 |
| 能量来源 | 需 ATP | 磷酸烯醇式丙酮酸（PEP） |
| 动态范围 | 宽（5-6 个数量级） | 窄（约 2 个数量级） |

**English**

The chemotactic system in our project is fundamentally different from the classical methyl-accepting chemotaxis protein (MCP) system in *E. coli*. The classical system uses methylation-based adaptation (Barkai-Leibler perfect adaptation model), whereas PTS-mediated chemotaxis is a non-methylated, linear signal transduction pathway.

Key differences:

| Feature | MCP Chemotaxis (Classical) | PTS Chemotaxis (This project) |
|-----------|-------------------------|-------------------------|
| Signal receptor | Transmembrane MCP receptors (e.g., Tar, Tsr) | PTS permease (e.g., AscF) |
| Adaptation mechanism | Methylation/demethylation (Barkai-Leibler perfect adaptation) | No strong intrinsic desensitization at PTS level (near-linear); downstream adaptation can proceed through chemotaxis machinery |
| Signal cooperativity | Highly cooperative (Hill coefficient ~10-12) | Non-cooperative (Hill coefficient ~1) |
| Gain | Signal amplification ~35-fold | Direct metabolic signal relay |
| Energy source | ATP-dependent | Phosphoenolpyruvate (PEP) |
| Dynamic range | Wide (5-6 decades) | Narrow (~2 decades) |

---

### 1.5 PTS 趋化的线性信号特性 / Linear Signaling in PTS Chemotaxis

**中文**

根据 Somavanshi 等人（2016, *PLoS Biology*）的研究，PTS 介导的碳源趋化信号转导近**线性**，缺失了 MCP 系统中的协同放大机制。这意味着：

- PTS 趋化的信号响应曲线是简单的 Michaelis-Menten 型，而非 sigmoidal 型。
- 在 PTS 网络层面，输入近似反映糖转运通量，且没有明显的内在脱敏。但当该信号传入 CheA/CheW/受体感觉复合体后，下游甲基化依赖的趋化适应仍可参与，使通路活性逐步回到基线附近。
- 因此，PTS 趋化更适合检测较陡的浓度梯度，而对浅梯度不敏感。

在我们的模型中，这将是区分 PTS 趋化与经典 MCP 趋化的核心特征。

**English**

According to Somavanshi et al. (2016, *PLoS Biology*), PTS-mediated carbon source chemotaxis signal transduction is approximately **linear**, lacking the cooperative amplification mechanism of the MCP system. This means:

- The signal-response curve of PTS chemotaxis follows a simple Michaelis-Menten form, not a sigmoidal form.
- At the PTS-network level, the input is approximately proportional to sugar influx and shows little intrinsic desensitization. Once transmitted into the CheA/CheW/receptor sensory complex, however, downstream methylation-dependent adaptation can still participate in returning pathway activity toward baseline.
- Consequently, PTS chemotaxis is better suited for detecting steep concentration gradients and is insensitive to shallow gradients.

In our model, this will be the central feature that distinguishes PTS chemotaxis from classical MCP chemotaxis.

---

## 2. 模型架构概述 / Model Architecture Overview

### 2.1 整体框架 / Overall Framework

**中文**

我们采用**三维基于智能体的模型（Agent-Based Model, ABM）**框架。该框架将每个细菌视为一个独立智能体，在三维空间中运动，并与扩散的纤维二糖浓度场相互作用。

模型架构包含三个主要组件：

1. **细菌智能体层（Agent Layer）**：每个 *E. coli* 细胞为一个智能体，具有位置 $(x, y, z)$、内部信号状态（CheY-P 浓度）、鞭毛马达状态（游动/翻转）和年龄等属性。
2. **浓度场层（Field Layer）**：纤维二糖浓度 $c(\mathbf{x}, t)$ 在三维空间中通过扩散-反应方程演化。
3. **边界层（Boundary Layer）**：纤维素颗粒作为静态边界条件，提供纤维二糖生成的源项。

**English**

We employ a **three-dimensional agent-based model (ABM)** framework. Each bacterium is treated as an independent agent moving in three-dimensional space and interacting with a diffusing cellobiose concentration field.

The model architecture comprises three main components:

1. **Agent Layer**: Each *E. coli* cell is an agent with attributes including position $(x, y, z)$, internal signaling state (CheY-P concentration), flagellar motor state (run/tumble), and age.
2. **Field Layer**: The cellobiose concentration $c(\mathbf{x}, t)$ evolves in 3D space via a diffusion-reaction equation.
3. **Boundary Layer**: Cellulose particles serve as static boundary conditions, providing the source term for cellobiose production.

### 2.2 智能体属性 / Agent Attributes

**中文**

每个细菌智能体由以下状态变量定义：

| 属性 | 符号 | 单位 | 描述 |
|-----------|-------|------|-------------|
| 位置 | $\mathbf{r} = (x, y, z)$ | $\mu$m | 三维空间坐标 |
| 速度方向 | $\mathbf{v}$ | — | 单位向量，表示当前运动方向 |
| CheY-P 浓度 | $[\text{CheY-P}]$ | $\mu$M | 内部信号分子浓度 |
| 马达状态 | $s$ | — | 二元变量：0 = 游动，1 = 翻转 |
| 年龄 | $\tau$ | s | 自"出生"以来的时间 |
| 顺时针旋转偏倚 | $b$ | — | $P(\text{tumble})$ 翻转概率 |

**English**

Each bacterial agent is defined by the following state variables:

| Attribute | Symbol | Units | Description |
|-----------|--------|-------|-------------|
| Position | $\mathbf{r} = (x, y, z)$ | $\mu$m | 3D spatial coordinates |
| Velocity direction | $\mathbf{v}$ | — | Unit vector indicating current direction of motion |
| CheY-P concentration | $[\text{CheY-P}]$ | $\mu$M | Internal signaling molecule concentration |
| Motor state | $s$ | — | Binary variable: 0 = run, 1 = tumble |
| Age | $\tau$ | s | Time since "birth" |
| Clockwise rotation bias | $b$ | — | $P(\text{tumble})$ probability |

### 2.3 运动模型 / Motion Model

**中文**

细菌的运动由经典的"游动-翻转"交替模式描述（Berg & Brown, 1972）：

- **游动（Run）**：细菌以 $v \approx 25\ \mu\text{m/s}$ 的速度沿当前方向近乎直线运动。翻转偏倚 $b$ 通过控制翻转发生率来决定游动段持续时间：

  $$\lambda_{\text{tumble}}(Y_P) = \lambda_{\min} + (\lambda_{\max} - \lambda_{\min})\,b(Y_P)$$

  $$P(\text{tumble in }\Delta t) = 1 - \exp[-\lambda_{\text{tumble}}(Y_P)\,\Delta t]$$

  $$\tau_{\text{run}} = \frac{1}{\lambda_{\text{tumble}}}$$

  其中 $\lambda_{\min}$ 和 $\lambda_{\max}$ 分别为最小和最大翻转速率。CheY-P 高 → $b$ 高 → 翻转率高 → 游动短；反之 CheY-P 低 → 游动长。

- **翻转（Tumble）**：细菌随机选择新方向，翻转服从指数分布 $P(\text{tumble duration} > t) = \exp(-t / \tau_{\text{tumble}})$，$\tau_{\text{tumble}} \approx 0.1\ \text{s}$。新方向在三维空间中均匀随机选取。

- **翻转偏倚的动态调节**：CheY-P 浓度与鞭毛马达的顺时针旋转偏倚 $b$ 之间的关系由 Hill 型函数描述：
  $$b(Y_P) = \frac{Y_P^h}{K_Y^h + Y_P^h}$$

  其中 $h \approx 10.3$ 是 Hill 系数（反映了 CheY-P 与 FliM 结合的高协同性），$K_Y \approx 3.1\ \mu\text{M}$ 是马达切换阈值（Cluzel et al., 2000 *Science*）。

**English**

Bacterial motion is described by the classic "run-tumble" alternation pattern (Berg & Brown, 1972):

- **Run**: Bacteria move nearly linearly along their current direction at speed $v \approx 25\ \mu\text{m/s}$. The tumble bias $b$ determines the run segment duration by controlling the tumble rate:

  $$\lambda_{\text{tumble}}(Y_P) = \lambda_{\min} + (\lambda_{\max} - \lambda_{\min})\,b(Y_P)$$

  $$P(\text{tumble in }\Delta t) = 1 - \exp[-\lambda_{\text{tumble}}(Y_P)\,\Delta t]$$

  $$\tau_{\text{run}} = \frac{1}{\lambda_{\text{tumble}}}$$

  where $\lambda_{\min}$ and $\lambda_{\max}$ are the minimum and maximum tumble rates. High CheY-P → high $b$ → high tumble rate → short runs; low CheY-P → long runs.

- **Tumble**: Bacteria randomly select a new direction. The tumble duration follows $P(\text{tumble duration} > t) = \exp(-t / \tau_{\text{tumble}})$, with $\tau_{\text{tumble}} \approx 0.1\ \text{s}$. The new direction is uniformly random in three-dimensional space.

- **Dynamic tumble bias modulation**: The relationship between CheY-P concentration and the flagellar motor clockwise rotation bias $b$ is described by a Hill-type function:
  $$b(Y_P) = \frac{Y_P^h}{K_Y^h + Y_P^h}$$
  
  where $h \approx 10.3$ is the Hill coefficient (reflecting the high cooperativity of CheY-P binding to FliM) and $K_Y \approx 3.1\ \mu\text{M}$ is the motor switching threshold (Cluzel et al., 2000 *Science*).

### 2.4 数值实现 / Numerical Implementation

**中文**

ABM 的实现基于以下数值方案：

- **时间步长**：$\Delta t = 0.01\ \text{s}$，足以解析〜0.1 s 尺度的翻转事件。
- **空间离散化**：浓度场在 $L \times L \times L = 10\ \text{mm} \times 10\ \text{mm} \times 10\ \text{mm}$ 的网格上求解，网格间距 $\Delta x = 50\ \mu\text{m}$。
- **智能体数量**：典型模拟包含 $N = 10^3 - 10^4$ 个智能体。
- **边界条件**：周期性边界条件（对于细菌智能体）；Dirichlet 边界条件 $c = 0$（对于浓度场，假设无限稀释）。
- **随机数生成**：翻转事件、新方向和初始位置均使用 Mersenne Twister 伪随机数生成器。

**English**

The ABM is implemented using the following numerical scheme:

- **Time step**: $\Delta t = 0.01\ \text{s}$, sufficient to resolve tumble events on the ~0.1 s timescale.
- **Spatial discretization**: The concentration field is solved on a grid of size $L \times L \times L = 10\ \text{mm} \times 10\ \text{mm} \times 10\ \text{mm}$, with grid spacing $\Delta x = 50\ \mu\text{m}$.
- **Agent count**: Typical simulations include $N = 10^3 - 10^4$ agents.
- **Boundary conditions**: Periodic boundary conditions (for bacterial agents); Dirichlet boundary condition $c = 0$ (for the concentration field, assuming infinite dilution).
- **Random number generation**: Tumble events, new directions, and initial positions use the Mersenne Twister pseudorandom number generator.

---

## 3. 行为建模：趋化轨道 / Behavior Modeling: The Chemotaxis Track

### 3.1 从 MCP 到 PTS：我们的建模历程 / From MCP to PTS: Our Modeling Journey

**中文**

我们最初使用的是经典的 Barkai-Leibler 模型——它为 MCP 趋化系统设计，包含甲基化适应回路和完美适应。在传统的大肠杆菌趋化研究中，这是教科书级的模型。

但在深入理解我们自己的项目后，我们意识到一个根本性的错配：我们的系统使用的是 **PTS 趋化**，而非 MCP 趋化。PTS 趋化的信号不是来自跨膜受体——它直接来自代谢流经 PTS 转运蛋白的磷酸转移过程。这意味着：

- 信号与代谢状态直接耦合，而不是与受体占有率耦合。
- 不存在甲基化适应——系统对绝对浓度作线性响应。
- 增强趋化性的方式不是重新工程化受体（如 MCP 系统需要的那样），而是简单地**增加膜上转运蛋白的数量**。

这个转变优雅而实用：PTS 增强策略允许我们使用启动子扫描来控制 AscF 的表达水平，从而将表达量映射到趋化强度。这在 MCP 系统中是无法做到的——你无法简单地通过"更多的受体"来增强趋化性，因为适应回路会抵消效果。

**English**

We initially began with the classical Barkai-Leibler model — designed for the MCP chemotaxis system, complete with a methylation adaptation loop and perfect adaptation. In traditional *E. coli* chemotaxis research, this is the textbook model.

But after deepening our understanding of our own project, we recognized a fundamental mismatch: our system uses **PTS chemotaxis**, not MCP chemotaxis. The signal in PTS chemotaxis does not come from transmembrane receptors — it comes directly from the metabolic flux through the PTS transporter's phosphotransfer process. This means:

- The signal is directly coupled to metabolic state, not receptor occupancy.
- There is no methylation adaptation — the system responds linearly to absolute concentration.
- The way to enhance chemotaxis is not to re-engineer receptors (as the MCP system would require), but simply to **put more transporter proteins on the membrane**.

This shift is both elegant and practical: the PTS enhancement strategy allows us to use promoter scanning to control AscF expression levels, thereby mapping expression level to chemotaxis strength. This is something you cannot do in the MCP system — you cannot simply enhance chemotaxis with "more receptors" because the adaptation loop cancels out the effect.

---

### 3.2 PTS 信号级联概述 / PTS Signal Cascade Overview

**中文**

PTS 趋化信号转导通路与糖的磷酸转运耦合。在大肠杆菌中，PTS 由两种通用细胞质蛋白（EI 和 HPr）和多种糖特异性的通透酶（EII 复合物）组成。在本项目中，纤维二糖通过 AscF（属于 EII 复合物）转运并磷酸化。

信号转导流程如下：

```
细胞外纤维二糖 → AscF 转运/磷酸化 → 磷酸化级联中
           EI-P + HPr → EI + HPr-P
           HPr-P + EIIA → HPr + EIIA-P
           EIIA-P + EIICB → EIIA + EIICB-P → 纤维二糖-6-P
           PEP + EI → EI-P + 丙酮酸（再循环）

趋化信号：去磷酸化的 EI 与 CheA 结合 → CheA 活性降低 → 
         CheY-P 减少 → 鞭毛逆时针旋转 → 游动（趋化吸引）
```

**English**

The PTS chemotactic signaling pathway is coupled to sugar phosphorylation and transport. In *E. coli*, the PTS consists of two general cytoplasmic proteins (EI and HPr) and multiple sugar-specific permeases (EII complexes). In this project, cellobiose is transported and phosphorylated through AscF (a member of the EII complex).

The signal transduction flow is as follows:

```
Extracellular cellobiose → AscF transport/phosphorylation → Phosphorylation cascade:
           EI-P + HPr → EI + HPr-P
           HPr-P + EIIA → HPr + EIIA-P
           EIIA-P + EIICB → EIIA + EIICB-P → cellobiose-6-P
           PEP + EI → EI-P + pyruvate (recycling)

Chemotactic signal: Dephosphorylated EI binds to CheA → CheA activity reduced → 
         CheY-P decreased → CCW flagellar rotation → smooth swimming (attraction)
```

---

### 3.3 简化 PTS–CheA–CheY 信号模型 / Simplified PTS–CheA–CheY Signaling Model

**中文**

我们最初参考了经典 Barkai-Leibler 模型（Barkai & Leibler, 1997 *Nature*），但该模型为 MCP 趋化系统的甲基化适应而设计，与本项目的 PTS 信号机制有本质区别。因此我们最终不采用其甲基化适应框架，而是构建一个直接描述 PTS–EI–CheA–CheY 信号流的粗粒度动力学模型。PTS 输入在 PTS 网络层面没有明显的内在脱敏（Somavanshi 等 2016），呈近线性传递；下游适应仍可经趋化通路发生（Neumann 等 2012）。模型框架如下：

**CheY-P 动力学**：

$$\frac{dY_P}{dt} = k_Y \left( Y_T - Y_P \right) [\text{CheA-P}] - k_Z Y_P$$

其中：
- $Y_P = [\text{CheY-P}]$，$Y_T = [\text{CheY}]_{\text{total}}$ 为总 CheY 浓度
- $k_Y$ 是 CheY 磷酸化速率常数
- $k_Z$ 是 CheY-P 去磷酸化速率常数（隐含 CheZ 活性）
- $[\text{CheA-P}]$ 是活性（磷酸化）CheA 浓度

**CheA 活性**：

CheA 的活性受其与去磷酸化 EI 的相互作用调控。去磷酸化的 EI 与 CheA 结合，抑制其自磷酸化活性；磷酸化 EI（EI∼P）不与 CheA 结合。我们用抑制函数描述：

$$[\text{CheA-P}] = A_T \cdot \frac{K_I}{K_I + E_T e}$$

其中 $A_T = [\text{CheA}]_{\text{total}}$，$E_T = [\text{EI}] + [\text{EI}\sim\!P]$，$e = [\text{EI}]/E_T$，$K_I$ 是去磷酸化 EI 对 CheA 的半抑制常数。$e$ 越大（EI 去磷酸化越多），CheA 活性越低。

**EI 磷酸化动力学（守恒形式）**：

EI 的磷酸化状态由细胞外纤维二糖浓度通过 AscF 转运速率决定。采用无量纲化变量 $e = [\text{EI}]/E_T$，并利用守恒关系 $[\text{EI}\sim\!P] = E_T(1-e)$：

$$\frac{de}{dt} = k_d\,J(S,G)\,(1 - e) - k_r\,e$$

其中 $J(S,G) = \dfrac{N_0 G\,k_{\text{cat}}\,S}{K_S + S}$ 是纤维二糖转运通量。$k_d\,J(S,G)\,(1-e)$ 项表示：通量越大去磷酸化越快，但可被去磷酸化的 EI∼P（即 $1-e$）随 $e$ 增大而减少；$k_r e$ 表示 PEP 依赖性再磷酸化。

**English**

We initially consulted the classical Barkai-Leibler model (Barkai & Leibler, 1997 *Nature*), but that model was designed for methylation-based adaptation in the MCP chemotaxis system — a mechanism absent from our PTS-based design. We therefore do not adopt its methylation adaptation framework. Instead, we construct a coarse-grained kinetic model that directly describes PTS–EI–CheA–CheY signal flow. PTS input shows no strong intrinsic desensitization at the PTS-network level (Somavanshi et al. 2016), propagating approximately linearly; downstream adaptation can still proceed through the chemotaxis machinery (Neumann et al. 2012). The model framework is as follows:

**CheY-P dynamics**:

$$\frac{dY_P}{dt} = k_Y \left( Y_T - Y_P \right) [\text{CheA-P}] - k_Z Y_P$$

where:
- $Y_P = [\text{CheY-P}]$, $Y_T = [\text{CheY}]_{\text{total}}$ is the total CheY concentration
- $k_Y$ is the CheY phosphorylation rate constant
- $k_Z$ is the CheY-P dephosphorylation rate constant (implicitly includes CheZ activity)
- $[\text{CheA-P}]$ is the active (phosphorylated) CheA concentration

**CheA activity**:

CheA activity is modulated by its interaction with dephosphorylated EI. Dephosphorylated EI binds to CheA and inhibits its autophosphorylation activity; phosphorylated EI (EI∼P) does not interact with CheA. We describe this with an inhibition function:

$$[\text{CheA-P}] = A_T \cdot \frac{K_I}{K_I + E_T e}$$

where $A_T = [\text{CheA}]_{\text{total}}$, $E_T = [\text{EI}] + [\text{EI}\sim\!P]$, $e = [\text{EI}]/E_T$, and $K_I$ is the half-inhibition constant of dephosphorylated EI on CheA. Larger $e$ (more dephosphorylated EI) means lower CheA activity.

**EI phosphorylation dynamics (conservation form)**:

The phosphorylation state of EI is determined by the extracellular cellobiose concentration through the AscF transport rate. Using the dimensionless variable $e = [\text{EI}]/E_T$ and the conservation relation $[\text{EI}\sim\!P] = E_T(1-e)$:

$$\frac{de}{dt} = k_d\,J(S,G)\,(1 - e) - k_r\,e$$

where $J(S,G) = \dfrac{N_0 G\,k_{\text{cat}}\,S}{K_S + S}$ is the cellobiose transport flux. The term $k_d\,J(S,G)\,(1-e)$ captures that greater flux drives faster dephosphorylation, but the available EI∼P ($1-e$) shrinks as $e$ grows; $k_r e$ represents PEP-dependent rephosphorylation.

---

### 3.4 AscF 转运动力学 / AscF Transport Kinetics

**中文**

纤维二糖通过 AscF 的转运遵循 Michaelis-Menten 动力学。定义转运通量：

$$J(S, G) = \frac{N_0 G \cdot k_{\text{cat}} \cdot [S]}{K_S + [S]}$$

其中：
- $[S]$ 是细胞外纤维二糖浓度
- $K_S \approx 20\text{--}50\ \mu\text{M}$ 是 AscF 对纤维二糖的米氏常数（Hall & Xu, 1992）
- $N_0$ 是参考启动子下单个细胞的 AscF 蛋白数量
- $G$ 是相对于该参考表达水平的增益因子（见第 6 节）
- $k_{\text{cat}}$ 是单个 AscF 转运蛋白的转换数

注意：AscF 在实验室条件下的标准 MG1655 培养中处于沉默状态，因此 $G$ 不表示相对于野生型的倍数——那将是"零乘以倍数仍为零"。$G$ 表示相对于一个工程参考表达水平（如 J23116 启动子驱动的表达量）的倍数。$N_0$ 取该参考启动子下的 AscF 蛋白数。

**English**

Cellobiose transport through AscF follows Michaelis-Menten kinetics. We define the transport flux:

$$J(S, G) = \frac{N_0 G \cdot k_{\text{cat}} \cdot [S]}{K_S + [S]}$$

where:
- $[S]$ is the extracellular cellobiose concentration
- $K_S \approx 20\text{--}50\ \mu\text{M}$ is the Michaelis constant of AscF for cellobiose (Hall & Xu, 1992)
- $N_0$ is the number of AscF proteins per cell under a reference promoter
- $G$ is the gain factor relative to that reference expression level (see Section 6)
- $k_{\text{cat}}$ is the turnover number of a single AscF transporter

Note: Since AscF is silent in standard MG1655 culture under laboratory conditions, $G$ does NOT represent fold-change relative to wild-type — that would be "zero times any fold equals zero." Instead, $G$ represents fold-change relative to an engineered reference expression level (e.g., the expression driven by the J23116 promoter). $N_0$ is the AscF protein count under that reference promoter.

---

### 3.5 完整 ODE 系统 / Complete ODE System

**中文**

结合以上所有组成部分，PTS 趋化子模型的完整常微分方程（ODE）系统为。定义 $E_T = [\text{EI}] + [\text{EI}\sim\!P]$（总 EI 池）、$Y_T = [\text{CheY}]_{\text{total}}$、$A_T = [\text{CheA}]_{\text{total}}$：

$$
\begin{aligned}
J(S,G) &= \frac{N_0 G \cdot k_{\text{cat}} \cdot S}{K_S + S} \\[4pt]
e &= \frac{[\text{EI}]}{E_T} \\[4pt]
\frac{de}{dt} &= k_d\,J(S,G)\,(1 - e) - k_r\,e \\[4pt]
[\text{CheA-P}] &= A_T\,\frac{K_I}{K_I + E_T e} \\[4pt]
\frac{dY_P}{dt} &= k_Y\,[\text{CheA-P}]\,(Y_T - Y_P) - k_Z\,Y_P \\[4pt]
b(Y_P) &= \frac{Y_P^h}{K_Y^h + Y_P^h}
\end{aligned}
$$

其中 $e \in [0,1]$ 是去磷酸化 EI 的分数。方程 $de/dt$ 采用守恒形式：糖转运通量 $J(S,G)$ 越大，EI 去磷酸化驱动力越强；但当 $e \to 1$ 时 $(1-e)$ 项趋零——可被去磷酸化的 EI 已所剩无几，速率自动饱和。

在稳态条件下，给定恒定浓度 $S$，令 $de/dt = 0$ 和 $dY_P/dt = 0$ 即可求解稳态 $e^*$ 和 $Y_P^*$。然而，在梯度存在的情况下，$S$ 随位置变化，导致不同位置的 $b$ 值不同，进而产生方向性趋化运动。

**模型假定：**
- 总 EI 池 $E_T$ 在趋化时间尺度上恒定（蛋白合成/降解远慢于磷酸化/去磷酸化）
- PEP 浓度隐含于 $k_r$ 项中（PEP 供体充足时为常数）
- CheZ（CheY-P 磷酸酶）活性隐含包含在 $k_Z$ 项中
- AscB 活性足够高，不会导致纤维二糖-6-P 的显著积累
- $K_I$ 为去磷酸化 EI 对 CheA 的半抑制常数

**English**

Combining all of the above components, the complete ordinary differential equation (ODE) system for the PTS chemotaxis sub-model is given below. We define $E_T = [\text{EI}] + [\text{EI}\sim\!P]$ (total EI pool), $Y_T = [\text{CheY}]_{\text{total}}$, and $A_T = [\text{CheA}]_{\text{total}}$:

$$
\begin{aligned}
J(S,G) &= \frac{N_0 G \cdot k_{\text{cat}} \cdot S}{K_S + S} \\[4pt]
e &= \frac{[\text{EI}]}{E_T} \\[4pt]
\frac{de}{dt} &= k_d\,J(S,G)\,(1 - e) - k_r\,e \\[4pt]
[\text{CheA-P}] &= A_T\,\frac{K_I}{K_I + E_T e} \\[4pt]
\frac{dY_P}{dt} &= k_Y\,[\text{CheA-P}]\,(Y_T - Y_P) - k_Z\,Y_P \\[4pt]
b(Y_P) &= \frac{Y_P^h}{K_Y^h + Y_P^h}
\end{aligned}
$$

Here $e \in [0,1]$ is the fraction of dephosphorylated EI. The $de/dt$ equation is written in conservation form: greater sugar transport flux $J(S,G)$ drives stronger EI dephosphorylation, but as $e \to 1$, the $(1-e)$ term vanishes — few phosphorylated EI molecules remain to be dephosphorylated, so the rate saturates automatically.

Under steady-state conditions with a constant $S$, setting $de/dt = 0$ and $dY_P/dt = 0$ yields the steady-state $e^*$ and $Y_P^*$. However, in the presence of a gradient, $S$ varies with position, leading to spatially varying $b$ values and thus directional chemotactic movement.

**Model assumptions:**
- The total EI pool $E_T$ is constant on chemotactic timescales (protein synthesis/degradation is much slower than phosphorylation/dephosphorylation)
- PEP concentration is implicitly contained in $k_r$ (constant under ample PEP supply)
- CheZ (CheY-P phosphatase) activity is implicitly included in $k_Z$
- AscB activity is sufficiently high to prevent significant accumulation of cellobiose-6-P
- $K_I$ is the half-inhibition constant of dephosphorylated EI on CheA

---

### 3.6 与 MCP 趋化的关键差异 / Key Differences from MCP Chemotaxis

**中文**

我们的模型与经典 MCP 趋化模型之间的关键差异总结如下：

1. **无 PTS 层面的内在脱敏**：PTS 网络层面不存在甲基化适应环，信号近线性传递（Somavanshi 等 2016）。但 PTS 信号进入 CheA/CheW/受体复合体后，下游甲基化依赖适应仍可参与，使通路活性逐步回归（Neumann 等 2012）。因此整体系统并非完全无适应，而是适应发生在 PTS 下游而非 PTS 内部。
2. **线性信号响应**：$b([S])$ 函数是近似 Michaelis-Menten 型，呈现双曲线形状（Hill 系数 $n \approx 1$），而非 MCP 系统的 sigmoidal 形状。
3. **较窄的动态范围**：PTS 系统在较窄的浓度范围内响应（约 1–100 $\mu$M），而 MCP 系统可响应 5–6 个数量级。
4. **与代谢的直接耦合**：PTS 信号直接反映糖的转运速率，因此与细胞的代谢状态紧密耦合。

这些差异意味着我们的菌株将在较陡的纤维二糖梯度上表现出趋化性，但在浅梯度上可能不如 MCP 介导的趋化有效。

**English**

Key differences between our model and classical MCP chemotaxis models are summarized below:

1. **No intrinsic desensitization at PTS level**: The methylation adaptation loop is absent from the PTS network itself; signal propagation is approximately linear (Somavanshi et al. 2016). However, once the PTS signal enters the CheA/CheW/receptor complex, downstream methylation-dependent adaptation can still participate, gradually returning pathway activity toward baseline (Neumann et al. 2012). The system as a whole is not entirely adaptation-free — adaptation occurs downstream of PTS, not within it.
2. **Linear signal response**: The $b([S])$ function is approximately Michaelis-Menten type with a hyperbolic shape (Hill coefficient $n \approx 1$), rather than the sigmoidal shape of the MCP system.
3. **Narrower dynamic range**: The PTS system responds over a narrower concentration range (~1–100 $\mu$M), whereas the MCP system can respond across 5–6 orders of magnitude.
4. **Direct metabolic coupling**: PTS signaling directly reflects sugar transport rate and is therefore tightly coupled to the cell's metabolic state.

These differences imply that our strain will exhibit chemotaxis to steeper cellobiose gradients but may be less effective than MCP-mediated chemotaxis for shallow gradients.

---

### 3.7 PTS 增强策略与膜约束 / PTS Enhancement Strategy and the Membrane Constraint

**中文**

PTS 趋化有一个关键的实际优势：与 MCP 趋化不同（你需要重新工程化受体结构域来改变配体特异性），PTS 趋化的增强策略出奇地简单——**只需要更多转运蛋白**。

我们可以使用启动子扫描（promoter scanning）来控制 AscF 的表达水平，从而建立一条从"启动子强度 → AscF 表达量 → 转运速率 → CheY-P 浓度 → 翻转偏倚 → 趋化强度"的完整映射链。

但这引入了一个工程约束，这个约束成为了我们整个建模工作的核心：**膜的物理面积是有限的**。PTS 转运蛋白（AscF）和 INP-展示蛋白（纤维素酶）都必须位于细胞膜上。它们竞争同一块物理资源。如果将转运蛋白的表达量推得过高：

- 膜过度拥挤 → 细胞毒性
- 膜蛋白过多 → 生长速率下降
- 信号饱和 → 梯度分辨能力丧失（即使膜能承受）

因此，G 因子不能任意取大——存在一个必须在建模中量化的物理上限。

此外，在细胞分裂过程中，膜蛋白由子细胞继承。在无蛋白质降解的简化假设下，每一代的膜健康状况只降不升——这是一个不可逆的累积效应，必须在多代模拟中考虑。

**English**

PTS chemotaxis has a crucial practical advantage: unlike MCP chemotaxis, where you need to re-engineer receptor domains to change ligand specificity, the enhancement strategy for PTS chemotaxis is surprisingly simple — **you just need more transporter protein**.

We can use promoter scanning to control AscF expression levels, thereby establishing a complete mapping chain from "promoter strength → AscF expression → transport rate → CheY-P concentration → tumble bias → chemotaxis strength."

But this introduces an engineering constraint that became central to our entire modeling effort: **the physical area of the membrane is finite**. Both PTS transporters (AscF) and INP-display proteins (cellulase) must reside on the cell membrane. They compete for the same physical resource. If transporter expression is pushed too high:

- Membrane overcrowding → cellular toxicity
- Excess membrane protein → reduced growth rate
- Signal saturation → loss of gradient discrimination (even if the membrane could tolerate it)

Thus, the G factor cannot be arbitrarily large — there exists a physical upper bound that must be quantified within the model.

Furthermore, during cell division, membrane proteins are inherited by daughter cells. Under the simplifying assumption of no protein degradation, membrane health can only decrease across generations — an irreversible cumulative effect that must be accounted for in multi-generation simulations.

---

### 3.8 涌现与"趋化等效流" / Emergence and the "Chemotaxis Equivalent Flow"

**中文**

多智能体模型最令人振奋的特征是**涌现**——个体的简单规则在群体层面产生复杂行为。在我们的 ABM 中，每个细菌执行相同的游动-翻转规则，但当它们的局部翻转偏倚因纤维二糖浓度场而在空间中变化时，种群统计上表现出朝向纤维素源的定向运动。

这引出了我们模型的一个"野心问题"（aspirational question）：

> **"趋化等效流"概念**：多大的趋化强度能够等效于地球重力在溶液中引起的对流混合效应？

换句话说：在一个没有重力的环境中（微重力），趋化性是否能够"替代"重力驱动的对流，将细菌有效地聚集到纤维素表面？如果可以，需要多强的趋化响应？

这是我们希望通过模型探索的核心科学问题之一。它并非我们必须在 iGEM 周期内给出确定答案的问题——而是我们希望通过模型打开的一个思考方向。

**English**

The most exhilarating feature of multi-agent models is **emergence** — simple individual rules producing complex population-level behavior. In our ABM, each bacterium follows the same run-and-tumble rules, but when their local tumble bias varies spatially due to the cellobiose concentration field, the population statistically exhibits directed motion toward the cellulose source.

This leads to what we call our model's "aspirational question":

> **The "Chemotaxis Equivalent Flow" concept**: What magnitude of chemotaxis equals the mixing effect that Earth's gravity produces through convection in solution?

In other words: in a gravity-free environment (microgravity), can chemotaxis "replace" gravity-driven convection and effectively aggregate bacteria at the cellulose surface? If so, how strong must the chemotactic response be?

This is one of the core scientific questions we hope to explore through our model. It is not a question to which we must deliver a definitive answer within the iGEM cycle — rather, it is a direction of inquiry we hope the model will open.

---

### 3.9 环境变量：三维扩散场与重力 / Environmental Variables: 3D Diffusion Field and Gravity

**中文**

ABM 运行在一个三维扩散场上。纤维二糖从纤维素源向外扩散，形成随时间演化的浓度梯度。细菌智能体在这个场中运动，既感知浓度、又被自身的消耗行为改变浓度场（反馈耦合）。

重力通过驱动对流来影响传质。在有重力（1g）的条件下，局部的温度差异和浓度差异会产生密度差，从而驱动微弱的对流。这种对流起到"混合"作用，削弱梯度。而在微重力条件下，对流缺失，传质仅靠扩散：

- 梯度更陡（无对流混合稀释）
- 耗尽区更大（无对流补充）
- 趋化信号可能更强（梯度更陡）

模型需要同时考虑这两种物理机制：扩散场和重力驱动的对流效应。

**English**

The ABM operates on a three-dimensional diffusion field. Cellobiose diffuses outward from the cellulose source, creating a time-evolving concentration gradient. Bacterial agents move within this field, both sensing concentration and altering it through their own consumption (feedback coupling).

Gravity affects mass transport by driving convection. Under terrestrial (1g) conditions, local temperature and concentration differences generate density differences, which drive weak convective flows. This convection acts as a "mixing" effect, weakening gradients. Under microgravity, convection is absent and mass transport is diffusion-only:

- Steeper gradients (no convective mixing to dilute)
- Larger depletion zones (no convective replenishment)
- Potentially stronger chemotactic signals (steeper gradients)

The model must account for both physical mechanisms: the diffusion field and gravity-driven convective effects.

---

## 4. 形态建模：膜轨道 / Morphology Modeling: The Membrane Track

### 4.1 胶囊几何模型 / Capsule Geometry Model

**中文**

形态建模轨道的起点是将杆状的大肠杆菌抽象为一种简单的几何体——**胶囊模型**（capsule model）：一个圆柱体加上两端各一个半球体。

对于标准 MG1655 细胞，其大致尺寸为：

- 长度（圆柱段）：$L_{\text{cyl}} \approx 2\ \mu\text{m}$
- 半径：$r \approx 0.5\ \mu\text{m}$

由此几何形状，我们可以推导出两个关键物理量：

**总体积**：

$$V_{\text{total}} = \pi r^2 L_{\text{cyl}} + \frac{4}{3}\pi r^3$$

**总膜表面积**：

$$A_{\text{total}} = 2\pi r L_{\text{cyl}} + 4\pi r^2$$

对于一个典型的 MG1655 细胞（$L_{\text{cyl}} = 2\ \mu\text{m}$，$r = 0.5\ \mu\text{m}$）：

$$A_{\text{total}} = 2\pi (0.5)(2) + 4\pi (0.5)^2 = 2\pi + \pi = 3\pi \approx 9.42\ \mu\text{m}^2$$

这个膜表面积是连接两条建模轨道的核心参数。

**English**

The starting point of the morphology modeling track is the abstraction of the rod-shaped bacterium into a simple geometric solid — the **capsule model**: a cylinder capped by two hemispheres.

For a standard MG1655 cell, approximate dimensions are:

- Length (cylindrical segment): $L_{\text{cyl}} \approx 2\ \mu\text{m}$
- Radius: $r \approx 0.5\ \mu\text{m}$

From this geometry, we derive two key physical quantities:

**Total volume**:

$$V_{\text{total}} = \pi r^2 L_{\text{cyl}} + \frac{4}{3}\pi r^3$$

**Total membrane surface area**:

$$A_{\text{total}} = 2\pi r L_{\text{cyl}} + 4\pi r^2$$

For a typical MG1655 cell ($L_{\text{cyl}} = 2\ \mu\text{m}$, $r = 0.5\ \mu\text{m}$):

$$A_{\text{total}} = 2\pi (0.5)(2) + 4\pi (0.5)^2 = 2\pi + \pi = 3\pi \approx 9.42\ \mu\text{m}^2$$

This membrane surface area is the core parameter connecting the two modeling tracks.

---

### 4.2 膜表面积预算 / Membrane Surface Area Budget

**中文**

并非所有 $9.42\ \mu\text{m}^2$ 的膜面积都可供工程蛋白使用。细胞的天然生存需求占据了大部分膜空间：

- **天然膜蛋白**（呼吸链复合物、ATP 合酶、转运系统、信号蛋白）
- **细胞壁附着位点**（Braun 脂蛋白、OmpA 等）
- **脂质结构完整性**（膜曲率维持、脂筏微域）
- **必需通量需求**（基础营养摄取和代谢物排出）

我们将这些统称为**基础占用面积** $A_{\text{basal}}$。只有剩余的**可分配面积** $A_{\text{available}}$ 才可用于工程蛋白：

$$A_{\text{available}} = A_{\text{total}} - A_{\text{basal}}$$

在可分配面积中，两类工程蛋白需要共存：

$$A_{\text{available}} = A_{\text{PTS}} + A_{\text{INP}}$$

其中：
- $A_{\text{PTS}}$ = AscF 转运蛋白（PTS 通透酶）占用的膜面积
- $A_{\text{INP}}$ = INP-纤维素酶融合蛋白（冰核蛋白展示系统）占用的膜面积

两类蛋白之间存在直接的**资源竞争关系**：分配给转运蛋白的面积多一单位，就少一单位给纤维素酶——反之亦然。这种权衡是我们优化问题的核心。

**English**

Not all $9.42\ \mu\text{m}^2$ of membrane area is available for engineered proteins. The cell's natural survival needs occupy a significant fraction of membrane space:

- **Native membrane proteins** (respiratory chain complexes, ATP synthase, transport systems, signaling proteins)
- **Cell wall attachment sites** (Braun's lipoprotein, OmpA, etc.)
- **Lipid structural integrity** (membrane curvature maintenance, lipid raft microdomains)
- **Essential flux demands** (basal nutrient uptake and metabolite efflux)

We collectively refer to these as the **basal occupied area** $A_{\text{basal}}$. Only the remaining **allocatable area** $A_{\text{available}}$ is available for engineered proteins:

$$A_{\text{available}} = A_{\text{total}} - A_{\text{basal}}$$

Within the allocatable area, two classes of engineered proteins must coexist:

$$A_{\text{available}} = A_{\text{PTS}} + A_{\text{INP}}$$

where:
- $A_{\text{PTS}}$ = membrane area occupied by AscF transporters (PTS permease)
- $A_{\text{INP}}$ = membrane area occupied by INP-cellulase fusion proteins (ice nucleation protein display system)

There exists a direct **resource competition** between the two protein classes: every unit of area allocated to transporters is one less unit available for cellulase — and vice versa. This trade-off lies at the heart of our optimization problem.

---

### 4.3 膜占用率与膜健康 / Membrane Occupancy Rate and Membrane Health

**中文**

我们定义**膜占用率**（membrane occupancy rate）$\phi$ 来描述工程蛋白对膜面积的占用程度：

$$\phi = \frac{A_{\text{PTS}} + A_{\text{INP}}}{A_{\text{available}}}$$

$\phi$ 的取值范围为 $[0, 1]$，其中：
- $\phi = 0$：无工程蛋白占用
- $\phi = 1$：可分配面积全部被工程蛋白占用

$\phi$ 是一个需要精细优化的参数：

- **$\phi$ 过低**：功能性蛋白数量不足，底物摄取受限，纤维素降解速率低。系统功能不强。
- **$\phi$ 过高**：膜过度拥挤，引发细胞胁迫反应，生长速率受抑制。蛋白质可能错误折叠或聚集。
- **最优区**：存在一个中间区域，在该区域内系统功能最大化，同时细胞胁迫处于可接受水平。

这引出**膜健康函数**（membrane health function）$H(\phi)$：

$$H(\phi) = \begin{cases}
1, & \phi \leq \phi_{\text{crit}} \\
\exp\left(-\alpha (\phi - \phi_{\text{crit}})^2\right), & \phi > \phi_{\text{crit}}
\end{cases}$$

其中 $\phi_{\text{crit}}$ 是临界占用率阈值，超过后膜健康开始快速下降；$\alpha$ 是衰减速率常数。

当占用率超过临界阈值时，膜健康急剧下降——这不是线性衰退，而是加速恶化。

**English**

We define the **membrane occupancy rate** $\phi$ to describe the degree to which engineered proteins occupy the membrane area:

$$\phi = \frac{A_{\text{PTS}} + A_{\text{INP}}}{A_{\text{available}}}$$

$\phi$ takes values in $[0, 1]$, where:
- $\phi = 0$: No engineered protein occupancy
- $\phi = 1$: All allocatable area occupied by engineered proteins

$\phi$ is a parameter requiring fine-tuned optimization:

- **$\phi$ too low**: Insufficient functional proteins, limited substrate uptake, low cellulose degradation rate. The system is under-functional.
- **$\phi$ too high**: Membrane overcrowding triggers cellular stress responses, growth rate is inhibited. Proteins may misfold or aggregate.
- **Optimal zone**: There exists an intermediate region where system function is maximized while cellular stress remains at an acceptable level.

This gives rise to the **membrane health function** $H(\phi)$:

$$H(\phi) = \begin{cases}
1, & \phi \leq \phi_{\text{crit}} \\
\exp\left(-\alpha (\phi - \phi_{\text{crit}})^2\right), & \phi > \phi_{\text{crit}}
\end{cases}$$

where $\phi_{\text{crit}}$ is the critical occupancy threshold beyond which membrane health begins to decline rapidly, and $\alpha$ is the decay rate constant.

When occupancy exceeds the critical threshold, membrane health drops sharply — this is not a linear decline but an accelerating deterioration.

---

### 4.3.5 膜面积的动态增长 / Dynamic Growth of Membrane Area

**中文**

上述膜占用率分析基于静态几何假设。然而，细胞在生长过程中，膜面积是动态变化的。按照 Harris & Theriot (2016) 和 Shi et al. (2021) 的框架，细菌的尺寸由表面积合成速率与体积合成速率的相对关系决定：

$$\frac{dV}{dt} = \alpha(t) \cdot V(t)$$

$$\frac{dA}{dt} = \beta(t) \cdot V(t)$$

由此可得表面积-体积比（SA/V）的动态方程：

$$\frac{d}{dt}\left(\frac{A}{V}\right) = \beta(t) - \alpha(t) \cdot \frac{A}{V}$$

其中：
- $\alpha(t)$ 是体积比生长速率，取决于营养状态：$\alpha(t) = \mu_{max} \cdot \frac{J_{PTS}}{K_J + J_{PTS}} \cdot f_{burden}(t)$
- $\beta(t)$ 是表面积比合成速率，受细胞壁合成能力和膜胁迫影响：$\beta(t) = \beta_0 \cdot f_{wall}(t) \cdot f_{burden}(t)$

当 $\beta(t) > \alpha(t) \cdot (A/V)$ 时，SA/V 上升，细胞趋向细长；当体积增长快于表面积合成时，SA/V 下降，细胞变粗。微重力条件下，传质限制使营养供给减弱，$\alpha(t)$ 下降，可能导致 SA/V 的动态平衡点发生偏移。

**English**

The membrane occupancy analysis above assumes static geometry. However, during cell growth, membrane area changes dynamically. Following the framework of Harris & Theriot (2016) and Shi et al. (2021), bacterial size is determined by the relative rates of surface area synthesis and volume synthesis:

$$\frac{dV}{dt} = \alpha(t) \cdot V(t)$$

$$\frac{dA}{dt} = \beta(t) \cdot V(t)$$

From these, the dynamic equation for the surface-area-to-volume ratio (SA/V) follows:

$$\frac{d}{dt}\left(\frac{A}{V}\right) = \beta(t) - \alpha(t) \cdot \frac{A}{V}$$

where:
- $\alpha(t)$ is the specific volume growth rate, dependent on nutrient status: $\alpha(t) = \mu_{max} \cdot \frac{J_{PTS}}{K_J + J_{PTS}} \cdot f_{burden}(t)$
- $\beta(t)$ is the specific surface area synthesis rate, affected by cell wall synthesis capacity and membrane stress: $\beta(t) = \beta_0 \cdot f_{wall}(t) \cdot f_{burden}(t)$

When $\beta(t) > \alpha(t) \cdot (A/V)$, SA/V increases and the cell becomes more elongated; when volume growth outpaces surface synthesis, SA/V decreases and the cell becomes wider. Under microgravity, mass transfer limitations reduce nutrient supply, lowering $\alpha(t)$ and potentially shifting the SA/V equilibrium point.

**文献依据 / Literature basis:**
- Harris, L. K. & Theriot, J. A. (2016). Relative rates of surface and volume synthesis set bacterial cell size. *Cell*, 165(6), 1479–1492.
- Shi, H., et al. (2021). Precise regulation of the relative rates of surface area and volume synthesis in bacterial cells growing in dynamic environments. *Nature Communications*, 12, 2209.

---

### 4.4 连续功能链 / The Continuous Functional Chain

**中文**

形态模型和行为模型并非孤立运行——它们通过膜表面积连接成一条连续的功能链：

```
表面展示蛋白（INP-纤维素酶）
        ↓
底物降解（纤维素 → 纤维二糖）
        ↓
近表面纤维二糖浓度升高
        ↓
PTS 转运（AscF 摄取纤维二糖）
        ↓
生长速率提升 → 细胞形态变化（体积增大、分裂加速）
        ↓
膜面积重新分配 → 蛋白质分配重新平衡
```

这条链中的每一步都由膜面积约束所限制。

**English**

The morphology model and behavior model do not operate in isolation — they are connected through membrane surface area into a continuous functional chain:

```
Surface display proteins (INP-cellulase)
        ↓
Substrate degradation (cellulose → cellobiose)
        ↓
Elevated near-surface cellobiose concentration
        ↓
PTS transport (AscF-mediated cellobiose uptake)
        ↓
Enhanced growth rate → cell morphology changes (increased volume, accelerated division)
        ↓
Membrane area reallocation → protein allocation rebalancing
```

Every step in this chain is constrained by the membrane area budget.

---

**中文**

表面展示蛋白的数量并非静态。随着细胞生长和分裂，单位膜面积上的展示蛋白密度会被**代际稀释**（generational dilution）。如果蛋白合成速率跟不上膜面积的增长速率，则子代细胞表面的功能蛋白密度将低于亲代。这一效应在表面展示系统的数学描述中不可忽视：

$$\frac{dN_p}{dt} = k_{exp}(t) \cdot \left(1 - \frac{N_p(t)}{N_{max}(t)}\right) - k_{loss} \cdot N_p(t) - \mu(t) \cdot N_p(t)$$

其中最右项 $-\mu(t) \cdot N_p(t)$ 代表因细胞生长和分裂导致的**稀释损耗**。这一项将形态模型（膜面积增长）与功能模型（表面展示容量）在时序上耦合起来。

稀释效应的存在意味着：即使启动子强度（$G$）很高，如果细胞生长太快，表面展示密度也可能不升反降。这正是我们在 G 扫描中观察"最优窗口"的另一个物理基础。

**English**

The number of surface-displayed proteins is not static. As cells grow and divide, the density of displayed proteins per unit membrane area undergoes **generational dilution**. If the protein synthesis rate cannot keep pace with the membrane area growth rate, the functional protein density on daughter cell surfaces will be lower than that of the parent. This effect cannot be ignored in the mathematical description of surface display systems:

$$\frac{dN_p}{dt} = k_{exp}(t) \cdot \left(1 - \frac{N_p(t)}{N_{max}(t)}\right) - k_{loss} \cdot N_p(t) - \mu(t) \cdot N_p(t)$$

The rightmost term $-\mu(t) \cdot N_p(t)$ represents the **dilution loss** caused by cell growth and division. This term couples the morphology model (membrane area growth) with the functional model (surface display capacity) in the temporal domain.

The existence of dilution means that even with a strong promoter (high $G$), if cells grow too rapidly, surface display density may actually decrease rather than increase. This provides another physical basis for the "optimal window" we observe in G-scanning.

---

### 4.5 微重力下的体相浓度 vs 近表面浓度 / Bulk vs Near-Surface Concentration in Microgravity

**中文**

在微重力条件下，必须区分两个浓度概念：

- **体相浓度（Bulk concentration）**：远离任何界面的溶液主体中的纤维二糖浓度。
- **近表面浓度（Near-surface concentration）**：紧贴纤维素表面（细菌所在位置）的纤维二糖浓度。

在正常重力（1g）条件下，对流起到混合作用——体相浓度和近表面浓度大致处于平衡状态。但在微重力条件下，传质仅靠分子扩散。细菌在纤维素表面消耗纤维二糖后，近表面浓度会降低。如果没有对流来补充，耗尽区就会形成并持续存在。

这意味着：即使体相中平均纤维二糖浓度充足，细菌实际"看到"的近表面浓度可能非常低。模型必须区分这两个浓度尺度，以正确预测微重力下的系统行为。

> **注意：本节内容不完整。** 进一步的定量分析——包括边界层厚度估算、Sherwood 数分析以及微重力条件下传质限制的完整建模——仍在进行中，将在后续的模型迭代中补充。

**English**

Under microgravity conditions, two concentration concepts must be distinguished:

- **Bulk concentration**: The cellobiose concentration in the solution body far from any interface.
- **Near-surface concentration**: The cellobiose concentration immediately adjacent to the cellulose surface, where bacteria reside.

Under normal gravity (1g), convection provides mixing — bulk and near-surface concentrations remain roughly in equilibrium. Under microgravity, however, mass transport is by molecular diffusion alone. After bacteria consume cellobiose at the cellulose surface, the near-surface concentration drops. Without convection to replenish it, a depletion zone forms and persists.

This means: even if the average bulk cellobiose concentration is adequate, the near-surface concentration that bacteria actually "see" may be very low. The model must distinguish between these two concentration scales to correctly predict system behavior under microgravity.

> **Note: This section is incomplete.** Further quantitative analysis — including boundary layer thickness estimation, Sherwood number analysis, and full modeling of mass transfer limitations under microgravity — is ongoing and will be supplemented in subsequent model iterations.

---

## 5. 扩散-反应系统 / Diffusion-Reaction System

### 5.1 纤维二糖浓度场方程 / Cellobiose Concentration Field Equation

**中文**

纤维二糖在三维空间中的浓度演化由反应-扩散方程描述。系统包含三个物理过程：分子扩散、纤维素表面降解产生纤维二糖、以及细菌摄取消耗：

$$\frac{\partial c(\mathbf{x}, t)}{\partial t} = D \nabla^2 c(\mathbf{x}, t) + P_{\text{cellulose}}(\mathbf{x}, t) - R_{\text{uptake}}(c, \mathbf{x}, t)$$

其中：
- $c(\mathbf{x}, t)$ 是位置 $\mathbf{x}$ 和时间 $t$ 处的纤维二糖浓度
- $D$ 是纤维二糖在水中的扩散系数
- $P_{\text{cellulose}}(\mathbf{x}, t)$ 是纤维素表面降解产生纤维二糖的源项
- $R_{\text{uptake}}(c, \mathbf{x}, t)$ 是细菌摄取消耗项

源项 $P_{\text{cellulose}}$ 由表面展示纤维素酶的细菌在纤维素表面附近的活性决定：

$$P_{\text{cellulose}}(\mathbf{x}, t) = \sum_i k_{\text{deg}}\,N_{\text{cellulase}}^{(i)}\,B(\mathbf{x}_i)$$

其中 $k_{\text{deg}}$ 为纤维素酶降解速率常数，$N_{\text{cellulase}}^{(i)}$ 为第 $i$ 个细菌表面展示的纤维素酶数量，$B(\mathbf{x}_i)$ 指示细菌 $i$ 是否接触/靠近纤维素表面。这一源项正是正反馈的数学体现：细菌越靠近纤维素表面 → 产纤维二糖越多 → 吸引更多细菌。

**English**

The evolution of cellobiose concentration in three-dimensional space is described by a reaction-diffusion equation. The system involves three physical processes: molecular diffusion, cellobiose production from cellulose surface degradation, and bacterial uptake consumption:

$$\frac{\partial c(\mathbf{x}, t)}{\partial t} = D \nabla^2 c(\mathbf{x}, t) + P_{\text{cellulose}}(\mathbf{x}, t) - R_{\text{uptake}}(c, \mathbf{x}, t)$$

where:
- $c(\mathbf{x}, t)$ is the cellobiose concentration at position $\mathbf{x}$ and time $t$
- $D$ is the diffusion coefficient of cellobiose in water
- $P_{\text{cellulose}}(\mathbf{x}, t)$ is the production source term from cellulose degradation
- $R_{\text{uptake}}(c, \mathbf{x}, t)$ is the bacterial uptake/consumption term

The source term $P_{\text{cellulose}}$ is determined by the activity of surface-displayed cellulases on bacteria near the cellulose surface:

$$P_{\text{cellulose}}(\mathbf{x}, t) = \sum_i k_{\text{deg}}\,N_{\text{cellulase}}^{(i)}\,B(\mathbf{x}_i)$$

where $k_{\text{deg}}$ is the cellulase degradation rate constant, $N_{\text{cellulase}}^{(i)}$ is the number of cellulase enzymes displayed on the surface of bacterium $i$, and $B(\mathbf{x}_i)$ indicates whether bacterium $i$ is in contact with or near a cellulose surface. This source term is the mathematical embodiment of positive feedback: the closer bacteria are to the cellulose surface → the more cellobiose is produced → the more bacteria are attracted.

---

### 5.2 参数与数值值 / Parameters and Numerical Values

**中文**

| 参数 | 符号 | 值 | 单位 | 参考文献 |
|-----------|-------|-------|-------|-----------|
| 扩散系数 | $D$ | $5 \times 10^{-10}$ | m²/s | Gerchman & Weiss, 2004 |
| 热力学极限（预测） | $c_{\text{eq}}$ | {{placeholder:equilibrium_concentration}} | M | — |
| 消耗速率 | $R_{\text{max}}$ | {{placeholder:max_consumption_rate}} | $\mu$M/s/cell | 依赖 AscF 和 AscB 表达水平 |
| 趋化系数（预测） | $\chi$ | {{placeholder:chemotactic_coefficient}} | $\mu$m²/s | 待拟合 / To be fitted |

**English**

| Parameter | Symbol | Value | Units | Reference |
|-----------|--------|-------|-------|-----------|
| Diffusion coefficient | $D$ | $5 \times 10^{-10}$ | m²/s | Gerchman & Weiss, 2004 |
| Thermodynamic limit (predicted) | $c_{\text{eq}}$ | {{placeholder:equilibrium_concentration}} | M | — |
| Consumption rate | $R_{\text{max}}$ | {{placeholder:max_consumption_rate}} | $\mu$M/s/cell | Dependent on AscF and AscB expression levels |
| Chemotactic coefficient (predicted) | $\chi$ | {{placeholder:chemotactic_coefficient}} | $\mu$m²/s | To be fitted |

---

### 5.3 消耗项 / Consumption Term

**中文**

消耗项 $R_{\text{uptake}}(c, \mathbf{x}, t)$ 由在位置 $\mathbf{x}$ 附近的细菌的 AscF/AscB 活性决定：

$$R_{\text{uptake}}(c, \mathbf{x}, t) = \sum_{i \in \text{nearby agents}} \frac{N_0 G_i\,k_{\text{cat}} \cdot c(\mathbf{x}, t)}{K_S + c(\mathbf{x}, t)} \cdot \delta(\mathbf{x} - \mathbf{x}_i)$$

在我们的网格离散化方案中，这被实现为每个网格点附近的细菌智能体的 Michaelis-Menten 消耗速率之和。

**English**

The consumption term $R_{\text{uptake}}(c, \mathbf{x}, t)$ is determined by the AscF/AscB activity of bacteria near position $\mathbf{x}$:

$$R_{\text{uptake}}(c, \mathbf{x}, t) = \sum_{i \in \text{nearby agents}} \frac{N_0 G_i\,k_{\text{cat}} \cdot c(\mathbf{x}, t)}{K_S + c(\mathbf{x}, t)} \cdot \delta(\mathbf{x} - \mathbf{x}_i)$$

In our grid discretization scheme, this is implemented as the sum of Michaelis-Menten consumption rates of bacterial agents near each grid point.

---

### 5.4 微重力条件下的扩散 / Diffusion Under Microgravity Conditions

**中文**

在地面（1g）条件下，对流可能有助于质量传递。在微重力条件下，扩散是唯一的传质机制。我们的模型预测，在没有对流的情况下：

1. **耗尽区更大**：细菌在纤维二糖源周围的耗尽区半径约为 5 mm（Gesztesi et al., 2023）。
2. **梯度更陡**：由于缺少对流的混合作用，局部梯度更陡。
3. **趋化响应更强**：较陡的梯度可能增强 PTS 趋化的定向运动。

微重力条件下的具体参数为：

$$R_{\text{depletion}} \approx \sqrt{D \cdot \tau_{\text{depletion}}} \sim 5\ \text{mm}$$

其中 $R_{\text{depletion}}$ 是耗尽区特征半径，$\tau_{\text{depletion}}$ 是消耗特征时间尺度。

**English**

Under terrestrial (1g) conditions, convection may contribute to mass transport. Under microgravity, diffusion is the sole mass transfer mechanism. Our model predicts that in the absence of convection:

1. **Larger depletion zone**: The depletion zone radius around bacteria clustered near the cellulose source is approximately 5 mm (Gesztesi et al., 2023).
2. **Steeper gradients**: Due to the absence of convective mixing, local gradients are steeper.
3. **Stronger chemotactic response**: Steeper gradients may enhance directed movement in PTS chemotaxis.

The specific parameter under microgravity is:

$$R_{\text{depletion}} \approx \sqrt{D \cdot \tau_{\text{depletion}}} \sim 5\ \text{mm}$$

where $R_{\text{depletion}}$ is the characteristic depletion zone radius and $\tau_{\text{depletion}}$ is the characteristic consumption timescale.

---

### 5.5 纤维素表面边界条件 / Cellulose Surface Boundary Condition

**中文**

在纤维素表面，我们采用 Neumann 边界条件描述纤维二糖的通量：

$$-D \left.\frac{\partial c}{\partial n}\right|_{\text{surface}} = J_{\text{surface}} = \alpha \cdot \rho_{\text{bacteria}} \cdot E_{\text{cellulase}}$$

其中：
- $\partial c / \partial n$ 是垂直于纤维素表面的浓度梯度
- $J_{\text{surface}}$ 是纤维二糖从纤维素表面释放的通量
- $\alpha$ 是纤维素水解的动力学常数（每个酶分子每秒产生的纤维二糖分子数）
- $\rho_{\text{bacteria}}$ 是在纤维素表面附近的细菌密度
- $E_{\text{cellulase}}$ 是每个细菌表面展示的纤维素酶活性

**English**

At the cellulose surface, we use a Neumann boundary condition to describe the cellobiose flux:

$$-D \left.\frac{\partial c}{\partial n}\right|_{\text{surface}} = J_{\text{surface}} = \alpha \cdot \rho_{\text{bacteria}} \cdot E_{\text{cellulase}}$$

where:
- $\partial c / \partial n$ is the concentration gradient normal to the cellulose surface
- $J_{\text{surface}}$ is the cellobiose release flux from the cellulose surface
- $\alpha$ is the kinetic constant for cellulose hydrolysis (cellobiose molecules produced per enzyme molecule per second)
- $\rho_{\text{bacteria}}$ is the density of bacteria in the vicinity of the cellulose surface
- $E_{\text{cellulase}}$ is the cellulase activity displayed per bacterium on the surface

---

## 6. 增益因子 G 与优化 / Gain Factor G and Optimization

### 6.1 天线隐喻 / The Antenna Analogy

**中文**

AscF 转运蛋白就像细胞表面的信号天线。一部处于信号死角的手机会收不到消息，但如果有多根天线，即使微弱信号也能被捕获。过表达 AscF = 为细菌添加更多天线。

这个直觉构成了整个 G 因子分析的起点：转运蛋白数量不是代谢问题，而是**信号采集问题**。在微重力环境中，纤维二糖的浓度梯度浅且仅靠扩散维持——细菌需要足够的"天线"才能在噪声中检测到信号。

**English**

AscF transporters are like signal antennas on the cell surface. A phone in a dead zone cannot receive messages, but with multiple antennas, even weak signals can be captured. Overexpressing AscF = adding more antennas to the bacterium.

This intuition forms the starting point of the entire G factor analysis: transporter count is not a metabolic issue, but a **signal acquisition problem**. In the microgravity environment, cellobiose concentration gradients are shallow and maintained solely by diffusion — bacteria need enough "antennas" to detect the signal against the noise.

---

### 6.2 步骤一：转运通量 / Step 1: Transport Flux

**中文**

纤维二糖总转运速率由 Michaelis-Menten 动力学描述：

$$J = N_0 G \cdot \frac{k_{\text{cat}} \cdot c}{K_S + c}$$

其中：
- $J$ = 总转运通量（分子/秒/细胞）
- $N_0 G$ = 膜上 AscF 转运蛋白数量（$N_0$ 为参考表达水平，$G$ 为增益因子——我们可控的变量）
- $c$ = 细胞外纤维二糖浓度
- $k_{\text{cat}}$ = 单个 AscF 转运蛋白的催化速率
- $K_S$ = AscF 对纤维二糖的米氏常数（半最大速率时的底物浓度）

两种工作区制：

- **食物充足**（$c \gg K_S$）：$J \approx N_0 G \cdot k_{\text{cat}}$ —— 通量与转运蛋白数量呈线性关系
- **食物稀缺**（$c \ll K_S$，微重力常态）：$J \approx (N_0 G \cdot k_{\text{cat}} / K_S) \cdot c$ —— 通量与浓度和转运蛋白数量的乘积成正比。每一个额外的 AscF 分子都弥足珍贵

在微重力环境中，纤维二糖从纤维素表面向外扩散，远场的浓度极低。因此，我们的系统主要工作在**食物稀缺区制**——这意味着增加 $G$（即增加 $N_0 G$）直接放大转运通量，进而放大趋化信号。

**English**

The total cellobiose transport rate is described by Michaelis-Menten kinetics:

$$J = N_0 G \cdot \frac{k_{\text{cat}} \cdot c}{K_S + c}$$

Where:
- $J$ = total transport flux (molecules/sec/cell)
- $N_0 G$ = number of AscF transporters on the membrane ($N_0$ is the reference expression level, $G$ is the gain factor — the variable we control)
- $c$ = extracellular cellobiose concentration
- $k_{\text{cat}}$ = catalytic rate of a single AscF transporter
- $K_S$ = Michaelis constant of AscF for cellobiose (substrate concentration at half-maximal rate)

Two regimes:

- **Abundant food** ($c \gg K_S$): $J \approx N_0 G \cdot k_{\text{cat}}$ — flux scales linearly with transporter count
- **Scarce food** ($c \ll K_S$, the microgravity norm): $J \approx (N_0 G \cdot k_{\text{cat}} / K_S) \cdot c$ — flux is proportional to BOTH concentration AND transporter count. Every additional AscF molecule is precious

In the microgravity environment, cellobiose diffuses outward from the cellulose surface, and the far-field concentration is extremely low. Our system therefore operates predominantly in the **scarce food regime** — meaning that increasing $G$ (i.e., increasing $N_0 G$) directly amplifies the transport flux, and consequently amplifies the chemotactic signal.

---

### 6.3 步骤二：增益因子 G / Step 2: Gain Factor G

**中文**

定义无量纲参数 $G$ 为相对于工程参考表达水平的增益倍数：

$$N_{\text{AscF}} = N_0 G$$

其中：
- $N_0$ = 参考启动子（如 J23116）下单个细胞的 AscF 蛋白数量
- $G$ = 相对于该参考水平的表达增益（$G = 1$ 对应参考水平）

关键洞察：增大 $G$ 通过增加总转运通量来放大 PTS 趋化信号，从而加速 EI 去磷酸化。与 MCP 趋化系统不同（在该系统中，"更多受体"的效果会被甲基化适应回路抵消），在 PTS 趋化中，更多转运蛋白直接意味着更强的信号。

在 MG1655 中，asc 操纵子在标准实验室条件下通常是沉默的（Jahreis et al., 2008 *BMC Microbiology*），因此野生型 AscF 表达水平极低，趋近于零。**$G$ 不表示相对于野生型的倍数**——否则"零乘以任何倍数仍为零"。$G$ 表示相对于工程参考表达水平的倍数。

**须注意**：$G$ 不能无限制增大。膜面积约束（见第 4 节）为 $G$ 设定了物理上限——过表达不仅会饱和趋化信号，还会导致膜毒性。

**English**

Define a dimensionless parameter $G$ as the gain factor relative to an engineered reference expression level:

$$N_{\text{AscF}} = N_0 G$$

Where:
- $N_0$ = number of AscF proteins per cell under a reference promoter (e.g., J23116)
- $G$ = expression gain relative to that reference level ($G = 1$ corresponds to the reference)

The key insight: increasing $G$ amplifies the PTS chemotaxis signal by increasing the total transport flux, which accelerates EI dephosphorylation. Unlike the MCP chemotaxis system — where the effect of "more receptors" is cancelled out by the methylation adaptation loop — in PTS chemotaxis, more transporters directly mean a stronger signal.

In MG1655, the *asc* operon is typically silent under standard laboratory conditions (Jahreis et al., 2008 *BMC Microbiology*), so the wild-type AscF expression level is extremely low, approaching zero. **$G$ does NOT represent fold-change relative to wild-type** — otherwise "zero times any fold equals zero." $G$ represents fold-change relative to an engineered reference expression level.

**Importantly**: $G$ cannot be increased without bound. The membrane area constraint (see Section 4) imposes a physical upper limit on $G$ — overexpression not only saturates the chemotactic signal but also causes membrane toxicity.

---

### 6.4 步骤三：完整模型耦合 / Step 3: Full Model Coupling

**中文**

将 $G$ 纳入 PTS 信号转导框架后，稳态 EI 去磷酸化分数 $e^*$ 由转运通量与再磷酸化能力的平衡决定。在低通量近似（$J \ll k_r E_T$）下，$e^* \propto J(S,G)$。更一般地，信号输入强度与再磷酸化能力的比值决定了趋化输出：

$$\frac{J(S,G)}{k_r E_T} = \frac{N_0 G \cdot k_{\text{cat}} \cdot c}{k_r E_T \cdot (K_S + c)}$$

- **分子**：总转运通量 $J(S,G)$ — 代表"信号输入强度"
- **分母**：$k_r E_T$ — 代表"系统 EI 再磷酸化吞吐量"

当该比值较大 → 转运通量压倒了再磷酸化 → EI 以去磷酸化状态累积 → CheA 被强抑制 → 趋化信号被放大。

这一耦合关系的物理含义：趋化输出不是由单一因素决定的，而是由**转运通量（信号输入）与再磷酸化能力（信号重置）之间的博弈**决定。在微重力条件下，由于 $c$ 通常很小（$c \ll K_S$），通量的绝对水平较低，因此增大 $G$ 是提升信号输入强度的核心手段。

**English**

Incorporating $G$ into the PTS signaling framework, the steady-state EI dephosphorylation fraction $e^*$ is determined by the balance between transport flux and re-phosphorylation capacity. Under the low-flux approximation ($J \ll k_r E_T$), $e^* \propto J(S,G)$. More generally, the ratio of signal input strength to re-phosphorylation capacity determines chemotactic output:

$$\frac{J(S,G)}{k_r E_T} = \frac{N_0 G \cdot k_{\text{cat}} \cdot c}{k_r E_T \cdot (K_S + c)}$$

- **Numerator**: total transport flux $J(S,G)$ — represents "signal input strength"
- **Denominator**: $k_r E_T$ — represents the system's overall EI re-phosphorylation throughput

When this ratio is large → transport overwhelms re-phosphorylation → EI accumulates in dephosphorylated state → CheA strongly inhibited → chemotactic signal amplified.

The physical meaning of this coupling: chemotactic output is not determined by any single factor, but by the **contest between transport flux (signal input) and re-phosphorylation capacity (signal reset)**. Under microgravity conditions, since $c$ is typically small ($c \ll K_S$), the absolute flux level is low, making an increase in $G$ the central means of boosting signal input strength.

---

### 6.5 步骤四：表观解离常数 / Step 4: The Effective Dissociation Constant

**中文**

进一步推导得到一个非常简洁的结果。定义 $k_r E_T$ 为系统的**总再磷酸化能力**（单位时间内能将多少 EI 分子重新磷酸化），则表观解离常数为：

$$K_D^{\text{eff}} = \frac{k_r E_T \cdot K_I \cdot K_S}{N_0 G \cdot k_{\text{cat}}}$$

其中 $K_I$ 为非磷酸化 EI 对 CheA 的半抑制常数。$k_r E_T$（分子/s）具有明确的物理含义——系统的磷酸化"复位"吞吐量。

$K_D^{\text{eff}}$ 是**灵敏度阈值**——在该纤维二糖浓度下，趋化响应达到半最大值。$K_D^{\text{eff}}$ 越小 = 检测越灵敏（"嗅觉越好"）。

**重要限定：** $K_D^{\text{eff}}$ 这一解析表达式仅在**低通量近似**（$J \ll k_r E_T$）和**低浓度近似**（$c \ll K_S$）下严格成立。当糖浓度较高、转运接近饱和时，需使用完整的 ODE 系统（见 §3.5）。在仿真中，我们始终使用完整方程；$K_D^{\text{eff}}$ 主要用于定性解释——说明为何过表达 AscF 可以降低感知阈值。

关键点在于 $G$ 位于**分母**：

$$G \uparrow \quad \Longrightarrow \quad N_0 G \uparrow \quad \Longrightarrow \quad K_D^{\text{eff}} \downarrow$$

**更高的 G → 更低的检测阈值 → 更灵敏的趋化性。**

这一推导也解释了为什么经典 MCP 趋化系统（通过构建更好的受体来扩大动态范围）与 PTS 趋化系统（通过增加转运蛋白数量来降低检测阈值）的策略方向截然不同：MCP 系统通过结构工程改造受体的亲和力，而 PTS 系统通过**拷贝数**来调节灵敏度。

**English**

Further derivation yields a remarkably simple result. Define $k_r E_T$ as the system's **total re-phosphorylation capacity** (how many EI molecules can be re-phosphorylated per unit time). The effective dissociation constant is then:

$$K_D^{\text{eff}} = \frac{k_r E_T \cdot K_I \cdot K_S}{N_0 G \cdot k_{\text{cat}}}$$

where $K_I$ is the half-inhibition constant of dephosphorylated EI on CheA. This form gives clear dimensional meaning: $k_r E_T$ (molecules/s) represents the system's phosphorylation "reset" throughput.

$K_D^{\text{eff}}$ is the **sensitivity threshold** — the cellobiose concentration at which the chemotactic response is half-maximal. SMALLER $K_D^{\text{eff}}$ = MORE SENSITIVE detection ("better sense of smell").

**Important caveat:** This analytical expression for $K_D^{\text{eff}}$ holds strictly only under the **low-flux approximation** ($J \ll k_r E_T$) and **low-concentration approximation** ($c \ll K_S$). When sugar concentrations are higher and transport approaches saturation, the full ODE system (§3.5) must be used. In our simulations, we always use the full equations; $K_D^{\text{eff}}$ serves primarily as a qualitative explanation of why overexpressing AscF lowers the sensing threshold.

Critically, $G$ appears in the DENOMINATOR:

$$G \uparrow \quad \Longrightarrow \quad N_0 G \uparrow \quad \Longrightarrow \quad K_D^{\text{eff}} \downarrow$$

**Higher G → Lower Detection Threshold → More Sensitive Chemotaxis.**

This derivation also explains why the strategic direction for the classical MCP chemotaxis system (build better receptors to expand dynamic range) is fundamentally different from that for the PTS chemotaxis system (increase transporter count to lower the detection threshold): the MCP system adjusts receptor affinity through structural engineering, whereas the PTS system modulates sensitivity through **copy number**.

---

### 6.6 步骤五：最优窗口 / Step 5: The Optimal Window

**中文**

然而，过表达并非没有代价。存在三个约束条件：

1. **PEP 池是有限的。** PEP 是糖酵解中间体；其总细胞浓度受代谢调控，不会随 EII 过表达而增加。高转运通量会消耗 PEP，可能与糖酵解竞争并抑制生长。

2. **EI 总蛋白量是固定的。** $E_T$ 受内源性 *ptsI* 表达限制。当转运通量 $J(S,G) \gg$ 再磷酸化能力（$k_r E_T$）时，$e \to 1$，即使痕量纤维二糖也几乎能使所有 EI 去磷酸化。趋化响应变为**"全或无"（all-or-none）**——一旦达到饱和，梯度分辨能力即告丧失。

3. **膜蛋白毒性。** AscF 是一种具有 8-10 个跨膜螺旋的内膜蛋白。大量过表达会扰乱膜蛋白稳态，可能激活 $\sigma^E$ 包膜应激反应并损害细胞健康。

因此，$G$ 存在一个**最优窗口**——太低 = 信号放大不足；太高 = 信号饱和 + 代谢负担 + 膜胁迫。

$$G_{opt} = \arg\max_G \left[ \text{Chemotactic Sensitivity}(G) - \lambda \cdot \text{Metabolic Cost}(G) \right]$$

预测形状为**单峰（钟形）**——G 扫描模拟将确定最优窗口的确切位置和宽度。{{data:g_scan_results}}

这三个约束条件在不同 $G$ 值区间起主导作用：低 $G$ 区间受限于灵敏度不足（约束 2 不相关，因为通量远低于再磷酸化能力）；中等 $G$ 区间为最优工作区；高 $G$ 区间先后被信号饱和（约束 2）和膜毒性（约束 3）所限制。PEP 消耗（约束 1）是一个贯穿各区间的持续性代价，但其影响在高 $G$ 区间显著加剧。

**English**

However, overexpression is not without cost. Three constraints:

1. **PEP pool is finite.** PEP is a glycolysis intermediate; its total cellular concentration is metabolically regulated and does not increase with EII overexpression. High transport flux drains PEP, potentially competing with glycolysis and inhibiting growth.

2. **Total EI protein is fixed.** $E_T$ is limited by endogenous *ptsI* expression. When transport flux $J(S,G) \gg$ re-phosphorylation capacity ($k_r E_T$), $e \to 1$ and even trace cellobiose can dephosphorylate nearly all EI. The chemotactic response becomes **"all-or-none"** — gradient discrimination is lost once saturation is reached.

3. **Membrane protein toxicity.** AscF is an inner membrane protein with 8–10 transmembrane helices. Massive overexpression disrupts membrane protein homeostasis, potentially activating the $\sigma^E$ envelope stress response and impairing cell health.

Therefore, $G$ has an **OPTIMAL WINDOW** — too low = insufficient signal amplification; too high = signal saturation + metabolic burden + membrane stress.

$$G_{opt} = \arg\max_G \left[ \text{Chemotactic Sensitivity}(G) - \lambda \cdot \text{Metabolic Cost}(G) \right]$$

The shape is predicted to be **unimodal (bell-shaped)** — G-scan simulation will determine the exact position and width of the optimum. {{data:g_scan_results}}

The three constraints dominate in different $G$ regimes: the low-$G$ regime is limited by insufficient sensitivity (constraint 2 is irrelevant because flux is far below re-phosphorylation capacity); the mid-$G$ regime is the optimal operating zone; the high-$G$ regime is successively limited by signal saturation (constraint 2) and membrane toxicity (constraint 3). PEP consumption (constraint 1) is a persistent cost across all regimes, but its impact intensifies significantly in the high-$G$ regime.

---

### 6.7 步骤六：启动子文库 / Step 6: Promoter Library for G-Scan

**中文**

为了通过实验验证 $G_{opt}$ 预测，我们构建了一个启动子文库：

| 启动子 | 相对强度 | 预期 G 区间 |
|----------|------------------|-------------------|
| J23118 | ~0.06 | 近基线 ($G \approx 1$) |
| J23116 | ~0.16 | 低（Cycle 1 基线） |
| J23113 | ~0.33 | 低-中 |
| J23109 | ~0.56 | 中 |
| J23105 | ~0.74 | 中-高 |
| J23102 | ~0.86 | 强 |
| J23100 | ~1.00 | 最强 |

模型预测最优窗口位于 J23109–J23105 范围内。这一预测的逻辑如下：J23118/J23116 提供的表达水平过低，信号放大不足，无法在微重力条件的低浓度下产生有意义的趋化偏倚；J23102/J23100 则可能进入信号饱和区和膜毒性区。J23109–J23105 的中等强度区间恰好平衡了信号放大与系统稳定性。{{placeholder:promoter_scan_results}}

该文库的设计并非均匀采样——我们在低强度区域设置了多个梯度（J23118/J23116/J23113），以精确确定"信号开始出现"的阈值；在高强度区域则间距较大，主要用于验证饱和边界。这种非均匀采样策略提高了在最优窗口附近的实验分辨率。

**English**

To experimentally validate the $G_{opt}$ prediction, we built a promoter library:

| Promoter | Relative Strength | Expected G regime |
|----------|------------------|-------------------|
| J23118 | ~0.06 | Near-baseline ($G \approx 1$) |
| J23116 | ~0.16 | Low (Cycle 1 baseline) |
| J23113 | ~0.33 | Low-medium |
| J23109 | ~0.56 | Medium |
| J23105 | ~0.74 | Medium-high |
| J23102 | ~0.86 | Strong |
| J23100 | ~1.00 | Strongest |

The model predicts the optimal window lies in the J23109–J23105 range. The logic behind this prediction: J23118/J23116 provide expression levels that are too low, giving insufficient signal amplification to produce a meaningful chemotactic bias at the low concentrations typical of microgravity; J23102/J23100 are likely to enter the signal saturation and membrane toxicity regimes. The mid-range strengths of J23109–J23105 strike the right balance between signal amplification and system stability. {{placeholder:promoter_scan_results}}

The library design does not use uniform sampling — we placed multiple gradient points in the low-strength region (J23118/J23116/J23113) to precisely determine the threshold where "the signal begins to appear"; the high-strength region has wider spacing, mainly for verifying the saturation boundary. This non-uniform sampling strategy improves experimental resolution in the vicinity of the optimal window.

---

### 6.8 G 扫描模拟计划 / G-Scan Simulation Plan

**中文**

我们计划执行 $G$ 扫描模拟，以测试上述预测：

- $G$ 范围：$10^{-1}, 10^0, 10^1, 10^2, 10^3, 10^4$（涵盖 5 个数量级）
- 每次模拟在相同的初始条件（均匀细菌分布、点纤维二糖源）下运行
- 输出指标：趋化指数 $\text{CI}$、到达纤维二糖源的细菌比例、平均趋化速度
- 同时监控膜占用率 $\phi$ 和膜健康 $H(\phi)$，标记超过临界阈值的 $G$ 值
- 额外输出：$K_D^{eff}$ 随 $G$ 的变化曲线，验证 $K_D^{eff} \propto 1/G$ 的预测关系

预期的 $G$-CI 曲线将呈现单峰形状，在 $G_{\text{opt}}$ 处达到峰值，之后可能因膜毒性或信号饱和而下降。我们将比较模拟结果与实验毛细管趋化试验的结果。

**English**

We plan to perform a $G$-scan simulation to test the above predictions:

- $G$ range: $10^{-1}, 10^0, 10^1, 10^2, 10^3, 10^4$ (spanning 5 orders of magnitude)
- Each simulation run under identical initial conditions (uniform bacterial distribution, point cellobiose source)
- Output metrics: chemotactic index $\text{CI}$, fraction of bacteria reaching the cellobiose source, average chemotactic drift velocity
- Simultaneously monitor membrane occupancy rate $\phi$ and membrane health $H(\phi)$, flagging $G$ values exceeding critical thresholds
- Additional output: $K_D^{eff}$ vs. $G$ curve, validating the predicted $K_D^{eff} \propto 1/G$ relationship

The expected $G$-CI curve will have a unimodal shape, peaking at $G_{\text{opt}}$, and potentially declining thereafter due to membrane toxicity or signal saturation. We will compare simulation results with experimental capillary chemotaxis assay results.

---

## 7. 正反馈模块 / Positive Feedback Module

### 7.1 耦合机制 / Coupling Mechanism

**中文**

正反馈模块描述了整个系统的核心耦合：细菌聚集 → 纤维素降解 → 纤维二糖释放 → 吸引更多细菌。

这是一个典型的自催化正反馈循环：

```
细菌在纤维素表面聚集
        ↓
纤维素酶在表面展示（INP-纤维素酶）
        ↓
纤维素被水解 → 纤维二糖局部释放
        ↓
纤维二糖浓度梯度建立
        ↓
PTS 趋化吸引更多细菌向表面运动
        ↓
（循环回到第一步）
```

**English**

The positive feedback module describes the core coupling of the entire system: bacterial aggregation → cellulose degradation → cellobiose release → attraction of more bacteria.

This is a classic autocatalytic positive feedback loop:

```
Bacteria aggregate at the cellulose surface
        ↓
Cellulase displayed on the surface (INP-cellulase)
        ↓
Cellulose is hydrolyzed → local cellobiose release
        ↓
Cellobiose concentration gradient is established
        ↓
PTS chemotaxis attracts more bacteria to the surface
        ↓
(Loops back to step 1)
```

---

### 7.2 数学模型 / Mathematical Formulation

**中文**

纤维二糖从纤维素表面的释放通量 $J_{\text{surface}}$ 是表面细菌密度的函数：

$$J_{\text{surface}}(\mathbf{x}, t) = \beta \cdot \rho_{\text{surface}}(\mathbf{x}, t) \cdot [E]_{\text{INP-cellulase}}$$

其中：
- $\beta$ 是每个纤维素酶的纤维二糖产率常数
- $\rho_{\text{surface}}(\mathbf{x}, t)$ 是纤维素表面附近的局部细菌密度
- $[E]_{\text{INP-cellulase}}$ 是每个细菌表面的 INP-纤维素酶水平

结合扩散-反应方程，我们得到：

$$\frac{\partial c}{\partial t} = D \nabla^2 c - R(c)$$

边界条件在纤维素表面：

$$-D \left.\frac{\partial c}{\partial n}\right|_{\text{surface}} = \beta \cdot \rho_{\text{surface}} \cdot [E]_{\text{INP-cellulase}}$$

**English**

The cellobiose release flux $J_{\text{surface}}$ from the cellulose surface is a function of the local bacterial density at the surface:

$$J_{\text{surface}}(\mathbf{x}, t) = \beta \cdot \rho_{\text{surface}}(\mathbf{x}, t) \cdot [E]_{\text{INP-cellulase}}$$

where:
- $\beta$ is the cellobiose yield constant per cellulase molecule
- $\rho_{\text{surface}}(\mathbf{x}, t)$ is the local bacterial density near the cellulose surface
- $[E]_{\text{INP-cellulase}}$ is the INP-cellulase level per bacterium on the surface

Combined with the diffusion-reaction equation, we obtain:

$$\frac{\partial c}{\partial t} = D \nabla^2 c - R(c)$$

with the boundary condition at the cellulose surface:

$$-D \left.\frac{\partial c}{\partial n}\right|_{\text{surface}} = \beta \cdot \rho_{\text{surface}} \cdot [E]_{\text{INP-cellulase}}$$

---

### 7.3 "暗启动"条件 / The "Dark Start" Condition

**中文**

初始条件设置为纤维二糖浓度为零（$c(\mathbf{x}, 0) = 0$）。这意味着信号必须从噪声中出现。这是我们的模型需要解决的一个具有挑战性的问题：如果一开始没有纤维二糖，细菌最初如何聚集到纤维素表面？

我们假设有两种可能的机制：

1. **随机涨落**：即使所有位置的平均浓度为 0，也存在局部涨落。个别细菌可能随机接触纤维素表面并开始释放低水平的纤维二糖。然后，该信号通过正反馈被放大。
2. **基础渗漏**：未诱导条件下 INP-纤维素酶可能存在低水平的本底表达，产生痕量的纤维二糖。

在我们的模拟中，我们通过向初始条件添加微小高斯噪声来建模"暗启动"：

$$c(\mathbf{x}, 0) = \epsilon(\mathbf{x})$$

其中 $\epsilon(\mathbf{x}) \sim \mathcal{N}(0, \sigma^2)$，$\sigma$ 很小（例如 $10^{-9}$ M）。

该正反馈系统的行为可能表现出阈值效应：低于临界细菌密度，纤维二糖的产生不足以维持梯度；高于临界密度，正反馈启动，形成稳定集群。

**English**

The initial condition is set to zero cellobiose concentration ($c(\mathbf{x}, 0) = 0$). This means the signal must emerge from noise. This presents a challenging problem for our model: if no cellobiose is initially present, how do bacteria first aggregate at the cellulose surface?

We hypothesize two possible mechanisms:

1. **Stochastic fluctuations**: Even though the average concentration at all positions is 0, local fluctuations exist. Individual bacteria may randomly contact the cellulose surface and begin releasing low levels of cellobiose. This signal is then amplified by the positive feedback.
2. **Basal leakage**: Low-level background expression of INP-cellulase may occur even under uninduced conditions, producing trace amounts of cellobiose.

In our simulation, we model the "dark start" by adding small Gaussian noise to the initial condition:

$$c(\mathbf{x}, 0) = \epsilon(\mathbf{x})$$

where $\epsilon(\mathbf{x}) \sim \mathcal{N}(0, \sigma^2)$, with small $\sigma$ (e.g., $10^{-9}$ M).

The behavior of this positive feedback system is expected to exhibit a threshold effect: below a critical bacterial density, cellobiose production is insufficient to sustain a gradient; above the critical density, positive feedback engages and a stable cluster forms.

---

## 8. 验证计划 / Validation Plan

### 8.1 毛细管趋化试验验证 / Capillary Chemotaxis Assay Validation

**中文**

我们计划通过毛细管趋化试验来验证模型的预测。在该试验中：

1. 将含有不同浓度纤维二糖的毛细管插入细菌悬浮液中。
2. 测量一段时间后进入毛细管的细菌数量。
3. 将实验数据与模型预测进行比较。

具体验证指标：

| 参数 | 实验测量 | 模型预测 | 比较方法 |
|-----------|----------------|-------------|-------------------|
| 趋化指数 $\text{CI}$ | 毛细管中细菌计数 | 模拟的积聚比 | 定量拟合 |
| 最佳浓度 $[S]_{\text{opt}}$ | 不同浓度的峰值 | $G$ 扫描预测 | 峰值位置比对 |
| 响应时间 | 细菌进入的时程 | 模拟的时间演化 | 定性比对 |
| $G$ 依赖关系 | 不同诱导剂浓度 | 不同 $G$ 值 | 曲线形状比对 |

{{placeholder:capillary_assay_comparison}}

**English**

We plan to validate model predictions through capillary chemotaxis assays. In this assay:

1. Capillaries containing different concentrations of cellobiose are inserted into a bacterial suspension.
2. The number of bacteria entering the capillary over time is measured.
3. Experimental data are compared with model predictions.

Specific validation metrics:

| Parameter | Experimental Measurement | Model Prediction | Comparison Method |
|-----------|------------------------|-----------------|-------------------|
| Chemotactic index $\text{CI}$ | Bacterial count in capillary | Simulated accumulation ratio | Quantitative fitting |
| Optimal concentration $[S]_{\text{opt}}$ | Peak across different concentrations | $G$-scan prediction | Peak position matching |
| Response time | Time course of bacterial entry | Simulated temporal evolution | Qualitative comparison |
| $G$ dependence | Different inducer concentrations | Different $G$ values | Curve shape comparison |

{{placeholder:capillary_assay_comparison}}

---

### 8.2 降解速率验证 / Degradation Rate Validation

**中文**

我们将通过纤维素降解实验来验证扩散-反应和正反馈模块的预测：

1. 将工程菌株与纤维素底物共培养。
2. 通过 DNS 比色法或 HPLC 测量纤维二糖和葡萄糖的累积。
3. 与模型预测的降解速率进行比较。

{{placeholder:degradation_rate_comparison}}

**English**

We will validate the diffusion-reaction and positive feedback module predictions through cellulose degradation experiments:

1. Co-culture the engineered strain with a cellulose substrate.
2. Measure cellobiose and glucose accumulation via DNS colorimetric assay or HPLC.
3. Compare with model-predicted degradation rates.

{{placeholder:degradation_rate_comparison}}

---

### 8.3 重力效应验证 / Gravity Effect Validation

**中文**

为了验证微重力效应预测，我们计划：

1. **地面实验（1g）**：在标准实验室条件下进行实验，作为基线对照。
2. **模拟微重力**：使用回转器（clinostat）模拟微重力环境。
3. **模型比较**：比较 1g 和模拟微重力条件下观测到的降解速率和细菌分布是否与模型预测一致。

预测：在模拟微重力条件下，由于对流减少，耗尽区更大，梯度更陡，趋化响应可能增强。然而，由于质量传递的限制，总体降解速率可能降低。

{{placeholder:gravity_comparison}}

**English**

To validate microgravity effect predictions, we plan:

1. **Ground experiment (1g)**: Conduct experiments under standard laboratory conditions as a baseline control.
2. **Simulated microgravity**: Use a clinostat (rotating bioreactor) to simulate microgravity conditions.
3. **Model comparison**: Compare observed degradation rates and bacterial distributions in 1g vs. simulated microgravity with model predictions.

Prediction: Under simulated microgravity conditions, due to reduced convection, the depletion zone will be larger, gradients will be steeper, and chemotactic response may be enhanced. However, the overall degradation rate may be reduced due to mass transfer limitations.

{{placeholder:gravity_comparison}}

---

### 8.4 膜占用率验证 / Membrane Occupancy Validation

**中文**

形态模型的膜占用率预测将通过以下方式验证：

1. 在不同启动子强度下测量 AscF 和 INP-纤维素酶的表达水平（通过荧光报告蛋白融合）。
2. 测量相应的生长速率变化（通过 OD600 时间曲线）。
3. 将膜占用率 $\phi$ 的预测值与观测到的生长抑制阈值进行比较。

{{placeholder:membrane_occupancy_validation}}

**English**

The morphology model's membrane occupancy predictions will be validated as follows:

1. Measure AscF and INP-cellulase expression levels at different promoter strengths (via fluorescent reporter fusion).
2. Measure corresponding growth rate changes (via OD600 time course).
3. Compare predicted membrane occupancy $\phi$ values with observed growth inhibition thresholds.

{{placeholder:membrane_occupancy_validation}}

---

## 9. 计划输出 / Planned Outputs

### 9.1 G 扫描曲线 / G-Scan Curve

**中文**

将生成趋化指数 $\text{CI}$ 与增益因子 $G$ 的关系曲线。预期该曲线呈现钟形（单峰），在 $G_{\text{opt}}$ 处达到最大 $\text{CI}$。该输出将直接指导我们选择诱导型启动子的强度。

预期特征：
- 在 $G_{\text{opt}}$ 处 $\text{CI}$ 峰值
- 在 $G \ll G_{\text{opt}}$ 时趋近零
- 在 $G \gg G_{\text{opt}}$ 时下降至低水平（信号饱和或膜毒性）

{{placeholder:g_scan_curve_figure}}

**English**

A plot of the chemotactic index $\text{CI}$ versus the gain factor $G$ will be generated. The curve is expected to be bell-shaped (unimodal), with maximum $\text{CI}$ at $G_{\text{opt}}$. This output will directly guide our selection of inducible promoter strength.

Expected characteristics:
- $\text{CI}$ peak at $G_{\text{opt}}$
- Approaches zero at $G \ll G_{\text{opt}}$
- Declines to low levels at $G \gg G_{\text{opt}}$ (signal saturation or membrane toxicity)

{{placeholder:g_scan_curve_figure}}

---

### 9.2 空间分布快照 / Spatial Distribution Snapshots

**中文**

将在不同时间点（$t = 0, 1, 10, 60, 360, 1440$ 分钟）生成细菌智能体的三维空间分布。这些快照将直观展示：

- 细菌向纤维素表面的趋化聚集过程
- 耗尽区的形成和演化
- 正反馈循环的建立

{{placeholder:spatial_snapshots_figure}}

**English**

Three-dimensional spatial distributions of bacterial agents will be generated at various time points ($t = 0, 1, 10, 60, 360, 1440$ minutes). These snapshots will visually demonstrate:

- The chemotactic aggregation process of bacteria toward the cellulose surface
- The formation and evolution of the depletion zone
- The establishment of the positive feedback loop

{{placeholder:spatial_snapshots_figure}}

---

### 9.3 降解速率比较 / Degradation Rate Comparison

**中文**

将生成 1g 与模拟 0g 条件下纤维素降解速率的比较图。预期结果：

- 1g：对流辅助传质，总体降解速率较高
- 0g（模拟）：仅扩散传质，降解速率可能较低，但细菌在表面的局部浓度可能更高

{{placeholder:degradation_rate_comparison_figure}}

**English**

A comparative plot of cellulose degradation rates under 1g vs. simulated 0g conditions will be generated. Expected results:

- 1g: Convection-assisted mass transfer, higher overall degradation rate
- 0g (simulated): Diffusion-only mass transfer, possibly lower degradation rate but potentially higher local bacterial concentration at the surface

{{placeholder:degradation_rate_comparison_figure}}

---

### 9.4 膜占用-健康曲线 / Membrane Occupancy-Health Curve

**中文**

将生成膜健康 $H(\phi)$ 与膜占用率 $\phi$ 的关系曲线。该曲线将确定在膜健康开始下降之前的最大允许工程蛋白表达水平。该输出将与 G 扫描结果交叉分析，以识别同时满足趋化性能和膜完整性要求的设计空间。

{{placeholder:membrane_health_curve_figure}}

**English**

A plot of membrane health $H(\phi)$ versus membrane occupancy $\phi$ will be generated. This curve will identify the maximum allowable engineered protein expression level before membrane health begins to decline. This output will be cross-analyzed with G-scan results to identify the design space satisfying both chemotactic performance and membrane integrity requirements.

{{placeholder:membrane_health_curve_figure}}

---

### 9.5 灵敏度分析 / Sensitivity Analysis

**中文**

将进行参数扰动灵敏度分析，以确定哪些参数对模型输出影响最大。我们将逐个扰动每个参数 $\pm 10\%$，并记录对以下输出的影响：

- 趋化指数 $\text{CI}$
- 达到稳态的时间
- 细菌在表面的最大积累量
- 膜健康 $H(\phi)$

灵敏度系数定义为：

$$S_{p} = \frac{\partial \ln(\text{output})}{\partial \ln(p)} \approx \frac{\Delta \text{output} / \text{output}}{\Delta p / p}$$

具有高 $|S_p|$ 值的参数被确定为实验中最需要精确控制的参数。

{{placeholder:sensitivity_analysis_results}}

**English**

A parameter perturbation sensitivity analysis will be performed to identify which parameters have the greatest influence on model outputs. Each parameter will be perturbed by $\pm 10\%$ and the effect on the following outputs will be recorded:

- Chemotactic index $\text{CI}$
- Time to reach steady state
- Maximum bacterial accumulation at the surface
- Membrane health $H(\phi)$

The sensitivity coefficient is defined as:

$$S_{p} = \frac{\partial \ln(\text{output})}{\partial \ln(p)} \approx \frac{\Delta \text{output} / \text{output}}{\Delta p / p}$$

Parameters with high $|S_p|$ values are identified as those requiring the most precise control in experiments.

{{placeholder:sensitivity_analysis_results}}

---

## 10. 参数汇总表 / Parameter Summary Table

### 10.1 趋化参数 / Chemotaxis Parameters

| 参数 | 符号 | 值 | 单位 | 参考文献 |
|-----------|-------|-------|-------|-----------|
| 游动速度 | $v$ | 25 | $\mu$m/s | Berg & Brown, 1972 |
| 最小翻转速率 | $\lambda_{\min}$ | {{placeholder:lambda_min}} | s$^{-1}$ | 待估计 / To be estimated |
| 最大翻转速率 | $\lambda_{\max}$ | {{placeholder:lambda_max}} | s$^{-1}$ | 待估计 / To be estimated |
| 翻转时间 | $\tau_{\text{tumble}}$ | 0.1 | s | Berg, 2004 |
| AscF 米氏常数（纤维二糖） | $K_S$ | 20–50 | $\mu$M | Hall & Xu, 1992 |
| AscF 转换数 | $k_{\text{cat}}$ | {{placeholder:k_cat_value}} | s$^{-1}$ | 待估计 / To be estimated |
| 参考表达下 AscF 数量 | $N_0$ | {{placeholder:N0_value}} | 分子/细胞 | 待测定 / To be measured |
| CheY-P Hill 系数 | $h$ | 10.3 | — | Cluzel et al., 2000 *Science* |
| CheY-P 马达切换阈值 | $K_Y$ | 3.1 | $\mu$M | Cluzel et al., 2000 *Science* |
| 总 EI 浓度 | $E_T$ | {{placeholder:ET_value}} | $\mu$M | Rohwer et al., 2000 *JBC* |
| EI 去磷酸化速率常数 | $k_d$ | {{placeholder:kd_value}} | ($\mu$M·s)$^{-1}$ | 待估计 / To be estimated |
| EI 再磷酸化速率常数 | $k_r$ | {{placeholder:kr_value}} | s$^{-1}$ | 待估计（隐含 PEP） |
| EI 对 CheA 半抑制常数 | $K_I$ | {{placeholder:KI_value}} | $\mu$M | 待估计 / To be estimated |
| 总 CheA 浓度 | $A_T$ | {{placeholder:AT_value}} | $\mu$M | Rohwer et al., 2000 *JBC* |
| 总 CheY 浓度 | $Y_T$ | {{placeholder:YT_value}} | $\mu$M | Rohwer et al., 2000 *JBC* |
| CheY 磷酸化速率 | $k_Y$ | {{placeholder:kY_value}} | $\mu$M$^{-1}$ s$^{-1}$ | Rohwer et al., 2000 *JBC* |
| CheY-P 去磷酸化速率 | $k_Z$ | {{placeholder:kZ_value}} | s$^{-1}$ | Rohwer et al., 2000 *JBC* |

---

### 10.2 扩散与反应参数 / Diffusion and Reaction Parameters

| 参数 | 符号 | 值 | 单位 | 参考文献 |
|-----------|-------|-------|-------|-----------|
| 纤维二糖扩散系数 | $D$ | $5 \times 10^{-10}$ | m²/s | Gerchman & Weiss, 2004 |
| 耗尽区半径（0g） | $R_{\text{depletion}}$ | ~5 | mm | Gesztesi et al., 2023 |
| 网格大小 | $L$ | 10 | mm | 模型选择 / Model choice |
| 网格间距 | $\Delta x$ | 50 | $\mu$m | 模型选择 / Model choice |
| 时间步长 | $\Delta t$ | 0.01 | s | 模型选择 / Model choice |
| 纤维素酶产糖率 | $\alpha$ | {{placeholder:alpha_value}} | s$^{-1}$ | 待测定 / To be measured |
| INP-纤维素酶展示量 | $[E]_{\text{INP}}$ | {{placeholder:INP_display_level}} | 分子/细胞 | 待测定 / To be measured |
| 细菌数量 | $N$ | $10^3\text{--}10^4$ | — | 模拟参数 / Simulation parameter |

---

### 10.3 PTS 动力学参数 / PTS Kinetic Parameters

| 参数 | 符号 | 值 | 单位 | 参考文献 |
|-----------|-------|-------|-------|-----------|
| EI 总量 | $[\text{EI}]_{\text{total}}$ | {{placeholder:EI_total}} | $\mu$M | Rohwer et al., 2000 *JBC* |
| HPr 总量 | $[\text{HPr}]_{\text{total}}$ | {{placeholder:HPr_total}} | $\mu$M | Rohwer et al., 2000 |
| 总 CheA | $[\text{CheA}]_{\text{total}}$ | {{placeholder:CheA_total}} | $\mu$M | Rohwer et al., 2000 |
| 总 CheY | $[\text{CheY}]_{\text{total}}$ | {{placeholder:CheY_total}} | $\mu$M | Rohwer et al., 2000 |
| PEP 浓度 | $[\text{PEP}]$ | {{placeholder:PEP_concentration}} | mM | Rohwer et al., 2000 |
| PEP 磷酸化速率 | $k_{\text{PEP}}$ | {{placeholder:k_PEP_value}} | $\mu$M$^{-1}$ s$^{-1}$ | Rohwer et al., 2000 |

---

### 10.4 形态与膜参数 / Morphology and Membrane Parameters

| 参数 | 符号 | 值 | 单位 | 参考文献 |
|-----------|-------|-------|-------|-----------|
| 细胞半径 | $r$ | ~0.5 | $\mu$m | 典型 MG1655 尺寸 / Typical MG1655 |
| 圆柱段长度 | $L_{\text{cyl}}$ | ~2 | $\mu$m | 典型 MG1655 尺寸 / Typical MG1655 |
| 总膜表面积 | $A_{\text{total}}$ | ~9.42 | $\mu$m² | 胶囊模型计算 / Capsule model calculation |
| 基础占用面积 | $A_{\text{basal}}$ | {{placeholder:A_basal_value}} | $\mu$m² | 待估计 / To be estimated |
| 可分配面积 | $A_{\text{available}}$ | {{placeholder:A_available_value}} | $\mu$m² | $A_{\text{total}} - A_{\text{basal}}$ |
| 膜占用率 | $\phi$ | {{placeholder:phi_value}} | — | $A_{\text{engineered}} / A_{\text{available}}$ |
| 临界占用阈值 | $\phi_{\text{crit}}$ | {{placeholder:phi_crit_value}} | — | 待测定 / To be measured |
| 膜健康衰减速率 | $\alpha$ | {{placeholder:alpha_decay_value}} | — | 待测定 / To be measured |

---

## 11. 建模趣事 / A Modeling Anecdote

**中文**

在 ABM 的第一次完整运行中，建模负责人设置了一个 30 分钟模拟时长的实验。参数设好后，代码开始运行。

然后他意识到一个错误。

他没有考虑**模拟时间与实际计算时间之间的时间加速比**。

模拟时间步长 $\Delta t = 0.01\ \text{s}$，模拟时长 $T = 1800\ \text{s}$（30 分钟）。这意味着 $1800 / 0.01 = 180,000$ 个时间步。每个时间步需要遍历 $N = 10^3$ 个智能体、更新位置、计算局部浓度、重新计算翻转偏倚、采样随机方向……

30 分钟的模拟时间，最终确实用了 30 分钟的实际时间来计算。

至少，我们学到了一个教训：在启动大规模模拟之前，始终估算计算复杂度。

**English**

During the first full ABM run, the modeling manager set up an experiment with a 30-minute simulation duration. Parameters were configured, and the code started running.

Then he realized a mistake.

He had forgotten to account for the **time acceleration ratio between simulated time and real computation time**.

The simulation time step was $\Delta t = 0.01\ \text{s}$, and the simulation duration was $T = 1800\ \text{s}$ (30 minutes). That means $1800 / 0.01 = 180,000$ time steps. Each time step involved looping over $N = 10^3$ agents, updating positions, computing local concentrations, recalculating tumble bias, sampling random directions...

30 minutes of simulated time ended up taking 30 minutes of real time to compute.

At least we learned the lesson: always estimate computational complexity before launching large-scale simulations.

---

## 12. 未来方向 / Future Directions

**中文**

当前的模型框架聚焦于 PTS 介导的**正趋化**——工程菌朝向纤维二糖梯度运动。这是项目第一阶段的核心需求。然而，该框架具有天然的扩展性，以下方向将在后续迭代中探索：

**1. 负趋化模块 / Negative Chemotaxis Module**

在太空生物反应器的更复杂场景中，代谢副产物（如乙酸、乙醇等短链脂肪酸和醇类）可能在局部积累并产生毒性。如果工程菌能够同时感知并**远离**这些抑制性物质——即负趋化（negative chemotaxis）——将进一步提升系统的稳健性。

在数学上，负趋化可以作为并行信号通道加入现有框架。设 $T_i(t)$ 为毒性信号（如局部乙酸浓度），则总趋化活性可扩展为：

$$a_i^{total} = a_{PTS,i} + w_T \cdot T_i$$

其中 $w_T$ 为负趋化权重。当毒性信号为正时，CheA 活性增强，翻转概率上升，细菌趋向于离开该区域。

**2. 多底物通用性 / Multi-Substrate Generalization**

当前模型针对纤维素→纤维二糖→PTS 趋化这一具体场景。然而，PTS 系统对多种糖类（葡萄糖、甘露糖、N-乙酰葡糖胺等）均有趋化性。如果未来的工程改造将表面展示酶替换为针对其他太空废弃物（蛋白质、脂质、合成聚合物）的降解酶，只要降解产物是 PTS 糖，同样的模型框架即可适用。这种"可互换性"正是 friskoli 作为通用设计范式的核心优势。

**3. 实验-模型闭环迭代 / Closed-Loop Model-Experiment Iteration**

当 RPM 微重力模拟实验数据就绪后，模型参数将进行系统的重新拟合。特别地：
- RPM 条件下测得的降解率将用于校准传质系数 $k_m$ 和有效扩散系数 $D_{eff}$
- 启动子文库扫描得到的趋化效率数据将用于验证 $G_{opt}$ 预测
- 形态测量数据（长度、半径、体积分布）将用于约束膜面积动态方程的参数

**4. 种群异质性 / Population Heterogeneity**

当前模型假设所有细胞在给定 $G$ 下具有相同的参数。实际上，即使是同基因群体也存在个体间的表达异质性和行为差异。未来可引入参数的分布（如 $G$ 在群体中的分布）和随机切换机制，以更好地模拟真实群体行为。

**English**

The current model framework focuses on PTS-mediated **positive chemotaxis** — engineered bacteria moving toward cellobiose gradients. This addresses the core need of the project's first phase. However, the framework is naturally extensible, and the following directions will be explored in subsequent iterations:

**1. Negative Chemotaxis Module / 负趋化模块**

In more complex space bioreactor scenarios, metabolic byproducts (such as acetate, ethanol, and other short-chain fatty acids and alcohols) may accumulate locally and become toxic. If engineered bacteria could simultaneously sense and **move away from** these inhibitory substances — i.e., negative chemotaxis — system robustness would be further improved.

Mathematically, negative chemotaxis can be incorporated as a parallel signal channel into the existing framework. Let $T_i(t)$ be the toxicity signal (e.g., local acetate concentration), then the total chemotactic activity can be extended as:

$$a_i^{total} = a_{PTS,i} + w_T \cdot T_i$$

where $w_T$ is the negative chemotaxis weight. When the toxicity signal is positive, CheA activity increases, tumble probability rises, and the bacterium tends to leave the region.

**2. Multi-Substrate Generalization / 多底物通用性**

The current model targets the specific scenario of cellulose → cellobiose → PTS chemotaxis. However, the PTS system mediates chemotaxis toward multiple sugars (glucose, mannose, N-acetylglucosamine, etc.). If future engineering replaces the surface-displayed enzymes with degradative enzymes targeting other space waste types (proteins, lipids, synthetic polymers), the same model framework applies — provided the degradation products are PTS sugars. This "interchangeability" is the core advantage of friskoli as a universal design paradigm.

**3. Closed-Loop Model-Experiment Iteration / 实验-模型闭环迭代**

Once RPM simulated microgravity experimental data becomes available, model parameters will undergo systematic re-fitting. In particular:
- Degradation rates measured under RPM conditions will calibrate the mass transfer coefficient $k_m$ and effective diffusion coefficient $D_{eff}$
- Chemotaxis efficiency data from the promoter library scan will validate the $G_{opt}$ prediction
- Morphometric data (length, radius, volume distributions) will constrain the parameters of the membrane area dynamics equations

**4. Population Heterogeneity / 种群异质性**

The current model assumes all cells with a given $G$ share identical parameters. In reality, even isogenic populations exhibit cell-to-cell heterogeneity in expression and behavior. Future iterations may introduce parameter distributions (e.g., distribution of $G$ within a population) and stochastic switching mechanisms to better simulate real population behavior.

---

## 13. 参考文献 / References

1. Barkai, N. & Leibler, S. (1997). Robustness in simple biochemical networks. *Nature*, 387(6636), 913–917.
2. Berg, H. C. & Brown, D. A. (1972). Chemotaxis in *Escherichia coli* analysed by three-dimensional tracking. *Nature*, 239(5374), 500–504.
3. Berg, H. C. (2004). *E. coli in Motion*. Springer.
4. Cluzel, P., Surette, M., & Leibler, S. (2000). An ultrasensitive bacterial motor revealed by monitoring signaling proteins in single cells. *Science*, 287(5458), 1652–1655.
5. Gerchman, S. E. & Weiss, R. (2004). Bacterial chemotaxis: Diffusion-based model for gradient sensing. *Physical Review E*, 70(1), 011910.
6. Gesztesi, J. L., et al. (2023). Bacterial chemotaxis in microgravity environments. *npj Microgravity*, 9, 45.
7. Somavanshi, R., Ghosh, B., & Sourjik, V. (2016). Sugar influx sensing by the phosphotransferase system of *Escherichia coli*. *PLoS Biology*, 14(8), e2000074. DOI: 10.1371/journal.pbio.2000074.
8. Hall, B. G. & Xu, J. (1992). Nucleotide sequence, function, activation, and evolution of the cryptic *asc* operon of *Escherichia coli* K-12. *Molecular Biology and Evolution*, 9(4), 688–706.
9. Jahreis, K., et al. (2008). The *asc* operon of *Escherichia coli* K-12: A paradigm for regulation by attenuation. *BMC Microbiology*, 8, 187.
10. Lux, R., et al. (1999). Chemotactic response to multiple stimuli in *Escherichia coli*. *Journal of Bacteriology*, 181(2), 437–445.
11. Neumann, S., et al. (2012). The chemotactic adaptation time of *Escherichia coli* depends on the stimulation protocol. *Biophysical Journal*, 102(3), 555–564.
12. Rohwer, J. M., et al. (2000). Understanding glucose transport by the bacterial phosphoenolpyruvate:glycose phosphotransferase system on the basis of kinetic measurements. *Journal of Biological Chemistry*, 275(45), 34909–34921.
13. Schnell, S. & Turner, T. E. (2004). Reaction kinetics in intracellular environments: Diffusion and reaction. *Progress in Biophysics and Molecular Biology*, 85(1), 37–57.
14. Tindall, M. J., et al. (2008). Mathematical modelling of chemotaxis: A review. *Bulletin of Mathematical Biology*, 70(6), 1579–1620.
15. Wadhams, G. H. & Armitage, J. P. (2004). Making sense of it all: Bacterial chemotaxis. *Nature Reviews Molecular Cell Biology*, 5(12), 1024–1037.
16. Harris, L. K. & Theriot, J. A. (2016). Relative rates of surface and volume synthesis set bacterial cell size. *Cell*, 165(6), 1479–1492.
17. Shi, H., et al. (2021). Precise regulation of the relative rates of surface area and volume synthesis in bacterial cells growing in dynamic environments. *Nature Communications*, 12, 2209.
18. Zea, L., et al. (2017). Phenotypic changes exhibited by *E. coli* cultured in space. *Frontiers in Microbiology*, 8, 1598.

---

> **本文档为 iGEM 2026 SZU-SIAT-China 团队项目 "friskoli" 的维基草稿。**
> **内容说明：本文档描述的是理论框架和计划中的建模工作。所有方程和公式代表我们将采用的建模方法。标注为 {{placeholder:...}} 的条目将在获得实际实验结果和模拟数据后更新。本文档中不存在任何捏造的模拟结果。**
> **版本：v2.0 (草稿)**
