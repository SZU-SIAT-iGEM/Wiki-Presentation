# Engineering Success / 工程成功

> **Project:** friskoli
> **Team:** SZU-SIAT-China | **Track:** Space Track | **Year:** 2026

---

> **Page status / 页面状态:** This page documents our **DBTL cycle design and reasoning**. Experimental data fills (marked `{{placeholder:...}}`) are added as each cycle completes. Where conclusions are stated, we use conditional language ("we expect," "predicted") for cycles not yet run. Last data merge: {{date}}.
> 本页面记录我们的 **DBTL 循环设计与推理过程**。实验数据填充（标记为 `{{placeholder:...}}`）将随各循环完成而增补。在结论性陈述处，对尚未运行的循环我们使用条件性语言（"我们预期"、"预测"）。上次数据合并：{{date}}。

## Overview / 总览

Engineering in synthetic biology is not about getting it right the first time. It is about designing a hypothesis, building it into DNA, testing it against reality, and learning what reality teaches you. The Design-Build-Test-Learn (DBTL) cycle is the heartbeat of our project. This page documents that heartbeat — not just the successes, but the reasoning, the dead ends we anticipated, and the questions we are still answering.

合成生物学的工程精髓不在于一次做对。它在于设计一个假设、将其构建到 DNA 中、用现实检验它、然后学习现实教给你的东西。设计-构建-测试-学习（DBTL）循环是我们项目的心跳。本页面记录了这心跳——不仅是成功，还有我们的推理、我们预见的死胡同、以及我们仍在回答的问题。

The friskoli project is organized into two engineering modules, each with its own DBTL trajectory:

- **Module A: Chemotaxis Engineering / 趋化工程** — awakening a silent operon to make *E. coli* chase cellobiose, then tuning the signal sensitivity for the weak mass-transport environment of microgravity.
- **Module B: Surface Display / 表面展示** — anchoring cellulases directly to the bacterial outer membrane so that in a convection-free world, the enzyme is never lost to diffusion.

friskoli 项目分为两个工程模块，每个模块有自己的 DBTL 轨迹：

- **模块 A: 趋化工程** ——唤醒沉睡的操纵子，让大肠杆菌追逐纤维二糖，然后针对微重力弱传质环境调谐信号灵敏度。
- **模块 B: 表面展示** ——将纤维素酶直接锚定到细菌外膜上，在一个没有对流的世界里，酶永远不会因扩散而丢失。

These modules are designed to converge in later integration cycles. But before integration, each must stand on its own evidence. That is what this page is for.

这些模块设计在后续的整合循环中汇合。但在整合之前，每一个都必须建立在自己独立的证据之上。这就是本页面的目的。

---

## Module A: Chemotaxis Engineering / 趋化工程

How do you make a bacterium swim toward food it cannot naturally sense? This is the central question of Module A. The answer lives in the phosphotransferase system (PTS) — the ancient sugar-transport machinery that doubles, in *E. coli*, as a chemotaxis signal integrator. Our strategy: reactivate a dormant genetic program, then amplify the signal it generates.

如何让细菌游向它天然无法感知的食物？这是模块 A 的核心问题。答案在于磷酸转移酶系统 (PTS)——这套古老的糖转运机制在大肠杆菌中同时兼任趋化信号的整合器。我们的策略：重新激活一个休眠的遗传程序，然后放大它产生的信号。

---

### Cycle 1: Awakening the Silent Operon / 唤醒沉睡的操纵子

Every *E. coli* cell carries a silent operon called *asc*. The *ascF* gene encodes a PTS transporter (EII^Asc); the *ascB* gene encodes a phospho-β-glucosidase. Together, they import and cleave β-glucosides — including cellobiose, the glucose-glucose dimer released by cellulose degradation. But in laboratory strains, a repressor called AscG keeps this operon locked down. The genes are there. They are just asleep.

每一个大肠杆菌细胞都携带一个名为 *asc* 的沉默操纵子。*ascF* 基因编码一个 PTS 转运蛋白 (EII^Asc)；*ascB* 基因编码一个磷酸-β-葡萄糖苷酶。它们共同输入并裂解 β-葡萄糖苷——包括纤维二糖，即纤维素降解释放的葡萄糖-葡萄糖二聚体。但在实验室菌株中，一个名为 AscG 的阻遏蛋白将这个操纵子牢牢锁住。基因就在那里。它们只是沉睡着。

What nature does slowly — spontaneous reactivation when *E. coli* enters cellulose-rich soil — we can do deliberately. Replace the native promoter with a constitutive one, and the sleeping operon wakes up.

大自然缓慢完成的事情——大肠杆菌进入富含纤维素的土壤时发生自发重新激活——我们可以主动完成。用组成型启动子替换天然启动子，沉睡的操纵子就苏醒了。

#### DESIGN / 设计

**The PTS-Chemotaxis Link.** To understand why awakening *asc* is more than a metabolic engineering trick, we need to look at how the PTS phosphotransfer cascade connects to the chemotaxis machinery.

**PTS-趋化连接。** 要理解为什么唤醒 *asc* 不仅是代谢工程的技巧，我们需要看清楚 PTS 磷酸转移级联如何连接到趋化机制。

The cascade flows like this:

$$PEP \rightarrow EI \rightarrow HPr \rightarrow EII\ complex\ (AscF) \rightarrow sugar$$

When PTS sugar transport is active, phosphoryl groups rapidly transfer from phosphorylated EI (EI~P) to HPr, converting EI to its unphosphorylated form (EI). Re-phosphorylation of EI requires the protein to first form a dimer — and dimerization is the slowest step in the entire cascade. So during active transport, non-phosphorylated EI accumulates rapidly.

当 PTS 糖转运活跃时，磷酸基团从磷酸化 EI (EI~P) 快速转移至 HPr，将 EI 转化为其非磷酸化形式 (EI)。EI 的重新磷酸化需要蛋白质首先形成二聚体——而二聚化是整个级联中最慢的步骤。因此，在活跃转运期间，非磷酸化 EI 迅速积累。

Here is the critical connection: high levels of non-phosphorylated EI directly bind and inhibit the CheA kinase. Less CheA activity means less CheY-P. Less CheY-P means the flagellar motors favor counterclockwise rotation — "smooth swimming." The bacterium swims longer in the direction of higher sugar concentration. This is chemotaxis, hardwired into the PTS.

关键连接在此：高水平的非磷酸化 EI 直接结合并抑制 CheA 激酶。较少的 CheA 活性意味着较少的 CheY-P。较少的 CheY-P 意味着鞭毛马达倾向于逆时针旋转——"平滑游动"。细菌在糖浓度较高的方向上游泳更长的时间。这就是内置于 PTS 的趋化性。

In other words: by giving *E. coli* a new PTS substrate (cellobiose), we are not just feeding it. We are giving it a new chemical to chase.

换句话说：通过给大肠杆菌一个新的 PTS 底物（纤维二糖），我们不仅在喂养它。我们在给它一个新的化学物质去追逐。

**Expression Cassette.** The construct is deliberately conservative for first-pass testing:

```
J23116 — B0034 — ascF — B0034 — ascB — B0015
```

- **J23116:** Anderson constitutive promoter, relative strength ~0.16. Weak enough to avoid membrane protein toxicity during initial characterization, strong enough to produce detectable phenotype.
- **B0034:** Medium-strength ribosome binding site, placed before each gene in the bicistronic operon.
- **ascF / ascB:** Coding sequences amplified from *E. coli* MG1655 genomic DNA. No codon optimization — these are endogenous genes.
- **B0015:** Double terminator for efficient transcription termination.
- **Vector backbone:** pBR322 origin (medium-low copy, ~15-20 copies/cell). A conservative choice: we want to see the phenotype before we push expression higher.

- **J23116:** Anderson 组成型启动子，相对强度约 0.16。足够弱以避免初始表征期间的膜蛋白毒性，足够强以产生可检测的表型。
- **B0034:** 中等强度核糖体结合位点，置于双顺反子操纵子中每个基因之前。
- **ascF / ascB:** 从大肠杆菌 MG1655 基因组 DNA 扩增的编码序列。未进行密码子优化——这些是内源基因。
- **B0015:** 双终止子，确保高效转录终止。
- **载体骨架:** pBR322 复制起点（中低拷贝，约 15-20 拷贝/细胞）。保守的选择：我们希望在提高表达水平之前先看到表型。

A critical reference guides our thinking: Vinuselvi & Lee (2011, DOI: 10.1007/s00253-011-3434-9) demonstrated engineering *E. coli* for cellobiose utilization using ONLY endogenous cryptic genes — no heterologous sequences needed. Through promoter replacement followed by adaptive evolution, they achieved glucose-comparable growth efficiency. This paper is our proof of principle: the chassis already has the hardware. We just need to turn it on.

一篇关键参考文献指导着我们的思考：Vinuselvi 与 Lee (2011, DOI: 10.1007/s00253-011-3434-9) 证明了仅使用内源性隐性基因（无需异源序列）工程化大肠杆菌实现纤维二糖利用。通过启动子替换和适应性进化，他们达到了与葡萄糖相当的生长效率。这篇论文是我们的原理验证：底盘已经拥有硬件。我们只需要打开开关。

**IMPORTANT NOTE from the literature:** Strains required 1-2 months of adaptive evolution AFTER engineering before achieving glucose-comparable cellobiose metabolism. We expect our initial transformants to show weak cellobiose growth. This is not a failure — it is exactly what the literature predicts. We are at the starting line of a marathon, not a sprint.

**来自文献的重要说明：** 菌株在工程化之后需要 1-2 个月适应性进化才能达到与葡萄糖相当的纤维二糖代谢。我们预期初始转化子的纤维二糖生长较弱。这不是失败——这正是文献预测的结果。我们站在马拉松的起跑线上，而非短跑的终点。

#### BUILD / 构建

Template: *E. coli* MG1655 genomic DNA, extracted using commercial purification kit. Nested PCR amplifies the *ascF* and *ascB* coding sequences. Gibson Assembly joins the fragments into the linearized pBR322-origin vector carrying the J23116 promoter and B0015 terminator. Transformation into DH5α for cloning and plasmid maintenance, followed by sequence verification and final transformation into MG1655 host for functional testing.

模板：大肠杆菌 MG1655 基因组 DNA，使用商业纯化试剂盒提取。巢式 PCR 扩增 *ascF* 和 *ascB* 编码序列。Gibson 组装将片段连接到携带 J23116 启动子和 B0015 终止子的线性化 pBR322-ori 载体中。转化至 DH5α 进行克隆和质粒维护，随后进行序列验证，最终转化至 MG1655 宿主进行功能测试。

Colony PCR screening results: {{placeholder:colony_pcr_results}}

Sanger sequencing confirmation: {{placeholder:sequencing_confirmation}}

#### TEST / 测试

**Test 1: Gene insertion verification.** Colony PCR using primers flanking the assembly junctions confirms the presence and correct orientation of the *ascF-ascB* cassette.

**测试一：基因插入验证。** 使用侧翼引物的菌落 PCR 确认 *ascF-ascB* 表达盒的存在和正确方向。

**Test 2: β-glucosidase activity.** Crude enzyme extract from induced cultures is assayed using the PNPG (p-nitrophenyl-β-D-glucopyranoside) chromogenic method. Activity is quantified by absorbance at 410 nm. This confirms that AscB is expressed and functional.

**测试二：β-葡萄糖苷酶活性。** 来自诱导培养物的粗酶提取液使用 PNPG（对硝基苯基-β-D-吡喃葡萄糖苷）显色法测定。活性通过 410 nm 吸光度定量。这确认了 AscB 的表达和功能。

**Test 3: AscF membrane protein expression.** Membrane protein fractions are extracted and analyzed by SDS-PAGE. The expected band for AscF is approximately 52–53 kDa; however, membrane proteins can migrate anomalously on SDS-PAGE, so the apparent band may deviate from the predicted molecular weight (Rath et al., 2009). Western blot confirmation: {{placeholder:western_blot_data}}

**测试三：AscF 膜蛋白表达。** 提取膜蛋白组分并通过 SDS-PAGE 分析。AscF 的预期条带约 52–53 kDa；但膜蛋白在 SDS-PAGE 中可能出现异常迁移，因此表观条带位置可能偏离预测分子量（Rath et al., 2009）。Western blot 确认：{{placeholder:western_blot_data}}

**Test 4: Cellobiose metabolism growth assay.** Cultures are grown in M9 minimal medium with 0.4% (w/v) cellobiose as the sole carbon source. Growth is monitored by OD₆₀₀ over 48-72 hours. The following controls are run in parallel:

| Condition / 条件 | Purpose / 目的 |
|:---|:---|
| Engineered strain in M9 + 0.4% cellobiose | Test: can the awakened operon support growth? |
| Engineered strain in M9 + 0.4% glucose | Positive control: is the strain healthy? |
| Empty vector in M9 + 0.4% cellobiose | Negative control: is there background cellobiose utilization? |
| Sterile M9 + 0.4% cellobiose | Blank: is there abiotic degradation of cellobiose? |

**测试四：纤维二糖代谢生长测定。** 培养物在以 0.4% (w/v) 纤维二糖为唯一碳源的 M9 基本培养基中生长。通过 OD₆₀₀ 监测 48-72 小时的生长。以下对照平行进行：

| 条件 | 目的 |
|:---|:---|
| 工程菌株在 M9 + 0.4% 纤维二糖中 | 测试：唤醒的操纵子能否支持生长？ |
| 工程菌株在 M9 + 0.4% 葡萄糖中 | 阳性对照：菌株是否健康？ |
| 空载体在 M9 + 0.4% 纤维二糖中 | 阴性对照：是否存在背景纤维二糖利用？ |
| 无菌 M9 + 0.4% 纤维二糖 | 空白：纤维二糖是否存在非生物降解？ |

{{placeholder:growth_curve_data}}

We expect the initial transformants to show detectable but weak growth on cellobiose relative to glucose — consistent with the Vinuselvi & Lee findings that adaptive evolution is required for full metabolic efficiency.

我们预期初始转化子在纤维二糖上相对于葡萄糖显示出可检测但较弱的生长——与 Vinuselvi 与 Lee的发现一致，即完全代谢效率需要适应性进化。

#### LEARN / 学习

{{placeholder:cycle1_conclusion}}

What we need to answer from Cycle 1: Does the awakened *asc* operon produce functional AscF and AscB? Can the engineered strain detectably grow on cellobiose as sole carbon source? What is the baseline expression level and does it cause any visible toxicity? These answers form the foundation for Cycle 2.

我们需要从循环一回答的问题：唤醒的 *asc* 操纵子是否产生有功能的 AscF 和 AscB？工程菌株能否在纤维二糖作为唯一碳源上检测到生长？基线表达水平是多少，是否造成任何可见的毒性？这些答案为循环二奠定基础。

---

### Cycle 2: Tuning the Signal Antenna / 调谐信号天线

Cycle 1 asked: *can* we awaken the operon? Cycle 2 asks a more subtle question: given the peculiar physics of microgravity, how sensitive can we make the signal?

循环一问的是：我们*能不能*唤醒这个操纵子？循环二问的是更微妙的问题：考虑到微重力特有的物理学，我们能把信号调到多灵敏？

In microgravity, there is no convection. No buoyancy-driven mixing. The only way molecules move is by diffusion — slow, random, undirected. A sugar molecule released from a cellulose fiber does not rise or fall. It just sits there, spreading outward in a sluggish Brownian dance. For a bacterium trying to find food, this is a nightmare: the gradient is shallow, the signal is weak, and every micron of progress must be earned.

在微重力中，没有对流。没有浮力驱动的混合。分子移动的唯一方式是扩散——缓慢、随机、无定向。从纤维素纤维释放的糖分子不会上升或下降。它只是停在那里，以迟缓的布朗运动向外扩散。对于试图寻找食物的细菌来说，这是一场噩梦：梯度很浅，信号很弱，每微米的进展都必须付出代价。

Our answer: give the bacterium more antennas.

我们的答案：给细菌更多天线。

#### DESIGN (THEORY) / 设计（理论）

This is the most mathematically detailed section of our engineering documentation. We want to be transparent about how we think — because the thinking itself is what we are testing.

这是我们工程文档中数学最详细的章节。我们想透明地展示我们的思考方式——因为思考本身正是我们在检验的东西。

**Step 1: The Antenna Metaphor / 天线隐喻**

AscF transporters are signal antennas. Each AscF protein sitting in the inner membrane is a portal through which cellobiose enters, and each entry event sends a pulse through the PTS cascade that ultimately whispers "more food this way" to the flagellar motors.

AscF 转运蛋白就是信号天线。每一个坐落在内膜中的 AscF 蛋白都是纤维二糖进入的门户，每一次进入事件都通过 PTS 级联发送一个脉冲，最终向鞭毛马达低语"这个方向有更多食物"。

In a rich environment where the bacterium is practically swimming through a sugar soup (c >> K_S), one more or one fewer transporter barely matters — the signal is already saturating. The transfer flux is:

$$J(S,G) = N_0 G \cdot \frac{k_{\text{cat}} \cdot c}{K_S + c}$$

When food is abundant (c >> K_S): J ≈ N_0 G · k_cat — all transporters are running at full speed. Linear scaling, but you are already at maximum.

But when food is SCARCE (c << K_S, the microgravity norm):

$$J \approx \frac{N_0 G \cdot k_{\text{cat}}}{K_S} \cdot c$$

In this regime, every additional transporter directly increases the flux. Every antenna you add captures more of the faint signal. This is the regime that matters for us. In microgravity, near a slowly degrading cellulose particle, the local cellobiose concentration will be tiny. Every AscF molecule is precious.

在食物稀缺时（c << K_S，微重力常态）：每一个额外的转运蛋白都直接增加通量。每增加一根天线都能捕获更多微弱的信号。这才是对我们重要的区域。在微重力中，靠近缓慢降解的纤维素颗粒，局部纤维二糖浓度将是极微小的。每一个 AscF 分子都是珍贵的。

**Step 2: Gain Factor G / 增益因子 G**

Define a dimensionless gain factor relative to an engineered reference expression level. Since the *asc* operon is silent in wild-type MG1655 (zero AscF), $G$ does NOT represent fold-change versus wild-type — instead, we define:

$$N_{\text{AscF}} = N_0 G$$

where $N_0$ is the AscF protein count under a reference promoter (our Cycle 1 J23116, ~0.16 relative strength). $G=1$ is our Cycle 1 baseline. $G=2$ means double the transporters. $G=5$ means five times.

定义无量纲增益因子，相对于工程参考表达水平。由于 *asc* 操纵子在野生型 MG1655 中沉默（AscF 为零），$G$ **不表示**相对于野生型的倍数——否则"零乘以任何倍数仍为零"。我们定义：

$$N_{\text{AscF}} = N_0 G$$

其中 $N_0$ 是参考启动子（循环一 J23116，~0.16 相对强度）下的 AscF 蛋白数量。$G=1$ 是我们的循环一基线。$G=2$ 意味着两倍的转运蛋白。$G=5$ 意味着五倍。

**Step 3: Full Model Integration / 完整模型整合**

We incorporate AscF overexpression into the PTS signaling framework. The key dimensionless ratio that determines chemotactic output emerges from the steady-state balance between transport-driven dephosphorylation and PEP-driven rephosphorylation:

$$\frac{J(S,G)}{k_r E_T} = \frac{N_0 G \cdot k_{\text{cat}} \cdot c}{k_r E_T \cdot (K_S + c)}$$

Numerator = total transport flux $J(S,G)$. This is the signal strength: how fast cellobiose is flowing into the cell. Denominator = the system's EI re-phosphorylation capacity ($k_r E_T$): how fast the PTS cascade can reset itself. Crucially, the total EI pool $E_T$ is fixed by endogenous *ptsI* expression and WON'T increase just because we overexpress AscF. So when transport flux overwhelms the re-phosphorylation machinery, the dephosphorylated EI fraction $e$ rises, CheA is inhibited, and chemotaxis is amplified.

将 AscF 过表达纳入 PTS 信号转导框架。决定趋化输出的关键无量纲比值来自转运驱动的去磷酸化与 PEP 驱动的再磷酸化之间的稳态平衡：

$$\frac{J(S,G)}{k_r E_T} = \frac{N_0 G \cdot k_{\text{cat}} \cdot c}{k_r E_T \cdot (K_S + c)}$$

分子 = 总转运通量 $J(S,G)$。这是信号强度：纤维二糖流入细胞的速度。分母 = 系统的 EI 再磷酸化能力 ($k_r E_T$)：PTS 级联重置自身的速度。关键的是，总 EI 池 $E_T$ 由内源性 *ptsI* 表达固定，不会因为我们过表达 AscF 而增加。因此当转运通量超过再磷酸化机制的容量时，去磷酸化 EI 分数 $e$ 上升，CheA 被抑制，趋化性被放大。

When this ratio is large → $e$ (dephosphorylated EI fraction) is high → CheA strongly inhibited → CheY-P low → flagella spin CCW longer → chemotaxis amplified. When it is small → EI stays mostly phosphorylated ($e$ low) → CheA active → CheY-P high → tumbles dominate → no directed movement.

当此比值大时 → $e$（去磷酸化 EI 分数）高 → CheA 被强烈抑制 → CheY-P 低 → 鞭毛更长时间逆时针旋转 → 趋化性放大。当此比值小时 → EI 多保持磷酸化（$e$ 低）→ CheA 活跃 → CheY-P 高 → 翻滚占主导 → 无定向运动。

**Step 4: Effective Dissociation Constant / 有效解离常数**

Rearrange the steady-state expression to isolate the concentration-dependent term. The result is an effective dissociation constant that characterizes the sensitivity threshold of the chemotactic response:

$$K_D^{\text{eff}} = \frac{k_r E_T \cdot K_I \cdot K_S}{N_0 G \cdot k_{\text{cat}}}$$

K_D^eff is the cellobiose concentration at which transport flux equals the EI re-phosphorylation capacity, marking the transition between the signal-limited regime ($c \ll K_D^{\text{eff}}$, steep response) and the saturation regime ($c \gg K_D^{\text{eff}}$, diminished sensitivity). A SMALLER K_D^eff means the bacterium can detect weaker gradients. And critically, G — the gain factor — is in the DENOMINATOR:

$$G \uparrow \quad \rightarrow \quad N_0 G \uparrow \quad \rightarrow \quad K_D^{\text{eff}} \downarrow$$

Higher G = lower detection threshold = better "smell." This is the mathematical justification for our entire promoter-tuning strategy. We are not just expressing more protein for the sake of it. We are moving the chemotactic detection threshold downward — exactly what microgravity demands.

将稳态表达式重排以分离与浓度依赖的项。结果是一个有效解离常数，表征趋化响应的灵敏度阈值：

$$K_D^{\text{eff}} = \frac{k_r E_T \cdot K_I \cdot K_S}{N_0 G \cdot k_{\text{cat}}}$$

K_D^eff 是转运通量等于 EI 再磷酸化能力时的纤维二糖浓度，标志着信号受限区（$c \ll K_D^{\text{eff}}$，响应陡峭）与饱和区（$c \gg K_D^{\text{eff}}$，灵敏度下降）之间的过渡。更小的 K_D^eff 意味着细菌能检测到更弱的梯度。关键是，G——增益因子——在分母中：

$$G \uparrow \quad \rightarrow \quad N_0 G \uparrow \quad \rightarrow \quad K_D^{\text{eff}} \downarrow$$

更高的 G = 更低的检测阈值 = 更好的"嗅觉"。这是我们整个启动子调谐策略的数学理由。我们不仅是为了表达更多蛋白而表达更多蛋白。我们是在降低趋化检测阈值——这正是微重力所要求的。

**The minimal usable model / 最小可用模型**

The full mathematical framework is documented on our [Model](10-Model.md) page. For the engineering discussion here, the following minimal ODE skeleton captures the core PTS–CheA–CheY signaling logic:

完整数学框架见 [Model](10-Model.md) 页面。此处给出最小 ODE 骨架，捕捉 PTS–CheA–CheY 信号的核心逻辑：

$$
\begin{aligned}
J(S,G) &= \frac{N_0 G\,k_{\text{cat}}\,S}{K_S + S} \\[3pt]
e &= \frac{[\text{EI}]}{E_T} \\[3pt]
\frac{de}{dt} &= k_d\,J(S,G)\,(1-e) - k_r\,e \\[3pt]
[\text{CheA-P}] &= A_T\,\frac{K_I}{K_I + E_T e} \\[3pt]
\frac{dY_P}{dt} &= k_Y\,[\text{CheA-P}]\,(Y_T - Y_P) - k_Z\,Y_P \\[3pt]
b(Y_P) &= \frac{Y_P^h}{K_Y^h + Y_P^h} \\[3pt]
\lambda_{\text{tumble}}(Y_P) &= \lambda_{\min} + (\lambda_{\max} - \lambda_{\min})\,b(Y_P) \\[3pt]
P_{\text{tumble}}(\Delta t) &= 1 - \exp[-\lambda_{\text{tumble}}\,\Delta t]
\end{aligned}
$$

This skeleton encodes the key design logic: increasing $G$ increases $J(S,G)$, which drives $e$ higher (more dephosphorylated EI), which lowers $[\text{CheA-P}]$, which lowers $Y_P$, which lowers $b(Y_P)$, which reduces the tumble rate, which produces longer runs toward the cellobiose source. The bell-shaped $G$–$\text{CI}$ curve emerges naturally when the three constraints below are imposed.

该骨架编码了核心设计逻辑：增大 $G$ → 增大 $J(S,G)$ → 推高 $e$（更多去磷酸化 EI）→ 降低 $[\text{CheA-P}]$ → 降低 $Y_P$ → 降低 $b(Y_P)$ → 降低翻转率 → 产生朝向纤维二糖源的更长游动。施以下述三个约束后，钟形 $G$–$\text{CI}$ 曲线自然涌现。

**Constraints / 约束条件**

This is not a "more is better" story. Three hard constraints bound the optimization:

1. **PEP pool is limited.** PEP is a glycolytic intermediate. Its concentration is set by central metabolism and will not increase when we overexpress EII. If total transport demand exceeds PEP supply, transporters sit idle — wasted protein synthesis, wasted membrane space.

2. **Total EI protein is fixed.** When transport flux $J(S,G)$ significantly exceeds the re-phosphorylation capacity ($k_r E_T$), the signal SATURATES — $e \to 1$, and further increases in $G$ produce no additional change in CheA inhibition. The chemotactic output becomes "all-or-none" — the bacterium cannot distinguish between a weak gradient and a strong one. Discrimination is lost.

3. **Membrane protein overexpression toxicity.** Overloading the inner membrane with foreign or overexpressed proteins triggers the σ^E envelope stress response. The cell diverts resources to protein folding and degradation, growth slows, and at high enough expression, viability drops.

1. **PEP pool limited / PEP 池有限。** PEP 是糖酵解中间产物。其浓度由中心代谢设定，当我们过表达 EII 时不会增加。如果总转运需求超过 PEP 供应，转运蛋白就闲置——白白浪费蛋白合成和膜空间。

2. **总 EI 蛋白固定。** 当转运通量 $J(S,G)$ 显著超过再磷酸化能力 ($k_r E_T$) 时，信号饱和——$e \to 1$，进一步增大 $G$ 不会产生额外的 CheA 抑制。趋化输出变成"全或无"——细菌无法区分弱梯度和强梯度。分辨能力丧失。

3. **膜蛋白过表达毒性。** 用外源或过表达蛋白过载内膜会触发 σ^E 包膜应激反应。细胞将资源转移到蛋白质折叠和降解上，生长减缓，在足够高的表达水平下，活力下降。

Therefore G has an OPTIMAL WINDOW. Too low = insufficient signal for chemotaxis. Too high = signal saturation plus metabolic burden. The engineering challenge is to find it.

因此 G 存在一个最优窗口。太低 = 趋化信号不足。太高 = 信号饱和加代谢负荷。工程挑战在于找到它。

**The Bell-Shaped Hypothesis / 钟形曲线假说**

We predict that chemotactic performance (measured by capillary assay accumulation or swarm plate expansion rate) will follow a bell-shaped curve as a function of AscF expression level. The ascending limb represents the "antenna gain" regime where more transporters genuinely improve signal detection. The peak represents the optimal balance. The descending limb represents the saturation-and-toxicity regime where costs outweigh benefits.

我们预测趋化性能（通过毛细管测定积累量或游动平板扩展速率测量）将作为 AscF 表达水平的函数遵循钟形曲线。上升段代表"天线增益"区域，更多转运蛋白真正改善了信号检测。峰代表最优平衡。下降段代表饱和与毒性区域，其中代价超过收益。

#### BUILD / 构建

**Strategy:** Replace the J23116 promoter with a library of Anderson constitutive promoters to create an AscF expression gradient for G-window scanning.

**策略：** 用 Anderson 组成型启动子文库替换 J23116 启动子，创建 AscF 表达梯度用于 G 窗口扫描。

| Promoter / 启动子 | Relative Strength / 相对强度 | Expected Effect / 预期效果 |
|:---|:---:|:---|
| J23118 | ~0.06 | Very weak, near-baseline / 极弱，接近基线 |
| J23116 | ~0.16 | Cycle 1 baseline / 循环一基线 |
| J23113 | ~0.33 | Low-medium / 中低 |
| J23109 | ~0.56 | Medium / 中等 |
| J23105 | ~0.74 | Medium-high / 中高 |
| J23102 | ~0.86 | Strong / 强 |
| J23100 | ~1.00 | Strongest / 最强 |

Expression cassette architecture (conserved across all variants):

表达盒架构（所有变体保持一致）：

```
P_Anderson — B0034 — ascF — B0034 — ascB — B0015
```

Each variant is constructed by Gibson Assembly with the same pBR322-origin backbone used in Cycle 1. All constructs are Sanger-verified before transformation into MG1655. Each construct is maintained as a separate strain for parallel characterization.

每个变体通过 Gibson 组装构建，使用与循环一相同的 pBR322-ori 骨架。所有构建体在转化至 MG1655 之前经过 Sanger 验证。每个构建体作为独立菌株维护，用于平行表征。

#### TEST / 测试

**Test 1: AscF relative expression quantification.** RT-qPCR for *ascF* mRNA across all seven promoter variants, normalized to a housekeeping gene (e.g., *gapA* or *rrsA*). Expected: monotonic increase in transcript level with increasing promoter strength. {{placeholder:rt_qpcr_data}}

**测试一：AscF 相对表达定量。** 对所有七个启动子变体进行 *ascF* mRNA 的 RT-qPCR，归一化至持家基因。预期：转录水平随启动子强度单调增加。{{placeholder:rt_qpcr_data}}

**Test 2: Cellobiose transport rate assay.** Uptake kinetics using a fluorescent cellobiose analog (if available) or radiolabeled cellobiose. Measures actual transport capacity, which may not perfectly correlate with mRNA due to membrane insertion bottlenecks. {{placeholder:transport_assay_data}}

**测试二：纤维二糖转运速率测定。** 使用荧光纤维二糖类似物或放射性标记纤维二糖的摄取动力学。测量实际转运能力，由于膜插入瓶颈，这可能与 mRNA 不完全相关。{{placeholder:transport_assay_data}}

**Test 3: Chemotaxis sensitivity — capillary assay.** Modified Adler capillary assay with cellobiose as chemoattractant. A capillary containing cellobiose solution (concentration gradient: 0.1 μM to 10 mM) is presented to a suspension of each strain. Accumulation is quantified after 60 minutes by dilution plating. Buffer-only capillaries serve as negative controls.

**测试三：趋化灵敏度——毛细管测定。** 改良 Adler 毛细管测定，以纤维二糖为化学引诱剂。含有纤维二糖溶液的毛细管呈现给每个菌株的悬浮液。60 分钟后通过稀释涂板定量积累。仅含缓冲液的毛细管作为阴性对照。

We expect a BELL-SHAPED response curve: very weak promoters (J23118) give near-background chemotaxis (too few antennas); medium-strong promoters (J23109-J23105) give the strongest chemotactic accumulation (optimal G window); the strongest promoters (J23100) may show diminished chemotaxis due to signal saturation and metabolic burden.

我们预期钟形响应曲线：极弱启动子 (J23118) 给出接近背景的趋化性（天线太少）；中强启动子 (J23109-J23105) 给出最强的趋化积累（最优 G 窗口）；最强启动子 (J23100) 可能因信号饱和和代谢负荷而显示趋化性减弱。

**Test 4: Chemotaxis sensitivity — swarm plate assay.** Soft agar plates (0.25-0.3% agar) with M9 minimal medium supplemented with 0.4% cellobiose. Inoculated at the center, swarm ring diameter measured every 4-6 hours over 48 hours. Expected: swarm expansion rate should follow the same bell-shaped pattern as the capillary assay. {{placeholder:swarm_plate_data}}

**测试四：趋化灵敏度——游动平板测定。** 软琼脂平板，含补充 0.4% 纤维二糖的 M9 基本培养基。中心接种，48 小时内每 4-6 小时测量游动环直径。预期：游动扩展速率应遵循与毛细管测定相同的钟形模式。{{placeholder:swarm_plate_data}}

**Test 5: Growth trade-off assessment.** Each strain is grown in two parallel conditions:

| Medium / 培养基 | What it measures / 测量内容 |
|:---|:---|
| M9 + 0.4% cellobiose | Functional performance: can the strain use cellobiose? |
| M9 + 0.4% glucose | Metabolic cost: glucose bypasses the PTS, revealing pure toxicity of AscF overexpression |

**测试五：生长权衡评估。** 每个菌株在两种平行条件下生长：

| 培养基 | 测量内容 |
|:---|:---|
| M9 + 0.4% 纤维二糖 | 功能性能：菌株能否利用纤维二糖？ |
| M9 + 0.4% 葡萄糖 | 代谢成本：葡萄糖绕过 PTS，揭示 AscF 过表达的纯毒性 |

In cellobiose medium, medium-strength promoters should produce the best growth (transport benefit exceeds metabolic cost). In glucose medium, high-expression strains may show growth defects (membrane toxicity without the compensating benefit of cellobiose transport). {{placeholder:growth_tradeoff_data}}

在纤维二糖培养基中，中等强度启动子应产生最佳生长（转运收益超过代谢成本）。在葡萄糖培养基中，高表达菌株可能显示生长缺陷（膜毒性，却没有纤维二糖转运的补偿收益）。{{placeholder:growth_tradeoff_data}}

#### LEARN / 学习

Expected optimal promoter window: J23109 to J23105 (relative strength ~0.56-0.74). But biology rarely follows predictions exactly, and that is the point of doing the experiment.

预期最优启动子窗口：J23109 至 J23105（相对强度约 0.56-0.74）。但生物学很少精确遵循预测，这正是做实验的意义所在。

Questions Cycle 2 must answer:

1. Is there a clear G threshold where the gain benefit is offset by metabolic cost? Does this threshold match our mathematical model?
2. The flagellar motor's switching response to CheY-P is highly cooperative (Hill coefficient $h \approx 10.3$; Cluzel et al. 2000 *Science*), which acts as a downstream amplifier of *any* upstream chemotactic signal — MCP-based or PTS-based. How does this motor-level cooperativity interact with the PTS pathway's linear upstream signaling — does it sharpen the G-optimum window or broaden it?
3. Will strains near the optimal G window further improve through adaptive evolution, as the Vinuselvi & Lee literature shows for metabolic adaptation? This is not just a curiosity — for long-duration space missions, strains that self-optimize over time are far more practical than strains that require constant selection pressure.
4. Does the bell-shaped curve we predict actually emerge, or is the relationship monotonic (suggesting our saturation model overestimates PEP/EI constraints)?

循环二必须回答的问题：

1. 是否存在一个清晰的 G 阈值，超过它增益收益被代谢成本抵消？这个阈值是否与我们数学模型匹配？
2. 鞭毛马达对 CheY-P 的开关响应具有高度协同性（Hill 系数 $h \approx 10.3$；Cluzel 等 2000 *Science*），这作为下游放大器作用于*任何*上游趋化信号——无论 MCP 还是 PTS。这种马达层级的协同性如何与 PTS 通路上游的线性信号相互作用——它会锐化还是拓宽 G 最优窗口？
3. 接近最优 G 窗口的菌株是否会通过适应性进化进一步改善，如 Vinuselvi 与 Lee的文献对代谢适应所展示的那样？这不仅是一个好奇心——对于长期太空任务，随时间自我优化的菌株远比需要持续选择压力的菌株更实用。
4. 我们预测的钟形曲线是否真的出现？还是关系是单调的（表明我们的饱和模型高估了 PEP/EI 约束）？

{{placeholder:cycle2_experimental_results}}

These are the questions that distinguish engineering from trial-and-error. We are not just trying seven promoters to see which one works best. We are testing a specific mathematical model of how PTS transporter abundance controls chemotactic sensitivity. If the model holds, we have a design rule that generalizes beyond this specific project. If it fails, we have learned something about the PTS-CheA interface that the literature has not captured.

这些是将工程与试错区分开来的问题。我们不只是测试七个启动子看哪个最好。我们是在检验一个特定的数学模型，关于 PTS 转运蛋白丰度如何控制趋化灵敏度。如果模型成立，我们就有了一个超越这个特定项目的通用设计规则。如果模型失败，我们就学到了文献尚未捕捉到的关于 PTS-CheA 接口的某些东西。

---

## Module B: Surface Display / 表面展示

Enzymes are soluble proteins. You express them, they diffuse into the medium, they find their substrate. This works fine in a shaken flask on Earth, where convection mixes everything. In microgravity, it is a fundamentally broken strategy.

酶是可溶性蛋白。你表达它们，它们扩散到培养基中，它们找到自己的底物。这在地球上的摇瓶中效果很好，对流混合了一切。在微重力中，这是一个从根本上有缺陷的策略。

Without convection, a secreted cellulase molecule drifts away from the bacterium that produced it. The cellobiose it releases diffuses outward in all directions — most of it never reaches the bacterium. It is a leaky pipeline: you invest energy in making enzyme, the enzyme makes sugar, and the sugar feeds someone else.

没有对流，分泌的纤维素酶分子会漂离产生它的细菌。它释放的纤维二糖向所有方向扩散——大部分永远不会到达细菌。这是一个漏水管道：你投入能量制造酶，酶制造糖，糖喂养了别人。

The solution was proposed decades ago in the cellulosome — nature's own answer to this problem. *Clostridium thermocellum* builds massive extracellular protein complexes that keep cellulases physically clustered. Our solution is simpler but follows the same logic: anchor the enzyme directly to the cell surface. Where the bacterium goes, the enzyme goes. No diffusion loss. No free riders.

解决方案几十年前就在纤维小体中提出——大自然对这个问题的回答。热纤梭菌构建了巨大的胞外蛋白复合物，使纤维素酶保持物理聚集。我们的解决方案更简单但遵循相同的逻辑：将酶直接锚定到细胞表面。细菌去哪儿，酶就去哪儿。没有扩散损失。没有搭便车者。

### DESIGN / 设计

**Cellulase Selection / 纤维素酶选择**

We selected three cellulases from *Clostridium thermocellum*, the model organism for efficient cellulose degradation:

我们从热纤梭菌中选择了三种纤维素酶——高效纤维素降解的模式生物：

| Enzyme / 酶 | Family / 家族 | Type / 类型 | Primary Product / 主要产物 | Reference / 参考文献 |
|:---|:---|:---|:---|:---|
| Cel48S | GH48 | Reducing-end exocellulase (CBH) / 还原端外切纤维素酶 | Cellobiose / 纤维二糖 | Leis et al., 2017 |
| Cel9K | GH9 | Processive cellulase (cellobiose-releasing) / 持续性纤维素酶（释放纤维二糖） | Cellobiose / 纤维二糖 | Leis et al., 2017 |
| Cel5L | GH5 | Processive endoglucanase / 持续性内切葡聚糖酶 | Cellobiose / 纤维二糖 | Leis et al., 2017 |

Why three enzymes? Crystalline cellulose is not a single chemical bond — it is a supramolecular structure of crystalline and amorphous regions. **Cel5L** (processive endoglucanase) cleaves internal β-1,4 linkages in amorphous regions, creating new chain ends. **Cel48S** (reducing-end exocellulase, CBH) processively releases cellobiose from those new ends. **Cel9K** (processive GH9 cellulase, intermediate between classical endo- and exo-action) contributes additional cellobiose release and is particularly effective on crystalline cellulose. Together they reproduce the endo-exo synergy of natural cellulosome activity.

为什么需要三种酶？因为结晶纤维素不是单一的化学键——它是一种由结晶区和无定形区组成的超分子结构。**Cel5L**（持续性内切葡聚糖酶）裂解无定形区域的内部 β-1,4 糖苷键，产生新的链端。**Cel48S**（还原端外切纤维素酶, CBH）从这些新末端持续性水解释放纤维二糖。**Cel9K**（持续性 GH9 纤维素酶，介于经典内切与外切之间）贡献额外的纤维二糖释放，对结晶纤维素尤其有效。三者协同再现了天然纤维小体的内切-外切协同活性。

**Anchor Selection / 锚定蛋白选择**

We use INPNC — a truncated ice nucleation protein from *Pseudomonas syringae*. The full-length INP contains an N-terminal domain, a central repeating domain (which we remove), and a C-terminal domain. The truncated version (INPNC, retaining only the N- and C-terminal domains) achieves 3-4 times higher surface expression than full-length INP, because the repetitive central domain is a translational bottleneck and a proteolytic hotspot.

我们使用 INPNC——来自丁香假单胞菌的截短冰核蛋白。全长 INP 包含 N 端结构域、中央重复结构域（我们将其去除）和 C 端结构域。截短版本（INPNC，仅保留 N 端和 C 端结构域）实现比全长 INP 高 3-4 倍的表面表达，因为重复性中央结构域是翻译瓶颈和蛋白水解热点。

- **iGEM Registry part:** BBa_K1933011 (His-tagged for Western blot verification)
- **References for INPNC surface display:** Li et al., 2004 (foundational INP-N domain paper); Liu et al., 2025 (surface display biocatalysis review); Zhang et al., 2025 (whole-cell biocatalyst surface display review)

- **iGEM 注册部件：** BBa_K1933011（His 标签用于 Western blot 验证）
- **INPNC 表面展示参考文献：** Li 等 2004（INP-N 端结构域奠基性文献）；Liu 等 2025（表面展示生物催化综述）；Zhang 等 2025（全细胞生物催化剂表面展示综述）

**Signal Peptide / 信号肽**

The TorA signal peptide (Tat pathway) directs the INPNC-cellulase fusion to the periplasm before outer membrane integration. Tat is chosen over Sec because it transports folded proteins — important for cellulases, which must fold into their active conformations before reaching the surface.

TorA 信号肽（Tat 途径）将 INPNC-纤维素酶融合蛋白引导至周质空间，然后再进行外膜整合。选择 Tat 而非 Sec 是因为它转运已折叠的蛋白质——这对纤维素酶很重要，它们必须在到达表面前折叠成活性构象。

**Linker Design / 连接肽设计**

The linker between INPNC and the cellulase catalytic domain is a MIXED rigid-plus-flexible design: EAAAK repeats (rigid α-helical spacer) combined with GGGGS repeats (flexible glycine-serine linker). The rigid segments prevent the bulky cellulase domain from sterically interfering with INPNC membrane insertion. The flexible segments allow the cellulase active site to sample a range of orientations for substrate access. The final linker composition is based on molecular dynamics modeling predictions of optimal fusion protein dynamics. {{placeholder:modeling_linker_data}}

INPNC 与纤维素酶催化结构域之间的连接肽采用混合刚柔设计：EAAAK 重复序列（刚性 α-螺旋间隔）与 GGGGS 重复序列（柔性甘氨酸-丝氨酸连接肽）相结合。刚性片段防止庞大的纤维素酶结构域在空间上干扰 INPNC 膜插入。柔性片段允许纤维素酶活性位点采样多种取向以接触底物。最终连接肽组成基于融合蛋白最佳动力学的分子动力学建模预测。{{placeholder:modeling_linker_data}}

**What We Removed / 我们删除了什么**

Dockerin domains — these are *C. thermocellum* cellulosome-specific scaffolding domains that mediate assembly into the multi-enzyme complex. In our surface display system, INPNC is the anchor. Dockerins are vestigial and would only add unnecessary bulk to the fusion protein. They have been excised from all three constructs.

Dockerin 结构域——这些是热纤梭菌纤维小体特有的支架结构域，介导组装成多酶复合物。在我们的表面展示系统中，INPNC 是锚。Dockerins 是残留的，只会给融合蛋白增加不必要的体积。它们已从所有三个构建体中切除。

**Sequence Optimization / 序列优化**

All three cellulase genes are codon-optimized for *E. coli* expression and ordered through IDT gene synthesis. Codon optimization is particularly important here: *C. thermocellum* is a low-GC Gram-positive bacterium and its codon usage differs substantially from *E. coli*.

所有三种纤维素酶基因都针对大肠杆菌表达进行了密码子优化，并通过 IDT 基因合成订购。密码子优化在这里特别重要：热纤梭菌是低 GC 革兰氏阳性菌，其密码子使用模式与大肠杆菌有显著差异。

**Vector / 载体**

pCDF-1b backbone: CloDF13 origin of replication, compatible with the pBR322-origin vector used in Module A. This enables future co-transformation without plasmid incompatibility. Medium-low copy number (~20-30 copies/cell), spectinomycin resistance.

pCDF-1b 骨架：CloDF13 复制起点，与模块 A 中使用的 pBR322-ori 载体兼容。这使得未来共转化无需担心质粒不相容性。中低拷贝数（约 20-30 拷贝/细胞），壮观霉素抗性。

**Three Parallel Constructs / 三个平行构建体**

```
Construct 1: J23116 — B0034 — TorA — INPNC — Linker — Cel9K  — B0015
Construct 2: J23116 — B0034 — TorA — INPNC — Linker — Cel48S — B0015
Construct 3: J23116 — B0034 — TorA — INPNC — Linker — Cel5L  — B0015
```

Each construct expresses ONE cellulase variant. The three strains are mixed as an engineered consortium for synergistic cellulose degradation. This modular approach also allows us to characterize each enzyme independently and adjust the mixing ratio.

每个构建体表达一种纤维素酶变体。三种菌株作为工程化联合体混合以实现协同纤维素降解。这种模块化方法还允许我们独立表征每种酶并调整混合比例。

### BUILD / 构建

All three cellulase genes (codon-optimized) are synthesized commercially. The TorA-INPNC-Linker fragment is synthesized as a single gBlock. Gibson Assembly joins each cellulase variant with the anchor-linker module, the J23116-B0034 promoter-RBS cassette, and the B0015 terminator into the pCDF-1b backbone.

所有三种纤维素酶基因（密码子优化）通过商业合成。TorA-INPNC-连接肽片段合成为单一 gBlock。Gibson 组装将每个纤维素酶变体与锚-连接肽模块、J23116-B0034 启动子-RBS 表达盒和 B0015 终止子连接到 pCDF-1b 骨架中。

Each construct is transformed into DH5α, screened by colony PCR, verified by Sanger sequencing of the full fusion junction, and finally transformed into MG1655 for functional testing. Three strains are maintained separately and mixed at defined ratios for consortium experiments.

每个构建体转化至 DH5α，通过菌落 PCR 筛选，通过全长融合连接处的 Sanger 测序验证，最终转化至 MG1655 进行功能测试。三个菌株分别维护，按确定比例混合用于联合体实验。

### TEST / 测试

**Test 1: Proteinase K accessibility assay.** This is the gold standard for confirming surface localization. Intact cells are treated with proteinase K — a broad-spectrum protease that cannot cross the outer membrane. Surface-exposed proteins are digested; periplasmic and cytoplasmic proteins are protected. Post-treatment, cell lysates are analyzed by SDS-PAGE and Western blot.

**测试一：蛋白酶 K 可及性测定。** 这是确认表面定位的金标准。完整细胞用蛋白酶 K 处理——一种不能穿过外膜的广谱蛋白酶。表面暴露的蛋白被消化；周质和胞质蛋白受到保护。处理后，细胞裂解液通过 SDS-PAGE 和 Western blot 分析。

Expected result: INPNC-cellulase fusion bands (~120-150 kDa depending on the cellulase) should disappear or significantly decrease after proteinase K treatment. {{placeholder:proteinase_k_data}}

**Test 2: Western Blot — His-tag detection.** The INPNC anchor carries a His-tag (from BBa_K1933011). Anti-His Western blot confirms the expression and approximate molecular weight of all three fusion proteins. {{placeholder:western_blot_data_module_b}}

**测试二：Western Blot——His 标签检测。** INPNC 锚定蛋白携带 His 标签（来自 BBa_K1933011）。抗 His Western blot 确认所有三种融合蛋白的表达和近似分子量。{{placeholder:western_blot_data_module_b}}

**Test 3: Whole-cell cellulase activity assay.** Washed whole cells expressing each surface-displayed cellulase are incubated with cellulose substrates. Reducing sugar release is quantified by the DNS (dinitrosalicylic acid) method with a glucose standard curve. Substrates tested: CMC (carboxymethyl cellulose, soluble) and Avicel (microcrystalline cellulose, insoluble). Activity is measured over 24-72 hour time courses. {{placeholder:cellulase_activity_data}}

**测试三：全细胞纤维素酶活性测定。** 表达每种表面展示纤维素酶的洗涤完整细胞与纤维素底物孵育。还原糖释放通过 DNS（二硝基水杨酸）法以葡萄糖标准曲线定量。测试底物：CMC（羧甲基纤维素钠，可溶性）和 Avicel（微晶纤维素，不溶性）。在 24-72 小时时间过程中测量活性。{{placeholder:cellulase_activity_data}}

**Test 4: Consortium synergy assay.** The three strains are mixed at defined ratios (1:1:1 initial test, then optimized based on individual activity data) and tested for cellulose degradation activity. The key question: is the consortium activity greater than the sum of individual activities? This would confirm synergistic degradation — the hallmark of natural cellulosome function. {{placeholder:consortium_synergy_data}}

**测试四：联合体协同测定。** 三种菌株按确定比例混合并进行纤维素降解活性测试。关键问题：联合体活性是否大于各自活性的总和？这将确认协同降解——天然纤维小体功能的标志。{{placeholder:consortium_synergy_data}}

**Test 5: Surface display stability over time.** Cells are cultured for extended periods (up to 72 hours) and sampled at intervals for surface cellulase activity. This measures whether surface-displayed enzymes remain anchored and active, or whether proteolytic shedding reduces activity over time — a known issue for surface display systems. {{placeholder:stability_data}}

**测试五：表面展示随时间稳定性。** 细胞长时间培养，间隔取样测量表面纤维素酶活性。这测量了表面展示的酶是否保持锚定和活性，或蛋白水解脱落是否随时间降低活性——这是表面展示系统的已知问题。{{placeholder:stability_data}}

### LEARN / 学习

{{placeholder:module_b_learnings}}

The Surface Display module must answer: Are the INPNC-cellulase fusions successfully displayed on the outer membrane? Do the displayed enzymes retain catalytic activity? Does the consortium approach produce synergistic degradation? And critically — what is the surface display half-life in growing culture?

表面展示模块必须回答：INPNC-纤维素酶融合蛋白是否成功展示在外膜上？展示的酶是否保留催化活性？联合体方法是否产生协同降解？以及关键问题——在生长培养中的表面展示半衰期是多少？

---

## Integration Roadmap / 整合路线图

Module A and Module B are designed from the start to converge. The pBR322 origin (Module A) and CloDF13 origin (Module B) are compatible for stable co-maintenance. Once each module is individually validated, the integration phase will combine the optimized ascF-ascB construct (with the G-optimum promoter identified in Cycle 2) with the cellulase consortium constructs (Module B) in a single MG1655 host.

模块 A 和模块 B 从一开始就设计为汇合。pBR322 复制起点（模块 A）和 CloDF13 复制起点（模块 B）兼容，可稳定共维护。一旦每个模块各自得到验证，整合阶段将在单一 MG1655 宿主中结合优化的 ascF-ascB 构建体（使用循环二中确定的 G 最优启动子）和纤维素酶联合体构建体（模块 B）。

The integrated system closes the loop: surface-displayed cellulases degrade cellulose to cellobiose, cellobiose is imported through AscF and metabolized through AscB, and the PTS transport flux generates the chemotactic signal that biases bacterial swimming toward regions where cellulose degradation is producing cellobiose. In microgravity, this self-reinforcing cycle is our answer to the diffusion problem.

整合系统闭合了回路：表面展示的纤维素酶将纤维素降解为纤维二糖，纤维二糖通过 AscF 输入并通过 AscB 代谢，PTS 转运通量产生趋化信号，使细菌倾向于游向纤维素降解正在产生纤维二糖的区域。在微重力中，这个自我强化的循环是我们在扩散问题上的答案。

Integration DBTL cycles will be documented as experimental data becomes available. {{placeholder:integration_status}}

整合 DBTL 循环将在实验数据可用时记录。{{placeholder:integration_status}}

---

## Summary of Engineering Iterations / 工程迭代总结

| Cycle / 循环 | Module / 模块 | Goal / 目标 | Key Innovation / 关键创新 | Status / 状态 |
|:---|:---|:---|:---|:---:|
| A-1 | Chemotaxis | Awaken silent *asc* operon | Endogenous gene reactivation, no heterologous DNA | {{placeholder:cycleA1_status}} |
| A-2 | Chemotaxis | Promoter library for G-window scan | Mathematical model of PTS-CheA sensitivity tuning | {{placeholder:cycleA2_status}} |
| B-1 | Surface Display | INPNC-cellulase surface anchoring | Three-enzyme cocktail on truncated INP anchor | {{placeholder:cycleB1_status}} |
| Integration | Combined | Close the degradation-chemotaxis loop | pBR322 + CloDF13 compatible dual-plasmid system | {{placeholder:integration_status}} |

**What we did not engineer (and do not claim improvements in) / 我们没有工程化（也不声称改进）的部分：**

- DNA damage response and radiation resistance — RecA/LexA pathway not modified. Strain behaves as wild-type MG1655 under radiation stress. / DNA 损伤响应与辐射抗性 — RecA/LexA 通路未改造。在辐射应激下菌株与野生型 MG1655 表现一致。
- pH stress response and toxin avoidance — gad operon and MCP-based negative chemotaxis not modified. friskoli's PTS chemotaxis is decoupled from these pathways. / pH 应激响应与毒物负趋化 — gad 操纵子与 MCP 介导的负趋化未改造。friskoli 的 PTS 趋化与这些通路解耦。
- Cell-division regulation under microgravity — FtsZ and divisome components not modified. Filamentation under prolonged microgravity is expected to occur at wild-type rates. / 微重力下的细胞分裂调控 — FtsZ 与分裂体组分未改造。长期微重力下的丝状化预期以野生型速率发生。
- Quorum sensing and biofilm formation control — LuxI/LuxR-class systems not modified. Biofilm formation behaves as wild-type. / 群体感应与生物膜形成控制 — LuxI/LuxR 类系统未改造。生物膜形成行为与野生型一致。

These are deliberately left as future-generation engineering targets. Documenting what we did not do is as much a part of the engineering record as documenting what we did. / 这些是被有意留作下一代工程化目标的内容。记录"我们没做什么"和记录"我们做了什么"同样是工程档案的一部分。

---

## References / 参考文献

1. Vinuselvi P, Lee SK. "Engineering *Escherichia coli* for efficient cellobiose utilization." *Applied Microbiology and Biotechnology*. 2011;92:125–132. DOI: 10.1007/s00253-011-3434-9.

2. Leis B, Held C, Bergkemper F, et al. "Comparative characterization of all cellulosomal cellulases from *Clostridium thermocellum* reveals high diversity in activity, stability, and synergy." *Biotechnology for Biofuels*. 2017;10:30.

3. Li L, Kang DG, Cha HJ. "Functional display of foreign protein on surface of *Escherichia coli* using N-terminal domain of ice nucleation protein." *Biotechnology and Bioengineering*. 2004;85(2):214–221. DOI: 10.1002/bit.10892.

4. Liu W, Sun W, Liang CC, Chen T, Zhuang W, Liu D, Chen Y, Ying H. "*Escherichia coli* surface display: Advances and applications in biocatalysis." *ACS Synthetic Biology*. 2025;14(3):648–661. DOI: 10.1021/acssynbio.4c00793.

5. Zhang B, Gao X, Zhou Y, You S, Qi W, Wang M. "Surface display technologies for whole-cell biocatalysts: Advances in optimization strategies, food applications, and future perspectives." *Foods*. 2025;14(10):1803. DOI: 10.3390/foods14101803.

6. Barkai N, Leibler S. "Robustness in simple biochemical networks." *Nature*. 1997;387:913–917.

7. Adler J. "A method for measuring chemotaxis and use of the method to determine optimum conditions for chemotaxis by *Escherichia coli*." *Journal of General Microbiology*. 1973;74(1):77–91.

8. Rath A, Glibowicka M, Nadeau VG, Chen G, Deber CM. "Detergent binding explains anomalous SDS-PAGE migration of membrane proteins." *Proceedings of the National Academy of Sciences*. 2009;106(6):1760–1765. DOI: 10.1073/pnas.0813167106.

9. Miller GL. "Use of dinitrosalicylic acid reagent for determination of reducing sugar." *Analytical Chemistry*. 1959;31(3):426–428.

---

*This page documents our engineering as it happens. Placeholders indicate data still being collected. All experimental procedures follow standard iGEM BSL-1 laboratory safety protocols. Last updated: May 2026.*

*本页面记录了我们的工程过程。占位符表示仍在收集中的数据。所有实验程序遵循标准 iGEM BSL-1 实验室安全方案。最后更新：2026 年 5 月。*
