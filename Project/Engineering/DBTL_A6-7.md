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

用设计好的三轮重叠延伸 PCR 引物，扩增对应启动子的线性 Donor DNA，第一轮扩增产物约为1300 bp，第二、第三轮扩增产物均约为1500bp。三轮电泳结果显示，所有泳道在预期长度处均出现单一主带，条带强度高、无拖尾，与预期长度相符，说明 Donor DNA 扩增成功。

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

**2. 纤维二糖表观消耗量**

![image-20261019223408045](./images%20of%20wetlabDBTL/image-20261019223408045.png)

不同 CP 工程菌均表现出不同程度的上清还原糖下降。其中，CP12 的表观消耗量最高，CP30 次之，CP7、CP44 和 CP25 也表现出较明显的下降，而 CP6 相对较弱。

##### 3. OD600 归一化后的单位细胞摄取速率

![image-20261019223505057](./images%20of%20wetlabDBTL/image-20261019223505057.png)

按各生物学重复的 OD₆₀₀ 归一化后，CP12 与 CP7 的表观平均消耗速率最高，均约为 0.0095 μmol·mL⁻¹·min⁻¹·OD₆₀₀⁻¹。CP44 和 CP30 次之，CP25、CP6 相对较低。

值得注意的是，CP7 虽然在 A6.2 中表现出较低的目标区域转录水平，且在 A6.3 中生长较弱，但本轮测得的归一化表观消耗速率却与 CP12 接近。

#### Learn｜学习

本轮测定显示，除了CP6之外，所有 CP 菌株的 60 min 剩余糖均显著低于 WT，chb 表达强度的差异确实转化成了可分辨的摄取表型差异，但其结果与此前的转录及生长表型并不完全一致，尤其是 CP7 的高表观消耗速率，其中的机制有待进一步探究。

同时，我们发现当前体系对高消耗能力菌株的分辨能力不足。CP12 在 30 min 时剩余糖浓度已低于本批标准曲线的可靠定量范围，导致 0–60 min 平均速率难以准确反映强株的早期消耗能力。 如果想进一步比较强株之间的的早期消耗能力差异，应该缩短取样时间，例如 5、10、20 min，并调整细胞浓度，使测定过程尽量处于可靠的检测范围。

但由于时间限制，我们并未能在wiki提交截止之前完成进一步的实验。

### DBTL A6.5 CP 系列菌株趋化能力测定

#### Cycle 1｜CP系列工程菌的趋化能力测定（胰蛋白胨软琼脂体系）

##### Design｜设计

上一轮软琼脂趋化实验我们采用了LB预培养菌株，最终CP12CHB没有得到比较显著的趋化表型，经过文献调研我们发现，大肠杆菌在营养充足和营养匮乏的环境中，会采用不同的生存策略。营养充足时，它倾向于把资源用于生长繁殖；营养匮乏时，它可能投入更多资源来形成鞭毛、增强环境感知能力，从而更有效地寻找营养物质。（Ni et al., 2020）

这一轮我们想验证：经贫瘠营养预培养的 CP 系列不同强度启动子工程菌，能否在胰蛋白胨软琼脂平板上表现出对纤维二糖的趋化响应，并初步比较不同启动子强度下趋化圈的差异。

为了评估工程菌对纤维二糖的趋化响应，我们建立了1%胰蛋白胨的软琼脂实验体系（tryptone swarm plate），使用含 0.35% agar 的培养基，并设置三种平板条件

| 平板条件 | 外加碳源 | 目的 |
| ---- | ---- | ---- |
| 纤维二糖板 | cellobiose | 检测工程菌对纤维二糖的趋化响应 |
| 葡萄糖板 | glucose | 阳性比较条件（内源 PTS 通路完好，预期所有菌株均能趋化） |
| 无糖板 | — | 基线对照（仅胰蛋白胨背景营养驱动的迁移） |

通过比较不同菌株在三种条件下的迁移扩展情况，我们希望初步评估 chb 操纵子系列改造是否改变细菌在纤维二糖环境中的运动表现。
##### Build｜实施

将 CP6、CP7、CP12、CP25、CP30、CP44 及 WT MG1655 在 M9 + 0.2% 甘油中预培养。制备含 1% 胰蛋白胨、0.35% 琼脂的软琼脂平板，分别添加 10 mM 纤维二糖、10 mM 葡萄糖或不额外添加糖。

各菌株采用多点针刺接种，于 30 °C 培养，记录菌斑形成及其向外扩展情况。


##### Test｜测试
https://static.igem.wiki/teams/6100/wiki/images-of-wetlab-dbtl/dbtl-a/cp-series.avif

实验结果显示：

葡萄糖组的主要在接种位置形成较小的菌斑，平板整体呈现较明显的灰白色浑浊，未能辨识出各接种点独立的迁移边界。

在纤维二糖条件下，部分 CP-chb 工程菌形成了较为明显的白色菌斑，与 WT 呈现不同的局部生长或扩展表型。无额外添加糖组（Empty）中，部分菌株同样能够形成局部菌斑，表明该培养体系可以支持一定程度的细菌基线生长。


##### Learn｜学习

葡萄糖组的平板出现这样的现象我们猜测可能第一个是工程菌趋化迁移扩展到了整个平板。第二个可能是葡萄糖组的平板被污染从而导致杂菌生长使平板变为灰白色。但在培养过程中，我们未能捕捉到各接种点独立的迁移边界，这一情况使得第二种情况的可能性更高。

纤维二糖组的部分工程菌形成了比无额外添加糖组更大的菌斑。由于纤维二糖既是潜在趋化信号，也是工程菌能够利用的碳源，这使我们不得不承认，菌斑扩大可能并非全部来源于细菌趋化贡献，极有可能有一部分贡献来源于生长，至于趋化在其中的具体占比有多少，这是我们尚未探索清楚的。

我们重新查阅了chb操纵子的趋化性文献，下一轮我们计划使用 Keyhani 的 M9 + 0.25% agar 体系，以几丁二糖作为文献阳性比较底物，再与纤维二糖进行比较，进行软琼脂趋化实验。(Keyhani & Roseman, 1997)

我们想探索我们的CP-chb 构建，在更接近Keyhani文献的条件下，是否能够形成可辨认的迁移环。在wiki截止之前，我们没有充足的时间进行下一轮实验了。





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
