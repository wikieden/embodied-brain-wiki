---
title: Tesla Optimus
created: 2026-05-11
updated: 2026-05-11
type: entity
tags: [company, model, robotics, embodiment, end-to-end]
sources: [raw/articles/soul2humanoid-report-tesla-optimus.md]
confidence: high
---

# Tesla Optimus

[官网](https://www.tesla.com/optimus) · [X/Twitter](https://x.com/Tesla_Optimus)

Tesla 人形机器人，FSD 神经网络直接移植，数据飞轮规模全球第一。

## 核心架构

- **单一端到端神经网络**：拒绝 HTN、行为树、状态机，梯度从控制直接流向感知
- **FSD 技术迁移**：8 摄像头纯视觉、Occupancy Network、端到端路径规划、车队学习
- **Grok LLM**：xAI 的 Grok 3 提供自然语言理解和语音交互
- **VLA 统一网络**：视觉 + 语言 + 动作在一个网络中联合学习

## 技术细节

### 硬件规格（Optimus Gen 2）

- **身高/体重**：173cm / 63kg（与 Figure 03 相当）
- **DoF**：全身 40+ 自由度，手部 11 DoF × 2，支持精细操作
- **执行器**：自研执行器，线性执行器与旋转执行器混合，支持 1kHz 控制频率
- **传感器**：8 个 Autopilot 级别摄像头（纯视觉）+ 壁虍音跟踪仪 + 力触觉传感器
- **计算**：内置 FSD 芯片（Samsung 7nm 工艺）+ Tesla 自研 SoC

### 训练基础设施

- **Cortex 超级计算机**：67,000+ NVIDIA H100 构成的超级计算集群，用于机器人与 FSD 的联合训练
- **OTA 更新**：类似 FSD 的滚动更新机制，全球机器人数据聚合后推送新模型
- **数据飞轮**：数百万辆特斯拉汽车的驾驶视频 → 数千台 Optimus 真机数据 → 互联网视频（YouTube、TikTok），规模无可匹敌

### FSD 迁移技术

Tesla 的核心竞争力在于将驾驶领域的技术直接复制到机器人：
- **Occupancy Network**：将三维空间占据网络从车辆视角转换为人形视角
- **End-to-End Path Planning**：车辆的路径规划网络适配为全身运动规划
- **车队学习**：每辆特斯拉都是数据采集器，机器人将继承同样的集体智慧
- **视觉栈共享**：Autopilot 的图像编码器直接用于 Optimus 的视觉理解

## 数据来源（三级学习）

| 阶段 | 方法 | 数据来源 | 规模 |
|------|------|----------|------|
| Stage 1 | 遥操作 | 动作捕捉 + VR 头显 | 极低 |
| Stage 2 | 第一人称视频 | 内置 5 摄像头 POV | 中等 |
| Stage 3 | 互联网视频 | YouTube 等第三方视频 | 理论上无限 |

## 合成数据：Digital Dreams

生成式视频 AI（Sora-like）从单次真实演示生成 10,000+ 变体，解决模仿学习的数据瓶颈。

## 记忆机制

- **空间记忆**：环境建图与导航
- **车队集体记忆**：Cortex 超算（67,000+ H100）聚合全球机器人数据，OTA 推送
- **生成式世界记忆**：Neural World Simulator 可"想象"未来状态

## 最新动态（2025-2026）

- **2024.10**：Optimus Gen 2 公开亮相，展示自主走路、爪子操作、折叠衣物等能力
- **2025.01**：Elon Musk 宣布 Optimus 将在 2025 年底开始有限量生产，目标 2026 年产量 50,000-100,000 台
- **2025 年中**：Tesla 工厂内部部署 Optimus 进行零件分拃与质量检测，作为"内部客户"
- **2025.10**：展示 Optimus 在工厂环境中自主导航与操作，支持自然语言指令
- **2026.01**：发布新一代手部设计，灵巧性显著提升
- **2026.04**：宣布目标成本降至 $20,000 以下，为大规模消费级交付做准备
- **制造优势**：利用 Tesla 汽车一体化压铸、结构化电池包等汽车级制造能力，目标极大降低机器人成本

## 竞争格局

- **数据飞轮规模**：与 [figure-ai](figure-ai.md) 、[physical-intelligence](physical-intelligence.md) 同为端到端派代表，但 Tesla 的数据飞轮规模全球第一，无可复制
- **制造能力**：拥有现有汽车产线和供应链，在规模化生产上潜在优势巨大
- **技术路线**："从车到机器人"的垂直整合，与 Figure 的 "从零构建"、PI 的 "纯软件" 形成对比
- **市场定位**：目标工业/工厂场景，与 1X 的家用定位形成差异化

## 关键人物

- **Elon Musk**：CEO，将 Optimus 视为 Tesla 未来价值的核心，多次表示 "Optimus 价值将超过汽车业务"
- **Ashok Elluswamy**：Autopilot 软件总监，负责 FSD 到 Optimus 的技术迁移
- **Milan Kovac**：Optimus 项目工程负责人，前 Autopilot 团队核心成员

## 关系

- 与 [figure-ai](figure-ai.md) 、[physical-intelligence](physical-intelligence.md) 同为端到端派代表
- 数据飞轮规模全球第一（数百万辆车 + 数千机器人）
- 与 [nvidia-isaac](nvidia-isaac.md) 在仿真领域有竞争/互补关系
- 数据策略参见 [data-flywheel-robotics](../concepts/data-flywheel-robotics.md)
