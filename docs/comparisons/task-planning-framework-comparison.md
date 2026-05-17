---
title: 任务规划框架对比
created: 2026-05-11
updated: 2026-05-11
type: comparison
tags: [comparison, task-planning, llm-planning, robotics, skill-composition]
sources: []
confidence: high
---

# 任务规划框架对比

> 从 SayCan (2022) 到 Reflect-VLM (2024)，LLM 驱动的机器人任务规划已经历经三代范式转变。本文对比 12 个代表性框架的架构选择、物理基定方式、失败恢复能力与开源状态。

---

## 1. 总体对比

| 框架 | 年份 | 机构 | 规划层级 | LLM 角色 | 物理基定 | 是否需训练 | 失败恢复 | 多机器人 | 开源 |
|------|------|------|----------|----------|----------|------------|----------|----------|------|
| **SayCan** | 2022 | Google | 高层语义 | 语义规划器 | 值函数 (Affordance) | 需低层策略 | 无 | ❌ | 社区实现 |
| **Code as Policies** | 2022 | Google | 中层代码 | 代码生成器 | 代码执行 + API | 零样本 | 无 | ❌ | 社区实现 |
| **Inner Monologue** | 2023 | Google | 高层语义 | 反馈驱动规划器 | 值函数 + 环境反馈 | 需低层策略 | 重新规划 | ❌ | ❌ |
| **VoxPoser** | 2023 | Stanford | 中层空间 | 约束提取器 | VLM 生成复杂值场 + MP | 零样本 | 无 | ❌ | [804⭐](https://github.com/huangwl18/VoxPoser) |
| **LLM+P / LLM+MAP** | 2023 | 多机构 | 高层符号 | PDDL 生成器 | 经典规划器保证最优 | 零样本 | 无 | ❌ | 社区实现 |
| **Plan-Seq-Learn** | 2024 | 多机构 | 分层 | LLM 引导器 | RL 策略学习 | 需要训练 | 重试 | ❌ | [127⭐](https://github.com/mihdalal/planseqlearn) |
| **Reflect-VLM** | 2024 | 多机构 | 分层 | 反思式规划器 | VLM 检测失败 + 反馈 | 需要训练 | 反思重规划 | ❌ | [174⭐](https://github.com/yunhaif/reflect-vlm) |
| **AutoTAMP** | 2024 | 多机构 | 分层 | 工具调用器 | TAMP 算法引擎 | 零样本 | 重新规划 | ❌ | [75⭐](https://github.com/yongchao98/AutoTAMP) |
| **SMART-LLM** | 2024 | Purdue | 高层协调 | 多机器人协调器 | 各机器人自主执行 | 零样本 | 重新分配 | ✅ | [191⭐](https://github.com/SMARTlab-Purdue/SMART-LLM) |
| **TypeFly** | 2024 | 社区 | 高层语义 | 任务规划器 | 低层策略执行 | 零样本 | 重试 | ❌ | [104⭐](https://github.com/typefly/TypeFly) |
| **kios** | 2024 | 社区 | 分层 | 行为树生成器 | 知识库 + 经典规划 + LLM | 零样本 | 重新规划 | ❌ | [78⭐](https://github.com/ProNeverFake/kios) |
| **SELP** | 2025 | Purdue | 分层 | 安全检查器 | 算法验证安全性 | 零样本 | 回退重规划 | ❌ | [18⭐](https://github.com/lt-asset/selp) |

---

## 2. 技术派别分析

### 派别 A: 高层语义规划 (符号级)

**代表**: SayCan, Inner Monologue, SMART-LLM, TypeFly

**核心逻辑**:
- LLM 生成高层语义动作序列（如"打开冰箱 → 取牛奶 → 关闭冰箱"）
- 每个动作的可行性由低层策略评估（SayCan 的 Affordance 函数）
- 优势: LLM 的语义理解能力强，可解释性好
- 劣势: 高层规划与低层执行之间存在"意图缝隙"，LLM 可能提出物理上不可行的动作

### 派别 B: 空间-符号混合规划 (代码/几何级)

**代表**: Code as Policies, VoxPoser, AutoTAMP, kios

**核心逻辑**:
- LLM 生成具有空间意识的中间表示（Python 代码、体素级 cost map、PDDL 约束）
- 优势: 规划结果具有物理基定，可解释性强
- 劣势: 依赖预定义的 API/工具/几何解算器，拓展性受限

### 派别 C: 反思式增强规划 (闭环级)

**代表**: Inner Monologue, Reflect-VLM, SELP

**核心逻辑**:
- 在执行过程中持续收集环境反馈（视觉、力矛、失败信号）
- LLM 根据反馈动态调整规划
- 优势: 适应动态环境，失败后能自我纠正
- 劣势: 反馈循环延迟较高，难以实时

### 派别 D: 学习增强规划 (数据驱动级)

**代表**: Plan-Seq-Learn, Reflect-VLM

**核心逻辑**:
- LLM 提供初始规划或中间表示，但核心能力通过强化学习获得
- 优势: 在复杂环境中性能上限高
- 劣势: 需要大量仿真/真实训练数据，数据收集成本高

---

## 3. 物理基定 (Physical Grounding) 对比

物理基定是任务规划框架最关键的差异点——**如何确保 LLM 生成的高层计划在物理世界中真正可执行**。

| 框架 | 基定机制 | 保证程度 | 代价 |
|------|----------|----------|------|
| **SayCan** | 低层策略评估每个提议的值函数 | 较高（筛除不可行动作） | 需要预先训练的低层策略 |
| **Code as Policies** | Python 代码在现实环境中执行，异常捕获 | 中（API 层面可行，但精度不保证） | 需要调试代码，延迟高 |
| **VoxPoser** | VLM 生成体素级 cost map + 运动规划器 | 高（几何级别碰撞检测） | 依赖精确的几何模型 |
| **LLM+P** | 经典 PDDL planner 保证规划完备性 | 最高（数学保证最优） | 需要将环境形式化为 PDDL |
| **AutoTAMP** | TAMP 算法引擎解答几何约束 | 高（动作+运动联合优化） | 算法复杂度高，延迟大 |
| **SELP** | 算法验证生成规划的安全性 | 高（等效性保证安全） | 限于可形式化验证的约束 |

---

## 4. 失败恢复能力对比

| 框架 | 失败检测 | 恢复策略 | 特点 |
|------|----------|----------|------|
| **SayCan** | 值函数低于阈值 | 排除该动作，选择下一个 | 被动式，无真正反思 |
| **Inner Monologue** | 环境反馈文本化 | 重新规划剩余步骤 | 主动式，利用环境反馈 |
| **Reflect-VLM** | VLM 检测执行失败 | 分析失败原因并重新规划 | 最完善的反思循环 |
| **AutoTAMP** | 运动规划失败 | 重新生成约束条件 | 算法级别的回退 |
| **SELP** | 安全检查不通过 | 回退到上一个安全状态重规划 | 形式化保证安全 |
| **SMART-LLM** | 机器人报告失败 | 重新分配子任务 | 多机器人协调层面的恢复 |

---

## 5. 开源生态与可用性

| 框架 | GitHub ⭐ | 语言 | 依赖复杂度 | 实际部署难度 |
|------|----------|------|------------|------------|
| **VoxPoser** | 804 | Python | 中（需要 LLM + VLM + 运动规划器） | 中 |
| **SMART-LLM** | 191 | Python | 低（纯 LLM 协调） | 低 |
| **Reflect-VLM** | 174 | Python | 高（需要 VLM + RL 策略） | 高 |
| **Plan-Seq-Learn** | 127 | Python | 高（需要 RL 环境 + LLM） | 高 |
| **TypeFly** | 104 | Python | 低 | 低 |
| **kios** | 78 | Python | 中（需要知识库 + 经典规划器） | 中 |
| **AutoTAMP** | 75 | Jupyter | 高（需要 TAMP 引擎） | 高 |
| **SELP** | 18 | 多种 | 中 | 中 |

> **推荐入门路径**:
> - 想快速上手: **TypeFly** 或 **SMART-LLM** (依赖少、代码简洁)
> - 想探索空间规划: **VoxPoser** (最完整的零样本空间规划)
> - 想研究失败恢复: **Reflect-VLM** (反思循环最完整)
> - 想研究多机器人: **SMART-LLM** (唯一开源的多机器人协调框架)

---

## 6. 趋势与演进方向

### 趋势 1: 从"单次规划"到"闭环反馈"
- SayCan → Inner Monologue → Reflect-VLM 的演进路径清晰表明，领域正在从"开放环规划"向"闭环控制"迁移
- 未来框架需要更紧密地融合视觉反馈和语言反思

### 趋势 2: 从"单机器人"到"多机器人协同"
- SMART-LLM 是目前唯一开源的多机器人协调规划框架
- 多机器人场景的复杂性（通信、同步、资源分配）尚未被充分研究

### 趋势 3: 从"零样本"到"学习增强"
- 早期框架（SayCan、VoxPoser）依赖零样本能力，新框架（Plan-Seq-Learn、Reflect-VLM）趋向于 LLM + RL 混合
- 如何在保留零样本通用性的同时提升任务特定性能是核心挑战

### 趋势 4: 安全保证从"启发式"到"形式化"
- SELP 开创了将形式化方法论（formal methods）引入 LLM 规划的先河
- 未来需要更多的安全验证工具来确保机器人不会执行危险动作

---

## 关系

- 框架详解: [task-planning-and-skill-composition](../concepts/task-planning-and-skill-composition.md)
- 具身大脑架构: [embodied-brain](../concepts/embodied-brain.md)
- 长程推理: [task-planning-and-skill-composition](../concepts/task-planning-and-skill-composition.md)
- 低层策略: [vla-vision-language-action](../concepts/vla-vision-language-action.md)
- 仿真到真实: [sim-to-real](../concepts/sim-to-real.md)
- 世界模型: [world-model-robotics](../concepts/world-model-robotics.md)
