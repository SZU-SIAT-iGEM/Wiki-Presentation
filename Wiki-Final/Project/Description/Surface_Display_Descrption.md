## Surface Display: Engineering Whole-Cell Biocatalysts for Cellulose Degradation

## Where Does the Cellobiose Signal Come From?

### 纤维二糖信号从何而来？

在前面的趋化模块中，我们希望利用纤维二糖作为化学信号，引导工程菌向纤维素颗粒附近聚集。

然而，纤维二糖并不会凭空产生。它需要通过纤维素酶对固体纤维素的降解而释放。

在我们的设想中，少量工程菌可以通过随机运动或初始空间分布首先接触纤维素颗粒，其携带的纤维素酶参与局部降解，释放包括纤维二糖在内的可溶性糖。如果这些糖在颗粒附近形成可被细菌感知的浓度梯度，便可能吸引更多工程菌向底物区域聚集，从而增加后续的酶与底物接触机会。

为了实现这一构想，我们需要让工程菌携带能够降解纤维素的酶。

## Why Cell Surface Display?

### 为什么选择细胞表面展示？

在微重力环境中，重力驱动的自然对流受到显著抑制，游离酶与固体纤维素之间的接触更加依赖扩散及其他混合机制。

如果采用传统的分泌型酶策略，部分游离酶可能扩散至远离纤维素颗粒的区域，降低局部有效酶浓度。

![地面与微重力下的细胞表面展示方案 (1)](./../../../Project/Engineering/images%20of%20wetlabDBTL/%E5%9C%B0%E9%9D%A2%E4%B8%8E%E5%BE%AE%E9%87%8D%E5%8A%9B%E4%B8%8B%E7%9A%84%E7%BB%86%E8%83%9E%E8%A1%A8%E9%9D%A2%E5%B1%95%E7%A4%BA%E6%96%B9%E6%A1%88%20(1).png)

因此，我们选择**细胞表面展示技术（Cell Surface Display）**，通过锚定蛋白将纤维素酶固定在工程菌表面，使细菌成为能够携带纤维素酶运动的全细胞生物催化剂（Whole-Cell Biocatalyst）。

我们希望通过这种方式，将细菌的运动能力与纤维素酶的局部催化功能结合起来，减少游离酶的空间分散，并提高工程菌接近底物时的有效催化机会。

## Selecting Our Cellulases

## 多酶协同降解：纤维素酶的选择

我们希望降解的目标材料包括废旧棉织物等富含纤维素的固体废弃物。纤维素（Cellulose）由葡萄糖通过 β-1,4 糖苷键连接而成，其分子链之间存在大量氢键，形成了结构紧密、难以降解的天然高分子材料。

因此，纤维素的高效降解通常需要不同类型的纤维素酶协同作用。内切型纤维素酶能够切割纤维素链内部的糖苷键，而外切型及过程性纤维素酶则能够沿纤维素链进一步降解，释放纤维二糖等可溶性产物。

对于 Friskoli，我们不仅希望降解纤维素，还希望产生足够的**纤维二糖（Cellobiose）**作为趋化模块的可溶性糖信号。参考 Leis et al.（2017）对 *Clostridium thermocellum* 纤维小体纤维素酶的系统研究，我们选择了三种具有不同催化特征的纤维素酶：

| Cellulase  | GH Family | Catalytic Mode                     | Expected Role in Friskoli                                    |
| ---------- | --------- | ---------------------------------- | ------------------------------------------------------------ |
| **Cel48S** | GH48      | Processive cellobiohydrolase (CBH) | Degrades cellulose from reducing ends and releases cellobiose. |
| **Cel9K**  | GH9       | Processive cellobiohydrolase (CBH) | Degrades cellulose from non-reducing ends and releases cellobiose. |
| **Cel5L**  | GH5_1     | Processive endoglucanase (pEG2)    | Cleaves internal cellulose bonds and releases cellobiose, potentially creating new chain ends. |

其中 Cel5L 对纤维素链内部的切割能够为其他酶提供更多可利用位点，而 Cel48S 和 Cel9K 则分别从纤维素还原端和从非还原端进一步降解纤维素。通过这样的组合，我们期望提高复杂纤维素底物的降解效率，并促进纤维二糖的大量释放。

## Anchoring Enzymes to the Cell Surface

## 如何将纤维素酶固定在细胞表面？

为了让纤维素酶固定在大肠杆菌表面，我们需要一种能够将目标蛋白定位到细胞外膜的**锚定蛋白（Anchor Protein）**。

我们最初选择了来源于丁香假单胞菌（*Pseudomonas syringae*）冰核蛋白（Ice Nucleation Protein, INP）的截短变体 **INPNC**。

INPNC 保留了天然冰核蛋白的 N 端和 C 端区域，去除了较长的中央重复区域，已被用于细菌细胞表面展示研究。(Liu et al., 2025)

![大肠杆菌外膜三种表面展示构建体示意图](./Images_of_descrption/%E5%A4%A7%E8%82%A0%E6%9D%86%E8%8F%8C%E5%A4%96%E8%86%9C%E4%B8%89%E7%A7%8D%E8%A1%A8%E9%9D%A2%E5%B1%95%E7%A4%BA%E6%9E%84%E5%BB%BA%E4%BD%93%E7%A4%BA%E6%84%8F%E5%9B%BE.png)我们计划将 INPNC 与 Cel48S、Cel9K 和 Cel5L 分别融合表达，利用 INPNC 的膜定位特征，使纤维素酶有机会暴露在大肠杆菌细胞表面。

通过这一设计，我们希望将纤维素酶固定在工程菌表面，使其随细菌共同移动，并在接触纤维素颗粒时参与局部降解。

## Microbial Cocktail: A Multi-Strain System

## Microbial Cocktail：多菌株催化体系

在确定纤维素酶组合后，我们选择采用**多菌株协同策略（Microbial Cocktail）**，而不是让单株大肠杆菌同时表达三种大型纤维素酶。

我们计划构建三株独立的工程菌，每株分别展示一种纤维素酶：

- **Strain 1：** 表面展示 Cel48S
- **Strain 2：** 表面展示 Cel9K
- **Strain 3：** 表面展示 Cel5L

为了将这些纤维素酶固定在细胞表面，我们最初选择了 **INPNC** 作为锚定蛋白（Anchor Protein），通过融合表达将纤维素酶连接到大肠杆菌的细胞表面。

这种混合微生物鸡尾酒的设计具有两个主要优势：

首先，每株菌只需表达一种纤维素酶融合蛋白，有助于降低单株细胞同时表达多个大型蛋白所带来的潜在负担。

其次，不同菌株可以独立构建和表征，使我们能够分别评估三种纤维素酶的表达及功能，并在后续调整不同菌株的组合比例。

最终，我们希望将三株工程菌组合成一个 **Microbial Cocktail**，利用不同纤维素酶的催化互补性参与固体纤维素降解，并产生能够被趋化系统感知的纤维二糖信号。这一设计将细胞表面展示与 PTS 趋化系统联系起来，为探索微重力弱混合环境下的主动底物接近与局部催化提供了工程基础。

## Reference

Leis, B., Held, C., Bergkemper, F., Dennemarck, K., Steinbauer, R., Reiter, A., Mechelke, M., Moerch, M., Graubner, S., Liebl, W., Schwarz, W. H., & Zverlov, V. V. (2017). Comparative characterization of all cellulosomal cellulases from Clostridium thermocellum reveals high diversity in endoglucanase product formation essential for complex activity. Biotechnology for Biofuels, 10, Article 240. https://doi.org/10.1186/s13068-017-0928-4

Liu, W., Sun, W., Liang, C. C., Chen, T., Zhuang, W., Liu, D., Chen, Y., & Ying, H. (2025). Escherichia coli surface display: Advances and applications in biocatalysis. ACS Synthetic Biology, 14(3), 648–661. https://doi.org/10.1021/acssynbio.4c00793
