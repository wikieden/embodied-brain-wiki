---
title: LeRobot
created: 2026-05-11
updated: 2026-05-11
type: entity
tags: [open-source, model, training, embodiment, company]
sources: [raw/articles/github-embodied-ai-projects-2026-05-11.md]
confidence: high
---

# LeRobot

> 由 [Hugging Face](https://github.com/huggingface) 发起的端到端机器人学习框架，目标是让 AI for Robotics 更易触达。[GitHub 23.9k ⭐](https://github.com/huggingface/lerobot)，是目前机器人学习领域最活跃的开源项目之一。

## 概览

LeRobot 提供从数据采集、训练到部署的全流程工具链，包含预训练模型、仿真环境接口、数据集管理与评估工具。

## 关键特性

- **预训练模型**：Diffusion Policy、ACT、Octo 等经典策略的开源实现
- **数据集**：与 HuggingFace Hub 集成，支持存取机器人数据集
- **仿真支持**：对接 MuJoCo、Isaac Gym 等仿真器
- **硬件支持**：提供实物部署工具链

## 开放问题

- 如何支持更多极端的 VLA 模型 (如 π⁰)？
- 实时控制频率与端侧部署优化
- 跨本体数据管理的标准化

## 参见

- [huggingface](huggingface.md) — 发起组织 (若存在页面)
- [embodied-ai-research-landscape](../concepts/embodied-ai-research-landscape.md) — 具身智能研究方向全景
- [diffusion-policy](diffusion-policy.md) — 其支持的核心策略之一
