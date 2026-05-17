---
title: Robotics Technical Factions
created: 2026-05-11
updated: 2026-05-11
type: concept
tags: [technical-factions, end-to-end, hierarchical-control, platform-ai, infrastructure, architecture]
sources: []
confidence: high
---

# 机器人技术分派 (Robotics Technical Factions)

> 具身智能领域没有"唯一正确"的技术路线。当前 industry 和 academia 围绕"感知→决策→控制"这条链路上多大程度交给神经网络、多大程度保留传统工程，形成了四大派别。理解这些分派的本质差异，是判断公司技术路线选择优劣的关键。

---

## 1. 端到端派 (End-to-End)

**核心信念**：*"梯度从控制直接流向感知，全局最优"*

**代表公司**：[figure-ai](../entities/figure-ai.md)、[tesla-optimus](../entities/tesla-optimus.md)、[physical-intelligence](../entities/physical-intelligence.md)、[1x-technologies](../entities/1x-technologies.md)

### 架构特点

```
摄像头/IMU/力矩传感器 → [单一神经网络] → 关节力矩/电机指令
```

- 用**单一神经网络**替代传统机器人学的感知→规划→控制分层
- 输入原始传感器数据，直接输出低层控制信号
- **拒绝**行为树、状态机、HTN 等人工编写的中间层
- Tesla 将 FSD 自动驾驶神经网络直接"移植"到机器人上
- Physical Intelligence 的 π⁰ 用 Flow Matching 生成连续动作，跨本体通用

### 优势

| 优势 | 说明 |
|------|------|
| **可扩展性强** | 数据越多性能越好，长尾场景自然泛化 |
| **性能上限高** | 避免了人工设计中间表示带来的信息损失 |
| **统一优化** | 感知、规划、控制联合优化，不存在层间接口次优问题 |
| **语言原生** | VLA 架构天然支持自然语言指令，无需额外翻译层 |

### 劣势

| 劣势 | 说明 |
|------|------|
| **黑箱难调试** | 出了问题很难定位是感知错了、规划错了还是控制错了 |
| **安全验证困难** | 无法像 MPC 那样进行形式化安全证明 |
| **数据饥渴** | 需要海量真实世界数据（Tesla 靠百万辆车，Figure 靠 BotQ） |
| **冷启动困难** | 初期没有数据时性能极差，需要大量仿真预训练 |

### 关键门槛

**数据飞轮规模**决定了端到端派的生死：
- Tesla：数百万辆车 + 数千台机器人，数据飞轮全球第一
- Figure AI：BotQ 自主数据生成系统，自研制造闭环
- Physical Intelligence：开源策略，依赖社区数据贡献

---

## 2. 分层混合派 (Hierarchical / Hybrid)

**核心信念**：*"MPC/传统控制提供可信赖基础，学习补充边缘能力"*

**代表公司**：[boston-dynamics](../entities/boston-dynamics.md)、[agility-robotics](../entities/agility-robotics.md)

### 架构特点

```
传感器 → [感知层] → [规划层: 行为树/状态机] → [控制层: MPC/ZMP] → 执行器
                    ↓
              [学习模块: Diffusion/RL] ← 语言指令
```

- **底层**：传统控制理论（MPC、ZMP、LIPM）保证稳定和安全性
- **中层**：行为树/状态机管理任务状态切换和异常处理
- **上层**：学习模块（如 Diffusion Transformer）负责灵巧操作等复杂技能
- Boston Dynamics Atlas：行走用 MPC+RL 混合，操作引入 450M 参数 Diffusion Transformer
- Agility Digit：LIPM+ZMP+MPC 三层递阶，预定义步态库 + 在线优化

### 优势

| 优势 | 说明 |
|------|------|
| **可解释、可调试** | 每层输入输出明确，出问题知道在哪一层 |
| **安全性高** | 底层控制有理论保证，不会突然摔倒 |
| **数据需求低** | 不需要像端到端那样海量数据 |
| **工程成熟** | 30+ 年控制理论的积累，工业级可靠性 |

### 劣势

| 劣势 | 说明 |
|------|------|
| **各层接口次优** | 感知层给规划层的信息可能不是最优表示 |
| **新场景处理难** | 遇到行为树没覆盖的情况会僵住 |
| **泛化天花板低** | 分层接口限制了信息流通 |
| **语言理解弱** | 自然语言需人工翻译为符号状态，损耗大 |

### 一个有趣的"叛逃"

Boston Dynamics 正在从"纯分层"向"混合"过渡：
- **行走**：仍坚守 MPC+RL 分层（不能倒）
- **操作**：已引入 **450M 参数的 Diffusion Transformer**（端到端）

这说明行业正在走向**"分层为底、端到端为顶"**的融合架构。

---

## 3. 平台 + 合作 AI 派 (Platform + Partner AI)

**核心信念**：*"硬件自研，AI 借力最强合作伙伴"*

**代表公司**：[apptronik](../entities/apptronik.md)、[enchanted-tools](../entities/enchanted-tools.md)

### 架构特点

```
语言指令 → [合作伙伴 LLM/VLA: Gemini 等] → [标准化接口/API] → [自研硬件控制] → 执行器
```

- 自己造机器人本体（执行器、机械结构、传感器集成）
- AI 大脑交给外部合作伙伴（Apptronik 用 Google Gemini）
- 通过标准化接口（如 ROS 2、GRPC）将合作伙伴的 AI 输出映射到硬件控制
- 专注硬件设计差异化：轻量化、模块化、成本控制

### 优势

| 优势 | 说明 |
|------|------|
| **AI 能力起点高** | 不需要从零训练大模型，快速获得语言理解和推理能力 |
| **专注硬件** | 资源投入在执行器设计、供应链、制造工艺 |
| **快速上市** | 跳过模型训练阶段，缩短产品周期 |

### 劣势

| 劣势 | 说明 |
|------|------|
| **对合作伙伴依赖高** | API 变更、价格调整、服务中断直接影响产品 |
| **自主 AI 护城河浅** | 竞争对手也可以用同样的外部 AI |
| **数据飞轮断裂** | 无法获取用户交互数据来迭代自有模型 |
| **定制化受限** | 合作伙伴的通用模型可能不适合特定场景 |

### 关键变量

这派公司的长期竞争力取决于：**能否在借力外部 AI 的同时，逐步构建自有 AI 能力**。Apptronik 已经开始测试 Gemini 之外的自研方案，但进展未知。

---

## 4. 基础设施派 (Infrastructure / "卖铲人")

**核心信念**：*"提供训练+仿真+部署全栈，不造机器人"*

**代表公司**：[nvidia-isaac](../entities/nvidia-isaac.md)、[google-deepmind](../entities/google-deepmind.md)

### 架构特点

- **不造终端机器人硬件**，也不直接面向消费者
- 提供仿真器（Isaac Sim/Lab）、训练框架（GR00T）、芯片（Jetson Thor）
- 提供数据集（Open X-Embodiment）、基础模型（RT-2、Gemini Robotics）
- 服务于其他三派公司，做"卖铲子的人"

### 优势

| 优势 | 说明 |
|------|------|
| **生态绑定深** | 所有机器人都需要仿真和训练基础设施 |
| **零机器人风险** | 不需要担心硬件召回、安全事故、供应链 |
| **规模效应** | 越多的公司用你的工具，你的数据和模型越强 |
| **标准制定者** | 定义数据格式、接口协议、评估基准 |

### 劣势

| 劣势 | 说明 |
|------|------|
| **不控制终端场景** | 无法直接获取真实世界的反馈数据 |
| **GR00T 待验证** | NVIDIA 自家的通用机器人模型尚未被大规模验证 |
| **竞争边界模糊** | 客户可能担心你未来进入终端市场 |
| **开源压力** | 社区开源工具（如 Genesis、LeRobot）可能侵蚀商业空间 |

---

## 四大派别本质对比

| 维度 | 端到端派 | 分层混合派 | 平台+合作AI | 基础设施派 |
|------|---------|-----------|------------|-----------|
| **谁写控制逻辑** | 神经网络学出来 | 工程师写 MPC/行为树 | 合作伙伴写 | 提供工具让别人写 |
| **数据需求** | 极大 | 中等 | 低 | 不直接需数据 |
| **可解释性** | 低（黑箱） | 高（白盒） | 中 | — |
| **安全性保证** | 统计保证 | 形式化/理论保证 | 依赖合作伙伴 | — |
| **长尾泛化** | 强 | 弱 | 中等 | — |
| **核心资产** | 数据飞轮 + 模型 | 控制算法 + 工程经验 | 硬件设计 + 供应链 | 生态 + GPU 垄断 |
| **护城河深度** | 深（数据壁垒） | 中（工程 know-how） | 浅（可替代） | 极深（生态锁定） |
| **典型风险** | 数据不够、黑箱事故 | 泛化瓶颈、人才断层 | 合作伙伴变心 | 开源替代、反垄断 |

---

## 历史演进与融合趋势

### Phase 1: 传统控制时代 (1990s-2015)
- Boston Dynamics 统治足式机器人
- 分层控制是唯一选择
- 学习仅用于感知（CNN 图像分类）

### Phase 2: 学习入侵 (2015-2022)
- RL 进入底层控制（ Isaac Gym、MPC+RL 混合）
- Google DeepMind 提出 QT-Opt、BC-Z
- 分层架构开始学习化

### Phase 3: VLA 革命 (2022-2024)
- RT-2 证明大模型可以直接输出动作
- Figure、Tesla、PI 押注端到端
- 行业出现路线之争

### Phase 4: 务实融合 (2024-)
- **Boston Dynamics**：行走保持分层，操作引入端到端
- **Tesla**：端到端为主体，但保留安全监控层
- **Apptronik**：外部 AI 快速起步，暗中自研
- 共识：**没有完美的单一架构，只有适合场景的组合**

---

## 如何根据场景选择派别

| 场景 | 推荐派别 | 理由 |
|------|---------|------|
| 工厂重复作业 | 分层混合 | 可靠性第一，场景固定 |
| 家庭通用服务 | 端到端 | 场景开放，需要强泛化 |
| 快速原型/MVP | 平台+合作AI | 最快上市，验证市场 |
| 学术研究 | 端到端 or 基础设施 | 探索上限 or 复用工具 |
| 物流仓储 | 分层混合 or 端到端 | Agility 证明分层可行，Figure 证明端到端也行 |

---

## 与相关概念的关系

- 与 [vla-vision-language-action](vla-vision-language-action.md) 的关系: 端到端派的核心技术载体就是 VLA
- 与 [sim-to-real](sim-to-real.md) 的关系: 端到端派极度依赖仿真预训练 + sim-to-real 迁移
- 与 [humanoid-robot](humanoid-robot.md) 的关系: 人形运动控制的分层 vs 端到端之争
- 与 [end-to-end-robotics](end-to-end-robotics.md) 的关系: 端到端派的专门概念页
- 与 [reinforcement-learning-robotics](reinforcement-learning-robotics.md) 的关系: 分层混合派用 RL 增强特定层
- 与 [data-flywheel-robotics](data-flywheel-robotics.md) 的关系: 端到端派的数据飞轮规模决定生死

## 参见

- [end-to-end-robotics](end-to-end-robotics.md) — 端到端架构详解
- [humanoid-robot](humanoid-robot.md) — 人形机器人技术分派概览
- [vla-architecture-comparison](../comparisons/vla-architecture-comparison.md) — 11 家公司 VLA 架构对比
- [data-strategy-comparison](../comparisons/data-strategy-comparison.md) — 数据策略对比
