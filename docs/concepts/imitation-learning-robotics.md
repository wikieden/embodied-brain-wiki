---
title: Imitation Learning in Robotics
created: 2026-05-11
updated: 2026-05-11
type: concept
tags: [imitation-learning, training, robotics]
sources: [raw/articles/soul2humanoid-report-tesla-optimus.md, raw/articles/soul2humanoid-report-figure-ai.md]
confidence: high
---

# Imitation Learning in Robotics

机器人通过模仿人类演示数据来学习任务。

## Tesla 的三级模仿学习

|| 阶段 | 方法 | 规模 | 时间 |
||------|------|------|------|
|| Stage 1 | 遥操作（动作捕捉 + VR） | 极低 | 2022-2024 |
|| Stage 2 | 第一人称视频（内置 5 摄像头） | 中等 | 2025 中期 |
|| Stage 3 | 互联网视频（YouTube 等） | 无限（理论） | 2025+ |

> "If Optimus can watch YouTube videos and learn to do that thing... you really have task extensibility that is dramatic."
> — Elon Musk

### 模仿学习技术范式

- **经典模仿学习**（Behavioral Cloning）：直接将观测映射到动作，简单高效但易受演示者波动和分布外推影响
- **Diffusion Policy**：将策略建模为去噪扩散过程，可表示多模态动作分布，是 2024-2025 年最重要的突破之一
- **ACT（Action Chunking with Transformers）**：通过 Transformer 预测动作块，提高并行式操作的平滑性和效率
- **VLA（Vision-Language-Action）**：将视觉-语言模型直接输出动作 token，支持自然语言指令和视觉理解，代表如 RT-2、OpenVLA

## 其他公司的模仿学习

- [figure-ai](../entities/figure-ai.md)：~500h 高质量遥操作数据，VLM 自动生成 hindsight 指令
- [physical-intelligence](../entities/physical-intelligence.md)：人类视频到机器人任务的迁移能力在规模上涌现
- [boston-dynamics](../entities/boston-dynamics.md)：人类遥操作（VR/平板）提供高质量种子数据
- [1x-technologies](../entities/1x-technologies.md)：Expert Mode 专家遥控，边做边学
- [robomimic](https://github.com/ARISE-Initiative/robomimic)：Stanford 开源模仿学习框架
- [ACT](https://github.com/tonyzhaozh/act)：Action Chunking with Transformers，遥操作模仿学习里程碑

### 核心数据集与开源框架

- **ALOHA Dataset**：Stanford 开源双臂遥操作数据集，支持精细操作任务的模仿学习，见 [aloha](../entities/aloha.md)
- **Open X-Embodiment**：Google DeepMind 主导的跨本体数据集，被 Physical Intelligence 的 π0 等模型直接使用
- **LeRobot**：Hugging Face 开源机器人学习框架，整合了 ALOHA、Diffusion Policy、ACT 等算法
- **DexCap Dataset**：基于手部动作捕捉的高精度操作数据，支持灵巧手精细操作，见 [dexcap](../entities/dexcap.md)

## 与 RL 的对比

|| | 模仿学习 | 强化学习 |
||--|----------|----------|
|| 数据来源 | 人类演示 | 自主试错 |
|| 学习速度 | 快（直接学习有效行为） | 慢（需要大量探索） |
|| 遭遇的场景 | 受限于演示覆盖范围 | 可以探索未知场景 |
|| 安全性 | 高（不会尝试危险行为） | 低（需要安全约束） |
|| 精度 | 受限于演示精度 | 可以超越人类演示 |

## 关系

- 常与 [reinforcement-learning-robotics](reinforcement-learning-robotics.md) 组合：IL 初始化 + RL 微调
- Tesla 的合成数据"数字梦境"将 IL 与生成式 AI 结合
- 与 [teleoperation-and-video-policies](teleoperation-and-video-policies.md) 相关：遥操作是模仿学习的核心数据来源
- 与 [vla-vision-language-action](vla-vision-language-action.md) 相关：VLA 模型将模仿学习从“动作模仿”推进到“语义理解 + 动作”的新阶段
