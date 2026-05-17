---
title: 具身智能基准测试 (Embodied Benchmarks)
created: 2026-05-11
updated: 2026-05-11
type: concept
tags: [benchmark, evaluation, embodiment, robotics, manipulation]
sources: [raw/articles/github-embodied-ai-projects-2026-05-11.md]
confidence: high
---

# 具身智能基准测试

> 基准测试是具身智能领域的"度量衡"——它决定了我们评估什么能力、用什么指标、以及在什么环境中测试。没有好的基准，就无法区分是真进步还是过拟合。当前基准已从单一任务（如抓取）演进到长程组合任务、跨本体泛化、因果推理和终身学习。

## 按任务类型分类

### 1. 操作技能 (Manipulation)

| 基准 | 星标 | 核心能力 | 仿真器 | 备注 |
|------|------|---------|--------|------|
| **[ManiSkill](https://github.com/haosulab/ManiSkill)** | 2860 ⭐ | 通用操作技能 | [SAPIEN](https://github.com/haosulab/SAPIEN) | GPU并行，NeurIPS'21 |
| **[robosuite](https://github.com/ARISE-Initiative/robosuite)** | 2405 ⭐ | 模块化操作 | MuJoCo | ARISE-Initiative，可组合环境 |
| **[MetaWorld](https://github.com/Farama-Foundation/Metaworld)** | 1814 ⭐ | 多任务/元学习 | MuJoCo | 50个操作任务，MT1/MT10/MT50 |
| **[LIBERO](https://github.com/Lifelong-Robot-Learning/LIBERO)** | 1821 ⭐ | 终身知识迁移 | - | 终身机器人学习基准 |
| **[LIBERO-plus](https://github.com/sylvestf/LIBERO-plus)** | 305 ⭐ | VLA鲁棒性 | - | LIBERO扩展，VLA深度鲁棒性分析 |
| **[RoboManipBaselines](https://github.com/isri-aist/RoboManipBaselines)** | 369 ⭐ | 模仿学习 | - | 多种模仿学习方法统一框架 |
| **[SoftGym](https://github.com/Xingyu-Lin/softgym)** | 339 ⭐ | 可变形物体 | - | 布料/绳索/液体等柔性物体 |
| **[FluidLab](https://github.com/zhouxian/FluidLab)** | 243 ⭐ | 流体操作 | - | ICLR'23，可微分流体仿真 |
| **[CausalWorld](https://github.com/rr-learning/CausalWorld)** | 242 ⭐ | 因果结构 | - | 因果推理与迁移学习 |
| **[GarmentLab](https://github.com/GarmentLab/GarmentLab)** | 161 ⭐ | 服装操作 | - | 统一服装仿真与基准 |
| **[bigym](https://github.com/NeuracoreAI/bigym)** | 221 ⭐ | 移动双臂 | - | Demo驱动移动双操作 |
| **[mshab](https://github.com/arth-shukla/mshab)** | 190 ⭐ | 家庭重排 | - | 低级操作家庭重排任务 |

### 2. 长程任务 (Long-Horizon)

| 基准 | 星标 | 核心能力 | 备注 |
|------|------|---------|------|
| **[CALVIN](https://github.com/mees/calvin)** | 910 ⭐ | 语言条件长程操作 | 多步骤组合，语言指令 |
| **[BEHAVIOR-1K](https://github.com/StanfordVL/BEHAVIOR-1K)** | 1457 ⭐ | 1000种室内活动 | 日常复杂任务，多步骤推理 |
| **[myGym](https://github.com/incognite-lab/myGym)** | 53 ⭐ | 无代码长程任务生成 | 自动组合基本动作为复杂流程 |
| **[cap-x](https://github.com/capgym/cap-x)** | 480 ⭐ | Coding Agent操作 | 用代码生成策略的机器人操作基准 |

### 3. 多智能体/协作 (Multi-Agent / Collaboration)

| 基准 | 星标 | 核心能力 | 备注 |
|------|------|---------|------|
| **[RoboTwin](https://github.com/RoboTwin-Platform/RoboTwin)** | 2299 ⭐ | 双臂数字孪生 | 双臂操作+数字孪生仿真 |
| **[VMAS](https://github.com/proroklab/VectorizedMultiAgentSimulator)** | 565 ⭐ | 多智能体RL | PyTorch向量2D物理，连续控制 |
| **[PARTNR](https://github.com/facebookresearch/partnr-planner)** | 368 ⭐ | 人机协作规划 | Meta，Habitat仿真，LPM规划 |
| **multiagent_mujoco** | 371 ⭐ | 连续多智能体控制 | MuJoCo多智能体基准 |

### 4. 跨本体/统一平台 (Cross-Embodiment / Unified)

| 基准 | 星标 | 核心能力 | 备注 |
|------|------|---------|------|
| **[RoboVerse](https://github.com/RoboVerseOrg/RoboVerse)** | 1737 ⭐ | 统一平台+数据集 | 可扩展、可泛化机器人学习 |
| **[VLA-Eval-Harness](https://github.com/allenai/vla-evaluation-harness)** | 280 ⭐ | VLA统一评估 | AllenAI，任意VLA在任意基准上评估 |
| **[LW-BenchHub](https://github.com/LightwheelAI/LW-BenchHub)** | 146 ⭐ | 统一基准中心 | Isaac Lab-Arena，268任务 |

### 5. 特殊领域 (Specialized)

| 基准 | 星标 | 核心能力 | 备注 |
|------|------|---------|------|
| **[EvoGym](https://github.com/EvolutionGym/evogym)** | 252 ⭐ | 软体机器人设计 | NeurIPS'21，协同优化设计与控制 |
| **[InternManip](https://github.com/InternRobotics/InternManip)** | 171 ⭐ | All-in-One操作套件 | 多种数据集和基准统一训练评估 |

## 按仿真器分类

| 仿真器 | 代表性基准 |
|--------|-----------|
| **MuJoCo** | [robosuite](https://github.com/ARISE-Initiative/robosuite), [MetaWorld](https://github.com/Farama-Foundation/Metaworld), multiagent_mujoco |
| **[SAPIEN](https://github.com/haosulab/SAPIEN)** | [ManiSkill](https://github.com/haosulab/ManiSkill) |
| **Isaac Sim/Lab** | [LW-BenchHub](https://github.com/LightwheelAI/LW-BenchHub) |
| **[Habitat](https://github.com/facebookresearch/habitat-sim)** | [PARTNR](https://github.com/facebookresearch/partnr-planner) |
| **[Genesis](https://github.com/Genesis-Embodied-AI/Genesis)** | - (新兴，未来可能集成) |
| **自研** | [RoboVerse](https://github.com/RoboVerseOrg/RoboVerse), [RoboTwin](https://github.com/RoboTwin-Platform/RoboTwin), [SoftGym](https://github.com/Xingyu-Lin/softgym), [FluidLab](https://github.com/zhouxian/FluidLab) |

## 评估维度演进

```
第一代: 成功率 (Success Rate)
    ↓
第二代: 样本效率 + 泛化 (Sample Efficiency, Generalization)
    ↓
第三代: 语言指令遵循 (Language-Conditioned)
    ↓
第四代: 长程组合 + 错误恢复 (Long-Horizon, Error Recovery)
    ↓
第五代: 跨本体迁移 + 终身学习 (Cross-Embodiment, Lifelong)
    ↓
第六代: 因果推理 + 协作规划 (Causal, Collaborative)
```

## 核心问题

1. **基准过拟合**: 模型在基准上表现好，但在真实世界失效。[BEHAVIOR-1K](https://github.com/StanfordVL/BEHAVIOR-1K) 试图用真实场景缓解，但仿真-真实鸿沟仍在。
2. **评估指标单一**: 大多数基准只看最终成功率，忽略中间过程的推理质量、恢复能力和时间效率。
3. **任务设计偏差**: 基准任务是否反映了真实世界的组合复杂性？还是只是简单任务的堆砌？
4. **跨基准可比性**: 不同仿真器、不同动作空间、不同观测空间，如何公平比较不同方法？
5. **VLA 评估困境**: VLA 模型输出高频连续动作，传统 RL 基准的离散动作评估框架不再适用。

## 与具身大脑的关系

- 当前基准大多测试**短视程反射**能力（单步/短步操作）
- 具身大脑需要的基准：**长程记忆保持、反事实推理、错误恢复、情感交互、终身学习**——这些在当前基准中严重缺失
- [LIBERO](https://github.com/Lifelong-Robot-Learning/LIBERO) 和 [BEHAVIOR-1K](https://github.com/StanfordVL/BEHAVIOR-1K) 是向这个方向迈进的重要尝试

## 与其他概念的关系

- [embodied-ai-research-landscape](embodied-ai-research-landscape.md) — 基准是研究方向的指南针
- [task-planning-and-skill-composition](task-planning-and-skill-composition.md) — 长程基准如 [CALVIN](https://github.com/mees/calvin)、[BEHAVIOR-1K](https://github.com/StanfordVL/BEHAVIOR-1K)已归入任务规划方向
- [cross-embodiment](cross-embodiment.md) — 跨本体基准如 [Open X-Embodiment](https://github.com/google-deepmind/open_x_embodiment)、[RoboVerse](https://github.com/RoboVerseOrg/RoboVerse)
- [sim-to-real](sim-to-real.md) — 基准的仿真器选择直接影响 sim2real 难度
- [vla-vision-language-action](vla-vision-language-action.md) — VLA 需要新的评估范式和指标
- [embodied-brain](embodied-brain.md) — 下一代基准需要测试认知能力而非仅动作成功率

## 参见

- [maniskill](../entities/maniskill.md) — GPU并行操作技能基准
- [robosuite](../entities/robosuite.md) — 模块化操作仿真框架
- [metaworld](../entities/metaworld.md) — 多任务元强化学习基准
- [roboverse](../entities/roboverse.md) — 统一可扩展机器人学习平台

## 最新研究动态 (2026-05-04 ~ 2026-05-11)

本周追踪到 2 篇基准测试/评估相关新论文：

- **TAVIS: A Benchmark for Egocentric Active Vision and Anticipatory Gaze in Imitation Learning** (Giacomo Spigler, 2026-05-08) — 主动视觉模仿学习基准，提供头部/手部双套任务、GALT 预期目光度量指标，基于 IsaacLab 和 GR1T2/Reachy2。[arXiv:2605.07943](https://arxiv.org/abs/2605.07943)
- **Bi3: A Biplatform, Bicultural, Biperson Dataset for Social Robot Navigation** (Andrew Stratton et al., 2026-05-07) — 社交机器人导航数据集，特点是双平台、双文化、双人种交互，补充了密集人群导航场景的数据稀缺。[arXiv:2605.06863](https://arxiv.org/abs/2605.06863)