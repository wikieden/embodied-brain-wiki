---
title: NVIDIA Isaac
created: 2026-05-11
updated: 2026-05-11
type: entity
tags: [company, robotics, sim-to-real, training, inference]
sources: [raw/articles/soul2humanoid-report-nvidia-isaac.md]
confidence: high
---

# NVIDIA Isaac

[官网](https://developer.nvidia.com/isaac) · [X/Twitter](https://x.com/nvidia) · [GitHub](https://github.com/NVIDIA-Omniverse)

NVIDIA 的具身智能基础设施平台，**卖铲人定位**

## 平台架构

| 层级 | 产品 | 功能 |
|------|------|------|
| 应用层 | GR00T | 人形机器人基础模型参考设计 |
| 训练层 | Isaac Lab | RL + 模仿学习 + Sim2Real |
| 仿真层 | Isaac Sim / Omniverse | 物理仿真 + 传感器模拟 |
| 计算层 | Jetson / DGX / H100 | 边缘推理 + 云端训练 |
| 本体层 | 参考设计 + 合作伙伴 | Figure、1X、Agility、BD 等 |

## 核心组件

- **[Isaac Sim](https://github.com/NVIDIA-Omniverse/IsaacSim)**：基于 Omniverse/USD，GPU 加速，支持数千环境并行
- **[Isaac Lab](https://github.com/isaac-sim/IsaacLab)**：统一 RL/IL 训练框架，兼容 PyTorch / [Hugging Face LeRobot](https://github.com/huggingface/lerobot)
- **Jetson Thor**：2024 年发布，专为机器人设计，集成 Transformer Engine
- **Omniverse Replicator**：程序化生成无限标注合成数据
- **Project GR00T**：Transformer VLA 参考模型

### 技术细节

#### Isaac Sim / Omniverse

- **USD（Universal Scene Description）**：皮克斯开发的场景描述标准，支持复杂场景的精确描述与跨应用共享
- **GPU 并行仿真**：支持数千个环境同时运行，大幅加速 RL 训练
- **传感器模拟**：支持摄像头、LiDAR、力触觉、IMU 等多种传感器的高保真模拟
- **生态系统**：与多家机器人公司（Figure、1X、Apptronik 等）深度集成

#### Isaac Lab

- **统一训练框架**：支持强化学习、模仿学习、Sim2Real 迁移的统一管线
- **LeRobot 兼容**：与 Hugging Face 的 LeRobot 框架无缝对接，支持从仿真到真机的工作流
- **GR00T 集成**：内置了人形机器人的 VLA 参考实现

#### Jetson 边缘计算

- **Jetson Thor**：专为机器人设计，集成 Transformer Engine，支持本地 VLA 推理
- **生态优势**：几乎所有人形机器人都使用 Jetson 系列作为边缘计算平台

## 最新动态（2025-2026）

- **2025 年初**：发布 Isaac Sim 4.5 和 Isaac Lab 2.0，大幅提升仿真保真度和训练速度
- **2025 年中**：Jetson Thor 正式量产，成为多家人形机器人的标准计算平台
- **2025 年底**：发布 Cosmos 世界基础模型，支持视频生成与世界模型，进一步增强合成数据能力
- **2026.01**：宣布 GR00T 项目的新进展，支持更多的人形机器人本体类型
- **生态扩张**：与 [unitree](unitree.md) 、[figure-ai](figure-ai.md) 、[1x-technologies](1x-technologies.md) 等的合作进一步深化

## 竞争格局

- **"卖铲子"定位**：不与任何机器人公司竞争，而是为所有公司提供基础设施
- **GPU 垄断**：AI 训练唯一选择是 NVIDIA GPU，Jetson 是边缘 AI 首选，垄断地位难以动摇
- **仿真竞争**：与开源仿真器（MuJoCo、Genesis、PyBullet）形成竞争，但 Isaac Sim 在 GPU 加速和生态集成上优势明显
- **数据飞轮**：Omniverse Replicator 的合成数据能力与合作伙伴的真实数据反馈形成闭环

## 关键人物

- **Jensen Huang**：NVIDIA CEO，积极推动机器人 AI 生态，多次在演讲中强调 "下一个 AI 波潮是物理 AI"
- **Deepu Talla**：NVIDIA 机器人与边缘计算 VP，负责 Isaac 平台的产品策略与生态合作
- **Dieter Fox**：NVIDIA 机器人研究 VP（前 Washington 大学教授），负责核心算法研究

## 关系

- 与 [figure-ai](figure-ai.md) 、[1x-technologies](1x-technologies.md) 、[unitree](unitree.md) 、[boston-dynamics](boston-dynamics.md) 、[apptronik](apptronik.md) 、[agility-robotics](agility-robotics.md) 均为合作伙伴
- 与开源仿真器（MuJoCo、Genesis、[genesis-world](genesis-world.md)）形成竞争
