---
title: ManiSkill
created: 2026-05-11
updated: 2026-05-11
type: entity
tags: [benchmark, robotics, manipulation, open-source]
sources: [raw/articles/github-embodied-ai-projects-2026-05-11.md]
---

# ManiSkill

> SAPIEN Manipulation Skill Framework，由 UC San Diego haosulab 开发。一个开源的 GPU 并行化机器人仿真器与操作技能基准。NeurIPS 2021 数据集与基准轨道。

## 关键数据

- **GitHub**: https://github.com/haosulab/ManiSkill
- **星标**: 2860 ⭐
- **主要语言**: Python
- **最近更新**: 2026-05-09 (活跃)
- **作者**: haosulab @ UC San Diego

## 核心特点

- **GPU 并行化**: 支持大规模并行仿真，显著加速 RL 训练
- **SAPIEN 引擎**: 基于 SAPIEN 仿真器，支持精细操作和物理模拟
- **通用操作技能**: 覆盖多种操作任务，包括抓取、推、旋转等
- **ManiSkill 2.0/3.0**: 持续迭代，增加更多任务和更好的仿真质量

## 与其他实体的关系

- 基于 [sapien](sapien.md) 仿真引擎
- 与 [robosuite](robosuite.md) 构成了操作技能基准的两大主流框架
- 被大量 VLA 研究用于评估
- 导入到 [lerobot](lerobot.md) 生态作为训练环境

## 参见

- [embodied-benchmarks](../concepts/embodied-benchmarks.md) — 具身智能基准总览
- [sapien](sapien.md) — SAPIEN 仿真引擎
- [robosuite](robosuite.md) — 另一大主流操作基准
