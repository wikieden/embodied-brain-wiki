---
title: 数据策略对比
created: 2026-05-11
updated: 2026-05-11
type: comparison
tags: [comparison, training, robotics, data-flywheel]
sources: [raw/articles/soul2humanoid-comparisons.md]
confidence: high
---

# 数据策略对比

11 家具身智能公司的数据来源、规模和飞轮模式对比。

## 数据来源与飞轮

| 公司 | 主要数据来源 | 规模 | 独特策略 | 飞轮强度 |
|------|------------|-------|---------|---------|
| **Figure AI** | BotQ 自主生成 + 真实部署 | 大规模 | BotQ 自主数据生成系统 | 强 |
| **Physical Intelligence** | Open X-Embodiment + DROID + 自采 | 1600万+ 跨本体轨迹 | 跨本体数据融合、人类视频迁移 | 强 |
| **Tesla** | 工厂部署 + FSD 数据迁移 | 数百万辆车 + 数千机器人 | FSD 数据直接复用于机器人 | 极强 |
| **Boston Dynamics** | Spot 2000+ 部署 + 仿真 + 遥操作 | 工业级 | Fleet 数据共享：Spot 数据预训练 Atlas | 中 |
| **1X** | 真实家庭 + Expert 遥操作 + World Model | 增长中 | Expert Mode：人类专家远程遥控生成高质量数据 | 早期 |
| **Unitree** | 仿真(RL) + 动作捕捉 + 遥操作 | 中等 | 开源生态：全球开发者贡献 | 弱 |
| **Agility** | 真实部署 + 仿真 + 遥操作 | 小规模 | 传统控制为主 | 弱 |
| **Apptronik** | 仿真 + VR 遥操作 + Google 合作 | 中等 | 借力 Google：跨本体数据集 | 中 |
| **NVIDIA** | Omniverse 合成数据 + 生态数据 | 无限（合成） | 合成数据工厂：Replicator 程序化生成 | 强 |
| **Enchanted** | 试点现场 + 遥操作 | 小规模 | 场景数据有限 | 弱 |
| **Genesis AI** | 未公开 | 未知 | 未公开 | 未知 |

## 最独特的三大数据策略

1. **Tesla FSD 迁移**：将数百万辆车的驾驶数据（视觉、决策、控制）直接用于人形机器人，任何竞争对手无法复制
2. **1X Expert Mode**：用"专家远程遥控"解决家庭场景数据稀缺问题，避免了 Figure 的 BotQ 那种重资本投入
3. **PI 跨本体数据**：用其他机器人的数据训练自己的策略，实现"数据杠杆"

## 合成数据角色

| 公司 | 合成数据方法 |
|------|------------|
| Tesla | Digital Dreams（Sora-like 视频生成） |
| NVIDIA | Omniverse Replicator（程序化生成标注数据） |
| Physical Intelligence | 世界模型仿真中试错 |
| Figure AI | 仿真 + 真实混合（BotQ 中） |

## 关系

- 数据驱动的核心机制：[data-flywheel-robotics](../concepts/data-flywheel-robotics.md)
- 数据集基础：[google-deepmind](../entities/google-deepmind.md) Open X-Embodiment
- 合成数据工具：[nvidia-isaac](../entities/nvidia-isaac.md) Omniverse Replicator
