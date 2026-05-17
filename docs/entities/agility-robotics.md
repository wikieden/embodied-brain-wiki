---
title: Agility Robotics
created: 2026-05-11
updated: 2026-05-11
type: entity
tags: [company, robotics, locomotion, manipulation]
sources: [raw/articles/soul2humanoid-report-agility-robotics.md]
confidence: high
---

# Agility Robotics

[官网](https://www.agilityrobotics.com) · [X/Twitter](https://x.com/agilityrobotics)

物流仓储专用人形机器人 Digit，分层控制 LIPM+ZMP+MPC。

## 设计哲学

- **场景优先**：完全围绕"搬运塑料 tote"优化，非通用设计
- **成本可控**：无五指灵巧手、无躯干自由度，硬件复杂度低
- **热插拔电池**：1-2 分钟更换，支持连续作业

## Digit 2.0 规格

- 身高 ~175cm / 体重 ~65kg / 16 DoF / 行走 1.5m/s
- 负载 ~16kg（单 tote）/ 续航 2-4h
- 头部 Intel RealSense 深度相机

## AI 架构：传统分层控制

|| 层级 | 方法 | 功能 |
||------|------|------|
|| 任务调度 | WMS 集成 | 接收搬运指令 |
|| 高层规划 | 路径规划 | 避障、抓取策略 |
|| 运动控制 | LIPM + ZMP + MPC | 双足动态行走 |
|| 底层关节 | PD + 力矩前馈 | 关节控制 |

- 预定义步态库，非神经网络生成
- 视觉伺服定位 tote，力/位置混合控制夹爪

### 技术细节

- **LIPM（线性倒立摇摆模型）**：将双足行走简化为倒立摇摆的物理模型，大幅降低计算复杂度，适合实时控制
- **ZMP（零势点）**：确保足底接触面内的压力中心始终位于支撑多边形内，是双足机器人不倒的关键条件
- **MPC（模型预测控制）**：在每个控制周期优化未来时域的运动轨迹，实现动态稳定性与能耗优化的平衡
- **与端到端派对比**：这种分层方法在工厂重复性任务上极为可靠，但缺乏泛化能力，难以应对未见场景

## 最新动态（2022-2026）

- **2022-2023**：与 **Amazon** 仓库试点，在实际物流环境中测试 Digit 的搬运能力
- **2024**：与 **GXO** 签订多年合作协议，是人形机器人领域最早的大型商业合作之一
- **2025 年底**：宣布与 **Google DeepMind** 合作，将 Gemini 集成到 Digit 的高层决策系统
- **2026 年初**：Peggy Johnson 新任 CEO（前 Magic Leap / Microsoft），提出 "Unconstrained Humanoids" 愿景，意味着从"仓库专用"向"通用人形"转型
- **核心挑战**：尝试在保持成本可控的同时增加灵巧性和泛化性

## 竞争格局

- **分层混合派**：与 [boston-dynamics](boston-dynamics.md) 同为分层混合派代表，但更侧重商业部署而非研究
- **场景专注**：与 [figure-ai](figure-ai.md) 、[tesla-optimus](tesla-optimus.md) 等通用人形定位不同，Agility 选择"做好一件事"的策略
- **成本优势**：无五指灵巧手、无躯干自由度的简化设计，使其在成本控制上具有显著优势
- **商业化程度**：是目前商业部署最成熟的人形机器人公司之一，拥有与 Amazon、GXO 的真实合作案例

## 关键人物

- **Peggy Johnson**：CEO（2026 年上任），前 Magic Leap CEO、Microsoft 高管，带来丰富的商业化经验
- **Damion Shelton**：前 CEO / 联合创始人，从 OSU 双足机器人实验室走出，负责 Digit 的早期设计与仓库场景验证
- **Jonathan Hurst**：联合创始人 / CTO，OSU 机械工程教授，双足机器人动力学专家，LIPM 方法的主要推动者

## 关系

- 与 [boston-dynamics](boston-dynamics.md) 同为**分层混合派**代表
- 与 [google-deepmind](google-deepmind.md) 合作（可信测试者，Digit 集成 Gemini）
