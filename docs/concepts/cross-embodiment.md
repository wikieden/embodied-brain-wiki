---
title: Cross-Embodiment Generalization
created: 2026-05-11
updated: 2026-05-11
type: concept
tags: [model, robotics, generalization]
sources: [raw/articles/soul2humanoid-report-physical-intelligence.md, raw/articles/soul2humanoid-report-google-deepmind.md]
confidence: high
---

# Cross-Embodiment Generalization

同一策略能够适配不同形态（单臂、双臂、移动底盘、人形）机器人的能力。

## 核心思想

机器人领域缺乏类似 ImageNet 的大规模预训练数据集。通过**跨本体数据融合**，用一个机器人的数据训练能控制另一个机器人。

## 关键进展

- **[Open X-Embodiment](https://github.com/google-deepmind/open_x_embodiment)**（2023.10）：[google-deepmind](../entities/google-deepmind.md) 联合 20+ 研究机构发布最大跨本体数据集，22 种形态、1600万+ 轨迹
- **RT-X**：在未见过的机器人上成功率比单一本体训练高 50%
- **[π0](https://github.com/Physical-Intelligence/openpi)**（2024.10）：[physical-intelligence](../entities/physical-intelligence.md) 同时控制 8 种截然不同的机器人形态
- **π0.7**（2026.04）：零样本迁移到从未见过的机器人，如将 Bi-ARX 折叠技能迁移到 UR5e 双臂

## 技术要点

- **统一动作空间**：通过规范化表示使同一策略适配不同 DoF
- **多模态提示**：提供机器人形态标签，让模型知道"当前在控制哪种机器人"
- **基于网络的适配**：策略网络内部自动适配不同输入/输出维度

## 意义

跨本体是解决机器人数据稀缺问题的**关键杠杆**——用其他机器人的数据训练自己的策略。

## 关系

- 数据基础：[google-deepmind](../entities/google-deepmind.md) Open X-Embodiment
- 最佳实践：[physical-intelligence](../entities/physical-intelligence.md) π0 / π0.7
- 与 [vla-vision-language-action](vla-vision-language-action.md) 紧密相关：VLA 是实现跨本体的主要架构
