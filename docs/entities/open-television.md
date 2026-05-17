---
title: Open-TeleVision
created: 2026-05-11
updated: 2026-05-11
type: entity
tags: [project, open-source, teleoperation, vr]
sources: [raw/articles/soul2humanoid-report-teleoperation.md]
confidence: high
---

# Open-TeleVision

[GitHub](https://github.com/OpenTeleVision/TeleVision) · 论文: *TeleVision: An Open Source Immersive Teleoperation System*

MIT 开源的沉浸式遥操作系统，通过 VR 头显让操作员获得机器人的第一人称视角。

## 核心设计

- **VR 沉浸感**：操作员戴上 VR 头显，以机器人的视角观察环境，增强空间感知
- **立体视觉**：采用串联摄像头方案提供沉浸式的 3D 视觉体验
- **低延迟**：优化了从机器人摄像头到 VR 显示的传输链路，降低操作延迟
- **开源实施**：硬件方案和软件完全开源，支持多种机器人平台

## 技术细节

### 视觉系统

- **双眼摄像头**：模拟人类双眼视觉，提供深度感知
- **宽视场角**：支持大视场角视觉，增强周边环境的感知
- **高刷新率**：优化传输协议支持高刷新率视频流
- **3D 投影**：将平面视频转换为适合 VR 显示的立体内容

### 控制系统

- **手部追踪**：支持手套或手指追踪设备，将人手姿态映射到机器人
- **主动约束**：支持通过主动约束管线直接控制关节力矤
- **视觉反馈环**：实时的视觉+力触觉反馈，提供沉浸式操作体验
- **安全机制**：包含力限制和紧急停机，确保操作安全

## 影响与应用

- **研究工具**：被多个研究机构用于机器人操作研究
- **数据采集**：支持高质量的人类演示数据采集
- **远程操作**：支持远程的机器人控制和协助
- **其他系统对比**：相比 ALOHA 的同构遥操作，提供了更高的沉浸感和更广泛的适用性

## 关系

- 与 [teleoperation-and-video-policies](../concepts/teleoperation-and-video-policies.md) 相关：代表 VR/沉浸式遥操作范式
- 与 [imitation-learning-robotics](../concepts/imitation-learning-robotics.md) 相关：为模仿学习提供高质量的人类演示数据
- 与 [data-flywheel-robotics](../concepts/data-flywheel-robotics.md) 相关：沉浸式遥操作可以提高数据采集的质量和效率
