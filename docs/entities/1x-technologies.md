---
title: 1X Technologies
created: 2026-05-11
updated: 2026-05-11
type: entity
tags: [company, robotics, embodiment, world-model]
sources: [raw/articles/soul2humanoid-report-1x-technologies.md, raw/articles/soul2humanoid-latest-news.md]
confidence: high
---

# 1X Technologies

[官网](https://www.1x.tech) · [X/Twitter](https://x.com/1x_tech)

OpenAI 投资的家用人形机器人公司，核心产品 NEO，肌腱驱动+世界模型。

## 核心定位

**唯一主打家用市场的人形机器人公司**，直接面向 C 端消费者，而非工业场景。

## 硬件：NEO

- 身高 167cm / 体重 30kg / 行走 1.4m/s / 奔跑 6.2m/s
- **肌腱驱动（Tendon-Driven）**：反向可驱动性 95%，噪音仅 22dB
- **软体设计**：3D 晶格聚合物结构，外衣可机洗
- **计算**：NVIDIA Jetson Thor，最高 2070 FP4 TFLOPS
- 双 8.85MP 90Hz 鱼眼立体相机

## AI 架构

- **Redwood VLA**：移动 + 操作联合控制，从失败中学习
- **1X World Model**：基于物理的视频生成模型，执行前"想象"结果
- **内置 LLM**：离线语言模型，实时预测用户意图
- **Expert Mode**：用户预约 1X Expert 远程遥控，边做边学

### 技术细节

#### 肌腱驱动（Tendon-Driven Actuation）

1X 的核心硬件创新是采用类似人类肌肉的肌腱驱动，而非传统的刚性关节电机：
- **反向可驱动性**：95% 的能量可以被外部力反向驱动，大幅降低了与人交互时的伤害风险
- **低噪音**：运行声音仅 22dB，比微风声还小，适合家庭环境
- **柔顺性**：支持类似人类的自然运动，避免了机械式的生硬感
- **挑战**：维护复杂度高，软件控制算法需要对弹性系数建模，控制难度高于刚性执行器

#### Redwood VLA 架构

- **多模态输入**：视觉（双鱼眼相机）+ 语言（内置 LLM）+ 本体感知（力触觉、IMU）
- **端到端训练**：移动与操作联合优化，而非分离的"先走到位置再操作"
- **从失败中学习**：自主采集失败轨迹，通过对比成功/失败轨迹改进策略
- **安全与开箱即用**：设计为非专业用户可操作，重视人机交互安全

#### 1X World Model

- **物理一致性**：视频生成模型基于物理引擎，确保"想象"的动作在物理上可行
- **在线规划**：执行前在脑中模拟多个未来轨迹，选择最优方案
- **与 Tesla 对比**：同样采用视频生成作为世界模型，但 1X 更侧重在线规划与安全验证

## 数据策略

- **Expert Mode**：核心创新，用户可预约 1X 专家进行远程遥操作，在任务执行过程中自动采集示范数据
- **家庭环境专有数据**：直接在真实家庭中部署，收集居家操作数据，这是工业/工厂场景无法获取的
- **数据稀缺性挑战**：家庭任务多样性高、反复率低，数据飞轮的转速远低于工厂场景

## 制造

- **NEO Factory**（Hayward, CA）：58K sqft，全垂直整合
- Revo2 电机、电池、肌腱、22-DoF 手全部自产
- 初始产能 10,000 台/年，2027 年底目标 100,000 台/年
- 预售 5 天售罄

## 最新动态（2024-2026）

- **2024.01**：完成 $100M B 轮融资，OpenAI 领投，用于 NEO 研发与量产
- **2024.08**：发布 NEO Beta 版，展示在家庭环境中的移动操作能力
- **2025.01**：开放 NEO 预订，定价策略显示目标消费级市场（预估 $20,000-$40,000 区间）
- **2025 年中**：开始在真实家庭中部署 NEO 进行数据采集，主要位于加州
- **2025.11**：预售 5 天内售罄，显示强劲的市场需求
- **2026.01**：发布 Redwood VLA 更新，展示更复杂的家居任务执行能力
- **2026.04**：宣布与多家零售商/物流公司探索合作，但仍以直接向消费者销售为主

## 竞争格局

- **唯一家用定位**：与 [figure-ai](figure-ai.md) 、[tesla-optimus](tesla-optimus.md) 、[unitree](unitree.md) 目标市场完全不同（家用 vs 工业/工厂）
- **数据挑战**：家庭场景的数据稀缺性是最大瓶颈，Expert Mode 是创新解决方案
- **安全壁垒**：肌腱驱动 + 软体设计构建了家用市场的安全门槛，但也增加了成本
- **OpenAI 绑定**：深度获得 OpenAI 的 LLM 能力和品牌背书，但也意味着技术路径受 OpenAI 战略影响

## 关键人物

- **Bernt Børnich**：CEO / 创始人，前 Google 工程师，2014 年创立 Halodi Robotics（后改名 1X），坚定推动家用定位
- **Eric Jang**：前 Google Brain 研究员，现任 AI 负责人，负责 Redwood VLA 和 1X World Model 的策略研发
- **团队背景**：多名前 OpenAI、Google DeepMind、NVIDIA 工程师，AI 实力强劲

## 关系

- OpenAI 深度绑定，LLM 能力独特
- 与 [nvidia-isaac](nvidia-isaac.md) 合作使用 Isaac Sim / Omniverse
- 与 [figure-ai](figure-ai.md) 、[tesla-optimus](tesla-optimus.md) 目标市场不同（家用 vs 商业/工厂）
- 数据策略参见 [data-flywheel-robotics](../concepts/data-flywheel-robotics.md) 与 [teleoperation-and-video-policies](../concepts/teleoperation-and-video-policies.md) 中的 Expert Mode
