# 🦾 Embodied Zoo

> 具身智能开源项目的"动物园" — 系统化分类、导航与全景追踪

[![Pages](https://img.shields.io/badge/GitHub%20Pages-live-brightgreen)](https://your-org.github.io/embodied-zoo)
[![License](https://img.shields.io/badge/license-CC--BY--SA%204.0-blue)](LICENSE)
[![Studies](https://img.shields.io/badge/research%20directions-13-orange)](#研究方向)
[![Entities](https://img.shields.io/badge/entities-35-blue)](#目录结构)

---

## 这是什么？

Embodied Zoo 是一个**持续更新的具身智能（Embodied AI）知识库**，采用 [Karpathy's LLM Wiki](https://gist.github.com/karpathy/442a6bf555914893e9891c11519de94f) 模式维护：

- **原始材料层 (raw/)**：论文、文章、访谈的原始文本，不可变
- **实体层 (entities/)**：公司、产品、开源项目的独立卡片
- **概念层 (concepts/)**：研究方向、技术范式的深度梳理
- **对比层 (comparisons/)**：多维度横向对比分析

目标是让每一个进入具身智能领域的研究者，在 **10 分钟内**看清全局，在 **1 小时内**找到可切入的具体方向。

---

## 🗺️ 当前全景

### 13 个研究方向

| # | 方向 | 核心问题 | 代表项目 |
|---|------|----------|----------|
| 1 | **物理仿真器与数字孪生** | 保真度 vs 速度 vs 可微分 | Genesis, Isaac Lab, MuJoCo |
| 2 | **数据集与数据引擎** | 如何低成本获取高质量多样化数据** | Open X-Embodiment, LeRobot |
| 3 | **VLA 模型架构** | 视觉-语言-动作的统一映射 | RT-2, OpenVLA, SpatialVLA |
| 4 | **世界模型** | 让机器人在"脑子里"预测物理 | 1X World Model, Tesla FSD |
| 5 | **动作生成** | 平滑高频连续动作轨迹 | Diffusion Policy, Flow Matching, π⁰ |
| 6 | **Sim2Real 迁移** | 仿真训练如何无缝落地 | Domain Randomization, RMA |
| 7 | **人形机器人运动控制** | 移动+操作+平衡的联合优化 | PACE, GMR, Humanoid-Gym |
| 8 | **开源硬件与低成本平台** | 降低研究门槛 | Unitree G1, Berkeley Humanoid |
| 9 | **可微分机器人学** | 让物理、几何、运动学可微分 | DiffTaichi, Warp |
| 10 | **具身大脑** | 统一记忆、推理、自我意识 | MemoryVLA, N.E.K.O, CogACT |
| 11 | **长程任务推理** | 多步骤、因果依赖的复杂任务 | CALVIN, Reflect-VLM |
| 12 | **跨本体学习与泛化** | 同一策略适配多种形态 | Open X-Embodiment, π⁰ |
| 13 | **基准测试与评估** | 领域的"度量衡" | ManiSkill, robosuite, MetaWorld |

### 商业公司 (12 家)

`[figure-ai](entities/figure-ai.md)` · `[tesla-optimus](entities/tesla-optimus.md)` · `[boston-dynamics](entities/boston-dynamics.md)` · `[1x-technologies](entities/1x-technologies.md)` · `[agility-robotics](entities/agility-robotics.md)` · `[apptronik](entities/apptronik.md)` · `[unitree](entities/unitree.md)` · `[enchanted-tools](entities/enchanted-tools.md)` · `[google-deepmind](entities/google-deepmind.md)` · `[nvidia-isaac](entities/nvidia-isaac.md)` · `[physical-intelligence](entities/physical-intelligence.md)` · `[genesis-ai](entities/genesis-ai.md)`

### 开源项目与平台 (7 个)

`[genesis-world](entities/genesis-world.md)` (28.7k⭐) · `[lerobot](entities/lerobot.md)` (23.9k⭐) · `[maniskill](entities/maniskill.md)` (2.9k⭐) · `[robosuite](entities/robosuite.md)` (2.4k⭐) · `[robotwin](entities/robotwin.md)` (2.3k⭐) · `[metaworld](entities/metaworld.md)` (1.8k⭐) · `[roboverse](entities/roboverse.md)` (1.7k⭐)

> 全部项目均附 GitHub 直达链接，点击即可跳转。

---

## 📁 目录结构

```
embodied-zoo/
├── README.md                      # 本文件
├── SCHEMA.md                      # 知识库规范（命名、标签、更新策略）
├── index.md                       # 总目录与导航
├── log.md                         # 更新日志（追加式）
│
├── raw/                           # Layer 1: 原始材料（不可变）
│   ├── articles/                  # 网络文章、调研报告
│   ├── papers/                    # 论文、arXiv 预印本
│   ├── transcripts/               # 访谈、会议记录
│   └── assets/                    # 图片、图表
│
├── entities/                      # Layer 2: 实体卡片
│   ├── figure-ai.md               # 公司/组织
│   ├── tesla-optimus.md
│   ├── genesis-world.md           # 开源项目
│   └── ...
│
├── concepts/                      # Layer 2: 概念与方向
│   ├── embodied-ai-research-landscape.md   # 13 方向全景图
│   ├── vla-vision-language-action.md       # VLA 架构
│   ├── embodied-brain.md                   # 具身大脑
│   └── ...
│
├── comparisons/                   # Layer 2: 横向对比
│   ├── vla-architecture-comparison.md
│   └── data-strategy-comparison.md
│
└── queries/                       # Layer 2: 归档的查询结果
```

---

## 🚀 三种使用方式

### 方式一：Obsidian（推荐，最强体验）

1. 克隆仓库
   ```bash
   git clone https://github.com/your-org/embodied-zoo.git
   cd embodied-zoo
   ```
2. 用 [Obsidian](https://obsidian.md) 打开本目录作为 Vault
3. 开启 **Graph View** 查看知识图谱，安装 **Dataview** 插件实现按标签筛选

> 原生支持 `[wikilinks](wikilinks.md)`、YAML frontmatter、反向链接。

### 方式二：GitHub 直接浏览

所有内容均为标准 Markdown，可直接在 GitHub 上阅读。从 [`index.md`](index.md) 开始导航。

### 方式三：GitHub Pages（在线站点）

访问 [在线站点](https://your-org.github.io/embodied-zoo) 获得：
- 全文搜索
- 知识图谱可视化
- 反向链接自动追踪
- 移动端适配

---

## 🏗️ 如何贡献

Embodied Zoo 是**人机协作**知识库：

- **人类**：发现新论文/项目/公司，判断什么值得收录
- **Agent**：格式化、交叉引用、维护一致性

### 贡献方式

1. **提交 Issue**：报告新开源项目、商业动态、方向变化
2. **提交 PR**：修正事实错误、补充链接、翻译内容
3. **提供 Raw 源**：把有价值的论文/文章/访谈发给我们，由 Agent 完成知识提取

### 收录标准

- **实体页**：公司/项目需在具身智能领域有实质性动作（论文、产品、开源代码）
- **概念页**：方向需有 2+ 独立研究组跟进，或已成为社区共识
- **不收录**：纯概念炒作、无代码无论文的"空气项目"

---

## 📜 许可

知识库内容采用 [CC BY-SA 4.0](LICENSE) 协议。

原始材料 (raw/) 归各自原作者所有，仅供研究参考。

---

> *在具身智能的动物园里，每一只"动物"都有自己的栖息地。我们希望这张地图，能帮你找到你想观察的那一只。* 🦁🤖
