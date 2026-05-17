---
title: Data Flywheel in Robotics
created: 2026-05-11
updated: 2026-05-11
type: concept
tags: [training, robotics, self-supervised, multi-task]
sources: [raw/articles/soul2humanoid-report-figure-ai.md, raw/articles/soul2humanoid-report-tesla-optimus.md, raw/articles/soul2humanoid-report-physical-intelligence.md]
confidence: high
---

# Data Flywheel in Robotics

机器人部署 → 数据采集 → 模型训练 → 模型部署 → 更好的机器人行为 → 更多部署的闭环。

## 各公司飞轮模式

|| 公司 | 飞轮模式 | 数据来源 | 强度 |
||------|----------|----------|------|
|| **Tesla** | 车队级 | 数百万辆车 + 数千机器人 + YouTube 视频 | 极强 |
|| **Figure AI** | BotQ 自主生成 | 仿真+真实混合 + 人类视频 | 强 |
|| **Physical Intelligence** | π* 在线 RL | Open X-Embodiment + 自主 episode | 强 |
|| **NVIDIA** | 平台级 | 生态反馈 + 合成数据 | 强 |
|| **Boston Dynamics** | Fleet 共享 | Spot 2000+ 部署数据 | 中 |
|| **1X** | 专家遥操作 | 真实家庭 + Expert 遥控 | 早期 |
|| **Agility** | 监控为主 | 仓库部署数据 | 弱 |

## 遥操作与视频数据引擎

遥操作（Teleoperation）是数据飞轮的核心入口。根据硬件与交互方式，可分为：

- **VR / 沉浸式遥操作**：如 [Open-TeleVision](https://arxiv.org/abs/2407.01512)，操作员通过 VR 头显获得机器人第一人称视角
- **低成本同构遥操作**：如 [ALOHA](https://github.com/MarkFzp/mobile-aloha)（< $5k），通过同构主臂直接控制从臂
- **手持式 / 视觉遥操作**：如 [UMI](https://arxiv.org/abs/2402.10329)，利用手持夹具或视觉手部追踪采集人类操作
- **动作捕捉遥操作**：如 [DexCap](https://arxiv.org/abs/2406.09546)，通过穿戴设备捕捉人手精细动作
- **伪遥操作 / 仿真扩展**：如 [MimicGen](https://arxiv.org/abs/2310.17596)，基于少量真人示范在仿真中自动生成大规模变体数据

> 更多详细信息与论文列表，见 [teleoperation-and-video-policies](teleoperation-and-video-policies.md)。

## 合成数据的角色

- [tesla-optimus](../entities/tesla-optimus.md) "Digital Dreams"：Sora-like 视频生成 10,000+ 变体
- [nvidia-isaac](../entities/nvidia-isaac.md) [Omniverse Replicator](https://github.com/NVIDIA-Omniverse/OmniIsaacGymEnvs)：程序化生成无限标注数据
- [physical-intelligence](../entities/physical-intelligence.md) 世界模型：在仿真中试错再迁移到真实世界

## 关键开源项目

- **LeRobot** (Hugging Face)：开源机器人学习框架，整合了 ALOHA、Diffusion Policy、ACT 等算法与数据集，是数据飞轮生态的重要基础设施
- **Open X-Embodiment Dataset** (Google DeepMind + 多机构)：汇集 22 种机器人、超 1000 万条轨迹的跨本体数据集，支撑 Octo、RT-X 等通才策略预训练

## 关系

- 与 [sim-to-real](sim-to-real.md) 紧密相关：数据飞轮的最终目标是缩小仿真-真实差距
- 与 [vla-vision-language-action](vla-vision-language-action.md) 相互依存：VLA 需要大规模数据，飞轮产生数据
- 与 [teleoperation-and-video-policies](teleoperation-and-video-policies.md) 相关：遥操作是数据飞轮的核心入口
- 与 [robotics-data-engines](robotics-data-engines.md) 相关：数据引擎是数据飞轮的技术支撑
