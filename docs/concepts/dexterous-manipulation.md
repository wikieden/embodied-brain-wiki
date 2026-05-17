---
title: Dexterous Manipulation and Tactile Sensing
created: 2026-05-11
updated: 2026-05-11
type: concept
tags: [dexterous-manipulation, tactile-sensing, multi-finger-hand, contact-rich, manipulation]
sources: []
confidence: high
---

# 灵巧操作与触觉感知 (Dexterous Manipulation & Tactile Sensing)

> 人形机器人的"最后一公里"。双足让机器人走到目标，但灵巧手让它真正与世界交互。灵巧操作研究多指手部的运动控制与触觉反馈，触觉感知则赋予机器人"接触世界"的能力。

## 为什么灵巧操作至关重要

人类日常任务中约 **70%** 依赖手部操作。开门、打火机、撕开零食袋、擀起杯子——这些任务需要多指协调、接触力控制和精细力觉反馈。与简单的平夹爪不同，灵巧手可以：

- 通过多指协调实现稳定抓取不规则物体
- 利用控制接触力避免挤碎脆弱物体
- 在视觉受阻时通过触觉完成闭环操作
- 执行精细操作（插插头、系鞋带、拉链子）

## 主流灵巧手平台对比

| 灵巧手 | 手指数 | DoF | 特点 | 定位 |
|---------|--------|-----|------|------|
| **Shadow Hand** | 5 | 20 | 伽马线传动，最接近人手，价格高昂 | 研究/展示 |
| **Allegro Hand** | 4 | 16 | 直驱电机，结构紧凑，商业化程度高 | 研究/产业 |
| **LEAP Hand** (Stanford) | 4 | 16 | 低成本、高效率电机，专为学习优化 | 开源/教育 |
| **Tesla Optimus Hand** | 5 | ~22 | 视觉+触觉传感器集成，与 FSD 网络融合 | 自研/工业 |
| **Figure AI Hand** | 5 | 未公开 | 与 Helix VLA 协同设计，商业级可靠性 | 自研/商业 |
| **Schunk SVH** | 5 | 20 | 工业级可靠性，已在工厂部署 | 工业 |

> 当前开源灵巧手领域的一大趋势是：从高成本的定制硬件（Shadow）向低成本、可复制的开源设计（LEAP Hand、RAPID Hand）迁移。

## 触觉传感器技术

视觉只能告诉机器人"物体在哪里"，触觉则能告诉它"我如何与物体交互"。

### 视觉触觉传感器 (Vision-Based Tactile)

| 传感器 | 原理 | 解析度 | 开源状态 |
|--------|------|--------|----------|
| **GelSight** (MIT) | 软胶+LED+相机拍摄表面变形 | 高 | [SDK 开源](https://github.com/gelsightinc/gsrobotics) (185 ⭐) |
| **DIGIT** (Meta) | 拍摄指尖胶膛变形 | 中 | [设计文件开源](https://github.com/facebookresearch/digit-design) (209 ⭐) |
| **DIGIT 360** (Meta) | 全向视角触觉传感 | 高 | 商业产品 |
| **Sparsh** (Meta) | 多模态触觉编码器 | — | [GitHub](https://github.com/facebookresearch/sparsh-multisensory-touch) (34 ⭐) |

### 力/矛感知 (Force/Torque Sensing)

- **手腕力矛传感器 (Wrist F/T Sensor)**：测量整个手掌与环境的交互力，用于控制抓取力度和碰撞检测
- **关节力矛传感器**：提供手指各关节的力馈，实现精细的力控制
- **本体感受 (Proprioception)**：电机电流、编码器反馈提供的低成本力估计

## 学习范式

### 1. 仿照学习 (Imitation Learning)

从人类示范中学习灵巧操作策略。

| 方法 | 核心思想 | 代表项目 |
|------|---------|---------|
| **Behavioral Cloning** | 直接回归从观测到关节力矩 | [hand_dapg](https://github.com/aravindr93/hand_dapg) (316 ⭐) |
| **Diffusion Policy** | 用扩散模型表达多模态动作分布 | 见 [flow-matching](flow-matching.md) |
| **DexUMI** | 将人手作为通用操作界面 | [DexUMI](https://github.com/real-stanford/DexUMI) |
| **Video-to-Policy** | 从人类操作视频提取策略 | [MAPLE](https://github.com/algvr/maple) (32 ⭐) |

### 2. 强化学习 (Reinforcement Learning)

在仿真中通过试错学习灵巧操作。

- **Hand DAPG**：结合深度模仿学习与策略梯度优化，实现24自由度灵巧手的复杂操作
- **Multi-task DiT Policy**：多任务扩散 Transformer 策略，在 Boston Dynamics Atlas 上验证
- **Domain Randomization + RL**：通过大量随机化缩小 sim-to-real gap

### 3. 触觉强化学习 (Tactile-Enhanced Learning)

将触觉信息融入策略学习循环。

- **Tactile Environments**：为 MuJoCo 环境增添视觉+触觉传感器 [tactile_envs](https://github.com/carlosferrazza/tactile_envs) (96 ⭐)
- **FusionSense**：融合视觉、触觉与基础模型常识 [FusionSense](https://github.com/ai4ce/FusionSense) (48 ⭐)
- **LocoTouch**：四足机器人动态运输中的触觉学习 [LocoTouch](https://github.com/linchangyi1/LocoTouch) (58 ⭐)

## 关键开源项目

**策略学习:**
- [hand_dapg](https://github.com/aravindr93/hand_dapg) (316 ⭐) — RSS 2018, 灵巧手操作的深度模仿学习
- [multitask_dit_policy](https://github.com/brysonjones/multitask_dit_policy) (122 ⭐) — 多任务扩散 Transformer 策略
- [DexUMI](https://github.com/real-stanford/DexUMI) (213 ⭐) — 用人手作为通用操作界面

**触觉与感知:**
- [tactile_envs](https://github.com/carlosferrazza/tactile_envs) (96 ⭐) — 配备视觉+触觉的 MuJoCo 环境
- [RAPID-Hand](https://github.com/SYSU-RoboticsLab/RAPID-Hand) (42 ⭐) — 经济型灵巧手平台
- [sparsh-multisensory-touch](https://github.com/facebookresearch/sparsh-multisensory-touch) (34 ⭐) — Meta 多模态触觉编码器

**传感器开源:**
- [digit-design](https://github.com/facebookresearch/digit-design) (209 ⭐) — DIGIT 触觉传感器设计文件
- [gsrobotics](https://github.com/gelsightinc/gsrobotics) (185 ⭐) — GelSight 传感器 SDK

## 核心挑战

1. **接触富有动力学**：灵巧操作涉及大量不连续接触和滑动，难以用传统运动学模型描述
2. **视觉遮挡**：手指在操作过程中往往遮挡视觉观测，必须依赖触觉或本体感受
3. **数据稀缺**：灵巧手的人类示范数据远比手臂操作稀缺，且存在人-机器人形态差异
4. **仿真到真实差距 (Sim-to-Real)**：灵巧手的接触和摩擦难以精确仿真，导致仿真策略迁移困难
5. **维护与可靠性**：灵巧手的结构复杂、执行器数量多，故障率高于简单夹爪

## 与其他概念的关系

- 与 [humanoid-robot](humanoid-robot.md) 的关系: 灵巧操作是人形机器人的"手"，与全身运动控制的"脚"形成补充
- 与 [vla-vision-language-action](vla-vision-language-action.md) 的关系: VLA 模型需要将高层指令映射到灵巧手的低层动作
- 与 [teleoperation-and-video-policies](teleoperation-and-video-policies.md) 的关系: 灵巧操作数据的采集严重依赖高自由度遥操作系统（如 DexCap）
- 与 [sim-to-real](sim-to-real.md) 的关系: 灵巧手的接触富有动力学使 sim-to-real 迁移极其困难
- 与 [imitation-learning-robotics](imitation-learning-robotics.md) 的关系: 灵巧操作是模仿学习最具挑战性的场景之一

## 参见

- [humanoid-robot](humanoid-robot.md) — 人形机器人运动控制
- [vla-vision-language-action](vla-vision-language-action.md) — 视觉-语言-动作统一架构
- [teleoperation-and-video-policies](teleoperation-and-video-policies.md) — 遥操作与视频策略
- [flow-matching](flow-matching.md) — 动作生成
- [open-hardware-robotics](open-hardware-robotics.md) — 开源硬件平台

## 最新研究动态 (2026-05-04 ~ 2026-05-11)

本周追踪到 5 篇灵巧操作/触觉相关新论文，核心趋势是：**无电子触觉界面**、**从 HOI 数据合成灵巧操作**、**无接触抓取稳定性预测**、**可微分仿真触觉**、**分层 RL+优化控制**。

- **TouchDrive: Electronics-Free Tactile Sensing Interface for Assistive Grasping** (Jing Xu et al., 2026-05-07) — 无需电子器件的纯机械触觉界面，通过简单的气动/机械结构实现抓取稳定性判断，极大降低辅助机械手系统复杂度。[arXiv:2605.06432](https://arxiv.org/abs/2605.06432)
- **DexSynRefine: Synthesizing and Refining Human-Object Interaction Motion for Physically Feasible Dexterous Robot Actions** (Hyesung Lee et al., 2026-05-07) — 从稀疏的 HOI 数据合成并精细化灵巧操作动作，通过物理可行性纠正解决形态不匹配和接触动力学问题。[arXiv:2605.05925](https://arxiv.org/abs/2605.05925)
- **Contact-Free Grasp Stability Prediction with In-Hand Time-of-Flight Sensors** (Kyle DuFrene et al., 2026-05-06) — 利用掌上 ToF 传感器在接触前预测抓取稳定性，免除传统触觉方法必须先抓取再判断的局限。[arXiv:2605.05461](https://arxiv.org/abs/2605.05461)
- **Reduced-order Neural Modeling with Differentiable Simulation for High-Detail Tactile Perception** (Yuhu Guo et al., 2026-05-06) — 结合可微分仿真与神经网络，对高分辨率触觉传感器的弹性体变形进行快速低阶建模，突破 FEM/MPM 的计算瓶颈。[arXiv:2605.05053](https://arxiv.org/abs/2605.05053)
- **Learning Reactive Dexterous Grasping via Hierarchical Task-Space RL Planning and Joint-Space QP Control** (Ho Jae Lee et al., 2026-05-05) — 层次化框架：高层多智能体 RL 负责任务空间意图，低层 QP 控制负责关节级执行，实现反应式灵巧抓取。[arXiv:2605.03363](https://arxiv.org/abs/2605.03363)