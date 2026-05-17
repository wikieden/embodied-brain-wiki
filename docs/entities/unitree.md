---
title: Unitree 宇树科技
created: 2026-05-11
updated: 2026-05-11
type: entity
tags: [company, robotics, locomotion, reinforcement-learning, open-source]
sources: [raw/articles/soul2humanoid-report-unitree.md, raw/articles/soul2humanoid-latest-news.md]
confidence: high
---

# Unitree 宇树科技

[官网](https://www.unitree.com) · [X/Twitter](https://x.com/UnitreeRobotics) · [GitHub](https://github.com/unitreerobotics)

宇树科技 2016 年成立于杭州，创始人王兴兴（1990 年生，上海大学硕士）。从四足机器人（机器狗）起家，2023 年切入人形机器人。

## 硬件产品

- **H1**：全尺寸人形，47kg（极致轻量化），行走速度 3.3m/s（世界纪录），189 N.m/Kg 扭矩密度
- **H1-2**：70kg，27 DoF，峰值负载 21kg
- **G1**：小型人形，$13,500 定价（"价格屠夫"），132cm / 35kg，面向教育/研究
- **R1 双臂平台**：$4,290 起，固定底座/轮式底座，15-31 DoF

## AI/控制

- **强化学习（RL）**驱动运动控制：行走、跑步、舞蹈（春晚《秧BOT》）
- **模仿学习**：动作捕捉 + 遥操作
- **UniFolm**：自研统一机器人大模型（跨四足+人形）
- 使用 [nvidia-isaac](nvidia-isaac.md) Isaac Sim / Gym 训练
- **运动控制架构**：基于 RL 的全身控制器，支持不同地形的自适应行走

## 成本控制秘诀

1. 自研 M107 关节电机，扭矩密度 189 N.m/Kg
2. 四足机器人量产经验摊薄研发成本
3. 中国制造供应链优势
4. 简化设计（G1 仅 5-DoF 手臂）
5. 模块化设计：关节、电机、控制器可独立更换与维护

## 2025-2026 动态

- **IPO 进程**：2025 年申请港股 IPO，预计筹资 $5.8 亿，目标进一步扩大产能与海外市场
- **年出货目标**：20,000 台（人形+四足），G1 占主导地位
- **海外市场**：正式进入美欧教育与研究市场，G1 成为多所大学的标准实验平台
- **工业合作**：与多家中国制造业企业合作测试人形机器人在产线上的应用
- **王兴兴 "80/80" 目标**：人形机器人在 80% 任务上达到 80% 成功率，被视为商业化的关键阈值

## 竞争格局

- **价格层**：与 [figure-ai](figure-ai.md) 、[boston-dynamics](boston-dynamics.md) 形成鲜明对比：Figure/Boston 做高端商业，Unitree 做低价研究级
- **量产能力**：拥有国内最完善的四足/人形量产线，是唯一能够大规模交付的中国人形机器人厂商
- **生态位置**：G1 定价 $13,500 极大降低了研究门槛，使得大量学术机构和初创公司能够进入人形机器人领域
- **技术路线**：以 RL 运动控制为核心壁垒，在动态平衡与移动操作上领先

## 关系

- 与 [nvidia-isaac](nvidia-isaac.md) 深度合作（Jetson Orin、Isaac Sim、GR00T 项目）
- 价格定位与 [figure-ai](figure-ai.md) 、[boston-dynamics](boston-dynamics.md) 形成鲜明对比
- G1 成为多个研究机构的标准实验平台，见 [genesis-world](genesis-world.md) 、[lerobot](lerobot.md) 等生态项目
