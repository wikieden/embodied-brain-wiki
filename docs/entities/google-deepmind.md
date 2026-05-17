---
title: Google DeepMind
created: 2026-05-11
updated: 2026-05-11
type: entity
tags: [lab, model, architecture, open-source]
sources: [raw/articles/soul2humanoid-report-google-deepmind.md, raw/articles/soul2humanoid-papers.md]
confidence: high
---

# Google DeepMind

[官网](https://deepmind.google) · [X/Twitter](https://x.com/GoogleDeepMind) · [GitHub](https://github.com/google-deepmind)

具身智能领域最重要的**技术赋能者**，不造硬件，纯软件/模型。定义了 VLA 架构，构建了行业数据基础设施。

## 技术演进

| 时间 | 技术 | 贡献 |
|------|------|------|
| 2023.07 | RT-2 | 首个大规模 VLA，VLM 直接输出机器人动作 token |
| 2023.10 | RT-X / Open X-Embodiment | 全球最大跨机器人数据集，22 种形态、1600万+ 轨迹 |
| 2024.03 | RT-H | 语言描述中间步骤，提升长程任务成功率 |
| 2024.08 | Gemini Robotics | Gemini 多模态能力引入机器人控制 |
| 2026.04 | Gemini Robotics-ER 1.6 | 增强具身推理，支持复杂任务规划 + 工具使用 |

## 双模型架构

- **Gemini Robotics 1.5（VLA）**：看 + 理解 + 动，跨本体泛化
- **Gemini Robotics-ER 1.6（具身推理）**：物理世界推理、逻辑决策、任务规划

### 技术细节

- **RT-2 突破**：首次证明 VLM 可以直接输出机器人动作 token，开创了 VLA 这一新范式
- **Open X-Embodiment**：全球 20+ 研究机构联合构建的跨本体数据集，包含 22 种机器人形态、1600 万+ 轨迹
- **Gemini 多模态能力**：利用 Gemini 的视觉理解与语言推理能力，支持复杂的多步骤任务规划与工具使用
- **开源生态**：通过开源数据集和发表基础论文，形成了具身智能领域的"公共品"定位

## 最新动态（2025-2026）

- **2025 年中**：发布 Gemini Robotics-ER 增强具身推理版本，支持更复杂的任务规划
- **2025 年底**：与 Apptronik、Boston Dynamics、Agility Robotics 等多家公司的合作进入深度集成阶段
- **2026.04**：发布 Gemini Robotics-ER 1.6，增强了物理世界推理和工具使用能力
- **合作生态扩张**：从单纯的技术输出者向"平台搭建者"转变，帮助合作伙伴快速获取 VLA 能力
- **人才流动**：多名 Boston Dynamics 和其他顶级机器人公司的 AI 研究人员加入 DeepMind

## 竞争格局

- **平台赋能者**：与 [physical-intelligence](physical-intelligence.md) 形成对比：平台赋能者 vs 垂直整合者
- **生态位置**：几乎所有主流机器人公司都在使用或参考其技术，是具身智能领域的"基础设施"
- **数据优势**：Open X-Embodiment 数据集是行业标准，[physical-intelligence](physical-intelligence.md) 的 π0 等模型直接基于该数据集训练
- **与其他巨头对比**：与 NVIDIA 的"卖铲子"、OpenAI 的"大模型"形成三足鼎立，各自占据生态位

## 关键人物

- **Sergey Levine**（Berkeley）：虽不是 DeepMind 员工，但其团队的 RT-2、Open X-Embodiment 等工作与 DeepMind 密切合作
- **Pete Florence**：DeepMind Robotics 团队负责人，负责 RT 系列和 Gemini Robotics 的策略与工程
- **Karol Hausman**：前 Google Brain Robotics 负责人，现 Physical Intelligence 联合创始人，体现了人才在生态中的流动

## 关系

- 与 [physical-intelligence](physical-intelligence.md) 形成对比：平台赋能者 vs 垂直整合者
- 几乎所有主流机器人公司都在使用或参考其技术
