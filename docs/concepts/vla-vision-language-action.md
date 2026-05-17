---
title: VLA (Vision-Language-Action)
created: 2026-05-11
updated: 2026-05-11
type: concept
tags: [model, architecture, multimodal, robotics]
sources: [raw/articles/soul2humanoid-papers.md, raw/articles/soul2humanoid-report-figure-ai.md, raw/articles/soul2humanoid-report-physical-intelligence.md]
confidence: high
---

# VLA (Vision-Language-Action)

将视觉感知、语言理解和动作生成统一在单一模型中的架构范式。

## 历史

[google-deepmind](../entities/google-deepmind.md) 的 **RT-2**（2023.07）首次将大规模视觉-语言模型（PaLI-X/PaLM-E）直接输出机器人动作 token，被引用 2000+ 次，成为具身智能基石论文。

## 架构组成

| 组件 | 功能 | 代表技术 |
|------|------|----------|
| 多模态输入 | 感知环境 + 任务指令 | 相机图像、自然语言、动作历史 |
| VLM 骨干 | 语义理解与知识迁移 | 3B 参数预训练视觉-语言模型 |
| 动作专家 | 生成高频连续动作 | Flow Matching / Diffusion / 自回归 |

## 动作表示方法

- **离散 token**：[RT-2](https://github.com/google-deepmind/rt2) 将动作离散化为 256 个 token
- **Flow Matching**：生成平滑连续动作轨迹（[physical-intelligence](../entities/physical-intelligence.md) [π0](https://github.com/Physical-Intelligence/openpi) 采用）
- **FAST**：DCT + BPE 动作 tokenization，10x 压缩率 ([Physical-Intelligence/fast](https://github.com/Physical-Intelligence/fast))

## 主流实现

| 公司 | 模型 | 动作生成 | 特点 |
|------|------|----------|------|
|| Figure AI | Helix | 双系统（快/慢） | 全身 loco-manipulation |
|| Physical Intelligence | [π0](https://github.com/Physical-Intelligence/openpi) | Flow Matching 50Hz | 跨本体 8 种机器人 |
|| Tesla | Optimus VLA | 端到端直接输出 | FSD 技术迁移 |
|| Google DeepMind | [Gemini Robotics](https://github.com/google-deepmind/gemini-robotics) | 动作 token | 双模型 VLA+ER |

## 挑战

- **实时性**：大模型推理延迟 vs 机器人 50-200Hz 控制需求
- **数据瓶颈**：机器人数据集远小于视觉-语言数据
- **安全验证**：端到端黑箱难以形式化验证

## 关系

- 定义者：[google-deepmind](../entities/google-deepmind.md) RT-2
- 开源基准：[physical-intelligence](../entities/physical-intelligence.md) π0
- 行业数据基础：[google-deepmind](../entities/google-deepmind.md) Open X-Embodiment

## 最新研究动态 (2026-05-04 ~ 2026-05-11)

本周追踪到 5 篇 VLA 相关新论文，核心趋势是：**联邦/无标注 VLA 训练**、**触觉融合**、**小样本 adaptation** 和**世界动作模型 (WAM)**。

- **ForgeVLA: Federated Vision-Language-Action Learning without Language Annotations** (Yuhao Zhou et al., 2026-05-08) — 联邦学习架构，允许多个机器人部署场景共享未标注视觉数据进行 VLA 训练，缓解标注瓶颈。[arXiv:2605.07474](https://arxiv.org/abs/2605.07474)
- **Escaping the Diversity Trap in Robotic Manipulation via Anchor-Centric Adaptation** (Yanzhe Chen et al., 2026-05-08) — 识别了 VLA 在低数据量下适应新硬件时的 "diversity trap"，提出 anchor-centric adaptation 策略提升少样本迁移效果。[arXiv:2605.07381](https://arxiv.org/abs/2605.07381)
- **AT-VLA: Adaptive Tactile Injection for Enhanced Feedback Reaction in Vision-Language-Action Models** (Xiaoqi Li et al., 2026-05-08) — 在 VLA 中自适应注入触觉信号，解决接触丰富操作场景中缺乏物理反馈的问题。[arXiv:2605.07308](https://arxiv.org/abs/2605.07308)
- **BioProVLA-Agent: Protocol-Driven, Vision-Enhanced VLA for Biological Laboratory Manipulation** (Zhaohui Du et al., 2026-05-08) — 垂直领域 VLA 落地案例：针对生物实验室的透明/反光器皿、多步验证、闭环推理。[arXiv:2605.07306](https://arxiv.org/abs/2605.07306)
- **OA-WAM: Object-Addressable World Action Model for Robust Robot Manipulation** (Yushan Liu et al., 2026-05-07) — 将 VLA 与 World Action Model 结合，用 object-addressable 表示替代全局图像/视频 token，提升动作解码器对细节的关注。[arXiv:2605.06481](https://arxiv.org/abs/2605.06481)