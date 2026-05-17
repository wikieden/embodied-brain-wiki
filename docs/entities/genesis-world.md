---
title: Genesis World
created: 2026-05-11
updated: 2026-05-11
type: entity
tags: [company, open-source, embodiment, world-model]
sources: [raw/articles/github-embodied-ai-projects-2026-05-11.md]
confidence: medium
---

# Genesis World

> 由 [Genesis-Embodied-AI](https://github.com/Genesis-Embodied-AI) 社区开发的生成式物理世界仿真器，支持差分运算、大规模并行与通用机器人学习。目前 [GitHub 28.7k ⭐](https://github.com/Genesis-Embodied-AI/Genesis)，是具身智能领域增长最快的开源仿真器之一。

## 概览

Genesis 定位为"一个生成式世界，用于通用机器人与具身 AI 学习"。其核心特色是将物理仿真、渲染、生成与数据增强统一在一个可差分的框架中。

## 关键特性

- **差分物理引擎**：支持梯度优化，可用于端到端学习
- **多物理后端**：刚体、液体、气体、软体统一仿真
- **GPU 加速**：大规模并行模拟
- **生成式**：可从语言描述生成 3D 场景、物体与任务

## 开放问题

- 与 NVIDIA Isaac / MuJoCo 相比，保真度与稳定性如何？
- 大规模并行的扩展性边界在哪里？
- 差分物理的数值稳定性仍是挑战

## 参见

- [nvidia-isaac](nvidia-isaac.md) — 企业级竞品框架
- [embodied-ai-research-landscape](../concepts/embodied-ai-research-landscape.md) — 具身智能研究方向全景
- [world-model-robotics](../concepts/world-model-robotics.md) — 世界模型
