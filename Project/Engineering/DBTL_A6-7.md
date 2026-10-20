# 路线 A 湿实验工程 DBTL：A6–A7

# DBTL A6 CP 系列启动子梯度菌株的构建与表征

## DBTL A6.1 CP 系列菌株的构建

## **Overview**

A5 中，我们用组成型启动子 CP12 替换 *E. coli* MG1655 染色体上内源 `chb` 操纵子的原有启动子区域，获得了 CP12CHB 工程菌。基因型验证确认了 CP12 替换；在纤维二糖培养条件下，CP12CHB 的 OD600 随时间增加，而 WT MG1655 未出现类似增长趋势。但初步软琼脂实验未提供 CP12CHB 具有明显增强的纤维二糖趋化表型的证据。

因此，我们进一步提出：改变 `chb` 的转录调控程度，能否产生不同的纤维二糖利用与迁移表型？ 为回答这一问题，我们构建了多个 CP 组成型启动子替换菌株，并按转录表达（RT-qPCR）、生长表型、软琼脂迁移和纤维二糖摄取速率的顺序开展功能表征。

## A6.1 Cycle 1｜构建 CP 系列启动子调控的 Chb 工程菌

### Design｜设计

A5 已证明用 CP12 替换内源 `chb` 启动子可激活 `chb` 系统，但单一 CP12 菌株不足以判断“转录调控程度”与“下游功能表型”的关系。因此，A6 在 MG1655 染色体上保留原有 `chb` 编码区，只替换其上游启动子，构建不同 CP 启动子调控的菌株系列，并以 WT MG1655 作对照。

我们参考文献，选择了一系列候选启动子：CP6、CP7、CP25、CP30、CP44、CP9a，加上已有 CP12，文献中的这些启动子的预期转录活性以及序列如下表所示。(Jensen & Hammer, 1998)

| Promoter                   | E.coli 相对活性（MU） | 5'‑3' DNA 序列                                               |
| -------------------------- | --------------------- | ------------------------------------------------------------ |
| CP44=CP45                  | 34                    | CATCGGGTAGTTTATTCTTGACAATTAAGTAGAGCCTGATATAATAGTTCAGTACTGTT  |
| CP30                       | 42                    | CATGACAGAGTTTATTCTTGACAGTATTGGGTTACTTTGGTATAATAGTTGAGTACTGTT |
| CP9a                       | 56                    | CATAGTCTAGTTTATTCTTGACACGCGGTCCATTGGCTGGTATAATAATTTAGTACTGTT |
| CP12（已有，作为中等锚点） | 101                   | CATATACAAGTTTATTCTTGACACTAGTCGGCCAAAATGATATAATACCTGAGTACTGTTCACACAGGAAACAGCTATG |
| CP7                        | 134                   | TATGCGGTAGTTTATTCTTGACATGACGAGACAGGTGTGGTATAATGGGTCTAGATTAGG |
| CP6                        | 280                   | CATGTGGGAGTTTATTCTTGACACAGATATTTCCGGATGATATAATAACTGAGTACTGTT |
| CP25                       | 528                   | CTTTGGCAGTTTATTCTTGACATGTAGTGAGGGGGCTGGTATAATCACATAGTACTGTT  |

### Build｜实施

沿用 A5 的 pKD46 / λ-Red 同源重组策略，设计带目标位点同源区域的线性 donor DNA，替换 MG1655 内源 `chb` 启动子区域，构建：

CP6CHB、CP7CHB、CP25CHB、CP30CHB、CP44CHB、CP9aCHB、CP12CHB（A5中已有构建）

用设计好的三轮重叠延伸 PCR 引物，扩增对应启动子的线性 Donor DNA，第一轮扩增产物预期约为1300 bp，第二、第三轮扩增产物预期均约为1500bp。

### Test｜测试

第一轮扩增产物

![DonorDNA第一轮](./images%20of%20wetlabDBTL/DonorDNA%E7%AC%AC%E4%B8%80%E8%BD%AE.png)

第二轮扩增产物

![DonorDNA第二轮](./images%20of%20wetlabDBTL/DonorDNA%E7%AC%AC%E4%BA%8C%E8%BD%AE.png)

第三轮扩增产物

![DonorDNA第三轮](./images%20of%20wetlabDBTL/DonorDNA%E7%AC%AC%E4%B8%89%E8%BD%AE.png)

用设计好的三轮重叠延伸 PCR 引物，扩增对应启动子的线性 Donor DNA，第一轮扩增产物约为1300 bp，第二轮扩增产物均约为1400bp，第三轮扩增产物约1500bp。三轮电泳结果显示，所有泳道在预期长度处均出现单一主带，条带强度高、无拖尾，与预期长度相符，说明 Donor DNA 扩增成功。

转化后涂布卡那霉素抗性平板，其中 CP9a 的平板上无菌落生长。

![CP所有平板](./images%20of%20wetlabDBTL/CP%E6%89%80%E6%9C%89%E5%B9%B3%E6%9D%BF.png)

挑取各平板单克隆进行扩培，使用两对测序引物进行菌落PCR，覆盖基因组同源区域和完整 Donor DNA，以筛选阳性克隆。两对引物预期产物分别为 ~800 bp，~900 bp。

![测序](./images%20of%20wetlabDBTL/%E6%B5%8B%E5%BA%8F.png)

测序结果显示，CP6-1菌株在CP6 promoter区域引入了一个额外的突变，其他CP系列染色体改造的单克隆菌株，其启动子区域的插入均符合预期。

![image-20261019153440839](./images%20of%20wetlabDBTL/image-20261019153440839.png)

### Learn｜学习

通过扩展单一 CP12 构建，获得了可比较不同启动子调控条件的菌株系列，我们关注的焦点从最初的能否激活 chb 变为，“如果我们去构建梯度启动子强度菌株，启动子强度的改变到底会不会产生不同功能表现？”

文献中给出的启动子为预期强度，染色体上的实际转录水平，不同构建还可能受局部序列背景和细胞状态影响。因此，在分析生长和迁移表型前，必须先测量不同构建的相对转录丰度。

在下一轮循环中，我们使用 RT-qPCR 比较 CP 系列启动子下游 chb operon 区域的转录水平。

### DBTL A6.2 CP 系列工程菌的 RT-qPCR 表征

#### Design｜设计

A6.1 中，我们构建了由不同 CP 启动子调控的 *chb* 工程菌。本轮采用 RT-qPCR 测定各菌株的相对转录水平，检验文献中的启动子活性差异能否在染色体 *chb* 调控背景下得到体现。

#### Build｜实施

将各菌株在 M9 + 甘油培养基中预培养，提取总 RNA 并逆转录为 cDNA。以 *cysG* 为内参，选取替换启动子下游、包含 *chbB* 起始部分的区域作为检测目标，通过 ΔΔCt 法计算相对于 WT MG1655 的转录丰度，并以 Log2 FC 表示。

#### Test｜测试

![A6.2-qPCR](./images%20of%20wetlabDBTL/A6.2-qPCR.png)

RT-qPCR 显示，不同 CP 启动子替换株的目标区域转录水平存在明显差异。其中，CP30 和 CP44 的相对转录水平最高，CP25 次之，CP12 表现出一定程度的转录上调，而 CP6、CP7 的测量结果接近 WT。

这一排序与 Jensen and Hammer（1998）报道的启动子活性排序并不一致，表明文献中的启动子强度不能直接用于预测本次染色体 *chb* 构建的转录水平。

#### Learn｜学习

RT-qPCR 表明，CP 启动子系列在本次培养条件下产生了不同的目标区域转录水平，但其相对排序与文献预期存在差异。该结果提示我们最初的假设是合理的，即启动子实际转录水平，在 chb 局部序列下的表达表现，是需要独立表征的。

下一步，我们将通过生长曲线比较不同工程菌的纤维二糖利用相关表型，检验转录差异是否伴随生长表型变化。

### DBTL A6.3 CP 系列工程菌的生长表型与重复性验证

#### Overview

A6.2 的 RT-qPCR 显示，不同 CP 启动子替换株具有不同的 *chb* 转录水平。不同的转录强度究竟是否带来不同的纤维二糖生长表型呢？我们进一步比较这些菌株在纤维二糖条件下的生长表现，观察转录变化是否伴随可检测的不同生长表型。

为此，我们通过连续 OD600 测量比较 CP 系列工程菌与 WT MG1655 在不同碳源条件下的生长情况，并尝试估计最大比生长速率（μmax）。

#### Cycle 1｜CP 系列工程菌的初步生长曲线测定

##### Design｜设计

我们首先希望验证不同 CP 启动子替换菌株能否在纤维二糖作为碳源的条件下生长，并比较其生长表现。

选择 CP6、CP7、CP12、CP25、CP30、CP44 及 WT MG1655，在 M9 最小培养基中设置2种碳源条件：

| 培养条件             | 实验目的                             |
| -------------------- | ------------------------------------ |
| M9 + 0.4% cellobiose | 比较各菌株的纤维二糖利用相关生长表型 |
| M9 + 0.4% glucose    | 比较葡萄糖条件下的生长表现           |

每组设置 3 个技术重复孔，连续监测 24 h。

##### Build｜实施

各菌株统一前培养后，使用 BioTek Synergy H1 每 15 min 测量 OD₆₀₀。数据经相应培养基空白校正后绘制生长曲线；对通过质量筛选的 6 h 滑动窗口进行对数线性拟合，取最大斜率作为最大 6 h 表观比生长速率（μ_app,6h,max），用于辅助比较生长表现。具体步骤见 OD₆₀₀ 数据处理及表观生长速率分析 Protocol。

##### Test｜测试

**1. CP 系列工程菌的生长曲线**

![CPseries生长曲线1修改](./images%20of%20wetlabDBTL/CPseries%E7%94%9F%E9%95%BF%E6%9B%B2%E7%BA%BF1%E4%BF%AE%E6%94%B9.png)

CP 系列启动子改造菌株在 cellobiose 与 glucose 条件下的生长曲线。

在纤维二糖条件下，在生长曲线图上，我们可以看到CP12、CP25、CP30 和 CP44 呈现较明显的 OD₆₀₀ 增长，而 CP6、CP7 增长较弱，WT MG1655几乎没有增长。各菌株在葡萄糖条件下均能生长。

**2. 最大 6 h 表观比生长速率**

![未标题-1(1)](./images%20of%20wetlabDBTL/%E6%9C%AA%E6%A0%87%E9%A2%98-1(1).png)

我们拟合了6 h 表观比生长速率（μ_app,6h,max），用于辅助比较生长表现

在纤维二糖条件下，CP12、CP25、CP30 和 CP44 的表观速率约为 7%–9%/h，CP6 约为 3.8%/h，而 CP7 和 WT 未能筛选出可靠的持续增长区间，因此不报告该指标（NA）。各菌株在葡萄糖条件下的表观速率约为 12%–16%/h。

##### Learn｜学习

结合 A6.2 的 RT-qPCR 结果，转录水平较低的 CP6、CP7 在纤维二糖条件下生长较弱，而 CP12、CP25、CP30 和 CP44 均表现出较明显的增长。然而， CP12 在转录量远低于 CP30、CP44 的情况下，仍表现出相近的生长速率，表明转录丰度与生长表现并非简单的正比例关系。

需要注意的是，本次生长曲线实验仅设置了三个技术重复，缺乏独立生物学重复，因此上述结果仅反映初步趋势，对于支持菌株间生长差异来说，具有统计学意义上的局限性。

由于生长是底物转运、代谢及细胞增殖共同作用的结果，我们下一步计划进一步采用 DNS 法比较不同工程菌的表观底物消耗能力，以分开观察生长表现与底物消耗水平。

### DBTL A6.4 chb 启动子梯度菌株的纤维二糖摄取定量（DNS 法）

### A6.4 Cycle 1｜DNS 法检测可行性验证

#### Design｜设计

为了进一步比较 CP 系列工程菌的纤维二糖消耗能力，我们计划采用 DNS 法测定反应上清中的还原糖浓度变化。然而，尚不确定该方法能否灵敏地检测细胞摄取造成的底物减少。

因此，我们首先选择 CP12CHB 和 WT MG1655 进行预实验，以 1 mM 纤维二糖为初始底物条件，设置高、低两种细胞浓度，评估 DNS 法的检测可行性，并观察细胞浓度对底物消耗及检测范围的影响。

#### Build｜实施

将 CP12CHB 与 WT MG1655 分别调整为高、低两种细胞浓度，加入含 1 mM 纤维二糖的反应体系。在 0、15、30 和 60 min 收集上清，使用 DNS 法测定还原糖浓度，比较不同细胞浓度下的变化趋势。

#### Test｜测试

![image-20261019222124722](./images%20of%20wetlabDBTL/image-20261019222124722.png)

WT 在两种细胞浓度下的上清还原糖浓度均基本保持稳定。相比之下，CP12CHB 的还原糖浓度随时间持续下降，其中高细胞浓度组从约 0.295 mg/mL 降至 0.154 mg/mL，低细胞浓度组则降至约 0.210 mg/mL。

高细胞浓度组表现出更明显的底物消耗，但在 60 min 时仍有可检测的还原糖残留。

#### Learn｜学习

预实验表明，DNS 法能够检测到 CP12CHB 反应体系中的还原糖浓度下降，且提高细胞浓度可以放大检测信号。这为后续 CP 系列工程菌的底物消耗比较提供了方法基础。

### A6.4 Cycle 2｜DNS 法测定CP系列工程菌纤维二糖摄取速率

#### Design｜设计

Cycle 1 验证了 DNS 法能够检测 CP12CHB 反应体系中的还原糖变化。本轮将测定扩展至全部 CP 系列工程菌，比较不同启动子构建的底物消耗能力，并进一步观察其与此前转录及生长表型的关系。

我们的预期是：WT 基本不消耗，CP 菌株的消耗速率应随 chb 表达强度拉开梯度。

#### Build｜构建

选择 CP6、CP7、CP12、CP25、CP30、CP44 和 WT MG1655，各设置三个独立生物学重复。菌株经预培养、收集和洗涤后，置于含 1 mM 纤维二糖的 PBS 反应体系中，于不同时间点收集上清，通过 DNS 法测定还原糖浓度。

同时测量各生物学重复的 OD₆₀₀，并据此计算 0–60 min 内单位 OD₆₀₀ 的表观平均消耗速率（q），以减少菌株间细胞浓度差异对比较结果的影响。

#### Test｜测试

**1. CP 系列工程菌的底物消耗变化**

![image-20261019225115082](./images%20of%20wetlabDBTL/image-20261019225115082.png)

WT 的上清还原糖浓度在测量期间基本保持稳定，而 CP 系列工程菌表现出不同程度的下降。其中，CP12 的下降最为明显，在 30 min 时剩余浓度已低于 0.1 mg/mL；CP30、CP7、CP44 和 CP25 也表现出明显的下降趋势，CP6 相对较弱。

![image-20261019225132598](./images%20of%20wetlabDBTL/image-20261019225132598.png)

60 min 终点测定进一步显示，CP12 的剩余还原糖浓度最低，CP30、CP7 和 CP44 次之，表明不同工程菌具有可区分的底物消耗表型。

##### 2. OD600 归一化后的单位细胞摄取速率

![image-20261019223505057](./images%20of%20wetlabDBTL/image-20261019223505057.png)

按各生物学重复的 OD₆₀₀ 归一化后，CP12 与 CP7 的表观平均消耗速率最高，均约为 0.0095 μmol·mL⁻¹·min⁻¹·OD₆₀₀⁻¹。CP44 和 CP30 次之，CP25、CP6 相对较低。

值得注意的是，CP7 虽然在 A6.2 中表现出较低的目标区域转录水平，且在 A6.3 中生长较弱，但本轮测得的归一化表观消耗速率却与 CP12 接近。

#### Learn｜学习

本轮测定显示，除了CP6之外，所有 CP 菌株的 60 min 剩余糖均显著低于 WT，chb 表达强度的差异确实转化成了可分辨的摄取表型差异，但其结果与此前的转录及生长表型并不完全一致，尤其是 CP7 的高表观消耗速率，其中的机制有待进一步探究。

同时，我们发现当前体系对高消耗能力菌株的分辨能力不足。CP12 在 30 min 时剩余糖浓度已低于本批标准曲线的可靠定量范围，导致 0–60 min 平均速率难以准确反映强株的早期消耗能力。 如果想进一步比较强株之间的的早期消耗能力差异，应该缩短取样时间，例如 5、10、20 min，并调整细胞浓度，使测定过程尽量处于可靠的检测范围。

但由于时间限制，我们并未能在wiki提交截止之前完成进一步的实验。

# DBTL A7｜CP 系列工程菌的软琼脂趋化表征与 RPM 模拟微重力探索

## Overview

A6 中，我们通过 RT-qPCR、生长曲线及 DNS 测定，发现 CP 系列工程菌具有不同的 *chb* 转录水平和纤维二糖利用表型。然而，底物摄取能力的增强是否能够转化为对纤维二糖的趋化响应，仍有待验证。

因此，我们采用软琼脂趋化实验，尝试比较 CP 系列工程菌与 WT 的群体迁移行为，并进一步探索纤维二糖浓度及 RPM 模拟微重力培养条件对这一表型的影响。

## A7.1｜CP 系列工程菌的初步软琼脂趋化实验

### Design｜设计

我们参考 Sanders et al. (2013) 的 *Supplemented Soft Agar Chemotaxis Assay*，采用含 1% 胰蛋白胨（tryptone）的软琼脂体系。该体系中的胰蛋白胨提供基础营养物质，细菌从接种点开始消耗周围的营养物质，逐渐形成向外升高的浓度梯度，从而驱动群体迁移。

与通常认为“趋化越强，迁移圈越大”的直观判断不同，Sanders et al. (2013) 发现，在软琼脂中均匀添加已知趋化吸引剂丝氨酸，反而会减慢大肠杆菌的群体迁移。作者推测，较高的初始吸引剂浓度可能延迟有效趋化梯度的形成，使固定时间点的迁移圈减小。

因此，我们希望通过比较 CP 系列与 WT 在纤维二糖添加条件下的群体扩展表现，初步判断 *chb* 改造是否引起了与纤维二糖相关的迁移响应。

此外，考虑到营养条件能够影响细菌对运动与趋化系统的资源投入（Ni et al., 2020），我们采用 M9 + 0.2% 甘油进行前培养，并设置以下三种平板条件：

| 平板条件         | 设计目的                           |
| ---------------- | ---------------------------------- |
| 10 mM Cellobiose | 观察 CP 系列对纤维二糖的迁移响应   |
| 10 mM Glucose    | 利用原生葡萄糖趋化系统提供阳性比较 |
| Empty            | 建立无额外糖添加时的群体扩展基线   |

通过比较 CP 系列与 WT 在不同条件下的菌斑扩展情况，我们希望初步判断 *chb* 改造是否带来了可辨认的纤维二糖趋化表型。

### Build｜实施

将 CP6、CP7、CP12、CP25、CP30、CP44 及 WT MG1655 经 M9 + 0.2% 甘油预培养后，采用多点针刺方式接种于含 1% tryptone、0.5% NaCl、0.35% agar 的软琼脂平板。

分别添加 10 mM 纤维二糖、10 mM 葡萄糖或不额外添加糖，于 30 °C 培养，观察菌斑形成和扩展。

### Test｜测试

**1. 葡萄糖对照组**

葡萄糖组主要在接种位置形成较小菌斑，平板整体呈现明显的灰白色浑浊，未能辨识出各接种点独立的迁移边界。

这一现象可能来自细菌扩展覆盖整个平板，也可能由杂菌污染造成。由于未能记录到清晰的迁移前沿，且平板整体浑浊异常，污染的可能性不能排除，因此该组无法提供可靠的阳性趋化判读。

**2. 纤维二糖组与无糖对照**

在 10 mM 纤维二糖条件下，CP12、CP30 和 CP44 形成的可见菌斑大于各自在无额外糖添加条件下的菌斑。

CP6、CP25 的差异相对不明确，而 CP7 的菌落形态不规则，难以准确比较。

https://static.igem.wiki/teams/6100/wiki/images-of-wetlab-dbtl/dbtl-a/cp-series.avif

### Learn｜学习

部分 CP 工程菌在添加纤维二糖后形成了更大的菌斑，但这一现象难道说明纤维二糖不是CP系列工程菌的趋化吸引物吗？答案也不一定

我们不妨先假设 CP12 能够利用纤维二糖，而且能够对其产生趋化，那么添加纤维二糖后，至少可能发生两种相反的影响。

1、第一种是额外营养的添加，使细菌长得快了：**添加纤维二糖 → CP12 获得额外可利用碳源 → 可能促进细菌增殖或改变迁移前沿的生长状态 → 可见扩展范围可能增大。**

2、另外一种是我们预期的过程，即较高吸引剂背景可能延迟趋化驱动的迁移：**添加纤维二糖 → 如果 CP12 确实能够感知它，且该浓度下的相对浓度变化不易被有效感知 → 向外的纤维二糖趋化漂移可能较晚出现 → 可见扩展范围可能减小。**

这两种作用可以同时存在。最终菌落是变大还是变小，取决于生长、运动和趋化等过程的综合作用。至于趋化响应速度慢，在其中的具体占比有多少，这是我们尚未探索清楚的。

我们由此提出下一轮问题：改变纤维二糖浓度，是否会产生可辨认的迁移差异？这种表型在 RPM 模拟微重力培养条件下又会如何变化？

## A7.2｜纤维二糖浓度与 RPM 培养条件下的群体迁移比较

### Design｜设计

A7.1 中，我们观察到部分 CP 工程菌在纤维二糖条件下形成更大的菌斑，但无法判断其中的趋化贡献。

为进一步探索这一问题，我们在原有胰蛋白胨软琼脂体系中增加低浓度纤维二糖条件，希望通过比较 1 mM 与 10 mM 纤维二糖下的迁移表现，观察降低底物浓度后是否出现更小或不同的迁移圈。

![化学趋化响应：相对变化对比](./images%20of%20wetlabDBTL/%E5%8C%96%E5%AD%A6%E8%B6%8B%E5%8C%96%E5%93%8D%E5%BA%94%EF%BC%9A%E7%9B%B8%E5%AF%B9%E5%8F%98%E5%8C%96%E5%AF%B9%E6%AF%94.png)

同时，我们引入经典趋化吸引剂 L-天冬氨酸和PTS趋化糖葡萄糖作为阳性参照。

与此同时我们还设置了 RPM（**Random Positioning Machine**） 模拟微重力与地面静置两个培养条件，我们想探索在未来应用场景相关联的微重力环境模拟条件下，工程菌的群体迁移表现如何。

本轮设置四种平板：

| 平板条件         | 设计目的                               |
| ---------------- | -------------------------------------- |
| 1 mM L-Asp       | 已知趋化吸引剂阳性参照                 |
| 1 mM Glucose     | 原生糖类趋化响应比较                   |
| 1 mM Cellobiose  | 观察低浓度纤维二糖下的迁移表现         |
| 10 mM Cellobiose | 与低浓度组比较，探索浓度相关的迁移差异 |

我们希望回答两个问题：纤维二糖浓度是否影响 CP 系列工程菌的群体扩展，以及 RPM 培养条件是否改变这一表型。

### Build｜实施

沿用 A7.1 的菌株、前培养及软琼脂配方，采用多点针刺接种方式制备四种平板。

设置地面静置组与 RPM 随机定位机培养组，均在约 25 °C 条件下培养，并通过拍照比较各菌株的菌斑形态与扩展范围。

![A7.2-Build](./images%20of%20wetlabDBTL/A7.2-Build.png)

### Test｜测试

**1. 地面静置组**

在 1 mM L-Asp 条件下，各菌株主要形成接种点附近的局部菌落。1 mM 葡萄糖组出现明显的不规则片状扩展，部分区域受到冷凝水影响，但二者仍可观察到部分接种点形成较小的菌斑。

这两种已知趋化吸引剂条件下的较小扩展范围，与 Sanders et al. (2013) 报道的吸引剂可能减缓软琼脂群体迁移的现象相符，为纤维二糖组提供了一些参考。。

比较 1 mM 与 10 mM 纤维二糖条件后，我们发现，多数 CP 工程菌在较高纤维二糖浓度下表现出更小的菌斑。其中，CP12、CP7 和 CP25 的变化较为明显，CP44 也呈现一定的减小趋势；CP6 的差异不明显，而 CP30 未表现出相同趋势。

值得注意的是，WT 在 10 mM 纤维二糖条件下反而形成了更大的菌斑，与多数 CP 工程菌呈现相反的变化方向。

![image-20261021024323345](./images%20of%20wetlabDBTL/image-20261021024323345.png)

**2. RPM 模拟微重力组**

本轮 RPM 实验遭遇了明显的技术问题。由于软琼脂机械强度较低，多块平板在 RPM 旋转过程中发生破裂，导致部分实验条件未能获得有效结果，其中包括 L-Asp 阳性参照组。

在保留下来的平板中，似乎只有在 10 mM 纤维二糖条件下，WT 与部分 CP 工程菌均形成可见菌。

而且与地面组相比，RPM 组多个菌株的可见扩展范围整体偏小，但由于部分平板损坏、菌斑边界不清晰，无法进行可靠的定量比较。

![image-20261021024340505](./images%20of%20wetlabDBTL/image-20261021024340505.png)

### Learn｜学习

**1. RPM 下的群体扩展可能发生变化，但无法归因于趋化调控**

RPM 组部分菌株表现出较小的可见扩展范围，且这一现象并不局限于 CP 工程菌。已有研究表明，模拟微重力相关培养条件可能改变大肠杆菌的鞭毛及趋化相关基因表达，我们确实观察到了和地面培养不同的运动状态，可能微重力模拟条件改变了大肠杆菌的一些生理状态。但其中发生了什么事情是我们暂时不清楚的，这也提示着我们未来的应用投放不能简单地认为地面实验取得的成果可以简单套用在微重力条件下，我们仍需经过多轮微重力模拟测试工程菌的各项参数是否与地面环境有差异。

**2. 纤维二糖浓度可能影响群体迁移，但尚不能确定其趋化贡献**

地面实验中，当纤维二糖浓度由 1 mM 提高至 10 mM 时，CP12、CP44 和 CP25 的菌斑明显减小，而 WT 的扩展范围反而增大。

这一结果与 Sanders et al. (2013) 提出的吸引剂背景浓度可能影响软琼脂迁移的机制是相符的。如果 CP 工程菌能够感知纤维二糖，那么在较低初始浓度下，局部底物消耗可能更容易产生可被感知的相对浓度变化，从而较早形成有效的向外趋化漂移。

这一结果有可能支持CP12,CP44,CP25菌株可能具有较强的趋化迁移能力，但如前文所述，群体迁移速度还是会受到生长和代谢的影响，所以本方法并不能完全肯定CP系列菌株有趋化结果。
我们或许需要一个人为制造浓度梯度的实验来观察趋化，而非通过细菌自身生长消耗糖形成梯度的实验来观察趋化——这可能还是会混杂代谢和生长因素。
所以下一轮我们的重点转向了A8，使用微流控芯片观察大肠杆菌趋化。

##### References

Morabbi Heravi, K., & Altenbuchner, J. (2018). Cross talk among transporters of the phosphoenolpyruvate-dependent phosphotransferase system in *Bacillus subtilis*. *Journal of Bacteriology, 200*(19), e00213-18. https://doi.org/10.1128/JB.00213-18

Parisutham, V., Jung, S.-K., Nam, D., & Lee, S. K. (2013). Transcriptome-driven synthetic re-modeling of *Escherichia coli* to enhance cellobiose utilization. *Chemical Engineering Science, 103*, 50–57. https://doi.org/10.1016/j.ces.2012.08.006

Parisutham, V., & Lee, S. K. (2015). Novel functions and regulation of cryptic cellobiose operons in *Escherichia coli*. *PLoS ONE, 10*(6), e0131928. https://doi.org/10.1371/journal.pone.0131928

Sanders, D. E., et al. (2013). Cell population control of swarming and surface behavior in *Escherichia coli*. 

Adler, J. (1973). A method for measuring chemotaxis and use of it to define the optimum conditions for chemotaxis by *Escherichia coli*. *Journal of General Microbiology, 74*, 77–91.

Croze, O. A., et al. (2011). Migration of *Escherichia coli* in semi-solid soft agar: Role of Gel Concentration. *Biophysical Journal*. 2011 Aug 3;101(3):525–534. doi: 10.1016/j.bpj.2011.06.023

Sourjik, V., & Wingreen, N. S. (2012). Responding to chemical gradients: bacterial chemotaxis. *Current Opinion in Cell Biology, 24*(2), 262–268. https://doi.org/10.1016/j.ceb.2011.11.008 

Ni, B., Colin, R., Link, H., Endres, R. G., & Sourjik, V. (2020). Growth-rate dependent resource investment in bacterial motile behavior quantitatively follows potential benefit of chemotaxis. *PNAS, 117*(1), 595–601. https://doi.org/10.1073/pnas.1909859116 

Zhao, K., Liu, M., & Burgess, R. R. (2007). Adaptation in bacterial flagellar and motility systems: from regulon members to 'foraging'-like behavior in *Escherichia coli*. *Nucleic Acids Research, 35*(13), 4441–4452. https://doi.org/10.1093/nar/gkm453

Jensen, P. R., & Hammer, K. (1998). The sequence of spacers between the consensus sequences modulates the strength of prokaryotic promoters. *Applied and Environmental Microbiology*, *64*(1), 82–87. https://doi.org/10.1128/aem.64.1.82-87.1998

Keyhani, N. O., & Roseman, S. (1997). Wild-type Escherichia coli grows on the chitin disaccharide, N,N′-diacetylchitobiose, by expressing the cel operon. Proceedings of the National Academy of Sciences, 94(26), 14367–14371. [https://doi.org/10.1073/pnas.94.26.14367](https://doi.org/10.1073/pnas.94.26.14367?utm_source=chatgpt.com)
