---
title: Reinforcement Learning in Robotics
created: 2026-05-11
updated: 2026-05-11
type: concept
tags: [reinforcement-learning, training, robotics, sim-to-real]
sources: [raw/articles/soul2humanoid-report-physical-intelligence.md, raw/articles/soul2humanoid-report-tesla-optimus.md, raw/articles/soul2humanoid-report-unitree.md]
confidence: high
---

# Reinforcement Learning in Robotics

通过试错和奖励反馈优化机器人策略。

## 应用场景

| 场景 | RL 角色 | 模仿学习的局限 |
|------|----------|----------------|
| 步态优化 | 仿真中探索数百万种步态，找到能量最优解 | 人类演示无法覆盖所有地形 |
| 力控制 | 通过试错发现抓取鸡蛋的最优力曲线 | 人类演示力信号难以精确采集 |
| 高动态运动 | 学习功夫、奔跑、舞蹈 | 人类演示者不能安全展示危险动作 |
| 摔倒恢复 | 虚拟中无数次摔倒后学习恢复 | 真实机器人摔倒成本过高 |

## 关键框架

- **[Isaac Lab](https://github.com/isaac-sim/IsaacLab)**：[nvidia-isaac](../entities/nvidia-isaac.md) GPU 并行 RL 训练，单张 GPU 数百个智能体
- **[MuJoCo](https://github.com/google-deepmind/mujoco)**：开源控制系统仿真，学术界标准
- **[robomimic](https://github.com/ARISE-Initiative/robomimic)**：Stanford 开源模仿学习框架
- **[RL-Games](https://github.com/Denys88/rl_games)**：高性能 RL 框架，与 Isaac Lab 集成

## 企业实践

- [physical-intelligence](../entities/physical-intelligence.md)：π*0.6 / Recap 首个在线 RL 训练的通用策略；RLT 从 VLA 中提取 RL Token 实现高效 RL
- [tesla-optimus](../entities/tesla-optimus.md)：步态优化、力控制、高动态运动均在 Neural World Simulator 中用 RL 训练
- [unitree](../entities/unitree.md)：春晚《秧BOT》的高动态舞蹈由 RL 训练
- [boston-dynamics](../entities/boston-dynamics.md)：Spot locomotion 引入 RL 策略网络，湿滑地形跌倒率显著下降

## Sim2Real 闭环

RL 几乎专门在仿真中训练，然后通过 [sim-to-real](sim-to-real.md) 迁移。

## 关系

- 仿真训练：[sim-to-real](sim-to-real.md)
- 行为克隆：与 [imitation-learning-robotics](imitation-learning-robotics.md) 常组合使用
- 数据飞轮：[data-flywheel-robotics](data-flywheel-robotics.md)
