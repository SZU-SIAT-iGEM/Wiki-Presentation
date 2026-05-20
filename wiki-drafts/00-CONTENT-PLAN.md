# friskoli Wiki Content Plan

Project: friskoli  
Team: SZU-SIAT-China  
Track: Space Track  
Year: 2026

这个文件记录当前仓库里的 Wiki 草稿状态，应当和 `wiki-drafts/` 目录下的实际文件保持一致。

## 当前草稿文件

| # | 文件 | Wiki 页面 | 当前状态 | 主要检查点 |
| --- | --- | --- | --- | --- |
| 0 | `00-CONTENT-PLAN.md` | Planning note | 已更新 | 保持本表与仓库实际文件一致 |
| 1 | `01-Home.md` | Home | 已有草稿 | 项目定位、tagline、导航、视觉叙事 |
| 2 | `02-Description.md` | Description | 已有草稿 | 问题叙述、asc operon 方案、文献引用 |
| 3 | `03-Design.md` | Design | 已有草稿 | genetic design、模块逻辑、机制准确性 |
| 4 | `04-Engineering-Success.md` | Engineering Success | 已有草稿 | DBTL 逻辑、后续实验循环证据 |
| 7 | `07-Parts.md` | Parts | 已有草稿 | part 描述、Registry 引用、表征缺口 |
| 9 | `09-Safety.md` | Safety | 已有草稿 | chassis 安全、实验室操作、风险评估、审批 |
| 10 | `10-Model.md` | Model | 已有草稿 | 方程、假设、参数来源、验证计划 |
| 11 | `11-Human-Practices.md` | Human Practices | 已有草稿 | stakeholders、访谈记录、反馈带来的项目修改 |
| 12 | `12-Education-Communication.md` | Education & Communication | 已有草稿 | 活动记录、照片、问卷结果 |
| 12b | `12b-Friskoli-I-Game.md` | Friskoli I Game | 已有草稿 | 游戏文本、教育目的、与 outreach 的关系 |
| 14 | `14-Proposed-Implementation.md` | Proposed Implementation | 已有草稿 | 可行性、部署场景、合作方、监管问题 |

## 计划中但尚未放入仓库的页面

这些页面属于更完整的 Wiki 计划，但当前仓库里还没有对应草稿：

| 计划页面 | 预计需要补充的内容 |
| --- | --- |
| Results | 实验数据与图表 |
| Experiments / Protocols | 最终 protocol 与真实实验条件 |
| Notebook | 按时间记录的实验日志 |
| Entrepreneurship | 市场分析与商业模式 |
| Collaborations | 已确认合作与证据材料 |
| Contribution | Registry 或 community contribution 细节 |
| Software | 部署链接、代码、demo 或截图 |
| Hardware | 如果实际做了硬件，再补设计与结果 |
| Team | 队员姓名、角色、照片、简介 |
| Attributions | 具体贡献记录 |

## 修改建议怎样提交

每一条独立修改建议请新开一个 GitHub Issue，不要把所有反馈都写在一个长帖里。

Issue 里建议包含：

1. 对应文件名。
2. 草稿中的位置，比如标题或段落。
3. 需要修改的内容。
4. 如果修改依赖数据、文献、图片、访谈记录或实验记录，请附上来源。

一个主题一个 Issue。这样后面分工和修改会清楚很多。

## 占位符约定

草稿里如果有暂时缺材料的位置，可以用这些标记：

| 标记 | 含义 |
| --- | --- |
| `{{experiment:capillary_data}}` | 需要 capillary 或 chemotaxis 实验结果 |
| `{{experiment:growth_curve}}` | 需要 growth curve 数据 |
| `{{event:expert_interview_1}}` | 需要专家访谈记录 |
| `{{event:collaboration_x}}` | 需要合作活动细节 |
| `{{team:member_name}}` | 需要队员姓名或简介 |
| `{{data:model_G_scan}}` | 需要 model simulation 结果 |
| `{{protocol:optimization}}` | 需要优化后的 protocol |

## 检查优先级

1. 先看事实：机制、实验计划、方程、引用、安全描述。
2. 再补证据：数据、记录、图片、访谈、问卷、参考文献。
3. 事实稳定后再改结构和措辞。
4. 最后再转换成正式 Wiki 页面。
