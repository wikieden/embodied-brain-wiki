---
title: Task Planning and Skill Composition
created: 2026-05-11
updated: 2026-05-11
type: concept
tags: [task-planning, skill-composition, llm-planning, code-as-policy, hierarchical-control]
sources: []
confidence: high
---

# 任务规划与技能组合 (Task Planning & Skill Composition)

> VLA 解决了"怎么做"（How），任务规划解决的是"做什么"（What）和"为什么做"（Why）。当用户说"把洗好的衣服晒到阳台"时，机器人需要先理解这个高层目标，将其分解为"取衣服→开门→走到阳台→撒开衣架→挂衣服"，然后调用低层策略逐一执行。
>
> 长程任务推理是任务规划的核心挑战之一：涉及多个子目标、长时间跨度、因果依赖和世界状态变化的复杂任务。与短视程反射式控制不同，长程推理需要在动作之前或之中进行意图识别、序列规划和错误恢复。

## 为什么需要独立的任务规划层

现代机器人架构正在从单一的端到端神经网络向**分层架构**迁移：

```
用户指令 → 任务规划划器 (Task Planner) → 技能库 (Skill Library) → 低层策略 (VLA/Controller) → 动作执行
```

**分层的好处:**
- **模块化**：新任务无需重新训练整个网络，只需组合现有技能
- **可解释性**：每个中间步骤都可以被人类检查和干预
- **故障恢复**：当某个技能失败时，规划器可以重新规划而不是僵死
- **跨本体迁移**：技能库中的原子动作可以在不同机器人平台间共享

## 历史脉络

### 阶段1: LLM 作为高层规划器 (2022-2023)

**典范: SayCan (Google, 2022)**
- 核心思想: LLM 提供语义规划，但每个提议的可行性由低层策略评估
- 关键论文: *Do As I Can, Not As I Say* (Google Robotics, RSS 2022)
- 影响: 开创了 LLM+机器人的经典范式

**典范: Inner Monologue (2023)**
- 核心思想: 机器人在执行过程中持续"内心独白"，根据环境反馈动态调整规划
- 关键论文: *Inner Monologue: Embodied Reasoning through Planning with Language Models*

### 阶段2: 代码作为策略 (2022-2023)

**典范: Code as Policies (Google, 2022)**
- 核心思想: LLM 生成 Python 代码作为机器人策略，代码可以调用预定义的控制原语
- 优势: 生成的代码是确定性的、可解释的、可复用的
- 开源: 多个社区实现

**典范: VoxPoser (Stanford, 2023)**
- 核心思想: LLM 提取约束条件，VLM 生成体素 (voxel) 级别的复杂值场 (cost map)，使用运动规划 (MP) 生成路径
- 开源: [huangwl18/VoxPoser](https://github.com/huangwl18/VoxPoser) (804 ⭐)
- 特点: 无需训练，几乎零样本适应新任务

**典范: LLM+P / LLM+MAP**
- 核心思想: 将 LLM 与经典规划器（如 PDDL planner）结合，LLM 负责理解自然语言，经典规划器负责最优解搜索
- 优势: 保证规划的完备性和最优性

### 阶段3: 反思与自我纠正 (2023-2024)

**典范: Reflect-VLM**
- 核心思想: 机器人在执行失败后进行"反思"，分析失败原因，调整后续规划
- 与 [embodied-brain](embodied-brain.md) 中的反事实思维概念相呼应

### 阶段4: 多智能体协同规划 (2024+)

**典范: SMART-LLM**
- 核心思想: 多机器人协同任务规划，LLM 担任协调器，分配子任务给不同机器人
- 开源: [SMARTlab-Purdue/SMART-LLM](https://github.com/SMARTlab-Purdue/SMART-LLM) (191 ⭐)

## 长程任务推理问题定义

**短视程 vs 长程:**
- 短视程: "抓起红色方块" — 单一动作，即时反射
- 长程: "做一顿正餐" — 需要切菜→炒菜→盛盘→清理，每步都依赖前一步的状态

**核心难点:**
1. 组合爆炸: 子任务的排列组合随长度指数增长
2. 中间状态不确定性: 动作失败后需要重新规划
3. 目标层次化: 高层意图 (煮饭) 如何分解为低层动作 (打开炉火)
4. 因果推理: "如果先切菜再洗菜，菜会不新鲜"

## 技术路线

### 技能表示 (Skill Representation)

技能是任务规划的基本构建块。常见的技能表示方式：

| 表示方式 | 特点 | 代表 |
|---------|------|------|
| **符号动作 (Symbolic Actions)** | 离散、可解释，适合 LLM 生成 | PDDL, Code as Policy |
| **密度动作 (Dense Actions)** | 连续、端到端，适合 VLA 执行 | Diffusion Policy, Flow Matching |
| **技能嵌入 (Skill Embeddings)** | 向量空间中的连续表示，支持插值 | SkillGPT, CALVIN |

### 技能发现 (Skill Discovery)

从未标注数据中自动发现原子技能。

- **CALVIN Benchmark**：提供长程、多技能的操作任务，测试机器人的技能组合能力
- **Large Behavior Models (LBM)**：在大量仿真数据上预训练，自然而然地学习技能分解和组合
- **AutoRT / RoboAgent**：自主探索并发现可复用的原子行为

### 技能组合 (Skill Composition)

将已有技能组合成复杂任务。

- **顺序组合**: 技能 A → 技能 B → 技能 C（如"打开冰箱→取出牛奶→倒入杯中"）
- **并行组合**: 多个技能同时执行（如一只手打开盖子，另一只手拿住容器）
- **嵌套组合**: 技能中调用其他技能（如"煮饭"中调用"切菜"、"炒菜"、"装盘"）

## 关键开源项目

**规划框架:**
- [VoxPoser](https://github.com/huangwl18/VoxPoser) (804 ⭐) — LLM+VLM 生成体素级复杂值场
- [SMART-LLM](https://github.com/SMARTlab-Purdue/SMART-LLM) (191 ⭐) — 多机器人 LLM 协同规划
- [TypeFly](https://github.com/typefly/TypeFly) (104 ⭐) — 基于 LLM 的机器人任务规划框架
- [AutoTAMP](https://github.com/yongchao98/AutoTAMP) (75 ⭐) — 增强 LLM/VLM 任务与运动规划
- [kios](https://github.com/ProNeverFake/kios) (78 ⭐) — 知识驱动的灵活任务规划

**技能学习:**
- [LIBERO](https://github.com/Lifelong-Robot-Learning/LIBERO) (1821 ⭐) — 终身机器人学习基准
- [BEHAVIOR-1K](https://github.com/StanfordVL/BEHAVIOR-1K) (1457 ⭐) — 室内复杂长程任务

**长程任务策略:**
- [Reflect-VLM](https://github.com/yunhaif/reflect-vlm) (174 ⭐) — 反思式多阶段规划，执行失败后分析原因并调整
- [Plan-Seq-Learn](https://github.com/mihdalal/planseqlearn) (127 ⭐, ICLR'24) — LLM 引导长程 RL 解决复杂任务
- [Action-Sketcher](https://github.com/FlagOpen/Action-Sketcher) (48 ⭐, CVPR'26) — 通过视觉草图从推理到动作
- [BUDS](https://github.com/UT-Austin-RPL/BUDS) (57 ⭐) — 从未分段示教中自底向上发现技能
- [Skill-Chaining](https://github.com/clvrai/skill-chaining) (36 ⭐, CoRL'21) — 对抗技能链接用于长程操作
- [PRoC3S](https://github.com/Learning-and-Intelligent-Systems/proc3s) (31 ⭐, CoRL'24) — LLM + 约束满足解决长程问题
- [myGym](https://github.com/incognite-lab/myGym) (53 ⭐) — 无代码生成多步长程任务

## 核心挑战

1. **幻觉问题 (Hallucination)**：LLM 可能生成在物理上不可行的规划（如"穿过一堵墙"）
2. **物理基定 (Physical Grounding)**：语言级规划如何确保每个子目标都能被低层策略实际执行
3. **技能库建设**：如何自动发现、命名、组织和维护大规模技能库
4. **失败恢复**：当某个技能失败时，如何快速识别问题并重新规划
5. **时效性**：LLM 生成规划的延迟较高，难以满足实时操作需求
6. **评估难题**: 仅看最终成功率会忽略中间过程的推理质量
7. **中间目标表示**: 如何让机器人自主发现或表示合适的中间目标？
8. **错误恢复**: 失败后回退 vs 绕过的判断

## 与其他概念的关系

- 与 [vla-vision-language-action](vla-vision-language-action.md) 的关系: 任务规划是 VLA 的"大脑"，VLA 是任务规划的"小脑"和"手"
- 与 [embodied-brain](embodied-brain.md) 的关系: 具身大脑是更广义的认知架构，任务规划是其中的执行控制层，长程推理是其核心能力之一
- 与 [world-model-robotics](world-model-robotics.md) 的关系: 世界模型为规划提供"内心模拟"，用于预测动作后果
- 与 [cross-embodiment](cross-embodiment.md) 的关系: 技能库的跨本体共享是实现通用机器人的关键

## 参见

- [vla-vision-language-action](vla-vision-language-action.md) — 视觉-语言-动作统一架构
- [embodied-brain](embodied-brain.md) — 具身大脑架构
- [world-model-robotics](world-model-robotics.md) — 世界模型
- [cross-embodiment](cross-embodiment.md) — 跨本体学习

## 最新研究动态 (2026-05-04 ~ 2026-05-11)

本周追踪到 2 篇任务规划与技能组合相关新论文，核心趋势是：**时序逻辑与 LLM 融合**、**视感运动技能组合**。

- **Melding LLM and temporal logic for reliable human-swarm collaboration in complex scenarios** (Junfeng Chen et al., 2026-05-08) — 将 LLM 与时序逻辑 (LTL) 融合，实现复杂场景下可靠的人-群体协作任务规划，支持验证和干预机制。[arXiv:2605.07877](https://arxiv.org/abs/2605.07877)
- **BrickCraft: Visuomotor Skill Composition with Situated Manual Guidance for Long-Horizon Interlocking Brick Assembly** (Jichuan Yu et al., 2026-05-08) — 面向长程互锁积木拼装的视感运动技能组合框架，通过位置化手动指导实现长程任务推理与细粒度操作的无缝整合。[arXiv:2605.07605](https://arxiv.org/abs/2605.07605)