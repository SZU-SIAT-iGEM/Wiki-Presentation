# Results

## Overview

Friskoli 的湿实验工程围绕两个主要目标展开：一是改造大肠杆菌的糖转运系统，提高其对纤维二糖的利用能力，并探索能否进一步产生趋化响应；二是利用细胞表面展示技术，使工程菌能够直接作用于固体纤维素底物。

在糖转运模块中，我们从 `ascFB` 和 `chb` 质粒表达路线转向染色体启动子替换，最终建立了 CP 系列 `chb` 工程菌，并从转录、生长及表观底物消耗三个层面进行了表征。在趋化模块中，我们开展了软琼脂实验，并尝试使用 RPM 和微流控装置进行补充验证。在表面展示模块中，我们完成了多个 INPNC–cellulase 表达盒的组装及后续排查，但尚未获得功能得到确认的表面展示菌株。

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

![Results-plate-of-CPseries](./../../Project/Engineering/images%20of%20wetlabDBTL/Results-plate-of-CPseries.png)

**[Figure 1. CP-chb chromosomal promoter replacement and genotypic verification]**

*待插入：染色体启动子替换示意图、代表性 PCR 电泳及测序结果。*

这些结果表明，染色体启动子替换策略使我们获得了具有不同 `chb` 调控背景的工程菌株，并能够进一步开展功能比较。

---

## Result 2 — RT-qPCR Characterization of CP-chb Strains

### Goal

比较不同 CP 启动子替换菌株的实际转录水平，判断文献报道的启动子强度差异能否在染色体 `chb` 调控背景下得到体现。

### Method

使用 RT-qPCR 检测替换启动子下游、包含 `chbB` 起始部分的目标区域。以 *cysG* 为内参，WT MG1655 为参照，通过 ΔΔCt 法计算各菌株的相对转录丰度。

### result

不同 CP 菌株的目标区域转录水平存在明显差异。CP30 和 CP44 的相对转录水平最高，CP25 次之，CP12 表现出一定程度的转录上调，而 CP6 和 CP7 的测量结果接近 WT。

**[Figure 2. Relative transcription levels of CP-chb strains]**

*待插入：A6.2 RT-qPCR 结果图。*

本次测得的转录丰度排序与 Jensen and Hammer（1998）报道的启动子相对活性排序不一致。这说明文献中的启动子活性不能直接用于预测其在当前染色体 `chb` 调控背景下的实际转录水平。

---

## Result 3 — Cellobiose-dependent Growth of CP-chb Strains

### Goal

检验 CP 启动子调控的转录差异是否伴随纤维二糖相关生长表型的变化，并比较不同工程菌的生长表现。

### Method

分别在 M9 + cellobiose 和 M9 + glucose 条件下连续监测 CP6、CP7、CP12、CP25、CP30、CP44 及 WT MG1655 的 24 h OD₆₀₀。以空白校正后的数据绘制生长曲线，并使用最大 6 h 表观比生长速率（μ_app,6h,max）辅助比较。

### result

在葡萄糖条件下，所有测试菌株均能够生长。在纤维二糖条件下，CP12、CP25、CP30 和 CP44 的 OD₆₀₀ 随时间明显增加，CP6 和 CP7 的增长较弱，WT MG1655 则基本没有增长。

**[Figure 3. Growth curves of CP-chb strains under different carbon sources]**

*待插入：CP 系列在 cellobiose 和 glucose 条件下的 24 h 生长曲线。*

在纤维二糖条件下，CP12、CP25、CP30 和 CP44 的最大 6 h 表观比生长速率约为 0.07–0.09 h⁻¹，CP6 约为 0.038 h⁻¹；CP7 和 WT 未能筛选出可靠的持续增长区间，因此不报告对应数值。

**[Figure 4. Maximum 6-hour apparent specific growth rates]**

*待插入：A6.3 表观比生长速率比较图。*

结合 RT-qPCR 结果，CP12 虽然具有低于 CP30 和 CP44 的转录水平，却表现出相近的纤维二糖相关生长速率，说明转录丰度与生长表现并非简单的正比例关系。

本次连续生长曲线仅包含三个技术重复，没有独立生物学重复，因此菌株之间的差异仍需作为初步观察结果解释。

---

## Result 4 — DNS-based Apparent Substrate Consumption

### Goal

比较不同 CP 工程菌对纤维二糖的表观消耗能力，并进一步观察其与转录水平及生长表型之间的关系。

### Method

首先使用 CP12CHB 和 WT MG1655 验证 DNS 法对上清还原糖变化的检测可行性；随后对 CP6、CP7、CP12、CP25、CP30、CP44 和 WT 开展比较。各菌株设置三个独立生物学重复，在含 1 mM 纤维二糖的反应体系中于不同时间点收集上清，并使用 DNS 法测量还原糖浓度。结合各重复的 OD₆₀₀，计算 0–60 min 内归一化的表观平均消耗速率。

### result

预实验显示，CP12CHB 的上清还原糖浓度随时间下降，而 WT 基本保持稳定。在 CP 系列比较中，WT 的上清还原糖浓度同样变化较小，CP 工程菌则表现出不同程度的下降。其中，CP12 的下降最明显，CP30、CP7、CP44 和 CP25 也出现较明显的消耗趋势，CP6 相对较弱。

**[Figure 5. Changes in residual reducing sugar concentrations]**

*待插入：A6.4 剩余还原糖浓度时间曲线及 60 min 终点比较图。*

按 OD₆₀₀ 归一化后，CP12 和 CP7 的表观平均消耗速率最高，均约为 0.0095 μmol·mL⁻¹·min⁻¹·OD₆₀₀⁻¹，CP44 和 CP30 次之。

**[Figure 6. OD₆₀₀-normalized apparent substrate consumption rates]**

*待插入：A6.4 归一化表观平均消耗速率图。*

值得注意的是，CP7 的目标区域转录水平较低、纤维二糖相关生长较弱，但其归一化表观消耗速率却与 CP12 接近。结合 CP12、CP30 和 CP44 的转录及生长数据可见，三个功能指标之间并不存在简单的一一对应关系。

**[Figure 7. Integrated characterization of CP-chb strains]**

*待插入：RT-qPCR、生长速率及 DNS 表观消耗速率综合比较图。*

需要注意的是，CP12 在 30 min 时的剩余还原糖浓度已低于本批标准曲线的可靠定量范围，因此本次 0–60 min 平均速率尚不能准确区分部分高消耗菌株的早期消耗能力。DNS 法测得的也是上清还原糖变化，不能直接等同于特异性转运速率。

---

## Result 5 — Soft Agar Migration Assay

### Goal

检验 CP 系列工程菌在纤维二糖条件下是否出现与 WT 不同的迁移扩展表型，并探索这些变化能否为趋化响应提供证据。

### Method

先对 CP12CHB 进行初步软琼脂测试，随后扩展至 CP6、CP7、CP12、CP25、CP30、CP44 和 WT。调整前培养条件后，采用含 1% 胰蛋白胨和 0.35% 琼脂的平板，分别设置纤维二糖、葡萄糖及无额外添加糖条件，观察菌斑形成与扩展情况。

### result

初步实验未观察到 CP12CHB 明显增强的纤维二糖迁移表型。后续 CP 系列实验中，部分工程菌在纤维二糖条件下形成了比 WT 或无额外添加糖条件更明显的局部菌斑。

然而，无额外添加糖的平板同样支持一定程度的菌斑形成；葡萄糖组出现大面积浑浊，未能获得可独立判读的迁移边界。

**[Figure 8. Soft agar migration phenotypes of CP-chb strains]**

*待插入：CP 系列不同碳源条件下的软琼脂平板照片。*

这些观察表明，部分 CP 工程菌在纤维二糖条件下具有不同的局部生长或迁移扩展表现。但纤维二糖同时是碳源和潜在趋化信号，菌斑扩大无法直接归因于定向趋化。现有结果尚不足以证明 CP 工程菌具有明显增强的纤维二糖定向趋化能力。

---

## Result 6 — RPM-based Soft Agar Assessment

### Goal

比较 RPM 旋转处理与常规静置条件下的软琼脂表型，为 Friskoli 的微重力相关研究提供补充观察。

### Method

**[待补充：RPM 装置参数、实际测试菌株、平板条件、处理时间及静置对照设置。]**

### result

**[待补充：RPM 与对照组的实际平板结果及可支持的结论。]**

**[Figure 9. Soft agar phenotypes under RPM treatment and stationary controls]**

*待插入：RPM 实验照片及对照结果。RPM 处理不能直接等同于真实微重力环境，也不能单凭软琼脂表型证明液相弱传质被克服。*

---

## Result 7 — Development of a Microfluidic Chemotaxis Observation System

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

## Result 8 — Initial INPNC–Cellulase Surface-display Constructs

### Goal

构建分别展示 Cel48S、Cel9K 和 Cel5L 的工程菌，并检验所获得候选菌株是否携带目标表达盒、表现出可检测的纤维素降解活性。

### Method

使用 pCDF-based backbone，分别通过 Gibson Assembly 组装三种 INPNC–cellulase 表达盒。将组装产物转化 MG1655 后，通过抗生素平板筛选、colony PCR、assembly-product PCR 和 CMC–Congo red assay 进行验证。

### result

三个组装产物均能够通过 PCR 检测到预期 DNA 结构，但候选菌落的 colony PCR 未获得目标条带，CMC–Congo red assay 也未显示可靠的纤维素水解圈。

进一步筛选测试显示，WT MG1655 在 streptomycin、spectinomycin 及相关筛选条件下仍能生长，说明原有抗性体系无法可靠区分真正的转化子与未转化菌株。

因此，虽然我们在组装产物中检测到了目标 DNA 结构，但未能获得经过基因型及功能双重验证的 INPNC–cellulase 工程菌。

---

## Result 9 — Rebuilding and Troubleshooting the Surface-display System

### Goal

排除原有抗生素筛选失败的影响，进一步判断载体与表达调控策略的调整能否改善 INPNC–cellulase 构建结果。

### Method

将表达系统更换为 pACYC-based backbone 与 chloramphenicol selection，并比较 WT、空载体及 INPNC–cellulase 构建的转化表现。随后将原有组成型表达策略调整为 Ptac-lacO，分别测试 Ptac-GFP 和 Ptac-INPNC-Cel9K。

### result

更换筛选体系后，WT 被有效抑制，空载体能够获得转化子，但三种 INPNC–cellulase 构建仍未获得可靠的重组菌落。

使用 Ptac-lacO 后，Ptac-GFP 获得了候选转化子，且 colony PCR 证实其携带预期 DNA 结构；Ptac-INPNC-Cel9K 仍未获得转化子。

**[Figure 11. Validation and troubleshooting of the surface-display system]**

*待插入：氯霉素筛选结果、Ptac-GFP colony PCR 与 INPNC–Cel9K 转化结果。*

这些结果说明，更新后的载体、筛选和克隆流程能够支持较简单的 GFP 构建，但仍未成功建立所测试的 INPNC–cellulase 融合系统。仅将 J23116 更换为 Ptac-lacO 并不足以解决这一问题。

基于这些结果，我们提出 Lpp-OmpA 替代锚定方案，但该方案尚未完成构建和功能验证。

