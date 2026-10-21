# Results

## Overview

Friskoli 的湿实验工程围绕两个主要目标展开：一是改造大肠杆菌的糖转运系统，提高其对纤维二糖的利用能力，并探索能否进一步产生趋化响应；二是利用细胞表面展示技术，使工程菌能够直接作用于固体纤维素底物。

在糖转运模块中，我们从 `ascFB` 和 `chb` 质粒表达路线转向染色体启动子替换，最终建立了 CP 系列 `chb` 工程菌，并从转录、生长及表观底物消耗三个层面进行了表征。在趋化模块中，我们开展了软琼脂实验，并尝试使用 RPM 和微流控装置进行更进一步探究。在表面展示模块中，我们完成了多个 INPNC–cellulase 表达盒的组装及后续排查，但尚未获得功能得到确认的表面展示菌株。

以下按照各项实验的目标、方法和实际结果展示主要发现。

---

## Result 1 — Construction of CP-chb Strains

### Goal

获得能够调控内源 `chb` 操纵子表达的工程菌株，为比较不同转录水平下的纤维二糖利用及趋化表型提供基础。

### Method

在早期 `ascFB` 质粒构建未产生预期功能增强、`chb` 质粒表达路线未获得稳定转化子的情况下，我们转向染色体启动子替换策略。通过 λ-Red 同源重组，将 MG1655 内源 `chb` 启动子区域替换为 CP 系列组成型启动子，并通过菌落 PCR 和测序筛选、验证候选菌株。

### result

我们首先成功获得并验证了 CP12CHB，随后将替换策略扩展至 CP6、CP7、CP25、CP30、CP44 和 CP9a。

PCR 与测序结果显示，CP12CHB 的编辑区域与设计序列一致。在后续构建中，CP9a 未获得转化菌落；其他启动子替换实验获得了候选菌株。其中，CP6-1 的启动子区域存在一个额外突变，其余已测序的目标克隆与预期序列一致。

https://static.igem.wiki/teams/6100/wiki/results-of-wetlab/results-plate-of-cpseries.avif

测序结果：

https://static.igem.wiki/teams/6100/wiki/results-of-wetlab/cp7seq.avif

https://static.igem.wiki/teams/6100/wiki/results-of-wetlab/cp25seq.avif

https://static.igem.wiki/teams/6100/wiki/results-of-wetlab/cp12seq.avif

https://static.igem.wiki/teams/6100/wiki/results-of-wetlab/cp30seq.avif

https://static.igem.wiki/teams/6100/wiki/results-of-wetlab/cp44seq.avif

https://static.igem.wiki/teams/6100/wiki/results-of-wetlab/cp6seq.avif

这些结果表明，染色体启动子替换策略使我们获得了具有不同 `chb` 调控背景的工程菌株，并能够进一步开展功能比较。

---

## Result 2 — RT-qPCR Characterization of CP-chb Strains

### Goal

比较不同 CP 启动子替换菌株的实际转录水平，判断文献报道的启动子强度差异能否在染色体 `chb` 调控背景下得到体现。

### Method

使用 RT-qPCR 检测替换启动子下游、包含 `chbB` 起始部分的目标区域。以 *cysG* 为内参，WT MG1655 为参照，通过 ΔΔCt 法计算各菌株的相对转录丰度。

### result

不同 CP 菌株的目标区域转录水平存在明显差异。CP30 和 CP44 的相对转录水平最高，CP25 次之，CP12 表现出一定程度的转录上调，而 CP6 和 CP7 的测量结果接近 WT。

https://static.igem.wiki/teams/6100/wiki/results-of-wetlab/a6-2-qpcr.avif

本次测得的转录丰度排序与 Jensen and Hammer（1998）报道的启动子相对活性排序不一致。这说明文献中的启动子活性不能直接用于预测其在当前染色体 `chb` 调控背景下的实际转录水平。

---

## Result 3 — Cellobiose-dependent Growth of CP-chb Strains

### Goal

检验 CP 启动子调控的转录差异是否伴随纤维二糖相关生长表型的变化，并比较不同工程菌的生长表现。

### Method

分别在 M9 + cellobiose 和 M9 + glucose 条件下连续监测 CP6、CP7、CP12、CP25、CP30、CP44 及 WT MG1655 的 24 h OD₆₀₀。以空白校正后的数据绘制生长曲线，并使用最大 6 h 表观比生长速率（μ_app,6h,max）辅助比较。

### result

在葡萄糖条件下，所有测试菌株均能够生长。在纤维二糖条件下，CP12、CP25、CP30 和 CP44 的 OD₆₀₀ 随时间明显增加，CP6 和 CP7 的增长较弱，WT MG1655 则基本没有增长。

https://static.igem.wiki/teams/6100/wiki/results-of-wetlab/cpseries-1.avif

在纤维二糖条件下，CP12、CP25、CP30 和 CP44 的最大 6 h 表观比生长速率约为 0.07–0.09 h⁻¹，CP6 约为 0.038 h⁻¹；CP7 和 WT 未能筛选出可靠的持续增长区间，因此不报告对应数值。

https://static.igem.wiki/teams/6100/wiki/results-of-wetlab/1-1.avif

结合 RT-qPCR 结果，CP12 虽然具有低于 CP30 和 CP44 的转录水平，却表现出相近的纤维二糖相关生长速率，说明转录丰度与生长表现并非简单的正比例关系。

本次连续生长曲线仅包含三个技术重复，没有独立生物学重复，因此测量的结果具有一定的局限性。

---

## Result 4 — DNS-based Apparent Substrate Consumption

### Goal

比较不同 CP 工程菌对纤维二糖的表观消耗能力，并进一步观察其与转录水平及生长表型之间的关系。

### Method

首先使用 CP12CHB 和 WT MG1655 验证 DNS 法对上清还原糖变化的检测可行性；随后对 CP6、CP7、CP12、CP25、CP30、CP44 和 WT 开展比较。各菌株设置三个独立生物学重复，在含 1 mM 纤维二糖的反应体系中于不同时间点收集上清，并使用 DNS 法测量还原糖浓度。结合各重复的 OD₆₀₀，计算 0–60 min 内归一化的表观平均消耗速率。

### result

预实验显示，CP12CHB 的上清还原糖浓度随时间下降，而 WT 基本保持稳定。在 CP 系列比较中，WT 的上清还原糖浓度同样变化较小，CP 工程菌则表现出不同程度的下降。其中，CP12 的下降最明显，CP30、CP7、CP44 和 CP25 也出现较明显的消耗趋势，CP6 相对较弱。

[image-20261019225115082.avif (1560×1140)](https://static.igem.wiki/teams/6100/wiki/results-of-wetlab/image-20261019225115082.avif)

https://static.igem.wiki/teams/6100/wiki/results-of-wetlab/image-20261019223408045.avif

按 OD₆₀₀ 归一化后，CP12 和 CP7 的表观平均消耗速率最高，均约为 0.0095 μmol·mL⁻¹·min⁻¹·OD₆₀₀⁻¹，CP44 和 CP30 次之。

[image-20261019223505057.avif (1680×1140)](https://static.igem.wiki/teams/6100/wiki/results-of-wetlab/image-20261019223505057.avif)

值得注意的是，CP7 的目标区域转录水平较低、纤维二糖相关生长较弱，但其归一化表观消耗速率却比较异常，与 CP12 接近。具体的机制和原因还待我们下一步排查。

需要注意的是，CP12 在 30 min 时的剩余还原糖浓度已低于本批标准曲线的可靠定量范围，因此本次 0–60 min 平均速率尚不能准确区分部分高消耗菌株的早期消耗能力。

---

## Result 5 — Soft Agar Migration Assessment of CP-chb Strains

### Goal

评估 CP 系列工程菌在纤维二糖条件下的群体迁移表现，探索纤维二糖浓度变化是否引起与 WT 不同的扩展表型，并初步观察 RPM 模拟微重力培养条件下的迁移变化。

### Method

采用含 1% 胰蛋白胨和 0.35% 琼脂的软琼脂体系，对 CP6、CP7、CP12、CP25、CP30、CP44 及 WT MG1655 进行多点接种。

第一轮比较 10 mM 纤维二糖、10 mM 葡萄糖及无额外糖添加条件。第二轮增加 1 mM 纤维二糖，并设置 L-天冬氨酸和葡萄糖阳性参照，同时比较地面静置与 RPM 培养条件下的菌斑扩展表现。

### result

**1. Cellobiose supplementation altered colony expansion**

第一轮实验中，CP12、CP30 和 CP44 在添加 10 mM 纤维二糖后形成了比无糖组更大的可见菌斑，而其他菌株的变化相对不明确。

葡萄糖组出现明显的异常浑浊，未能获得可靠的迁移圈判定结果。

这一现象提示，纤维二糖添加能够影响部分工程菌的局部生长或群体扩展，但无法区分生长与趋化的贡献。

https://static.igem.wiki/teams/6100/wiki/images-of-wetlab-dbtl/dbtl-a/cp-series.avif

**2. Cellobiose concentration affected migration phenotypes**

第二轮地面实验中，多数 CP 工程菌在 10 mM 纤维二糖条件下的可见菌斑小于 1 mM 条件。其中，CP12、CP44和 CP25 的变化较为明显，CP44 也表现出一定的减小趋势；CP6 CP7的差异不明显，CP30 则未表现出相同趋势。

相比之下，WT 在 10 mM 纤维二糖条件下形成了更大的菌斑，与多数 CP 工程菌呈现相反的变化方向。

L-天冬氨酸和葡萄糖参照组的部分接种点形成了较小菌斑，与已知吸引剂可能减缓软琼脂群体迁移的文献现象是相符合的。

这一结果有可能支持CP12,CP44,CP25菌株可能具有较强的趋化迁移能力，但群体迁移速度还是会受到生长和代谢的影响，所以本方法并不能直接判定CP系列菌株对纤维二糖有趋化结果。我们需要更进一步的实验，需要一个人为制造纤维二糖浓度梯度的趋化实验来观察工程菌的趋化，而非通过细菌自身生长消耗糖形成梯度的实验来观察趋化。

https://static.igem.wiki/teams/6100/wiki/results-of-wetlab/image-20261021024323345.avif

**3. Exploratory assessment under RPM exposure**

在 RPM 培养条件下，保留的 10 mM 纤维二糖平板上，WT 与部分 CP 工程菌仍能形成可见菌斑。与地面静置组相比，多个菌株的扩展范围似乎减小。所以RPM的培养环境和地面环境还是有较大差异。

这提示着我们未来的应用投放不能简单地认为地面实验取得的成果可以简单复用在微重力条件下，我们仍需经过多轮微重力模拟测试工程菌的各项参数是否与地面环境有差异。

https://static.igem.wiki/teams/6100/wiki/results-of-wetlab/image-20261021024340505.avif

---

## Result 6 — Development of a Microfluidic Chemotaxis Observation System

### Goal

尝试建立能够在化学梯度下观察细菌运动的微流控测量体系，为后续区分主动趋化与被动流体位移提供条件。

### Method

制作三流道 PDMS 芯片并与凝胶层组装，逐步调整接口加工、通液方式及显微观察条件。采用天冬氨酸作为初步观察用的吸引物，先后比较琼脂和琼脂糖底层，并调整菌液重悬体系及密度。

### result

通过改进接口加工和组装顺序，部分流道的连通性得到改善；使用琼脂糖替代琼脂后，显微背景更加清晰，能够辨认流道中的菌体。调整菌液浓度及重悬液后，观察背景中的杂质与菌体密度也有所改善。

但在后续观察中，管路压力变化与液体回流仍明显干扰了菌体的表观位移，无法可靠区分主动运动和被动流体迁移。

**[Figure 10. Microfluidic chip assembly and preliminary observations]**

*待插入：芯片实物、流道示意及代表性显微图。*

截至 Wiki 截止时，我们尚未获得可用于定量分析的连续运动轨迹，也未完成 CP 系列工程菌的有效微流控趋化比较。因此，这一部分属于趋化测量平台开发的阶段性结果，而不是趋化能力的阳性或阴性验证。

---

## Result 7 — Initial INPNC–Cellulase Surface-display Constructs

### Goal

构建分别展示 Cel48S、Cel9K 和 Cel5L 的工程菌，并检验所获得候选菌株是否携带目标表达盒、表现出可检测的纤维素降解活性。

### Method

使用 pCDF-based backbone，分别通过 Gibson Assembly 组装三种 INPNC–cellulase 表达盒。将组装产物转化 MG1655 后，通过抗生素平板筛选、colony PCR、assembly-product PCR 和 CMC–Congo red assay 进行验证。

### result

三个组装产物均能够通过 PCR 检测到预期 DNA 结构，但候选菌落的 colony PCR 未获得目标条带，CMC–Congo red assay 也未显示可靠的纤维素水解圈。

进一步筛选测试显示，WT MG1655 在 streptomycin、spectinomycin 及相关筛选条件下仍能生长，说明原有抗性体系无法可靠区分真正的转化子与未转化菌株。

因此，虽然我们在组装产物中检测到了目标 DNA 结构，但未能获得经过基因型及功能双重验证的 INPNC–cellulase 工程菌。

---

## Result 8 — Rebuilding and Troubleshooting the Surface-display System

### Goal

排除原有抗生素筛选失败的影响，进一步判断载体与表达调控策略的调整能否改善 INPNC–cellulase 构建结果。

### Method

将表达系统更换为 pACYC-based backbone 与 chloramphenicol selection，并比较 WT、空载体及 INPNC–cellulase 构建的转化表现。随后将原有组成型表达策略调整为 Ptac-lacO，分别测试 Ptac-GFP 和 Ptac-INPNC-Cel9K。

### result

更换筛选体系后，WT 被有效抑制，空载体能够获得转化子，但三种 INPNC–cellulase 构建仍未获得可靠的重组菌落。

使用 Ptac-lacO 后，Ptac-GFP 获得了候选转化子，且 colony PCR 证实其携带预期 DNA 结构；Ptac-INPNC-Cel9K 仍未获得转化子。

https://static.igem.wiki/teams/6100/wiki/results-of-wetlab/re-sd.avif

这些结果说明，更新后的载体、筛选和克隆流程能够支持较简单的 GFP 构建，但仍未成功建立所测试的 INPNC–cellulase 融合系统。仅将 J23116 更换为 Ptac-lacO 并不足以解决这一问题。

基于这些结果，我们提出 Lpp-OmpA 替代锚定方案，但该方案尚未完成构建和功能验证。

