---
title: UMI
created: 2026-05-11
updated: 2026-05-11
type: entity
tags: [project, open-source, teleoperation, manipulation]
sources: [raw/articles/soul2humanoid-report-teleoperation.md]
confidence: high
---

# UMI (Universal Manipulation Interface)

[GitHub](https://github.com/real-stanford/universal_manipulation_interface) · 论文: *Universal Manipulation Interface: In-The-Wild Robot Teaching Without In-The-Wild Robots*

Stanford 开源的通用操作接口，通过手持式夹具实现了不依赖机器人本体的数据采集。

## 核心设计

- **手持式夹具**：操作员手持简单的机械夹具进行操作，夹具内置摄像头和传感器
- **本体解耦**：数据采集与机器人本体完全解耦，可以用任意机器人本体执行任务
- **中心围绕采集**：在任意环境中采集，不需要专门的机器人或控制环境
- **视觉为主**：主要通过视觉观测来记录操作轨迹

## 技术细节

### 硬件设计

- **手持夹具**：3D 打印的轻量级夹具，配备 GoPro 风格的广角摄像头
- **视觉追踪**：通过夹具上的摄像头记录人手的精细操作轨迹
- **传感器集成**：包括 IMU、力传感器等，记录操作过程中的物理信息
- **低成本**：整个采集套件成本远低于传统的同构遥操作系统

### 策略学习

- **Diffusion Policy**：采用去噪扩散模型表示动作策略，支持多模态动作分布
- **视觉模态引导**：利用预训练的视觉模型提取视觉特征，提高策略的泛化能力
- **在线推理**：支持实时的视觉反馈，适应环境变化

## 影响与应用

- **任意本体**：因为采集与执行解耦，可以让不同的机器人学习同一套技能
- **跨场景**：在多个不同的环境中采集数据，提高泛化性
- **数据增强**：结合仿真扩展（如 MimicGen）可以生成大规模训练数据
- **开源生态**：被 Hugging Face LeRobot 等框架支持

## 关系

- 与 [teleoperation-and-video-policies](../concepts/teleoperation-and-video-policies.md) 相关：代表手持式/视觉遥操作范式
- 与 [imitation-learning-robotics](../concepts/imitation-learning-robotics.md) 相关：是视频模仿学习的重要开源工具
- 与 [data-flywheel-robotics](../concepts/data-flywheel-robotics.md) 相关：本体解耦的数据采集方式有助于加速数据飞轮转动
