## What is chemotaxis and how do bacteria find food?

### 细菌是如何寻找食物的？

想象你身处一片黑暗的海洋，周围散布着食物，却无法用眼睛看到它们。你会怎样找到食物？

细菌也面临着类似的问题。虽然细菌没有眼睛和鼻子，但它们能够感知周围环境中化学物质的浓度变化，并调整自己的运动方向。这种能力被称为**趋化性（Chemotaxis）**。

以大肠杆菌为例，大肠杆菌是怎么探索环境的呢？它有两种运动状态，由它的鞭毛的状态决定它是怎么运动的。

一种是随机翻滚状态“Tumble”，这出现在当环境对细菌不那么有利时，它会频繁地改变方向，寻找食物；但是一旦细菌发现自己正朝着食物浓度更高的区域运动时，它会减少翻滚，变为直线游走“Run”的状态，推动细菌朝某个特定方向前进。

通过这种方式，细菌虽然无法预先知道食物在哪里，却能逐渐向食物更丰富的区域聚集。

这里有一个有趣的问题：细菌究竟如何将周围食物浓度的变化，转化成对自身运动的控制呢？

## How Does the PTS System and CheY Guide Bacteria?

### PTS 系统如何帮助细菌寻找食物？

要回答这个问题，我们首先需要认识一位控制细菌运动的重要角色——**CheY-P**。这种磷酸化蛋白的浓度控制了我们刚刚提到的“Tumble”和“Run”的状态的出现。

（示意图，画面需美化，文字需翻译）

![image-20261012213319240](./Images_of_descrption/image-20261012213319240.png)

那么 CheY-P 水平，是如何跟细菌感知到食物有关的呢？

对于许多糖类，大肠杆菌拥有一套特殊的系统，叫作**磷酸烯醇式丙酮酸依赖型糖磷酸转移酶系统（PTS）**。

PTS系统是大肠杆菌“运输食物”和“传递信号”的一套精密装置。当细菌摄取 PTS 糖时，PTS系统会将转运进来的糖类贴上磷酸标签。

而这个磷酸又是从哪里来的呢？这是由细胞中一条磷酸传递链去完成的：磷酸基团先由上游的磷酸烯醇式丙酮酸 (PEP)传递给系统中一种叫作 EI 的蛋白质，再由 EI 传递给糖类（PEP → EI → HPr → EII → Sugar）。未磷酸化的EI要想重新从PEP获得磷酸基团，必须先形成一个二聚体，而二聚化是整个接力过程中最慢的一步。当细菌遇到PTS糖并开始高速转运时，EI的去磷酸化速度远快于其再磷酸化速度。这会导致细胞内未磷酸化 EI 的浓度升高。(Lux et al., 1995)

这些未磷酸化的 EI 不仅参与糖运输，还能够抑制趋化信号蛋白 CheA 的活性，进而使下游 CheY-P 的水平下降，最终使细菌的鞭毛状态发生改变，细菌更倾向于直线游走。

借助PTS系统，细菌可以将 “吃到了食物~” 这一信息转化为“ 朝着这个方向前进！”

## Awakening E. coli's Hidden Sugar Utilization Systems

### 唤醒大肠杆菌沉睡的糖利用系统

既然 PTS 系统能够将糖的摄取与细菌的趋化行为联系起来，我们想利用这一机制，让工程菌主动寻找纤维素颗粒。

但是纤维素（Cellulose）是由葡萄糖单元连接而成的天然高分子，通常不溶于水，无法被细菌的 PTS 系统感知到。我们需要找到一种可溶性物质信号，能够告诉细菌“纤维素颗粒在哪里”。

我们想到使用在大肠杆菌表面展示纤维素酶的策略，在纤维素酶（Cellulase）的作用下，纤维素分子链可以逐步被降解，释放出的主要产物之一为纤维二糖。纤维二糖为一种可溶性糖类，由两个葡萄糖单元组成。

团队大胆提出设想，假如纤维素颗粒周围不断释放纤维二糖这种可溶性糖，形成由近及远的浓度梯度，我们再将其作为趋化信号，利用纤维二糖 PTS 系统，细菌就能够沿着这一信号找到纤维素颗粒。

那么要如何实现这一工程构想呢?

我们首先选择了大肠杆菌作为我们的底盘，因为大肠杆菌的趋化性被研究得比较多，而且它的遗传操作技术也相对成熟。

我们在调查文献后查到，大肠杆菌的基因组中本身就存在 PTS 糖转运和代谢有关的基因：asc 操纵子和 chb 操纵子。只是在通常条件下，它们的表达受到严格沉默。asc 系统包含参与糖转运的 AscF 和参与糖代谢的 AscB；而 chb 系统则包含 ChbA、ChbB、ChbC 等 PTS 转运组分，以及参与后续糖代谢的 ChbF。

虽然这些系统并非天然专门用于高效利用纤维二糖，但已有研究表明(Vinuselvi & Lee, 2011)，通过适当的遗传改造，大肠杆菌可以利用这些内源性基因获得纤维二糖转运和代谢能力。接下来我们的工程改造重点放在，尝试唤醒它本来就拥有的糖利用能力。

## Engineering Bacteria to Follow Cellobiose

## 改造细菌，使其能够追踪纤维二糖

### Stage I : Plasmid-Based Expression：asc and chb operon

我们最初采用质粒表达策略，尝试增强大肠杆菌对纤维二糖的摄取与利用能力。首先，我们选择了结构相对简单的 **asc 系统**，其主要包含两个功能蛋白：

- **AscF：** PTS 糖转运蛋白，参与纤维二糖等 β-葡萄糖苷类糖的转运。
- **AscB：** 磷酸化 β-葡萄糖苷酶，参与摄入糖的后续水解与代谢。

由于 ascFB 所需表达的功能基因较少，我们首先构建了 **ascFB 质粒表达系统**，探索其对纤维二糖利用能力和趋化响应的影响。

初步测试未观察到预期的明显改善，因此我们进一步尝试了 **chbBCAF 质粒表达方案**。该系统包含 ChbA、ChbB、ChbC 等 PTS 转运组分，以及参与糖代谢的 ChbF。然而，该方案未能获得经验证的有效转化子。

因此，我们决定从质粒表达转向对内源性操纵子的基因组改造。

### Stage II : Engineering the chb Operon

Vinuselvi 和 Lee（2011）的研究表明，使用人工组成型启动子 CP12 替换天然 chb 启动子，可使大肠杆菌利用纤维二糖作为唯一碳源生长。

基于这一研究，我们采用**chromosomal promoter replacement**，首先将 chb 的天然启动子替换为 CP12，随后引入不同强度的 CP 系列启动子，构建了一系列启动子替换菌株。通过调控 chb 操纵子的表达，我们希望比较不同工程菌的纤维二糖利用能力，并进一步探索糖转运能力与趋化响应之间的关系。

**Can enhanced cellobiose utilization lead to improved chemotaxis?**

如果这一设想能够实现，纤维二糖就不仅是细菌的营养来源，还能成为引导工程菌寻找纤维素颗粒的导航信号。







Reference

Lux, R., Jahreis, K., Bettenbrock, K., Parkinson, J. S., & Lengeler, J. W. (1995). Coupling the phosphotransferase system and the methyl-accepting chemotaxis protein-dependent chemotaxis signaling pathways of Escherichia coli. Proceedings of the National Academy of Sciences, 92(25), 11583–11587. https://doi.org/10.1073/pnas.92.25.11583

Vinuselvi, P., & Lee, S. K. (2011). Engineering Escherichia coli for efficient cellobiose utilization. Applied Microbiology and Biotechnology, 92, 125–132. https://doi.org/10.1007/s00253-011-3434-9
