---
title: Physical Intelligence (π)
created: 2026-05-11
updated: 2026-05-11
type: entity
tags: [company, model, architecture, robotics, open-source]
sources: [raw/articles/soul2humanoid-report-physical-intelligence.md]
confidence: high
---

# Physical Intelligence (π)

[官网](https://www.physicalintelligence.company) · [X/Twitter](https://x.com/PhysicalIntel) · [GitHub](https://github.com/Physical-Intelligence)

致力于构建控制**任意机器人**完成**任意任务**的通用机器人基础模型。由学术明星团队创立，18 个月内完成 7 次重大迭代。

## 核心模型演进

| 时间 | 版本 | 突破 |
|------|------|------|
| 2024.10 | π0 | 首个通用跨本体策略，VLM + Flow Matching，8 种机器人 |
| 2025.01 | FAST | DCT + BPE 动作 tokenization，10x 压缩，5x 加速 |
| 2025.02 | 开源 | π0 + FAST 权重与代码开源 |
| 2025.11 | π*0.6 / Recap | 首个在线 RL 训练的通用策略 |
| 2026.03 | MEM + RLT | 多尺度具身记忆（15min 长程）+ 高效 RL Token |
| 2026.04 | π0.7 | 可组合泛化，涌现技能重组能力 |

## 六大研究方向

1. **通用 VLA 基础模型**：3B VLM + Flow Matching 动作专家，50Hz 连续控制
2. **FAST 动作表示**：DCT 频域压缩 + BPE 子词编码，使自回归 VLA 成为可能
3. **跨本体迁移**：同一策略控制单臂/双臂/移动底盘，零样本迁移到新机器人
4. **RL 自提升闭环**：通用策略 → 在线 RL 优化 → 蒸馏回通用策略
5. **MEM 多尺度记忆**：短期视觉记忆 + 长期语言记忆，支持 15 分钟长程任务
6. **实时性优化**：Real-Time Chunking、Knowledge Insulation、RLT

## 技术细节

### FAST 动作 Tokenization

FAST（Frequency-space Action Tokenization with BPE）是 PI 的核心创新之一：
- **DCT 压缩**：将连续动作轨迹转换到频域，仅保留低频系数，实现 10x 压缩比
- **BPE 子词化**：在 DCT 系数上运行字节对编码，将动作表示为离散 token 序列
- **意义**：让自回归 VLM （如 PaLI/Gemma）可以直接生成动作 token，无需改变架构

### π0 架构

- **基座 VLM**：3B 参数的 PaLI-3 变体，处理视觉+语言输入
- **动作专家**：基于 Flow Matching 的连续动作生成模块，输出 50Hz 的关节目标标准
- **训练数据**：Open X-Embodiment 数据集（100k+ 条轨迹，涉及 8 种机器人）
- **推理**：支持自然语言指令解解码，可处理复杂多步骤任务

## 最新动态（2025-2026）

- **2024.10**：发布 π0，首个通用跨本体策略
- **2025.01**：发布 FAST，动作 tokenization 方案
- **2025.02**：开源 π0 + FAST 权重与代码，成为学术界基准
- **2025.11**：发布 π*0.6 / Recap，首个在线 RL 训练的通用策略
- **2026.03**：发布 MEM + RLT，多尺度具身记忆与高效 RL Token
- **2026.04**：发布 π0.7，展示可组合泛化与涌现技能重组
- **商业化**：PI 不自研硬件，采用 "软件即服务" 模式，与多家机器人制造商合作部署其策略

## 竞争格局

- 与 [figure-ai](figure-ai.md) 、[tesla-optimus](tesla-optimus.md) 构成端到端 VLA 三强，但 PI 专注通用策略而非自有硬件
- **核心区别**：Figure/Tesla 做 "终端——自有硬件+自有模型"；PI 做 "底层——通用模型服务任意硬件"
- **开源生态优势**：开源策略使其成为学术界和初创公司的首选基线，形成类似 LLaMA 在 NLP 中的生态位

## 关键人物

- **Karol Hausman**（前 Google Brain Robotics）：联合创始人，负责策略开发
- **Chelsea Finn** (Stanford) 、**Sergey Levine** (Berkeley) 等：顾问团队，提供学术背书与人才网络
- **团队规模**：约 100+ 人，主要在旧金山，集中于策略研究与工程

## 关系

- 与 [google-deepmind](google-deepmind.md) 间接依赖（数据集与人才）
- 与 [figure-ai](figure-ai.md) 、[tesla-optimus](tesla-optimus.md) 构成端到端 VLA 三强，但 PI 专注通用策略而非自有硬件
- 数据来源参见 [data-flywheel-robotics](../concepts/data-flywheel-robotics.md) 与 [cross-embodiment](../concepts/cross-embodiment.md)
