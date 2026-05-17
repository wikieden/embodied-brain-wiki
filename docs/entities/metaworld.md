---
title: MetaWorld
created: 2026-05-11
updated: 2026-05-11
type: entity
tags: [benchmark, robotics, reinforcement-learning, multi-task, open-source]
sources: [raw/articles/github-embodied-ai-projects-2026-05-11.md]
---

# MetaWorld

> 面向多任务和元强化学习的机器人仿真环境集合。Farama Foundation 维护。

## 关键数据

- **GitHub**: https://github.com/Farama-Foundation/Metaworld
- **星标**: 1814 ⭐
- **主要语言**: Python
- **最近更新**: 2026-05-09 (活跃)
- **维护方**: Farama Foundation (Gymnasium 生态)

## 核心特点

- **50 个操作任务**: 包括 MT1、MT10、MT50 集，从简单到复杂
- **元学习专为**: 支持元 RL (meta-RL)、多任务 RL 研究
- **MuJoCo 引擎**: 基于 MuJoCo 的 Sawyer 机械臂仿真
- **标准化接口**: 符合 Gymnasium API 规范
- **广泛使用**: 元强化学习论文的标准测试基准

## 任务集分类

| 集合 | 任务数 | 目的 |
|------|--------|------|
| MT1 | 1 | 单任务训练基线 |
| MT10 | 10 | 少量多任务 |
| MT50 | 50 | 大规模多任务泛化 |
| ML1/ML10/ML45 | 1/10/45 | 元学习对应集 |

## 与其他实体的关系

- 基于 [mujoco](mujoco.md) 物理引擎
- 属于 Farama Foundation 生态，与 [gymnasium](gymnasium.md) 兼容
- 与 [maniskill](maniskill.md)、[robosuite](robosuite.md) 一起构成了三大主流操作基准
- 常被用于测试 [reinforcement-learning-robotics](../concepts/reinforcement-learning-robotics.md) 方法

## 参见

- [embodied-benchmarks](../concepts/embodied-benchmarks.md) — 具身智能基准总览
- [robosuite](robosuite.md) — 另一大主流操作基准
- [maniskill](maniskill.md) — 另一大主流操作基准
