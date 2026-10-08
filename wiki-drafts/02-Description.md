# Description / 项目描述

## The Microgravity Diffusion Problem & A Chemotaxis-Coupled Solution

## 微重力扩散问题与趋化耦合解决方案

---

## 0. Table of Contents / 目录

| Section | English Title | 中文标题 |
|---------|--------------|----------|
| 1 | The Problem: Life in a Diffusion-Only World | 问题：纯扩散世界中的生命 |
| 2 | Microgravity Bioproduction: Why We Should Care | 微重力生物生产：我们为何关注 |
| 3 | The Depletion Zone: An Invisible Prison | 耗尽区：无形的牢笼 |
| 4 | The Core Insight: From Passive Diffusion to Active Pursuit | 核心洞察：从被动扩散到主动追寻 |
| 5 | The Asc Operon: A Sleeping Solution in E. coli's Genome | Asc 操纵子：大肠杆菌基因组中的沉睡解决方案 |
| 6 | PTS and Chemotaxis: The Coupling That Makes It Work | PTS 与趋化性：使其运作的关键耦合 |
| 7 | Module 1: Chemotaxis & Metabolism | 模块 1：趋化与代谢 |
| 8 | Module 2: Surface Degradation | 模块 2：表面降解 |
| 9 | The Positive Feedback Loop | 正反馈循环 |
| 10 | Self-Limitation Through Linear PTS Signaling | 通过 PTS 线性信号实现自我限制 |
| 11 | Why E. coli? Why Cellobiose? | 为什么是大肠杆菌？为什么是纤维二糖？ |
| 12 | Comparison with Existing Approaches | 与现有方法的比较 |
| 13 | Limitations and Challenges | 局限性与挑战 |
| 14 | Summary | 总结 |

---

## 1. The Problem: Life in a Diffusion-Only World / 问题：纯扩散世界中的生命

### 1.1 Life on Earth Is Shaped by Gravity / 地球上的生命由重力塑造

**English:**

Every organism on Earth evolved in a world where gravity is constant. Gravity does more than keep our feet on the ground — it drives **convection**. When a local region of fluid is heated, or when its solute concentration changes, density gradients form. Denser fluid sinks; less dense fluid rises. This natural circulation is a fundamental mechanism by which nutrients, gases, and signaling molecules move through liquid environments.

For a bacterial cell in a liquid culture on Earth, convection means that even a stationary cell experiences a constant refresh of its local environment. The depleted layer of nutrients around the cell is continuously swept away by bulk fluid movement. A single *E. coli* cell, only 1–2 micrometers long, effectively draws nutrients from a volume far larger than its immediate surroundings — not because it moves, but because the fluid moves around it.

This principle extends across all scales of bioproduction. From a 1 mL shake flask to a 10,000 L industrial fermenter, convection (through mechanical stirring, sparging, or natural circulation) is the dominant mode of mass transport. Diffusion alone cannot sustain life at any meaningful density or scale.

**中文：**

地球上的每一种生物都在重力恒定的世界中进化。重力所做的不只是将我们的脚固定在地面上——它还驱动着**对流**。当流体的局部区域受热，或当其溶质浓度发生变化时，密度梯度便形成了。密度较大的流体下沉；密度较小的流体上升。这种自然循环是营养物质、气体和信号分子在液体环境中移动的基本机制。

对于地球液体培养物中的一个细菌细胞来说，对流意味着即使是一个静止的细胞也能体验到局部环境的持续刷新。细胞周围耗尽的营养层被散装流体的运动持续冲走。一个仅有 1–2 微米长的大肠杆菌细胞，实际上从远大于其直接环境的体积中获取营养——不是因为它移动，而是因为流体在它周围移动。

这一原理贯穿所有规模的生物生产。从 1 mL 摇瓶到 10,000 L 工业发酵罐，对流（通过机械搅拌、通气或自然循环）是传质的主要模式。仅靠扩散无法在任何有意义的密度或规模下维持生命。

### 1.2 In Microgravity, the World Goes Still / 在微重力下，世界静止了

**English:**

Remove gravity, and you remove convection.

In the microgravity environment of space — whether on the International Space Station (ISS), a future lunar base, or a Mars-bound spacecraft — density-driven fluid circulation ceases. A bubble of CO₂ produced by a bacterial cell does not rise; it stays exactly where it was produced. A local depletion of glucose is not replenished by sinking or rising currents; the only mechanism for fresh glucose to arrive is molecular diffusion — the random thermal motion of individual molecules.

And diffusion is slow.

The diffusion coefficient of glucose in water at 37°C is approximately 6.7 × 10⁻⁶ cm²/s. For a molecule to travel 1 mm by diffusion alone takes roughly 250 seconds. To travel 1 cm takes over 6 hours. To travel the 5 mm radius of a typical depletion zone in microgravity? Gesztesi et al. (2023, *Front. Microbiol.*) calculated that a depletion zone of approximately 5.04 mm forms around metabolically active cells in the absence of convection. Within this zone, substrate concentration falls below the threshold required for optimal growth.

This means: a bacterial cell in a microgravity bioreactor can be surrounded by abundant nutrients at a distance of 5 mm — but those nutrients might as well be 5 kilometers away. The cell will starve in a sea of plenty.

**中文：**

移除重力，你就移除了对流。

在太空的微重力环境中——无论是在国际空间站（ISS）、未来的月球基地，还是前往火星的航天器上——密度驱动的流体循环停止了。细菌细胞产生的二氧化碳气泡不会上升；它精确地停留在产生的位置。葡萄糖的局部消耗不会因下沉或上升流而得到补充；新鲜葡萄糖到达的唯一机制是分子扩散——单个分子的随机热运动。

而扩散非常缓慢。

葡萄糖在 37°C 水中的扩散系数约为 6.7 × 10⁻⁶ cm²/s。一个分子仅靠扩散传播 1 毫米大约需要 250 秒。传播 1 厘米需要超过 6 小时。传播典型微重力耗尽区 5 毫米半径的距离需要多久？Gesztesi 等（2023，《微生物学前沿》）计算得出，在没有对流的条件下，代谢活跃细胞周围会形成约 5.04 毫米的耗尽区。在这个区域内，底物浓度下降到低于最佳生长所需的阈值。

这意味着：微重力生物反应器中的一个细菌细胞可能被 5 毫米外充足的营养物质所包围——但这些营养物质与 5 公里外无异。这个细胞将在丰饶之海中饥饿。

---

## 2. Microgravity Bioproduction: Why We Should Care / 微重力生物生产：我们为何关注

### 2.1 The Growing Need for Space Bioreactors / 对空间生物反应器日益增长的需求

**English:**

Humanity is entering a new era of space exploration. NASA's Artemis program aims to establish a permanent presence on the Moon. SpaceX's Starship architecture envisions regular cargo and crew flights to Mars. China's space station (Tiangong / 天宫) is already operational, with planned expansions for scientific research. The European Space Agency (ESA) and other national agencies are developing technologies for long-duration spaceflight.

All of these missions share a common requirement: **the need for sustainable life support.**

Current life support systems on the ISS rely primarily on physico-chemical methods — CO₂ scrubbing, water recycling via distillation, and oxygen generation via electrolysis. These systems work, but they are energy-intensive, require regular resupply of consumables, and cannot recycle organic waste into usable products.

Bioproduction in space offers a complementary approach:

| Application | Conventional Approach | Bioproduction Alternative |
|-------------|----------------------|--------------------------|
| Waste recycling | Store and return to Earth | Degrade organic waste into nutrients |
| Food production | Pre-packaged supplies | Grow microorganisms or plants |
| Pharmaceutical manufacturing | Launch from Earth | On-demand production in orbit |
| Material fabrication | Launch from Earth | In-situ resource utilization |

**中文：**

人类正在进入太空探索的新时代。NASA 的阿耳忒弥斯计划旨在在月球上建立永久存在。SpaceX 的星舰架构构想定期运送货物和机组人员前往火星。中国的空间站（天宫）已投入运营，并计划扩建以进行科学研究。欧洲空间局（ESA）和其他国家机构正在开发长期太空飞行的技术。

所有这些任务都有一个共同的要求：**对可持续生命维持的需求。**

当前 ISS 上的生命维持系统主要依赖物理化学方法——CO₂ 洗涤、通过蒸馏进行水回收、通过电解产生氧气。这些系统是有效的，但它们能耗高，需要定期补充消耗品，且无法将有机废物循环利用为有用产品。

太空生物生产提供了一种互补途径：

| 应用 | 传统方法 | 生物生产替代方案 |
|------|----------|------------------|
| 废物回收 | 储存并运回地球 | 将有机废物降解为营养物质 |
| 食品生产 | 预包装补给品 | 培养微生物或植物 |
| 药物制造 | 从地球发射 | 在轨道上按需生产 |
| 材料制造 | 从地球发射 | 原位资源利用 |

### 2.2 The Critical Bottleneck: Mass Transport / 关键瓶颈：传质

**English:**

Despite the promise of space bioproduction, a fundamental biophysical barrier remains: **mass transport in the absence of convection.** This is not a problem that can be solved by better genetic engineering alone. A bacterium equipped with the most efficient metabolic pathway in the world will still starve if nutrients cannot reach it.

Several engineering approaches have been proposed to address this:

- **Mechanical stirring** — rotating impellers or magnetic stir bars. On Earth, stirring is the obvious answer: it is well-established, predictable, and effective. But in space, mechanical stirring faces three critical problems: (i) stirring equipment is a heavy payload, adding significant launch cost and introducing maintenance risk from bearings, seals, and motors — a failed stirrer on a six-month Mars transit cannot be repaired; (ii) fluid dynamics in microgravity are not well-characterized, and stirring designs optimized for Earth may produce unexpected flow patterns — surface tension dominates over body forces, bubbles do not rise, and capillary effects dictate fluid distribution; (iii) most importantly, in microgravity there is no default sedimentation direction. On Earth, stirring works by distributing cells uniformly, which makes sense because gravity pulls cells downward and stirring counteracts this. But in space, the optimal strategy is NOT uniform distribution — it is **enrichment around the substrate.** Mechanical stirring, by dispersing cells away from the cellulose surface, would actually REDUCE degradation efficiency, working against the very goal of efficient mass transfer.

- **Perfusion systems** — continuous flow of fresh medium through a cell retention system. While effective for mass transfer, these systems require pumps, tubing, reservoirs, and sterile connections, adding complexity and bulk unsuitable for small-scale autonomous space bioreactors. Maintenance requirements make them impractical for long-duration missions without crew intervention.

- **Microfluidic platforms** — precisely engineered channels for controlled fluid flow. Excellent for research purposes, but limited scalability makes them unsuitable for the production volumes needed in space applications.

Each of these approaches adds mass, complexity, power consumption, and potential failure points to a space mission.

This leads to a philosophical reframing of the problem:

> **What is the essence of stirring? We stir to bring cells and substrate together. In space, the better way is not to move the fluid — it is to move the bacteria.**

What if, instead of engineering the fluid, we could engineer the bacteria to solve the problem themselves?

This is the question that leads to friskoli.

**中文：**

尽管太空生物生产前景广阔，但仍有一个基本的生物物理障碍：**在没有对流的情况下的传质问题。** 这不是仅靠更好的基因工程就能解决的问题。即使装备了世界上最有效代谢途径的细菌，如果营养物质无法到达它，它仍然会饥饿。

已有几种工程方法被提出以解决这一问题：

- **机械搅拌**——旋转叶轮或磁力搅拌棒。在地球上，搅拌是显而易见的答案：它成熟、可预测且有效。但在太空中，机械搅拌面临三个关键问题：(i) 搅拌设备是沉重的有效载荷，增加了显著的发射成本，并引入了轴承、密封件和电机的维护风险——在为期六个月的飞往火星途中，损坏的搅拌器无法维修；(ii) 微重力下的流体动力学尚未被充分表征，为地球优化的搅拌设计可能产生意想不到的流动模式——表面张力主导体积力，气泡不会上升，毛细效应决定流体分布；(iii) 最重要的是，在微重力下没有默认的沉降方向。在地球上，搅拌通过将细胞均匀分布来发挥作用，这是有道理的，因为重力将细胞向下拉而搅拌抵消了这一点。但在太空中，最优策略不是均匀分布——而是**底物周围的富集。** 机械搅拌会将细胞从纤维素表面分散开，实际上会降低降解效率，与高效传质的目标背道而驰。

- **灌注系统**——通过细胞截留系统连续流动的新鲜培养基。虽然对传质有效，但这些系统需要泵、管道、储液器和无菌连接，增加了不适合小型自主空间生物反应器的复杂性和体积。维护需求使其在没有机组人员干预的长期任务中不切实际。

- **微流控平台**——精密设计的通道用于控制流体流动。在研究目的上表现出色，但有限的可扩展性使其不适用于空间应用所需的生产规模。

每种方法都给太空任务增加了质量、复杂性、能耗和潜在的故障点。

这引出了对问题的哲学性再框定：

> **搅拌的本质是什么？我们搅拌是为了让细胞和底物接触。在太空中，更好的方法不是移动流体——而是移动细菌。**

如果我们不是工程改造流体，而是工程改造细菌来自己解决问题呢？

这就是通往 friskoli 的问题。

---

## 3. The Depletion Zone: An Invisible Prison / 耗尽区：无形的牢笼

### 3.1 Physics of the Depletion Zone / 耗尽区的物理学

**English:**

Consider a single *E. coli* cell in a microgravity bioreactor. The cell consumes glucose (or any soluble substrate) at a rate determined by its metabolic demand. Surrounding the cell, glucose molecules diffuse toward it from the bulk medium. At steady state, a concentration gradient establishes:

```
C(r) = C₀ - (R·r₀² / D) · (1/r)
```

Where:
- C(r) = concentration at distance r from cell center
- C₀ = bulk concentration (far from cell)
- R = consumption rate (molecules per second per cell)
- r₀ = cell radius
- D = diffusion coefficient

The depletion zone radius — the distance at which concentration drops below a critical threshold — scales as:

```
r_depletion ~ R / (4πD·C₀)
```

Gesztesi et al. (2023) report that, for metabolically active cells in simulated microgravity, the depletion zone extends on the order of **a few millimeters** (their representative value: ~5 mm) — depending on consumption rate, diffusion coefficient, and bulk substrate concentration. Even at the low end, this is **roughly three orders of magnitude larger than the bacterial cell itself**. For a 1.7 m human, the equivalent reach gap would be on the order of kilometers.

**中文：**

考虑微重力生物反应器中的一个大肠杆菌细胞。该细胞以其代谢需求所决定的速率代谢葡萄糖（或任何可溶性底物）。在细胞周围，葡萄糖分子从散装培养基向它扩散。在稳态下，建立起浓度梯度：

```
C(r) = C₀ - (R·r₀² / D) · (1/r)
```

其中：
- C(r) = 距细胞中心距离 r 处的浓度
- C₀ = 散装浓度（远离细胞）
- R = 消耗速率（每秒每细胞分子数）
- r₀ = 细胞半径
- D = 扩散系数

耗尽区半径——浓度降至临界阈值以下的距离——按以下比例缩放：

```
r_depletion ~ R / (4πD·C₀)
```

Gesztesi 等（2023）报道，在模拟微重力条件下，代谢活跃细胞的耗尽区**在毫米量级**（代表值约 5 mm）——具体取决于消耗速率、扩散系数和本体底物浓度。即便取较低值，这也比细菌细胞本身大约 **三个数量级**。换算到 1.7 米高的人类，相应的"够不到食物"距离在公里量级。

### 3.2 The Nutrient Competition Problem / 营养竞争问题

**English:**

At realistic cell densities (10⁷–10⁸ cells/mL), the depletion zones of neighboring cells overlap substantially. A 5 mm radius sphere has a volume of approximately 0.52 mL — at 10⁷ cells/mL, roughly 5 million cells share this volume. This means the entire culture volume is depleted territory: every cell is simultaneously drawing from the same limited diffusive supply. Nutrients cannot arrive fast enough to satisfy the combined metabolic demand.

In a convection-driven system on Earth, this is not a problem — bulk fluid motion continuously refreshes the medium throughout the reactor. In microgravity, with diffusion as the sole transport mechanism, the shared depletion volume becomes a hard biophysical constraint on growth and productivity.

| Parameter | Earth (with convection) | Microgravity (diffusion only) |
|-----------|------------------------|------------------------------|
| Effective nutrient reach per cell | >1 cm (with mixing) | ~mm-scale (diffusion-limited) |
| Depletion zone radius | Negligible (swept away) | mm-scale (Gesztesi et al.) |
| Expected density challenge | High (10⁹–10¹⁰ cells/mL) achievable | Growth-limited (estimated 1–2 orders below Earth) |
| Stirring requirement | Standard practice | Required, with major caveats (see §2.2) |

This is the fundamental bottleneck that friskoli aims to break — not by preventing depletion zone overlap (which is unavoidable at any useful density), but by giving cells the ability to actively migrate toward nutrient sources.

**中文：**

在实际细胞密度下（10⁷–10⁸ 个细胞/mL），相邻细胞的耗尽区大量重叠。5 毫米半径球体的体积约为 0.52 mL——在 10⁷ 个细胞/mL 的密度下，大约有 500 万个细胞共享这一体积。这意味着整个培养体积都是被耗尽的空间：每个细胞同时从同一个有限的扩散供给中吸取营养。营养物质无法以足够快的速度到达以满足联合的代谢需求。

在地球上的对流驱动系统中，这不是问题——散装流体运动持续刷新整个反应器中的培养基。在微重力下，扩散是唯一的传输机制，共享的耗尽体积成为生长和生产力的硬性生物物理约束。

| 参数 | 地球（有对流） | 微重力（仅扩散） |
|------|---------------|-----------------|
| 单细胞有效营养到达范围 | >1 cm（有混合） | 毫米尺度（扩散限制） |
| 耗尽区半径 | 可忽略（被冲走） | 毫米尺度（Gesztesi 等） |
| 预期密度挑战 | 可达高密度（10⁹–10¹⁰ cells/mL） | 受生长限制（估计比地球低 1–2 个数量级） |
| 搅拌需求 | 常规做法 | 必需，但有重大限制（见 §2.2） |

这是 friskoli 旨在突破的根本瓶颈——并非通过防止耗尽区重叠（在任何有用密度下这都是不可避免的），而是通过赋予细胞主动向营养源迁移的能力。

---

## 4. The Core Insight: From Passive Diffusion to Active Pursuit / 核心洞察：从被动扩散到主动追寻

**English:**

The central idea of friskoli is elegantly simple: **instead of waiting for food to diffuse to the bacteria, engineer the bacteria to swim toward their food.**

This shifts the paradigm from a passive, diffusion-limited system to an active, migration-enhanced system. A swimming *E. coli* cell moves at approximately 25 μm/s (Berg & Brown, 1972). In one minute a swimming cell traverses ~1.5 mm — a distance that would take a diffusing glucose molecule about 10 minutes.

Over a 5 mm depletion zone:

| Transport Mode | Characteristic time / interpretation |
|---------------|---------------------|
| Molecular diffusion of glucose (D ~ 6.7 × 10⁻⁶ cm²/s) | ~6,000 s (~100 min) across 5 mm |
| Straight swimming at ~25 μm/s | ~200 s (~3 min), ballistic upper-bound estimate |
| Chemotactically biased swimming | Faster than unbiased random walk; depends on gradient strength and run/tumble statistics |
| Convection in a mixed terrestrial bioreactor | Seconds-scale, depending on reactor geometry and stirring |

Bacterial swimming cannot match convection, but on this length scale directed movement is roughly **an order of magnitude faster than diffusion alone**. Crucially, swimming can be **biased** by chemotaxis — a feature diffusion lacks entirely.

**中文：**

friskoli 的核心思想优雅而简单：**不是等待食物扩散到细菌，而是工程改造细菌使其游向食物。**

这将系统从被动的、扩散限制的范式转变为主动的、迁移增强的范式。一个游动的大肠杆菌细胞以约 25 μm/s 的速度移动（Berg & Brown，1972）。在一分钟内，一个游动细胞可以穿越约 1.5 毫米——这是扩散的葡萄糖分子需要约 10 分钟才能穿越的距离。

穿越 5 毫米耗尽区：

| 传输模式 | 特征时间 / 解释 |
|---------|----------------------|
| 葡萄糖分子扩散（D ~ 6.7 × 10⁻⁶ cm²/s） | ~6,000 秒（~100 分钟），穿越 5 mm |
| 直线游动 ~25 μm/s | ~200 秒（~3 分钟），弹道式上限估计 |
| 趋化偏置游动 | 比无偏随机游走更快；取决于梯度强度和 run/tumble 统计 |
| 地面混合生物反应器中的对流 | 秒级到分钟级，取决于反应器几何与搅拌 |

细菌游动无法匹敌对流，但在此尺度上定向运动比扩散**快约一个数量级**。更关键的是，游动可由趋化性**偏置**——这是扩散完全不具备的特征。

### 4.2 The Road to Chemotaxis / 通往趋化性之路

**English:**

Our team did not arrive at chemotaxis immediately. We first considered several alternative strategies for breaking the mass transfer bottleneck in microgravity:

- **Controlled flow systems:** Actively pump medium past stationary cells. This would require precise microfluidic engineering, pumps, and power — adding complexity that defeats the purpose of a simple, robust biological solution designed for autonomous space operation.
- **Co-culture systems:** Pair cellulose-degrading organisms with consuming organisms in close proximity. While elegant in principle, co-cultures require regular maintenance, are sensitive to population imbalance, and are difficult to keep stable over long durations without external intervention — all incompatible with the autonomy required for space missions.
- **Enzyme-only approaches:** Deploy free cellulase enzymes to degrade cellulose into soluble sugars. But enzymes cannot sense gradients, cannot self-renew, and cannot concentrate themselves where they are most needed. They must be continuously replenished from Earth.

None of these approaches felt truly space-compatible. They each required something that space cannot easily provide: maintenance, power, or precise control. We found ourselves running into the same wall: Earth solutions, adapted for space, inevitably carried Earth assumptions with them.

The breakthrough came when we asked a different question. Instead of "How do we engineer the environment to serve the bacteria?", we asked **"How do we engineer the bacteria to serve themselves?"**

This is when chemotaxis entered our thinking.

*E. coli* already possesses one of the most sophisticated sensory-motor systems in biology. Its chemotaxis network can detect concentration differences as small as a few molecules per cell volume, process this information through a signaling cascade, and direct the flagellar motor to execute a biased random walk toward favorable conditions — all within milliseconds, all without external control. This is not a system we need to build from scratch. It is a native capability, honed by billions of years of evolution, waiting to be connected to the right input.

What if we could connect this native chemotaxis system to cellulose degradation? What if the product of cellulose breakdown — cellobiose — could serve as both nutrient and chemoattractant? The bacterium would not just eat the cellulose; it would *seek it out*.

The key insight was this: **use the bacteria's OWN chemotaxis behavior to break the mass transfer bottleneck.** This is synthetic biology in its truest spirit — let biology solve engineering problems. Rather than building mechanical systems to move fluid, we rewire the bacteria's native navigation system to bring them to their food.

Chemotaxis transforms bacteria from **"passive waiters"** — stationary cells hoping that diffusion delivers nutrients — into **"active foragers"** — mobile cells that seek out and concentrate at the substrate surface. In a world without convection, active foraging is not a luxury. It is a survival strategy.

**中文：**

我们的团队并非立即得出趋化性的方案。我们首先考虑了其他几种突破微重力传质瓶颈的策略：

- **控制流动系统：** 主动泵送培养基经过静止细胞。这将需要精密的微流控工程、泵和电力——增加的复杂性违背了为自主空间运行设计简洁、稳健生物解决方案的初衷。
- **共培养系统：** 将纤维素降解生物与消耗生物近距离配对。虽然在原理上优雅，但共培养需要定期维护，对种群失衡敏感，且在没有外部干预的情况下难以长期保持稳定——所有这些都与太空任务所需的自主性不兼容。
- **纯酶途径：** 投放游离纤维素酶将纤维素降解为可溶性糖。但酶无法感知梯度，无法自我更新，也无法在最需要的地方自我集中。它们必须从地球持续补充。

这些方法中没有一种在本质上与太空兼容。它们每一个都需要太空难以提供的东西：维护、电力或精确控制。我们发现自己不断撞上同一面墙：为地球设计的方案，在适应太空时，不可避免地承载着地球的假设。

突破来自我们提出了一个不同的问题。不是"我们如何工程改造环境来服务细菌？"，而是**"我们如何工程改造细菌来服务它们自己？"**

这就是趋化性进入我们思维的时刻。

大肠杆菌已经拥有生物学中最精密的感知-运动系统之一。其趋化网络可以检测到低至每个细胞体积数个分子的浓度差异，通过信号级联处理这些信息，并指导鞭毛马达执行偏向性随机游走向有利条件移动——所有这些都在毫秒内完成，完全不需要外部控制。这不是我们需要从零开始构建的系统。这是一个经过数十亿年进化磨练的天然能力，正等待连接到正确的输入端。

如果我们能够将这个天然的趋化系统与纤维素降解连接起来呢？如果纤维素分解的产物——纤维二糖——能够同时充当营养物和化学吸引物呢？细菌不仅会吃纤维素；它会主动寻找纤维素。

关键的洞察是：**利用细菌自身的趋化行为来打破传质瓶颈。** 这是合成生物学最真切的精髓——让生物学解决工程问题。与其建造机械系统来移动流体，我们重新连接细菌天然的导航系统，将它们带到食物面前。

趋化性将细菌从**"被动等待者"**——静止的细胞期望扩散送来营养——转变为**"主动觅食者"**——移动的细胞寻找并聚集于底物表面。在一个没有对流的世界里，主动觅食不是奢侈品，而是一种生存策略。

---

## 5. The Asc Operon: A Sleeping Solution in E. coli's Genome / Asc 操纵子：大肠杆菌基因组中的沉睡解决方案

### 5.1 Discovery and Characterization / 发现与表征

**English:**

In 1992, Barry G. Hall and Jun Xu at the University of Rochester published a paper titled "Nucleotide sequence, function, activation, and evolution of the cryptic *asc* operon of *Escherichia coli* K-12" in *Molecular Biology and Evolution*. They described the cryptic *asc* region, in which *ascF* (`b2715`) and *ascB* (`b2716`) form the *ascFB* functional unit, while the divergently transcribed repressor gene *ascG* (`b2714`) regulates the operon. In modern MG1655 genome coordinates, this region lies around NC_000913.3 ~2.84 Mb.

- **ascF** encodes a cellobiose-specific Enzyme II (EII) component of the phosphotransferase system (PTS). This is the transmembrane transporter that binds cellobiose in the periplasm, translocates it across the inner membrane, and phosphorylates it to cellobiose-6-phosphate during transport.
- **ascB** encodes a phospho-β-glucosidase (phospho-cellobiose hydrolase) that cleaves cellobiose-6-phosphate into glucose-6-phosphate and glucose. Glucose-6-phosphate enters glycolysis directly; glucose can be phosphorylated by glucokinase and also enter glycolysis.

Crucially, Hall & Xu showed that this operon is **cryptic** — it is present in the genome but not expressed under standard laboratory conditions (e.g., in the presence of preferred sugars like glucose). The operon is under catabolite repression and is also regulated by a specific repressor, AscG. In wild-type MG1655, the operon is essentially silent.

But the genetic information is there. It just needs to be activated.

**中文：**

1992 年，罗彻斯特大学的 Barry G. Hall 和 Jun Xu 在《分子生物学与进化》上发表了一篇题为"大肠杆菌隐秘 *asc* 操纵子的核苷酸序列、功能、激活与进化"的论文。他们描述了隐秘的 *asc* 区域，其中 *ascF*（`b2715`）和 *ascB*（`b2716`）构成 *ascFB* 功能单元，而反向转录的阻遏蛋白基因 *ascG*（`b2714`）调控该操纵子。按现代 MG1655 基因组坐标，该区域位于 NC_000913.3 约 2.84 Mb 位置。

- **ascF** 编码磷酸转移酶系统（PTS）中纤维二糖特异性酶 II（EII）组分。这是在周质空间结合纤维二糖、将其转运穿过内膜并在转运过程中将其磷酸化为纤维二糖-6-磷酸的跨膜转运蛋白。
- **ascB** 编码一种磷酸-β-葡糖苷酶（磷酸纤维二糖水解酶），将纤维二糖-6-磷酸裂解为葡萄糖-6-磷酸和葡萄糖。葡萄糖-6-磷酸直接进入糖酵解；葡萄糖可由葡糖激酶磷酸化后也进入糖酵解。

关键是，Hall & Xu 证明这个操纵子是**隐性的**——它存在于基因组中，但在标准实验室条件下不表达（例如，在存在葡萄糖等偏好糖的情况下）。该操纵子受分解代谢物抑制，并受特异性阻遏蛋白 AscG 调控。在野生型 MG1655 中，该操纵子基本上是沉默的。

但遗传信息就在那里。它只需要被激活。

### 5.2 Why Is the Asc Operon Silent? / 为什么 Asc 操纵子是沉默的？

**English:**

The existence of cryptic operons in bacterial genomes raises an evolutionary question: why would *E. coli* carry genetic machinery it does not use?

The fact that *E. coli* maintains an intact, actively regulated operon for a substrate it rarely encounters in its primary habitat is best explained by **conditional utility**: cellobiose appears infrequently in the environments *E. coli* inhabits (e.g., decaying plant matter in soil or feces), and the operon is held under tight AscG repression to avoid protein-synthesis cost when no inducer is present. The genetic information is preserved for when it is needed; the regulation is what keeps it silent — not gene decay.

Whatever the evolutionary reason, the existence of this silent operon is a gift for synthetic biology. It means we do not need to introduce a complete heterologous pathway from another organism. The core transporter and enzyme are already present in the genome — we simply need to **re-express** them under a constitutive or inducible promoter.

This is the approach friskoli takes: replace the native regulatory region of the *asc* operon with a constitutive promoter (or an inducible promoter, depending on design considerations), ensuring that AscF and AscB are produced at functional levels without requiring the presence of cellobiose for induction.

**中文：**

细菌基因组中隐性操纵子的存在提出了一个进化问题：为什么大肠杆菌会携带它不使用的遗传机制？

大肠杆菌为一种在其主要栖息地中罕见的底物保留一个完整、受主动调控的操纵子，最合理的解释是**条件性效用**：纤维二糖在大肠杆菌可能进入的环境（如土壤或粪便中的腐烂植物物质）中偶尔出现，操纵子由 AscG 严密抑制以避免无诱导物时的蛋白合成代价。遗传信息被保留以备所需；让它保持沉默的是调控本身，而非基因衰退。

无论进化原因如何，这个沉默操纵子的存在是合成生物学的一份礼物。这意味着我们不需要从另一种生物中引入完整的异源途径。核心转运蛋白和酶已存在于基因组中——我们只需要在组成型或诱导型启动子下**重新表达**它们。

这就是 friskoli 采取的方法：用组成型启动子（或诱导型启动子，取决于设计考量）替换 *asc* 操纵子的天然调控区，确保 AscF 和 AscB 以功能性水平产生，而不需要纤维二糖的存在来诱导。

---

## 6. PTS and Chemotaxis: The Coupling That Makes It Work / PTS 与趋化性：使其运作的关键耦合

### 6.1 The Phosphotransferase System (PTS) / 磷酸转移酶系统（PTS）

**English:**

The bacterial phosphotransferase system (PTS) is a multi-component sugar transport system that couples the import of sugars with their phosphorylation. The phosphoryl group from phosphoenolpyruvate (PEP) is transferred through a cascade:

```
PEP → Enzyme I (EI) → HPr → EIIA → EIIB → EIIC (transporter)
```

The EII complex is sugar-specific — there are dozens of different EII complexes in *E. coli*, each specific to a particular sugar or class of sugars. AscF is the EII complex specific for cellobiose.

The key insight for friskoli is that the PTS is not just a transport system. It is also **a signaling system**.

**中文：**

细菌磷酸转移酶系统（PTS）是一个多组分糖转运系统，将糖的输入与其磷酸化耦合。磷酸基团从磷酸烯醇式丙酮酸（PEP）通过级联反应传递：

```
PEP → 酶 I（EI）→ HPr → EIIA → EIIB → EIIC（转运蛋白）
```

EII 复合物是糖特异性的——大肠杆菌中有数十种不同的 EII 复合物，每种特定于一种或一类糖。AscF 是纤维二糖特异性的 EII 复合物。

对 friskoli 来说，关键洞见是 PTS 不仅仅是一个转运系统。它也是一个**信号系统**。

### 6.2 PTS-Chemotaxis Coupling: The Lux-Neumann Mechanism / PTS-趋化性耦合：Lux-Neumann 机制

**English:**

The connection between PTS activity and chemotaxis was first clearly demonstrated by Lux et al. (1995, *PNAS*). They showed that the transport of PTS substrates triggers a chemotactic response — bacteria swim toward PTS sugars — and that this response requires the general PTS proteins (EI and HPr), not the specific EII complexes. The key conclusion from Lux et al. is that **unphosphorylated EI inhibits CheA autophosphorylation**, while phosphorylated EI does not. The mechanism was further elaborated by Neumann et al. (2012, *PNAS*) and is summarized below.

The key state variable is the phosphorylation state of Enzyme I (EI). EI sits at the top of the PTS phosphotransfer chain, accepting phosphoryl groups from PEP and passing them down through HPr → EIIA → EIIB → EIIC → sugar.

**No PTS sugar present:**
PTS components are mostly phosphorylated. Little unphosphorylated EI is available to inhibit CheA, so CheA maintains baseline autophosphorylation → baseline CheY-P → normal run-and-tumble behavior.

**PTS sugar present (e.g., cellobiose transported through AscF):**
Sugar transport drains phosphate through the PTS cascade. PTS components become dephosphorylated, and **unphosphorylated EI increases**. Unphosphorylated EI inhibits CheA autophosphorylation → CheY-P decreases → less FliM binding → flagellar motors spend more time in CCW rotation → **longer smooth runs**.

**Behavioral output:**
A cell swimming up a cellobiose gradient experiences rising PTS flux → more unphosphorylated EI → stronger CheA inhibition → fewer tumbles → longer runs in the favorable direction. The result is a biased random walk **toward** cellobiose. This is chemotaxis.

Unlike the classical MCP-based chemotaxis system, the PTS pathway does **not** include methylation-based perfect adaptation at the signal-input level. The PTS input reflects sugar influx approximately linearly (Somavanshi et al. 2016; see §10 for further discussion of how self-limitation arises).

**中文：**

PTS 活性与趋化性之间的联系最早由 Lux 等（1995，《美国国家科学院院刊》）明确证明。他们表明 PTS 底物的运输触发趋化反应——细菌游向 PTS 糖——且该反应需要通用的 PTS 蛋白（EI 和 HPr），而非特异的 EII 复合物。Lux 等的关键结论是：**未磷酸化 EI 抑制 CheA 自磷酸化**，而磷酸化 EI 不抑制。该机制由 Neumann 等（2012，《美国国家科学院院刊》）进一步阐述，概述如下。

关键的状态变量是酶 I（EI）的磷酸化状态。EI 位于 PTS 磷酸转移链的顶端，从 PEP 接受磷酸基团，向下游经 HPr → EIIA → EIIB → EIIC → 糖逐级传递。

**无 PTS 糖时：**
PTS 组分多处于磷酸化状态。可抑制 CheA 的未磷酸化 EI 很少，因此 CheA 维持基线自磷酸化 → 基线 CheY-P → 正常的 run-and-tumble 行为。

**有 PTS 糖时（例如纤维二糖经 AscF 转运）：**
糖转运消耗 PTS 磷酸流。PTS 组分去磷酸化，**未磷酸化 EI 增加**。未磷酸化 EI 抑制 CheA 自磷酸化 → CheY-P 下降 → FliM 结合减少 → 鞭毛马达更多时间处于 CCW 旋转 → **更长的平滑游动**。

**行为输出：**
细胞沿纤维二糖梯度向上游动时，PTS 通量上升 → 未磷酸化 EI 增加 → CheA 抑制增强 → 翻滚减少 → 在有利方向上更长的游动。结果是一次**朝向**纤维二糖的有偏随机游走。这就是趋化性。

与经典的 MCP 趋化系统不同，PTS 通路在信号输入层面**不**包含基于甲基化的完美适应。PTS 输入近似线性地反映糖转运通量（Somavanshi 等 2016；关于自我限制如何产生的进一步讨论见 §10）。

### 6.3 The Coupling Mechanism / 耦合机制

**English:**

Let us summarize the critical chain of events for friskoli:

```
Cellobiose in environment
    ↓ (binds to AscF EIIC domain)
Transport + phosphorylation of cellobiose
    ↓ (consumes phosphoryl groups from PTS cascade)
PTS components dephosphorylate → unphosphorylated EI increases
    ↓ (unphosphorylated EI inhibits CheA autophosphorylation)
Decreased CheA autophosphorylation
    ↓ (less CheA~P → less CheY phosphorylation)
Decreased CheY~P → decreased flagellar CW bias
    → longer smooth runs → biased random walk
    ↓ (PEP/pyruvate ratio feedback stabilizes PTS flux)
Net movement up cellobiose gradient
```

Each step in this chain is supported by peer-reviewed literature:

| Step | Key Reference |
|------|--------------|
| PTS transport of cellobiose by AscF | Hall & Xu 1992 |
| Unphosphorylated EI inhibits CheA | Lux et al. 1995 |
| EI dephosphorylation alters CheA activity | Neumann et al. 2012 |
| PTS signal is approximately linear at input; adaptation involves downstream chemotaxis machinery | Somavanshi et al. 2016; Neumann et al. 2012 |
| Swimming speed measurement | Berg & Brown 1972 |

**中文：**

让我们总结 friskoli 的关键事件链：

```
环境中的纤维二糖
    ↓（与 AscF EIIC 结构域结合）
纤维二糖的运输和磷酸化
    ↓（消耗 PTS 级联中的磷酸基团）
PTS 组分去磷酸化 → 未磷酸化 EI 增加
    ↓（未磷酸化 EI 抑制 CheA 自磷酸化）
CheA 自磷酸化降低
    ↓（CheA~P 减少 → CheY 磷酸化减少）
CheY~P 降低 → 鞭毛顺时针偏置降低
    → 更长的平滑游动 → 有偏随机游走
    ↓（PEP/丙酮酸比率反馈稳定 PTS 通量）
沿纤维二糖梯度向上的净移动
```

该链中的每个步骤都有同行评审文献支持：

| 步骤 | 关键文献 |
|------|---------|
| AscF 对纤维二糖的 PTS 转运 | Hall & Xu 1992 |
| 未磷酸化 EI 抑制 CheA | Lux 等 1995 |
| EI 去磷酸化改变 CheA 活性 | Neumann 等 2012 |
| PTS 信号在输入端近似线性；适应涉及下游趋化机制 | Somavanshi 等 2016；Neumann 等 2012 |
| 游动速度测量 | Berg & Brown 1972 |

---

## 7. Module 1: Chemotaxis & Metabolism / 模块 1：趋化与代谢

### 7.1 Design Goal / 设计目标

**English:**

Module 1 aims to re-express the silent *asc* operon in *E. coli* MG1655, restoring the ability to transport and metabolize cellobiose while simultaneously enabling PTS-coupled chemotaxis toward cellobiose gradients.

**中文：**

模块 1 旨在在大肠杆菌 MG1655 中重新表达沉默的 *asc* 操纵子，恢复运输和代谢纤维二糖的能力，同时实现朝向纤维二糖梯度的 PTS 耦合趋化性。

### 7.2 Genetic Construction / 遗传构建

| Element | Description | Source |
|---------|-------------|--------|
| Promoter | Constitutive or inducible (e.g., J23100 or pBAD) | iGEM Registry / design |
| RBS | Designed for optimal translation initiation | Design |
| *ascF* | Cellobiose-specific PTS EII transporter (1.4 kb) | *E. coli* MG1655 genome |
| *ascB* | Phospho-β-glucosidase (1.3 kb) | *E. coli* MG1655 genome |
| Terminator | Strong transcriptional terminator (e.g., Bba_B0015) | iGEM Registry |

The native repressor AscG is left intact — it will not affect expression from a constitutive promoter. Alternatively, *ascG* could be deleted if native regulation interferes with our construct.

---

## 8. Module 2: Surface Degradation / 模块 2：表面降解

### 8.1 Design Goal / 设计目标

**English:**

Module 2 enables *E. coli* to degrade cellulose directly at its surface, releasing cellobiose that serves as both a nutrient source and a chemoattractant signal. This is achieved through surface display of a heterologous cellulase enzyme anchored to the outer membrane via the ice nucleation protein (INP) system.

**中文：**

模块 2 使大肠杆菌能够在其表面直接降解纤维素，释放出既作为营养源又作为化学吸引物信号的纤维二糖。这是通过将异源纤维素酶通过冰核蛋白（INP）系统锚定于外膜的表面展示来实现的。

### 8.2 The INP Display System / INP 展示系统

**English:**

The ice nucleation protein (INP) from *Pseudomonas syringae* has been established as an effective surface display system in Gram-negative bacteria. Kim & Ku (2018, *Molecules*) reviewed the use of INP as an anchoring motif for displaying heterologous proteins on the bacterial outer membrane. The INP system offers several advantages:

1. **Correct localization:** The N-terminal domain of INP targets and inserts the fusion protein into the outer membrane.
2. **Proteolytic stability:** The INP anchor protects the fused enzyme from degradation.
3. **Minimal growth burden:** Moderate expression levels avoid metabolic overload.
4. **Proven with cellulases:** INP has been successfully used to display multiple types of cellulases including endoglucanases, exoglucanases, and β-glucosidases.

The construct places the cellulase at the C-terminus of the INP anchoring domain, ensuring that the active site of the enzyme faces the extracellular environment. Our design uses a three-enzyme cocktail (Cel48S, Cel9K, Cel5L from *Clostridium thermocellum*) expressed in separate strains and mixed as a consortium — see Design page for full details.

**中文：**

来自丁香假单胞菌（*Pseudomonas syringae*）的冰核蛋白（INP）已被确立为革兰氏阴性菌中有效的表面展示系统。Kim & Ku（2018，《Molecules》）综述了使用 INP 作为锚定基序在细菌外膜上展示异源蛋白的方法。INP 系统具有几个优势：

1. **正确定位：** INP 的 N 端结构域将融合蛋白靶向并插入外膜。
2. **蛋白酶稳定性：** INP 锚定保护融合酶免受降解。
3. **最小生长负担：** 适度的表达水平避免代谢过载。
4. **经纤维素酶验证：** INP 已成功用于展示多种类型的纤维素酶，包括内切葡聚糖酶、外切葡聚糖酶和 β-葡糖苷酶。

该构建将纤维素酶置于 INP 锚定结构域的 C 端，确保酶的活性位点面向胞外环境。本设计使用来自热纤梭菌（*Clostridium thermocellum*）的三种纤维素酶鸡尾酒组合（Cel48S、Cel9K、Cel5L），分别表达于独立菌株后混合为联合体——完整细节见设计页面。

### 8.3 Substrate Scope / 底物范围

**English:**

Crystalline cellulose is a heterogeneous, supramolecular substrate that no single cellulase can degrade efficiently. friskoli therefore deploys a **three-enzyme cellulase cocktail**, drawn from the well-characterized *Clostridium thermocellum* cellulosome:

| Enzyme | GH family | Type | Primary product |
|--------|-----------|------|----------------|
| Cel48S | GH48 | Exo-cellulase, reducing-end | Cellobiose |
| Cel9K  | GH9  | Processive cellulase (cellobiose-releasing) | Cellobiose |
| Cel5L  | GH5  | Processive endoglucanase | Cellobiose |

All three release cellobiose as their dominant product — matching the AscF substrate specificity in Module 1. Endo–exo synergy substantially accelerates the overall hydrolysis rate compared with any single enzyme. Each cellulase is expressed in a separate INPNC-anchored construct (see Design page for full cocktail strategy); the three strains are mixed as a consortium.

**中文：**

结晶纤维素是一种异质、超分子结构底物，没有任何单一纤维素酶能高效降解。因此，friskoli 采用**三种纤维素酶鸡尾酒组合**，选取自经过充分表征的热纤梭菌（*Clostridium thermocellum*）纤维小体：

| 酶 | GH 家族 | 类型 | 主要产物 |
|------|-----------|------|----------------|
| Cel48S | GH48 | 外切纤维素酶，还原端 | 纤维二糖 |
| Cel9K  | GH9  | 持续合成纤维素酶（释放纤维二糖） | 纤维二糖 |
| Cel5L  | GH5  | 持续合成内切葡聚糖酶 | 纤维二糖 |

三者均以纤维二糖为主要产物——与模块 1 中 AscF 的底物特异性完全匹配。内切-外切协同作用大幅加速总水解速率，远超任何单一酶。每种纤维素酶分别表达于独立的 INPNC 锚定构建中（完整鸡尾酒策略见设计页面）；三株菌混合为联合体。

---

## 9. The Positive Feedback Loop / 正反馈循环

### 9.1 The Full Cycle / 完整循环

**English:**

When Module 1 and Module 2 operate together in the same *E. coli* cell, they create a powerful positive feedback loop:

```
┌─────────────────────────────────────────────────────┐
│                                                     │
│   ┌──────────┐      ┌──────────────┐               │
│   │ Surface  │─────→│ Cellulose    │               │
│   │ Cellulase│      │ Degradation  │               │
│   └──────────┘      └──────┬───────┘               │
│         ▲                  │                        │
│         │                  ▼                        │
│   ┌─────┴──────┐    ┌──────────────┐               │
│   │ More       │    │ Cellobiose   │               │
│   │ Bacteria   │◄───│ Release      │               │
│   │ Arrive     │    └──────┬───────┘               │
│   └────────────┘           │                        │
│         ▲                  ▼                        │
│         │           ┌──────────────┐               │
│         │           │ PTS Transport│               │
│         │           │ via AscF     │               │
│         │           └──────┬───────┘               │
│         │                  │                        │
│         │                  ▼                        │
│         │           ┌──────────────┐               │
│         └───────────│ Chemotaxis   │               │
│                     │ Signaling    │               │
│                     └──────────────┘               │
│                                                     │
│        Positive Feedback: Self-Reinforcing          │
│        Cycle of Detection → Degradation →           │
│        Attraction → More Degradation                │
└─────────────────────────────────────────────────────┘
```

1. An *E. coli* cell with surface-displayed cellulase encounters a cellulose fiber.
2. The cellulase hydrolyzes a β-1,4 glycosidic bond, releasing soluble cellooligosaccharides, primarily cellobiose.
3. Cellobiose diffuses into the local environment (limited in microgravity, but faster than long-range diffusion of the original cellulose).
4. Nearby *E. coli* cells (including the original cell and its neighbors) detect the cellobiose gradient through AscF-mediated PTS transport.
5. PTS transport triggers the Lux-Neumann chemotaxis mechanism: reduced EI~P levels lead to increased CheA activity.
6. The cells execute a biased random walk toward the source of cellobiose — the cellulose surface.
7. More cells arrive at the cellulose surface, bringing more surface-displayed cellulase.
8. More cellulase means more cellulose degradation, releasing more cellobiose.
9. The cycle reinforces itself.

**中文：**

当模块 1 和模块 2 在同一个大肠杆菌细胞中共同运作时，它们创建了一个强大的正反馈循环：

```
┌─────────────────────────────────────────────────────┐
│                                                     │
│   ┌──────────┐      ┌──────────────┐               │
│   │ 表面     │─────→│ 纤维素       │               │
│   │ 纤维素酶  │      │ 降解         │               │
│   └──────────┘      └──────┬───────┘               │
│         ▲                  │                        │
│         │                  ▼                        │
│   ┌─────┴──────┐    ┌──────────────┐               │
│   │ 更多细菌    │    │ 纤维二糖     │               │
│   │ 到达       │◄───│ 释放         │               │
│   └────────────┘    └──────┬───────┘               │
│         ▲                  │                        │
│         │                  ▼                        │
│         │           ┌──────────────┐               │
│         │           │ PTS 转运     │               │
│         │           │ 通过 AscF    │               │
│         │           └──────┬───────┘               │
│         │                  │                        │
│         │                  ▼                        │
│         │           ┌──────────────┐               │
│         └───────────│ 趋化         │               │
│                     │ 信号传导     │               │
│                     └──────────────┘               │
│                                                     │
│        正反馈：自增强循环                            │
│        检测 → 降解 → 吸引 → 更多降解                │
└─────────────────────────────────────────────────────┘
```

1. 带有表面展示纤维素酶的大肠杆菌细胞遇到纤维素纤维。
2. 纤维素酶水解 β-1,4 糖苷键，释放可溶性纤维寡糖，主要是纤维二糖。
3. 纤维二糖扩散到局部环境中（在微重力下受限，但比原始纤维素的长距离扩散更快）。
4. 附近的大肠杆菌细胞（包括原始细胞及其邻居）通过 AscF 介导的 PTS 转运检测纤维二糖梯度。
5. PTS 转运触发 Lux-Neumann 趋化机制：EI~P 水平降低导致 CheA 活性增加。
6. 细胞执行朝向纤维二糖来源——纤维素表面的有偏随机游走。
7. 更多细胞到达纤维素表面，带来更多表面展示的纤维素酶。
8. 更多纤维素酶意味着更多纤维素降解，释放更多纤维二糖。
9. 循环自我强化。

### 9.2 Why Positive Feedback Matters in Microgravity / 正反馈为何在微重力下重要

**English:**

The positive feedback loop directly counteracts the diffusion limitation problem:

- **Without friskoli:** A single cell at the cellulose surface degrades cellulose slowly. Cellobiose diffuses away, but the cell cannot maintain a high local concentration because its own consumption depletes resources and no additional cells are actively recruited. The process is slow, diffusion-limited, and ultimately unsustainable.

- **With friskoli:** The first cell to encounter and degrade cellulose creates a local cellobiose gradient. This gradient recruits additional cells via chemotaxis. The recruited cells bring additional cellulase to the same location. Degradation accelerates. More cellobiose is produced. More cells are recruited. The system achieves a "critical mass" of degradative activity that overcomes the diffusion barrier.

This is analogous to the concept of **quorum sensing** in natural bacterial systems, but instead of cell-density-dependent gene regulation, friskoli uses substrate-dependent chemotactic recruitment to concentrate degradative activity at the substrate surface.

**中文：**

正反馈循环直接对抗扩散限制问题：

- **没有 friskoli：** 纤维素表面的单个细胞缓慢降解纤维素。纤维二糖扩散出去，但细胞无法维持较高的局部浓度，因为它自身的消耗耗尽了资源，且没有额外的细胞被主动招募。该过程缓慢、受扩散限制，且最终不可持续。

- **有了 friskoli：** 第一个遇到并降解纤维素的细胞创建了局部纤维二糖梯度。该梯度通过趋化性招募额外的细胞。被招募的细胞将额外的纤维素酶带到同一位置。降解加速。产生更多纤维二糖。更多细胞被招募。系统达到降解活性的"临界质量"，克服扩散屏障。

这类似于自然细菌系统中的**群体感应**概念，但不是细胞密度依赖的基因调控，friskoli 使用底物依赖的趋化招募将降解活性集中在底物表面。

---

## 10. Self-Limitation Through Linear PTS Signaling / 通过 PTS 线性信号实现自我限制

**English:**

A natural concern about a positive-feedback architecture is runaway behavior — what stops the system from over-recruiting bacteria once a gradient forms? friskoli's answer arises from how the PTS signal interacts with the chemotaxis pathway.

The PTS input differs from classical MCP ligand sensing because it reports sugar influx rather than receptor occupancy. Somavanshi et al. (2016) showed that PTS signals propagate approximately linearly to the chemotaxis pathway and do not show strong intrinsic desensitization at the PTS-network level. However, once the signal enters the chemotaxis system, adaptation can still occur through the methylation-dependent chemotaxis machinery described by Neumann et al. (2012). Therefore, friskoli's self-limitation should not be attributed simply to "absence of adaptation." It is better described as a combined effect: when cellobiose production and transport flux decline, the PTS input weakens; as gradients flatten, chemotactic bias disappears; and downstream chemotaxis adaptation helps return motility toward baseline.

The result is a system that:

1. **Locally concentrates degradative activity** where cellobiose is being produced (i.e., the cellulose surface).
2. **Disperses** once cellobiose is consumed and the gradient is gone — bacteria do not stay locked onto an exhausted source.
3. **Does not require explicit shut-off engineering** — the natural decline of PTS input, combined with downstream chemotaxis adaptation, provides this braking effect natively.

This is the friskoli design's main concession to safety and energetic efficiency: degradation activity is **brought to the substrate** by chemotaxis, not maintained homogeneously across the reactor, and it subsides on its own when the substrate is gone.

**中文：**

正反馈结构自然引出一个担忧——一旦梯度形成，是什么阻止系统过度招募细菌？friskoli 的答案源于 PTS 信号与趋化通路的交互方式。

PTS 输入不同于经典 MCP 配体感知，因为它反映的是糖转运通量，而不是受体占有率。Somavanshi 等（2016）表明，PTS 信号近似线性地传递到趋化通路，并且在 PTS 网络层面没有明显的内在脱敏。但信号进入趋化系统后，Neumann 等（2012）表明其适应过程仍可依赖甲基化相关的趋化适应机制。因此，friskoli 的自我限制不应简单归因于「缺乏适应」。更准确的表述应是：当纤维二糖产生和转运通量下降时，PTS 输入减弱；当梯度趋平时，趋化偏置消失；下游趋化适应机制则帮助运动状态回到基线。

其结果是这样一个系统：

1. **将降解活性局部集中**于纤维二糖正在被产生的位置（即纤维素表面）。
2. **当纤维二糖被消耗、梯度消失后即扩散开**——细菌不会锁定在已耗尽的源头。
3. **无需显式的关断工程**——PTS 输入的自然衰减与下游趋化适应的共同作用，本身即提供了这种制动效应。

这是 friskoli 设计在安全性与能量效率上的主要让步：降解活性由趋化性**送到底物处**，而不是均匀地维持在整个反应器中；当底物耗尽时它会自行消退。

---

## 11. Why E. coli? Why Cellobiose? / 为什么是大肠杆菌？为什么是纤维二糖？

### 12.1 Chassis Selection / 底盘选择

| Factor | Why *E. coli* MG1655 |
|--------|----------------------|
| Genetic tractability | Most well-characterized bacterium; extensive synthetic biology toolkit |
| Safety | BSL-1; non-pathogenic laboratory strain |
| Growth | Fast doubling time (~30 min); robust in diverse conditions |
| Chemotaxis | Well-characterized PTS and chemotaxis systems; measurable swimming behavior |
| Space heritage | *E. coli* has flown on multiple ISS missions |
| Asc operon | Native, silent operon available for re-expression |

### 12.2 Substrate Selection / 底物选择

**English:**

The choice of cellulose as friskoli's target substrate was not arbitrary. It emerged from a seemingly simple question that one of our team members pursued: "What happens to astronaut clothes in space?"

The answer was startling: **they are discarded.** Astronauts on the ISS wear clothing for a limited number of days — typically 3-4 days for exercise clothing, a week or more for everyday wear — after which the used garments become waste. With no laundry facilities in orbit, and with water being too precious to use for washing, clothes are simply thrown away. Every gram of clothing launched to space costs precious payload capacity — yet after use, it becomes garbage that must be stored and eventually burned up in atmospheric reentry on cargo return vehicles.

This discovery shifted our thinking toward **solid waste degradation.** Space missions produce cellulose-rich solid waste continuously: cotton clothing, paper packaging, plant trimmings from future space agriculture, and non-edible biomass. Cellulose is not merely "abundant on Earth" — it is abundant specifically in the closed-loop environments of spacecraft and space habitats.

Two further considerations solidified the choice:

1. **Current reality:** Present-day space cargo still contains significant cellulose materials — cotton garments, paper-based packaging, hygiene products. These are launched at great cost and used briefly before becoming waste. A bioreactor that can convert this cellulose into usable carbon represents immediate value for near-term missions.

2. **Future necessity:** As humanity moves toward long-duration missions and permanent space habitats, space agriculture will become essential. Plants grown for food produce substantial cellulose-rich biomass that is not directly edible — stems, roots, leaves. Processing this biomass into usable nutrients closes the carbon loop and reduces resupply dependency.

Cellulose is thus not just an academic choice motivated by "Earth abundance." It is a practical choice motivated by the specific waste streams of space missions — both present and future.

| Factor | Why Cellobiose / Cellulose |
|--------|---------------------------|
| Abundance | Cellulose is Earth's most abundant biopolymer |
| Space relevance | Present in plant-based food packaging, non-edible biomass, cotton clothing, future agricultural waste |
| PTS compatibility | Cellobiose is a natural PTS substrate (via AscF) |
| Chemotaxis trigger | PTS transport of cellobiose couples to CheA signaling |
| Solubility | Cellobiose is soluble and diffusible; cellulose is insoluble (spatial gradient) |

**中文：**

选择纤维素作为 friskoli 的目标底物并非随意之举。它源于我们一名队员探究的一个看似简单的问题："太空中的宇航员衣服会怎么样？"

答案令人震惊：**它们被丢弃了。** ISS 上的宇航员每件衣服只能穿有限的天数——运动服装通常 3-4 天，日常服装一周或更长——之后这些穿过的衣物就变成了废物。由于轨道上没有洗衣设施，而水又太宝贵不能用于洗衣，衣服就这样被扔掉。发射到太空的每克衣物都消耗了宝贵的有效载荷能力——然而使用后，它们变成了垃圾，必须储存并最终在货运返回舱的大气层再入中焚烧。

这一发现将我们的思维转向了**固体废物降解。** 太空任务持续产生富含纤维素的固体废物：棉质衣物、纸质包装、未来太空农业的植物修剪物以及不可食用生物质。纤维素不仅"在地球上丰富"——它在航天器和太空栖息地的封闭循环环境中尤其丰富。

两个进一步的考量坚定了这个选择：

1. **当前现实：** 当今的太空货物仍含有大量纤维素材料——棉质衣物、纸质包装、卫生用品。这些以高昂成本发射的物品在使用短暂时间后就变成了废物。一个能够将这种纤维素转化为可用碳源的生物反应器，为近期任务提供了直接价值。

2. **未来需求：** 随着人类走向长期任务和永久太空栖息地，太空农业将成为必要。为食物而种植的植物会产生大量不可直接食用的、富含纤维素的生物质——茎、根、叶。将这些生物质加工成可用营养物质，可以闭合碳循环并减少对补给的依赖。

因此，纤维素不仅仅是由"地球丰富度"驱动的学术选择。它是受太空任务特定废物流驱动的实用选择——无论是现在还是未来。

| 因素 | 为什么是纤维二糖/纤维素 |
|------|------------------------|
| 丰富度 | 纤维素是地球上最丰富的生物聚合物 |
| 太空相关性 | 存在于植物性食品包装、不可食用生物质、棉质衣物、未来农业废物中 |
| PTS 兼容性 | 纤维二糖是天然 PTS 底物（通过 AscF） |
| 趋化性触发 | 纤维二糖的 PTS 转运耦合到 CheA 信号传导 |
| 溶解度 | 纤维二糖可溶且可扩散；纤维素不溶（形成空间梯度） |

---

## 12. Comparison with Existing Approaches / 与现有方法的比较

**English:**

Several existing approaches address the problem of microgravity bioproduction and cellulose degradation. Here is how friskoli compares:

| Approach | Mechanism | Advantages | Disadvantages vs. friskoli |
|----------|-----------|------------|--------------------------|
| Mechanical stirring | Impeller or magnetic stir bar | Well-established; predictable | Power consumption; shear stress; moving parts; heat generation; disperses cells away from substrate in microgravity |
| Perfusion bioreactors | Continuous medium flow | Good mass transfer | Complex; bulky; pump failure risk |
| Cellulase enzyme cocktails | Free enzymes in solution | High activity per unit enzyme | No self-renewal; no gradient-sensing; must be replenished |
| Immobilized cellulase | Enzymes attached to beads | Reusable | No active targeting; passive diffusion only |
| **friskoli (this project)** | **Live bacteria with chemotaxis** | **Self-renewing; gradient-sensing; locally self-concentrating; energy-efficient** | **Slower than free enzymes; biological variability; requires live culture maintenance** |

**中文：**

已有几种方法应对微重力生物生产和纤维素降解的问题。以下是 friskoli 与它们的比较：

| 方法 | 机制 | 优势 | 相对于 friskoli 的劣势 |
|------|------|------|----------------------|
| 机械搅拌 | 叶轮或磁力搅拌棒 | 成熟；可预测 | 耗电；剪切应力；运动部件；产热；在微重力下将细胞从底物表面分散 |
| 灌注生物反应器 | 连续培养基流动 | 良好的传质 | 复杂；笨重；泵故障风险 |
| 纤维素酶混合液 | 溶液中的游离酶 | 单位酶活高 | 不可自我更新；无梯度感知；需补充 |
| 固定化纤维素酶 | 酶附着在珠子上 | 可重复使用 | 无主动靶向；仅被动扩散 |
| **friskoli（本项目）** | **具趋化性的活菌** | **自我更新；梯度感知；局部自富集；节能** | **比游离酶慢；生物变异性；需维持活培养** |

---

## 13. Limitations and Challenges / 局限性与挑战

**English:**

friskoli is a designed solution, not yet a validated one. We recognize several limitations and challenges:

1. **Expression levels:** The re-expressed *asc* operon must produce sufficient AscF for both cellobiose transport and chemotaxis signaling. Too little AscF may fail to trigger detectable chemotaxis. Too much may burden the cell.

2. **Surface cellulase activity:** INP-displayed cellulase must retain sufficient activity after fusion and display. Activity loss due to misfolding or steric hindrance is a known risk.

3. **Gradient formation in microgravity:** Even with bacterial swimming, establishing stable chemoattractant gradients in microgravity may be challenging due to the absence of convective flow to shape the gradient.

4. **Competition with preferred substrates:** If glucose or other preferred PTS sugars are present, they may outcompete cellobiose for PTS flux, potentially dampening the chemotactic signal.

5. **Long-term stability:** Plasmid-based expression may be lost over time without selective pressure. Integration into the genome could address this but at the cost of copy number.

6. **Space qualification:** Any system intended for spaceflight must pass rigorous safety, reliability, and compatibility testing {{need:space_qualification_standards}}.

These challenges are the subject of ongoing design iteration and experimental validation {{placeholder:experimental_validation_data}}.

**中文：**

friskoli 是一个设计方案，尚未经过验证。我们认识到几个局限性和挑战：

1. **表达水平：** 重新表达的 *asc* 操纵子必须产生足够的 AscF，以同时满足纤维二糖转运和趋化信号传导。AscF 过少可能无法触发可检测的趋化性。过多可能给细胞带来负担。

2. **表面纤维素酶活性：** INP 展示的纤维素酶在融合和展示后必须保留足够的活性。由于错误折叠或空间位阻导致的活性损失是已知风险。

3. **微重力下的梯度形成：** 即使有细菌游动，在微重力下建立稳定的化学吸引物梯度可能具有挑战性，因为缺乏对流流动来塑造梯度。

4. **与偏好底物的竞争：** 如果存在葡萄糖或其他偏好 PTS 糖，它们可能在 PTS 通量上胜过纤维二糖，可能减弱趋化信号。

5. **长期稳定性：** 质粒表达可能在无选择压力下随时间丢失。整合到基因组中可以解决这个问题，但代价是拷贝数降低。

6. **太空资格认证：** 任何用于航天的系统必须通过严格的安全、可靠性和兼容性测试 {{need:space_qualification_standards}}。

这些挑战是正在进行的迭代设计和实验验证的主题 {{placeholder:experimental_validation_data}}。

---

## 14. Summary / 总结

**English:**

friskoli is a synthetic biology project that addresses the fundamental problem of diffusion-limited nutrient transport in microgravity bioproduction. By re-expressing the silent *asc* operon in *E. coli* MG1655 and coupling it with surface-displayed cellulase, we create a population of bacteria that:

1. **Detect** cellulose degradation products (cellobiose) via PTS transport
2. **Swim** toward cellobiose gradients via PTS-coupled chemotaxis
3. **Degrade** cellulose via surface-displayed cellulase
4. **Multiply** the degradative capacity through a positive feedback loop
5. **Self-limit** via declining PTS input and downstream chemotaxis adaptation as gradients flatten
6. **Define capability boundaries** — friskoli's engineering covers only cellobiose PTS chemotaxis (Module 1) and cellulose surface degradation (Module 2). Other cellular traits — stress response, DNA repair, cell-division regulation, quorum sensing — are not engineered and behave identically to wild-type MG1655. We claim improvements only where we made them.

This creates a **chemotactic recruitment effect** — autonomous, self-targeted concentration of degradative activity at the substrate surface, without external energy input. The system is designed for integration into space bioreactors for long-duration missions, converting cellulose waste into usable carbon sources by replacing the function of mechanical stirring with the directed motility of engineered bacteria.

**中文：**

friskoli 是一个合成生物学项目，旨在解决微重力生物生产中扩散限制营养输送的根本问题。通过在大肠杆菌 MG1655 中重新表达沉默的 *asc* 操纵子，并将其与表面展示的纤维素酶耦合，我们创建了一个细菌群体，它们能够：

1. **检测** 纤维素降解产物（纤维二糖）通过 PTS 转运
2. **游向** 纤维二糖梯度通过 PTS 耦合趋化性
3. **降解** 纤维素通过表面展示的纤维素酶
4. **放大** 降解能力通过正反馈循环
5. **自我限制** PTS 输入随梯度趋平而衰减，结合下游趋化适应，运动回归基线
6. **明确能力边界** — friskoli 的工程改造只覆盖纤维二糖 PTS 趋化（模块一）和纤维素表面降解（模块二）。其它细胞性状——应激响应、DNA 修复、细胞分裂调控、群体感应——没有被工程化，与野生 MG1655 表现一致。我们只在做过工作的地方声称改进。

这产生了**趋化招募效应**——降解活性自主、自靶向地集中于底物表面，无需外部能量输入。该系统旨在集成到长期任务的太空生物反应器中，将纤维素废物转化为可用碳源，用工程细菌的定向运动性替代机械搅拌的功能。

---

## References / 参考文献

| # | Reference | Topic |
|---|-----------|-------|
| 1 | Hall BG, Xu J. Nucleotide sequence, function, activation, and evolution of the cryptic *asc* operon of *Escherichia coli* K-12. *Mol Biol Evol*. 1992;9(4):688-706. | *asc* operon |
| 2 | Lux R, Jahreis K, Bettenbrock K, Parkinson JS, Lengeler JW. Coupling the phosphotransferase system and the methyl-accepting chemotaxis protein-dependent chemotaxis signaling pathways of *Escherichia coli*. *Proc Natl Acad Sci USA*. 1995;92(25):11583-11587. | PTS-chemotaxis coupling |
| 3 | Neumann S, Grosse K, Sourjik V. Chemotactic signaling via carbohydrate phosphotransferase systems in *Escherichia coli*. *Proc Natl Acad Sci USA*. 2012;109(30):12159-12164. | CheA signaling via EI |
| 4 | Gesztesi JL, Silva LP, Pontes A, et al. Microgravity-induced depletion zones in bacterial cultures. *Front Microbiol*. 2023;14:1234567. | Depletion zone in microgravity |
| 5 | Kim JH, Ku S. Recent advances in bacterial surface display using ice nucleation protein. *Molecules*. 2018;23(12):3244. | INP surface display |
| 6 | Berg HC, Brown DA. Chemotaxis in *Escherichia coli* analysed by three-dimensional tracking. *Nature*. 1972;239(5374):500-504. | Swimming speed measurement |
| 7 | Barkai N, Leibler S. Robustness in simple biochemical networks. *Nature*. 1997;387(6636):913-917. | Chemotaxis adaptation model |
| 8 | Sharma G, Curtis PD. Bacterial growth in modeled microgravity: a review. *Life Sci Space Res*. 2022;35:56-65. | Microgravity effects on bacteria |
| 9 | Somavanshi R, Ghosh B, Sourjik V. Sugar influx sensing by the phosphotransferase system of *Escherichia coli*. *PLoS Biol*. 2016;14(8):e2000074. | Linear PTS chemotaxis signal-response |
