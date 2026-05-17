---
title: DexCap
created: 2026-05-11
updated: 2026-05-11
type: entity
tags: [project, open-source, teleoperation, hand-tracking]
sources: [raw/articles/soul2humanoid-report-teleoperation.md]
confidence: high
---

# DexCap

[GitHub](https://github.com/jlwu002/DexCap) · 论文: *DexCap: Scalable and Portable Hand Motion Capture for Human-Robot Skill Transfer*

Columbia / Stanford 开发的手部动作捕捉系统，通过穿戴设备实现人手精细操作到机器人灵巧手的技能迁移。

## 核心设计

- **手部动作捕捉**：通过穿戴在手背的徽型相机阵列捕捉人手的精细动作
- **可移动性**：整个系统轻便可移动，可在任意环境中使用
- **可扩展性**：支持长时间的数据采集，适合大规模训练
- **灵巧手对齐**：专注于人手精细操作到机器人灵巧手的技能迁移

## 技术细节

### 穿戴硬件

- **徽型相机**：多个小型摄像头安装在手背，从多角度捕捉手部动作
- **手指追踪**：支持精细的手指姿态估计，捕捉细微的操作动作
- **IMU 传感器**：记录手部加速度和角度，补充视觉信息
- **轻量设计**：整个穿戴套件轻便，不影响人的自然操作

### 数据处理

- **三维手部重建**：从多视角视频中重建三维手部罔架
- **动作分解**：将复杂操作分解为基本动作单元
- **技能对齐**：将人手动作映射到机器人灵巧手的关节空间
- **时序建模**：采用 Transformer 或 Diffusion 模型学习动作序列

## 影响与应用

- **灵巧操作**：专门用于需要精细手部动作的任务（如插入插头、操作工具、编织）
- **人形机器人**：支持人形机器人灵巧手的数据采集
- **可持续采集**：可以进行长时间的连续数据采集
- **数据集贡献**：支持构建高质量的灵巧操作数据集

## 关系

- 与 [teleoperation-and-video-policies](../concepts/teleoperation-and-video-policies.md) 相关：代表动作捕捉/穿戴式遥操作范式
- 与 [imitation-learning-robotics](../concepts/imitation-learning-robotics.md) 相关：为灵巧操作的模仿学习提供高精度数据
- 与 [data-flywheel-robotics](../concepts/data-flywheel-robotics.md) 相关：可移动的数据采集方案支持多场景的数据飞轮运转
