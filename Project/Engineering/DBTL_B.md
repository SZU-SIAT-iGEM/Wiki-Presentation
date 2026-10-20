# 路线 B 表面展示系统工程 DBTL 

## Overview

为了使工程菌能够直接作用于固体纤维素底物，我们最初设计了基于 **INPNC** 的细胞表面展示系统，并计划分别将 **Cel5L、Cel9K 和 Cel48S** 展示于三株工程菌表面。

实际构建过程中，我们连续遇到了转化、筛选和表达架构相关的问题，因此整个路线逐步演化为一系列诊断与重设计循环。

**DBTL B0** 聚焦于初始表面展示系统的设计，包括 INPNC 锚定元件、三种 cellulase cargo 以及组成型表达策略的选择。

**DBTL B1** 构建第一代 pCDF-based INPNC-cellulase 系统。虽然 Gibson assembly products 中能够检测到目标 DNA 结构，但候选菌落的 colony PCR 和 CMC–Congo red assay 均未提供有效的阳性证据，使问题从单纯的组装失败转向转化与筛选过程。

**DBTL B2** 重新评估原有 SmR-based selection system。WT 在 streptomycin、spectinomycin 及两者联合条件下均能够生长，说明原有筛选体系无法可靠区分 transformants 与未转化细胞，因此这一筛选策略被弃用。

**DBTL B3** 使用 pACYC-based backbone 和 chloramphenicol selection 重新建立转化体系。WT 被有效抑制，empty vector 能够正常获得转化子，但三个 INPNC-cellulase constructs 仍未形成可靠菌落；与此同时，assembly PCR 仍可检测到正确的目标结构，使问题进一步集中到 **INPNC-cellulase expression cassette 本身**。

**DBTL B4** 基于上述结果重新审视表达架构。我们开始考虑持续组成型表达可能增加宿主负担，同时也意识到需要通过更简单的 cargo 对现有组装体系进行独立验证，因此决定引入诱导型表达和 GFP reporter。

**DBTL B5** 同期构建 **Ptac-GFP** 和 **Ptac-INPNC-Cel9K**。Ptac-GFP 获得了候选菌落，并经 colony PCR 验证为正确重组子，而 Ptac-INPNC-Cel9K 仍未获得转化子。这一结果说明，当前 pACYC-based cloning 和 chloramphenicol selection 本身能够获得正确重组质粒，而仅将 J23116 替换为 Ptac-lacO 并不足以解决 INPNC-cellulase 构建失败的问题。

结合 Human Practices 访谈中关于 **anchor–passenger compatibility** 的反馈，我们进一步认识到，不同表面展示锚定系统与 passenger protein 之间可能存在不同的适配性，没有绝对的规则能够预测乘客蛋白究竟和哪一个系统适配。因此，**DBTL B6** 不再继续围绕 INPNC 进行重复尝试，而是引入另一种经典外膜展示系统 **Lpp-OmpA**，并设计 Ptac-Lpp-OmpA-Cel9K 和 Ptac-Lpp-OmpA-Cel48S 作为下一轮候选构建。

通过这些连续的 DBTL cycles，我们逐步将问题从最初笼统的“表面展示质粒构建失败”，收窄到 **特定 surface-display fusion architecture 与 cellulase cargo 的兼容性问题**。这一过程也使后续工程方向从单纯重复 cloning，转变为有依据地比较不同表达调控和锚定系统。

---

## DBTL B0 Designing the surface-display expression system

### Overview

在开始湿实验之前，我们先确定了三个设计决策：用什么锚定元件把纤维素酶固定到细胞表面、选择哪些纤维素酶 cargo、以及用什么调控方式驱动表达。本节记录这些决策及其依据。

其中第三项——表达调控方式——在后续工程中被两次修订（DBTL B5 中 Ptac-GFP 与 Ptac-Cel9K 两条路线同期将启动子由 J23116 更换为 Ptac-lacO），因此原始决策的理由在此完整记录。

#### Design

**1、Selecting the surface-display anchor**

为了实现纤维素酶在细胞表面的固定，我们需要一个能够穿越大肠杆菌外膜、并把 cargo 展示在膜外的锚定元件。

我们选择 Ice Nucleation Protein（INP）的截短型变体 INPNC 作为外膜锚定元件，采用 iGEM Registry 中的 BBa_K1933011。该元件删除了原有终止密码子，便于与下游 cellulase 序列融合，并包含用于后续蛋白表达检测的 His-tag。相关研究已经报道 INP 衍生锚定系统可用于异源蛋白的细胞表面展示。

与此同时，我们保留了 Lpp-OmpA 等备选锚定方案。

在融合蛋白设计中，我们于 INPNC 上游加入 TorA signal peptide，并在建模组同学的建议下，采用了 `(EAAAK)` 和 `(GGGGS)` 单元组成的混合 linker 设置在INPNC 与 cellulase 之间，以尝试改善蛋白转运、融合蛋白的空间构象及底物可及性。值得注意的是，TorA 与 INPNC 定位机制的兼容性尚未得到实验验证。

**2、Cellulase cargos**

根据 Friskoli 的整体设计，我们希望利用大肠杆菌表面展示系统构建具有纤维素降解潜力的全细胞催化剂，因此 cargo 需要在降解功能与融合表达可行性之间取得平衡。

我们选择来自 *Clostridium thermocellum* 的三种纤维素酶 Cel48S、Cel9K 和 Cel5L。三者分属不同糖苷水解酶家族，在纤维素降解链上承担不同类型的切割功能，理论上互补。

| Cellulase  | GH Family | Catalytic Mode                     | Expected Role in Friskoli                                    |
| ---------- | --------- | ---------------------------------- | ------------------------------------------------------------ |
| **Cel48S** | GH48      | Processive cellobiohydrolase (CBH) | Degrades cellulose from reducing ends and releases cellobiose. |
| **Cel9K**  | GH9       | Processive cellobiohydrolase (CBH) | Degrades cellulose from non-reducing ends and releases cellobiose. |
| **Cel5L**  | GH5_1     | Processive endoglucanase (pEG2)    | Cleaves internal cellulose bonds and releases cellobiose, potentially creating new chain ends. |

考虑到同时表达三个大型融合蛋白可能给单株工程菌造成较大的表达负担，我们决定分别构建三株独立的工程菌，每株菌仅表达一种 cellulase，最终再以 microbial cocktail 的形式组合使用。

在序列层面，我们对三种 cargo 进行了两项改造：

- **删除 dockerin 结构域**：本系统不依赖天然纤维小体的 scaffoldin–dockerin 组装机制，三种纤维素酶中不再需要的 dockerin 结构域被删除，以减少融合蛋白的结构复杂度与分子量；

- **密码子优化**：对拟合成的编码序列进行了适用于大肠杆菌宿主的密码子优化。

**3、 Expression system**

表达调控方式是三个设计决策中影响最深远的一项，因此完整记录其依据。

为了尽量降低大型融合蛋白表达对宿主细胞的潜在负担，我们选用了 Anderson 组成型启动子 J23116（约396 a.u.），并搭配 B0034 RBS。另外一个原因我们考虑到，希望工程菌能够在接触固体纤维素底物之前，预先表达并积累一定数量的表面展示酶，从而在进入反应体系时具备初始催化能力。同时，组成型表达无需额外的诱导步骤，有利于简化系统操作。

## DBTL B1 Building the first INPNC-cellulase surface display system

### Cycle 1｜构建表面展示工程菌

#### Design

为了尽量降低大型融合蛋白表达对宿主细胞的潜在负担，我们选用了 Anderson 组成型启动子 J23116，并搭配 B0034 RBS。

载体采用 pCDF-based plasmid，其具有 CloDF13 replication origin 和 SmR selection marker。

在此基础上，我们设计了三个独立的表面展示表达盒：

| Construct    | Expression cassette                         |
| ------------ | ------------------------------------------- |
| INPNC–Cel48S | J23116–B0034–TorA–INPNC–Linker–Cel48S–B0015 |
| INPNC–Cel9K  | J23116–B0034–TorA–INPNC–Linker–Cel9K–B0015  |
| INPNC–Cel5L  | J23116–B0034–TorA–INPNC–Linker–Cel5L–B0015  |

三个 constructs 共用相同的调控元件、锚定模块及融合策略，主要区别在于 cellulase cargo。

这一设计使我们能够独立构建和测试三种融合蛋白，并为后续比较不同 cargo 与表面展示系统的适配性提供基础。

如果 Gibson assembly 正确完成，并且重组质粒成功进入 MG1655，那么转化后的细胞应当能够在选择平板上形成菌落，并同时表现出正确的 genotype 和 cellulose-degrading phenotype。

---

#### Build

根据上述设计，我们分别准备 pCDF 质粒骨架以及 INPNC、linker、Cel48S、Cel9K 和 Cel5L 等构建所需的 DNA 片段。

通过 PCR 扩增，我们获得了带有预定同源重叠序列的 DNA fragments。

![pCDF-1b–INPNC–CelX Gibson 组装示意图](./images%20of%20wetlabDBTL/pCDF-1b-INPNC-CelX-Gibson-assembly.png)

上图为第一代表面展示质粒的构建策略。通过 Gibson Assembly 将线性化 pCDF-1b 载体、INPNC-Linker 片段及三种纤维素酶编码片段分别组装，构建对应的 INPNC–cellulase 表达质粒。

随后，我们采用 Gibson Assembly 方法，将线性化载体与相应的插入片段进行组装，分别构建：

- pCDF–INPNC–Cel48S
- pCDF–INPNC–Cel9K
- pCDF–INPNC–Cel5L

三个 Gibson Assembly reactions 分别进行，以获得对应的重组质粒候选产物。

将产物转化MG1655大肠杆菌,划线接种于LB+链霉素平板，37℃倒置培养

#### Test

![图片1](./images%20of%20wetlabDBTL/图片1.png)

图1.1-1 三个构建组的链霉素选择平板

为了初步检验构建产物能否用于获得候选工程菌，我们将三个 Gibson Assembly products 分别转化至 *E. coli* MG1655。

转化后，我们将细胞涂布至含链霉素的选择平板上并进行培养。

实验结果显示，三个构建组的选择平板上均观察到了菌落形成。

这一结果最初使我们认为，三个重组质粒可能已经成功导入 MG1655，并获得了潜在的工程菌转化子。

#### Learn

在第一轮工程循环中，我们完成了三种 INPNC–cellulase 表达盒的设计与 Gibson Assembly，并在三个转化实验组中均观察到了候选菌落。

**Do the colonies actually carry functional INPNC–cellulase constructs?**

下一轮工程循环将以这些候选菌落为研究对象，通过 colony PCR 进行基因型验证；在此之后，还将结合 CMC–Congo red assay 检查是否存在可检测的纤维素降解表型。

### Cycle 2｜验证表面展示工程菌菌落的基因型

#### Design

在上一轮构建中，我们将三种 INPNC–cellulase assembly products 分别转化至 MG1655，并在所有实验组的链霉素选择平板上观察到了菌落。

本轮的第一个工程目标是验证这些候选菌落的基因型，即使用 colony PCR 检测目标 INPNC–cellulase DNA 结构是否存在于候选菌落中。

#### Build

我们从上一轮链霉素选择平板中挑取三个构建组的候选单菌落，将对应菌落分别用于 colony PCR 的样品准备。

#### Test

我们使用针对目标表达结构设计的引物，对不同构建组获得的候选菌落进行 colony PCR。

实验结果显示，三个构建组均未获得预期大小的目的条带。

这意味着，我们未能从这些菌落中获得证明目标 INPNC–cellulase constructs 存在的基因型证据。

<img width="484" height="497" alt="image" src="https://github.com/user-attachments/assets/7aa78def-8aa2-4ea5-862b-98a6c0ac68ac" />

图1.2-1 三个构建组候选菌落的 colony PCR 电泳结果

#### Learn

Colony PCR 没有检测到目标 DNA，这使我们开始重新审视上一轮获得的候选菌落是否真正携带目标重组质粒。

不过，这一阴性结果本身有两种可能的解释：一种是候选菌落中确实不含目标 construct，另一种是 colony PCR 出现了技术性假阴性。

为了区分这两种情况，我们决定先跳过菌落这一步，直接检测 Gibson Assembly products 中是否存在预期的 DNA 结构。

### Cycle 3｜质粒 PCR 直接检测组装产物

#### Design

Colony PCR 没有得到预期条带，有两种可能的解释：一种是候选菌落中确实不含目标 construct，另一种是 colony PCR 本身出现了技术性假阴性。为了区分这两种情况，我们决定暂时跳过菌落这一步，直接以三个 Gibson Assembly products 为模板进行 PCR，检验目标 DNA 结构在转化之前是否已经组装成功。

#### Build

我们使用针对目标表达结构设计的引物，分别以 pCDF–INPNC–Cel48S、pCDF–INPNC–Cel9K 和 pCDF–INPNC–Cel5L 的 assembly products 为模板进行 PCR，并将产物进行琼脂糖凝胶电泳。

#### Test

电泳结果显示，三个 assembly products 均获得了预期大小的目的条带。

![质粒PCR](./images%20of%20wetlabDBTL/质粒PCR.png)

图1.3-1 以三个 assembly products 为模板的 PCR 电泳结果

#### Learn

这一结果说明，目标 INPNC–cellulase DNA 结构在 assembly 阶段已经成功组装，此前 colony PCR 的阴性结果并不能归因于组装失败。

因此，问题的关键已经从“DNA 有没有组装成功”转变为“组装好的质粒有没有真正进入并保留在细菌中”。链霉素选择平板上长出的菌落是否真正携带目标质粒，以及原有的抗生素筛选条件是否可靠，都成为下一个需要排查的环节。

在重新评估筛选体系之前，我们还想从功能表型的角度对候选菌株做一次补充验证。

### Cycle 4｜验证候选菌落的纤维素降解表型

#### Design

在 colony PCR 阴性、质粒 PCR 又确认目标 DNA 已经组装成功之后，我们希望进一步从功能表型的角度判断候选菌株是否表现出可检测的纤维素降解活性。

我们采用 CMC–Congo red assay，观察候选菌株能否在 CMC 平板上形成可检测的水解圈。

#### Build

我们将此前挑取的候选单菌落进一步接种至含 CMC 的培养基中培养，用于纤维素酶活性定性检测。

培养完成后，我们对含 CMC 的平板进行刚果红染色及脱色处理，观察菌落周围是否形成纤维素水解区域。

针对第一轮观察到的微弱信号，我们统一实验条件进行了第二轮检测，并增设 MG1655、MG1655-EV 和 DH5α-EV 对照。

#### Test

然而，三个构建组均未观察到预期的清晰水解圈。

![CMC–Congo red assay 第一轮平板](./images%20of%20wetlabDBTL/CMC-round1.png)

图1.4-1 三个构建组候选菌株的 CMC–Congo red assay 结果（第一轮）

此后，我们用标准化条件对该表型检测进行了一次重复，以检验第一轮观察到的弱信号是否可靠。第二轮重复实验中，对照菌株生长良好，而候选工程菌生长较弱，染色后仍未观察到可判读的水解圈。

重复结果显示：对照组生长良好，而工程菌生长明显更弱；染色后背景整体呈红色，仍未形成可判读的清晰水解圈。**第一轮观察到的微弱信号未能在重复实验中得到确认。**

#### Learn

因此，该实验也没有提供能够确认工程菌具有纤维素降解活性的功能证据。

两轮 CMC–Congo red assay 均未获得可重复的纤维素水解表型，未能为候选菌株的纤维素酶活性提供有效证据。

结合此前 colony PCR 的阴性结果，我们仍无法确认这些菌落是否真正携带目标重组质粒。

但是既然已验证目标 DNA 确实已经组装成功，那么我们的下一步问题是：

**Were the colonies on the selection plates genuine transformants at all?**

---

## DBTL B2 Re-evaluating the antibiotic selection system

### Overview

上一轮实验暴露出了一个此前被我们忽略的 assumption：能够在 antibiotic plate 上生长的 colony，并不一定就是目标 transformant。

因此，我们决定重新测试整个 SmR-based selection system，并加入未经 transformation 的 DH5α WT（wild type） 作为 negative control。

我们设置了三种 selection condition：

1. **链霉素平板**：同时涂布工程菌和 WT，判断链霉素能否抑制 WT；

2. **壮观霉素平板**：同时涂布工程菌和 WT，判断壮观霉素能否抑制 WT；

3. **链霉素 + 壮观霉素平板**：同时涂布工程菌和 WT，判断双抗生素组合是否能提高筛选严谨性。

如果 selection system 工作正常，那么，工程菌应当能够生长，WT 应当无法生长。

### Cycle 1｜What does the streptomycin plate alone tell us?

#### Design

链霉素平板是最初 DBTL B1 中使用的 selection condition。

我们首先保留这一条件，观察工程菌和 WT 是否能够形成 colonies。

#### Build

将转入 pCDF-based SmR plasmid 的工程菌和未经 transformation 的 WT 分别涂布于链霉素平板，所有平板在 37℃ 下过夜培养。

#### Test

结果显示，链霉素平板上的工程菌能够形成单菌落，这一结果与 DBTL B1 中观察到的现象一致；但同时，链霉素平板上的野生型菌株也能够形成单菌落。

https://static.igem.wiki/teams/6100/wiki/images-of-wetlab-dbtl/dbtl-b/sd-smr-wt.avif

#### Learn

这一结果与我们的预期明显不符。如果 streptomycin selection 工作正常，那么，工程菌应当生长，WT 应当无法生长，但实际结果是 WT 同样能够生长。

这说明，WT 没有被链霉素有效抑制，streptomycin 单抗生素条件在我们的实验体系中无法可靠区分 WT 与 plasmid-containing cells。

### Cycle 2｜Can spectinomycin provide a more reliable selection condition?

#### Design

为了进一步验证问题是否仅仅来源于第一批 streptomycin plates 或 antibiotic condition，我们重新购买了 spectinomycin，并重新制备 selection plates。

这一轮实验我们保留了 WT negative control。

我们的目标是测试：更换 antibiotic condition 后，是否能够真正建立 WT 与 transformants 之间清晰的生长差异？

#### Build

我们重新进行 transformation，并将工程菌和未经 transformation 的 WT 分别涂布于新的 spectinomycin-containing plates，所有平板在 37℃ 下过夜培养。

#### Test

结果显示，壮观霉素平板上，工程菌能够形成 colonies；同时，DH5α WT 也能够在壮观霉素平板上形成 colonies。

https://static.igem.wiki/teams/6100/wiki/images-of-wetlab-dbtl/dbtl-b/sd-spcr-wt.avif

#### Learn

这一结果与我们的预期明显不符。如果 spectinomycin selection 工作正常，那么工程菌应当生长，WT 应当无法生长，但实际结果是 WT 同样能够生长。

这说明，WT 没有被壮观霉素有效抑制，spectinomycin 单抗生素条件在我们的实验体系中无法可靠区分 WT 与 plasmid-containing cells。

### Cycle 3｜Does combined streptomycin + spectinomycin selection improve stringency?

#### Design

由于壮观霉素单药不能抑制 WT，我们进一步测试双抗生素组合是否能够提高 selection stringency。

我们使用链霉素 + 壮观霉素双抗生素平板同时涂布：

- 工程菌

- 未经 transformation 的 WT

如果双药组合能够抑制 WT，而工程菌仍然生长，则说明双药 selection 可能比单药更可靠。

如果 WT 仍然生长，则说明 SmR-based selection system 整体无法承担筛选 transformants 的功能。

#### Build

我们重新制备链霉素 + 壮观霉素双药平板。

随后将工程菌和  WT 分别涂布于双药平板上，所有组在 37℃ 培养条件下过夜培养。

#### Test

结果显示，链霉素 + 壮观霉素双抗平板上，工程菌能够形成 colonies；同时，DH5α WT 也能够在链霉素 + 壮观霉素双抗平板上形成 colonies。

https://static.igem.wiki/teams/6100/wiki/images-of-wetlab-dbtl/dbtl-b/sd-smr-spcr.avif

#### Learn

连续三种 selection condition 的结果可以总结为：

| Selection condition | 工程菌        | WT         |
| ------------------- | ---------- | ---------- |
| 链霉素平板               | 有 colonies | 有 colonies |
| 壮观霉素平板              | 有 colonies | 有 colonies |
| 链霉素 + 壮观霉素平板        | 有 colonies | 有 colonies |

我们能够从中提取的关键信息是：WT 在壮观霉素单药和链霉素 + 壮观霉素双药条件下都能够生长。

这说明问题并不是简单地由某一种 antibiotic 或某一个浓度条件造成。

至少在本实验体系中：

spectinomycin 单药不能抑制 WT；

streptomycin + spectinomycin 双药也不能抑制 WT；

因此 SmR-based selection 无法可靠地区分 WT 与 transformants，所以在下一轮中，我们需要重新设置 selection condition，丢弃 SmR-based selection。

## DBTL B3 Rebuilding the system with an independent selection strategy

### Cycle 1｜pACYC-based backbone组装

### Design

上一轮实验表明，原有的SmR抗性基因筛选体系无法可靠区分候选转化子与未转化细胞。我们更换了 plasmid backbone 和 antibiotic resistance marker。

新的载体采用 pACYC-based backbone，具有 p15A-family replication origin，并使用 chloramphenicol resistance marker。

我们通过这一轮的改变，建立了三个具有不同诊断意义的 control levels：

| 菌株类型                   | 构建目的                                                     |
| -------------------------- | ------------------------------------------------------------ |
| WT                         | **chloramphenicol selection 能否有效抑制没有 resistance plasmid 的 cells？** |
| EV — Empty Vector          | **MG1655 是否能够接受并维持新的 plasmid backbone？**         |
| INPNC-cellulase constructs | **在 vector backbone、transformation 和 selection 均能够正常工作的情况下，加入目标 surface-display expression cassette 后是否仍能够获得 transformants？** |

这一组 controls 使我们能够更加系统地定位 failure。

---

### Build

我们重新设计引物，利用 PCR 和 Gibson Assembly，在 pACYCDuet-1b 载体上分别构建了三个由 J23116 驱动的 INPNC–cellulase 表达质粒。

三个 pACYC 重建质粒的构建策略如下。三者共用同一线性化骨架与 INPNC-Linker 锚定模块，**启动子也完全相同**，仅 cargo 不同。

![pACYCDuet-1–INPNC–Cel5L Gibson 组装示意图](./images%20of%20wetlabDBTL/pACYCDuet-1-Cel5L-Gibson-assembly.png)

图3-构1 *pACYC–INPNC–Cel5L 的 Gibson Assembly 构建策略*

![pACYCDuet-1–INPNC–Cel48S Gibson 组装示意图](./images%20of%20wetlabDBTL/pACYCDuet-1-Cel48S-Gibson-assembly.png)

图3-构2*pACYC–INPNC–Cel48S 的 Gibson Assembly 构建策略*。

![pACYCDuet-1–J23116–INPNC–Cel9K Gibson 组装示意图](./images%20of%20wetlabDBTL/pACYCDuet-1-Cel9K-J23116-Gibson-assembly.png)

图3-构3 *pACYC–INPNC–Cel9K 的 Gibson Assembly 构建策略*。

随后，我们将三个 Gibson Assembly products 分别转化至 MG1655，并设置 WT 和 EV 对照，使用氯霉素平板进行筛选。

#### Test

片段扩增与组装过程以凝胶电泳跟踪：

![0924-pACYC-R1](./images%20of%20wetlabDBTL/0924-pACYC-R1.png)

图3.1-1 一轮 PCR 电泳



实验结果首先在两个 control groups 中表现出了非常清晰的差异。

##### WT没有观察到 colony growth。Empty Vector能够获得 colonies。

---

#### Learn

WT 无法在 chloramphenicol plate 上生长，说明新的 antibiotic selection 能够有效抑制没有 resistance plasmid 的 MG1655。

Empty-vector transformants 能够形成 colonies，则说明MG1655 可以接受并维持 pACYC-based plasmid。

但是我们的三个 recombinant groups 均没有获得预期 colonies。问题开始集中到 experimental groups 与 EV 之间最大的区别：**INPNC-cellulase expression cassette。**

但是，在得出 expression burden 或 toxicity 的结论之前，我们仍然需要排除一种更加简单的可能性：三个 recombinant constructs 是否只是再次发生了 assembly failure？因此，我们进一步检测新的 assembly products。

---

### Cycle 2｜Did the recombinant assemblies fail again?

#### Design

如果三个 INPNC-cellulase Gibson assemblies 全部失败，那么 experimental groups 没有 colonies 仍然可以由 cloning failure 解释。

因此，我们再次直接检测 assembly products。

---

#### Test

以三个 assembly products 为 PCR templates，可以分别获得预期大小的 expression-cassette bands。

![pACYCD-assembly](./images%20of%20wetlabDBTL/pACYCD-assembly.png)

图3.3-1 以三个新 assembly products 为模板的 PCR 电泳结果

目标 structures 在 transformation 前的 assembly mixtures 中仍然可以被检测到。三个gibson构建组均获得了预期大小的 PCR 条带。

---

#### Learn

PCR 结果表明，组装反应中存在可扩增的目标表达盒结构，至少我们的组装是有完整重组质粒的产生的。

我们的指导老师Tim老师给我们提出建议，他建议我们可以用已知的较小分子量蛋白测试我们的组装方案本身会不会造成抗性基因的失效。

同时我们查阅文献也发现，表面展示系统大多数的表达方式都是诱导型，组成型表达方式是未经验证的表面展示蛋白表达方式，也有可能会造成宿主毒性从而导致转化失败。

因此，下一轮将组成型启动子尝试调整为诱导型启动子控制表达，并且使用GFP测试我们的组装流程是否会存在破坏质粒抗性基因的问题。

---

## DBTL B5 Testing an inducible architecture with a GFP reporter

### Overview

为了验证我们的猜想。即由组成型表达方式 J23116有可能会造成宿主毒性从而导致转化失败。我们将其更换为可诱导的 **Ptac-lacO**。如果负担与组成型持续高表达有关，诱导型表达可以把目标蛋白的表达限定在特定时段，降低宿主压力；

cargo 暂时以 **GFP** 作为小分子量报告 cargo，先单独验证测试我们的组装方案本身会不会造成抗性基因的失效，再回到大型纤维素酶。

### Cycle 1｜Redesigning the expression architecture

#### Design

我们将两个 constructs 置于相同的 **Ptac-lacO inducible architecture** 下，但使用不同 cargo。

| Construct            | Cargo       | Purpose                                                      |
| -------------------- | ----------- | ------------------------------------------------------------ |
| **Ptac-GFP**         | GFP         | 测试新的载体与组装架构是否能够获得稳定转化子                 |
| **Ptac-INPNC-Cel9K** | INPNC-Cel9K | 测试降低转化阶段的持续表达后，大型表面展示融合蛋白能否被宿主接受 |

如果两个 constructs 均能够获得克隆，则说明诱导型调控可能缓解了此前的构建问题。

#### Build

我们在 pACYCDuet-1 骨架上重新构建诱导型表达系统，并以 **GFP** 作为报告 cargo。通过 PCR 分别获得带有 **Ptac-lacO 调控区域、GFP 表达盒及 rrnB T1 terminator** 的目标片段和线性化载体骨架，随后利用 Gibson Assembly 完成 **pACYC-Ptac-GFP** 的组装。

![pACYCD-GFP Gibson 组装示意图](./images%20of%20wetlabDBTL/pACYCD-GFP-Gibson-assembly.png)

图5-构1 DBTL B5 报告系统的构建策略

与 GFP 报告系统同时进行的是，我们还用同一启动子策略，回到纤维素酶 cargo，构建了 pACYCDuet-1–Ptac–INPNC–Cel9K：

![pACYCDuet-1–Ptac–INPNC–Cel9K Gibson 组装示意图](./images%20of%20wetlabDBTL/pACYCDuet-1-Cel9K-Gibson-assembly.png)

图5-构2 pACYCDuet-1–Ptac–INPNC–Cel9K（7290 bp）的构建策略

#### Test

GFP 片段的扩增于 2026 年 9 月底至 10 月初分多轮完成，各轮产物均以凝胶电泳确认。

![1002-GFP-R1](./images%20of%20wetlabDBTL/1002-GFP-R1.png)

图5.1-1 GFP PCR 第一轮

![1003-GFP-R2](./images%20of%20wetlabDBTL/1003-GFP-R2.png)

图5.1-2 pACYCDuet第一轮和GFP第二轮

![1003-GFP-pACYCD-R2](./images%20of%20wetlabDBTL/1003-GFP-pACYCD-R2.png)

图5.1-3 pACYCD 第二轮 PCR

通过PCR成功得到各条带之后我们进行gibson assembly。将重组产物转化至 *E. coli* MG1655，并在未加入诱导剂的条件下筛选转化子。

![pACYC-GFP-Colony](./images%20of%20wetlabDBTL/pACYC-GFP-Colony.png)

pACYC-Ptac-GFP平板得到了单个候选克隆

![B5-Ptac-Cel9K](./images%20of%20wetlabDBTL/B5-Ptac-Cel9K.png)

pACYC-Ptac-GFP平板没有得到克隆

#### Learn

在相同的 Ptac-lacO 调控背景下，GFP 构建能够获得候选克隆，而 Ptac-INPNC-Cel9K 仍未获得转化子。

这一结果说明，**仅将 J23116 更换为诱导型 Ptac-lacO 并不足以恢复 INPNC-Cel9K 构建**。因此，此前的失败不能简单归因于组成型表达方式。

与此同时，GFP 构建能够形成 colony，提示新的 pACYC-based assembly architecture 至少具有获得重组转化子的可能性。为了确认该 colony 是否真正携带正确的 GFP construct，而不是筛选过程中产生的假阳性，我们在下一轮对其进行 colony PCR 验证。

### Cycle 2｜对GFPcolony验证插入情况

#### Design

片段扩增之后，需要回到与 B1–B3 相同的诊断逻辑：**先证明构建存在，再讨论表达**。我们以菌落 PCR 验证 GFP 构建是否真正进入并保留在细菌中。

#### Build

将 pACYCD-GFP平板上的菌株挑取单菌落进行菌落 PCR。

#### Test

![1006-GFP-colony](./images%20of%20wetlabDBTL/1006-GFP-colony.png)

图5.2-2 MG1655菌落 GFP PCR

#### Learn

Colony PCR 进一步确认，Ptac-GFP 候选菌落确实携带正确的重组 construct。该结果说明，在当前 **pACYC-based backbone、chloramphenicol selection 和 Gibson Assembly strategy** 下，目标重组质粒可以被正确组装、转化并稳定保留，因此此前 INPNC-cellulase 构建连续失败不能简单归因于组装流程或抗性基因失效。

与此同时，**Ptac-GFP 可以获得正确转化子，而采用相同诱导型调控策略的 Ptac-INPNC-Cel9K 仍未获得 colony**。这说明，将 J23116 更换为 Ptac-lacO 并不足以解决 INPNC-cellulase 构建失败的问题，限制因素更可能与具体的 surface-display fusion architecture 有关。

在与中国科学院深圳先进技术研究院的易啸老师的 Human Practices 访谈中，我们进一步了解到，不同surface-display anchor 与 不同的passenger protein 之间的适配性不同。对于我们的纤维素酶来说，INPNC并一定是最优锚定系统，他建议我们多测试不同的表面展示系统和纤维素酶的组合，并且与我们分享了他的经验，即Lpp-OmpA系统的鲁棒性比较强，有可能更好兼容我们的纤维素酶。因此，我们下一轮的设计中引入另一种经典外膜展示系统 **Lpp-OmpA**，重新测试其与 cellulase cargo 的兼容性。

## DBTL B6 Redesigning the surface-display system with Lpp-OmpA

### Design

本轮我们参考HP访谈的建议，将设计修改如下：**保持诱导型表达策略和 pACYC-based backbone 不变，将表面展示锚定模块由 INPNC 更换为 Lpp-OmpA。**这样的设计我们考虑到可以尽量减少同时改变的变量，以便我们能够更直接地比较不同 anchor 与 cellulase cargo 的适配性。

我们设计了以下两个候选 constructs：

| Construct                | Planned expression cassette                        |
| ------------------------ | -------------------------------------------------- |
| **Ptac-Lpp-OmpA-Cel9K**  | Ptac-lacO–RBS–Lpp-OmpA–6×His–Linker–Cel9K–rrnB T1  |
| **Ptac-Lpp-OmpA-Cel48S** | Ptac-lacO–RBS–Lpp-OmpA–6×His–Linker–Cel48S–rrnB T1 |

构建策略采用三个 PCR fragments 进行 Gibson Assembly：

1. **Linearised pACYCDuet-1 backbone**：保留 p15A ori、CmR 和 lacI，并在连接区域引入 Ptac-lacO 相关序列；
2. **Lpp-OmpA–6×His–Linker fragment**：作为新的 surface-display anchor；
3. **Cellulase–terminator fragment**：分别使用 Cel9K 或 Cel48S，并保留 rrnB T1 terminator。

![image-20261020181107154](./images%20of%20wetlabDBTL/image-20261020181107154.png)

*Construction of pACYCDuet-1–Ptac–Lpp-OmpA–Cel9K.*

![image-20261020181135192](./images%20of%20wetlabDBTL/image-20261020181135192.png)

*Construction of pACYCDuet-1–Ptac–Lpp-OmpA–Cel48S.*

![image-20261020181252560](./images%20of%20wetlabDBTL/image-20261020181252560.png)

*Construction of pACYCDuet-1–Ptac–Lpp-OmpA–Cel5L.*

如果该设计能够在后续实验中获得稳定转化子，将进一步支持 **anchor-cargo compatibility** 是此前 INPNC-cellulase 构建失败的重要影响因素；如果仍然无法获得转化子，则需要继续考虑 cellulase cargo 本身、融合蛋白整体负担或其他结构因素。

由于项目进入 Wiki 提交前的最后阶段，本轮设计尚未在截止前完成实际构建和实验验证。
