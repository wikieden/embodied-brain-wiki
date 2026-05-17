---
title: 数据集与数据引擎
created: 2026-05-11
updated: 2026-05-11
type: concept
tags: [dataset, training, embodiment, data-engine]
sources: [raw/articles/github-embodied-ai-projects-2026-05-11.md]
confidence: high
---

# 数据集与数据引擎

机器人学习的"石油"。当前的瓶颈不是算法，而是高质量、多样化、可扩展的数据。如何低成本获取大规模数据，如何统一不同机器人的数据格式，如何利用伪标签和合成数据拓展数据湖，是领域的核心议题。

## 核心数据集

| 数据集 | 来源 | 规模 | 特点 |
|--------|------|-------|------|
| [Open X-Embodiment](https://github.com/google-deepmind/open_x_embodiment) | Google DeepMind + 20+ 研究机构 | 22 种形态、1600万+ 轨迹 | 跨本体、多任务、RLDS 格式 |
| [LeRobot](https://github.com/huggingface/lerobot) | HuggingFace | 多种预训练数据集 | 统一格式、Hub 集成 |
| [GigaWorld-0](https://github.com/open-gigaai/giga-world-0) | Open Giga AI | 世界模型生成 | 用世界模型作为数据引擎 |
| [1xgpt](https://github.com/1x-technologies/1xgpt) | 1X Technologies | 人形机器人世界建模挑战 | 视频预测 + 动作标签 |

## 数据引擎工具

| 工具 | 功能 | 链接 |
|------|------|------|
| LeRobot | 数据采集、管理、训练、部署全流程 | [lerobot](https://github.com/huggingface/lerobot) |
| forge | RLDS / LeRobot / Zarr / HDF5 格式转换 | [forge](https://github.com/arpitg1304/forge) |
| Omniverse Replicator | NVIDIA 程序化生成无限标注合成数据 | [IsaacGymEnvs](https://github.com/NVIDIA-Omniverse/OmniIsaacGymEnvs) |

## 数据来源演进

1. **遥操作 (Teleoperation)**：高质量、低规模。人类操作员通过 VR/AR 手柄控制机器人，录制精确的动作对。
2. **仿真合成**：无限规模、但存在域差异。利用仿真器生成大量带标注的训练数据。
3. **视频到任务 (Video2Tasks)**：可扩展性最强。从 YouTube 等人类视频中提取操作知识。Tesla 正在探索这一路径。
4. **自主采集 (Self-Supervised)**：机器人在部署中自动采集数据，通过飞轮闭环不断增长。

## 核心问题

1. **跨本体数据融合**：不同机器人、不同传感器配置的数据如何统一表示？Open X-Embodiment 的 RLDS 格式是一种尝试。
2. **数据质量 vs 规模**：大规模低质量数据是否有用？如何筛选、重新采样、或通过自监督学习提升数据质量？
3. **合成数据的域差异**：仿真生成的数据与真实世界的差距如何弥补？
4. **遥操作效率**：如何降低人类采集成本？半自主、伪标签、视频到任务都是潜力方向。

## 可研究细分

- 数据集格式标准化（统一动作空间、观察空间、元数据）
- 自动质量评分与数据筛选
- 视频理解生成机器人操作 (video-to-policy)
- 在线数据增强与自适应

## 关系

- [lerobot](../entities/lerobot.md) — 数据管理与训练框架
- [cross-embodiment](cross-embodiment.md) — 跨本体数据融合
- [nvidia-isaac](../entities/nvidia-isaac.md) — 合成数据工具
- [world-model-robotics](world-model-robotics.md) — 世界模型作为数据引擎
- [data-flywheel-robotics](data-flywheel-robotics.md) — 数据飞轮闭环
