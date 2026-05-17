---
title: 可微分机器人学与基础工具
created: 2026-05-11
updated: 2026-05-11
type: concept
tags: [differentiable, tool, robotics, optimization, geometry]
sources: [raw/articles/github-embodied-ai-projects-2026-05-11.md]
confidence: high
---

# 可微分机器人学与基础工具

让物理、几何、运动学都可微分，支持端到端梯度优化。可微分机器人学是连接传统机器人学与深度学习的桥梁，让策略网络的梯度直接流经物理引擎。

## 核心工具

| 工具 | 功能 | Stars |
|------|------|-------|
| [PyPose](https://github.com/pypose/pypose) | 流形上的可微分机器人学库，支持 SE(3)、SO(3) 等权李群 | 1.5k |
| [NVIDIA Warp](https://github.com/NVIDIA/warp) | GPU 加速可微分仿真、稀疏运算、机器人学习 | 6.6k |
| [robot-descriptions.py](https://github.com/robot-descriptions/robot_descriptions.py) | 标准化 URDF/MJCF 机器人描述汇总 | 1.5k |
| [Genesis](https://github.com/Genesis-Embodied-AI/Genesis) | 可差分物理引擎（也归类为仿真器） | 28.7k |
| [MuJoCo](https://github.com/google-deepmind/mujoco) | 部分支持可差分运算 | — |

## 关键技术维度

### 流形优化 (Manifold Optimization)

旋转和姿态不是欧氏空间中的向量，而是权李群 (Lie Group) 上的元素。直接用标准梯度下降会破坏正交性。[PyPose](https://github.com/pypose/pypose) 提供了流形上的自动微分机制。

### 可差分运动学

正向运动学 (FK) 已经可差分，但逆向运动学 (IK) 的梯度回传仍是活跃研究方向。

### 可差分碰撞检测

碰撞检测是个离散事件（碰/不碰），梯度在碰撞界面上不连续。[NVIDIA Warp](https://github.com/NVIDIA/warp) 使用稀疏运算和影子体函数 (SDF) 来实现平滑的碰撞检测梯度。

### 可差分接触力解算

接触力解算是一个不平滑的线性补丁问题 (LCP)。如何让 LCP 的解对参数可微分，是 Genesis 等引擎的核心挑战。

## 核心问题

1. **梯度流经物理引擎**：如何让碰撞检测、接触力解算都可微分？
2. **流形优化**：旋转、姿态在权李群上的优化如何自动化？
3. **数值稳定性**：可差分物理引擎的梯度为什么容易数值爆炸？
4. **计算效率**：可微分运算的计算开销如何降低？

## 可研究细分

- 差分几何与权李群优化
- 可微分运动学 (IK 梯度回传)
- 平滑碰撞检测与接触力模型
- 梯度优化框架的稳定性与性能

## 关系

- [genesis-world](../entities/genesis-world.md) — 可差分物理引擎的实践
- [physics-simulators](physics-simulators.md) — 仿真器与数字孪生
- [nvidia-isaac](../entities/nvidia-isaac.md) — Warp 等可微分工具
- [open-hardware-robotics](open-hardware-robotics.md) — 开源硬件的标准化描述
