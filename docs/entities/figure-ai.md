---
title: Figure AI
created: 2026-05-11
updated: 2026-05-11
type: entity
tags: [company, model, robotics, embodiment]
sources: [raw/articles/soul2humanoid-report-figure-ai.md, raw/articles/soul2humanoid-latest-news.md]
confidence: high
---

# Figure AI

[官网](https://www.figure.ai) · [X/Twitter](https://x.com/Figure_robot)

估值 $390 亿的通用人形机器人公司，Helix VLA + BotQ 制造。

## 核心产品

- **Figure 03**：为量产、家庭、AI 设计的 173cm / 61kg 人形机器人，5h 续航
- **Helix VLA**：端到端视觉-语言-动作模型
  - Helix V1（2025.02）：上半身通才，35-DoF，200Hz
  - Helix 02（2026.01）：全身 loco-manipulation，三层时序架构
- **BotQ**：专用制造工厂，首代年产 12,000 台，四年目标 100,000 台

## Helix 三层架构

| 系统 | 频率 | 功能 |
|------|------|------|
| System 2 | 7 Hz | 语义/慢速推理："做什么" |
| System 1 | 200 Hz | 运动/中速控制："怎么做" |
| System 0 | 1 kHz | 执行/实时平衡："稳不稳" |

## 关键人物

- **Brett Adcock**：创始人（Archer / Vettery 连续创业者）

## 数据策略

1. 遥操作数据（500h）→ 2. 人体运动数据（1000h+）→ 3. 互联网规模人类视频（Project Go-Big，Brookfield 住宅环境）

## 技术细节

- **Helix 训练管线**：采用类似 Tesla FSD 的 "video-to-control" 端到端流程，不依赖中间表示（如关键点、骨架）
- **System 2 架构**：基于 Transformer 的慢速推理系统，处理语义理解与任务分解，可接受自然语言指令和图像输入
- **System 1 构建**：基于 diffusion 或 flow matching 的中速运动生成器，输出 200Hz 的关节目标位置
- **System 0 实时性**：硬实时控制回路（不经过神经网络），确保 1kHz 的平衡与反射控制
- **跨模态迁移**：Helix 支持在不同机器人形态间迁移，核心突破是 "unified action space" 的设计

## 最新动态（2025-2026）

- **2025.02**：发布 Helix V1，展示上半身通才操作能力
- **2025 年中**：BotQ 工厂开始运营，首批量产 Figure 03
- **2025.11**：宣布与 BMW 合作，在南卡罗来纳州工厂部署人形机器人
- **2026.01**：发布 Helix 02，支持全身 loco-manipulation，展示同时行走与操作
- **2026.04**：宣布获得 $675M 融资（预备，待验证），估值接近 $2.6B（注：与之前 $39B 传闻可能不同，需核实）
- **数据飞轮**：Project Go-Big 在 Brookfield 实际住宅环境中收集人类视频数据，用于扩展通用性

## 竞争格局

- 与 [tesla-optimus](tesla-optimus.md) 、[1x-technologies](1x-technologies.md) 构成端到端 VLA 三强，但 Figure 更侧重商业化部署
- 与 [boston-dynamics](boston-dynamics.md) 不同，Figure 不卖只卖 "机器人+大脑" 的整体解决方案
- 核心壁垒：自有硬件与自有模型的垂直整合，对比 PI 的 "纯软件" 路线

## 关键人物

- **Brett Adcock**：创始人（Archer / Vettery 连续创业者），积极在 X 上分享公司进展，被视为该领域最活跃的公关人物之一
- **Corey Lynch**（前 Google DeepMind）：技术高管，负责 Helix 模型开发
- **Jerry Pratt**（前 IHMC）：人形机器人运动控制专家

## 关系

- 与 [nvidia-isaac](nvidia-isaac.md) 合作使用 Isaac Sim 训练
- Helix 架构受 [google-deepmind](google-deepmind.md) RT 系列启发
- 与 [physical-intelligence](physical-intelligence.md) 、[tesla-optimus](tesla-optimus.md) 构成端到端 VLA 三强
- 数据策略参见 [data-flywheel-robotics](../concepts/data-flywheel-robotics.md)

> 来源：soul2humanoid-report-figure-ai.md, soul2humanoid-latest-news.md
