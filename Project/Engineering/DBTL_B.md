# 路线 B 表面展示系统工程 DBTL 

## Overview

为了使工程菌能够直接作用于固体纤维素底物，我们设计了基于 INPNC 的细胞表面展示系统，并计划分别将 Cel5L、Cel9K 和 Cel48S 展示于三株工程菌表面。

整个构建过程主要经历了六个阶段。

**DBTL B0** 聚焦于表面展示表达系统的设计决策——锚定元件、纤维素酶 cargo 与表达调控方式的选择。

**DBTL B1** 聚焦于第一代表面展示系统的构建与验证。我们尝试使用 pCDF-based vector 构建三种 INPNC-cellulase 质粒，并通过基因型和功能表型两种方式判断工程菌是否构建成功。在 colony PCR 未获得阳性结果后，我们进一步对 assembly products 进行质粒 PCR，确认目标 DNA 结构已经成功组装，从而将问题指向转化与筛选环节。

**DBTL B2** 聚焦于抗生素筛选体系。由于第一轮实验中出现了“选择平板有菌落，但无法验证目标构建”的矛盾现象，我们加入 WT 对照，并重新评估原有 SmR-based selection 是否能够真正筛选出转化子。

**DBTL B3** 聚焦于重新建立可靠的转化与筛选体系。我们更换为 pACYC-based chloramphenicol selection system，并通过 WT、empty vector 和三个 INPNC-cellulase constructs 的对照逐步判断问题发生在哪一个环节。

**DBTL B4** 聚焦于重新设计表面展示架构。在前三轮把问题收窄到表达架构之后，我们提出下一轮必须主动改变表达结构，而不是重复原来的 cloning procedure，并给出两个方向：拆分 construct 定位负担来源，以及比较备选锚定元件。

**DBTL B5** 沿着同一假设实施了互补的两项改变：将组成型启动子 J23116 更换为可诱导的 Ptac-lacO，并以 GFP 作为小分子量报告 cargo 先单独验证展示系统本身；同一启动子策略也同期延伸至 Cel9K（Ptac-Cel9K）。

这些连续的 DBTL cycles 使我们逐渐将问题从笼统的“质粒构建失败”，缩小到目标表面展示表达结构本身可能带来的细胞负担；而 B4 / B5 进一步把问题转变为“在改变表达结构的前提下，细胞能否接受表面展示系统”。

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

目标 structures 在 transformation 前的 assembly mixtures 中仍然可以被检测到。

---

#### Learn

这一结果与前面所有 controls 结合后，使 failure 的范围进一步缩小。

目前我们已经观察到：

**WT + chloramphenicol**

→ no growth

说明 selection 有效。

**Empty pACYC + chloramphenicol**

→ colonies

说明 host、transformation 和 backbone 可以工作。

**pACYC + INPNC-cellulase**

→ no colonies

说明 failure 与目标 construct 的加入相关。

与此同时：

**assembly-product PCR**

→ expected bands

说明目标 DNA arrangement 至少存在于 assembly reaction 中。

当然，assembly PCR 仍然不能严格证明最终已经形成完整、无突变、可复制的 circular recombinant plasmid。

因此，我们还不能单凭这些结果宣称：

**INPNC expression definitely causes toxicity。**

但是，与最开始相比，问题已经被明显缩小。

三个不同的 cellulase constructs 都出现相似 failure，而它们共享非常相似的：

- promoter/RBS architecture；
- INPNC membrane-display module；
- fusion strategy；
- expression architecture。

因此，一个比“连续三个独立 cloning failure”更加值得下一轮测试的共同假设是：

> **the shared INPNC-cellulase expression architecture may impose a strong cellular burden, potentially related to membrane-protein expression or fusion-protein toxicity.**

我们的工程问题由此发生改变。

最初的问题是：

> **Why can we not obtain the correct plasmid?**

现在的问题变成了：

> **Can the cells tolerate our current surface-display architecture?**

---

## DBTL B4 Redesigning the surface-display architecture

### Design

经过前三轮 DBTL，我们认为继续简单重复相同的 transformation 已经无法带来更多信息。

如果 failure 确实与 expression burden 有关，那么下一轮设计必须主动改变表达结构，而不是重复原来的 cloning procedure。

因此，下一步将围绕两个问题展开：

#### Which component causes the burden?

可以进一步拆分完整 construct，例如分别测试：

- INPNC-only；
- cellulase without INPNC display；
- complete INPNC-cellulase fusion。

通过比较这些 constructs 的 transformation 和 growth phenotype，可以进一步判断 failure 更可能来自：

**INPNC membrane localization**

还是

**cellulase expression**

还是

**the complete fusion architecture。**

#### Can another surface-display platform improve host tolerance?

INPNC 并不是唯一可能的 outer-membrane display strategy。

因此，我们计划进一步比较其他 surface-display anchors，例如 Lpp-OmpA。

如果 alternative anchor 能够稳定获得 transformants，则可以进一步验证：

**surface-display scaffold selection itself may be one of the key design variables。**

---

## DBTL B5 Testing an inducible architecture with a GFP reporter

### Overview

DBTL B3 结束时，证据链已经收窄为一个清晰的模式：

- WT + chloramphenicol → no growth（selection 有效）；
- empty pACYC + chloramphenicol → colonies（宿主可转化、骨架可维持）；
- pACYC + INPNC-cellulase → no colonies（failure 与目标 construct 的加入相关）；
- assembly-product PCR → expected bands（目标 DNA arrangement 存在于 assembly mixture 中）。

DBTL B4 据此提出：下一轮设计必须主动改变表达结构，而不是重复原来的 cloning procedure，并给出两个方向——拆分 construct 定位负担来源，以及比较备选锚定元件。

本轮（B5）沿着同一假设实施了互补的两项改变：

1. **启动子类型**：由组成型 J23116 更换为可诱导的 **Ptac-lacO**。如果负担与组成型持续高表达有关，诱导型表达可以把目标蛋白的表达限定在特定时段，降低宿主压力；
2. **cargo 大小**：以 **GFP** 作为小分子量报告 cargo，先单独验证“锚定 + 展示”系统本身，再回到大型纤维素酶。

这一组合同时覆盖了 B4 拆分实验的两端：GFP–INPNC 既是“小 cargo + 锚定模块”的拆分测试，也是诱导型启动子的承载平台。

由此，本轮的工程问题变为：

> **在诱导型表达 + 小分子量 cargo 的条件下，表面展示系统能否被细胞接受？**

### Cycle 1｜Redesigning the expression architecture: inducible promoter and GFP cargo

#### Design

本轮同时改变两个变量，使它们各自的作用可以在后续实验中被区分：

| 变量 | 第一代（DBTL B1） | 本轮（DBTL B5） |
| --- | --- | --- |
| 启动子 | 组成型 J23116 | 诱导型 Ptac-lacO |
| cargo | Cel48S / Cel9K / Cel5L（1.4–3 kb 大型酶） | GFP（小分子量报告蛋白） |
| 载体 | pCDF-1b（CloDF13 / SmR，已弃用） | pACYCDuet-1b（p15A / CmR） |

我们据此设计了两条互补的构建路线：

- **pACYCD-GFP（promoter swap 路线）**：保留 pACYCDuet-1b 骨架，将 GFP 置于 Ptac-lacO 调控之下，作为整个 redesign 的“探针”；
- **pACYCDuet-1–Ptac–INPNC–CelX（cellulase 路线）**：同一启动子策略延伸回纤维素酶，与 GFP 系统共用线性化骨架与组装策略。其中 **Cel9K 的 Ptac 变体已与 Ptac-GFP 同期构建**（见下文 Build）；Cel5L / Cel48S 的 Ptac 变体则待 GFP 路线给出明确信号后再行推进。

两条路线给出互补的判读：如果 GFP 路线能够稳定获得转化子，则说明锚定与转运模块可以工作，问题更可能集中在大型 cellulase cargo 本身；如果 GFP 同样无法获得转化子，则负担来源将指向 INPNC 膜定位或更上游的环节。

启动子更换并非简单“换个元件”，而是针对 DBTL B3 证据链所指向的负担假设的正面回应：

- **Ptac 的性质**：Ptac 为 trp 启动子 −35 区与 lacUV5 启动子 −10 区/operator 的杂合启动子（de Boer et al., 1983, PNAS），表达受 LacI 阻遏蛋白抑制、可被 IPTG 诱导，且表达量随 IPTG 浓度在数个数量级内可调；其强度约为天然 lac 的 2–3 倍、T7 系统的 1/3–1/5，属于中等强度。对本模块而言，可诱导性比绝对强度更重要。
- **膜蛋白过表达的毒性机制**：文献中，膜蛋白（或分泌途径蛋白）过量表达的毒性主要源于 Sec translocon 饱和——分泌途径前体在细胞质中聚集、内源膜蛋白（包括呼吸链复合物）被竞争性排除、包膜完整性与能量代谢受损；且毒性与“每细胞过表达物质量”正相关，而与蛋白种类关系不大（Wagner et al., 2007, Mol Cell Proteomics；Wagner et al., 2008, PNAS）。因此，**降低并可控化表达量**本身就是对膜定位展示系统最直接的减负手段。
- **时间解耦**：可诱导性还把“生长”与“产蛋白”在时间上解耦——细胞先长至足够密度，再承受展示结构的负担，这正是组成型 J23116 无法做到的。

需要同时记录的限定：Ptac 存在泄漏表达（leaky expression），未加 IPTG 时仍有基础转录；若目标结构毒性强，后续可配合高拷贝 lacIq 菌株或 lacI 共表达进一步压低关闭态。

#### Build

按照设计，我们先在 SnapGene 中完成表达盒搭建与引物设计，再进行 PCR 扩增与 Gibson 组装。

GFP 路线采用**两条分支、四轮 PCR**的策略：

- **GFP 分支**：以 GFP 质粒（模板 2766 bp）为模板，PCR ①（GFP-F + GFP-R）获得 818 bp 的第一轮产物；由于模板没有完美引物，再以 PCR ②（GFP-Overlap-F/R）在两端分别接上 LacO-RBS（5′ 端）与 rrnB T1（3′ 端，与 Cel 系列相同）及同源臂，获得 Fragment A（878 bp）；
- **载体分支**：以 pACYCDuet-1b 为模板，PCR ① 反向 PCR 线性化（pACYCD-F1 + pACYCD-Overlap-R1，去除 LacO 区，3′ 端保留部分 Ptac 序列与同源臂），获得 3679 bp 线性化骨架；PCR ②（pACYCD-Overlap-F1/R1）在 5′ 端补齐 rrnB T1 另一半序列与同源臂，获得 Fragment B（3746 bp）。

两条分支的产物等摩尔混合，以 5 μL 2× CE Mix V3、ddH2O 补至 10 μL、37 ℃ 反应 30 min 的条件下进行 Gibson Assembly，获得 4586 bp 的环状 pACYCD-GFP。

![pACYCD-GFP Gibson 组装示意图](./images%20of%20wetlabDBTL/pACYCD-GFP-Gibson-assembly.png)

图5-构1 DBTL B5 报告系统的构建策略：两条分支、四轮 PCR。GFP 分支经两轮 PCR 获得带同源臂的 GFP 表达盒 Fragment A（878 bp，5′ 端换为 LacO-RBS、3′ 端换为 rrnB T1）；载体分支经反向 PCR 线性化 + 第二轮补齐，获得 Fragment B（3746 bp）。两片段等摩尔组装为 4586 bp 的 pACYCD-GFP，图中红色末端为引物引入的 18–20 bp 同源臂。

与 GFP 报告系统同期，我们还用同一启动子策略延伸回纤维素酶 cargo，构建了 pACYCDuet-1–Ptac–INPNC–Cel9K：

![pACYCDuet-1–Ptac–INPNC–Cel9K Gibson 组装示意图](./images%20of%20wetlabDBTL/pACYCDuet-1-Cel9K-Gibson-assembly.png)

图5-构2 pACYCDuet-1–Ptac–INPNC–Cel9K（7290 bp）的构建策略：与 GFP 系统共用反向 PCR 线性化骨架（3679 bp，LacO 区去除、Ptac 由引物引入）与 INPNC-Linker 片段（1126 bp，两轮 PCR 获得），第三片段为 Cel9K-Ter（2537 bp），三片段等摩尔一步组装。Ptac 受骨架上 lacI 编码的阻遏蛋白抑制，可用 IPTG 诱导。该构建与 Ptac-GFP 同期完成；转化后平板上未长出菌落（未获转化子，Cycle 11 记录），尚未获得生物学验证。

#### Test

GFP 片段的扩增于 2026 年 9 月底至 10 月初分多轮完成，各轮产物均以凝胶电泳确认。

![](E:\Wet-lab\Git\1002-GFP-R1.png)

图5.1-1 GFP PCR 第一轮

![](E:\Wet-lab\Git\1003-GFP-R2.png)

图5.1-2 pACYCDuet第一轮和GFP第二轮

![](E:\Wet-lab\Git\1003-GFP-pACYCD-R2.png)

图5.1-3 pACYCD 第二轮 PCR

#### Learn

多轮 PCR 与两轮补接同源臂的策略，与第一代构建中解决重复区段非特异扩增的方法（SDX-05）一脉相承：**当模板或引物不理想时，用两轮 PCR 逐步补齐序列与同源臂，比一次性设计长引物更可靠**。这一经验随后被写入引物设计流程（P09）。

需要说明的是，本轮各凝胶的逐泳道判读（哪些泳道为预期大小的目的条带）尚未在原始记录中标注，正式发布前需核对后补充 [待确认]。

### Cycle 2｜Verifying the GFP constructs at the colony level

#### Design

片段扩增之后，需要回到与 B1–B3 相同的诊断逻辑：**先证明构建存在，再讨论表达**。我们以菌落 PCR 验证 GFP 构建是否真正进入并保留在细菌中。

#### Build

将 pACYCD-GFP 组装产物转化至克隆宿主（DH5α）与出发宿主（MG1655），挑取单菌落进行菌落 PCR。

#### Test

![](E:\Wet-lab\Git\1003-DH5a-GFP-colony.png)

图5.2-1 DH5α-GFP 菌落 PCR

![](E:\Wet-lab\Git\1006-GFP-colony.png)

图5.2-2 MG1655菌落 GFP PCR

#### Learn

至此，GFP 报告系列的**构建与菌落级验证已经开展**（2026.9.29–10.6）。但从证据链的角度，本轮尚未闭合：

1. **菌落 PCR 的判读待确认**——各泳道是否出现预期条带、哪些菌落被判定为阳性，需核对原始记录后才能写入结论；
2. **功能验证尚未开展**——GFP 路线更直接的价值在于报告“展示是否发生”（荧光观察 / 表面定位检测），该部分尚无记录；
3. **与 B4 拆分计划的关系待理顺**——GFP–INPNC 本质上是 B4 拆分实验（INPNC-only / cellulase-only / 完整融合）的一个实例，两条线应在下一轮合并呈现；
4. **测序闭环仍未完成**——与 B3 结束时相同，assembly PCR 与菌落 PCR 均不能替代 Sanger 测序（P11），该闭环在本模块始终未完成。

因此，本轮结束时我们的工程问题再次发生转变：

> 由“细胞能否耐受组成型高表达的表面展示结构”，变为“**在诱导型表达 + 小分子量 cargo 的条件下，表面展示系统能否被细胞接受？**”

而回答这个问题，需要把 B5 的初步结果与 B4 的拆分实验（INPNC-only、cellulase-only、完整融合）合并到下一个 DBTL cycle 中系统推进。

---

> 注：本文图片存放于 `images of wetlabDBTL/` 目录，正式发布时需上传至 static.igem.wiki 并将本地路径替换为对应 URL。
