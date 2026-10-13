# DESIGN

## Making Encounters Possible

### Designing the Path Between Life and Matter

Friskoli 的设计始于一个简单的设想：让细菌主动接近需要它们参与反应的地方。

细菌拥有感知化学环境和调节运动的天然能力，而许多生物转化过程又受到局部物质分布与接触条件的影响。如果能够将底物降解产生的化学信号与细胞趋化行为联系起来，我们就有机会通过生物学设计，改变细胞到达底物附近的方式。

为了探索这一设想，我们选择大肠杆菌 MG1655 作为实验底盘，以纤维素降解为示范场景，围绕**底物转化、糖摄取信号与趋化运动**三个相互关联的过程建立工程设计。

**Our design begins with bringing biological activity closer to where it is needed.**

---

# 01 / THE DESIGN QUESTION

## From Chemical Information to Cellular Motion

### 如何让细菌找到底物？

在含有固体底物的生物反应体系中，反应物的空间分布与细胞运动共同影响着局部生物转化。

我们的设计需要建立三个相互关联的功能：

1. **Signal Generation — 信号产生：** 在底物附近形成与其位置有关的可溶性化学信号。
    
2. **Signal Perception — 信号感知：** 使细胞能够将这些化学信号与内部运动调控网络联系起来。
    
3. **Directed Migration — 趋化迁移：** 利用细菌的运动行为，提高细胞接近目标区域的概率。
    

这三个功能共同构成了 Friskoli 的生物学设计基础。

我们进一步关注细胞到达底物表面后的行为，希望将运动、接触和局部降解联系起来，从而研究趋化是否能够在特定条件下改善细胞与底物之间的有效相遇。

![[BioGDP-GDPI14VEV2-layered-animated.gif]]
[Figure DES-01｜Friskoli 整体生物学架构：底物降解、化学信号、PTS 相关感知、细菌趋化及界面接触｜原创交互图]

---

# 02 / OUR BIOLOGICAL DESIGN

## Turning Chemical Gradients into Motion

### 将底物转化与细胞运动联系起来

纤维素为这一设计提供了具体的物质基础。

作为一种不溶性的多糖，纤维素能够通过酶促水解产生纤维二糖等可溶性产物。这些产物在周围液体中扩散，并可能被细菌进一步摄取和代谢。

因此，我们将纤维素的局部降解与细菌对糖类信号的响应联系起来，构建了一条从底物转化到细胞行为的工程路径。

## 2.1 Substrate Conversion

### Creating a Local Chemical Signal

底物降解模块的设计目标，是将固体纤维素转化为可以在液体中扩散的糖类产物，并使这一过程与细胞所在的位置建立联系。

我们选择细胞表面展示作为主要探索策略之一。通过在细菌外膜锚定纤维素酶，可以使催化功能与细胞形成空间关联，让细胞到达底物附近后的酶促反应成为一个值得研究的过程。

==在具体设计中，我们采用冰核蛋白衍生的 INPNC 锚定元件，并选择来自 _Clostridium thermocellum_ 的 Cel5L、Cel9K 和 Cel48S 作为候选纤维素酶。==

三种酶具有不同的催化特征，因而可以帮助我们研究不同水解作用在纤维素降解中的潜在贡献。

考虑到大型融合蛋白的表达负担，我们设计了分别表达不同纤维素酶的工程菌模块，希望通过独立构建与表征，为后续的组合应用提供依据。

表面展示系统的功能需要通过蛋白表达、表面定位和实际催化活性逐步确认。不同酶的水解产物组成，也将影响后续可供细胞利用的化学信号。

[Figure DES-02｜INPNC 表面展示构型与 Cel5L、Cel9K、Cel48S 模块示意图｜结合真实构建图绘制]

[Explore Biological Parts → Parts]

## 2.2 Sugar Uptake and Signaling

### From Molecular Uptake to Cellular Response

底物附近产生可溶性糖类后，下一步是使细胞能够感知这些物质的变化。

我们最初考虑过直接改造趋化受体，使其识别与纤维素降解相关的化学信号。随着研究深入，我们将注意力转向了大肠杆菌已有的糖摄取与趋化调控机制。

磷酸转移酶系统（Phosphotransferase System, PTS）通过磷酸基团的逐级传递参与多种糖的摄取与磷酸化。除了物质转运，PTS 组分的磷酸化状态还能够影响细胞内部的调控网络。

Neumann 等人（2012）的研究表明，PTS 相关信号能够传递至由趋化受体、CheW 和 CheA 构成的感知复合体，并与经典趋化信号共享下游的适应过程。Somavanshi 等人（2016）进一步研究了 PTS 网络对糖摄取通量的感知与信号传递机制。

这些研究为我们提供了一条利用已有细胞信号网络的工程路径。

围绕纤维二糖相关的糖转运，我们先后研究了两种策略：

**AscFB 系统**

AscF 是与部分 β-葡萄糖苷转运相关的 PTS 组分，AscB 则参与相应磷酸化糖的后续水解。我们通过组合表达 `ascF` 与 `ascB`，探索纤维二糖相关的摄取和代谢能力。

**Chb 系统**

在 AscFB 的实验探索之后，我们进一步研究大肠杆菌内源 Chb 系统的工程化可能性。团队尝试了外源表达与染色体调控区域改造，希望通过改变相关基因的表达，研究纤维二糖利用及后续信号响应。

这两条路线为糖转运功能的工程探索提供了不同的切入点。我们希望进一步研究，特定糖的实际摄取通量能否在细胞内产生足以调节趋化行为的信号。

[Figure DES-03｜AscFB 与 Chb 工程路线对照，连接 PTS 共用磷酸传递组分｜原创机制图]

[Explore Our Engineering → Engineering]

## 2.3 Chemotactic Motion

### Turning Signals into Movement

在大肠杆菌中，趋化信号通过内部调控网络影响鞭毛马达的运动状态。

对于具有吸引作用的 PTS 糖摄取信号，细胞内的磷酸传递状态变化可以抑制趋化感知复合体的激酶活性，进一步影响 CheY 的磷酸化水平。

CheY-P 参与调节鞭毛马达的旋转方向。当相应吸引信号增强时，细胞的翻转倾向可以降低，从而延长沿有利方向的游动过程。CheR、CheB 介导的适应机制则帮助细胞在变化的环境中持续比较信号。

通过这样的信号处理，细菌能够在不断游动和改变方向的过程中，对化学梯度形成统计意义上的趋化响应。

在 Friskoli 中，我们关注 PTS 相关信号能否使细胞对纤维二糖浓度变化产生可测量的运动响应。

为了研究这一过程，我们进一步建立了连接糖摄取、PTS 状态、CheA/CheY 信号与 Run-and-Tumble 运动的数学模型，探索分子信号如何逐步影响单细胞行为与群体空间分布。

[Figure DES-04｜PTS → CheA/CheY → Flagellar Motor 信号路径｜参考 Neumann et al., 2012；Somavanshi et al., 2016，重绘]

[Explore Our Model → Model]

---

# 03 / FROM MOVEMENT TO CONTACT

## Closing the Distance

### 相遇之后，还会发生什么？

细菌向目标区域迁移，是主动相遇过程的开始。

对于依赖固体底物的生物转化，细胞是否能够到达底物附近、是否发生实际接触，以及接触持续多长时间，都可能影响后续的局部反应。

因此，我们将研究目标组织为一条连续的功能路径：

**Sensing → Movement → Arrival → Contact → Conversion**

感知、运动、到达、接触与转化。

每个环节对应着不同的可观测行为。

细胞趋化能够改变其运动轨迹与空间分布；底物表面的几何结构及相互作用可能影响细胞的接触和停留；而酶的定位与催化活性则决定接触之后可能发生的转化过程。

在模型中，我们分别关注细胞首次到达底物附近所需的时间、底物附近的细胞分布、实际表面接触比例及接触持续时间，并进一步研究这些变化对局部底物转化的可能影响。

这样的设计使我们能够逐步分析：细胞运动的改变，究竟在什么条件下能够转化为有效的界面接触。

[Figure DES-05｜从趋化轨迹到表面接触：Arrival、Contact、Residence Time 的测量定义｜模型示意]

---

# 04 / EXPLORING THE FEEDBACK

## When Encounters Create New Signals

### 从局部作用到动态反馈

Friskoli 的另一个研究目标，是探索底物降解与细胞迁移之间可能形成的动态反馈。

在我们的设计构想中，携带表面展示纤维素酶的细胞接近底物后，局部催化活动有机会释放更多可溶性糖类。这些产物扩散到周围环境，并可能通过糖摄取相关信号影响其他细胞的运动。

随着细胞重新分布，底物附近的催化活动也可能改变，进而影响后续的信号产生。

这一过程将**局部降解、信号形成、细胞迁移与表面接触**联系起来。

反馈的建立需要一定的初始条件。在表面展示体系中，早期到达底物附近的细胞及其催化活动，可能成为局部信号来源。信号生成速率、扩散与摄取之间的平衡，则决定梯度能否进一步发展。

我们通过数学模型比较不同初始分布、信号产生速率、扩散条件和细胞响应参数，研究反馈可能出现的条件，以及这种反馈对细胞空间富集与表面接触的影响。

[Figure DES-06｜趋化—降解反馈环：初始接触、糖释放、梯度建立、细胞迁移、后续催化｜动态交互图]

[Explore the Feedback Model → Model]

---

# 05 / DESIGNING FOR MEASUREMENT

## Making the Invisible Observable

### 让微观行为成为可检验的证据

要研究趋化能否改善细胞与底物之间的相遇，我们需要将微观运动转化为可以观察和比较的数据。

因此，测量方法从研究初期便成为 Friskoli 工程设计的重要组成部分。

我们围绕微流控、显微成像与计算机视觉建立测量思路，希望在可控的局部化学环境中，记录细胞运动、空间分布及其随时间发生的变化。

在测量方法的开发中，我们选择以大肠杆菌对天冬氨酸的天然趋化响应作为参考体系，首先研究实验装置、化学梯度和图像分析是否能够共同提供可靠的运动数据，再逐步探索其在其他趋化系统中的应用。

通过比较不同梯度、细胞运动条件与对照组，我们希望建立能够描述方向性响应、局部富集和空间迁移的定量方法。

这些测量结果也可以与模型预测相互比较，帮助我们检查运动机制、空间边界及参数选择的合理性。

[Figure DES-07｜微流控趋化测量原理：梯度、细胞成像、轨迹追踪与统计指标｜原创示意图]

[Explore Our Measurement → Measurement]

---

# 06 / DESIGNING WITH RESPONSIBILITY

## Freedom to Move, Boundaries to Protect

### 为生物系统建立可靠边界

Friskoli 希望利用细菌的主动运动，同时也需要对其活动环境进行可靠的管理。

在实验与未来应用构想中，细胞应当在受控的培养体系内发挥功能。因此，物理隔离与反应器的结构完整性成为我们优先考虑的设计条件。

封闭培养空间、可靠的流体接口、明确的样品处理程序和培养物灭活措施，共同构成了当前实验体系中的基本安全要求。

对于未来的空间应用，我们还需要关注微重力流体行为对培养物管理、气液分布、泄漏风险和操作可靠性的影响。

这些条件将与工程菌功能共同进入未来系统的设计与评价。

[Explore Our Safety → Safety]

---

# 07 / BEYOND THE FIRST SUBSTRATE

## A Design for Further Exploration

### 从参考实例走向更多可能

通过纤维素这一具体场景，我们将底物转化、化学信号、细胞运动和局部接触组织成一套可研究的功能关系。

这一设计也提示了更广泛的可能性。

不同的生物反应体系可以具有不同的底物、可溶性信号、微生物底盘和感知机制。如果能够明确这些因素之间的联系，就有机会进一步探索相应的主动相遇策略。

为了支持这类研究，我们尝试将扩散、细胞运动、信号调控和局部相互作用整理成可配置的计算模块，并逐步发展 Friskoli-CAD。

这一工具帮助我们将特定的纤维素研究实例，与更加一般的微尺度物质相遇问题联系起来。

[Explore FriskoliCAD → Software]

## Epilogue · Where Life Meets Matter

在宏观尺度上，生物反应器由容器、流路与复杂的设备组成。

而在微观尺度上，许多重要的过程，始于一个细胞与一份底物之间的相遇。

Friskoli 希望通过工程设计理解和调节这些相遇，让细胞的感知与运动成为研究局部生物转化的新途径。

**Sometimes, a small change in direction can make an important encounter possible.**

---

## References

[1] Hall, B. G., & Xu, L. (1992). Nucleotide sequence, function, activation, and evolution of the cryptic asc operon of Escherichia coli K12. _Molecular Biology and Evolution_, 9(4), 688–706. [https://doi.org/10.1093/oxfordjournals.molbev.a040753](https://doi.org/10.1093/oxfordjournals.molbev.a040753)

[2] Neumann, S., Grosse, K., & Sourjik, V. (2012). Chemotactic signaling via carbohydrate phosphotransferase systems in Escherichia coli. _PNAS_, 109(30), 12159–12164. [https://doi.org/10.1073/pnas.1205307109](https://doi.org/10.1073/pnas.1205307109)

[3] Somavanshi, R., Ghosh, B., & Sourjik, V. (2016). Sugar Influx Sensing by the Phosphotransferase System of Escherichia coli. _PLOS Biology_, 14(8), e2000074. [https://doi.org/10.1371/journal.pbio.2000074](https://doi.org/10.1371/journal.pbio.2000074)

[4] Francisco, J. A., et al. (1993). Specific adhesion and hydrolysis of cellulose by intact Escherichia coli expressing surface anchored cellulase or cellulose binding domains. _Bio/Technology_, 11, 491–495. [https://doi.org/10.1038/nbt0493-491](https://doi.org/10.1038/nbt0493-491)

[5] Leis, B., et al. (2017). Comparative characterization of all cellulosomal cellulases from Clostridium thermocellum reveals high diversity in endoglucanase product formation essential for complex activity. _Biotechnology for Biofuels_, 10, 240. [https://doi.org/10.1186/s13068-017-0928-4](https://doi.org/10.1186/s13068-017-0928-4)