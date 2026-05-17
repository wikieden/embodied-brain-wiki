---
title: Boston Dynamics
created: 2026-05-11
updated: 2026-05-11
type: entity
tags: [company, robotics, locomotion, mpc, lab]
sources: [raw/articles/soul2humanoid-report-boston-dynamics.md, raw/articles/soul2humanoid-latest-news.md]
confidence: high
---

# Boston Dynamics

[官网](https://bostondynamics.com) · [X/Twitter](https://x.com/BostonDynamics) · [GitHub](https://github.com/boston-dynamics)

1992 年创立的足式机器人领导者，Atlas/Spot/Stretch 产品线，分层混合架构。

## 产品矩阵

| 产品 | 形态 | 场景 | 部署规模 |
|------|------|------|----------|
| Spot | 四足 | 工业巡检 | 2,000+ |
| Stretch | 轮式+臂 | 仓储搬运 | 试点 |
| Atlas | 双足人形 | 制造/零件排序 | ~4 台/月（2026） |
| Orbit | 软件 | Fleet 管理 | — |

## Atlas 技术规格（产品版）

- 身高 1.9m / 体重 90kg / 56 DoF
- 关节**连续旋转**（无机械限位），超越人类运动范围
- 防护等级 IP67，工作温度 -20°C ~ 40°C
- 负载 50kg（瞬时）/ 30kg（持续），续航 4h

## AI 架构：分层混合

|| 层级 | 方法 | 能力 |
||------|------|------|
|| 底层平衡 | MPC + RL | 实时稳定、防滑、动态响应 |
|| 中层运动规划 | 优化 + 学习 | 全身协调、避障、自碰撞避免 |
|| 高层感知决策 | 视觉基础模型 + VLA | 语义理解、任务推理 |
|| 操纵执行 | Diffusion Transformer（4.5亿参数） | 端到端灵巧操作、语言条件化 |

### 技术细节

- **MPC + RL 混合控制**：底层使用模垄预测控制（MPC）确保稳定性和安全性，上层使用强化学习优化运动效率，二者结合实现高动态表现与安全保障
- **Diffusion Transformer 操纵**：Atlas 的灵巧操作端使用 450M 参数的 Diffusion Transformer，从视觉观测和语言指令生成高频动作，是 Boston Dynamics 向端到端学习过渡的关键技术
- **Orbit 软件平台**：集中管理 Spot 机器人队，支持任务编排、数据聚合、远程监控，是从单机向队级部署过渡的核心软件

## 关键合作与学术贡献

- **TRI**（Toyota Research Institute）：联合发表论文，Atlas 使用单一 Diffusion Transformer 完成复杂长程操作
- **Google DeepMind**：Atlas AI 行为系统可能集成 Gemini Robotics
- **MIT / Harvard 等**：Boston Dynamics 是足式机器人领域的学术先驱，Spot 和 Atlas 的技术论文影响了整个领域

## 最新动态（2024-2026）

- **2024.04**：发布全新电动 Atlas（取代液压版），重新设计的电气和软件架构，更轻、更灵活、更安全
- **2024.06**：Hyundai 正式宣布将 Boston Dynamics 作为机器人业务核心，计划大规模投资
- **2025 年中**：电动 Atlas 进入工厂试点部署，主要用于零件排序和简单操作
- **2025 年底**：Spot 部署量突破 2,000 台，主要集中在工业巡检、建筑和公共安全
- **2026 年初**：CEO Robert Playter 退休、CTO Aaron Saunders 加入 DeepMind、VP Scott Kuindersma 离职 — 核心管理层大换血
- **2026 年中**：Hyundai 要求年产 30,000 台，但当时仅 ~4 台/月，研究→商业转型阵痛明显
- **Atlas 量产挑战**：电动版 Atlas 的量产化难度远超预期，核心问题在于成本控制与可靠性

## 竞争格局

- **技术深度**：与 [agility-robotics](agility-robotics.md) 同为**分层混合派**代表，拥有 30+ 年的足式机器人研究底蕴，在动态平衡和运动控制上无可匹敌
- **商业化透明**：与 [figure-ai](figure-ai.md) 、[unitree](unitree.md) 相比，Boston Dynamics 的商业化速度明显滞后，但技术优势仍在
- **路线分歧**：从 "研究为主" 向 "商业为主" 转型中，人才流失严控是核心风险
- **开源影响**：Spot SDK 和学术论文对整个足式机器人/人形领域产生了深远影响

## 关键人物

- **Marc Raibert**：创始人（1992），足式机器人领域先驱，现任 Boston Dynamics AI Institute 主任，负责长期研究规划
- **Robert Playter**：前 CEO，任期内推动 Spot 商业化和电动 Atlas 重新设计，2026 年初退休
- **Aaron Saunders**（前 CTO）：转投 Google DeepMind，反映了 AI 人才向科技巨头集中的趋势
- **Scott Kuindersma**（前 VP of Robotics）：Atlas 运动控制核心负责人，离职后加入其他机器人公司

## 关系

- 与 [agility-robotics](agility-robotics.md) 同为**分层混合派**代表
- 与 [google-deepmind](google-deepmind.md) 合作探索 VLA 集成
- 产品路线参见 [humanoid-robot](../concepts/humanoid-robot.md) 与 [embodied-benchmarks](../concepts/embodied-benchmarks.md)
