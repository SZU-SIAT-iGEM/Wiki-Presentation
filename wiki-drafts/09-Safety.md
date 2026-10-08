# 安全性 / Safety

> **项目：** friskoli — SZU-SIAT-China, iGEM 2026  
> **赛道：** 太空赛道 (Space Track)  
> **最后更新：** 2026年4月

---

## 目录 / Table of Contents

1. [引言 / Introduction](#1-引言--introduction)
2. [底盘生物安全性 / Chassis Safety](#2-底盘生物安全性--chassis-safety)
3. [元件安全性 / Part Safety](#3-元件安全性--part-safety)
4. [实验室安全操作 / Laboratory Safety Practices](#4-实验室安全操作--laboratory-safety-practices)
5. [化学品安全 / Chemical Safety](#5-化学品安全--chemical-safety)
6. [生物安全等级论证 / Biosafety Level Justification](#6-生物安全等级论证--biosafety-level-justification)
7. [机构生物安全委员会审批 / Institutional Biosafety Committee Approval](#7-机构生物安全委员会审批--institutional-biosafety-committee-approval)
8. [环境安全性 / Environmental Safety](#8-环境安全性--environmental-safety)
9. [双重用途考量 / Dual-Use Considerations](#9-双重用途考量--dual-use-considerations)
10. [太空特定安全考量 / Space-Specific Safety Considerations](#10-太空特定安全考量--space-specific-safety-considerations)
11. [iGEM 安全框架合规 / iGEM Safety Framework Compliance](#11-igem-安全框架合规--igem-safety-framework-compliance)
12. [总结与结论 / Summary and Conclusions](#12-总结与结论--summary-and-conclusions)
13. [参考文献 / References](#13-参考文献--references)

---

## 1. 引言 / Introduction

**中文**

本文件描述了 iGEM 2026 项目 "friskoli"（SZU-SIAT-China）的全面安全性分析。我们的项目旨在利用表达在内膜上的 AscF 转运蛋白和 AscB 磷酸-β-葡萄糖苷酶对纤维二糖进行趋化响应，并通过冰核蛋白（INP）锚定系统在大肠杆菌外膜展示内切葡聚糖酶，以实现微重力条件下的纤维素降解。本安全性文件涵盖了底盘生物安全、遗传元件安全、实验室操作规范、化学品管理、环境安全评估以及太空应用的特殊考量。

我们坚信，合成生物学的安全性应贯穿于项目设计的始终，而非事后补充。因此，我们从设计阶段就选择了安全的底盘、内源性元件和标准的实验室实践，以确保人员、环境和社会安全。

**English**

This document presents a comprehensive safety analysis for the iGEM 2026 project "friskoli" (SZU-SIAT-China). Our project aims to engineer *Escherichia coli* MG1655 to respond chemotactically to cellobiose via the AscF transporter and AscB phospho-β-glucosidase expressed on the inner membrane, and to display endoglucanase on the outer membrane via an ice nucleation protein (INP) anchor system, for cellulose degradation under microgravity conditions. This safety document covers chassis biosafety, genetic part safety, laboratory practices, chemical management, environmental risk assessment, and space-specific considerations.

We firmly believe that biosafety in synthetic biology must be integrated throughout project design, not added as an afterthought. Therefore, from the earliest design stage, we selected safe chassis, endogenous genetic elements, and standard laboratory practices to ensure the safety of personnel, the environment, and society.

---

## 2. 底盘生物安全性 / Chassis Safety

### 2.1 底盘选择 / Chassis Selection

**中文**

我们选择 **大肠杆菌 K-12 MG1655** 作为项目底盘。MG1655 是国际公认的 **生物安全一级（BSL-1）** 菌株，具有悠久的实验室安全使用历史。

**English**

We selected **Escherichia coli K-12 MG1655** as our project chassis. MG1655 is internationally recognized as a **Biosafety Level 1 (BSL-1)** strain with an extensive history of safe laboratory use.

### 2.2 安全历史与特性 / Safety History and Characteristics

**中文**

大肠杆菌 K-12 谱系最初于 1922 年在斯坦福大学从一名白喉康复者的样本中分离，自 1940 年代起被用作实验模式生物，自 1970 年代起成为分子生物学的常用菌株。经过数十年的实验室传代，它已积累了对富营养培养基的适应，并丧失了与野外生存相关的若干性状。与野生型大肠杆菌相比，K-12 系具有以下关键安全特征：

| 特征 | 描述 | 参考文献 |
|--------|-------------|-----------|
| 非致病性 | 缺乏肠致病性大肠杆菌（EPEC）、肠出血性大肠杆菌（EHEC）等病原菌株的毒力因子 | Blattner et al. 1997 *Science* |
| 毒力基因缺失 | 基因组中不含志贺毒素（Stx）、 intimin（Eae）、溶血素等毒力基因 | Hayashi et al. 2006 *Mol Syst Biol* |
| 实验室适应 | 经过数千代实验室培养，已丧失在环境中的竞争生存能力 | Daegelen et al. 2009 *J Mol Biol* |
| 环境适应度降低 | 数十年的实验室适应已削弱了相对于野生大肠杆菌的 rpoS 依赖性应激响应和外膜 LPS 结构（O-抗原丢失），损害了在受控培养之外的生存能力 | Browning 等 2013 *PLoS Genet*；K-12 血清型丢失 / serotype loss in K-12 |

**English**

The *E. coli* K-12 lineage was originally isolated in 1922 from a convalescent diphtheria patient at Stanford University. It has been used as a laboratory model organism since the 1940s and as a molecular biology workhorse since the 1970s. After many decades of laboratory passage, it has accumulated adaptations to nutrient-rich culture media and lost characters relevant to environmental survival. Compared to wild-type *E. coli*, the K-12 lineage possesses the following critical safety characteristics:

| Characteristic | Description | Reference |
|----------------|-------------|-----------|
| Non-pathogenic | Lacks virulence factors found in pathogenic strains such as EPEC and EHEC | Blattner et al. 1997 *Science* |
| Virulence gene deletion | Genome contains no Shiga toxin (Stx), intimin (Eae), hemolysin, or other virulence genes | Hayashi et al. 2006 *Mol Syst Biol* |
| Laboratory-adapted | After thousands of generations in laboratory culture, has lost competitive viability in natural environments | Daegelen et al. 2009 *J Mol Biol* |
| Reduced environmental fitness | Decades of laboratory adaptation have reduced rpoS-dependent stress response and outer-membrane LPS structure (O-antigen loss) relative to wild *E. coli*, compromising survival outside controlled culture | Browning et al. 2013 *PLoS Genet*; serotype loss in K-12 |

### 2.3 生存能力评估 / Viability Assessment

**中文**

多项研究记录了实验室适应的大肠杆菌菌株在非实验室环境中存活能力降低。大肠杆菌 K-12 缺失完整的 O-抗原生物合成（rfb-50 IS5 插入；Liu & Reeves 1994），使其对胆盐和补体介导的杀伤更为敏感。加上多个 K-12 亚谱系中完整荚膜（colanic acid）的缺失和 rpoS 活性降低，这使 K-12 菌株在环境中的持续存活能力显著低于肠道分离的大肠杆菌。我们不引用关于自然水体中特定对数衰减数字，因为公开数据随菌株、温度、水质化学差异很大。其生长温度范围窄（最适 37°C，无法在 45°C 以上或 15°C 以下有效生长），对紫外线敏感。所有这些特性使其成为安全的实验室菌株选择。

**English**

Multiple studies have documented that laboratory-adapted *E. coli* strains have reduced survival in non-laboratory environments. *E. coli* K-12 lacks intact O-antigen biosynthesis (rfb-50 IS5 disruption; Liu & Reeves 1994), which sensitizes it to bile salts and complement-mediated killing. Combined with the absence of an intact colanic acid capsule and reduced rpoS activity in many K-12 sublineages, this gives K-12 strains substantially lower environmental persistence than enteric *E. coli* isolates. We do not cite specific log-decline figures for natural water bodies, as published values vary widely with strain, temperature, and water chemistry. Its growth temperature range is narrow (optimal at 37°C, unable to grow effectively above 45°C or below 15°C), and it is sensitive to UV radiation. All of these characteristics make it a safe laboratory strain choice.

---

## 3. 元件安全性 / Part Safety

### 3.1 所有元件均为内源性或标准 iGEM 元件 / All Parts Are Endogenous or Standard iGEM Parts

**中文**

本项目的安全特征因模块而异：**模块一（趋化与代谢）**重新激活内源性基因；**模块二（表面展示）**引入异源蛋白，但这些蛋白已充分表征且非致病性。具体而言：

- **ascF**：编码 PTS 纤维二糖特异性酶 II（EIIABC 融合蛋白），是大肠杆菌 MG1655 基因组中的内源性基因，位于基因座 **b2715**（NC_000913.3, ~2.84 Mb）。该基因在标准实验室条件下因 AscG 的主动抑制而处于转录沉默状态；我们通过用合成启动子替换天然调控区域来重新激活其表达。
- **ascB**：编码磷酸-β-葡萄糖苷酶 B，将 6-磷酸纤维二糖水解为 6-磷酸葡萄糖和葡萄糖。同样是 MG1655 的内源性基因，位于基因座 **b2716**，与 ascF 位于同一操纵子中并共表达。该操纵子的反向转录抑制因子 **ascG** 位于基因座 **b2714**。
- **INP-纤维素酶融合蛋白（模块二）**：我们使用来自植物相关细菌 *Pseudomonas syringae* 冰核蛋白的 N 端锚定结构域（INPNC）——该 INP 锚定结构不是人或动物致病因子，并已被广泛用于大肠杆菌外膜表面展示。我们展示的纤维素酶是来自 *Clostridium thermocellum* 纤维小体的三个已充分表征的成员：Cel48S (GH48)、Cel9K (GH9) 和 Cel5L (GH5)。*C. thermocellum* 是一种嗜热厌氧菌，不是人类或动物病原体，这些特定的纤维素酶也不是其来源生物的毒力因子。
- **启动子和终止子**：均来自 iGEM 标准元件库。具体而言，我们使用 Anderson 文库组成型启动子 J23116（BBa_J23116）作为模块一的基线表征启动子（Cycle 2 扫描更广的 J23100–J23119 系列），标准 RBS B0034（BBa_B0034）和终止子 B0015（BBa_B0015）。所有元件均有广泛的 iGEM 安全使用记录。

**我们没有引入任何毒素基因、毒力因子或致病性相关序列。**

**English**

The safety profile of our project differs by module: **Module 1 (chemotaxis & metabolism)** reactivates endogenous genes; **Module 2 (surface display)** introduces heterologous proteins that are well-characterized and non-pathogenic. Specifically:

- **ascF**: Encodes the PTS cellobiose-specific Enzyme II (EIIABC fused protein), an endogenous gene at locus **b2715** in the *E. coli* MG1655 genome (NC_000913.3, ~2.84 Mb). This gene is transcriptionally silent under standard laboratory conditions due to active AscG repression; we reactivate its expression by replacing the native regulatory region with a synthetic promoter.
- **ascB**: Encodes phospho-β-glucosidase B, which hydrolyzes cellobiose-6-phosphate into glucose-6-phosphate and glucose. It is an endogenous MG1655 gene at locus **b2716**, located in the same operon as ascF and co-expressed with it. The operon's divergently transcribed repressor **ascG** is at locus **b2714**.
- **INP-cellulase fusion (Module 2)**: We use the N-terminal anchor domain (INPNC) of the ice nucleation protein from the plant-associated bacterium *Pseudomonas syringae* — the INP anchor is not a human or animal virulence factor and has been widely used as an outer-membrane display motif in *E. coli*. The cellulases we display are three well-characterized members of the *Clostridium thermocellum* cellulosome: Cel48S (GH48), Cel9K (GH9), and Cel5L (GH5). *C. thermocellum* is a thermophilic anaerobe that is not a human or animal pathogen, and these specific cellulases are not virulence factors of their source organism.
- **Promoters and terminators**: All from the standard iGEM parts collection. Specifically, we use the Anderson library constitutive promoter J23116 (BBa_J23116) for Module 1 baseline characterization (with the broader J23100–J23119 family scanned in Cycle 2), the standard RBS B0034 (BBa_B0034), and terminator B0015 (BBa_B0015). All have an extensive iGEM safety record.

**We have introduced no toxin genes, virulence factors, or pathogenicity-associated sequences.**

### 3.2 asc 操纵子重新激活的生物学意义 / Biological Significance of *asc* Operon Reactivation

**中文**

值得重点强调的是，**模块一**（趋化-代谢臂）仅仅是**重新激活**了大肠杆菌 MG1655 基因组中已经存在的一个操纵子。模块二（纤维素酶表面展示）引入了异源蛋白，如 §3.1 所述，但这些蛋白本身是已充分表征的非致病性酶。两个模块都没有创造在自然界中不存在的新功能；我们是将已有功能整合到一个安全的底盘之中。

我们的工程改造引入了两个主要能力：
1. **对纤维二糖的趋化响应**：通过重新表达 AscF 转运蛋白，细胞能够感知纤维二糖梯度并进行趋化运动。
2. **表面展示纤维素酶活性**：通过 INP 锚定系统在细胞外膜表面展示内切葡聚糖酶，使细胞能够水解纤维素。

这两种功能（纤维素降解和糖趋化）在自然界中广泛存在于各种微生物中。我们仅仅是将它们整合在一个安全、非致病性的实验室底盘菌株中。

**English**

It is worth emphasizing that **Module 1** (the chemotaxis-metabolism arm) merely **reactivates** an operon already present in the *E. coli* MG1655 genome. Module 2 (cellulase surface display) introduces heterologous proteins, as described in §3.1, but those proteins are themselves well-characterized non-pathogenic enzymes. Neither module creates a function that does not already exist somewhere in nature; we are integrating existing functions into a safe chassis.

Our engineering introduces two main capabilities:
1. **Chemotactic response to cellobiose**: By re-expressing the AscF transporter, cells can sense cellobiose gradients and perform chemotactic movement.
2. **Surface-displayed cellulase activity**: By displaying endoglucanase on the outer membrane via the INP anchor system, cells can hydrolyze cellulose.

Both of these functions (cellulose degradation and sugar chemotaxis) are widely found across diverse microorganisms in nature. We are simply integrating them into a safe, non-pathogenic laboratory chassis strain.

---

## 4. 实验室安全操作 / Laboratory Safety Practices

### 4.1 生物安全一级（BSL-1）操作规范 / BSL-1 Operational Standards

**中文**

所有实验室工作均在 **BSL-1 标准**条件下进行。BSL-1 适用于与不致病菌株相关的非感染性工作，具体要求包括：

**English**

All laboratory work is conducted under **BSL-1 standard** conditions. BSL-1 is suitable for non-infectious work involving non-pathogenic strains. Specific requirements include:

### 4.2 标准操作程序 / Standard Operating Procedures (SOPs)

**中文**

| 项目 | 操作规范 |
|------|----------|
| 个人防护装备（PPE） | 实验服、丁腈手套、护目镜（处理液体培养物时强制佩戴） |
| 手部卫生 | 进出实验室必须洗手；脱手套后立即洗手 |
| 消毒 | 工作台面使用 70% 乙醇在实验前后消毒；溢洒立即用 1% 次氯酸钠处理 |
| 高压灭菌 | 所有液体培养物和固体废物在丢弃前须经 121°C、20 分钟高压灭菌 |
| 废物分类 | 锐器单独收集；液体废物灭活后按市政污水排放；固体废物按生物危害废物处理 |
| 无菌操作 | 所有微生物操作均在生物安全柜（BSC）中进行 |
| 记录 | 所有实验操作均需在实验记录本上详细记录 |

**English**

| Item | Operational Standard |
|------|----------------------|
| PPE | Lab coat, nitrile gloves, safety goggles (mandatory when handling liquid cultures) |
| Hand hygiene | Hand washing required upon entering and leaving the lab; immediate hand washing after glove removal |
| Disinfection | Work surfaces disinfected with 70% ethanol before and after use; spills immediately treated with 1% sodium hypochlorite |
| Autoclaving | All liquid cultures and solid waste autoclaved at 121°C for 20 minutes before disposal |
| Waste segregation | Sharps collected separately; liquid waste inactivated then discharged per municipal wastewater standards; solid waste disposed as biohazard waste |
| Aseptic technique | All microbiological manipulations performed in a biosafety cabinet (BSC) |
| Recordkeeping | All experimental operations documented in detail in laboratory notebooks |

### 4.3 废物处理流程 / Waste Disposal Protocol

**中文**

我们的废物处理流程遵循"灭活—分类—处理"的三步原则：

1. **灭活**：所有含有活菌的液体培养物在丢弃前加入 1% 次氯酸钠或 70% 乙醇处理至少 24 小时，或使用高压灭菌锅灭菌。
2. **分类**：将锐器、塑料耗材、玻璃器皿和液体废物按规定分类。
3. **处理**：灭菌后的废物按一般实验室废物处理；未经灭菌的废物不得离开实验室。

**English**

Our waste disposal protocol follows the three-step principle of "inactivate — segregate — dispose":

1. **Inactivation**: All liquid cultures containing viable bacteria are treated with 1% sodium hypochlorite or 70% ethanol for at least 24 hours, or sterilized using an autoclave, before disposal.
2. **Segregation**: Sharps, plastic consumables, glassware, and liquid waste are segregated according to regulations.
3. **Disposal**: Sterilized waste is handled as general laboratory waste; unsterilized waste must never leave the laboratory.

---

## 5. 化学品安全 / Chemical Safety

### 5.1 本项目中使用的化学品 / Chemicals Used in This Project

**中文**

本项目中使用的化学品均属于实验室常规化学品，但仍需安全处理：

**English**

All chemicals used in this project are routine laboratory chemicals, but safe handling is still required:

### 5.2 化学品安全表 / Chemical Safety Table

| 化学品 | CAS 编号 | 危害分类 | 安全处理 | 废物处置 |
|---------|----------|--------------|----------------|----------------|
| 溴化乙锭 (EtBr) | 1239-45-8 | 疑似致癌物（2B 类），诱变剂 | 佩戴丁腈手套操作；使用 EtBr 专用工作区；避免飞溅 | 经活性炭过滤柱处理后焚烧；或使用专用去污袋处理 |
| 氨苄青霉素 (Ampicillin) | 69-53-8 | 刺激性；潜在过敏原（青霉素类） | 佩戴手套操作；称量时佩戴口罩；在通风橱中配制溶液 | 高压灭菌后按危险废物处理 |
| 壮观霉素 (Spectinomycin) | 1695-77-8 | 氨基糖苷类抗生素；高剂量时有耳毒性 | 佩戴手套操作；在通风橱中配制溶液 | 高压灭菌后按危险废物处理 |
| PNPG (p-硝基苯基-β-D-葡萄糖苷) | 2492-87-7 | 刺激性 | 佩戴手套和护目镜；避免皮肤接触 | 小量可稀释后排放；大量应作为化学废物处理 |
| 次氯酸钠 (漂白剂) | 7681-52-9 | 腐蚀性；氧化剂 | 佩戴手套和护目镜；不可与酸混合 | 稀释后排放 |

**English**

| Chemical | CAS Number | Hazard Classification | Safe Handling | Waste Disposal |
|----------|------------|----------------------|---------------|----------------|
| Ethidium Bromide (EtBr) | 1239-45-8 | Suspected carcinogen (2B), mutagen | Wear nitrile gloves; use dedicated EtBr work area; avoid splashing | Through activated carbon filter and incineration; or use dedicated decontamination bags |
| Ampicillin | 69-53-8 | Irritant; potential allergen (penicillin class) | Wear gloves when handling; wear mask when weighing; prepare solutions in fume hood | Autoclave then dispose as hazardous waste |
| Spectinomycin | 1695-77-8 | Aminoglycoside; ototoxic at high doses | Wear gloves when handling; prepare solutions in fume hood | Autoclave then dispose as hazardous waste |
| PNPG (p-nitrophenyl-β-D-glucopyranoside) | 2492-87-7 | Irritant | Wear gloves and goggles; avoid skin contact | Dilute small quantities before disposal; large quantities as chemical waste |
| Sodium hypochlorite (bleach) | 7681-52-9 | Corrosive; oxidizer | Wear gloves and goggles; do not mix with acids | Dilute before disposal |

### 5.3 化学品储存与管理 / Chemical Storage and Management

**中文**

- 所有化学品均储存在指定的化学品柜中，按危害类别分开存放。
- 抗生素粉末储存在干燥、避光的专用容器中。
- 溴化乙锭溶液储存在避光容器中并明确标示。
- 所有化学品容器均标明名称、浓度、危害提示和接收日期。
- 化学品库存由实验室安全负责人定期检查和更新。

**English**

- All chemicals are stored in designated chemical cabinets, segregated by hazard category.
- Antibiotic powders are stored in dry, light-protected dedicated containers.
- Ethidium bromide solution is stored in light-protected containers with clear labeling.
- All chemical containers are labeled with name, concentration, hazard warnings, and receipt date.
- Chemical inventory is regularly inspected and updated by the laboratory safety officer.

---

## 6. 生物安全等级论证 / Biosafety Level Justification

### 6.1 BSL-1 适用性论证 / BSL-1 Applicability Justification

**中文**

根据世界卫生组织（WHO）《实验室生物安全手册》第四版和中国《病原微生物实验室生物安全管理条例》，BSL-1 适用于不会导致健康成人致病的微生物操作。我们选择 BSL-1 等级的理由如下：

**English**

According to the WHO *Laboratory Biosafety Manual* (4th edition) and the Chinese *Regulations on Biosafety Management of Pathogenic Microorganism Laboratories*, BSL-1 is applicable for operations involving microorganisms that do not cause disease in healthy adults. Our justification for BSL-1 classification is as follows:

### 6.2 论证表 / Justification Table

| 标准 / Criterion | MG1655 状态 / MG1655 Status | 满足 BSL-1？/ BSL-1 Compliant? |
|------------------|----------------------------|-------------------------------|
| 致病性 / Pathogenicity | 无致病性，无感染性 | 是 / Yes |
| 毒力因子 / Virulence factors | 基因组中无已知毒力因子 | 是 / Yes |
| 毒素产生 / Toxin production | 不产生任何已知毒素 | 是 / Yes |
| 感染剂量 / Infectious dose | 不适用 — 非病原体 | 是 / Yes |
| 宿主范围 / Host range | 大肠杆菌是哺乳动物肠道的共生菌；与野生共生分离株相比，MG1655 等实验室适应 K-12 菌株定殖肠道的能力降低（Smati 等 2015 *Microbiology*；菌毛减少、LPS 截短、O-抗原丢失） | 是 / Yes |
| 抗生素敏感性 / Antibiotic sensitivity | 对多种常用抗生素敏感 | 是 / Yes |
| 环境存活能力 / Environmental survival | 在环境中持续存活能力低（见 §2.3） | 是 / Yes |
| 基因改造的影响 / Impact of modification | 模块一重新激活内源性操纵子；模块二引入已充分表征的非致病性异源蛋白 | 是 / Yes |

### 6.3 关于抗生素抗性标记的说明 / Note on Antibiotic Resistance Markers

**中文**

我们的构建体含有氨苄青霉素抗性（AmpR，pBR322-ori 载体）和壮观霉素抗性（SpecR，pCDF-1b 质粒）选择标记。根据 iGEM 安全性指南和 WHO 建议，我们对此做出以下风险缓解说明：

- 氨苄青霉素在临床医学中广泛使用，不应被淡化。我们仅在 BSL-1 防护下将 AmpR 用作实验室选择标记；无任何抗生素抗性标记用于环境或部署目的。所有含质粒菌株均保持物理防护，并在处置前进行去污处理。
- 壮观霉素在 WHO AWaRe 分类中属"Access"级别，不在最高优先级类别中。
- 任何含有质粒的菌株均不允许在实验室外释放。
- 所有培养物和废液在丢弃前均经过严格的灭菌处理。
- 所有实验完成后，将评估是否需要移除抗性标记（此时尚未决定，最终决策将基于实验完成后的风险评估）。{{placeholder:antibiotic_marker_final_decision}}

**English**

Our constructs contain ampicillin resistance (AmpR, pBR322-origin vector) and spectinomycin resistance (SpecR, pCDF-1b plasmid) selection markers. In accordance with iGEM safety guidelines and WHO recommendations, we note the following risk mitigation measures:

- Ampicillin is widely used in clinical medicine and should not be minimized. We use AmpR only as a laboratory selection marker under BSL-1 containment; no antibiotic-resistance marker is intended for environmental or deployment use. All plasmid-bearing strains remain physically contained and are decontaminated before disposal.
- Spectinomycin is classified as "Access" in the WHO AWaRe categorization and is not on the highest WHO CIA priority tiers.
- No plasmid-containing strains are permitted for release outside the laboratory.
- All cultures and waste liquids undergo strict sterilization before disposal.
- Upon completion of all experiments, we will evaluate whether the resistance markers should be removed (decision pending; final determination will be based on post-experimental risk assessment). {{placeholder:antibiotic_marker_final_decision}}

---

## 7. 机构生物安全委员会审批 / Institutional Biosafety Committee Approval

**中文**

我们的实验方案和生物安全计划已提交深圳理工大学（拟）—中国科学院深圳先进技术研究院 机构生物安全委员会进行审批。在获得正式批准前，不进行任何活体实验。

{{placeholder:institutional_approval_details}}

审批状态将在此更新：{{placeholder:institutional_approval_status}}

**English**

Our experimental protocols and biosafety plan have been submitted to the Institutional Biosafety Committee (IBC) of Shenzhen University of Advanced Technology (proposed) — Shenzhen Institute of Advanced Technology, Chinese Academy of Sciences for review and approval. No live experiments will be conducted prior to formal approval.

{{placeholder:institutional_approval_details}}

Approval status will be updated here: {{placeholder:institutional_approval_status}}

---

## 8. 环境安全性 / Environmental Safety

### 8.1 环境影响评估 / Environmental Impact Assessment

**中文**

我们评估了工程菌株在意外释放情况下的环境影响。主要结论如下：

1. **低存活率**：MG1655 在自然环境中（土壤、淡水、海水）的存活时间极短，因为其已高度适应富含营养的实验室条件（见 §2.3）。
2. **无生态扰动能力**：该菌株不具备在微生物群落中占据生态位的能力。
3. **基因水平转移风险极低**：
   - 我们的质粒是不具接合性的：pBR322（及其衍生物，包括 pGEX-ascFB 骨架）缺少接合转移所需的 *tra* 基因座（Bolivar 等 1977; Sutcliffe 1979），pCDF-1b（CloDF13 复制起点）同样缺少接合机制。若存在共存的接合性辅助质粒（如 F 或 RP4），原则上可能发生动员，但 MG1655 中不存在此类质粒。即使发生动员，被转移的质粒仍需在受体菌中建立并维持，在没有抗生素选择的情况下这是不太可能的。
   - 内源性基因 *ascF* 和 *ascB* 已经存在于大肠杆菌基因组中。水平转移至另一株大肠杆菌不会引入新功能。转移至不同物种将赋予该生物纤维二糖 PTS 摄取能力，但 (a) 纤维二糖摄取系统在众多细菌中独立分布，(b) *asc* 基因本身不赋予致病性或纤维二糖丰富生态位之外的环境优势，(c) 此类转移需要我们的质粒所不具备的接合机制（见上）。
   - 纤维素酶活性本身（内切葡聚糖酶和纤维二糖水解酶）在环境细菌和真菌中广泛存在。INPNC-纤维素酶融合构建体是工程化的，在自然界中不存在，但该构建体并非自主的：它需要具有功能性 Sec/Tat 转位机制的大肠杆菌宿主才能定位至外膜，且其提供的纤维素酶功能不会赋予受体生物适应性优势，除非该生物本身也是纤维素降解者。
4. **生存劣势**：在没有抗生素选择压力的自然环境中，携带质粒的菌株面临代谢负担，相对于本地细菌具有生存劣势。

**English**

We have assessed the environmental impact of accidental release of our engineered strain. The principal conclusions are:

1. **Low survivability**: MG1655 survives only briefly in natural environments (soil, freshwater, seawater) because it is highly adapted to nutrient-rich laboratory conditions (see §2.3).
2. **No ecological disturbance capability**: This strain cannot occupy an ecological niche in microbial communities.
3. **Extremely low horizontal gene transfer risk**:
   - Our plasmids are non-conjugative: pBR322 (and its derivatives, including the pGEX-ascFB backbone) lacks the *tra* locus required for conjugative transfer (Bolivar et al. 1977; Sutcliffe 1979), and pCDF-1b (CloDF13 origin) likewise lacks conjugative machinery. Mobilization could in principle occur if a co-resident conjugative helper plasmid (e.g., F or RP4) were present, but this is not the case in MG1655. Even if mobilization did occur, the transferred plasmid would still need to establish and maintain itself in the recipient, which is unlikely without antibiotic selection.
   - The endogenous genes *ascF* and *ascB* are already present in the *E. coli* genome. Horizontal transfer to another *E. coli* would not introduce a novel function. Transfer to a different species would add cellobiose PTS uptake to that organism, but (a) cellobiose-uptake systems are independently distributed across many bacteria, (b) the *asc* genes themselves do not confer pathogenicity or environmental advantage outside cellobiose-rich niches, and (c) such transfer requires conjugative machinery absent from our plasmids (see above).
   - The cellulase activities themselves (endoglucanase and cellobiohydrolase) are widespread among environmental bacteria and fungi. The INPNC-cellulase fusion construct is engineered and not found in nature, but the construct is not autonomous: it requires an *E. coli* host with functional Sec/Tat translocation machinery to localize to the outer membrane, and the cellulase function it provides confers no fitness advantage to a recipient organism unless that organism is also a cellulose degrader.
4. **Fitness disadvantage**: In natural environments without antibiotic selection pressure, plasmid-bearing strains bear a metabolic burden and are at a fitness disadvantage relative to native bacteria.

### 8.2 风险缓解措施 / Risk Mitigation Measures

**中文**

- 所有液体培养物在高压灭菌前不得打开盖子。
- 转移菌株时使用二级容器（例如，培养管置于塑料烧杯中运输）。
- 所有标识（培养皿、培养管、冻存管）均清晰标明菌株名称、抗性标记和日期。
- 长期存放的菌种保存在 -80°C 具有锁扣机制的冻存盒中。

**English**

- No liquid culture lids are opened prior to autoclaving.
- Secondary containment is used when transferring strains (e.g., culture tubes transported in plastic beakers).
- All labels (plates, tubes, cryovials) clearly indicate the strain name, resistance markers, and date.
- Long-term strain stocks are stored at -80°C in lockable cryoboxes.

---

## 9. 双重用途考量 / Dual-Use Considerations

### 9.1 双重用途潜力评估 / Dual-Use Potential Assessment

**中文**

我们根据 iGEM 安全指南和国家生物安全法规对本项目的双重用途潜力进行了评估。

**结论：本项目不构成双重用途关切。** 理由如下：

1. **所有元件均为良性**：我们没有使用、改造或发现任何具有潜在武器化应用的基因或元件。
2. **底盘安全性**：MG1655 是非致病性菌株，不能用于制造生物武器制剂。
3. **教育目的**：本项目是典型的合成生物学教育项目，旨在教授细菌趋化性、表面展示技术和代谢工程的基本原理。
4. **透明度**：我们完全公开所有元件序列、实验方案和建模方法（通过 iGEM 维基和 GitHub 仓库）。

**English**

We have assessed the dual-use potential of our project in accordance with iGEM safety guidelines and national biosafety regulations.

**Conclusion: This project does not raise dual-use concerns.** The rationale is:

1. **All parts are benign**: We have not used, modified, or discovered any genes or elements with potential weapons applications.
2. **Chassis safety**: MG1655 is a non-pathogenic strain and cannot be used to create biological weapons.
3. **Educational purpose**: This project is a typical synthetic biology educational project aimed at teaching fundamental principles of bacterial chemotaxis, surface display technology, and metabolic engineering.
4. **Transparency**: We fully disclose all part sequences, experimental protocols, and modeling methods (via the iGEM wiki and GitHub repository).

### 9.2 负责任的研究实践 / Responsible Research Practices

**中文**

我们承诺：
- 遵守 iGEM 安全政策和当地法规。
- 不将本项目中的任何元件或菌株用于有害目的。
- 在维基上持续更新安全相关信息。
- 发现任何安全问题时立即向主管老师和 iGEM 安全委员会报告。

**English**

We commit to:
- Complying with iGEM safety policies and local regulations.
- Not using any parts or strains from this project for harmful purposes.
- Continuously updating safety-related information on the wiki.
- Immediately reporting any safety concerns to our PI and the iGEM Safety Committee.

---

## 10. 太空特定安全考量 / Space-Specific Safety Considerations

### 10.1 太空应用的生物安全 / Biosafety for Space Applications

**中文**

虽然本项目主要在地面实验室条件下进行概念验证，但我们设置此部分讨论未来在太空环境中部署的理论安全考量。本项目被 iGEM 太空赛道接受，因此明确考虑太空应用场景是必要和适当的。

**English**

Although this project primarily conducts proof-of-concept work under terrestrial laboratory conditions, we include this section to discuss theoretical safety considerations for future deployment in space environments. This project has been accepted in the iGEM Space Track, making it necessary and appropriate to explicitly consider space application scenarios.

### 10.2 太空部署的限制条件 / Constraints for Space Deployment

**中文**

如果本系统将来被考虑用于太空应用（例如，国际空间站或月球基地的生物反应器中的纤维素废物处理），以下安全措施将是必要的：

**English**

If this system were to be considered for future space applications (e.g., cellulose waste processing in bioreactors aboard the ISS or lunar bases), the following safety measures would be necessary:

### 10.3 太空安全措施表 / Space Safety Measures Table

| 考量方面 | 措施 | 优先级 |
|-----------|--------|----------|
| 物理遏制 | 多层密封反应器，使用 HEPA 排气过滤 | 强制 |
| 微重力处理 | 表面张力约束式容器（无自由液面）；扩散膜气体交换；被动气泡阱防止气溶胶形成 | 强制 |
| 灭菌程序 | 任务结束后的热化学原位灭菌 | 强制 |
| 遗传遏制 | 可诱导的自杀开关（例如，毒素-抗毒素系统） | 推荐 |
| 环境监测 | 实时空气和表面微生物监测 | 推荐 |
| 应急协议 | 泄漏时自动关闭、紫外线照射和化学消毒 | 强制 |
| 返回地球限制 | 无活菌返回地球；所有材料在返回前原位灭菌 | 强制 |

**English**

| Consideration | Measure | Priority |
|---------------|---------|----------|
| Physical containment | Multi-layer sealed reactor with HEPA exhaust filtration | Mandatory |
| Microgravity handling | Surface-tension-confined containment (no free liquid surfaces); diffusion-membrane gas exchange; passive bubble-trap to prevent aerosol formation | Mandatory |
| Sterilization protocol | Thermal-chemical in-situ sterilization at end of mission | Mandatory |
| Genetic containment | Inducible kill switch (e.g., toxin-antitoxin system) | Recommended |
| Environmental monitoring | Real-time air and surface microbial monitoring | Recommended |
| Emergency protocol | Automatic shutdown, UV irradiation, and chemical disinfection on leakage | Mandatory |
| Earth return restriction | No live organisms returned to Earth; all material sterilized in situ before return | Mandatory |

*注：上表所列措施中，**无一属于当前 friskoli 实验室设计的一部分**。这些是为假想的未来太空部署所需的安全功能。当前的实验室工作通过物理防护（BSL-1 密封反应器）进行，且不会将菌株部署至实验室之外。*

*Note: Of the measures listed above, **none are part of the current friskoli laboratory design**. They are the safety features that would be required for hypothetical future space deployment. The current laboratory work is contained physically (BSL-1 sealed reactor) and does not deploy the strain outside the laboratory.*

### 10.4 太空部署的进一步考量 / Further Considerations for Space Deployment

**中文**

{{placeholder:space_safety_details}}

未来太空部署需要的具体安全评估包括但不限于：
- 微重力对细菌生长和基因表达的影响评估
- 太空辐射对质粒稳定性和突变率的影响
- 与其他太空微生物组（如 ISS 上发现的环境微生物）的相互作用风险
- 封闭航天器环境中气溶胶传播风险评估
- 联邦和国际太空机构（NASA、ESA、CNSA）的生物安全要求的合规性

**English**

{{placeholder:space_safety_details}}

Specific safety assessments required for future space deployment include, but are not limited to:
- Assessment of microgravity effects on bacterial growth and gene expression
- Effects of space radiation on plasmid stability and mutation rates
- Interaction risks with other space microbiomes (e.g., environmental microorganisms found on the ISS)
- Aerosol transmission risk assessment in closed spacecraft environments
- Compliance with federal and international space agency (NASA, ESA, CNSA) biosafety requirements

---

## 11. iGEM 安全框架合规 / iGEM Safety Framework Compliance

### 11.1 与 iGEM 安全中心的对接 / Engagement with iGEM Safety Hub

**中文**

本项目遵循 iGEM 安全框架，已完成以下要求：

1. **安全检查表（Check-In）**：我们已提交安全检查表，确认我们的项目属于标准合成生物学范畴，未涉及高风险应用。
2. **安全表格**：我们已填写并提交所有要求的 iGEM 安全表格（Safety Form Part 1 & Part 2），详细描述了我们的底盘、元件、实验方案和风险评估。
3. **受管制项目评估**：我们的项目未涉及任何受管制类别（动物实验、人体研究、高危病原体、DNA 合成筛选、生物武器相关活动）。
4. **良好实践准则**：我们承诺遵守 iGEM 生物安全和生物安保良好实践准则。

**English**

This project follows the iGEM safety framework and has completed the following requirements:

1. **Safety Check-In**: We have submitted the Safety Check-In, confirming that our project falls within standard synthetic biology and does not involve high-risk applications.
2. **Safety Forms**: We have completed and submitted all required iGEM safety forms (Safety Form Part 1 & Part 2), providing detailed descriptions of our chassis, parts, experimental protocols, and risk assessment.
3. **Restricted Project Evaluation**: Our project does not involve any restricted categories (animal experiments, human research, high-risk pathogens, DNA synthesis screening, bioweapons-related activities).
4. **Good Practice Guidelines**: We commit to following the iGEM good biosafety and biosecurity practice guidelines.

### 11.2 所需安全表格清单 / Required Safety Forms Checklist

| 表格 / Form | 状态 / Status | 备注 / Notes |
|-------------|--------------|-------------|
| Safety Check-In | {{placeholder:safety_checkin_status}} | 已提交 / Submitted |
| Safety Form Part 1 (Basic) | {{placeholder:safety_form1_status}} | 底盘和元件描述 / Chassis & parts description |
| Safety Form Part 2 (Detailed) | {{placeholder:safety_form2_status}} | 详细风险评估 / Detailed risk assessment |
| Final Safety Review | {{placeholder:safety_final_review_status}} | 最终审核 / Final review |

### 11.3 安全政策链接 / Safety Policy Links

**中文**

- iGEM 安全中心: [https://responsibility.igem.org/safety](https://responsibility.igem.org/safety)
- iGEM 安全政策: [https://responsibility.igem.org/safety-policies](https://responsibility.igem.org/safety-policies)
- iGEM 安全检查过程: [https://responsibility.igem.org/safety-check-in](https://responsibility.igem.org/safety-check-in)
- iGEM 安全表格: [https://responsibility.igem.org/safety-forms](https://responsibility.igem.org/safety-forms)

**English**

- iGEM Safety Hub: [https://responsibility.igem.org/safety](https://responsibility.igem.org/safety)
- iGEM Safety Policies: [https://responsibility.igem.org/safety-policies](https://responsibility.igem.org/safety-policies)
- iGEM Safety Check-In: [https://responsibility.igem.org/safety-check-in](https://responsibility.igem.org/safety-check-in)
- iGEM Safety Forms: [https://responsibility.igem.org/safety-forms](https://responsibility.igem.org/safety-forms)

---

## 12. 总结与结论 / Summary and Conclusions

**中文**

本项目 "friskoli" 在设计之初即将安全作为核心考量。总结如下：

- **底盘**：大肠杆菌 BSL-1 菌株 MG1655，具有长期的实验室安全使用记录。
- **元件**：模块一重新激活内源性 *asc* 操纵子；模块二引入已充分表征的异源纤维素酶和 INPNC 锚定结构域，均非致病因子。
- **操作**：实验在 BSL-1 条件下进行，严格执行标准微生物操作规范。
- **化学品**：所有化学品均按照标准实验室安全规范处理。
- **环境影响**：工程菌株在自然环境中存活能力极低，无生态风险。
- **双重用途**：本项目纯粹为教育目的，不涉及双重用途问题。
- **太空安全**：未来太空部署需要额外遏制和灭菌措施（见第 10 节）。
- **合规**：完全遵循 iGEM 安全框架和中国生物安全法规。

**我们相信本项目对实验室人员、社区和环境是安全的。**

**English**

Safety has been a core consideration in the design of the "friskoli" project from the outset. Summary:

- **Chassis**: *E. coli* BSL-1 strain MG1655 with an extensive record of safe laboratory use.
- **Parts**: Module 1 reactivates the endogenous *asc* operon; Module 2 introduces well-characterized heterologous cellulases and the INPNC anchor domain, none of which are pathogenicity factors.
- **Practices**: Experiments conducted under BSL-1 conditions with strict adherence to standard microbiological practices.
- **Chemicals**: All chemicals handled according to standard laboratory safety protocols.
- **Environmental impact**: Engineered strain has extremely low viability in natural environments; no ecological risk.
- **Dual use**: This project is purely educational and raises no dual-use concerns.
- **Space safety**: Future space deployment requires additional containment and sterilization measures (see Section 10).
- **Compliance**: Full adherence to the iGEM safety framework and Chinese biosafety regulations.

**We believe this project is safe for laboratory personnel, the community, and the environment.**

---

## 13. 参考文献 / References

1. Blattner, F. R., et al. (1997). The complete genome sequence of *Escherichia coli* K-12. *Science*, 277(5331), 1453–1462.
2. Hayashi, K., et al. (2006). Highly accurate genome sequences of *Escherichia coli* K-12 strains MG1655 and W3110. *Molecular Systems Biology*, 2, 2006.0007.
3. Daegelen, P., et al. (2009). Tracing ancestors and relatives of *Escherichia coli* B, and the derivation of B strains. *Journal of Molecular Biology*, 394(4), 634–643.
4. Lenski, R. E., et al. (1991). Long-term experimental evolution in *Escherichia coli*. I. Adaptation and divergence during 2,000 generations. *The American Naturalist*, 138(6), 1315–1341.
5. WHO (2020). *Laboratory Biosafety Manual*, 4th edition. World Health Organization.
6. WHO (2023). *WHO AWaRe (Access, Watch, Reserve) classification of antibiotics*.
7. iGEM Safety Hub. [https://responsibility.igem.org/safety](https://responsibility.igem.org/safety)
8. 中华人民共和国国务院 (2018). 《病原微生物实验室生物安全管理条例》. 国务院令第 424 号.
9. National Academies of Sciences, Engineering, and Medicine (2018). *Biodefense in the Age of Synthetic Biology*. The National Academies Press.
10. Moe-Behrens, G. H. G., et al. (2013). Preparing synthetic biology for the world. *Frontiers in Microbiology*, 4, 5.
11. Liu, D., & Reeves, P. R. (1994). *Escherichia coli* K12 regains its O antigen. *Microbiology*, 140(1), 49–57. DOI: 10.1099/13500872-140-1-49.
12. Smati, M., et al. (2015). Quantitative analysis of commensal *Escherichia coli* populations reveals host-specific enterotypes at the intra-species level. *MicrobiologyOpen*, 4(4), 604–615.
13. Browning, D. F., et al. (2013). Laboratory adapted *Escherichia coli* K-12 becomes a pathogen of *Caenorhabditis elegans* upon restoration of O antigen biosynthesis. *Molecular Microbiology*, 87(5), 939–950.

---

> **本文档为 iGEM 2026 SZU-SIAT-China 团队项目 "friskoli" 的维基草稿。**  
> **内容真实性：本文件中的安全性声明基于公开的科学文献和标准实验室实践。占位符标记的条目将在获得相关数据或批准后更新。**  
> **版本：v1.0 (草稿)**
