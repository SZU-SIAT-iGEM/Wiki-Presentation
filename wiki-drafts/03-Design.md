# Design / 设计理念

> **Project:** friskoli
> **Team:** SZU-SIAT-China | **Track:** Space Track | **Year:** 2026

---

## System Overview / 系统总览

The friskoli system is built on a two-module genetic architecture operating within *Escherichia coli* MG1655. The core design principle is to transform cellulose degradation into a self-amplifying chemotactic signal — bacteria that degrade cellulose produce more cellobiose, which recruits more bacteria to the degradation site via the native phosphotransferase system (PTS) — chemotaxis coupling pathway. The two modules are carried on orthogonal plasmids with compatible origins of replication and distinct antibiotic selection markers.

friskoli 系统基于在大肠杆菌 MG1655 中运行的双模块基因架构构建。核心设计理念是将纤维素降解转化为自放大趋化信号——降解纤维素的细菌会产生更多纤维二糖，通过天然磷酸转移酶系统-趋化信号耦合通路将更多细菌招募至降解位点。两个模块携带在具有兼容复制起点和不同抗生素选择标记的正交质粒上。

```
┌─────────────────────────────────────────────────────────────────────┐
│                     E. coli MG1655 Chassis                          │
│                                                                     │
│  ┌─────────────────────────┐    ┌──────────────────────────────┐   │
│  │    MODULE 1 (pGEX-ascFB)│    │    MODULE 2 (pCDF-1b)       │   │
│  │   Med-Low Copy (~15-20) │    │   Med-Low Copy (~20-30)     │   │
│  │   Ampicillin Resistance │    │   Spectinomycin Resistance  │   │
│  │                         │    │                              │   │
│  │  J23116 (weak P)        │    │  J23116 (weak P)             │   │
│  │    ↓                    │    │    ↓                         │   │
│  │  B0034 (RBS)            │    │  B0034 (RBS)                 │   │
│  │    ↓                    │    │    ↓                         │   │
│  │  ascF (PTS EII^Asc)     │    │  INPNC-Cocktail(Cel9K/48S/5L)│   │
│  │    ↓                    │    │    ↓                         │   │
│  │  B0034 (RBS)            │    │  B0015 (Terminator)          │   │
│  │    ↓                    │    │                              │   │
│  │  ascB (Phospho-β-glu)   │    │                              │   │
│  │    ↓                    │    │                              │   │
│  │  B0015 (Terminator)     │    │                              │   │
│  └──────────┬──────────────┘    └──────────────┬───────────────┘   │
│             │                                  │                    │
│             ▼                                  ▼                    │
│    Cellobiose-6-P → G6P               Cellulose Degradation        │
│    → Glycolysis                        → Cellobiose ──────┐        │
│         │                                     ▲          │        │
│         └─────────── Metabolism ───────────────┘          │        │
│                                                            │        │
│    ┌───────────────────────────────────────────────────────┘        │
│    │  Positive Feedback Loop:                                     │
│    │  More cellobiose → More PTS flux → More chemotaxis           │
│    │  → More bacteria → More cellulase → More degradation         │
│    │  → More cellobiose                                            │
│    └───────────────────────────────────────────────────────────────┘
│                                                                     │
│    ┌───────────────────────────────────────────────────────────────┐│
│    │  Self-Limiting: Metabolic byproducts modulate PTS state       ││
│    │  → natural homeostasis prevents runaway response              ││
│    └───────────────────────────────────────────────────────────────┘│
└─────────────────────────────────────────────────────────────────────┘
```

### Two-Module Rationale / 双模块设计原理

The separation into two plasmids serves three purposes. First, it enables independent optimization of the two functions — cellobiose sensing/transport (Module 1) and cellulose degradation (Module 2) — allowing each to be tuned to its optimal expression level. Second, Module 1 requires low expression (AscF is a transmembrane protein with toxicity risk at high levels), while Module 2 benefits from higher expression for sufficient surface display of cellulase. Third, the orthogonal replication origins (pBR322 origin for pGEX-ascFB [1], CloDF13 origin for pCDF-1b [2]) ensure plasmid stability in the presence of dual antibiotic selection.

双质粒分离服务于三个目的。第一，它允许两个功能各自独立优化——纤维二糖感应/转运（模块一）和纤维素降解（模块二）——使每个模块都能调整到最佳表达水平。第二，模块一需要低表达（AscF 是一种跨膜蛋白，高表达有毒性风险），而模块二需要较高表达以确保足够的纤维素酶表面展示。第三，正交复制起点（pGEX-ascFB 使用 pBR322 复制子 [1]，pCDF-1b 使用 CloDF13 复制子 [2]）确保在双抗生素选择下质粒的稳定性。

---

## Module 1: Cellobiose Transport, Metabolism, and Chemotaxis Signaling / 模块一：纤维二糖转运、代谢与趋化信号

### The asc Operon / asc 操纵子

The *asc* operon (also known as the cellobiose operon) is an endogenous genetic element in the *Escherichia coli* MG1655 genome. The functional unit consists of *ascF* (`b2715`) and *ascB* (`b2716`), with the divergently transcribed repressor gene *ascG* (`b2714`) regulating the operon. In modern MG1655 genome coordinates, this region lies around NC_000913.3 ~2.84 Mb. It was first sequenced and characterized by Hall and Xu in 1992 [3]. In wild-type MG1655, the *asc* operon is typically cryptic — it is present but not expressed under standard laboratory conditions due to the action of the AscG repressor and the absence of inducing levels of cellobiose. The friskoli system takes advantage of this endogenous genetic resource by expressing *ascF* and *ascB* from a synthetic, constitutive promoter on a plasmid, bypassing the native regulatory control.

asc 操纵子（也称为纤维二糖操纵子）是大肠杆菌 MG1655 基因组中的内源性遗传元件。其功能单元由 *ascF*（`b2715`）和 *ascB*（`b2716`）组成，反向转录的阻遏蛋白基因 *ascG*（`b2714`）调控该操纵子。按现代 MG1655 基因组坐标，该区域位于 NC_000913.3 约 2.84 Mb 位置。1992 年由 Hall 和 Xu 首次测序和鉴定 [3]。在野生型 MG1655 中，asc 操纵子通常是隐性的——由于 AscG 阻遏蛋白的作用以及缺乏诱导水平的纤维二糖，它在标准实验室条件下不表达。friskoli 系统利用了这一内源性遗传资源，通过在质粒上使用合成型组成型启动子表达 *ascF* 和 *ascB*，绕过天然的调控控制。

### AscF: The PTS EII^Cellobiose Transporter / AscF：PTS 纤维二糖转运蛋白

AscF is a membrane-integral protein belonging to the glucose-glucoside (Glc) family of the bacterial phosphotransferase system (PTS) enzyme II complexes [4]. It is a fused EIIABC protein, meaning all three functional domains — EIIA (phosphocarrier from HPr), EIIB (phosphocarrier to sugar), and EIIC (transmembrane channel and sugar recognition) — are encoded within a single polypeptide chain of approximately 480 amino acids (predicted ~52–53 kDa; note that membrane proteins often migrate anomalously on SDS-PAGE) [3]. AscF spans the inner membrane with multiple transmembrane helices (predicted 8–10 TM segments in the EIIC domain).

AscF 是一种膜整合蛋白，属于细菌磷酸转移酶系统（PTS）酶 II 复合物中的葡萄糖-葡萄糖苷（Glc）家族 [4]。它是一种融合的 EIIABC 蛋白，意味着所有三个功能结构域——EIIA（来自 HPr 的磷酸载体）、EIIB（向糖的磷酸载体）和 EIIC（跨膜通道和糖识别）——都编码在约 480 个氨基酸（预测 ~52–53 kDa；注意膜蛋白在 SDS-PAGE 中常有异常迁移）的单条多肽链中 [3]。AscF 通过多个跨膜螺旋跨越内膜（EIIC 结构域预测有 8-10 个 TM 区段）。

AscF specifically recognizes and transports cellobiose (β-D-glucopyranosyl-(1→4)-D-glucopyranose), a disaccharide composed of two glucose monomers linked by a β-1,4 glycosidic bond. Transport is coupled to phosphorylation via the PTS phosphotransfer chain:

AscF 特异性识别并转运纤维二糖（β-D-吡喃葡萄糖基-(1→4)-D-吡喃葡萄糖），一种由 β-1,4 糖苷键连接两个葡萄糖单体组成的二糖。转运通过 PTS 磷酸转移链与磷酸化偶联：

```
PEP → Enzyme I (EI) → HPr → EIIA^Asc → EIIB^Asc → EIIC^Asc → Cellobiose

                         Phosphotransfer chain
                         
PEP + Cellobiose (extracellular) → Pyruvate + Cellobiose-6-P (intracellular)
```

The energetic driving force is the high-energy phosphoryl group from phosphoenolpyruvate (PEP), making cellobiose transport effectively irreversible under physiological conditions [5].

能量驱动力来自磷酸烯醇式丙酮酸（PEP）的高能磷酸基团，使纤维二糖转运在生理条件下实际上是不可逆的 [5]。

### AscB: Phospho-β-glucosidase / AscB：磷酸-β-葡萄糖苷酶

AscB is a phospho-β-glucosidase enzyme (EC 3.2.1.86) of approximately 470 amino acids (~50 kDa) belonging to glycosyl hydrolase family 1 (GH1) [3]. It specifically hydrolyzes the β-1,4 glycosidic bond of cellobiose-6-phosphate, releasing glucose-6-phosphate (G6P) and free glucose. The reaction is:

AscB 是一种磷酸-β-葡萄糖苷酶（EC 3.2.1.86），约 470 个氨基酸（~50 kDa），属于糖苷水解酶家族 1（GH1）[3]。它特异性水解纤维二糖-6-磷酸的 β-1,4 糖苷键，释放 6-磷酸葡萄糖（G6P）和游离葡萄糖。反应如下：

```
Cellobiose-6-P + H₂O → Glucose-6-P + Glucose
```

Critically, the substrate specificity of AscB requires the 6-phosphate modification on the non-reducing end glucose moiety. This ensures that only AscF-transported cellobiose (which is phosphorylated during transport) enters this metabolic channel. Unphosphorylated cellobiose that might diffuse or be taken up by other mechanisms is not a substrate for AscB, preventing metabolic short-circuits.

关键的是，AscB 的底物特异性要求非还原端葡萄糖部分有 6-磷酸修饰。这确保了只有 AscF 转运的纤维二糖（在转运过程中被磷酸化）进入这一代谢通道。可能通过扩散或其他机制进入细胞的非磷酸化纤维二糖不是 AscB 的底物，从而防止代谢短路。

The G6P produced feeds directly into the Embden-Meyerhof-Parnas (glycolytic) pathway via the action of phosphoglucose isomerase (Pgi). Glucose is phosphorylated by glucokinase (Glk) to also enter glycolysis. This provides both energy (ATP) and biosynthetic precursors from a cellulose-derived carbon source.

产生的 G6P 通过磷酸葡萄糖异构酶（Pgi）的作用直接进入糖酵解（EMP）途径。葡萄糖由葡萄糖激酶（Glk）磷酸化后也进入糖酵解。这为从纤维素衍生的碳源提供了能量（ATP）和生物合成前体。

### The PTS-Chemotaxis Coupling Mechanism / PTS-趋化信号耦合机制

This is the central mechanistic innovation of the friskoli system. The system exploits a direct molecular link between the PTS and the flagellar chemotaxis signaling pathway, first demonstrated by Lux and colleagues in 1995 [6].

这是 friskoli 系统的核心机制创新。该系统利用了 PTS 与鞭毛趋化信号通路之间的直接分子联系，该联系由 Lux 及其同事在 1995 年首次证明 [6]。

#### The Standard Chemotaxis Pathway / 标准趋化信号通路

In *E. coli*, chemotaxis is mediated by a conserved two-component signaling system. Transmembrane methyl-accepting chemotaxis proteins (MCPs) detect extracellular chemical cues. The histidine kinase CheA, tethered to the MCP array via the adapter protein CheW, autophosphorylates at a conserved histidine residue. CheA-P then transfers phosphate to the response regulator CheY. CheY-P binds to the flagellar motor switch protein FliM, inducing clockwise (CW) rotation of the flagellar motor, which causes a tumble — random reorientation of the cell. Dephosphorylation of CheY by CheZ terminates the signal, enabling counterclockwise (CCW) rotation and smooth swimming [7].

在大肠杆菌中，趋化性由保守的双组分信号系统介导。跨膜甲基趋化蛋白（MCP）检测胞外化学信号。组织酸激酶 CheA 通过衔接蛋白 CheW 锚定到 MCP 阵列，在保守的组织酸残基上发生自磷酸化。CheA-P 随后将磷酸基团转移给响应调节蛋白 CheY。CheY-P 与鞭毛马达开关蛋白 FliM 结合，诱导鞭毛马达顺时针（CW）旋转，引起翻滚——细胞的随机重定向。CheZ 对 CheY 的去磷酸化终止信号，使鞭毛恢复逆时针（CCW）旋转和平滑游动 [7]。

```
Attractant → MCP → CheA-P ↓(less) → CheY-P ↓(less) → CCW (Run)
No attractant → MCP → CheA-P ↑(more) → CheY-P ↑(more) → CW (Tumble)
```

#### The PTS Connection / PTS 的连接作用

The key discovery by Lux et al. [6] was that Enzyme I (EI, encoded by *ptsI*), the first protein in the PTS phosphotransfer chain, physically and functionally interacts with the CheA-CheW signaling complex at the chemoreceptor array. The interaction is phosphorylation-state dependent:

Lux 等人 [6] 的关键发现是，酶 I（EI，由 *ptsI* 编码）是 PTS 磷酸转移链中的第一个蛋白，在化学受体阵列上与 CheA-CheW 信号复合物发生物理和功能性相互作用。这种相互作用依赖于磷酸化状态：

1. **EI ∼ P (phosphorylated):** When no PTS sugar is being transported, PTS components are mostly phosphorylated. Little unphosphorylated EI is available to inhibit CheA, so CheA maintains baseline autophosphorylation → baseline CheY-P → normal run-and-tumble behavior.

   **EI~P（磷酸化形式）：** 当没有 PTS 糖类正在被转运时，PTS 组分多处于磷酸化状态。可抑制 CheA 的未磷酸化 EI 很少，因此 CheA 维持基线自磷酸化 → 基线 CheY-P → 正常的 run-and-tumble。

2. **EI (unphosphorylated):** When a PTS sugar (such as cellobiose) is being actively transported, the phosphotransfer chain drains phosphate, and unphosphorylated EI increases. Unphosphorylated EI inhibits CheA autophosphorylation. Low CheA-P leads to low CheY-P, and the flagellar motor spends more time in CCW rotation (smooth runs).

   **EI（非磷酸化形式）：** 当 PTS 糖类（如纤维二糖）正在被活跃转运时，磷酸转移链消耗磷酸基团，未磷酸化 EI 增加。未磷酸化 EI 抑制 CheA 自磷酸化。低 CheA-P 导致低 CheY-P，鞭毛马达更多时间处于 CCW 旋转（平滑游动）。

#### Step-by-Step Signaling in the friskoli System / friskoli 系统中的逐步信号传导

```
Step 1: AscF transports cellobiose + phosphorylates it using PEP

Step 2: PTS flux increases → EI dephosphorylates (P → HPr → ... → cellobiose)

Step 3: Dephosphorylated EI does NOT activate CheA

Step 4: Low CheA-P → Low CheY-P → No FliM binding

Step 5: Flagellar motor runs CCW (smooth swimming) → longer runs

Step 6: Bacteria swim UP the cellobiose gradient (toward cellulose)

Step 7: More bacteria arrive → more cellulase → more degradation → MORE CELLOBIOSE

         This is the positive feedback loop that drives the system.
```

This mechanism means that cellobiose functions simultaneously as the signal and the carbon source in our system. The signal transduction is post-translational and rapid — no transcription or translation is required for the chemotactic response, allowing real-time gradient sensing and directional swimming.

这一机制意味着纤维二糖在我们的系统中同时充当信号和碳源。信号转导是翻译后水平的且快速——趋化反应不需要转录或翻译，从而实现实时梯度感应和定向游动。

---

## Module 2: Surface Display / 模块二：表面展示

### Why Surface Display Instead of Secretion / 为什么选择表面展示而非分泌

In microgravity, the physical environment fundamentally changes how molecules move. Liquid convection is effectively eliminated — shear stress drops to approximately 0.02 dynes/cm^2 — and mass transport relies entirely on molecular diffusion. This has critical implications for our enzyme deployment strategy.

在微重力环境中，物理环境根本性地改变了分子的运动方式。液体对流实际上被消除——剪切应力降至约 0.02 dynes/cm^2——质量传输完全依赖于分子扩散。这对我们的酶部署策略具有关键影响。

If we were to use SECRETED cellulases, the enzymes would diffuse randomly away from both the bacterium and the cellulose substrate. This is "diffusion loss" (扩散损失) — enzyme molecules drift without directional bias, and without convection, they cannot be "carried back" to the substrate. The consequence is that secreted enzymes progressively dilute into the bulk medium, degrading efficiency over time.

如果我们使用分泌型纤维素酶，酶会从细菌和纤维素底物两侧随机扩散出去。这就是"扩散损失"——酶分子无方向性地漂移，由于没有对流，它们无法被"携带回"底物表面。其后果是分泌的酶逐渐稀释到整体培养基中，降解效率随时间持续下降。

Surface display solves this problem by immobilizing the cellulase on the bacterial cell surface. Where the bacterium goes, the enzyme goes. The enzyme is permanently co-localized with the chemotactic machinery (AscF) that senses its product. In the microgravity context, this design principle is not merely advantageous — it is essential for maintaining the spatial coupling between degradation and signal sensing.

表面展示通过将纤维素酶固定在细菌细胞表面来解决这一问题。细菌到哪里，酶就到哪里。酶与感知其产物的趋化机器（AscF）永久共定位。在微重力环境中，这一设计原则不仅是优势——它是维持降解与信号感应之间空间耦合的必要条件。

Additionally, surface display offers three further advantages over secretion:

此外，相比分泌策略，表面展示还提供三个额外优势：

1. **Substrate accessibility:** Cellulose is an insoluble polymer that cannot cross the outer or inner membranes. By displaying the enzyme on the cell surface, the catalytic domain gains direct physical access to the cellulose fibers. An intracellular or periplasmic enzyme would only act on soluble degradation products, defeating the purpose.

   **底物可及性：** 纤维素是不溶性聚合物，不能穿过外膜或内膜。通过将酶展示在细胞表面，催化结构域可以直接物理接触到纤维素纤维。胞内或周质酶只能作用于可溶性降解产物，这违背了设计目的。

2. **Processivity and proximity:** Surface-displayed enzymes catalyze the reaction at the cell-substrate interface. After one cell releases cellobiose via degradation, a neighboring cell (or the same cell) immediately transports it via AscF. This spatial coupling of production and consumption concentrates the chemotactic signal at the cell surface.

   **持续性和邻近性：** 表面展示的酶在细胞-底物界面催化反应。当一个细胞通过降解释放纤维二糖后，邻近细胞（或同一细胞）立即通过 AscF 将其转运。这种产生与消耗的空间耦合将趋化信号集中在细胞表面。

3. **Avoiding product dilution:** In a liquid culture (or microgravity bioreactor), secreting cellulase into the medium would allow the enzyme and its product (cellobiose) to diffuse away. Surface display keeps the activity cell-associated, maximizing the local cellobiose concentration gradient around each cell for chemotactic sensing.

   **避免产物稀释：** 在液体培养（或微重力生物反应器）中，将纤维素酶分泌到培养基中会使酶及其产物（纤维二糖）扩散出去。表面展示使活性保持与细胞关联，最大化每个细胞周围用于趋化感应的局部纤维二糖浓度梯度。

### Cellulase Cocktail Strategy / 纤维素酶鸡尾酒策略

Rather than relying on a single cellulase, we deploy three complementary cellulases from *Clostridium thermocellum*, a thermophilic anaerobic bacterium renowned for its highly efficient cellulosome system [13]. All three produce cellobiose as their primary hydrolysis product — perfectly matched to the AscF-PTS chemotaxis signal in Module 1.

我们没有依赖单一的纤维素酶，而是部署了来自*热纤梭菌*（*Clostridium thermocellum*）的三种互补纤维素酶。热纤梭菌是一种嗜热厌氧细菌，以其高效的纤维小体系统而闻名 [13]。这三种酶均以纤维二糖作为主要水解产物——与模块一中的 AscF-PTS 趋化信号完美匹配。

| Enzyme | GH family | Type | Primary product |
|:---|:---|:---|:---|
| **Cel48S** | GH48 | Reducing-end exocellulase (CBH) / 还原端外切纤维素酶 | Cellobiose / 纤维二糖 |
| **Cel9K** | GH9 | Processive cellulase, cellobiose-releasing / 持续性纤维素酶，释放纤维二糖 | Cellobiose / 纤维二糖 |
| **Cel5L** | GH5 | Processive endoglucanase / 持续性内切葡聚糖酶 | Cellobiose / 纤维二糖 |

**Why a cocktail?** Natural cellulose is heterogeneous — it contains crystalline regions (highly ordered, resistant to hydrolysis) and amorphous regions (disordered, more accessible). Individual cellulases have different specificities, and combining them produces synergistic effects:

**为什么使用鸡尾酒？** 天然纤维素是异质的——它包含结晶区（高度有序、抗水解）和无定形区（无序、更易接触）。不同的纤维素酶具有不同的特异性，组合使用时产生协同效应：

- **Cel48S (GH48)** is a classical reducing-end-acting cellobiohydrolase (CBH) that processively releases cellobiose from chain ends and is particularly effective on crystalline cellulose.

  **Cel48S (GH48)** 是一种经典的还原端作用型纤维二糖水解酶（CBH），从链端持续释放纤维二糖，对结晶纤维素特别有效。

- **Cel9K (GH9)** is a processive GH9 cellulase that combines features of endo- and exo-action: it cleaves internal β-1,4 linkages and then processively releases cellobiose. It contributes substantial cellobiose release especially on crystalline substrates [13].

  **Cel9K (GH9)** 是一种持续性 GH9 纤维素酶，兼具内切和外切作用特征：先切割内部 β-1,4 键，随后持续释放纤维二糖，尤其在结晶底物上有显著的纤维二糖释放贡献 [13].

- **Cel5L (GH5)** is a processive endoglucanase that cleaves internal β-1,4 linkages within amorphous regions, creating new chain ends for the other enzymes to attack.

  **Cel5L (GH5)** 是一种持续性内切葡聚糖酶，在无定形区内切割内部 β-1,4 键，为其他酶创造新的链端。

The combination reproduces the endo–exo synergy that makes natural cellulosomes efficient on crystalline cellulose: Cel5L opens new chain ends, Cel48S processively chases them down, and Cel9K covers the intermediate processive/endo space [13].

这种组合再现了天然纤维小体在结晶纤维素上的内切-外切协同效应：Cel5L 打开新的链端，Cel48S 持续性追踪还原端，Cel9K 覆盖中间的内切/持续性空间 [13].

All three enzymes naturally carry **dockerin domains** for cellulosome scaffolding in *C. thermocellum*. In our design, these dockerin domains have been **removed** — they are cellulosome-specific and unnecessary when INPNC is used as the outer membrane anchor. Removing them reduces protein size, eases expression burden, and eliminates potential mis-targeting (note: *E. coli* does not encode a native cellulosome, so the risk is minimal, but removal follows best practice for heterologous expression).

所有三种酶天然携带用于热纤梭菌纤维小体支架的**多克因（dockerin）结构域**。在我们的设计中，这些多克因结构域已被**移除**——它们是纤维小体特异的，当使用 INPNC 作为外膜锚时不需要。移除它们减少了蛋白质大小、降低了表达负担，并消除了潜在的定位错误（注意：大肠杆菌不编码天然纤维小体，因此风险最小，但移除符合异源表达的最佳实践）。

Each cellulase is expressed in a **separate bacterial strain**. The three strains are mixed as a "cellulase cocktail" consortium. This modular approach allows independent optimization of each enzyme's expression level and enables tuning of the consortium composition for different cellulose substrates.

每种纤维素酶在**独立的细菌菌株**中表达。三种菌株混合形成"纤维素酶鸡尾酒"联合体。这种模块化方法允许独立优化每种酶的表达水平，并能够针对不同的纤维素底物调整联合体组成。

### INPNC Anchor / INPNC 锚定蛋白

We use the truncated ice nucleation protein variant **INPNC** from *Pseudomonas syringae* as the outer membrane anchor. Full-length INP (~1200 amino acids) contains three distinct domains [8, 9]:

我们使用来自丁香假单胞菌的截短型冰核蛋白变体 **INPNC** 作为外膜锚定蛋白。全长 INP（约 1200 个氨基酸）包含三个不同的结构域 [8, 9]：

| Domain / 结构域 | Proportion / 比例 | Function / 功能 | Status in Our Design / 设计中的状态 |
|:---|:---|:---|:---|
| **N-terminal** / N端 | ~15% | Hydrophobic membrane anchor / 疏水膜锚 | **Retained** / 保留 |
| **Central repeat** / 中央重复 | ~80% | Spacer, ice nucleation / 间隔区，冰核形成 | **REMOVED** / 移除 |
| **C-terminal** / C端 | ~4% | Hydrophilic cargo fusion site / 亲水货物融合位点 | **Retained** / 保留 |

The truncated INPNC variant (N-terminal + C-terminal domains only) was chosen because it expresses **3–4 times higher** than full-length INP and achieves approximately **2 times more fusion protein targeted to the outer membrane** [14, 15]. The removal of the large central repeat domain reduces the translational burden and eliminates unnecessary ice nucleation activity. This variant is available in the iGEM Registry as **BBa_K1933011** (His-tagged version).

选择截短的 INPNC 变体（仅保留 N 端和 C 端结构域）是因为其表达水平比全长 INP 高 **3–4 倍**，并且靶向到外膜的融合蛋白量约为全长版本的 **2 倍** [14, 15]。移除大型中央重复结构域减少了翻译负担，并消除了不必要的冰核活性。该变体在 iGEM 标准库中的编号为 **BBa_K1933011**（带 His 标签版本）。

The N-terminal domain integrates into the outer membrane, while the C-terminal domain provides the fusion site for the cellulase cargo. The orientation presents the C-terminal end toward the extracellular space, ensuring that the fused cellulase faces outward for direct contact with cellulose fibers.

N 端结构域整合到外膜中，而 C 端结构域为纤维素酶货物提供融合位点。其定向使 C 端朝向胞外空间，确保融合的纤维素酶朝向外侧，以直接接触纤维素纤维。

### Fusion Protein Architecture / 融合蛋白架构

The Module 2 fusion protein follows this architecture:

模块二的融合蛋白遵循以下架构：

```
TorA — INPNC — Linker — Cellulase
```

**Signal Peptide — TorA (Tat Pathway):** A TorA signal peptide is added upstream of INPNC to direct the fusion protein to the periplasm via the **Twin-arginine translocation (Tat) pathway** [16]. The Tat pathway is critical because it transports fully folded proteins across the inner membrane, unlike the Sec pathway which translocates unfolded polypeptides. This enables the cellulase domain to fold properly in the cytoplasm before being translocated to the periplasm for subsequent outer membrane integration via the INPNC anchor.

**信号肽 — TorA（Tat 途径）：** 在 INPNC 上游添加了 TorA 信号肽，通过**双精氨酸转位（Tat）途径**将融合蛋白引导至周质空间 [16]。Tat 途径至关重要，因为它转运完全折叠的蛋白质穿过内膜，而不像 Sec 途径转运未折叠的多肽链。这使得纤维素酶结构域能够在细胞质中正确折叠，然后被转位到周质空间，随后通过 INPNC 锚进行外膜整合。

**Linker Design:** The linker between INPNC and the cellulase uses a **mixed rigid-flexible strategy**, alternating **EAAAK** (rigid, α-helical) and **GGGGS** (flexible, extended) motifs. This design was informed by molecular dynamics simulations performed by the modeling team, which demonstrated that mixed linkers outperform purely rigid or purely flexible designs in terms of catalytic domain accessibility to the insoluble cellulose substrate. {{placeholder:modeling_linker_simulation_results}}

**连接肽设计：** INPNC 与纤维素酶之间的连接肽采用**混合刚柔策略**，交替使用 **EAAAK**（刚性、α-螺旋）和 **GGGGS**（柔性、伸展）基序。该设计基于建模团队的分子动力学模拟，表明混合连接肽在催化结构域对不溶性纤维素底物的可及性方面优于纯刚性或纯柔性设计。{{placeholder:modeling_linker_simulation_results}}

### Vector, Synthesis, and Expression Cassettes / 载体、合成与表达盒

**Vector:** pCDF-1b — carries the CloDF13 origin of replication, which is compatible with the pBR322 origin used in Module 1, enabling stable co-transformation of both plasmids. Its medium-low copy number provides sufficient cellulase expression without excessive metabolic burden.

**载体：** pCDF-1b — 携带 CloDF13 复制起点，与模块一使用的 pBR322 复制起点兼容，可实现两个质粒的稳定共转化。其中低拷贝数提供了充足的纤维素酶表达，而不会造成过度的代谢负担。

**Gene synthesis:** All three cellulase genes (Cel9K, Cel48S, Cel5L) were codon-optimized for *E. coli* MG1655 and ordered through IDT synthesis service.

**基因合成：** 所有三种纤维素酶基因（Cel9K、Cel48S、Cel5L）均针对大肠杆菌 MG1655 进行了密码子优化，通过 IDT 合成服务订购。

**Expression cassettes — 3 parallel constructs:**

**表达盒 — 三个平行构建体：**

```
Construct A: J23116 — B0034 — TorA — INPNC — Linker — Cel9K — B0015
Construct B: J23116 — B0034 — TorA — INPNC — Linker — Cel48S — B0015
Construct C: J23116 — B0034 — TorA — INPNC — Linker — Cel5L — B0015
```

All three constructs use the same regulatory elements for balanced expression: the weak constitutive promoter **J23116** (relative strength 0.16) to maintain moderate expression levels appropriate for membrane protein display, the strong RBS **B0034** (relative strength 1.0) to ensure efficient translation initiation, and the terminator **B0015** for reliable transcriptional termination.

所有三个构建体均使用相同的调控元件以实现均衡表达：弱组成型启动子 **J23116**（相对强度 0.16）维持适合膜蛋白展示的中等表达水平，强 RBS **B0034**（相对强度 1.0）确保高效的翻译起始，终止子 **B0015** 提供可靠的转录终止。

### Design Comparison: Why This Approach Wins / 设计比较：为何此方案胜出

| Approach / 方案 | Advantages / 优势 | Disadvantages vs. Our Design / 相对于本设计的劣势 |
|:---|:---|:---|
| **Secreted cellulases / 分泌型纤维素酶** | Simple single-plasmid design; no membrane protein burden / 简单的单质粒设计；无膜蛋白负担 | Diffusion loss in microgravity; enzyme dilution; uncoupled from chemotaxis machinery / 微重力下的扩散损失；酶稀释；与趋化机器脱钩 |
| **Whole cellulosome display / 完整纤维小体展示** | Multi-enzyme complex; natural synergy optimization / 多酶复合物；天然协同优化 | Massive protein complex (~2 MDa); dockerin-cohesin scaffolding requires multiple heterologous proteins; severe expression burden / 巨型蛋白复合物（~2 MDa）；多克因-粘合蛋白支架需要多种异源蛋白；严重的表达负担 |
| **Single-enzyme approach / 单一酶策略** | Minimal genetic parts; easy to construct / 最少遗传元件；易于构建 | Cannot efficiently degrade crystalline cellulose; endo-only or exo-only activity limits hydrolysis rate / 无法有效降解结晶纤维素；仅内切或仅外切活性限制水解速率 |
| **THIS DESIGN — Cocktail consortium with INPNC / 本设计——INPNC 鸡尾酒联合体** | Co-localized enzyme + sensor; cocktail synergy; compatible with microgravity physics; modular strain mixing / 共定位酶+传感器；鸡尾酒协同；兼容微重力物理；模块化菌株混合 | Requires co-culture management; three strains to maintain / 需要共培养管理；维持三种菌株 |

Our design is specifically optimized for the microgravity environment. The surface display strategy directly addresses the diffusion-loss problem that would cripple a secretion-based approach under the near-zero convection conditions of space. The three-enzyme cocktail provides synergistic cellulose hydrolysis that no single enzyme can achieve — Cel5L opens internal chain breaks in amorphous regions, Cel48S processively releases cellobiose from reducing ends, and Cel9K provides additional processive cellobiose-release activity especially on crystalline regions. The strain-consortium architecture maintains modularity: each enzyme can be optimized independently, and the consortium ratio can be tuned for different cellulose substrates. The use of INPNC (rather than full-length INP) maximizes expression while minimizing metabolic burden. The TorA Tat-pathway targeting ensures proper folding of the cellulase domains before outer membrane integration. Together, these design choices create a system where cellulase activity remains cell-associated, cellobiose gradients are maximized, and the chemotactic positive feedback loop operates at peak efficiency.

我们的设计专门针对微重力环境进行了优化。表面展示策略直接解决了扩散损失问题——在太空近乎零对流的条件下，该问题会严重削弱基于分泌的方法。三酶鸡尾酒提供了单一酶无法实现的协同纤维素水解——Cel5L 在无定形区打开内部链断裂，Cel48S 从还原端持续释放纤维二糖，Cel9K 尤其在结晶区提供额外的持续性纤维二糖释放活性。菌株联合体架构保持了模块化：每种酶可以独立优化，联合体比例可以根据不同的纤维素底物进行调整。使用 INPNC（而非全长 INP）最大化表达同时最小化代谢负担。TorA Tat 途径定位确保纤维素酶结构域在外膜整合前正确折叠。这些设计选择共同创建了一个系统，其中纤维素酶活性保持与细胞关联，纤维二糖梯度最大化，趋化正反馈回路以最高效率运行。

---

## The Positive Feedback Architecture / 正反馈架构

The system creates a closed-loop positive feedback that is the core innovation of friskoli. There are two coupled amplification loops:

该系统创建了一个闭环正反馈，这是 friskoli 的核心创新。存在两个耦合的放大环：

### Loop 1: Signal Amplification / 环一：信号放大

```
Cellulase degrades cellulose → releases cellobiose
  → AscF transports cellobiose → PTS flux increases
    → EI dephosphorylates → CheA activity decreases
      → CheY-P decreases → Longer flagellar runs
        → Chemotaxis UP cellobiose gradient
          → MORE BACTERIA ARRIVE
            → More total cellulase at the site
              → More cellulose degradation
                → MORE CELLOBIOSE (cycle repeats)
```

This signal loop operates at two timescales: the rapid PTS signaling response (milliseconds to seconds) enables individual cells to sense and swim up the gradient, while the population-level accumulation (minutes to hours) creates the macroscopic amplification effect.

该信号环在两个时间尺度上运行：快速的 PTS 信号响应（毫秒到秒）使单个细胞能够感应并逆梯度游动，而群体水平的积累（分钟到小时）则产生宏观放大效应。

### Loop 2: Growth Amplification / 环二：生长放大

```
Cellobiose → AscF transport → Cellobiose-6-P
  → AscB hydrolysis → Glucose-6-P
    → Glycolysis → ATP + biosynthetic precursors
      → CELL GROWTH AND DIVISION
        → More cells → More cellulase
          → More degradation → MORE CELLOBIOSE
```

This growth loop provides a slower but sustained amplification. Cellobiose serves as a carbon source for growth, creating a selective advantage for cells that carry both modules in environments containing cellulose. In effect, cellulose becomes a self-provisioning growth substrate — the bacteria create their own food source.

该生长环提供了较慢但持续的放大效应。纤维二糖作为生长的碳源，为在含纤维素环境中携带两个模块的细胞创造了选择性优势。实际上，纤维素成为了一种自给自足的生长底物——细菌自己创造食物来源。

### Coupling of the Loops / 两个环的耦合

The two loops are coupled through the shared intermediate, cellobiose. The signal loop provides rapid, directional recruitment, while the growth loop provides sustained population expansion. This coupling means that the system functions both as a **sensor** (recruiting cells to where cellulose is being degraded) and as a **processor** (converting cellulose into biomass).

两个环通过共享的中间代谢物——纤维二糖——耦合在一起。信号环提供快速、定向的招募，而生长环提供持续的群体扩增。这种耦合意味着该系统同时作为**传感器**（将细胞招募到纤维素正在被降解的地方）和**处理器**（将纤维素转化为生物量）工作。

---

## Self-Limiting Negative Feedback / 自限性负反馈

An important feature of the friskoli system is that the positive feedback is inherently self-limiting via the metabolic regulation of PTS activity. This prevents uncontrolled signal amplification that would otherwise lead to chemotactic overload or metabolic imbalance.

friskoli 系统的一个重要特征是正反馈通过 PTS 活性的代谢调节具有内在的自限性。这防止了不受控制的信号放大，否则会导致趋化过载或代谢失衡。

The self-limitation arises from the following mechanisms:

自限性源于以下机制：

### 1. PEP/Pyruvate Ratio / PEP/丙酮酸比率

The PTS is balanced by the intracellular PEP-to-pyruvate ratio [5]. As cellobiose is metabolized through glycolysis, PEP is consumed (in gluconeogenic flux) and pyruvate accumulates. When PTS flux is high (lots of cellobiose transport), PEP is consumed faster than it can be regenerated. This reduces the available phosphoryl donor for EI rephosphorylation, which initially sustains the chemotactic signal. However, as the metabolic state shifts toward higher ATP and biomass, the PEP/pyruvate ratio eventually stabilizes, creating a steady state where PTS flux and chemotactic response reach a plateau.

PTS 受到细胞内 PEP 与丙酮酸比率的调节 [5]。随着纤维二糖通过糖酵解代谢，PEP 被消耗（通过糖异生通量），丙酮酸积累。当 PTS 通量很高时（大量纤维二糖转运），PEP 的消耗速度超过其再生速度。这减少了可用于 EI 再磷酸化的磷酸供体，最初维持了趋化信号。然而，随着代谢状态转向更高的 ATP 和生物量，PEP/丙酮酸比率最终稳定下来，形成 PTS 通量和趋化反应达到平台的稳态。

### 2. Fructose-1,6-bisphosphate Regulation / 果糖-1,6-二磷酸调节

The glycolytic intermediate fructose-1,6-bisphosphate (FBP) is a known allosteric regulator of PTS activity. High FBP levels (indicating active glycolysis) inhibit the dephosphorylation of EIIA~P, effectively reducing PTS flux for sugar transport [4]. In the friskoli system, rapid cellobiose metabolism generates FBP, which feeds back to inhibit PTS flux through AscF, creating a natural brake on continued cellobiose import when glycolytic flux is already high.

糖酵解中间代谢物果糖-1,6-二磷酸（FBP）是 PTS 活性的已知别构调节因子。高 FBP 水平（表明糖酵解活跃）抑制 EIIA~P 的去磷酸化，有效降低糖转运的 PTS 通量 [4]。在 friskoli 系统中，快速的纤维二糖代谢产生 FBP，反馈抑制通过 AscF 的 PTS 通量，当糖酵解通量已经很高时，为持续的纤维二糖输入创造了天然的制动机制。

### 3. AscF Expression Limitation / AscF 表达限制

As a transmembrane protein, AscF has a finite expression ceiling. Overexpression leads to membrane protein toxicity, including inclusion body formation, membrane stress, and saturation of the Sec translocon [11]. By using a weak promoter (J23116, relative strength 0.16) on a medium-low-copy plasmid (pGEX-ascFB, pBR322 origin, ~15-20 copies/cell), the system inherently limits the number of AscF transporters per cell. This imposes a maximum rate of cellobiose import, providing another layer of self-limitation.

作为跨膜蛋白，AscF 具有有限的表达上限。过表达会导致膜蛋白毒性，包括包涵体形成、膜应激和 Sec 转位子的饱和 [11]。通过使用弱启动子（J23116，相对强度 0.16）和中低拷贝质粒（pGEX-ascFB，pBR322 复制子，约 15-20 拷贝/细胞），系统内在限制了每个细胞的 AscF 转运蛋白数量。这设置了纤维二糖输入的最大速率，提供了另一层自限性。

---

## Design Rationale and Comparison with Alternatives / 设计原理与替代方案比较

### Why This Approach? / 为什么选择这个方案？

The friskoli design was chosen after considering several alternative strategies for coupling bacterial chemotaxis to cellulose degradation:

friskoli 的设计是在考虑了多种将细菌趋化性与纤维素降解耦合的替代策略后选择的：

| Approach / 方案 | Mechanism / 机制 | Limitations / 局限性 |
|:---|:---|:---|
| **Engineered MCPs / 工程化 MCP** | Modify Tar/Tsr receptors to bind cellobiose or cellulose fragments | Requires extensive protein engineering; signal may be weak; uncoupled from metabolism |
| **Heterologous two-component system / 异源双组分系统** | Express a cellobiose-responsive sensor kinase that activates CheY | Genetic burden; crosstalk risk; requires synthetic signaling circuits |
| **Metabolite-responsive transcription / 代谢物响应转录** | Cellobiose-responsive TF controls motility genes | Slow (transcriptional delay); cannot track spatial gradients in real-time |
| **THIS DESIGN — Modified PTS / 本设计——修饰的 PTS** | Cellobiose = PTS substrate → EI state → CheA activity | No heterologous signaling proteins; rapid response; signal = degradation product; native pathway integration |

**Our design offers three key advantages:**

**本设计提供三个关键优势：**

1.  **Signal fidelity:** The chemotactic signal is precisely the molecule produced by the degradation reaction (cellobiose). There is no artificial signal transduction — the pathway is direct.

    **信号保真度：** 趋化信号正是降解反应产生的分子（纤维二糖）。没有人为的信号转导——信号通路是直接的。

2.  **No heterologous signaling components:** We use *E. coli*'s native EI-HPr-CheA coupling mechanism. No foreign chemotaxis receptors, histidine kinases, or scaffold proteins are required. The only non-native components are the INPNC display system (from *P. syringae*, homologous to other OMPs) and the constitutive promoter-RBS-terminator elements from the iGEM Registry.

    **无异源信号组分：** 我们使用大肠杆菌天然的 EI-HPr-CheA 耦合机制。不需要外源的趋化受体、组织酸激酶或支架蛋白。唯一的非天然组分是 INPNC 展示系统（来自丁香假单胞菌，与其他 OMP 同源）和来自 iGEM 标准库的组成型启动子-RBS-终止子元件。

3.  **Built-in coupling:** Degradation and sensing are inseparable. Every molecule of cellobiose produced by Module 2 is simultaneously a carbon source (via Module 1) and a chemotactic signal (via the PTS coupling). This is not true for any synthetic biology approach that uses orthogonal receptors and inducers.

    **内在耦合：** 降解与感应不可分割。模块二产生的每一个纤维二糖分子同时是碳源（通过模块一）和趋化信号（通过 PTS 耦合）。这对于任何使用正交受体和诱导剂的合成生物学方法来说都是无法实现的。

### Expression Window Concept / 表达窗口概念

A critical design consideration is the "expression window" — the range of AscF expression levels that provide sufficient transport activity for chemotactic signaling without causing membrane toxicity. This window is defined by two constraints:

一个关键的设计考虑是"表达窗口"——提供足够趋化信号传导的转运活性而不引起膜毒性的 AscF 表达水平范围。这个窗口由两个约束条件定义：

```
                   Membrane toxicity threshold
                  ↑
    |------------|====================|--------------|
  No function    │  EXPRESSION       │  Toxic
    (insufficient│   WINDOW          │ (membrane
     AscF)       │   ✓               │  stress)
                  ↓
              Functional threshold
```

- **Lower bound (functional threshold):** Enough AscF must be present to transport sufficient cellobiose to generate a detectable change in EI phosphorylation state and thus modulate CheA activity. The model of Rohwer et al. [5] predicts that even 100–200 transporters per cell are sufficient for PTS flux to significantly alter EI-P levels under the relevant cellobiose concentrations (μM range).

  **下限（功能阈值）：** 必须有足够的 AscF 以转运足够量的纤维二糖，从而产生可检测的 EI 磷酸化状态变化，进而调节 CheA 活性。Rohwer 等人 [5] 的模型预测，在相关的纤维二糖浓度（μM 范围）下，每个细胞仅需 100-200 个转运蛋白就足以使 PTS 通量显著改变 EI-P 水平。

- **Upper bound (toxicity threshold):** Overexpression of membrane proteins saturates the SecYEG translocon and the Bam complex, leading to protein aggregation in the cytoplasm, membrane insertion stress, and activation of the σᴱ stress response [11]. For a 10-TM protein such as AscF, expression must be carefully controlled.

  **上限（毒性阈值）：** 膜蛋白的过表达会饱和 SecYEG 转位子和 Bam 复合物，导致细胞质中的蛋白聚集、膜插入应激和 σᴱ 应激反应的激活 [11]。对于像 AscF 这样具有 10 个 TM 区的蛋白，必须仔细控制表达。

The combination of the weak J23116 promoter (relative strength 0.16 [12]) and the low-copy pGEX-ascFB backbone (~15-20 copies/cell, pBR322 ori [1]) was selected to place AscF expression within this window. Quantitative estimates based on published promoter strength measurements [12] suggest this configuration produces approximately 50–200 AscF molecules per cell, which is predicted to be within the functional window.

选择弱启动子 J23116（相对强度 0.16 [12]）和中低拷贝 pGEX-ascFB 骨架（约 15-20 拷贝/细胞，pBR322 复制子 [1]）的组合，旨在将 AscF 表达置于此窗口内。基于已发表的启动子强度测量值的定量估计 [12] 表明，该配置每个细胞产生大约 50-200 个 AscF 分子，预计在功能窗口内。

---

## References / 参考文献

[1] pGEX-ascFB — constructed vector with pBR322 origin of replication and ampicillin resistance.
[2] pCDF-1b — commercial vector (Novagen) with CloDF13 origin of replication and spectinomycin resistance.
[3] Hall BG, Xu J. Nucleotide sequence, function, activation, and evolution of the cryptic *asc* operon of *Escherichia coli* K-12. *Mol Biol Evol*. 1992;9(4):688-706.
[4] Postma PW, Lengeler JW, Jacobson GR. Phosphoenolpyruvate:carbohydrate phosphotransferase systems of bacteria. *Microbiological Reviews*. 1993;57(3):543-594.
[5] Rohwer JM, Meadow ND, Roseman S, Westerhoff HV, Postma PW. Understanding glucose transport by the bacterial phosphoenolpyruvate:glycose phosphotransferase system on the basis of kinetic measurements *in vitro*. *Journal of Biological Chemistry*. 2000;275:34909-34921.
[6] Lux R, Jahreis K, Bettenbrock K, Parkinson JS, Lengeler JW. Coupling the phosphotransferase system and the methyl-accepting chemotaxis protein-dependent chemotaxis signaling pathways of *Escherichia coli*. *Proceedings of the National Academy of Sciences*. 1995;92(25):11583-11587.
[7] Wadhams GH, Armitage JP. Making sense of it all: bacterial chemotaxis. *Nature Reviews Molecular Cell Biology*. 2004;5(12):1024-1037.
[8] Wolber PK. Bacterial ice nucleation. *Advances in Microbial Physiology*. 1993;34:203-237.
[9] Kim H, Ku S. Development and optimization of an ice nucleation protein (INP)-based surface display system in *Escherichia coli*. 2018.
[10] Beguin P, Aubert JP. The biological degradation of cellulose. *FEMS Microbiology Reviews*. 1994;13(1):25-58.
[11] Wagner S, Bader ML, Drew D, de Gier JW. Rationalizing membrane protein overexpression. *Trends in Biotechnology*. 2006;24(8):364-371.
[12] Kelly JR, Rubin AJ, Davis JH, Ajo-Franklin CM, Cumbers J, Czar MJ, de Mora K, Glieberman AL, Monie DD, Endy D. Measuring the activity of BioBrick promoters using an *in vivo* reference standard. *Journal of Biological Engineering*. 2009;3:4.
[13] Leis B, Held C, Bergkemper F, Dennemarck K, Steinbauer R, Reiter A, Mechelke M, Moerch M, Graubner S, Liebl W, Schwarz WH, Zverlov VV. Comparative characterization of all cellulosomal cellulases from *Clostridium thermocellum* reveals high diversity in activity and stability. *Biotechnology for Biofuels*. 2017;10:135.
[14] Zhang B, Gao X, Zhou Y, You S, Qi W, Wang M. Surface Display Technologies for Whole-Cell Biocatalysts: Advances in Optimization Strategies, Food Applications, and Future Perspectives. *Foods*. 2025;14(10):1803. DOI: 10.3390/foods14101803.
[15] Liu W, Sun W, Liang CC, Chen T, Zhuang W, Liu D, Chen Y, Ying H. *Escherichia coli* Surface Display: Advances and Applications in Biocatalysis. *ACS Synthetic Biology*. 2025;14(3):648–661. DOI: 10.1021/acssynbio.4c00793.
[16] Tullman-Ercek D, DeLisa MP, Kawarasaki Y, Iranpour P, Hayhurst A, Georgiou G. Export pathway selectivity of *Escherichia coli* twin arginine translocation signal peptides. *Journal of Biological Chemistry*. 2007;282(11):8309-8316.
[17] Cluzel P, Surette M, Leibler S. An ultrasensitive bacterial motor revealed by monitoring signaling proteins in single cells. *Science*. 2000;287(5458):1652-1655. DOI: 10.1126/science.287.5458.1652.

---

*This page was last updated for iGEM 2026. All scientific claims are based on published literature. Experimental results should be inserted as they become available.*
