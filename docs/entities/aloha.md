---
title: ALOHA
created: 2026-05-11
updated: 2026-05-11
type: entity
tags: [project, open-source, teleoperation, imitation-learning]
sources: [raw/articles/soul2humanoid-report-teleoperation.md]
confidence: high
---

# ALOHA

[GitHub](https://github.com/MarkFzp/mobile-aloha) · 论文: *Learning Fine-Grained Bimanual Manipulation with Low-Cost Hardware*

Stanford 开源双臂遥操作系统，以极低成本（< $5,000）实现了精细操作的数据采集。

## 核心设计

- **同构遥操作**：主臂（操作员操作）与从臂（机器人）结构完全一致，直接映射动作
- **双臂协同**：支持需要双手配合的复杂操作（如撤链、打结、操作工具）
- **低成本硬件**：基于工业机械臂改装，总成本控制在 5,000 美元以内
- **高精度力控**：支持精细力/位置控制的操作，如插入电缆、擀牛油果

## 技术细节

### 硬件架构

- **主臂**：操作员手持的引导臂，通过直接物理接触输入动作
- **从臂**：复现主臂动作的机器人臂，具有相同的自由度配置
- **摄像头阵列**：多角度摄像头记录操作视角与环境信息
- **力触觉传感**：集成低成本力传感器，支持触觉反馈

### 数据采集与学习

- **ALOHA Dataset**：开源的双臂操作数据集，被广泛用于模仿学习研究
- **动作块（Action Chunking）**：采用 ACT 算法，将连续动作分块处理提高平滑度
- **固定场景采集**：在控制环境中采集数据，确保可重复性

## 影响与衍生

- **Mobile ALOHA**：增加了移动底盘，扩展到移动操作场景
- **ALOHA 2**：硬件升级版，提升了可靠性和精度
- **生态影响**：被 [LeRobot](https://github.com/huggingface/lerobot)、[robomimic](https://github.com/ARISE-Initiative/robomimic) 等开源框架直接支持

## 关系

- 与 [teleoperation-and-video-policies](../concepts/teleoperation-and-video-policies.md) 相关：代表低成本同构遥操作范式
- 与 [imitation-learning-robotics](../concepts/imitation-learning-robotics.md) 相关：是模仿学习领域最重要的开源数据来源之一
- 与 [data-flywheel-robotics](../concepts/data-flywheel-robotics.md) 相关：低成本数据采集是数据飞轮的重要组成部分
