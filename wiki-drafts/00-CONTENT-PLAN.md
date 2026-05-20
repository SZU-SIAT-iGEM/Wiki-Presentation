# friskoli Wiki Content Plan / 内容规划

> **Project:** friskoli
> **Team:** SZU-SIAT-China | **Track:** Space Track | **Year:** 2026

---

## Overview / 总览

This document maps every iGEM Wiki section to a status:

| Color | Status | Meaning |
|-------|--------|---------|
| 🟢 **Write Now** | Can write with confidence | Literature-backed science, design rationale, storytelling |
| 🟡 **Partial** | Write framework + placeholders | Needs real data from experiments or events |
| 🔴 **Wait** | Full placeholder | Requires experimental results or confirmed events |

---

## Section Status Matrix

| # | Section | Status | What We Can Write Now | What Needs Data/Events |
|---|---------|--------|----------------------|----------------------|
| 1 | **Home / 首页** | 🟢 | Project name (friskoli), team (SZU-SIAT-China), tagline, space theme, navigation | — |
| 2 | **Description / 项目描述** | 🟢 | Microgravity diffusion problem, asc operon solution, positive feedback concept, all literature citations | — |
| 3 | **Design / 设计** | 🟢 | ascF/ascB module, PTS chemotaxis mechanism, INP surface display, two-plasmid architecture, positive feedback loop, self-limiting mechanism | — |
| 4 | **Engineering Success / 工程成功** | 🟡 | DBTL framework, planned cycles, design rationale | Actual cycle outcomes, experimental data |
| 5 | **Results / 实验结果** | 🔴 | Section structure only | All experimental data |
| 6 | **Experiments / Protocols** | 🟡 | Planned protocols, methods description | Refined protocols, actual conditions |
| 7 | **Parts / 生物元件** | 🟢 | ascF, ascB, INP-Cellulase descriptions, Registry references | Characterization data (if available) |
| 8 | **Notebook / 实验记录** | 🔴 | Template structure | Actual lab records |
| 9 | **Safety / 安全** | 🟢 | BSL1, MG1655 chassis safety, standard lab practices, risk assessment | Institutional approvals |
| 10 | **Model / 建模** | 🟢 | Barkai-Leibler framework, PTS signaling ODE, agent-based model design, gain factor G concept, parameter sources, validation plan | Simulation results, G-scan curves, model-experiment comparison |
| 11 | **Human Practices / 人类实践** | 🟡 | Framework, target stakeholders, planned approach | Actual interviews, feedback received, project changes from feedback |
| 12 | **Education & Communication** | 🟡 | Web-based simulation tool concept, planned outreach | Actual events, photos, survey results |
| 13 | **Entrepreneurship / 创业** | 🟡 | Space bioreactor market concept | Market data, business model |
| 14 | **Proposed Implementation / 实施方案** | 🟢* | *Storytelling zone!* Vision for space waste recycling, universal platform concept, long-term roadmap | Specific partners/regulatory info |
| 15 | **Collaborations / 合作** | 🟡 | Planned collaboration areas | Actual collaborations |
| 16 | **Team / 团队** | 🟢 | Team name, university department, structure | Member names, photos, bios |
| 17 | **Attributions / 归属说明** | 🟡 | Framework, categories | Actual names, specific contributions |
| 18 | **Contribution / 贡献** | 🟡 | Contribution concept | Actual Registry submissions |
| 19 | **Software / 软件** | 🟡 | Web simulator design concept | Actual deployed tool URL, demo |
| 20 | **Hardware / 硬件** | 🔴 | — | If any hardware was built |

\* = Storytelling-encouraged section

---

## Storytelling vs. Factual Guide / 叙事与事实指南

### 🔬 Must Be Factual (No Exaggeration)
Areas where accuracy is critical because judges will verify:

| Area | Why It Matters | What to Do |
|------|---------------|------------|
| **Literature citations** | Judges know the papers | Quote accurately, don't over-claim |
| **Molecular mechanism** | Peer review scrutiny | Stay within established PTS chemotaxis literature |
| **Experimental methods** | Reproducibility | Describe exactly what was done (or planned) |
| **Experimental results** | Core judging evidence | Report honestly, never fabricate |
| **Model equations** | Scientific credibility | Use correct equations from cited papers |
| **Safety claims** | Institutional requirement | Be accurate about BSL and risk |

### 🎨 Storytelling Encouraged (Can Be Creative)
Narrative framing that should be compelling but not misrepresent science:

| Area | Story Angle | Creative Freedom |
|------|------------|------------------|
| **Home page tagline** | "When gravity disappears, bacteria must learn to find food again" | High — metaphorical language |
| **Problem narrative** | Space vs Earth contrast | High — set emotional stakes |
| **Inspiration** | Why asc operon? "A sleeping gene awakened" | Medium — narrative framing |
| **Vision section** | Long-term future of space bioreactors | High — "what if" scenarios |
| **Chemotaxis as functional alternative to stirring** | Moving cells instead of fluid | Medium — functional equivalence, not fluid dynamics |
| **Positive feedback poetry** | The beauty of self-reinforcing systems | High — philosophical framing |
| **Implementation** | A universal platform for space waste | Medium — aspirational but grounded |

### ⚠️ Grey Zone — Handle with Care

| Area | Risk | Approach |
|------|------|----------|
| **Claiming "first"** | Another team may have done it | Say "novel approach" not "first" |
| **Claiming performance** | Without data it's speculation | Use conditional language: "we expect", "our model predicts" |
| **Microgravity advantage** | Only RPM simulation, not real space | Clearly state "simulated microgravity" |
| **Clinical/medical claims** | High scrutiny | Avoid; focus on technical demonstration |

---

## Placeholder Convention / 占位符约定

Use these markers in Wiki drafts so team members know what to fill:

| Marker | Meaning |
|--------|---------|
| `{{experiment:capillary_data}}` | Experimental result needed |
| `{{experiment:growth_curve}}` | Growth curve data |
| `{{event:expert_interview_1}}` | Expert interview details |
| `{{event:collaboration_x}}` | Collaboration details |
| `{{team:member_name}}` | Team member name |
| `{{data:model_G_scan}}` | Model simulation result |
| `{{protocol:optimization}}` | Refined protocol |

---

## Writing Order / 写作顺序

This is the recommended order based on what we can write now:

```
Priority 1 — Write Now (No Data Needed):
  ├── Home / 首页
  ├── Description / 项目描述
  ├── Design / 设计
  ├── Parts / 生物元件
  ├── Safety / 安全
  ├── Model / 建模 (theory & framework)
  └── Proposed Implementation / 实施方案 (vision)

Priority 2 — Framework Only (Data Later):
  ├── Engineering Success (DBTL structure)
  ├── Human Practices (planned activities)
  ├── Education & Communication (concept)
  ├── Entrepreneurship (framework)
  ├── Collaborations (planned areas)
  ├── Software (design concept)
  ├── Team (structure + placeholder names)
  └── Attributions (framework + placeholder names)

Priority 3 — Wait for Data:
  ├── Results (all experimental data)
  ├── Experiments/Protocols (refinements)
  ├── Notebook (chronological records)
  ├── Model validation (G-scan results)
  ├── Contribution (Registry submissions)
  └── Hardware (if any)
```

---

## File Structure / 文件结构

Wiki drafts live alongside the meta-guide:

```
igem-wiki-guide/
├── wiki-drafts/              ← Real Wiki content for friskoli
│   ├── 00-CONTENT-PLAN.md    ← This file
│   ├── 01-Home.md
│   ├── 02-Description.md
│   ├── 03-Design.md
│   ├── 04-Engineering-Success.md
│   ├── ... (one file per wiki page)
│   └── appendices/
│       ├── glossary.md
│       └── references.md
├── 00-Overview/              ← Meta-guide (already created)
├── 01-Project-Core/
└── ...
```
