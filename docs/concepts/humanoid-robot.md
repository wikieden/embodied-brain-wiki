---
title: Humanoid Robot
created: 2026-05-11
updated: 2026-05-11
type: concept
tags: [robotics, embodiment, locomotion, manipulation]
sources: [raw/articles/soul2humanoid-index.md, raw/articles/soul2humanoid-comparisons.md]
confidence: high
---

# Humanoid Robot

拥有类人形态（双足、双臂、头部、躯干）的机器人，设计初衷是适配人类现有环境。

## 为什么是人形

- **环境通用性**：无需为每种任务改造环境，一个形态服务数百万种任务
- **视角相似性**：运动学和视角与人类相似，便于从人类视频迁移知识
- **社会接受度**：人类对类人形态有本能的亲和感

## 主流产品对比

| 公司 | 产品 | 身高 | 体重 | DoF | 价格/定位 | 市场 |
|------|------|-------|-------|-----|------------|------|
| Figure AI | Figure 03 | 173cm | 61kg | ~35+ | $400-600/月租赁 | 商业→家庭 |
| Boston Dynamics | Atlas | 190cm | 90kg | 56 | 未公开 | 工业 B2B |
| Tesla | Optimus | ~173cm | ~73kg | ~78 | 未公开 | 工厂→家庭 |
| 1X | NEO | 167cm | 30kg | ~30+ | 未公开 | 家庭 C 端 |
|| [Unitree](https://github.com/unitreerobotics) | H1 | 180cm | 47kg | ~20 | 不是消费级 | 教育/研究 |
|| [Unitree](https://github.com/unitreerobotics) | G1 | 132cm | 35kg | 23 | $13,500 | 教育/研究 |
| Agility | Digit | 175cm | 65kg | 16 | 未公开 | 仓储 B2B |
| Apptronik | Apollo | 173cm | 73kg | ~30+ | 未公开 | 工业 B2B |

## 技术分派

- **端到端派**：[figure-ai](../entities/figure-ai.md)、[physical-intelligence](../entities/physical-intelligence.md)、[tesla-optimus](../entities/tesla-optimus.md)
- **分层混合派**：[boston-dynamics](../entities/boston-dynamics.md)、[agility-robotics](../entities/agility-robotics.md)
- **平台+合作 AI**：[apptronik](../entities/apptronik.md)、[enchanted-tools](../entities/enchanted-tools.md)

## 关系

- AI 大脑：[vla-vision-language-action](vla-vision-language-action.md)
- 训练基础：[sim-to-real](sim-to-real.md)
- 数据驱动：[data-flywheel-robotics](data-flywheel-robotics.md)

## 最新研究动态 (2026-05-04 ~ 2026-05-11)

本周追踪到 1 篇人形机器人运动控制相关新论文：

- **BifrostUMI: Bridging Robot-Free Demonstrations and Humanoid Whole-Body Manipulation** (Chenhao Yu et al., 2026-05-05) — 无需机器人的全身操作示范方案，受 UMI 启发，解决人形机器人数据采集硬件不足、效率低的痛点。[arXiv:2605.03452](https://arxiv.org/abs/2605.03452)