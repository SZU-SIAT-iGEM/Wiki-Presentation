# PARTS

## Every Part Carries a Decision

### 每一个元件，都记录着一次设计判断。

## Building Blocks of Friskoli

### From Individual Parts to Biological Systems

合成生物学使我们能够将生物系统拆解为具有不同功能的组成部分，再通过设计、组合和调控，使它们共同完成新的任务。

一个启动子可以调节基因表达，一个转运蛋白可以参与物质进入细胞的过程，一种酶能够催化特定反应，而多个元件之间的协作，则能够形成更为复杂的生物学功能。

Friskoli 正是在这样的工程思路下逐渐发展起来的。

为了探索纤维素降解产物与细菌趋化行为之间的联系，我们研究了糖转运、胞内代谢、表达调控及相关生物模块，并通过不同的组合方式建立可供实验检验的工程系统。

这些元件也见证了我们的设计演进。

从最初的 AscFB 表达盒，到围绕 Chb 系统开展的构建探索，再到通过启动子替换调整染色体内源基因的表达，我们逐渐认识到，元件的实际功能不仅取决于自身序列，也与其他生物组分的协作关系及宿主环境密切相关。

在这一页面，我们介绍 Friskoli 使用、设计与构建的生物元件，展示它们的功能、结构、实验表征及在项目中的作用。对于已经完成正式登记的元件，相应的 Registry 记录将提供更详细的序列信息与使用资料。

我们也希望分享这些元件在实际工程中带来的经验：哪些组合成功形成了目标构建，哪些实验揭示了系统的关键限制，以及这些认识如何影响下一阶段的设计。

**Biological parts become more valuable when their behavior is understood and their knowledge is shared.**

当生物元件的功能得到更充分的认识，当围绕它们积累的经验能够被其他研究者获取，每一个元件便都有机会成为新的研究起点。

---

# 01 / WHAT WE CONTRIBUTE

## Our Contributions to the Registry

### 从元件设计到工程贡献

Friskoli 的生物元件工作围绕三个相互联系的方向展开：底物降解、糖转运与代谢、细胞感知和运动调控。

其中，糖转运与代谢系统经历了较为完整的工程探索。

我们首先构建了由 `ascF` 和 `ascB` 组成的双顺反子表达盒，通过克隆、PCR 和测序完成 DNA 层面的确认，并进一步开展生长与蛋白分析。

随后，我们将研究对象扩展至 Chb 系统，先后尝试外源质粒表达和染色体内源启动子替换，以探索不同调控策略对纤维二糖相关表型的影响。

与此同时，围绕纤维素降解、趋化感知和运动响应展开的研究，也为 Friskoli 的整体生物系统设计提供了重要依据。

这些工作形成了不同层次的成果，包括已有标准元件的应用、组合表达盒的构建、染色体调控改造，以及实验表征与设计经验。

### Our Registry Contributions

|Category|Number|Registry Records|
|---|---|---|
|New Basic Parts|—|—|
|New Composite Parts|—|—|
|Improved Parts|—|—|
|Part Collection|—|—|

---

# 02 / THE PARTS AT A GLANCE

## Our Biological Toolkit

### 认识 Friskoli 的生物元件

Friskoli 的元件按照它们在系统中承担的功能进行组织。

表达调控元件决定基因何时及以何种水平表达；糖转运与代谢模块连接胞外底物和胞内生化过程；降解相关模块承担底物转化功能；信号和运动系统则构成细胞响应环境变化的生物学基础。

我们将这些元件组合成不同的工程构建，并通过实验逐步认识它们在真实细胞环境中的行为。

### Table A — New Parts Contributed

|Part Name|Registry ID|Type|Length|Source Organism|Role in Friskoli|Characterization|
|---|---|---|---|---|---|---|
|—|—|—|—|—|—|—|

### Table B — Composite Constructs

|Construct|Registry ID|Components|Purpose|Experimental Progress|
|---|---|---|---|---|
|AscFB Expression Cassette|—|J23116–B0034–ascF–B0034–ascB–B0015|糖转运与代谢功能研究|DNA 构建经验证，完成初步蛋白与表型测试|
|Chb Expression Constructs|—|不同强度组成型启动子与 Chb 表达模块|探索 Chb 表达水平与糖利用的关系|完成多轮质粒组装和构建排查|
|CP12-chb Chromosomal Construct|—|CP12 启动子与染色体内源 Chb 系统|通过调控改造研究纤维二糖利用|编辑区域经序列核对，获得生长相关表型|

### Table C — Existing Registry Parts Used

|Part Name|Registry ID|Type|Role in Friskoli|
|---|---|---|---|
|J23116|BBa_J23116|Promoter|AscFB 表达盒的组成型转录调控|
|B0034|BBa_B0034|RBS|AscF 与 AscB 的翻译起始调控|
|B0015|BBa_B0015|Terminator|表达盒下游转录终止|

---

# 03 / WHERE EACH PART SITS IN THE SYSTEM

## From Parts to Systems

### 从独立功能走向系统协作

Friskoli 的生物学设计连接了底物降解、产物感知、细胞运动和局部富集等多个环节。

这些环节共同构成了我们探索微重力低对流环境下主动传质机制的基础。

为了理解每一个元件在其中发挥的作用，我们将整体系统划分为五个相互联系的功能层次。

### I. Degradation — 降解

**Turning Substrates into Accessible Signals**

降解模块承担着将复杂底物转化为可溶性产物的任务。

在 Friskoli 的纤维素参考实例中，我们关注纤维素酶及其表面展示策略，希望通过局部酶促反应产生能够被细胞进一步利用或感知的糖类产物。

这一模块连接了固体底物表面与周围的溶液环境，也为后续研究化学梯度的形成提供了生物学基础。

→ [Design](https://chatgpt.com/c/Project/Design.md)

### II. Sensing — 感知

**Connecting Sugar Uptake to Cellular Signaling**

感知模块是 Friskoli 设计中的重要组成部分。

我们围绕 AscF、AscB 及 Chb 系统开展了连续的工程研究，探索纤维二糖相关的转运、代谢和调控过程。

其中，PTS 系统为糖摄取与细胞内部磷酸传递网络之间的联系提供了研究入口。

围绕这些元件积累的实验数据，帮助我们逐渐明确糖利用和趋化信号研究各自需要的验证方法。

→ [Design](https://chatgpt.com/c/Project/Design.md)

### III. Movement — 运动

**Translating Signals into Cellular Behavior**

运动模块决定细胞如何响应其感知到的环境变化。

对于典型的大肠杆菌趋化系统，细胞内部信号可以通过 CheA、CheY 等调控组分影响鞭毛马达行为，改变游动与翻转之间的统计关系。

Friskoli 的计算模型进一步研究了这种信号调节如何影响细胞在空间中的运动轨迹，为解释趋化行为提供定量框架。

→ [Model](https://chatgpt.com/c/Drylab/Model.md)

### IV. Recruitment — 招募

**From Individual Movement to Collective Distribution**

当多个细胞在空间中运动时，单细胞行为可能逐渐形成可观察的群体分布变化。

Friskoli 关注这一过程中细胞向底物附近到达、接触和停留的行为，并尝试研究这些过程如何受到化学信号、扩散条件及运动规则的影响。

这一功能层次连接了分子感知与反应器中的空间传质问题，也是后续趋化测量和模型分析的重要对象。

→ [Engineering](https://chatgpt.com/c/Project/Engineering.md)

### V. Standards, Backbones and Assembly

**The Framework Behind Our Constructs**

标准化元件与载体系统为生物功能模块的组装提供了基础。

在 Friskoli 中，我们使用组成型启动子、RBS、终止子及不同复制系统的质粒骨架，探索目标基因的表达与调控。

从 pGEX-4T-1 到 RSF、p15A 相关质粒，再到染色体调控区域改造，不同工程载体为我们提供了比较表达策略与构建行为的机会。

→ [How the Parts Are Assembled](https://chatgpt.com/c/6ac8dd72-d0b4-83ec-8139-d68a49f839bf#05--how-the-parts-are-assembled)

---

# 04 / PART BY PART

## Understanding Each Building Block

### 每一个元件背后的设计

一个生物元件的价值，既包含其自身具有的功能，也来自它在具体工程环境中的表现。

本节按照元件及相关构建逐一介绍其生物学基础、设计思路、实验表征和在 Friskoli 中积累的研究经验。

## AscF — Sugar Transport-Related Component

### What It Is

`ascF` 来源于大肠杆菌的 `asc` 系统，编码与糖转运相关的膜蛋白，属于 PTS 相关转运组分。

在 Friskoli 的初始工程设计中，AscF 被用于探索纤维二糖相关的跨膜转运过程。

### How It Works

AscF 对应 PTS EII 系统中与膜转运和磷酸传递相关的组分，其功能与细胞内其他 PTS 蛋白的协作密切相关。

### Why We Chose It

我们最初选择大肠杆菌自身的 `asc` 系统，希望利用宿主已有的代谢与调控背景建立相对直接的工程路径。

`ascF` 与 `ascB` 被组合到同一表达盒中，为研究糖转运与后续胞内代谢提供了基础。

### What We Characterized

我们完成了 `ascF` 所在表达盒的克隆、菌落 PCR 与序列验证。

在蛋白实验中，我们进一步尝试通过 SDS-PAGE 和亚细胞组分分离观察 AscF 相关信号。粗膜组分中目标分子量附近的变化较弱，因此 AscF 的蛋白丰度与膜定位成为后续研究的重要方向。

### What It Adds

AscF 的研究帮助我们深入认识了 PTS 多组分转运系统的工程特点，也促使团队将注意力扩展到蛋白表达、系统组成与宿主背景之间的联系。

### Related Research

[Engineering](https://chatgpt.com/c/Project/Engineering.md) · [Experiments](https://chatgpt.com/c/Wetlab/Experiments.md)

## AscB — Intracellular Metabolic Component

### What It Is

`ascB` 同样来自大肠杆菌的 `asc` 系统，编码参与 β-葡萄糖苷类化合物后续代谢的酶。

在 Friskoli 中，AscB 与 AscF 被共同引入工程表达盒。

### How It Works

AscB 参与相关底物进入细胞之后的代谢转化，与糖转运模块共同构成对可溶性糖进行处理的候选途径。

### Why We Chose It

为了同时研究底物进入细胞和胞内利用两个环节，我们选择将 `ascB` 与 `ascF` 组合表达，并通过独立的 RBS 调节翻译起始。

### What We Characterized

我们完成了包含 `ascB` 的表达盒构建与序列检查。

蛋白分析中，工程菌可溶性组分在约 55 kDa 附近出现相较于空载体更明显的蛋白信号，其分子量与定位符合 AscB 的预期。

RBS Calculator 的分析进一步显示，AscB 的预测翻译起始速率约为 AscF 的 3.4 倍，为理解表达差异提供了新的线索。

### What It Adds

AscB 的表征将 DNA 构建、蛋白观察与计算预测联系起来，为进一步优化多基因表达盒提供了参考。

### Related Research

[Engineering](https://chatgpt.com/c/Project/Engineering.md) · [Experiments](https://chatgpt.com/c/Wetlab/Experiments.md)

## AscFB Expression Cassette — Combined Transport and Metabolism

### What It Is

AscFB 表达盒由组成型启动子、两段独立翻译单元和转录终止子组成。

其设计结构为：

`J23116 → B0034 → ascF → B0034 → ascB → B0015`

### How It Works

该表达盒将糖转运相关蛋白和后续代谢相关蛋白组织在同一构建中，便于在统一的细胞背景下研究两者的表达及相关表型。

### Why We Chose It

双顺反子结构使我们能够在一个工程构建中引入两个功能基因，同时保留各自的翻译起始调控序列。

这一设计适合开展 DNA 构建、蛋白分析和初步功能验证。

### What We Characterized

我们通过巢式 PCR、Touchdown PCR、Gibson Assembly、菌落筛选及测序完成表达盒构建，并将其转入 MG1655。

随后，通过软琼脂、t-HAP、生长曲线及蛋白分级实验，研究工程菌在不同条件下的表现。

葡萄糖条件支持工程菌生长与宏观扩展；纤维二糖条件下，AscFB 工程菌尚未呈现预期的利用优势。

### What It Adds

这一构建形成了 Friskoli 早期较完整的一组基因型、蛋白检测与表型研究资料。

相关结果也成为团队进一步研究 Chb 系统及其他转运调控方案的依据。

### Related Research

[Engineering](https://chatgpt.com/c/Project/Engineering.md) · [Experiments](https://chatgpt.com/c/Wetlab/Experiments.md) · [Results](https://chatgpt.com/c/Project/Result.md)

## Chb System — Exploring an Alternative Uptake Pathway

### What It Is

Chb 是大肠杆菌中与特定糖类转运和代谢有关的基因系统。

在 Friskoli 的工程研究中，我们将其作为继 AscFB 之后的重要替代方案。

### How It Works

Chb 相关组分参与 PTS 依赖的底物转运与代谢，其功能受到转录调控和系统内多个蛋白组分协作的影响。

### Why We Chose It

在分析 AscFB 的实验结果和相关研究后，我们决定进一步探索具有不同组分结构及调控方式的糖转运系统。

为研究表达水平可能产生的影响，我们最初设计了由多种 Anderson 系列组成型启动子驱动的 Chb 质粒表达方案。

### What We Characterized

我们先后尝试基于 RSF 和 p15A 复制系统构建 Chb 表达载体。

Gibson 反应后的 PCR 检测获得了与连续组装模板相符的扩增信号；转化筛选则持续呈现难以获得有效克隆的情况。

这些结果推动团队将设计进一步转向染色体内源 Chb 的调控改造。

### What It Adds

Chb 系统的研究拓展了 Friskoli 对糖转运模块的工程探索，也提供了比较质粒表达与染色体调控两种策略的具体案例。

### Related Research

[Engineering](https://chatgpt.com/c/Project/Engineering.md) · [Experiments](https://chatgpt.com/c/Wetlab/Experiments.md)

## CP12-chb — Chromosomal Regulation of the Native Chb System

### What It Is

CP12-chb 是通过替换染色体内源 `chb` 调控区域获得的工程构建。

该设计保留了宿主已有的 Chb 编码系统，并通过新的启动子调节其表达。

### How It Works

组成型启动子替换改变了内源操纵子的转录调控方式，使团队能够研究 Chb 表达变化对相关糖利用表型的影响。

### Why We Chose It

此前的 Chb 质粒实验促使我们探索新的构建策略。

利用染色体中已有的转运系统，可以将工程重点集中在调控层面，同时提供不同于外源多基因质粒表达的实验路径。

### What We Characterized

我们采用 λ-Red 同源重组相关方法开展启动子替换，并通过 PCR 与 Sanger 测序核对目标编辑区域。

在随后开展的生长实验中，CP12-chb 菌株在纤维二糖培养条件下表现出缓慢的 OD600 增长趋势，由约 0.14 上升至 24 小时时约 0.21，而同期野生型的读出基本维持在初始水平附近。

我们也开展了软琼脂观察，当前条件下的菌体扩展较弱。

### What It Adds

CP12-chb 提供了从 DNA 调控改造走向糖利用相关表型的具体研究实例。

这一结果为后续研究启动子强度、糖转运与趋化行为之间的联系建立了新的实验基础。

### Related Research

[Engineering](https://chatgpt.com/c/Project/Engineering.md) · [Experiments](https://chatgpt.com/c/Wetlab/Experiments.md) · [Results](https://chatgpt.com/c/Project/Result.md)

---

# 05 / HOW THE PARTS ARE ASSEMBLED

## Assembly Strategies and Biological Chassis

### 从元件序列到工程菌株

在 Friskoli 的实验过程中，我们采用了不同的 DNA 组装与遗传改造策略，将目标元件引入大肠杆菌并开展功能测试。

这些方法分别服务于不同阶段的研究目标，也使我们能够比较不同表达载体和调控方式的实验表现。

### AscFB Plasmid Construction

AscFB 采用 pGEX-4T-1 作为载体骨架，以 BamHI/EcoRI 位点制备线性化载体，并通过 Gibson Assembly 组装双顺反子表达盒。

实验先在 DH5α 中完成克隆与序列筛选，再将经过核对的质粒转入 MG1655，用于后续功能分析。

### Chb Plasmid Construction

Chb 质粒研究采用不同强度的组成型启动子，尝试建立可比较的表达梯度。

我们先后测试 RSF 与 p15A 相关复制系统，并通过组装 PCR、转化和克隆筛选逐步排查构建过程中的关键问题。

### CP12-chb Chromosomal Engineering

在染色体工程阶段，我们采用 λ-Red 同源重组相关策略，以 CP12 启动子替换内源 `chb` 调控区域。

目标区域经过 PCR 与测序核对，随后进入生长及表型测试。

### Construction Overview

|Construct|Strategy|Host|Main Verification|
|---|---|---|---|
|AscFB Expression Cassette|Gibson Assembly|DH5α → MG1655|菌落 PCR、Sanger 测序|
|Chb Plasmid Constructs|Gibson Assembly|大肠杆菌克隆底盘|组装 PCR、转化筛选|
|CP12-chb|λ-Red Recombination|MG1655|编辑区 PCR、Sanger 测序|

[Design](https://chatgpt.com/c/Project/Design.md) · [Experiments](https://chatgpt.com/c/Wetlab/Experiments.md)

---

# 06 / WHAT WE MEASURED

## Characterization and Experimental Evidence

### 从基因型到功能表型

Friskoli 的元件表征覆盖了 DNA 构建、蛋白表达分析与细胞功能观察三个层次。

通过这些不同层次的实验，我们能够逐渐建立从元件设计到实际生物学行为的联系。

### Construct Level — DNA 构建

我们利用 PCR、限制性酶切、Gibson Assembly、克隆筛选和测序等方法，对不同工程构建进行验证。

AscFB 表达盒经过多轮 PCR 与序列核对，成功转入 MG1655。

CP12-chb 的目标染色体编辑区域同样获得了 PCR 与测序支持。

### Expression Level — 蛋白表达

在 AscFB 工程中，我们通过 SDS-PAGE 比较工程菌与空载体对照的蛋白组成。

可溶性组分中出现了与 AscB 预期分子量接近的额外信号，膜组分分析则为后续研究 AscF 的表达与定位提供了方向。

RBS Calculator 的翻译起始预测进一步为表达调控分析提供了计算依据。

### Function Level — 功能表型

我们通过软琼脂、t-HAP 和生长曲线等方法研究工程菌的实际表现。

AscFB 的初步测试呈现出葡萄糖与纤维二糖条件下的不同生长和扩展特征。

CP12-chb 则在纤维二糖培养条件下获得了可观察的 OD600 增长趋势，成为后续研究糖利用与趋化联系的重要对象。

### Evidence Overview

|Construct|DNA Characterization|Protein Characterization|Functional Characterization|
|---|---|---|---|
|AscFB|PCR 与测序确认|SDS-PAGE、蛋白分级、RBS 预测|生长曲线、软琼脂、t-HAP|
|Chb Plasmid Constructs|组装 PCR、转化筛选|—|—|
|CP12-chb|编辑区 PCR 与测序确认|—|纤维二糖生长曲线、软琼脂观察|

[Measurement](https://chatgpt.com/c/Wetlab/Measurement.md) · [Results](https://chatgpt.com/c/Project/Result.md)

---

# 07 / DESIGNS UNDER DEVELOPMENT

## The Next Steps in Our Parts Engineering

### 从已有构建继续探索

Friskoli 的元件研究也积累了一系列值得继续探索的设计方向。

这些工作来自实际实验中发现的问题，并为后续团队提供了进一步开展工程研究的起点。

### Chb Expression Series

此前的 Chb 质粒方案尝试以五种不同强度的组成型启动子建立表达梯度。

在经历载体构建与转化筛选问题后，这一方向的后续工作可以围绕质粒稳定性、表达调控与宿主适配展开。

### Chromosomal Promoter Series

CP12-chb 的生长实验为染色体调控研究提供了新的基础。

进一步构建不同强度的启动子系列，有助于研究 Chb 表达水平与纤维二糖相关表型之间的联系。

### Linking Uptake with Chemotaxis

糖转运与代谢功能的研究，最终还需要与细菌感知和运动行为建立联系。

未来通过更加直接的梯度响应测量、单细胞运动追踪与系统化对照实验，可以进一步研究相关元件对细胞趋化行为的影响。

这些方向延续了 Friskoli 从分子构建走向细胞运动，再走向局部传质研究的整体思路。

---

# 08 / USING THESE PARTS

## For Future Builders

### Building on What We Have Learned

标准化元件的价值，随着知识的积累与共享而不断增长。

我们希望后来者能够通过这一页面找到适合自身研究的元件，了解已有的实验条件和表征结果，并在此基础上开展新的设计。

Friskoli 所留下的，既包括我们构建过的生物元件，也包括围绕这些元件积累的研究经验。

对于研究糖转运和代谢的团队，AscFB 与 Chb 的工程路线可以提供不同构建策略及实验表现的参考。

对于关注遗传调控的团队，CP12-chb 的研究展示了通过染色体启动子改造探索功能表型的一条路径。

而对于希望进一步研究趋化与物质传递的团队，这些元件所连接的转运、代谢和调控过程，则为后续系统设计提供了新的切入点。

我们希望通过清晰的序列记录、实验表征和跨页面链接，让这些成果更容易被理解、比较和复用。

**Every part is a possible beginning.**

每一个元件，都可能成为下一段研究的起点。

[Contribution](https://chatgpt.com/c/Project/Contribution.md) · [Collaboration](https://chatgpt.com/c/Engagement/Collaboration.md)

---

## References

1. Morabbi Heravi, K., & Altenbuchner, J. (2018). Cross talk among transporters of the phosphoenolpyruvate-dependent phosphotransferase system in _Bacillus subtilis_. _Journal of Bacteriology_, 200(19), e00213-18. [https://doi.org/10.1128/JB.00213-18](https://doi.org/10.1128/JB.00213-18)
    
2. Parisutham, V., Jung, S.-K., Nam, D., & Lee, S. K. (2013). Transcriptome-driven synthetic re-modeling of _Escherichia coli_ to enhance cellobiose utilization. _Chemical Engineering Science_, 103, 50–57. [https://doi.org/10.1016/j.ces.2012.08.006](https://doi.org/10.1016/j.ces.2012.08.006)
    
3. Parisutham, V., & Lee, S. K. (2015). Novel functions and regulation of cryptic cellobiose operons in _Escherichia coli_. _PLOS ONE_, 10(6), e0131928. [https://doi.org/10.1371/journal.pone.0131928](https://doi.org/10.1371/journal.pone.0131928)


# PARTS

## Every Part Carries a Decision

### 每一个元件，都记录着一次设计判断。

# Building Blocks of Friskoli

### From Individual Parts to Biological Systems

合成生物学使我们能够从不同功能的生物元件出发，通过设计、组合和调控，构建具有特定功能的生物系统。

在 Friskoli 的研究过程中，我们围绕底物转化、环境感知与细胞响应等环节，探索了不同生物元件的作用及其组合方式。

每一项选择都有自己的研究背景。从元件的生物学功能，到表达方式、宿主环境和系统兼容性，这些因素共同影响着我们的工程设计。

随着实验的推进，我们不断调整元件组合，积累了关于构建方法、表达特征和功能表现的研究经验。

**Biological parts become more valuable when their behavior is understood and their knowledge is shared.**

我们希望通过整理和分享这些成果，让每一个元件及其背后的工程经验，都有机会成为未来研究的基础。

---

# 01 / OUR PARTS

## Our Biological Toolkit

### 探索我们的生物元件

Friskoli 的元件库汇集了项目研究过程中使用、设计与构建的生物元件。

我们按照元件的功能与类型组织相关资料，展示其基本信息、设计目的、实验表征及对应的 Registry 记录。

通过这一目录，读者可以了解不同元件在 Friskoli 中承担的角色，并进一步探索它们的生物学特征与应用潜力。

### New Parts

### Composite Parts

### Existing Parts

---

# 02 / FROM PARTS TO SYSTEMS

## Engineering Biological Functions

### 从单个元件到完整系统

一个生物元件能够提供特定的功能，而多个元件之间的协作，则使我们能够设计更为复杂的生物学过程。

在 Friskoli 中，我们根据不同研究阶段的目标，将相关元件组织为功能模块，并探索它们在完整系统中的作用。

从分子层面的功能选择，到细胞层面的表达与调控，再到不同模块之间的联系，这些设计共同构成了我们的工程体系。

这一过程也为我们提供了持续优化和拓展系统的空间。

---

# 03 / PART CHARACTERIZATION

## Understanding How Our Parts Perform

### 通过实验认识元件

元件的设计为实验提供了起点，而实际表征则帮助我们认识它们在生物系统中的行为。

在研究过程中，我们采用不同的实验方法，对元件的构建、表达及功能表现进行分析。

这些记录展示了不同元件在具体实验条件下的特征，也帮助我们发现值得进一步探索的工程问题。

我们将相关实验结果与设计资料相互关联，使每个元件的研究历程都能够得到追溯。

---

# 04 / OUR ENGINEERING JOURNEY

## Decisions Behind the Design

### 从一次选择走向下一次设计

随着研究的推进，我们对生物系统的理解也在不断深入。

一些元件帮助我们建立了最初的工程方案，一些实验推动了表达策略或功能模块的调整，还有一些设计为后续研究提供了新的方向。

这些经历记录了 Friskoli 的工程演进，也让我们逐渐认识到不同元件在系统中的潜力与适用条件。

每一次设计选择，都成为下一轮研究的基础。

---

# 05 / FOR FUTURE BUILDERS

## Sharing What We Have Learned

### 让元件成为新的起点

标准化生物元件的价值，随着研究经验的积累与共享而不断增长。

我们希望其他团队能够通过这一页面找到适合自身研究的元件，了解它们的功能、实验条件和已有表征，并在此基础上开展新的设计。

每一份序列记录、每一次构建经验和每一组实验结果，都可能为未来的研究提供参考。

通过 iGEM Registry 和相关研究资料，我们希望这些成果能够继续被使用、检验与改进。

**Every part is a possible beginning.**

每一个元件，都可能成为下一段研究的起点。