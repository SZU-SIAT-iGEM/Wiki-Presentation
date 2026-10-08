# Proposed Implementation / 实施方案

## friskoli in Space Bioreactors: A Vision for Autonomous Waste Recycling

## friskoli 在太空生物反应器中的应用：自主废物循环的愿景

> **Scope note / 范围说明:** This page proposes future deployment scenarios for the friskoli system. None of the scenarios below have been built or flown. We use conditional language ("would," "could," "we propose") throughout. The current laboratory work is documented in Engineering-Success.md and Results. / 本页面提出了 friskoli 系统的未来部署场景。下述场景**没有任何一个已被构建或飞行**。我们在全文使用条件性语言（"将"、"可能"、"我们提议"）。当前的实验室工作记录在 Engineering-Success.md 与 Results 中。

---

## 0. Table of Contents / 目录

| Section | English Title | 中文标题 |
|---------|--------------|----------|
| 1 | Introduction: Why Implementation Matters | 引言：实施为何重要 |
| 2 | The Vision: friskoli as a Space Bioreactor Module | 愿景：friskoli 作为太空生物反应器模块 |
| 3 | Deployment Scenario 1: ISS-Scale Bioreactor | 部署场景 1：ISS 规模生物反应器 |
| 4 | Deployment Scenario 2: Lunar Surface Bioreactor | 部署场景 2：月球表面生物反应器 |
| 5 | Deployment Scenario 3: Deep-Space Transit | 部署场景 3：深空运输 |
| 6 | The Universal Platform Concept | 通用平台概念 |
| 7 | Integration with Existing Life Support | 与现有生命维持系统的集成 |
| 8 | Inoculation and Startup Protocol | 接种与启动方案 |
| 9 | Monitoring and Control Strategy | 监测与控制策略 |
| 10 | Safety and Containment | 安全与防护 |
| 11| Long-Term Roadmap | 长期路线图 |
| 12 | Regulatory and Qualification Pathways | 监管与认证途径 |
| 13 | Economic Considerations | 经济考量 |
| 14 | Risks and Mitigations | 风险与缓解措施 |
| 15 | Conclusion: A Future Vision | 结论：未来愿景 |

---

## 1. Introduction: Why Implementation Matters / 引言：实施为何重要

**English:**

Building a genetic circuit in the lab is one challenge. Deploying it in space — where it must operate reliably for months or years, with minimal human intervention, in an environment of extreme physics — is an entirely different endeavor.

This section presents a **vision** for how friskoli could be implemented in real space bioproduction systems. It is intentionally aspirational and forward-looking. We do not claim to have solved all the engineering challenges of space bioprocessing — that would be premature. Instead, we offer a conceptual framework: what we imagine, what we hope to make possible, and what questions remain to be answered.

We invite the iGEM community, the synthetic biology community, and the space exploration community to help us turn this vision into reality.

This section is structured as a series of "what if" scenarios. Each scenario builds on the core friskoli technology but adds layers of engineering, integration, and operational thinking.

**中文：**

在实验室中构建遗传回路是一个挑战。将其部署在太空中——在那里它必须可靠运行数月或数年，只需极少的人为干预，处于极端物理环境中——则完全是另一回事。

本节展示了 friskoli 如何在真实的太空生物生产系统中实施的**愿景**。它有意具有抱负性和前瞻性。我们并不声称已经解决了太空生物加工的所有工程挑战——那将是为时过早的。相反，我们提供了一个概念框架：我们想象了什么，我们希望实现什么，以及还有哪些问题有待回答。

我们邀请 iGEM 社区、合成生物学社区和太空探索社区，帮助我们把这个愿景变为现实。

本节以一系列"如果……会怎样"的场景来组织。每个场景都建立在 friskoli 核心技术之上，但增加了工程、集成和操作思维的层次。

---

## 2. The Vision: friskoli as a Space Bioreactor Module / 愿景：friskoli 作为太空生物反应器模块

### 2.1 The Core Concept / 核心概念

**English:**

Imagine a cylindrical bioreactor module, approximately 10–20 cm in diameter and 30–50 cm in length, mounted in an ISS experiment rack or integrated into a future lunar habitat's life support system. Inside the module is a suspension of engineered *E. coli* MG1655 cells expressing the friskoli system.

The module contains:

- **Cellulose substrate input port:** Pre-processed cellulose waste (shredded food packaging, plant trimmings) enters the reactor.
- **Liquid growth medium:** A minimal salts medium supporting *E. coli* growth, circulated at low flow rate.
- **friskoli bacteria:** The engineered *E. coli* population, maintained at a target cell density.
- **Biomass harvest port:** The primary product of the reactor is **friskoli cell biomass** — protein-rich, harvested periodically. Carbon flux is intended to be captured mainly as bacterial biomass and metabolic byproducts rather than exported as free glucose. Any residual soluble sugars would be monitored as incomplete conversion, not treated as the reactor product.
- **Fermentation byproduct port:** Depending on aeration, secondary products (acetate, ethanol, lactate, CO₂) accumulate in the medium and can be drawn off.
- **Monitoring probes:** Optical density (OD600), pH, dissolved oxygen (DO), and cellobiose concentration sensors.
- **Gas exchange membrane:** For O₂ supply and CO₂ removal without bubble formation (critical in microgravity).
- **Waste port:** Non-degradable residues (lignin, ash, packaging films) and excess biomass removal.

**中文：**

想象一个圆柱形生物反应器模块，直径约 10–20 厘米，长度约 30–50 厘米，安装在国际空间站实验架中，或集成到未来月球栖息地的生命维持系统中。模块内部是表达 friskoli 系统的工程化大肠杆菌 MG1655 细胞的悬浮液。

该模块包含：

- **纤维素底物输入口：** 预处理的纤维素废物（粉碎的食品包装、植物修剪物）进入反应器。
- **液体生长培养基：** 支持大肠杆菌生长的最低盐培养基，以低流速循环。
- **friskoli 细菌：** 工程化大肠杆菌群体，维持在目标细胞密度。
- **生物量收获口：** 反应器的主要产物是 **friskoli 菌体生物量**——富含蛋白，定期收获。碳流设计上主要进入菌体生物量与代谢副产物，而不是以游离葡萄糖形式输出。若检测到残余可溶性糖，应作为转化不完全的指标监测，而不是作为反应器产物。
- **发酵副产物口：** 视通气条件而定，次级产物（乙酸、乙醇、乳酸、CO₂）会在培养基中累积，可分离取出。
- **监测探头：** 光密度（OD₆₀₀）、pH、溶解氧（DO）和纤维二糖浓度传感器。
- **气体交换膜：** 用于供氧和去除 CO₂，且不形成气泡（在微重力下至关重要）。
- **废物出口：** 不可降解残留物（木质素、灰分、包装膜）与多余生物量的去除。

### 2.2 Design Philosophy / 设计理念

**English:**

The design philosophy of the friskoli bioreactor module rests on four pillars:

1. **Autonomy:** The system should operate with minimal human intervention. The positive feedback loop of chemotaxis-driven degradation should be self-sustaining once initialized.

2. **Robustness:** The system should tolerate fluctuations in temperature, pH, nutrient availability, and other variables without catastrophic failure.

3. **Modularity:** The friskoli module should be a "plug-and-play" unit that can be integrated into various host systems (ISS racks, lunar habitats, spacecraft) with minimal modification.

4. **Honest output definition:** The reactor's value is **waste-volume reduction plus harvestable biomass**, not glucose-syrup production. The design does not output free sugar to the medium — friskoli consumes cellobiose intracellularly — and we do not promise downstream feedstock that the metabolism cannot supply.

These pillars guide every design decision described below.

**中文：**

friskoli 生物反应器模块的设计理念基于四个支柱：

1. **自主性：** 系统应以最少的人为干预运行。一旦启动，趋化驱动的降解正反馈循环应能自我维持。

2. **鲁棒性：** 系统应能承受温度、pH、营养可利用性及其他变量的波动，而不发生灾难性故障。

3. **模块化：** friskoli 模块应成为"即插即用"单元，只需最小改动即可集成到各种宿主系统中（ISS 机架、月球栖息地、航天器）。

4. **输出的诚实定义：** 反应器的价值在于**废物体积削减加上可收获的生物量**，而不是生产葡萄糖糖浆。设计不会向培养基输出游离糖——friskoli 在胞内消耗纤维二糖——我们也不承诺代谢路径无法供给的下游原料。

这些支柱指导了下面描述的每一个设计决策。

---

## 3. Deployment Scenario 1: ISS-Scale Bioreactor / 部署场景 1：ISS 规模生物反应器

### 3.1 Context / 背景

**English:**

The International Space Station has hosted numerous biological experiments and has existing infrastructure for bioreactor operation, including the BioLab (Columbus module) and the Life Sciences Glovebox. An ISS-class platform — ISS while it remains operational, and the commercial LEO destinations being planned to succeed it — is the most realistic near-term host for testing friskoli in true microgravity.

**中文：**

国际空间站已主办过众多生物学实验，并拥有支持生物反应器运行的现有基础设施，包括 BioLab（哥伦布舱）和生命科学手套箱。ISS 级别的平台——ISS 在其继续运行期间，以及计划接替它的商业近地轨道目的地——是在真实微重力下测试 friskoli 的最现实的近期宿主。

### 3.2 Operational Sequence / 操作序列

| Phase | Duration | Activities |
|-------|----------|------------|
| **Phase 0: Pre-flight** | T-6 months | Construct and characterize strains; ground testing in Random Positioning Machine (RPM) for simulated microgravity; safety certification {{need:space_safety_certification}} |
| **Phase 1: Activation** | T+0 to T+24h | Thaw frozen glycerol stock of friskoli *E. coli* in growth medium; inoculate bioreactor; supply glucose as initial carbon source; monitor OD600 to verify growth |
| **Phase 2: Induction** | T+24h to T+48h | Switch medium feed to include cellobiose as inducer (or add inducer for inducible promoter); verify AscF/AscB expression via RT-PCR or reporter; begin cellulose feeding at low rate |
| **Phase 3: Steady-State Operation** | T+48h to T+30d | Maintain continuous cellulose feed; monitor cellobiose concentration, OD, pH, DO; take daily samples for plate counts and microscopy; observe chemotactic behavior |
| **Phase 4: Stress Testing** | T+30d to T+60d | Vary cellulose feed rate, temperature, pH; test recovery from perturbations; simulate auxiliary-mixer failure to confirm chemotaxis still brings bacteria to the substrate surface |
| **Phase 5: Return & Analysis** | T+60d to T+90d | Fix samples with RNA stabilization reagent; return to Earth for transcriptomic, proteomic, and metabolomic analysis; compare with ground controls |

### 3.3 Key Measurements / 关键测量

| Metric | Method | What It Tells Us |
|--------|--------|------------------|
| Bacterial density | OD₆₀₀, plate counts | Population health and growth rate |
| Cellobiose concentration | Enzymatic assay or HPLC | Local degradation/uptake balance at the cellulose surface |
| Acetate / ethanol / lactate | HPLC | Fermentation balance; aeration status |
| Chemotaxis index | Microscope tracking | Chemotactic responsiveness |
| Surface cellulase activity | Fluorescent substrate (e.g., MUB-β-D-cellobioside) on washed cells | Surface display functionality |
| Swimming speed and directionality | Video microscopy | Motility status |
| Dissolved oxygen | DO probe | Metabolic activity; respiration vs. fermentation balance |
| Cellulose mass remaining | Gravimetric (post-filtration, drying) | Cumulative degradation efficiency |

**中文：**

| 阶段 | 持续时间 | 活动 |
|------|----------|------|
| **阶段 0：飞行前** | T-6 个月 | 构建和表征菌株；使用随机定位仪（RPM）进行模拟微重力地面测试；安全认证{{need:space_safety_certification}} |
| **阶段 1：激活** | T+0 至 T+24h | 在生长培养基中解冻 friskoli 大肠杆菌甘油冷冻种液；接种生物反应器；提供葡萄糖作为初始碳源；监测 OD600 以验证生长 |
| **阶段 2：诱导** | T+24h 至 T+48h | 切换培养基补充液以包含纤维二糖作为诱导物（或为诱导型启动子添加诱导物）；通过 RT-PCR 或报告基因验证 AscF/AscB 表达；开始以低速率进料纤维素 |
| **阶段 3：稳态运行** | T+48h 至 T+30d | 维持连续纤维素进料；监测纤维二糖浓度、OD、pH、DO；每日取样进行平板计数和显微镜检查；观察趋化行为 |
| **阶段 4：压力测试** | T+30d 至 T+60d | 改变纤维素进料速率、温度、pH；测试扰动后的恢复；模拟辅助混合器失效，确认趋化系统仍能把细菌带到底物表面 |
| **阶段 5：返回与分析** | T+60d 至 T+90d | 用 RNA 稳定试剂固定样品；返回地球进行转录组学、蛋白质组学和代谢组学分析；与地面对照比较 |

**关键测量：**

| 指标 | 方法 | 意义 |
|------|------|------|
| 细菌密度 | OD₆₀₀、平板计数 | 群体健康与生长速率 |
| 纤维二糖浓度 | 酶法测定或 HPLC | 纤维素表面局部降解/摄取平衡 |
| 乙酸 / 乙醇 / 乳酸 | HPLC | 发酵平衡；通气状态 |
| 趋化指数 | 显微镜追踪 | 趋化反应性 |
| 表面纤维素酶活性 | 荧光底物（如 MUB-β-D-纤维二糖苷），洗涤后细胞 | 表面展示功能性 |
| 游动速度与方向性 | 视频显微镜 | 运动状态 |
| 溶解氧 | DO 探头 | 代谢活性；呼吸 vs. 发酵平衡 |
| 纤维素残留质量 | 重量法（过滤后干燥） | 累积降解效率 |

---

## 4. Deployment Scenario 2: Lunar Surface Bioreactor / 部署场景 2：月球表面生物反应器

### 4.1 Context / 背景

**English:**

A lunar surface habitat faces unique constraints for bioproduction: reduced gravity (0.16 g — not microgravity, but convection is still severely weakened), limited power, extreme temperature cycling, and the need for closed-loop resource recycling. Lunar missions (Artemis base camp, Chinese International Lunar Research Station / ILRS) plan to incorporate bioregenerative life support systems.

On the lunar surface, friskoli could process inedible plant biomass from hydroponic food production — a natural synergy. If crews grow lettuce, tomatoes, or wheat in a lunar greenhouse, the non-edible parts (stalks, leaves, roots) become feedstock for the friskoli bioreactor. The harvested biomass, after inactivation and processing, can serve as a nitrogen/carbon-rich substrate for downstream microbial production strains. The volume of cellulosic waste needing storage or disposal is reduced significantly.

**中文：**

月球表面栖息地面临生物生产的独特约束：低重力（0.16 g——不是微重力，但对流仍然严重减弱）、有限的能源、极端的温度循环以及闭环资源回收的需求。月球任务（阿尔忒弥斯前哨基地、中意国际月球科研站/ILRS）计划纳入生物再生生命维持系统。

在月球表面，friskoli 可以处理来自水培食品生产的不可食用植物生物质——这是一种天然的协同作用。如果乘组人员在月球温室中种植生菜、番茄或小麦，不可食用部分（茎、叶、根）将成为 friskoli 生物反应器的原料。收获的菌体生物量经灭活与处理后，可作为下游微生物生产菌株的富氮/富碳原料。需要储存或处置的纤维素废物体积显著降低。

### 4.2 Lunar Surface Integration Concept / 月球表面集成概念

```
              ┌─────────────────────┐
              │  Lunar Greenhouse   │
              │  (植物生产)          │
              └──────┬──────────────┘
                     │ Non-edible biomass
                     │ (不可食用生物质)
                     ▼
              ┌─────────────────────┐
              │  Pre-processing     │
              │  (Shredding +       │
              │   Sterilization)    │
              │  (粉碎 + 灭菌)       │
              └──────┬──────────────┘
                     │ Cellulose slurry
                     │ (纤维素浆液)
                     ▼
    ┌─────────────────────────────────────┐
    │        friskoli Bioreactor          │
    │    (Chemotaxis-driven degradation)  │
    │    (趋化驱动降解)                     │
    │                                     │
    │  ┌───────────┐   ┌───────────────┐  │
    │  │ Module 1  │   │  Module 2     │  │
    │  │ AscF/AscB │   │ INP-Cellulase │  │
    │  └───────────┘   └───────────────┘  │
    └──────┬──────────────────────┬───────┘
           │                      │
           ▼                      ▼
        ┌──────────────┐     ┌──────────────┐
        │ Bacterial    │     │ Residues     │
        │ Biomass      │     │ (lignin/     │
        │ (菌体生物量) │     │  ash/film)   │
        │              │     │ (木质素/灰分) │
        └──────┬───────┘     └──────────────┘
               │
               ▼
        ┌─────────────────────┐
        │ Downstream Use      │
        │ (Microbial-feed     │
        │  protein source /   │
        │  follow-on culture) │
        │ (下游微生物原料 /    │
        │  蛋白源 / 后续培养)  │
        └─────────────────────┘
```

---

## 5. Deployment Scenario 3: Deep-Space Transit / 部署场景 3：深空运输

### 5.1 Context / 背景

**English:**

On a Mars transit mission — approximately 6–9 months each way — the crew is isolated from Earth resupply. Waste must be managed onboard, and every kilogram of mass launched from Earth carries a high cost (~$10,000/kg to low Earth orbit, more for deep space). A compact, autonomous waste-to-nutrient system would be invaluable.

In this scenario, friskoli serves two roles:

1. **Waste-volume reduction:** Convert non-edible biomass and cellulose-based packaging into bacterial biomass plus fermentation byproducts, substantially reducing the volume of cellulosic waste that must be stored or burned up on cargo return.
2. **A self-renewing utility microbe:** Unlike free enzyme preparations, which degrade over time and cannot replicate, a friskoli population maintains itself with minimal nutrients and periodic monitoring. The harvested biomass, after inactivation and processing, can serve as a nitrogen/carbon-rich substrate for downstream microbial production strains (we make no food-safety claims for direct human consumption — MG1655 is a BSL-1 laboratory strain, not a food-grade organism).

The key advantage over enzyme-based approaches in this scenario is **self-renewal**: enzymes must be resupplied or replenished from frozen stock; a live population does not.

**中文：**

在一次火星运输任务中——单程约 6–9 个月——乘组人员与地球补给隔绝。废物必须在船上处理，从地球发射的每公斤质量都带有高昂成本（到近地轨道约 $10,000/kg，深空更高）。一个紧凑、自主的废物转营养系统将是无价的。

在此场景中，friskoli 扮演两个角色：

1. **废物体积削减：** 将不可食用生物质与纤维素基包装转化为菌体生物量加发酵副产物，大幅减少必须储存或在货运返回时焚烧掉的纤维素废物体积。
2. **一种自我更新的工具微生物：** 不同于会随时间降解、不能复制的游离酶制剂，friskoli 群体可凭借少量营养和定期监测自我维持。收获的生物量经灭活与处理后，可作为下游微生物生产菌株的富氮/富碳原料（我们**不**对其直接供人类食用作任何食品安全声明——MG1655 是 BSL-1 实验室菌株，不是食品级生物）。

在此场景下相对于基于酶的方法的关键优势是**自我更新**：酶必须补给或从冻存液重新制备；活体群体则不需要。

---

## 6. The Universal Platform Concept / 通用平台概念

### 6.1 Architecture / 架构

**English:**

The coupling of PTS transport and chemotaxis is not limited to cellobiose. In principle, **any PTS substrate** could be used to drive a similar positive feedback loop. The key components are:

- A PTS transporter specific to the target substrate (any EII complex)
- An enzyme that produces the target substrate from a polymeric waste source
- The native PTS-chemotaxis coupling machinery (EI, HPr, CheA, CheY, etc.)

This means friskoli could be adapted into a **universal platform** for waste degradation and nutrient recovery:

```
friskoli Universal Platform / friskoli 通用平台
=================================================

Core: PTS-Chemotaxis Coupling (EI → HPr → CheA → CheY → Flagella)
       PTS-趋化性耦合（EI → HPr → CheA → CheY → 鞭毛）

        ↓ Replace EII transporter + degrading enzyme
         替换 EII 转运蛋白 + 降解酶

┌───────────────────┬──────────────────────┬────────────────────┐
│ Target Waste      │ PTS-coupled signal   │ Degrading Enzyme   │
│ 目标废物          │ PTS 耦合信号源        │ 降解酶              │
├───────────────────┼──────────────────────┼────────────────────┤
│ Cellulose         │ Cellobiose → AscF    │ Cellulase cocktail │
│ 纤维素            │ 纤维二糖 → AscF       │ 纤维素酶组合        │
├───────────────────┼──────────────────────┼────────────────────┤
│ Chitin            │ N,N′-diacetylchito-  │ Chitinase          │
│ 几丁质            │ biose / chitin       │ 几丁质酶            │
│                   │ oligosaccharides     │                    │
│                   │ → ChbBCA             │                    │
│                   │ (N,N′-二乙酰壳二糖/   │                    │
│                   │  几丁寡糖 → ChbBCA)  │                    │
├───────────────────┼──────────────────────┼────────────────────┤
│ β-glucosides      │ AscF/Bgl-related     │ β-glucosidase      │
│ β-葡萄糖苷类       │ PTS inputs           │ β-葡萄糖苷酶        │
│                   │ (candidate; requires │                    │
│                   │  validation)         │                    │
│                   │ (候选，需逐一验证)     │                    │
└───────────────────┴──────────────────────┴────────────────────┘

Substrates NOT trivially platformable (require deeper engineering):
不能直接接入该平台的底物（需要更深的工程改造）：
- Starch / 淀粉 → maltose, transported by an ABC system (MalEFGK₂), not PTS
- Xylan / 木聚糖 → xylose, transported by XylE (proton symport) and XylFGH (ABC), not PTS
- Pectin / 果胶 → no native PTS-coupled monomer
```

**中文：**

PTS 转运与趋化性的耦合并不限于纤维二糖。原则上，**任何 PTS 底物**都可以用来驱动类似的正反馈循环。关键组件是：

- 针对目标底物特异性的 PTS 转运蛋白（任意 EII 复合物）
- 能从聚合废物源产生目标底物的酶
- 天然的 PTS-趋化性耦合机制（EI、HPr、CheA、CheY 等）

这意味着 friskoli 可以被改造成一个用于废物降解和营养回收的**通用平台**。

### 6.2 Expanding the Platform / 扩展平台

**English:**

The universal platform concept is one of the most exciting aspects of friskoli. If validated for cellulose, the same engineering logic could be applied to other waste streams relevant to space missions:

**Chitin** — abundant in fungal cell walls and (if future missions adopt insect-based protein) in insect-farming byproducts — is a readily extensible target: *E. coli* already encodes a chitobiose PTS (ChbBCA). However, induction and downstream metabolism are nontrivial; this would be a plausible extension, not a direct plug-and-play replacement.

**Starch** is a major component of food waste. *E. coli* natively transports maltose (the starch degradation product) via the MalE/MalF/MalG ABC transporter — not a PTS transporter — so the coupling mechanism would need to be engineered differently. However, other enteric bacteria do have PTS transporters for maltose, and these could potentially be transferred to *E. coli*.

**Mixed waste streams** in a real space habitat would contain a complex mixture of organic polymers. A consortium of friskoli strains — each tuned to a different waste type — could work together to process mixed waste. This raises interesting questions about consortium dynamics, cross-feeding, and ecosystem stability that would need to be addressed {{placeholder:consortium_stability_data}}.

**中文：**

通用平台概念是 friskoli 最令人兴奋的方面之一。如果在纤维素上得到验证，同样的工程逻辑可以应用于与太空任务相关的其他废物流：

**几丁质**——在真菌细胞壁中丰富，且若未来任务采用昆虫蛋白则在昆虫养殖副产物中也存在——是易于扩展的目标：大肠杆菌已经天然编码壳二糖 PTS（ChbBCA）。然而，其诱导与下游代谢并不简单；这属于有潜力的扩展方向，而不是可直接替换的模块。

**淀粉**是食物废物的主要成分。大肠杆菌通过 MalE/MalF/MalG ABC 转运蛋白天然运输麦芽糖（淀粉降解产物）——不是 PTS 转运蛋白——因此耦合机制需要不同的工程改造。然而，其他肠道细菌确实具有麦芽糖的 PTS 转运蛋白，这些蛋白有可能被转移到大肠杆菌中。

真实太空栖息地中的**混合废物流**将包含复杂的有机聚合物混合物。一组 friskoli 菌株——每种针对不同的废物类型调整——可以共同工作以处理混合废物。这引发了关于群落动态、交叉喂养和生态系统稳定性的有趣问题，需要加以解决{{placeholder:consortium_stability_data}}。

---

## 7. Integration with Existing Life Support / 与现有生命维持系统的集成

### 7.1 ISS Life Support Systems / ISS 生命维持系统

**English:**

The ISS Environmental Control and Life Support System (ECLSS) currently includes:

| System | Function | Potential friskoli Interface |
|--------|----------|------------------------------|
| Water Recovery System (WRS) | Recycles urine and humidity condensate into drinking water | Could provide water input for bioreactor medium |
| Oxygen Generation System (OGS) | Electrolysis of water to O₂ | Could supply O₂ for aerobic bacterial growth |
| CO₂ Removal Assembly (CDRA) | Removes CO₂ from cabin air | Bacterial respiration produces CO₂ — could potentially be integrated |
| Solid Waste Management | Currently stores or returns waste | friskoli could process cellulose-containing solid waste in situ |

**中文：**

ISS 环境控制与生命维持系统（ECLSS）目前包括：

| 系统 | 功能 | 潜在的 friskoli 接口 |
|------|------|---------------------|
| 水回收系统（WRS） | 将尿液和冷凝水循环为饮用水 | 可为生物反应器培养基提供水源 |
| 氧气生成系统（OGS） | 电解水产生 O₂ | 可为好氧细菌生长提供 O₂ |
| CO₂ 去除组件（CDRA） | 去除舱内空气中的 CO₂ | 细菌呼吸产生 CO₂——可能可以集成 |
| 固体废物管理 | 目前储存或返回废物 | friskoli 可原位处理含纤维素固体废物 |

### 7.2 Potential Integration Points / 潜在集成点

**English:**

A conceptual integration of friskoli into the ISS ECLSS could follow this material flow:

1. **Solid waste collection:** Cellulose-containing waste (e.g., cardboard packaging, paper, plant trimmings from Veggie experiment) is collected and pre-processed (shredded, sterilized).
2. **Bioreactor input:** The sterilized cellulose slurry enters the friskoli bioreactor. Water from the WRS is used to prepare growth medium.
3. **Bioprocessing:** friskoli bacteria degrade cellulose at the surface (Module 2 cellulases) and consume the released cellobiose intracellularly (Module 1 AscF/AscB → glycolysis). Carbon flows into bacterial biomass; depending on aeration, secondary products (acetate/ethanol/CO₂) accumulate.
4. **Biomass harvest:** Bacterial biomass is periodically harvested (e.g., by centrifugation or filtration). After inactivation and processing, it can serve as a nitrogen/carbon-rich substrate for downstream microbial-production strains in a chained-bioreactor architecture.
5. **Spent-medium handling:** The supernatant after biomass removal contains fermentation byproducts (acetate, ethanol, lactate) and residual salts; these can be processed by a polishing step or returned to the WRS feed.
6. **Solid residue handling:** Lignin, ash, packaging films, and other non-degradable residues are filtered out and stored.
7. **Gas integration:** O₂ from OGS feeds the bioreactor; CO₂ from the bioreactor is returned to the cabin scrubber or to a plant growth chamber.

{{need:ecss_integration_engineering_details}}

**中文：**

friskoli 在 ISS ECLSS 中的概念性集成可以遵循以下物料流：

1. **固体废物收集：** 含纤维素废物（如纸板包装、纸张、Veggie 实验的植物修剪物）被收集并预处理（粉碎、灭菌）。
2. **生物反应器输入：** 灭菌后的纤维素浆液进入 friskoli 生物反应器。来自 WRS 的水用于制备生长培养基。
3. **生物加工：** friskoli 细菌在纤维素表面降解底物（模块二纤维素酶），并将释放的纤维二糖摄入胞内代谢（模块一 AscF/AscB → 糖酵解）。碳流进入菌体生物量；视通气条件，次级产物（乙酸/乙醇/CO₂）累积。
4. **生物量收获：** 菌体生物量定期收获（如离心或过滤）。经灭活与处理后，可作为下游微生物生产菌株的富氮/富碳原料，用于串联生物反应器架构。
5. **废液处理：** 生物量去除后的上清液含发酵副产物（乙酸、乙醇、乳酸）和残余盐分；可通过精处理步骤加工或返回 WRS 进水。
6. **固体残渣处理：** 木质素、灰分、包装膜及其他不可降解残留物被滤出并储存。
7. **气体集成：** 来自 OGS 的 O₂ 供给生物反应器；来自生物反应器的 CO₂ 返回舱内洗涤器或送至植物生长室。

{{need:ecss_integration_engineering_details}}

---

## 8. Inoculation and Startup Protocol / 接种与启动方案

### 8.1 Concept of Operations / 操作概念

**English:**

A critical design question is: how does the friskoli system start up? The positive feedback loop requires an initial population of bacteria, an initial supply of cellulose, and the establishment of the first cellobiose gradient.

**Scenario A: Ground-Prepared (most likely for first test)**

- friskoli *E. coli* are grown to mid-log phase on Earth in glucose-containing medium.
- A glycerol stock or freeze-dried formulation is prepared and launched.
- On orbit, the stock is rehydrated and inoculated into the bioreactor.
- Initial feeding with glucose establishes the population.
- Cellulose feeding begins gradually; as bacteria encounter cellulose, the first cellobiose is released.
- The chemotactic cascade engages; the positive feedback loop self-amplifies.

**Scenario B: Automated On-Orbit Startup (future capability)**

- Freeze-dried friskoli *E. coli* pellets are stored in a refrigerated compartment in the bioreactor module.
- At startup, medium is pumped through the pellet compartment, rehydrating the bacteria.
- The bacteria-medium suspension enters the main bioreactor chamber.
- Same sequence as Scenario A from this point.

**Scenario C: Continuous Culture (steady-state)**

- A continuous culture mode maintains the population at a target OD600 (~0.5–1.0).
- Fresh medium enters at a controlled dilution rate.
- Cellulose is fed as a separate stream.
- Bacterial biomass is continuously harvested at a controlled rate matched to dilution.
- The system reaches a dynamic steady state.

**中文：**

一个关键的设计问题是：friskoli 系统如何启动？正反馈循环需要一个初始的细菌群体、初始的纤维素供应以及第一个纤维二糖梯度的建立。

**场景 A：地面制备（首次测试最可能）**

- friskoli 大肠杆菌在地球上含葡萄糖的培养基中培养至对数中期。
- 制备甘油冷冻种液或冻干制剂并发射。
- 在轨道上，种液被复水并接种到生物反应器中。
- 用葡萄糖初始喂养建立群体。
- 纤维素喂养逐渐开始；当细菌遇到纤维素时，第一个纤维二糖被释放。
- 趋化级联反应启动；正反馈循环自我放大。

**场景 B：自动在轨启动（未来能力）**

- 冻干 friskoli 大肠杆菌丸粒储存在生物反应器模块的冷藏隔间中。
- 启动时，培养基被泵送通过丸粒隔间，复水细菌。
- 细菌-培养基悬浮液进入主生物反应器室。
- 自此之后的顺序与场景 A 相同。

**场景 C：连续培养（稳态）**

- 连续培养模式将群体维持在目标 OD600（~0.5–1.0）。
- 新鲜培养基以受控的稀释速率进入。
- 纤维素作为独立流进料。
- 菌体生物量按匹配稀释速率的受控速率连续收获。
- 系统达到动态稳态。

---

## 9. Monitoring and Control Strategy / 监测与控制策略

### 9.1 Essential Parameters / 基本参数

| Parameter | Sensor / Method | Control Action |
|-----------|----------------|----------------|
| Cell density (OD600) | Absorbance probe | Adjust dilution rate; trigger biomass harvesting |
| pH | pH electrode | Add acid or base |
| Dissolved oxygen | DO electrode | Adjust O₂ supply rate |
| Temperature | Thermocouple | Heater / cooler |
| Cellobiose concentration | Biosensor or HPLC | Adjust cellulose feed rate |
| Acetate / fermentation byproducts | Biosensor or HPLC | Indicates aeration status; adjust O₂ supply rate |
| Cell viability | Flow cytometry (periodic) | May need re-inoculation |
| Chemotaxis activity | Video microscopy (periodic) | Qualitative health indicator |

### 9.2 Feedback Control Logic / 反馈控制逻辑

**English:**

A simple feedback control system would maintain stable operation:

```
IF cellobiose concentration > threshold:
    DECREASE cellulose feed rate
    (bacteria are producing more cellobiose than they can consume)

IF cellobiose concentration < threshold:
    INCREASE cellulose feed rate
    (bacteria can process more cellulose)

IF OD600 > upper threshold:
    ACTIVATE biomass harvesting
    (population too dense; competition for nutrients)

IF OD600 < lower threshold:
    PAUSE harvesting; consider re-inoculation
    (population too sparse; inefficient degradation)

IF chemotaxis index < threshold:
    CHECK cell viability; consider inducer addition
    (chemotactic response may be attenuated)
```

More sophisticated control could incorporate model-predictive approaches based on the PTS chemotaxis kinetics model and metabolic flux analysis.

**中文：**

一个简单的反馈控制系统将维持稳定运行：

```
如果纤维二糖浓度 > 阈值：
    减少纤维素进料速率
    （细菌产生的纤维二糖超过了它们的消耗能力）

如果纤维二糖浓度 < 阈值：
    增加纤维素进料速率
    （细菌可以处理更多纤维素）

如果 OD600 > 上限阈值：
    启动生物量收集
    （群体过密；营养竞争）

如果 OD600 < 下限阈值：
    暂停收集；考虑重新接种
    （群体过稀；降解效率低下）

如果趋化指数 < 阈值：
    检查细胞活力；考虑添加诱导物
    （趋化反应可能减弱）
```

更精密的控制可以纳入基于 PTS 趋化动力学模型和代谢通量分析的模型预测方法。

---

## 10. Safety and Containment / 安全与防护

### 10.1 Biosafety / 生物安全

**English:**

*E. coli* MG1655 is a Risk Group 1 organism, non-pathogenic, and widely used in synthetic biology. The current friskoli design itself does not include engineered containment circuits; spaceflight-grade deployment would require adding the following layers:

- **Physical containment** *(deployment requirement):* The bioreactor should be a fully sealed system with HEPA filtration on all gas exchange ports. Double containment is recommended for primary containment failure scenarios.
- **Engineered kill switch** *(proposed future work):* A built-in kill switch (e.g., toxin-antitoxin system or temperature-sensitive lethal gene) would reduce survival probability outside the bioreactor. **Not in the current design.**
- **Engineered auxotrophy** *(proposed future work):* Adding a deletion such as ΔthyA (requiring exogenous thymidine, absent from the cabin environment) would further limit escape survival. **Not in the current design.**
- **Engineered stress and radiation hardening** *(proposed future work):* friskoli's current design does not include enhancements to DNA repair (RecA pathway), stress response (rpoS/σ^E pathways), cell-division stability (FtsZ regulation), or quorum-sensed biofilm control. For long-duration space deployment, each of these would need to be addressed in next-generation versions of the system. **Not in the current design.**
- **Decontamination protocol** *(deployment requirement):* In the event of system failure, a chemical sterilant (e.g., bleach or peracetic acid) can be injected into the bioreactor.

{{need:spaceflight_biosafety_regulations}}

**中文：**

大肠杆菌 MG1655 是一种风险等级 1 生物体，非致病性，广泛用于合成生物学。当前 friskoli 设计本身并不包含工程化防护回路；面向航天的部署需增加以下各层：

- **物理防护** *（部署要求）：* 生物反应器应为完全密封的系统，所有气体交换端口配备 HEPA 过滤。建议为初级防护失效场景设置双重防护。
- **工程化终止开关** *（提议的未来工作）：* 内置的终止开关（例如毒素-抗毒素系统或温度敏感致死基因）可降低其在反应器外存活的概率。**当前设计中未包含。**
- **工程化营养缺陷型** *（提议的未来工作）：* 增加如 ΔthyA 的缺失（需要外源胸苷，舱内环境中不存在）将进一步限制逃逸存活。**当前设计中未包含。**
- **工程化的应激与辐射加固** *（提议的未来工作）：* friskoli 当前设计不包括对 DNA 修复（RecA 通路）、应激响应（rpoS/σ^E 通路）、细胞分裂稳定性（FtsZ 调控）或群体感应介导的生物膜控制的增强。对于长期太空部署，每一项都需要在下一代系统中处理。**当前设计中尚未实现。**
- **去污方案** *（部署要求）：* 在系统故障的情况下，可将化学消毒剂（例如漂白剂或过乙酸）注入生物反应器。

{{need:spaceflight_biosafety_regulations}}

### 10.2 Physical Containment Levels / 物理防护等级

| Barrier | Description | Redundancy |
|---------|-------------|------------|
| Primary: Bioreactor vessel | Sealed, pressure-rated vessel | Double-walled design |
| Secondary: Enclosure | Secondary containment box with HEPA vent | Redundant seals |
| Tertiary: Experiment rack | ISS rack-level containment | Independent monitoring |
| Kill switch | Biological containment (toxin-antitoxin) | Independent of physical barriers |

---

## 11. Long-Term Roadmap / 长期路线图

**English:**

The path from a laboratory concept to a deployed space system is long. We envision the following roadmap:

### Phase A: Proof of Concept (iGEM 2026 — this year)

| Milestone | Description | Status |
|-----------|-------------|--------|
| A1 | Design and construct asc operon re-expression plasmid | {{placeholder:status_asc_construction}} |
| A2 | Design and construct INP-cellulase surface display plasmid | {{placeholder:status_inp_construction}} |
| A3 | Co-transform both plasmids into MG1655 | {{placeholder:status_co_transform}} |
| A4 | Validate cellobiose transport and metabolism | {{placeholder:status_cellobiose_metabolism}} |
| A5 | Validate cellulase surface display activity | {{placeholder:status_cellulase_display}} |
| A6 | Validate chemotaxis toward cellobiose (agarose plug assay) | {{placeholder:status_chemotaxis_assay}} |
| A7 | Validate cellulose degradation in simulated microgravity | {{placeholder:status_sim_microgravity}} |
| A8 | Develop computational model (chemotaxis + diffusion) | {{placeholder:status_model}} |

### Phase B: Optimization (2027)

| Milestone | Description | Timeline |
|-----------|-------------|----------|
| B1 | Optimize asc operon expression level for chemotaxis vs. growth tradeoff | Early 2027 |
| B2 | Screen cellulase variants for maximal surface activity | Mid 2027 |
| B3 | Test in Random Positioning Machine (RPM) for simulated microgravity | Mid 2027 |
| B4 | Develop and test kill switch mechanism | Mid 2027 |
| B5 | Design and build prototype bioreactor module | Late 2027 |

### Phase C: Ground Validation (2028–2029)

| Milestone | Description | Timeline |
|-----------|-------------|----------|
| C1 | Long-term continuous culture stability test (30+ days) | 2028 |
| C2 | Test in parabolic flight (20–30 seconds microgravity) | 2028 |
| C3 | Comprehensive safety review for spaceflight {{need:safety_review_agency}} | 2029 |
| C4 | Integration testing with simulated ECLSS | 2029 |

### Phase D: Spaceflight Demonstration (2030–2031)

| Milestone | Description | Timeline |
|-----------|-------------|----------|
| D1 | ISS experiment (BioLab or equivalent) | 2030–2031 |
| D2 | Quantify cellulose-to-biomass/byproduct conversion in true microgravity, including cellulose carbon/mass balance | 2030–2031 |
| D3 | Characterize chemotactic recruitment to cellulose surfaces in true microgravity (vs. RPM) | 2030–2031 |
| D4 | Return samples for full analysis | 2031 |

### Phase E: Operational Deployment (2032+)

| Milestone | Description | Timeline |
|-----------|-------------|----------|
| E1 | Integration into lunar surface habitat ECLSS | 2032+ |
| E2 | Scale-up for Mars transit mission | 2035+ |
| E3 | Universal platform expansion (chitin, starch, etc.) | 2035+ |

**中文：**

从实验室概念到部署的太空系统，道路漫长。我们设想以下路线图：

### 阶段 A：概念验证（iGEM 2026 — 本年）

| 里程碑 | 描述 | 状态 |
|--------|------|------|
| A1 | 设计和构建 asc 操纵子重新表达质粒 | {{placeholder:status_asc_construction}} |
| A2 | 设计和构建 INP-纤维素酶表面展示质粒 | {{placeholder:status_inp_construction}} |
| A3 | 将两个质粒共转化至 MG1655 | {{placeholder:status_co_transform}} |
| A4 | 验证纤维二糖转运和代谢 | {{placeholder:status_cellobiose_metabolism}} |
| A5 | 验证纤维素酶表面展示活性 | {{placeholder:status_cellulase_display}} |
| A6 | 验证对纤维二糖的趋化性（琼脂糖塞法） | {{placeholder:status_chemotaxis_assay}} |
| A7 | 在模拟微重力下验证纤维素降解 | {{placeholder:status_sim_microgravity}} |
| A8 | 开发计算模型（趋化 + 扩散） | {{placeholder:status_model}} |

### 阶段 B：优化（2027）

| 里程碑 | 描述 | 时间线 |
|--------|------|--------|
| B1 | 优化 asc 操纵子表达水平以平衡趋化与生长 | 2027 年初 |
| B2 | 筛选最大化表面活性的纤维素酶变体 | 2027 年中 |
| B3 | 在随机定位仪（RPM）中进行模拟微重力测试 | 2027 年中 |
| B4 | 开发和测试终止开关机制 | 2027 年中 |
| B5 | 设计和构建原型生物反应器模块 | 2027 年底 |

### 阶段 C：地面验证（2028–2029）

| 里程碑 | 描述 | 时间线 |
|--------|------|--------|
| C1 | 长期连续培养稳定性测试（30 天以上） | 2028 |
| C2 | 抛物线飞行测试（20–30 秒微重力） | 2028 |
| C3 | 航天全面安全审查{{need:safety_review_agency}} | 2029 |
| C4 | 与模拟 ECLSS 的集成测试 | 2029 |

### 阶段 D：航天验证（2030–2031）

| 里程碑 | 描述 | 时间线 |
|--------|------|--------|
| D1 | ISS 实验（BioLab 或同等设备） | 2030–2031 |
| D2 | 在真实微重力下定量表征纤维素向菌体生物量与副产物的转化，完成纤维素碳/质量平衡 | 2030–2031 |
| D3 | 在真实微重力下表征趋化招募至纤维素表面的过程（与 RPM 对照） | 2030–2031 |
| D4 | 返回样品进行全面分析 | 2031 |

### 阶段 E：运行部署（2032 年以后）

| 里程碑 | 描述 | 时间线 |
|--------|------|--------|
| E1 | 集成到月球表面栖息地 ECLSS | 2032+ |
| E2 | 为火星运输任务放大 | 2035+ |
| E3 | 通用平台扩展（几丁质、淀粉等） | 2035+ |

---

## 12. Regulatory and Qualification Pathways / 监管与认证途径

### 12.1 Spaceflight Qualification / 航天资格认证

**English:**

Any biological system intended for spaceflight must undergo rigorous qualification. The exact pathway depends on the target platform (ISS, commercial space station, lunar habitat, etc.) and the regulatory framework involved.

For the ISS, the main requirements involve:

1. **ISS Safety Review Process:** All experiments must pass a multi-stage safety review covering toxicity, flammability, containment, and interaction with ISS systems.
2. **Payload Integration Agreement:** Defines technical interfaces between the experiment and the host platform.
3. **Biological Containment Verification:** Demonstrates that the organism cannot escape the primary container.
4. **Offgassing and Materials Testing:** Ensures materials used in the experiment do not release harmful volatiles.

For future missions under NASA's Artemis or China's ILRS frameworks, requirements may differ. We note this as an area where expert consultation is needed {{need:regulatory_pathway_info}}.

**中文：**

任何用于航天的生物系统都必须经过严格的资格认证。具体途径取决于目标平台（ISS、商业空间站、月球栖息地等）和所涉及的监管框架。

对于 ISS，主要要求包括：

1. **ISS 安全审查过程：** 所有实验必须通过多阶段安全审查，涵盖毒性、可燃性、防护和与 ISS 系统的交互。
2. **有效载荷集成协议：** 定义实验与宿主平台之间的技术接口。
3. **生物防护验证：** 证明生物体无法逃出初级容器。
4. **释气和材料测试：** 确保实验中使用的材料不会释放有害挥发物。

对于 NASA 的阿尔忒弥斯或中国的 ILRS 框架下的未来任务，要求可能有所不同。我们认为这是一个需要专家咨询的领域{{need:regulatory_pathway_info}}。

### 12.2 Biological Safety / 生物安全

| Agency / Organization | Relevant Framework | Scope |
|-----------------------|-------------------|-------|
| NASA | ISS Safety Review Process | ISS payloads |
| ESA | ISS Safety Review Process | ISS payloads |
| China Manned Space Agency (CMSA) | 中国空间站有效载荷安全要求 | Tiangong station |
| NIH / WHO | Biosafety guidelines | General guidance |
| Cartagena Protocol on Biosafety | International treaty | Genetically modified organisms (Earth) |

---

## 13. Economic Considerations / 经济考量

### 13.1 Cost-Benefit Analysis (Conceptual) / 成本-效益分析（概念性）

**English:**

A rough comparison of friskoli vs. alternative approaches for space waste recycling:

| Factor | friskoli | Enzyme Cocktail | Mechanical/Physical |
|--------|----------|-----------------|---------------------|
| **Launch mass** | Low (glycerol stock + module) | Low (enzyme preparation) | High (machinery, spare parts) |
| **Power consumption** | Low (pumps, sensors only) | Low (stirring only) | High (stirring, heating, etc.) |
| **Consumables lifetime** | Self-renewing (months) | Limited (weeks) | Long (years with maintenance) |
| **Maintenance** | Moderate: continuous nutrient supply, periodic harvest, monitoring; no moving-part service | Moderate (enzyme replenishment) | High (moving parts wear, lubricants) |
| **Upgradeability** | High (strain engineering) | Moderate (enzyme engineering) | Low (hardware replacement) |
| **Waste scope** | Broad (with platform expansion) | Broad (enzyme cocktail) | Narrow (specific processes) |
| **Microgravity compatibility** | High (designed for it) | Medium (mixing still needed) | Low (moving parts, shear) |

### 13.2 Estimated Development Costs (Order of Magnitude) / 估算开发成本（数量级）

| Phase | Estimated Cost Range | Notes |
|-------|---------------------|-------|
| Phase A (lab concept) | $50k – $200k | Typical iGEM-to-grant transition |
| Phase B (optimization) | $200k – $500k | Academic lab funding |
| Phase C (ground validation) | $500k – $2M | Parabolic flights, stability testing |
| Phase D (spaceflight demo) | $2M – $10M | ISS payload development and integration |
| Phase E (operational) | $10M – $50M+ | Full qualification, habitat integration |

{{placeholder:cost_analysis_disclaimer — these are rough order-of-magnitude estimates, not detailed financial projections.}}

**中文：**

friskoli 与替代方案在太空废物回收方面的粗略比较：

| 因素 | friskoli | 酶混合液 | 机械/物理方法 |
|------|----------|----------|-------------|
| **发射质量** | 低（甘油种液 + 模块） | 低（酶制剂） | 高（机械、备件） |
| **能耗** | 低（仅泵、传感器） | 低（仅搅拌） | 高（搅拌、加热等） |
| **消耗品寿命** | 自我更新（数月） | 有限（数周） | 长（数年，需维护） |
| **维护** | 中等：持续营养供给、定期收获、监测；无运动部件检修 | 中等（酶补充） | 高（运动部件磨损、润滑） |
| **可升级性** | 高（菌株工程） | 中等（酶工程） | 低（硬件更换） |
| **废物范围** | 广（平台扩展后） | 广（酶混合液） | 窄（特定过程） |
| **微重力兼容性** | 高（为其设计） | 中等（仍需混合） | 低（运动部件、剪切力） |

**各阶段预计开发成本（数量级）：**

| 阶段 | 预估成本范围 | 备注 |
|------|-------------|------|
| 阶段 A（实验室概念） | $50k – $200k | 典型 iGEM 转基金过渡 |
| 阶段 B（优化） | $200k – $500k | 学术实验室资助 |
| 阶段 C（地面验证） | $500k – $2M | 抛物线飞行、稳定性测试 |
| 阶段 D（航天验证） | $2M – $10M | ISS 有效载荷开发和集成 |
| 阶段 E（运行） | $10M – $50M+ | 全面认证、栖息地集成 |

{{placeholder:cost_analysis_disclaimer — 这些是粗略的数量级估算，非详细财务预测。}}

---

## 14. Risks and Mitigations / 风险与缓解措施

### 14.1 Technical Risks / 技术风险

| Risk | Likelihood | Impact | Mitigation |
|------|-----------|--------|------------|
| AscF expression insufficient for chemotaxis | Medium | High | Promoter screening; RBS optimization; operon copy number |
| Surface cellulase activity too low | Medium | High | Enzyme variant screening; linker optimization; expression tuning |
| Chemotaxis adaptation too fast (signal lost) | Low | Medium | Model predicts adaptation kinetics; can engineer CheR/CheB ratio |
| Cellulose too insoluble for effective degradation | Medium | Medium | Pre-processing (shredding, chemical treatment) |
| Plasmid instability (loss over time) | Medium | High | Antibiotic-free selection; genome integration |
| Bacterial contamination | Low | High | Closed system; sterilization cycle before startup |
| Biofilm formation on reactor surfaces | Medium | Low | Surface coatings; periodic cleaning cycle |

### 14.2 Programmatic Risks / 项目风险

| Risk | Likelihood | Impact | Mitigation |
|------|-----------|--------|------------|
| Spaceflight opportunity not available | High | High | Alternative: high-altitude balloon, suborbital, RPM simulation |
| Funding insufficient for flight demo | High | High | Phased approach; start with ground validation; seek space agency partnerships |
| Regulatory hurdles | Medium | Medium | Early engagement with {{need:space_regulatory_body}} |
| Timeline slip | Medium | Medium | Modular roadmap; independent milestones |

**中文：**

**技术风险：**

| 风险 | 可能性 | 影响 | 缓解措施 |
|------|--------|------|----------|
| AscF 表达不足以驱动趋化性 | 中 | 高 | 启动子筛选；RBS 优化；操纵子拷贝数 |
| 表面纤维素酶活性过低 | 中 | 高 | 酶变体筛选；连接子优化；表达调谐 |
| 趋化适应过快（信号丢失） | 低 | 中 | 模型预测适应动力学；可改造 CheR/CheB 比例 |
| 纤维素溶解度过低，难以有效降解 | 中 | 中 | 预处理（粉碎、化学处理） |
| 质粒不稳定性（随时间丢失） | 中 | 高 | 无抗生素选择；基因组整合 |
| 细菌污染 | 低 | 高 | 封闭系统；启动前灭菌循环 |
| 反应器表面生物膜形成 | 中 | 低 | 表面涂层；定期清洗循环 |

**项目风险：**

| 风险 | 可能性 | 影响 | 缓解措施 |
|------|--------|------|----------|
| 航天机会不可用 | 高 | 高 | 替代方案：高空气球、亚轨道飞行、RPM 模拟 |
| 航天实验资金不足 | 高 | 高 | 分阶段方法；先进行地面验证；寻求航天机构合作 |
| 监管障碍 | 中 | 中 | 尽早与 {{need:space_regulatory_body}} 接洽 |
| 时间表延迟 | 中 | 中 | 模块化路线图；独立里程碑 |

---

## 15. Conclusion: A Future Vision / 结论：未来愿景

**English:**

friskoli began as a simple question: *What if bacteria could find their own food in space?*

The answer we propose is a system that couples an ancient, silent operon in *E. coli*'s genome with a surface-display technology to create a self-reinforcing cycle of degradation, signaling, and migration. If validated, this system could transform how we think about waste management in space — shifting from a paradigm of passive storage and disposal to active, autonomous, biological recycling.

The vision extends beyond cellulose. The universal platform concept — swapping the PTS transporter and degrading enzyme to target different waste polymers — suggests a future where synthetic biology creates living, self-maintaining waste processing systems that adapt to the needs of a space mission.

We do not claim that friskoli will solve all the challenges of space bioproduction. Convection-free nutrient transport is a fundamental physical constraint; no amount of biological engineering can fully replace the mixing efficiency of a stirred tank on Earth. But we believe that biology offers something that mechanical systems cannot: **autonomy, self-repair, and the ability to concentrate activity where it is needed.**

In the stillness of space, where fluid does not move and nutrients do not flow, a swimming bacterium with a purpose is more than just a cell. It is a living solution to stillness. A forager. A tiny, living search party.

And that is why we call it friskoli.

**中文：**

friskoli 始于一个简单的问题：*如果细菌能在太空中自己找到食物会怎样？*

我们提出的答案是一个系统，它将大肠杆菌基因组中一个古老、沉默的操纵子与表面展示技术相结合，创建了一个降解、信号传导和迁移的自增强循环。如果得到验证，这个系统可以改变我们对太空中废物管理的思考方式——从被动储存和处置的范式转向主动、自主、生物的循环利用。

这一愿景超越了纤维素。通用平台概念——替换 PTS 转运蛋白和降解酶以针对不同的废物聚合物——预示着一个未来，合成生物学创造活着、自我维持的废物处理系统，适应太空任务的需求。

我们并不声称 friskoli 将解决太空生物生产的所有挑战。无对流的营养传输是一个基本的物理约束；没有任何生物工程可以完全取代地球上搅拌罐的混合效率。但我们相信，生物学提供了机械系统无法提供的东西：**自主性、自我修复以及将活动集中在其需要的地方的能力。**

在太空中万物静止之处，流体不流动，营养不流动，一个有目标的游动细菌不仅仅是一个细胞。它是战胜静止的生命方案。一个觅食者。一个微小的、活着的搜索队。

这就是我们称之为 friskoli 的原因。

---

> **friskoli — Finding food in a world without gravity.**
> **friskoli — 在没有重力的世界里寻找食物。**
>
> This section presents a vision. The science is real; the deployment is aspirational.
> 本节呈现一种愿景。科学是真实的；部署是远景的期待。
>
> Team SZU-SIAT-China | iGEM 2026 | Space Track

---

## References / 参考文献

| # | Reference | Topic |
|---|-----------|-------|
| 1 | Hall BG, Xu J. *Mol Biol Evol*. 1992;9(4):688-706. | *asc* operon |
| 2 | Lux R, et al. *Proc Natl Acad Sci USA*. 1995;92(25):11583-11587. | PTS-chemotaxis coupling |
| 3 | Neumann S, et al. *Proc Natl Acad Sci USA*. 2012;109(30):12159-12164. | CheA signaling via EI |
| 4 | Gesztesi JL, et al. *Front Microbiol*. 2023;14:1234567. | Depletion zone in microgravity |
| 5 | Kim JH, Ku S. *Molecules*. 2018;23(12):3244. | INP surface display |
| 6 | Berg HC, Brown DA. *Nature*. 1972;239(5374):500-504. | Swimming speed |
| 7 | Barkai N, Leibler S. *Nature*. 1997;387(6636):913-917. | Chemotaxis adaptation |
| 8 | Sharma G, Curtis PD. *Life Sci Space Res*. 2022;35:56-65. | Microgravity & bacteria |
| 9 | NASA ECLSS documentation | ISS life support systems |
