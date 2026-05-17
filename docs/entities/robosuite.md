---
title: robosuite
created: 2026-05-11
updated: 2026-05-11
type: entity
tags: [benchmark, robotics, manipulation, open-source]
sources: [raw/articles/github-embodied-ai-projects-2026-05-11.md]
---

# robosuite

> 由 Stanford ARISE Initiative 开发的模块化仿真框架与机器人学习基准。支持环境的组合配置、控制器模块化和多种任务。

## 关键数据

- **GitHub**: https://github.com/ARISE-Initiative/robosuite
- **星标**: 2405 ⭐
- **主要语言**: Python
- **最近更新**: 2026-05-09 (活跃)
- **开发者**: Stanford ARISE Initiative

## 核心特点

- **模块化设计**: 可自由组合机器人、控制器、环境和任务
- **MuJoCo 引擎**: 基于 MuJoCo 物理引擎
- **丰富的控制器支持**: OSC (Operational Space Control)、JOINT_VELOCITY、JOINT_POSITION 等
- **商业级机器人支持**: Panda, Sawyer, Kinova, UR5e 等
- **被广泛使用**: 许多模仿学习和 RL 研究的基础环境

## 与其他实体的关系

- 基于 [mujoco](mujoco.md) 物理引擎
- 与 [maniskill](maniskill.md) 构成了操作技能基准的两大主流框架
- 是 [robomimic](robomimic.md) 等模仿学习框架的推荐环境
- 被用于 [open-x-embodiment](open-x-embodiment.md) 数据集的部分环境

## 参见

- [embodied-benchmarks](../concepts/embodied-benchmarks.md) — 具身智能基准总览
- [maniskill](maniskill.md) — 另一大主流操作基准
- [mujoco](mujoco.md) — MuJoCo 物理引擎
