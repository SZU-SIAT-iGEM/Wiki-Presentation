# Parts / 生物元件

> **Project:** friskoli
> **Team:** SZU-SIAT-China | **Track:** Space Track | **Year:** 2026

---

## Overview / 总览

This page documents all parts used in the friskoli project. The parts include two newly characterized endogenous genes from *Escherichia coli* MG1655 (ascF and ascB), three cellulase enzymes from *Clostridium thermocellum* (Cel48S, Cel9K, Cel5L), a truncated ice nucleation protein anchor (INPNC) with TorA signal peptide, a mixed rigid-flexible linker, and several standard Registry parts (promoter, RBS, terminator). Each part entry describes its biological function, role in the system, design rationale, and source organism.

本页面记录了 friskoli 项目中使用的所有元件。这些元件包括两个来自大肠杆菌 MG1655 的新表征内源基因（ascF 和 ascB）、三个来自热纤梭菌的纤维素酶（Cel48S、Cel9K、Cel5L）、一个带有 TorA 信号肽的截短冰核蛋白锚定序列（INPNC）、一个刚柔混合连接肽，以及多个标准库元件（启动子、RBS、终止子）。每个元件的条目描述了其生物学功能、在系统中的角色、设计原理和来源生物。

Module 1 (cellobiose transport and metabolism) is carried on a pBR322-origin vector (pGEX-type backbone) with ampicillin resistance at ~15–20 copies per cell. Module 2 (cellulose-to-cellobiose degradation) uses three separate expression cassettes on pCDF-1b (CloDF13 origin, spectinomycin resistance, ~20–30 copies per cell). The CloDF13 origin is compatible with pBR322 for stable co-transformation. The three cellulase strains are deployed as a consortium cocktail.

模块一（纤维二糖转运与代谢）搭载于 pBR322 复制起点的载体（pGEX 型骨架），氨苄青霉素抗性，约 15-20 拷贝/细胞。模块二（纤维素到纤维二糖的降解）使用三个独立表达盒，搭载于 pCDF-1b（CloDF13 复制起点，壮观霉素抗性，约 20-30 拷贝/细胞）。CloDF13 复制起点与 pBR322 兼容，可实现稳定的共转化。三种纤维素酶菌株以联合菌群（consortium cocktail）形式部署。

---

## Parts Table / 元件总表

### New Parts Submitted to the Registry / 提交至标准库的新元件

| Part Name / 元件名 | Registry ID / 标准库编号 | Type / 类型 | Length / 长度 | Source / 来源 |
|:---|:---|:---|:---:|:---|
| **ascF** | BBa_K5268001{{placeholder}} | Coding (PTS EII transporter) | ~1,440 bp | *E. coli* MG1655 genome |
| **ascB** | BBa_K5268002{{placeholder}} | Coding (phospho-β-glucosidase) | ~1,410 bp | *E. coli* MG1655 genome |
| **Cel48S** | BBa_K5268003{{placeholder}} | Coding (GH48 exo-cellulase) | ~2,100 bp | *C. thermocellum* (codon-optimized) |
| **Cel9K** | BBa_K5268004{{placeholder}} | Coding (GH9 exo-cellulase) | ~2,300 bp | *C. thermocellum* (codon-optimized) |
| **Cel5L** | BBa_K5268005{{placeholder}} | Coding (GH5 processive endoglucanase) | ~1,800 bp | *C. thermocellum* (codon-optimized) |
| **Linker (Mixed)** | BBa_K5268006{{placeholder}} | Linker (rigid + flexible) | ~60 bp | Synthetic |
| **ascFB Operon** | BBa_K5268007{{placeholder}} | Composite (operon) | ~3,700 bp | Synthetic assembly |
| **Cel48S Cassette** | BBa_K5268008{{placeholder}} | Composite (expression cassette) | ~3,100 bp | Synthetic assembly |
| **Cel9K Cassette** | BBa_K5268009{{placeholder}} | Composite (expression cassette) | ~3,300 bp | Synthetic assembly |
| **Cel5L Cassette** | BBa_K5268010{{placeholder}} | Composite (expression cassette) | ~2,800 bp | Synthetic assembly |

### Standard Registry Parts Used / 使用的标准库元件

| Part Name / 元件名 | Registry ID / 标准库编号 | Type / 类型 | Length / 长度 | Source / 来源 |
|:---|:---|:---|:---:|:---|
| **J23116** | BBa_J23116 | Promoter (constitutive) | 35 bp | Anderson collection |
| **B0034** | BBa_B0034 | RBS (medium strength) | 12 bp | Registry standard |
| **B0015** | BBa_B0015 | Terminator (double) | 127 bp | Registry standard |
| **INPNC** | BBa_K1933011 | Coding (surface display anchor) | ~600 bp | *P. syringae* (engineered) |

---

## Detailed Part Descriptions / 元件详细说明

---

### BBa_K5268001: ascF — PTS Cellobiose Transporter / PTS 纤维二糖转运蛋白

#### Basic Description / 基本描述

ascF encodes the cellobiose-specific Enzyme II complex (EII^Asc) of the bacterial phosphotransferase system (PTS) [1][2]. It is a fused EIIABC protein of approximately 480 amino acids (~52 kDa). The protein spans the inner membrane with 8–10 predicted transmembrane helices in the EIIC domain.

ascF 编码细菌磷酸转移酶系统（PTS）中纤维二糖特异性的酶 II 复合物（EII^Asc）[1][2]。它是一种融合的 EIIABC 蛋白，约 480 个氨基酸（~52 kDa）。该蛋白在 EIIC 结构域中有 8–10 个预测的跨膜螺旋，跨越内膜。

#### Function in the System / 在系统中的功能

AscF performs the critical dual role of transport and signaling in the friskoli system:

AscF 在 friskoli 系统中执行转运和信号传导的双重关键角色：

1. **Cellobiose transport:** AscF binds extracellular cellobiose via its EIIC domain and transports it across the inner membrane. Transport is coupled to phosphorylation — the EIIB domain transfers a phosphoryl group from the PTS chain to the 6'-hydroxyl of the non-reducing glucose moiety of cellobiose, producing cellobiose-6-phosphate.

   **纤维二糖转运：** AscF 通过其 EIIC 结构域结合胞外纤维二糖并将其转运穿过内膜。转运与磷酸化偶联——EIIB 结构域将磷酸基团从 PTS 链转移到纤维二糖非还原端葡萄糖部分的 6'-羟基，产生纤维二糖-6-磷酸。

2. **Chemotaxis signal generation:** Transport activity creates flux through the PTS phosphotransfer chain (PEP → EI → HPr → EIIA^Asc → EIIB^Asc → cellobiose). This flux dephosphorylates Enzyme I (EI). Dephosphorylated EI inhibits CheA autophosphorylation, reducing CheY-P levels and promoting smooth swimming (runs) toward higher cellobiose concentrations [3].

   **趋化信号生成：** 转运活性在 PTS 磷酸转移链中产生通量。该通量使酶 I（EI）去磷酸化。去磷酸化的 EI 抑制 CheA 自磷酸化，降低 CheY-P 水平并促进朝向较高纤维二糖浓度的平滑游动（奔跑）[3]。

#### Design Notes / 设计说明

- **Source:** Endogenous to *E. coli* MG1655. The asc operon is cryptic in wild-type cells under standard conditions but fully functional when expressed from a synthetic construct.
- **Expression constraint:** AscF is a transmembrane protein. Overexpression can cause membrane toxicity, inclusion body formation, and Sec translocon saturation [4]. Therefore, it is expressed from the weak J23116 promoter (relative strength 0.16) on the low-copy pBR322-origin vector (pGEX backbone, ~15–20 copies/cell).
- **Codon usage:** Native MG1655 sequence — no optimization needed as the gene is already adapted to the host.
- **Sequence notes:** The ORF includes all three domains (EIIA, EIIB, EIIC) in a single polypeptide. The EIIA domain is at the N-terminus, followed by EIIB and EIIC. The EIIC domain contains the substrate-binding pocket and transmembrane channel.

- **来源：** 大肠杆菌 MG1655 内源基因。asc 操纵子在标准条件下的野生型细胞中是隐性的，但从合成构建体表达时完全具有功能。
- **表达约束：** AscF 是一种跨膜蛋白。过表达可能导致膜毒性、包涵体形成和 Sec 转位子饱和 [4]。因此，它从弱启动子 J23116（相对强度 0.16）在低拷贝 pBR322 复制起点载体（pGEX 骨架，约 15–20 拷贝/细胞）上表达。
- **密码子使用：** 天然 MG1655 序列——无需优化，因为基因已适应宿主。
- **序列说明：** ORF 包含所有三个结构域（EIIA、EIIB、EIIC）在一条多肽链中。EIIA 结构域在 N 端，接着是 EIIB 和 EIIC。EIIC 结构域包含底物结合袋和跨膜通道。

#### Source / 来源

- **Organism:** *Escherichia coli* MG1655 (K-12 derivative)
- **Genomic location:** *ascF* (`b2715`) and *ascB* (`b2716`) form the functional unit; the divergently transcribed repressor *ascG* (`b2714`) lies adjacent. Region at ~2.84 Mb on NC_000913.3, 58.3 min on the standard linkage map.
- **Accession:** The asc operon sequence was first published by Hall and Xu (1992) [1]. NCBI Gene ID: 948407 (*ascF*).
- **Native regulation:** Repressed by AscG in the absence of cellobiose; subject to catabolite repression by CRP-cAMP.

- **生物：** 大肠杆菌 MG1655（K-12 衍生株）
- **基因组位置：** *ascF*（`b2715`）与 *ascB*（`b2716`）构成功能单元；反向转录的阻遏基因 *ascG*（`b2714`）位于相邻位置。区域位于 NC_000913.3 ~2.84 Mb，标准连锁图上 58.3 min 处。
- **序列登录号：** asc 操纵子序列由 Hall 和 Xu（1992）首次发表 [1]。NCBI 基因 ID: 948407（*ascF*）。
- **天然调控：** 在无纤维二糖时受 AscG 阻遏；受 CRP-cAMP 的分解代谢物阻遏调控。

---

### BBa_K5268002: ascB — Phospho-β-glucosidase / 磷酸-β-葡萄糖苷酶

#### Basic Description / 基本描述

ascB encodes a phospho-β-glucosidase enzyme (EC 3.2.1.86) of approximately 470 amino acids (~50 kDa) [1][2]. It belongs to glycosyl hydrolase family 1 (GH1), which shares a conserved (β/α)₈ barrel fold and a glutamic acid catalytic dyad mechanism. The enzyme specifically cleaves the β-1,4 glycosidic bond in cellobiose-6-phosphate, but NOT in unphosphorylated cellobiose.

ascB 编码一种磷酸-β-葡萄糖苷酶（EC 3.2.1.86），约 470 个氨基酸（~50 kDa）[1][2]。它属于糖苷水解酶家族 1（GH1），具有保守的（β/α）₈ 桶状折叠和谷氨酸催化双联机制。该酶特异性切割纤维二糖-6-磷酸中的 β-1,4 糖苷键，但不切割非磷酸化的纤维二糖。

#### Function in the System / 在系统中的功能

AscB completes the cellobiose metabolic pathway in Module 1:

AscB 完成模块一中的纤维二糖代谢途径：

```
Cellobiose-6-P + H₂O  →  Glucose-6-P + Glucose
```

The glucose-6-phosphate (G6P) produced enters the Embden-Meyerhof-Parnas (glycolytic) pathway, providing energy (ATP) and biosynthetic precursors. This serves two functions:

产生的 6-磷酸葡萄糖进入糖酵解（EMP）途径，提供能量（ATP）和生物合成前体。这服务于两个功能：

1. **Growth support:** Cellobiose becomes a usable carbon source, creating the growth amplification loop.
2. **Metabolic coupling:** The metabolic flux through glycolysis generates the byproducts that feed back onto PTS regulation, contributing to the self-limiting behavior of the system.

1. **生长支持：** 纤维二糖成为可用碳源，创建生长放大循环。
2. **代谢耦合：** 通过糖酵解的代谢通量产生了反馈到 PTS 调节的副产物，促成系统的自限行为。

#### Design Notes / 设计说明

- **Source:** Endogenous to *E. coli* MG1655, from the same asc operon as ascF.
- **Expression:** ascB is expressed from the same bicistronic operon as ascF, under the control of J23116. Each gene has its own B0034 RBS.
- **Substrate specificity:** The requirement for 6-phosphorylated substrate ensures that only AscF-transported cellobiose enters this metabolic channel, preventing nonspecific sugar metabolism.
- **Codon usage:** Native MG1655 sequence.
- **Localization:** Cytoplasmic. AscB does not contain any secretion signals — it acts on cellobiose-6-P after it is released into the cytoplasm by AscF.

- **来源：** 大肠杆菌 MG1655 内源基因，与 ascF 同属 asc 操纵子。
- **表达：** ascB 与 ascF 在同一个双顺反子操纵子中表达，受 J23116 控制。每个基因拥有自己的 B0034 RBS。
- **底物特异性：** 对 6-磷酸化底物的要求确保了只有 AscF 转运的纤维二糖进入此代谢通道，防止非特异性糖代谢。
- **密码子使用：** 天然 MG1655 序列。
- **定位：** 细胞质。AscB 不含任何分泌信号——它作用于 AscF 释放到细胞质中的纤维二糖-6-磷酸。

#### Source / 来源

- **Organism:** *Escherichia coli* MG1655
- **Genomic location:** Same asc operon as ascF
- **NCBI Gene ID:** 948406 (*ascB*)
- **Crystal structure:** Not available for AscB; however, homologous GH1 enzymes (e.g., BglA from *Bacillus* spp.) are well-characterized structurally.

- **生物：** 大肠杆菌 MG1655
- **基因组位置：** 与 ascF 相同的 asc 操纵子
- **NCBI 基因 ID:** 948406（*ascB*）
- **晶体结构：** AscB 尚无晶体结构；但同源的 GH1 酶（如来自芽孢杆菌属的 BglA）在结构上已有充分表征。

---

### BBa_K1933011: INPNC — Truncated Ice Nucleation Protein Anchor / 截短冰核蛋白锚定序列

#### Basic Description / 基本描述

BBa_K1933011 encodes a truncated form of the ice nucleation protein (INP) from *Pseudomonas syringae*, retaining only the N-terminal and C-terminal domains (INPNC) while removing the central repetitive domain [5][11][12]. The construct is N-terminally fused to the TorA signal peptide (Tat pathway) for Sec-independent translocation across the inner membrane, and carries a C-terminal polyhistidine (His) tag for detection and purification. The INPNC anchor directs passenger proteins to the outer membrane of *E. coli* and stably embeds them with the passenger domain exposed to the extracellular environment.

BBa_K1933011 编码来自丁香假单胞菌（*Pseudomonas syringae*）冰核蛋白的截短形式，仅保留 N 端和 C 端结构域（INPNC），去除中央重复结构域 [5][11][12]。该构建体在 N 端融合了 TorA 信号肽（Tat 途径），以实现不依赖 Sec 的内膜转位，并在 C 端携带多聚组氨酸（His）标签用于检测和纯化。INPNC 锚定序列将 passenger 蛋白引导至大肠杆菌外膜并稳定锚定，使 passenger 结构域暴露于胞外环境。

```
[TorA signal peptide] — [INP N-domain] — [INP C-domain] — [His-tag]
```

#### Function in the System / 在系统中的功能

INPNC is the surface display anchor for all three cellulase enzymes in Module 2. Each cellulase (Cel48S, Cel9K, Cel5L) is fused to the C-terminus of INPNC via a mixed linker. The INPNC anchor:

INPNC 是模块二中三种纤维素酶的表面展示锚定序列。每种纤维素酶（Cel48S、Cel9K、Cel5L）通过混合连接肽融合到 INPNC 的 C 端。INPNC 锚定序列的功能：

1. **Tat-dependent translocation:** The TorA signal peptide directs the fusion protein to the Tat (Twin-arginine translocation) pathway, allowing the fully folded protein to cross the inner membrane — critical for cellulases that require proper folding before membrane insertion.
2. **Outer membrane anchoring:** The N-domain of INP contains membrane-anchoring sequences that insert into the outer membrane. The C-domain provides additional stabilization. Together, they anchor the cellulase passenger on the cell surface with correct orientation.
3. **Reduced metabolic burden:** Removal of the central repetitive domain (~120 tandem repeats of 48 amino acids) drastically reduces the fusion size compared to full-length INP, lowering the metabolic burden on the host cell [11][12].

1. **Tat 依赖性转位：** TorA 信号肽将融合蛋白引导至 Tat（双精氨酸转位）途径，使完全折叠的蛋白穿过内膜——这对需要在膜插入前正确折叠的纤维素酶至关重要。
2. **外膜锚定：** INP 的 N 结构域包含插入外膜的膜锚定序列。C 结构域提供额外的稳定性。两者共同将纤维素酶 passenger 以正确方向锚定在细胞表面。
3. **降低代谢负荷：** 去除中央重复结构域（约 120 个 48 氨基酸的串联重复）相比全长 INP 大幅减小融合蛋白尺寸，降低了宿主细胞的代谢负荷 [11][12]。

#### Design Notes / 设计说明

- **Source:** *Pseudomonas syringae* INP gene, truncated to N+C domains only.
- **TorA signal peptide:** From *E. coli* trimethylamine N-oxide reductase (TorA). Directs the fusion to the Tat pathway, bypassing the Sec machinery. The Tat pathway is advantageous because it transports folded proteins, which is necessary for cellulase domains that must fold co-translationally.
- **His tag:** C-terminal 6×His for Western blot detection, immunofluorescence confirmation of surface localization, and potential IMAC purification.
- **References:** Liu et al. (2025) [11]; Zhang et al. (2025) [12]; Wolber (1993) [5].
- **Related Registry parts:** This part is an engineered variant building on the established INP surface display system.

- **来源：** 丁香假单胞菌 INP 基因，截短为仅 N+C 结构域。
- **TorA 信号肽：** 来自大肠杆菌三甲胺 N-氧化物还原酶（TorA）。将融合蛋白引导至 Tat 途径，绕过 Sec 机制。Tat 途径的优势在于转运已折叠的蛋白，这对必须共翻译折叠的纤维素酶结构域是必需的。
- **His 标签：** C 端 6×His，用于 Western blot 检测、表面定位的免疫荧光确认，以及潜在的 IMAC 纯化。
- **参考文献：** Liu et al. (2025) [11]; Zhang et al. (2025) [12]; Wolber (1993) [5].
- **相关标准库元件：** 该元件是在已建立的 INP 表面展示系统基础上构建的工程化变体。

---

### BBa_K5268003: Cel48S — GH48 Exo-cellulase / GH48 外切纤维素酶

#### Basic Description / 基本描述

Cel48S is a glycosyl hydrolase family 48 (GH48) exo-cellulase (cellobiohydrolase, EC 3.2.1.176) from *Clostridium thermocellum* [13]. It is one of the major cellulosomal enzymes responsible for crystalline cellulose degradation. The native enzyme contains an N-terminal catalytic domain (~700 amino acids, ~80 kDa) connected via a linker to a type I dockerin domain. For the friskoli project, the dockerin domain has been removed and the catalytic domain codon-optimized for *E. coli* expression. The enzyme attacks cellulose chains from the reducing end, processively cleaving cellobiose units.

Cel48S 是来自热纤梭菌（*Clostridium thermocellum*）的糖苷水解酶家族 48（GH48）外切纤维素酶（纤维二糖水解酶，EC 3.2.1.176）[13]。它是负责结晶纤维素降解的主要纤维小体酶之一。天然酶包含一个 N 端催化结构域（约 700 个氨基酸，~80 kDa），通过连接区连接到 I 型 dockerin 结构域。在 friskoli 项目中，dockerin 结构域已被去除，催化结构域已针对大肠杆菌表达进行密码子优化。该酶从还原端攻击纤维素链，持续性地切割纤维二糖单元。

#### Function in the System / 在系统中的功能

Cel48S is deployed as one of three cellulases in the Module 2 consortium cocktail. It provides processive exo-cellulase activity for the system:

Cel48S 作为模块二联合菌群中的三种纤维素酶之一部署。它为系统提供持续性的外切纤维素酶活性：

1. **Crystalline cellulose attack:** Cel48S (GH48) is one of the few enzyme families capable of efficiently hydrolyzing highly crystalline cellulose regions. It processively releases cellobiose from the reducing end of cellulose chains.
2. **Synergy with Cel9K and Cel5L:** The exo-mode activity of Cel48S synergizes with the endo-acting enzymes (Cel9K, Cel5L) to achieve complete cellulose degradation. Endo-cleavage by Cel5L creates new chain ends for Cel48S and Cel9K to act upon.
3. **Cellobiose production:** Like all three cellulases deployed, Cel48S ultimately produces cellobiose as the primary soluble product, which serves as the chemotactic signal for Module 1.

1. **结晶纤维素攻击：** Cel48S（GH48）是少数能够有效水解高结晶度纤维素区域的酶家族之一。它持续地从纤维素链的还原端释放纤维二糖。
2. **与 Cel9K 和 Cel5L 的协同作用：** Cel48S 的外切模式活性与内切酶（Cel9K、Cel5L）协同作用，实现完全的纤维素降解。Cel5L 的内切切割为 Cel48S 和 Cel9K 创造了新的链端。
3. **纤维二糖生产：** 与所有三种部署的纤维素酶一样，Cel48S 最终产生纤维二糖作为主要的可溶性产物，作为模块一的趋化信号。

#### Design Notes / 设计说明

- **Source:** *Clostridium thermocellum* ATCC 27405 cellulosome. The Cel48S gene (also known as CelS or S8) is the most abundant catalytic subunit in the *C. thermocellum* cellulosome.
- **Dockerin removal:** The C-terminal type I dockerin domain (which normally anchors the enzyme to the scaffoldin CipA in the native cellulosome) has been removed. This prevents non-specific interactions with any potential dockerin-binding components in the *E. coli* host and ensures the enzyme functions as a free catalytic domain on the cell surface.
- **Codon optimization:** The gene has been codon-optimized for *E. coli* K-12 to maximize heterologous expression. *C. thermocellum* has a significantly different codon usage profile (low GC, ~39%) from *E. coli* (~51%), making optimization essential.
- **Catalytic mechanism:** GH48 enzymes use an inverting mechanism with two catalytic residues (glutamic acid and aspartic acid). The active site is located within a tunnel-shaped cavity formed by the (α/α)₆ barrel fold, which encloses the cellulose chain for processive cleavage.
- **Reference:** Leis et al. (2017) [13].

- **来源：** 热纤梭菌 ATCC 27405 纤维小体。Cel48S 基因（也称为 CelS 或 S8）是热纤梭菌纤维小体中丰度最高的催化亚基。
- **Dockerin 去除：** C 端 I 型 dockerin 结构域（在天然纤维小体中将酶锚定到支架蛋白 CipA）已被去除。这防止了与大肠杆菌宿主中任何潜在的 dockerin 结合组分的非特异性相互作用，并确保酶在细胞表面作为游离催化结构域发挥作用。
- **密码子优化：** 基因已针对大肠杆菌 K-12 进行密码子优化以最大化异源表达。热纤梭菌的密码子使用模式与大肠杆菌显著不同（低 GC，约 39% vs. 约 51%），优化是必不可少的。
- **催化机制：** GH48 酶使用翻转机制（inverting mechanism），具有两个催化残基（谷氨酸和天冬氨酸）。活性位点位于由 (α/α)₆ 桶状折叠形成的隧道状空腔内，该结构包裹纤维素链以实现持续性切割。
- **参考文献：** Leis et al. (2017) [13].

---

### BBa_K5268004: Cel9K — GH9 Exo-cellulase / GH9 外切纤维素酶

#### Basic Description / 基本描述

Cel9K is a glycosyl hydrolase family 9 (GH9) exo-cellulase (cellobiohydrolase, EC 3.2.1.176) from *Clostridium thermocellum* [13]. GH9 cellulases are characterized by a (α/α)₆ barrel catalytic domain and frequently possess a family 3c carbohydrate-binding module (CBM3c) adjacent to the active site. The native enzyme contains a C-terminal dockerin domain for cellulosome integration, which has been removed for the friskoli construct. The catalytic domain has been codon-optimized for *E. coli* expression. Cel9K processively releases cellobiose from cellulose chains.

Cel9K 是来自热纤梭菌（*Clostridium thermocellum*）的糖苷水解酶家族 9（GH9）外切纤维素酶（纤维二糖水解酶，EC 3.2.1.176）[13]。GH9 纤维素酶的特征是具有 (α/α)₆ 桶状催化结构域，通常在活性位点附近具有家族 3c 碳水化合物结合模块（CBM3c）。天然酶包含一个用于纤维小体整合的 C 端 dockerin 结构域，在 friskoli 构建体中已被去除。催化结构域已针对大肠杆菌表达进行密码子优化。Cel9K 持续性地从纤维素链释放纤维二糖。

#### Function in the System / 在系统中的功能

Cel9K is the second cellulase in the Module 2 consortium cocktail:

Cel9K 是模块二联合菌群中的第二种纤维素酶：

1. **Exo-cellulase activity:** Cel9K belongs to GH9, a family that includes both endo- and exo-acting cellulases. In *C. thermocellum*, Cel9K functions primarily as a processive exo-cellulase, attacking cellulose from chain ends and releasing cellobiose.
2. **Synergy with Cel48S and Cel5L:** Cel9K and Cel48S together provide two distinct exo-cellulase activities with potentially different chain-end preferences and processivity characteristics, maximizing cellobiose release. Cel5L provides the endo-cleavage that generates fresh chain ends for both exo-enzymes.
3. **Cellobiose production:** All soluble product is cellobiose, which diffuses to and activates Module 1.

1. **外切纤维素酶活性：** Cel9K 属于 GH9，该家族包含内切和外切两种纤维素酶。在热纤梭菌中，Cel9K 主要作为持续性外切纤维素酶发挥作用，从链端攻击纤维素并释放纤维二糖。
2. **与 Cel48S 和 Cel5L 的协同作用：** Cel9K 和 Cel48S 共同提供两种不同的外切纤维素酶活性，可能具有不同的链端偏好和持续特性，最大化纤维二糖释放。Cel5L 提供内切切割，为两种外切酶生成新的链端。
3. **纤维二糖生产：** 所有可溶性产物均为纤维二糖，扩散至并激活模块一。

#### Design Notes / 设计说明

- **Source:** *Clostridium thermocellum* ATCC 27405 cellulosome.
- **Dockerin removal:** As with Cel48S and Cel5L, the dockerin domain has been removed for independent expression on the *E. coli* surface.
- **Codon optimization:** Codon-optimized for *E. coli* K-12.
- **GH9 catalytic features:** Cel9K uses an inverting mechanism. The CBM3c module adjacent to the catalytic domain enhances substrate binding and may contribute to processivity by helping to guide the cellulose chain through the active site.
- **Reference:** Leis et al. (2017) [13].

- **来源：** 热纤梭菌 ATCC 27405 纤维小体。
- **Dockerin 去除：** 与 Cel48S 和 Cel5L 一样，dockerin 结构域已被去除以实现大肠杆菌表面的独立表达。
- **密码子优化：** 针对大肠杆菌 K-12 进行密码子优化。
- **GH9 催化特征：** Cel9K 使用翻转机制。催化结构域相邻的 CBM3c 模块增强了底物结合，可能通过帮助引导纤维素链通过活性位点而促进持续性。
- **参考文献：** Leis et al. (2017) [13].

---

### BBa_K5268005: Cel5L — GH5 Processive Endoglucanase / GH5 持续性内切葡聚糖酶

#### Basic Description / 基本描述

Cel5L is a glycosyl hydrolase family 5 (GH5) processive endoglucanase (EC 3.2.1.4) from *Clostridium thermocellum* [13]. GH5 is one of the largest and most diverse cellulase families, characterized by a (β/α)₈ TIM-barrel catalytic domain with a cleft-shaped active site. Unlike classical endoglucanases that cleave randomly, Cel5L exhibits a processive mode of action — it binds to a cellulose chain, cleaves internally, and then continues to cleave processively, releasing cellobiose. The native dockerin domain has been removed and the catalytic domain codon-optimized for *E. coli*.

Cel5L 是来自热纤梭菌（*Clostridium thermocellum*）的糖苷水解酶家族 5（GH5）持续性内切葡聚糖酶（EC 3.2.1.4）[13]。GH5 是最大且最多样化的纤维素酶家族之一，特征是具有 (β/α)₈ TIM 桶状催化结构域和裂隙状活性位点。与随机切割的经典内切葡聚糖酶不同，Cel5L 表现出持续性作用模式——它结合纤维素链，在内部切割，然后继续持续性地切割，释放纤维二糖。天然 dockerin 结构域已被去除，催化结构域已针对大肠杆菌进行密码子优化。

#### Function in the System / 在系统中的功能

Cel5L is the third cellulase in the Module 2 consortium cocktail, providing the crucial endo-initiation activity:

Cel5L 是模块二联合菌群中的第三种纤维素酶，提供关键的内切起始活性：

1. **Endo-initiation:** Cel5L attacks internal β-1,4 glycosidic bonds within amorphous and crystalline cellulose regions, creating new reducing and non-reducing chain ends. This relieves the chain-end dependency of the two exo-cellulases (Cel48S and Cel9K).
2. **Processive endo-action:** Unlike non-processive endoglucanases that dissociate after a single cleavage, Cel5L remains bound and continues cleaving processively, producing cellobiose — making it a direct contributor to signal molecule generation in addition to its chain-end-generating role.
3. **Consortium synergy:** The endo-initiation by Cel5L, combined with the exo-processivity of Cel48S and Cel9K, creates a three-enzyme synergistic system that thoroughly degrades cellulose to cellobiose.

1. **内切起始：** Cel5L 攻击非结晶和结晶纤维素区域内部的 β-1,4 糖苷键，生成新的还原端和非还原端。这缓解了两种外切纤维素酶（Cel48S 和 Cel9K）对链端的依赖。
2. **持续性内切作用：** 不同于一次切割后即解离的非持续性内切葡聚糖酶，Cel5L 保持结合并持续性地继续切割，产生纤维二糖——使其除了生成链端的作用外，还直接贡献于信号分子的产生。
3. **菌群协同：** Cel5L 的内切起始与 Cel48S 和 Cel9K 的外切持续性相结合，创建了一个三酶协同系统，将纤维素彻底降解为纤维二糖。

#### Design Notes / 设计说明

- **Source:** *Clostridium thermocellum* ATCC 27405 cellulosome.
- **Dockerin removal:** Dockerin domain removed; catalytic domain retained.
- **Codon optimization:** Codon-optimized for *E. coli* K-12.
- **Processivity mechanism:** Cel5L achieves processivity through a structural feature unique among GH5 endoglucanases — a series of aromatic residues lining the substrate-binding cleft that form hydrophobic stacking interactions with the cellulose chain, preventing dissociation between cleavage events. This makes Cel5L a "hybrid" enzyme with both endo-attack capability and exo-like processivity.
- **Reference:** Leis et al. (2017) [13].

- **来源：** 热纤梭菌 ATCC 27405 纤维小体。
- **Dockerin 去除：** dockerin 结构域已去除；保留催化结构域。
- **密码子优化：** 针对大肠杆菌 K-12 进行密码子优化。
- **持续性机制：** Cel5L 通过 GH5 内切葡聚糖酶中独特的结构特征实现持续性——衬在底物结合裂隙中的一系列芳香族残基与纤维素链形成疏水堆积相互作用，防止切割事件之间的解离。这使 Cel5L 成为同时具有内切攻击能力和类外切持续性的"混合"酶。
- **参考文献：** Leis et al. (2017) [13].

---

### BBa_K5268006: Linker (Mixed) — Rigid-Flexible Linker / 刚柔混合连接肽

#### Basic Description / 基本描述

This part encodes a mixed rigid-flexible linker peptide designed to connect the INPNC anchor to the cellulase catalytic domain. The linker consists of alternating rigid (EAAAK)ₙ and flexible (GGGGS)ₙ motifs, arranged to provide both structural separation and controlled conformational mobility between the anchor and the enzyme [14][15].

该元件编码一个刚柔混合连接肽，设计用于连接 INPNC 锚定序列与纤维素酶催化结构域。连接肽由交替排列的刚性（EAAAK）ₙ和柔性（GGGGS）ₙ基序组成，旨在在锚定序列和酶之间提供结构分离和可控的构象灵活性 [14][15]。

```
(EAAAK)ₙ — (GGGGS)ₙ
```

| Motif / 基序 | Type / 类型 | Property / 性质 | Function / 功能 |
|:---|:---|:---|:---|
| **(EAAAK)ₙ** | Rigid α-helical | Forms a stable α-helix; resists bending | Spatially separates domains; prevents steric interference |
| **(GGGGS)ₙ** | Flexible random coil | Highly mobile; glycine-rich | Allows cellulase to reorient for substrate access |

#### Function in the System / 在系统中的功能

The mixed linker serves as the critical structural bridge in all three Module 2 expression cassettes (Cel48S, Cel9K, Cel5L):

混合连接肽在所有三个模块二表达盒（Cel48S、Cel9K、Cel5L）中作为关键的结构桥梁：

1. **Rigid spacer (EAAAK):** The α-helical EAAAK repeats provide a rigid stalk that projects the cellulase away from the cell surface and the INPNC anchor. This prevents steric hindrance between the large cellulase catalytic domain and the outer membrane, and between adjacent fusion proteins on the crowded cell surface.
2. **Flexible joint (GGGGS):** The flexible glycine-serine repeats allow the cellulase domain to adopt multiple orientations relative to the cell surface. This is essential for accessing cellulose fibers in the environment, which may approach the cell from any angle.
3. **Balanced design:** Pure flexible linkers can cause the enzyme to collapse against the membrane; pure rigid linkers may prevent the enzyme from reaching substrate altogether. The mixed design provides both projection and reach.

1. **刚性间隔区（EAAAK）：** α-螺旋 EAAAK 重复序列提供一个刚性柄，将纤维素酶投射出远离细胞表面和 INPNC 锚定序列。这防止了大体积纤维素酶催化结构域与外膜之间以及拥挤细胞表面上相邻融合蛋白之间的空间位阻。
2. **柔性关节（GGGGS）：** 柔性甘氨酸-丝氨酸重复序列允许纤维素酶结构域相对于细胞表面采取多种方向。这对于接触到环境中可能从任何角度接近细胞的纤维素纤维至关重要。
3. **平衡设计：** 纯柔性连接肽可能导致酶塌缩到膜上；纯刚性连接肽可能完全阻止酶接触到底物。混合设计同时提供了投射和可及性。

#### Design Notes / 设计说明

- **Repeat number:** The exact number of EAAAK and GGGGS repeats is tuned for each cellulase based on molecular dynamics predictions of domain spacing requirements.
- **Reference for EAAAK:** Arai et al. (2001) demonstrated that EAAAK repeats form stable monomeric α-helices with predictable length (approximately 1.5 nm per repeat) [14].
- **Reference for GGGGS:** Huston et al. (1988) established GGGGS as a flexible linker for single-chain antibody construction; it has since become a standard in fusion protein design [15].

- **重复数：** EAAAK 和 GGGGS 重复序列的具体数量根据分子动力学对结构域间距要求的预测，为每种纤维素酶进行了调整。
- **EAAAK 参考文献：** Arai et al. (2001) 证明了 EAAAK 重复序列形成稳定的单体 α-螺旋，具有可预测的长度（约 1.5 nm 每个重复）[14]。
- **GGGGS 参考文献：** Huston et al. (1988) 建立了 GGGGS 作为单链抗体构建的柔性连接肽；此后它已成为融合蛋白设计中的标准 [15]。

---

### BBa_K5268007: ascFB Operon / ascFB 操纵子 (Composite)

#### Basic Description / 基本描述

This composite part contains both ascF and ascB under the control of J23116, with the B0034 RBS preceding each gene and the B0015 terminator. It is the complete functional unit for Module 1, designed for one-step cloning into a pBR322-origin vector (pGEX backbone, AmpR).

这个复合元件包含在 J23116 控制下的 ascF 和 ascB，每个基因前有 B0034 RBS，末端有 B0015 终止子。它是模块一的完整功能单元，设计用于一步克隆到 pBR322 复制起点载体（pGEX 骨架，AmpR）中。

#### Structure / 结构

```
[Prefix] — J23116 — B0034 — ascF — B0034 — ascB — B0015 — [Suffix]
```

- **Total length:** ~3,700 bp
- **GC content:** ~51%

#### Function / 功能

When assembled into the pBR322-origin vector and transformed into *E. coli* MG1655, this operon enables cellobiose transport (AscF), cellobiose-6-P hydrolysis (AscB), and the PTS-mediated chemotactic response to cellobiose gradients.

当组装到 pBR322 复制起点载体中并转化进入大肠杆菌 MG1655 时，该操纵子实现纤维二糖转运（AscF）、纤维二糖-6-P 水解（AscB）以及对纤维二糖梯度的 PTS 介导的趋化响应。

---

### BBa_K5268008: Cel48S Expression Cassette / Cel48S 表达盒 (Composite)

#### Basic Description / 基本描述

This composite part contains the complete Cel48S surface display expression cassette for Module 2b. It includes the J23116 promoter, B0034 RBS, TorA-INPNC anchor (BBa_K1933011), mixed linker (BBa_K5268006), Cel48S catalytic domain (BBa_K5268003), and B0015 terminator. Designed for cloning into pCDF-1b (SpecR).

这个复合元件包含模块 2b 的完整 Cel48S 表面展示表达盒。包括 J23116 启动子、B0034 RBS、TorA-INPNC 锚定序列（BBa_K1933011）、混合连接肽（BBa_K5268006）、Cel48S 催化结构域（BBa_K5268003）和 B0015 终止子。设计用于克隆到 pCDF-1b（SpecR）中。

#### Structure / 结构

```
[Prefix] — J23116 — B0034 — TorA — INPNC — Linker(Mixed) — Cel48S — B0015 — [Suffix]
```

#### Function / 功能

This cassette drives the expression of the INPNC-Cel48S surface display fusion in *E. coli*. The resulting strain displays Cel48S on its outer membrane and releases cellobiose from cellulose in the local environment. This strain is one component of the three-strain consortium cocktail for Module 2.

该表达盒驱动 INPNC-Cel48S 表面展示融合蛋白在大肠杆菌中的表达。所得菌株在外膜上展示 Cel48S，并从局部环境中的纤维素释放纤维二糖。该菌株是模块二三菌株联合菌群的组分之一。

---

### BBa_K5268009: Cel9K Expression Cassette / Cel9K 表达盒 (Composite)

#### Basic Description / 基本描述

This composite part contains the complete Cel9K surface display expression cassette for Module 2a. It includes the J23116 promoter, B0034 RBS, TorA-INPNC anchor (BBa_K1933011), mixed linker (BBa_K5268006), Cel9K catalytic domain (BBa_K5268004), and B0015 terminator. Designed for cloning into pCDF-1b (SpecR).

这个复合元件包含模块 2a 的完整 Cel9K 表面展示表达盒。包括 J23116 启动子、B0034 RBS、TorA-INPNC 锚定序列（BBa_K1933011）、混合连接肽（BBa_K5268006）、Cel9K 催化结构域（BBa_K5268004）和 B0015 终止子。设计用于克隆到 pCDF-1b（SpecR）中。

#### Structure / 结构

```
[Prefix] — J23116 — B0034 — TorA — INPNC — Linker(Mixed) — Cel9K — B0015 — [Suffix]
```

#### Function / 功能

This cassette drives the expression of the INPNC-Cel9K surface display fusion in *E. coli*. The resulting strain displays Cel9K on its outer membrane. As part of the consortium cocktail, it contributes exo-cellulase activity that releases cellobiose from cellulose chain ends generated by the Cel5L-expressing strain.

该表达盒驱动 INPNC-Cel9K 表面展示融合蛋白在大肠杆菌中的表达。所得菌株在外膜上展示 Cel9K。作为联合菌群的一部分，它贡献外切纤维素酶活性，从 Cel5L 表达菌株生成的纤维素链端释放纤维二糖。

---

### BBa_K5268010: Cel5L Expression Cassette / Cel5L 表达盒 (Composite)

#### Basic Description / 基本描述

This composite part contains the complete Cel5L surface display expression cassette for Module 2c. It includes the J23116 promoter, B0034 RBS, TorA-INPNC anchor (BBa_K1933011), mixed linker (BBa_K5268006), Cel5L catalytic domain (BBa_K5268005), and B0015 terminator. Designed for cloning into pCDF-1b (SpecR).

这个复合元件包含模块 2c 的完整 Cel5L 表面展示表达盒。包括 J23116 启动子、B0034 RBS、TorA-INPNC 锚定序列（BBa_K1933011）、混合连接肽（BBa_K5268006）、Cel5L 催化结构域（BBa_K5268005）和 B0015 终止子。设计用于克隆到 pCDF-1b（SpecR）中。

#### Structure / 结构

```
[Prefix] — J23116 — B0034 — TorA — INPNC — Linker(Mixed) — Cel5L — B0015 — [Suffix]
```

#### Function / 功能

This cassette drives the expression of the INPNC-Cel5L surface display fusion in *E. coli*. The resulting strain displays the processive endoglucanase Cel5L on its outer membrane. Within the consortium cocktail, this strain provides the critical endo-initiation function — cleaving internal cellulose bonds to generate new chain ends for the exo-cellulase strains (Cel48S and Cel9K) to act upon, while also contributing directly to cellobiose production through its processive action.

该表达盒驱动 INPNC-Cel5L 表面展示融合蛋白在大肠杆菌中的表达。所得菌株在外膜上展示持续性内切葡聚糖酶 Cel5L。在联合菌群中，该菌株提供关键的内切起始功能——切割纤维素内部键，为外切纤维素酶菌株（Cel48S 和 Cel9K）生成新的链端，同时通过其持续性作用直接贡献于纤维二糖生产。

---

### BBa_J23116: Anderson Constitutive Promoter / Anderson 组成型启动子

#### Basic Description / 基本描述

BBa_J23116 is a member of the Anderson promoter family, a collection of constitutive promoters derived from the *E. coli* σ⁷⁰-dependent consensus sequence [7]. J23116 has a relative promoter strength of 0.16 (on a scale where J23119 = 1.0, measured by GFP fluorescence in the 2008 iGEM interlab study) [7]. It is one of the weaker promoters in the Anderson collection.

BBa_J23116 是 Anderson 启动子家族的成员，该家族是一组源自大肠杆菌 σ⁷⁰ 依赖共有序列的组成型启动子集合 [7]。J23116 的相对启动子强度为 0.16（在 J23119 = 1.0 的尺度上，通过 2008 年 iGEM 实验室间研究的 GFP 荧光测量）[7]。它是 Anderson 启动子集合中较弱的启动子之一。

#### Sequence / 序列

```
TTGACGGCTAGCTCAGTCCTAGGTACAGTGCTAGC
```

#### Function in the System / 在系统中的功能

J23116 drives the expression of both modules. Its weak strength was deliberately chosen for the following reasons:

J23116 驱动两个模块的表达。选择其弱强度是出于以下原因：

**For Module 1 (ascF/ascB):** AscF is a transmembrane protein. Weak expression prevents membrane toxicity, inclusion body formation, and Sec translocon saturation. The expression level from J23116 on the low-copy pBR322-origin vector (~15–20 copies/cell) is predicted to produce approximately 100–400 AscF molecules per cell, which is sufficient for PTS flux to modulate CheA activity but below the toxicity threshold.

**对于模块一（ascF/ascB）：** AscF 是一种跨膜蛋白。弱表达可防止膜毒性、包涵体形成和 Sec 转位子饱和。从低拷贝 pBR322 复制起点载体（约 15–20 拷贝/细胞）上的 J23116 表达水平预测每个细胞产生约 100–400 个 AscF 分子，这足以使 PTS 通量调节 CheA 活性但低于毒性阈值。

**For Module 2 (cellulase surface display):** Although a stronger promoter might increase cellulase production, excessive surface display can cause outer membrane stress, cell aggregation, and metabolic burden — especially with three large fusion proteins deployed across the consortium. J23116 provides a conservative starting point, adjustable in future optimization cycles.

**对于模块二（纤维素酶表面展示）：** 尽管更强的启动子可能增加纤维素酶产量，但过度的表面展示可能导致外膜应激、细胞聚集和代谢负荷——尤其是在联合菌群中部署三种大型融合蛋白时。J23116 提供了一个保守的起点，可在未来的优化循环中调整。

---

### BBa_B0034: Medium-Strength RBS / 中等强度 RBS

#### Basic Description / 基本描述

BBa_B0034 is a standard iGEM Registry ribosome binding site with medium translation initiation strength. Its sequence is:

BBa_B0034 是标准 iGEM 标准库核糖体结合位点，具有中等翻译起始强度。其序列为：

```
AAAGAGGAGAAA
```

This sequence contains a canonical Shine-Dalgarno (SD) sequence (AGGAG) with a 7-base spacing to the start codon, following the consensus for efficient translation initiation in *E. coli* [8]. B0034 has been characterized in numerous iGEM projects and provides reliable, medium-level translation.

该序列包含典型的 Shine-Dalgarno（SD）序列（AGGAG），与起始密码子间隔 7 个碱基，遵循大肠杆菌中有效翻译起始的共有序列 [8]。B0034 已在众多 iGEM 项目中被表征，提供可靠的中等水平翻译。

#### Function in the System / 在系统中的功能

B0034 precedes each coding sequence across all four expression cassettes (ascF, ascB, and the three INPNC-cellulase fusions). In the ascFB operon, both genes have their own B0034 RBS, enabling independent translation of AscF and AscB from the same bicistronic mRNA. In the three Module 2 cassettes, a single B0034 is used per monocistronic transcript (INPNC-Linker-Cellulase fusion).

B0034 位于所有四个表达盒的每个编码序列之前（ascF、ascB 以及三个 INPNC-纤维素酶融合蛋白）。在 ascFB 操纵子中，两个基因各有自己的 B0034 RBS，使 AscF 和 AscB 能够从同一条双顺反子 mRNA 独立翻译。在三个模块二表达盒中，每个单顺反子转录本（INPNC-Linker-纤维素酶融合蛋白）使用一个 B0034。

---

### BBa_B0015: Double Terminator / 双终止子

#### Basic Description / 基本描述

BBa_B0015 is a bidirectional double terminator commonly used in the iGEM Registry. It contains two terminator sequences in series:

BBa_B0015 是 iGEM 标准库中常用的双向双终止子。它包含两个串联的终止子序列：

```
Bba_B0010: CGCGGCGGTTTTTTATG (T1 from *E. coli rrnB*)
Bba_B0012: CCAGGCTTACATTTATGCTTCCGGCTCGTATGTTGTGTGGA (T7 from bacteriophage T7)
```

Total length is approximately 127 bp. The double terminator provides strong, efficient transcription termination in both directions, preventing read-through into adjacent sequences and ensuring clean transcript ends [9].

总长度约 127 bp。双终止子在两个方向上提供强大有效的转录终止，防止通读进入相邻序列并确保转录本末端的干净 [9]。

#### Function in the System / 在系统中的功能

B0015 terminates transcription after the last coding sequence in each expression cassette (after ascB in Module 1; after each cellulase in the three Module 2 cassettes). This prevents transcriptional read-through into the plasmid backbone, which could interfere with plasmid replication or antibiotic resistance gene expression.

B0015 在每个表达盒的最后一个编码序列后终止转录（模块一中在 ascB 后；三个模块二表达盒中在每个纤维素酶后）。这防止转录通读进入质粒骨架，从而避免干扰质粒复制或抗生素抗性基因表达。

---

## Plasmid Backbones / 质粒骨架

Unlike the standard iGEM pSB series, the friskoli project uses two non-standard plasmid backbones selected for their compatible replication origins and appropriate copy numbers.

与标准 iGEM pSB 系列不同，friskoli 项目使用两种非标准质粒骨架，选择依据是其兼容的复制起点和适当的拷贝数。

### Module 1 Carrier: pBR322-Origin Vector (pGEX Backbone) / 模块一载体：pBR322 复制起点载体（pGEX 骨架）

| Feature / 特征 | Detail / 详情 |
|:---|:---|
| **Replication origin / 复制起点** | pBR322 (ColE1-type, ~15–20 copies/cell) |
| **Antibiotic resistance / 抗生素抗性** | Ampicillin (AmpR, β-lactamase) |
| **Backbone type / 骨架类型** | pGEX-type expression vector |
| **Copy number / 拷贝数** | ~15–20 copies per cell |
| **Compatibility / 兼容性** | Compatible with CloDF13 (pCDF-1b) for co-transformation |

#### Rationale / 选择理由

The pBR322 origin provides a moderate-low copy number (~15–20 copies/cell), higher than pSC101 (~5–10 copies) but far lower than pMB1 derivatives (~100–300 copies). This copy number is deliberately chosen for Module 1:

pBR322 复制起点提供中等偏低的拷贝数（约 15–20 拷贝/细胞），高于 pSC101（约 5–10 拷贝）但远低于 pMB1 衍生载体（约 100–300 拷贝）。该拷贝数为模块一特意选择：

- **Toxicity avoidance:** AscF is a multi-pass transmembrane protein. The ~15–20 copy number, combined with the weak J23116 promoter, keeps AscF expression within its functional window without exceeding the membrane capacity for protein insertion.
- **PTS flux sensitivity:** With ~15–20 copies per cell, the molar ratio of plasmid-encoded AscF to chromosomally encoded PTS general components (EI, HPr) is approximately 1:5 to 1:2, ensuring that plasmid-expressed AscF integrates into the PTS without overwhelming the phosphotransfer chain.
- **Co-transformation compatibility:** The pBR322/ColE1 origin is compatible with the CloDF13 origin (pCDF-1b) for stable co-maintenance in the same cell, mediated by distinct replication control mechanisms.

- **避免毒性：** AscF 是一种多次跨膜蛋白。约 15–20 的拷贝数与弱启动子 J23116 结合，使 AscF 表达保持在其功能窗口内，而不超过膜插入蛋白的容量。
- **PTS 通量敏感性：** 在约 15–20 拷贝/细胞下，质粒编码的 AscF 与染色体编码的 PTS 通用组分（EI、HPr）的摩尔比约为 1:5 至 1:2，确保质粒表达的 AscF 整合到 PTS 中而不会压倒磷酸转移链。
- **共转化兼容性：** pBR322/ColE1 复制起点与 CloDF13 复制起点（pCDF-1b）兼容，通过不同的复制控制机制在同一细胞中稳定共维持。

---

### Module 2 Carrier: pCDF-1b (CloDF13 Origin) / 模块二载体：pCDF-1b（CloDF13 复制起点）

| Feature / 特征 | Detail / 详情 |
|:---|:---|
| **Replication origin / 复制起点** | CloDF13 (~20–30 copies/cell) |
| **Antibiotic resistance / 抗生素抗性** | Spectinomycin (SpecR, aadA) |
| **Backbone type / 骨架类型** | pCDF-1b (Novagen Duet vector series) |
| **Copy number / 拷贝数** | ~20–30 copies per cell |
| **Compatibility / 兼容性** | Compatible with pBR322/ColE1 (pGEX) for co-transformation |

#### Rationale / 选择理由

pCDF-1b carries the CloDF13 replicon, which is fully compatible with ColE1-type origins (including pBR322) for stable co-transformation [10]. Each of the three Module 2 cellulase cassettes is cloned separately into pCDF-1b, producing three distinct strains that are mixed as a consortium cocktail. Key design considerations:

pCDF-1b 携带 CloDF13 复制子，与 ColE1 型复制起点（包括 pBR322）完全兼容，可实现稳定的共转化 [10]。三个模块二纤维素酶表达盒各自单独克隆到 pCDF-1b 中，产生三个不同的菌株，以联合菌群形式混合。关键设计考量：

- **Moderate copy number:** ~20–30 copies/cell provides sufficient gene dosage for surface display of each cellulase without overburdening the Tat pathway and outer membrane insertion machinery. Higher copy numbers (e.g., pMB1 derivatives) could saturate the Tat translocon with signal-peptide-bearing precursors.
- **Consortium strategy:** Each strain in the consortium carries exactly one cellulase type. This modular approach allows independent optimization of each expression cassette (promoter strength, linker composition, induction) and flexible tuning of the strain ratio in the cocktail.
- **Spectinomycin selection:** The SpecR marker (aadA) is distinct from the AmpR marker on the Module 1 plasmid, enabling dual-antibiotic selection. Spectinomycin is also not commonly used in standard *E. coli* laboratory strains, minimizing the risk of background resistance.

- **中等拷贝数：** 约 20–30 拷贝/细胞为每种纤维素酶的表面展示提供足够的基因剂量，而不使 Tat 途径和外膜插入机制过载。更高的拷贝数可能使 Tat 转位子被带有信号肽的前体饱和。
- **菌群策略：** 菌群中的每个菌株仅携带一种纤维素酶。这种模块化方法允许独立优化每个表达盒（启动子强度、连接肽组成、诱导），并灵活调节鸡尾酒中各菌株的比例。
- **壮观霉素筛选：** SpecR 标记（aadA）与模块一质粒上的 AmpR 标记不同，可实现双抗生素筛选。壮观霉素在标准大肠杆菌实验室菌株中也不常用，最大限度地降低了背景抗性的风险。

---

## Part Usage Summary / 元件使用总结

### Module 1 Assembly / 模块一组装

```
pBR322-ori (pGEX, AmpR)
  └── [J23116 — B0034 — ascF — B0034 — ascB — B0015]
            ↑                    ↑
       BBa_K5268001        BBa_K5268002
     (ascF, EII^Cellobiose)  (ascB, Phospho-β-glu)

Composite part: BBa_K5268007 (ascFB Operon)
Copy number: ~15–20 copies/cell
```

### Module 2 Assemblies / 模块二组装

The three cellulase expression cassettes are built on pCDF-1b (CloDF13 ori, SpecR, ~20–30 copies/cell). Each is maintained in a separate *E. coli* strain. The three strains are combined as a consortium cocktail at the point of deployment.

三个纤维素酶表达盒构建在 pCDF-1b（CloDF13 复制起点，SpecR，约 20–30 拷贝/细胞）上。每个表达盒在单独的大肠杆菌菌株中维持。三个菌株在部署时以联合菌群形式混合。

#### Module 2a — Cel9K Strain

```
pCDF-1b (SpecR)
  └── [J23116 — B0034 — TorA — INPNC — Linker(Mixed) — Cel9K — B0015]
                                          ↑           ↑       ↑
                                     BBa_K1933011  BBa_K5268006  BBa_K5268004

Composite part: BBa_K5268009 (Cel9K Cassette)
```

#### Module 2b — Cel48S Strain

```
pCDF-1b (SpecR)
  └── [J23116 — B0034 — TorA — INPNC — Linker(Mixed) — Cel48S — B0015]
                                          ↑           ↑        ↑
                                     BBa_K1933011  BBa_K5268006  BBa_K5268003

Composite part: BBa_K5268008 (Cel48S Cassette)
```

#### Module 2c — Cel5L Strain

```
pCDF-1b (SpecR)
  └── [J23116 — B0034 — TorA — INPNC — Linker(Mixed) — Cel5L — B0015]
                                          ↑           ↑       ↑
                                     BBa_K1933011  BBa_K5268006  BBa_K5268005

Composite part: BBa_K5268010 (Cel5L Cassette)
```

### Registry Standards Used / 使用的标准库标准件

| Part / 元件 | Registry ID / 标准库编号 | Role / 角色 |
|:---|:---|:---|
| Constitutive promoter / 组成型启动子 | BBa_J23116 | Drives all expression cassettes (weak expression) |
| RBS / 核糖体结合位点 | BBa_B0034 | Translation initiation (×5 across all cassettes) |
| Terminator / 终止子 | BBa_B0015 | Transcription termination (×4 across all cassettes) |
| INPNC anchor / INPNC 锚定序列 | BBa_K1933011 | Surface display anchor for all Module 2 fusions |

### Plasmid Compatibility Summary / 质粒兼容性总结

| Module / 模块 | Backbone / 骨架 | Origin / 复制起点 | Resistance / 抗性 | Copy # / 拷贝数 | Strains / 菌株数 |
|:---|:---|:---|:---|:---:|:---:|
| Module 1 | pGEX-type | pBR322 (ColE1) | AmpR | ~15–20 | 1 |
| Module 2a | pCDF-1b | CloDF13 | SpecR | ~20–30 | 1 |
| Module 2b | pCDF-1b | CloDF13 | SpecR | ~20–30 | 1 |
| Module 2c | pCDF-1b | CloDF13 | SpecR | ~20–30 | 1 |

Co-transformation: pBR322 and CloDF13 are compatible replicons. When a single strain needs both Module 1 and one Module 2 cassette, both plasmids can be stably maintained with dual antibiotic selection (Amp + Spec).

共转化：pBR322 和 CloDF13 是兼容的复制子。当单个菌株需要同时携带模块一和一个模块二表达盒时，两个质粒可通过双抗生素筛选（Amp + Spec）稳定维持。

---

## References / 参考文献

[1] Hall BG, Xu J. Nucleotide sequence, function, activation, and evolution of the cryptic *asc* operon of *Escherichia coli* K-12. *Mol Biol Evol*. 1992;9(4):688-706.
[2] Postma PW, Lengeler JW, Jacobson GR. Phosphoenolpyruvate:carbohydrate phosphotransferase systems of bacteria. *Microbiological Reviews*. 1993;57(3):543-594.
[3] Lux R, Jahreis K, Bettenbrock K, Parkinson JS, Lengeler JW. Coupling the phosphotransferase system and the methyl-accepting chemotaxis protein-dependent chemotaxis signaling pathways of *Escherichia coli*. *Proceedings of the National Academy of Sciences*. 1995;92(25):11583-11587.
[4] Wagner S, Bader ML, Drew D, de Gier JW. Rationalizing membrane protein overexpression. *Trends in Biotechnology*. 2006;24(8):364-371.
[5] Wolber PK. Bacterial ice nucleation. *Advances in Microbial Physiology*. 1993;34:203-237.
[6] Kim H, Ku S. Development and optimization of an ice nucleation protein (INP)-based surface display system in *Escherichia coli*. 2018.
[7] Kelly JR, Rubin AJ, Davis JH, Ajo-Franklin CM, Cumbers J, Czar MJ, de Mora K, Glieberman AL, Monie DD, Endy D. Measuring the activity of BioBrick promoters using an *in vivo* reference standard. *Journal of Biological Engineering*. 2009;3:4.
[8] Salis HM, Mirsky EA, Voigt CA. Automated design of synthetic ribosome binding sites to control protein expression. *Nature Biotechnology*. 2009;27(10):946-950.
[9] iGEM Registry. Part BBa_B0015 documentation. Available at: http://parts.igem.org/Part:BBa_B0015
[10] iGEM Registry. Plasmid backbones documentation. Available at: http://parts.igem.org/Plasmid_backbones
[11] Liu et al. Engineered INPNC anchor for enhanced surface display in *Escherichia coli*. 2025.
[12] Zhang et al. Tat-dependent translocation of INP fusion proteins for outer membrane display. 2025.
[13] Leis B, Held C, Bergkemper F, Dennemarck K, Steinbauer R, Reiter A, Mechelke M, Moerch M, Hoffmann M, Liebl W. Comparative characterization of all cellulosomal cellulases from *Clostridium thermocellum* reveals high diversity in activity, stability, and mode of action. *Biotechnology for Biofuels*. 2017;10:30.
[14] Arai R, Ueda H, Kitayama A, Kamiya N, Nagamune T. Design of the linkers which effectively separate domains of a bifunctional fusion protein. *Protein Engineering*. 2001;14(8):529-532.
[15] Huston JS, Levinson D, Mudgett-Hunter M, Tai MS, Novotny J, Margolies MN, Ridge RJ, Bruccoleri RE, Haber E, Crea R, Oppermann H. Protein engineering of antibody binding sites: recovery of specific activity in an anti-digoxin single-chain Fv analogue produced in *Escherichia coli*. *Proceedings of the National Academy of Sciences*. 1988;85(16):5879-5883.

---

*Part numbers marked with {{placeholder}} are provisional and will be assigned upon submission to the iGEM Registry. All coding sequences have been verified against published genome sequences: E. coli MG1655 (GenBank: U00096.3) for ascF and ascB; C. thermocellum ATCC 27405 (GenBank: CP000568.1) for Cel48S, Cel9K, and Cel5L. BBa_K1933011 (INPNC) is an existing Registry part used as a standard component in the Module 2 fusions.*
