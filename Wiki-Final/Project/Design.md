# DESIGN

## Making Encounters Possible

### Designing the Path Between Life and Matter

在一个充满流动的世界里，我们很少注意到物质是怎样彼此相遇的。

水流携带溶解的分子，搅拌让反应物不断混合，复杂的流体运动帮助物质跨越空间。

这些过程构成了许多生物反应器运行的基础。

但在微重力环境中，浮力驱动的自然对流减弱，流体和物质的空间分布也可能发生改变。

对于依赖细胞与底物接触的生物反应来说，局部物质传递因此成为一个值得关注的问题。

这让我们产生了一个想法：

**What if microorganisms could help close the distance?**

如果微生物能够主动缩短它们与目标物质之间的距离，会发生什么？

在自然界中，许多细菌已经拥有这样的能力。

通过趋化，它们能够感知环境中的化学信号，并调整自己的运动行为，在不断探索中提高接近特定区域的概率。

Friskoli 希望将这种能力引入生物反应器的设计。

我们尝试利用微生物自身的运动，在局部尺度上增加细胞与底物相遇、接触和发生反应的机会。

**Our design begins with a simple idea: bringing biological activity closer to where it is needed.**

我们的设计始于一个简单的想法：让生物学活动更有机会发生在需要它的地方。

---

# 01 / THE DESIGN QUESTION

## When Transport Becomes a Challenge

### 从物质传递到生物运动

在生物反应器中，反应效率受到许多因素共同影响。

底物需要到达活性酶或细胞所在的位置；产物需要从反应区域扩散或被运输；营养物质、代谢状态和局部流体环境也会影响反应过程。

对于含有固体底物的体系，这些问题往往集中在固液界面附近。

当流动条件发生变化时，细胞与底物之间的空间关系可能成为影响反应的重要因素。

在这一背景下，我们开始关注微生物自主运动能够发挥怎样的作用。

细菌能够以自身的运动方式探索周围环境，并通过感知化学梯度改变游动行为。

这一机制为局部物质传递提供了一种新的研究思路。

在 Friskoli 的设计中，机械混合与微生物趋化承担不同尺度上的任务。

宏观流动负责反应器整体的物质输送，而细胞运动则有机会在低流速区域、扩散边界层或底物附近补充局部传质。

两种机制共同构成了我们对未来生物反应器的设想。

---

# 02 / OUR BIOLOGICAL DESIGN

## Turning Chemical Gradients into Motion

### 将化学信号连接到细胞行为

要让细菌主动接近目标底物，首先需要在底物与细胞之间建立可以被感知的联系。

我们选择纤维素作为研究这一机制的参考底物。

纤维素经过酶促水解，可以产生纤维二糖等可溶性糖类。这些产物为连接局部降解反应、物质扩散和微生物行为提供了可能。

围绕这一思路，我们逐渐形成了相互联系的生物学设计模块。

## 2.1 Substrate Conversion

### Creating a Local Chemical Signal

纤维素降解模块负责将聚合物底物转化为可溶性产物。

我们关注纤维素酶的选择、表达及其与细胞表面的空间关系，希望通过局部催化过程，为细胞感知提供与底物位置有关的化学信息。

表面展示是其中一种值得探索的工程策略。

通过将酶与细胞表面相联系，可以使细胞运动和酶的局部作用位置形成更直接的空间关系。

这一设计为研究细胞到达底物之后的接触、停留和降解过程提供了基础。

[Explore Biological Parts → Parts](https://chatgpt.com/c/Project/Parts.md)

## 2.2 Sugar Uptake and Signaling

### From Molecular Uptake to Cellular Response

细胞需要通过生物学机制，将环境中的物质变化转化为内部信号。

在 Friskoli 中，我们将研究重点放在糖转运与趋化信号之间的联系。

大肠杆菌的磷酸转移酶系统（Phosphotransferase System, PTS）参与多种糖类的转运与磷酸化过程，其磷酸传递状态也能够通过下游趋化网络影响细胞运动。

这一机制为我们提供了工程设计的基础。

我们尝试通过研究相关糖转运和代谢模块，探索纤维素降解产物能否与细胞的趋化行为建立联系。

具体的工程路线经历了不同阶段的调整，相关构建与实验表征记录于 Parts 和 Engineering 页面。

[Explore Our Engineering → Engineering](https://chatgpt.com/c/Project/Engineering.md)

## 2.3 Chemotactic Motion

### Turning Signals into Movement

趋化行为发生在细胞信号网络与鞭毛运动系统之间。

在典型的大肠杆菌趋化过程中，CheA、CheY 等蛋白参与信号传递与运动调控，影响细胞游动和翻转的统计特征。

细菌通过不断运动和改变方向，逐渐形成对化学梯度的方向性响应。

Friskoli 希望研究这种微观行为如何影响细胞的空间分布，以及它们接近底物的概率。

为此，我们将单细胞运动、信号响应与群体空间分布联系起来，构建可用于计算分析的运动模型。

这些模型帮助我们探索不同梯度、细胞运动参数和边界条件下可能出现的行为。

[Explore Our Model → Model](https://chatgpt.com/c/Drylab/Model.md)

---

# 03 / FROM MOVEMENT TO CONTACT

## Closing the Distance

### 相遇之后，还会发生什么？

趋化使细胞更有可能接近某些区域。

但对于生物反应器来说，细胞到达底物附近只是整个过程的一部分。

我们还关心细胞是否真正接触底物、能够在表面停留多久，以及局部接触是否有机会进一步影响底物转化。

因此，Friskoli 将研究过程组织为一条连续的功能路径：

**Sensing → Movement → Arrival → Contact → Conversion**

感知、运动、到达、接触和转化。

每一个环节都有各自的生物学意义，也对应不同的实验观察与计算分析。

细胞的运动参数会影响到达行为，界面条件可能影响接触时间，而酶活性与底物性质则决定后续反应的可能性。

通过研究这些环节之间的联系，我们希望逐渐理解趋化在什么条件下能够带来实际的传质收益。

---

# 04 / EXPLORING THE FEEDBACK

## When Encounters Create New Signals

### 从局部作用到动态反馈

在我们的设计构想中，细胞运动与底物降解可能形成一个相互影响的过程。

细胞接近纤维素表面后，局部酶促作用可以释放新的可溶性产物。

这些产物经过扩散和运输，可能进一步改变附近细胞感受到的化学环境。

而细胞的重新分布，又可能影响底物附近的局部催化活动。

这种潜在的反馈关系，是 Friskoli 希望探索的核心机制之一。

反馈的具体表现取决于多种因素，包括底物转化速率、产物扩散、糖摄取、信号响应、细胞数量及界面行为。

我们通过计算模型分析不同条件下的反馈表现，并通过实验逐步研究组成这一过程的生物学环节。

[Explore the Feedback Model → Model](https://chatgpt.com/c/Drylab/Model.md)

---

# 05 / DESIGNING FOR MEASUREMENT

## Making the Invisible Observable

### 让微观行为成为可以研究的证据

趋化、分子扩散和细胞接触都发生在微小的空间尺度上。

为了研究这些过程，我们需要能够观察、记录和量化相关行为的方法。

因此，测量方案也是 Friskoli 整体设计的一部分。

通过选择适当的实验条件、构建可控的化学环境，并使用显微成像和运动分析方法，我们希望将细胞的空间行为转化为可比较的数据。

其中，微流控提供了研究局部流体环境和化学梯度的实验途径。

图像分析和细胞运动追踪，则能够帮助我们从时间序列中提取细胞位置与行为信息。

这些测量方法也为检验模型预测提供了进一步的可能。

[Explore Our Measurement → Measurement](https://chatgpt.com/c/Wetlab/Measurement.md)

---

# 06 / DESIGNING WITH RESPONSIBILITY

## Freedom to Move, Boundaries to Protect

### 为生物系统建立可靠边界

Friskoli 关注微生物的主动运动，也重视对其活动范围的管理。

在我们的应用设想中，微生物应当在受控的培养环境中发挥作用。

封闭的反应器结构、可靠的流体连接和清晰的运行条件，为安全使用生物系统提供了重要基础。

我们将这些需求纳入未来设备与实验方案的设计之中，并进一步研究微重力流体环境可能带来的特殊安全问题。

通过将生物学功能与安全要求共同考虑，我们希望逐渐形成更加完整、可靠的工程思路。

[Explore Safety → Safety](https://chatgpt.com/c/Project/Safety.md)

---

# 07 / BEYOND THE FIRST SUBSTRATE

## A Design for Further Exploration

### 从参考实例走向更多可能

纤维素为 Friskoli 提供了一个具体的研究入口。

通过这一参考实例，我们能够研究可溶性产物的形成、细胞对化学环境的响应，以及微生物运动与局部底物转化之间的联系。

但微尺度的相遇问题，也存在于其他具有空间不均一性和传质限制的反应体系中。

未来，研究者可以根据不同的底物、宿主和感知机制，探索与之相适应的工程设计。

我们希望 Friskoli 所建立的研究思路与计算工具，能够帮助这些新的探索获得更加清晰的起点。

## Epilogue · Where Life Meets Matter

在宏观尺度上，生物反应器由容器、流路和复杂的设备构成。

而在微观尺度上，许多重要的过程，始于一个细胞与一份底物之间的相遇。

Friskoli 希望理解这些相遇如何发生，以及我们能否通过生物学设计，让它们更有可能发生在需要的地方。

**Sometimes, a small change in direction can make an important encounter possible.**

有时候，一次微小的方向改变，就可能让一场重要的相遇成为可能。