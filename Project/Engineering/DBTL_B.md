# 路线 B 表面展示系统湿实验工程 DBTL 草稿

## Overview

为了使工程菌能够直接作用于固体纤维素底物，我们设计了基于 INPNC 的细胞表面展示系统，并计划分别将 Cel5L、Cel9K 和 Cel48S 展示于三株工程菌表面。

整个构建过程主要经历了三个阶段。

**DBTL B1** 聚焦于第一代表面展示系统的构建与验证。我们尝试使用 pCDF-based vector 构建三种 INPNC-cellulase 质粒，并通过基因型和功能表型两种方式判断工程菌是否构建成功。

**DBTL B2** 聚焦于抗生素筛选体系。由于第一轮实验中出现了“选择平板有菌落，但无法验证目标构建”的矛盾现象，我们加入 WT 对照，并重新评估原有 SmR-based selection 是否能够真正筛选出转化子。

**DBTL B3** 聚焦于重新建立可靠的转化与筛选体系。我们更换为 pACYC-based chloramphenicol selection system，并通过 WT、empty vector 和三个 INPNC-cellulase constructs 的对照逐步判断问题发生在哪一个环节。

这些连续的 DBTL cycles 使我们逐渐将问题从笼统的“质粒构建失败”，缩小到目标表面展示表达结构本身可能带来的细胞负担。

---

## DBTL B1 Building the first INPNC-cellulase surface display system

### Overview

### Cycle 1｜构建表面展示工程菌

### Design

#### 1. Establishing the first-generation surface display architecture

根据 Friskoli 的整体设计，我们希望利用大肠杆菌表面展示系统构建具有纤维素降解潜力的全细胞催化剂。

在第一轮工程循环中，我们的主要任务是选择合适的表面锚定元件和纤维素酶，并将其整合为能够在 *E. coli* MG1655 中表达的融合蛋白系统。

我们选择来自 *Clostridium thermocellum* 的三种纤维素酶 Cel48S、Cel9K 和 Cel5L，分别承担不同类型的纤维素降解功能。

考虑到同时表达三个大型融合蛋白可能给单株工程菌造成较大的表达负担，我们决定采用模块化构建策略：分别构建三株独立的工程菌，每株菌仅表达一种 cellulase，最终再以 microbial cocktail 的形式组合使用。

#### 2. Selection of the INPNC anchor

为了实现纤维素酶在细胞表面的固定，我们选择 Ice Nucleation Protein（INP）的截短型变体 INPNC 作为外膜锚定元件。

我们采用 iGEM Registry 中的 BBa_K1933011。该元件删除了原有终止密码子，便于与下游 cellulase 序列融合，并包含用于后续蛋白表达检测的 His-tag。

相关研究已经报道 INP 衍生锚定系统可用于异源蛋白的细胞表面展示，因此我们将 INPNC 作为第一代融合结构的基础。

#### 3. Engineering the fusion protein

为了适配 INPNC 融合表达结构，我们对三种 cellulase cargo 进行了相应的序列设计。

首先，由于本系统不依赖天然纤维小体的 scaffoldin–dockerin 组装机制，我们删除了三种纤维素酶中不再需要的 dockerin 结构域，以减少融合蛋白的结构复杂度。

其次，我们在 INPNC 与 cellulase 之间设计了由刚性 `(EAAAK)` 和柔性 `(GGGGS)` 单元组成的混合 linker，希望提供适当的空间距离及构象自由度，降低融合对纤维素酶折叠和底物接近的潜在影响。

同时，我们在 INPNC 上游加入 TorA signal peptide，尝试辅助融合蛋白转运。该设计是否能够与 INPNC 的定位机制兼容，仍需后续实验确认。

在 DNA 序列设计阶段，我们还对拟合成的编码序列进行了适用于大肠杆菌宿主的密码子优化。

#### 4. Designing the expression system

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

第一代载体采用 pCDF-based plasmid。该载体具有 CloDF replication origin，并携带 SmR selection marker。

如果 Gibson assembly 正确完成，并且重组质粒成功进入 MG1655，那么转化后的细胞应当能够在选择平板上形成菌落，并同时表现出正确的 genotype 和 cellulose-degrading phenotype。

---

### Build

根据上述设计，我们分别准备 pCDF 质粒骨架以及 INPNC、linker、Cel48S、Cel9K 和 Cel5L 等构建所需的 DNA 片段。

通过 PCR 扩增，我们获得了带有预定同源重叠序列的 DNA fragments。

随后，我们采用 Gibson Assembly 方法，将线性化载体与相应的插入片段进行组装，分别构建：

- pCDF–INPNC–Cel48S
- pCDF–INPNC–Cel9K
- pCDF–INPNC–Cel5L

三个 Gibson Assembly reactions 分别进行，以获得对应的重组质粒候选产物。

此时，我们获得的是用于后续转化的 assembly mixtures，尚未通过测序确认其中是否存在完整且正确的环状重组质粒。

### Test 

![图片1](./images%20of%20wetlabDBTL/图片1.png)

为了初步检验构建产物能否用于获得候选工程菌，我们将三个 Gibson Assembly products 分别转化至 *E. coli* MG1655。

转化后，我们将细胞涂布至含链霉素的选择平板上并进行培养。

**实验结果显示，三个构建组的选择平板上均观察到了菌落形成。**

这一结果最初使我们认为，三个重组质粒可能已经成功导入 MG1655，并获得了潜在的工程菌转化子。

然而，抗生素选择平板上的 colony formation 仅能证明相应实验组在该培养条件下出现了细胞生长，尚不能确认菌落是否真正携带目标 INPNC–cellulase construct。

### Learn

在第一轮工程循环中，我们完成了三种 INPNC–cellulase 表达盒的设计与 Gibson Assembly，并在三个转化实验组中均观察到了候选菌落。

**Do the colonies actually carry functional INPNC–cellulase constructs?**

下一轮工程循环将以这些候选菌落为研究对象，通过 colony PCR 进行基因型验证，并结合 CMC–Congo red assay 检查是否存在可检测的纤维素降解表型。

### Cycle 2｜验证表面展示工程菌菌落的基因型和功能表型

## Design

在上一轮构建中，我们将三种 INPNC–cellulase assembly products 分别转化至 MG1655，并在所有实验组的链霉素选择平板上观察到了菌落。

本轮的工程目标是进一步验证这些候选菌落的基因型和功能表型。

我们选择两种互补的验证方法。

首先，使用 colony PCR 检测目标 INPNC–cellulase DNA 结构是否存在于候选菌落中。

其次，利用 CMC–Congo red assay 观察菌株是否表现出可检测的纤维素降解活性。若纤维素酶能够有效水解 CMC，理论上可以在刚果红染色和脱色后观察到菌落周围的浅色水解区域。

## Build

我们从上一轮链霉素选择平板中挑取三个构建组的候选单菌落。

将对应菌落分别用于 colony PCR 的样品准备，并进一步接种至含 CMC 的培养基中，用于后续纤维素酶活性定性检测。

## Test

### Test 1 — Colony PCR

我们使用针对目标表达结构设计的引物，对不同构建组获得的候选菌落进行 colony PCR。

实验结果显示，三个构建组均未获得预期大小的目的条带。

这意味着，我们未能从这些菌落中获得证明目标 INPNC–cellulase constructs 存在的基因型证据。

### Test 2 — CMC–Congo Red Assay

为了进一步排除 colony PCR 技术性假阴性的可能，我们对候选菌株进行了 CMC–Congo red 功能验证。

培养完成后，我们对含 CMC 的平板进行刚果红染色及脱色处理，观察菌落周围是否形成纤维素水解区域。

然而，三个构建组均未观察到预期的清晰水解圈。

因此，该实验也没有提供能够确认工程菌具有纤维素降解活性的功能证据。

## Learn

本轮两种验证方法均未获得预期的阳性结果。

Colony PCR 没有检测到目标 DNA，而 CMC–Congo red assay 也没有观察到明确的纤维素降解表型。

这使我们开始重新审视上一轮获得的候选菌落是否真正携带目标重组质粒。

不过，这些阴性结果仍然不能单独区分 DNA 组装失败、转化与筛选问题以及融合蛋白表达问题。

特别是，CMC 染色阴性本身不能证明目标 DNA 不存在，因为蛋白表达、定位或酶活不足同样可能造成阴性结果。

因此，下一轮我们决定从两个方向排查：

1. 直接检测 Gibson Assembly products 中是否存在预期的 DNA 结构。
2. 重新评估原有抗生素筛选条件是否能够真正区分野生型细胞与携带质粒的转化子。

我们的下一步问题是：

**Did our DNA assembly fail, or were we unable to reliably identify genuine transformants?**

---

## DBTL B2 Re-evaluating the antibiotic selection system

### Overview

上一轮实验暴露出了一个此前被我们忽略的 assumption：

> 能够在 antibiotic plate 上生长的 colony，并不一定就是目标 transformant。

因此，我们决定重新测试整个 SmR-based selection system，并加入未经 transformation 的 DH5α WT 作为 negative control。

这一轮我们同时比较不同 antibiotic condition 下：

- 工程菌，即尝试转入 pCDF-based SmR plasmid 的 DH5α；

- 野生型 DH5α WildType，未转入任何 plasmid。

我们设置了三种 selection condition：

1. **链霉素平板**：同时涂布工程菌和 WT，判断链霉素能否抑制 WT；

2. **壮观霉素平板**：同时涂布工程菌和 WT，判断壮观霉素能否抑制 WT；

3. **链霉素 + 壮观霉素平板**：同时涂布工程菌和 WT，判断双抗生素组合是否能提高筛选严谨性。

如果 selection system 工作正常，那么：

- 工程菌应当能够生长；

- WT 应当无法生长。

我们使用新的 DH5α competent cells，并进行 pCDF-based SmR plasmid transformation，同时保留未经任何 plasmid transformation 的 DH5α WT。

随后将各组细胞分别涂布于三种 selection condition 下的平板，所有平板在 37℃ 的相同培养条件下过夜培养。

### Cycle 1｜What does the streptomycin plate alone tell us?

#### Design

链霉素平板是最初 DBTL B1 中使用的 selection condition。

我们首先保留这一条件，观察工程菌和 DH5α WT 是否能够形成 colonies。

#### Build

将转入 pCDF-based SmR plasmid 的工程菌和未经 transformation 的 DH5α WT 分别涂布于链霉素平板，所有平板在 37℃ 下过夜培养。

#### Test

结果显示，链霉素平板上的工程菌能够形成单菌落，这一结果与 DBTL B1 中观察到的现象一致；但同时，链霉素平板上的野生型菌株也能够形成单菌落。

<img width="1233" height="1235" alt="SD链霉素板子含WT" src="https://github.com/user-attachments/assets/cccdd42a-2a68-46b4-ab08-002baafa0f74" />

图2.1-1 涂布接种工程菌和野生型菌株的链霉素平板

#### Learn

这一结果与我们的预期明显不符。如果 streptomycin selection 工作正常，那么，工程菌应当生长，WT 应当无法生长，但实际结果是 WT 同样能够生长。

这说明，WT 没有被链霉素有效抑制，streptomycin 单抗生素条件在我们的实验体系中无法可靠区分 WT 与 plasmid-containing cells。

### Cycle 2｜Can spectinomycin provide a more reliable selection condition?

#### Design

为了进一步验证问题是否仅仅来源于第一批 streptomycin plates 或 antibiotic condition，我们重新购买了 spectinomycin，并重新制备 selection plates。

这一轮实验我们保留了 WT negative control。

我们的目标是测试：更换 antibiotic condition 后，是否能够真正建立 WT 与 transformants 之间清晰的生长差异？

#### Build

我们重新进行 transformation，并将工程菌和未经 transformation 的 DH5α WT 分别涂布于新的 spectinomycin-containing plates，所有平板在 37℃ 下过夜培养。

#### Test

结果显示，壮观霉素平板上，工程菌能够形成 colonies；同时，DH5α WT 也能够在壮观霉素平板上形成 colonies。

<img width="2487" height="2476" alt="SD壮观霉素板子" src="https://github.com/user-attachments/assets/9101b274-14de-4a04-a870-ca6a302bce28" />

图2.2-1 涂布接种工程菌和野生型菌株的壮观霉素平板

#### Learn

这一结果与我们的预期明显不符。如果 spectinomycin selection 工作正常，那么工程菌应当生长，WT 应当无法生长，但实际结果是 WT 同样能够生长。

这说明，WT 没有被壮观霉素有效抑制，spectinomycin 单抗生素条件在我们的实验体系中无法可靠区分 WT 与 plasmid-containing cells。

### Cycle 3｜Does combined streptomycin + spectinomycin selection improve stringency?

#### Design

由于壮观霉素单药不能抑制 WT，我们进一步测试双抗生素组合是否能够提高 selection stringency。

我们使用链霉素 + 壮观霉素双抗生素平板同时涂布：

- 工程菌

- 未经 transformation 的 DH5α WT

如果双药组合能够抑制 WT，而工程菌仍然生长，则说明双药 selection 可能比单药更可靠。

如果 WT 仍然生长，则说明 SmR-based selection system 整体无法承担筛选 transformants 的功能。

#### Build

我们重新制备链霉素 + 壮观霉素双药平板。

随后将工程菌和 DH5α WT 分别涂布于双药平板上，所有组在 37℃ 培养条件下过夜培养。

#### Test

结果显示，链霉素 + 壮观霉素双抗平板上，工程菌能够形成 colonies；同时，DH5α WT 也能够在链霉素 + 壮观霉素双抗平板上形成 colonies。

<img width="2487" height="2476" alt="SD双抗板子" src="https://github.com/user-attachments/assets/209d5579-04bb-43d9-8efe-70dc7063d65a" />

图2.3-1 涂布接种工程菌和野生型菌株的的链霉素+壮观霉素平板

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

### Design

为了摆脱上一轮 selection uncertainty，我们更换了 plasmid backbone 和 antibiotic resistance marker。

新的载体采用 pACYC-based backbone，具有 p15A-family replication origin，并使用 chloramphenicol resistance marker。

这一轮最重要的改变不仅是“换一个质粒”，而是建立三个具有不同诊断意义的 control levels：

#### WT

未经 transformation 的 MG1655。

用于判断：

**chloramphenicol selection 能否有效抑制没有 resistance plasmid 的 cells？**

#### EV — Empty Vector

转入 empty pACYC vector 的 MG1655。

用于判断：

**MG1655 是否能够接受并维持新的 plasmid backbone？**

同时也用于确认：

**chloramphenicol resistance cassette 是否能够正常支持 transformant growth？**

#### INPNC-cellulase constructs

分别转入：

- INPNC-Cel5L
- INPNC-Cel9K
- INPNC-Cel48S

用于判断：

**在 vector backbone、transformation 和 selection 均能够正常工作的情况下，加入目标 surface-display expression cassette 后是否仍能够获得 transformants？**

这一组 controls 使我们能够更加系统地定位 failure。

---

### Build

我们根据新的 pACYC backbone 重新设计 assembly primers，并重新扩增构建所需的 DNA fragments。

随后分别完成：

- empty pACYC vector transformation；
- pACYC-INPNC-Cel5L assembly and transformation；
- pACYC-INPNC-Cel9K assembly and transformation；
- pACYC-INPNC-Cel48S assembly and transformation。

同时设置未经 transformation 的 MG1655 WT。

所有实验组均使用 chloramphenicol selection。

---

### Cycle 1｜Does the new transformation-selection system work?

#### Test

实验结果首先在两个 control groups 中表现出了非常清晰的差异。

##### WT

没有观察到 colony growth。

##### Empty Vector

能够获得 colonies。

---

#### Learn

这一结果为后续分析建立了一个可靠的 baseline。

WT 无法在 chloramphenicol plate 上生长，说明：

**新的 antibiotic selection 能够有效抑制没有 resistance plasmid 的 MG1655。**

Empty-vector transformants 能够形成 colonies，则说明：

**MG1655 可以接受并维持 pACYC-based plasmid。**

同时说明新的 chloramphenicol resistance system 可以正常发挥作用。

因此，前一轮一直无法确定的几个问题，在这一轮中得到了明显改善：

- antibiotic selection is functional；
- host cells can be transformed；
- the new plasmid backbone can be maintained。

这使我们能够更加有信心地分析三个 recombinant constructs 的结果。

---

### Cycle 2｜What happens after adding the INPNC-cellulase cassette?

#### Test

与 empty-vector group 明显不同，三个 recombinant groups 均没有获得预期 colonies：

- INPNC-Cel5L：no colony
- INPNC-Cel9K：no colony
- INPNC-Cel48S：no colony

这一结果呈现出了非常明显的 construct-dependent pattern。

---

#### Learn

因为 WT 与 EV controls 已经分别证明：

- chloramphenicol selection 可以工作；
- MG1655 可以进行 transformation；
- pACYC backbone 可以在 MG1655 中维持；

所以三个 recombinant groups 同时没有获得 colonies，就不能再简单解释为：

**整个 transformation system 都失败了。**

问题开始集中到 experimental groups 与 EV 之间最大的区别：

**INPNC-cellulase expression cassette。**

但是，在得出 expression burden 或 toxicity 的结论之前，我们仍然需要排除一种更加简单的可能性：

> 三个 recombinant constructs 是否只是再次发生了 assembly failure？

因此，我们进一步检测新的 assembly products。

---

### Cycle 3｜Did the recombinant assemblies fail again?

#### Design

如果三个 INPNC-cellulase Gibson assemblies 全部失败，那么 experimental groups 没有 colonies 仍然可以由 cloning failure 解释。

因此，我们再次直接检测 assembly products。

---

#### Test

以三个 assembly products 为 PCR templates，可以分别获得预期大小的 expression-cassette bands。

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

## Overall Learning

这一系列 DBTL cycles 最重要的结果并不是简单得到：

**“我们的 construct 没有转出来。”**

更重要的是，我们通过不断增加能够区分不同 failure modes 的 controls，使问题逐渐从一个模糊的 cloning failure 被拆解。

最初：

**Selection plate 上有 colonies**

↓

但：

**Colony PCR negative**

以及：

**CMC-Congo red functional assay negative**

↓

因此我们检测：

**Assembly products**

↓

发现：

**Target expression cassette can be detected**

↓

于是开始怀疑：

**Are the colonies actually transformants?**

↓

加入 WT control：

**WT also grows under the original selection condition**

↓

说明：

**The original SmR-based selection is unreliable in our experimental system**

↓

更换：

**pACYC + chloramphenicol**

↓

得到：

**WT: no colony**

**Empty vector: colonies**

↓

说明：

**selection, host transformation and plasmid backbone can work**

↓

但是：

**INPNC-Cel5L / Cel9K / Cel48S: no colonies**

↓

同时：

**target DNA remains detectable in assembly products**

↓

因此我们将下一轮工程问题聚焦为：

> **Does the shared INPNC-cellulase expression architecture impose excessive cellular burden?**

这使我们的下一轮设计不再是单纯重复 cloning，而是开始重新思考：

**How should the surface-display architecture itself be redesigned?**
