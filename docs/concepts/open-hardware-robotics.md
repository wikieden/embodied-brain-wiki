---
title: 开源硬件与低成本平台
created: 2026-05-11
updated: 2026-05-11
type: concept
tags: [hardware, open-source, embodiment, low-cost, robotics]
sources: [raw/articles/github-embodied-ai-projects-2026-05-11.md]
confidence: high
---

# 开源硬件与低成本平台

降低具身智能研究的硬件门槛。当商业人形机器人价格在数万到数十万美元时，开源硬件让学术界和爱好者能以 <$3,000 的成本在实物上验证算法。

## 主流开源硬件平台

| 平台 | 价格 | 特点 | Stars |
|------|-------|-------|-------|
| [OpenArm](https://github.com/OpenArm/) | — | 全开源人形手臂 | 2.4k |
| [Roboto Origin](https://github.com/Roboparty/roboto_origin) | 手搓级 | 全开源 DIY 人形机器人 | 1.7k |
| [Zeroth-Bot](https://github.com/zeroth-robotics/zeroth-bot) | 3D 打印 | Sim2Real + RL 优化的低成本人形 | 763 |
| [HOPEJr](https://github.com/TheRobotStudio/HOPEJr) | — | 开源灵巧手人形 | 793 |
| [Asimov v0/v1](https://github.com/asimovinc) | — | 开源人形机器人 | 730/612 |
| [Poppy Humanoid](https://github.com/poppy-project/poppy-humanoid) | — | 3D 打印研究/教育用人形 | 898 |
| [Unitree G1](https://www.unitree.com) | $13,500 | 商业级性价比之王 | — |
| [Berkeley Humanoid](https://github.com/berkeleyhumanoid) | — | 加州大学开源人形 | — |

## 关键技术挑战

### 成本

开源硬件的核心竞争力在于成本。[Zeroth-Bot](https://github.com/zeroth-robotics/zeroth-bot) 使用 3D 打印和商用执行器把成本压到极低，但动力学性能和耐久性仍是挑战。

### 灵巧手 (Dexterous Hand)

精细操作是人形机器人最难的部分之一。[HOPEJr](https://github.com/TheRobotStudio/HOPEJr) 尝试用低成本执行器实现多指灵巧手，但力控制精度和触觉反馈仍与商业产品有距离。

### 开放标准

URDF / MJCF 描述的统一与兼容性仍是问题。[robot-descriptions.py](https://github.com/robot-descriptions/robot_descriptions.py) 正在尝试建立标准化的机器人描述汇总。

### 通用接口

如何让同一策略跑在不同硬件上？[LeRobot](https://github.com/huggingface/lerobot) 提供了一层抽象，但硬件驱动层仍需要针对每款机器人单独实现。

## 核心问题

1. **<$3,000 的完整人形**：如何在极低成本下构建可操作的人形机器人？
2. **灵巧手**：低成本执行器如何实现精细操作？
3. **开放标准**：URDF/MJCF 描述的统一与兼容性如何促进？
4. **通用接口**：同一策略如何跑在不同硬件上？

## 可研究细分

- 设计优化（拘架结构、重量分布、性价比）
- 执行器选型与力控制
- 低成本感知传感器
- 开放控制框架与驱动

## 关系

- [unitree](../entities/unitree.md) — 商业级低成本人形
- [lerobot](../entities/lerobot.md) — 硬件部署框架
- [nvidia-isaac](../entities/nvidia-isaac.md) — 仿真训练与部署
- [sim-to-real](sim-to-real.md) — 仿真到真实迁移是开源硬件的核心挑战
- [humanoid-robot](humanoid-robot.md) — 人形机器人概览
