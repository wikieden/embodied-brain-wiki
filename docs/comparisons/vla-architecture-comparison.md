---
title: VLA 架构对比
created: 2026-05-11
updated: 2026-05-11
type: comparison
tags: [comparison, model, architecture, robotics]
sources: [raw/articles/soul2humanoid-comparisons.md]
confidence: high
---

# VLA 架构对比

11 家具身智能公司的 VLA 架构选择对比。

## 总体架构

| 维度 | Figure AI (Helix) | Physical Intelligence (π0) | Tesla (Optimus) | Boston Dynamics (Atlas) | 1X (Redwood) | Google DeepMind (Gemini) | Agility (Digit) | Apptronik (Apollo) | NVIDIA (GR00T) |
|------|-------------------|---------------------------|-----------------|------------------------|--------------|--------------------------|----------------|-------------------|----------------|
| 架构类型 | 端到端 VLA | 端到端 VLA | 端到端神经网络 | 分层混合 | 端到端 VLA + World Model | 双模型 VLA+ER | 传统分层 | 硬件+合作 AI | Transformer VLA 参考 |
| 基础模型 | 自研 VLA | 3B VLM + Flow Matching | FSD 神经网络移植 | Diffusion Transformer (4.5亿) | Redwood VLA + 内置 LLM | Gemini 多模态 | LIPM+ZMP+MPC | Gemini (合作) | GR00T Transformer |
| 动作生成 | 双系统 (快/慢) | Flow Matching 50Hz | 端到端直接输出 | Flow Matching 30Hz | VLA 联合移动+操作 | VLA 动作 token | 预定义步态库 | Gemini 输出 | VLA 动作 token |
| 跨本体 | 否 | ✅ (8种) | 否 | 否 | 否 | ✅ | 否 | 部分 | ✅ (参考) |
| 语言条件化 | ✅ | ✅ | Grok | ✅ | ✅ 内置LLM | ✅ Gemini | ❌ | ✅ (Gemini) | ✅ |

## 技术派别

| 派别 | 代表公司 | 核心信念 | 优势 | 风险 |
|------|---------|---------|------|------|
| **端到端** | Figure AI, PI, Tesla | "梯度从控制直接流向感知，全局最优" | 可扩展、长尾适应好、性能上限高 | 黑箱难调试、安全验证困难、需要海量数据 |
| **分层混合** | Boston Dynamics, Agility | "MPC/传统控制提供可信赖基础，学习补充边缘" | 可解释、可调试、安全性高、数据需求低 | 各层接口可能次优、新场景处理难 |
| **平台+合作AI** | Apptronik, Enchanted | "硬件自研，AI 借力最强合作伙伴" | AI 能力起点高、专注硬件差异化 | 对合作伙伴依赖高、自主 AI 护城河浅 |
| **基础设施** | NVIDIA Isaac | "提供训练+仿真+部署全栈，不造机器人" | 生态绑定深、零机器人风险 | 不控制终端场景、GR00T 能力待验证 |

## 关系

- 架构基础：[vla-vision-language-action](../concepts/vla-vision-language-action.md)
- 动作生成：[flow-matching](../concepts/flow-matching.md)
- 数据驱动：[data-flywheel-robotics](../concepts/data-flywheel-robotics.md)
