---
title: 具身智能研究方向全景图
created: 2026-05-11
updated: 2026-05-11
type: concept
tags: [survey, embodiment, robotics, benchmark, model, world-model, sim-to-real]
sources: [raw/articles/github-embodied-ai-projects-2026-05-11.md]
confidence: high
---

# 具身智能研究方向全景图

> 基于 GitHub 开源生态、顶会论文与产业实践，将具身智能 (Embodied AI) 拆解为 15 个可投入的研究方向。每个方向附关键项目、核心问题与开放性问题。

---

## 0. 产业领军者与商业公司 (Industry Leaders)

> 商业公司以产品化为目标，它们的技术选择、数据飞轮和市场定位往往比学术研究提前 2-5 年反映出领域的真实需求。学术研究者可以通过分析公司的技术分派和数据策略来发现真正有缺口的问题。

**核心技术栈**

| 公司 | 产品/代码 | 技术分派 | 关键特征 |
|------|-----------|---------|---------|
| [figure-ai](../entities/figure-ai.md) | Helix VLA + BotQ 制造 | 端到端神经网络 | 自研制造+强大数据飞轮 |
| [tesla-optimus](../entities/tesla-optimus.md) | Optimus | 端到端神经网络 | FSD 移植，视觉主导，规模第一 |
| [boston-dynamics](../entities/boston-dynamics.md) | Atlas / Spot / Stretch | 分层混合架构 | 足式运动+操作，传感器丰富 |
| [1x-technologies](../entities/1x-technologies.md) | NEO | 筋膜驱动+世界模型 | 家用场景，柔性安全交互 |
| [physical-intelligence](../entities/physical-intelligence.md) | π⁰ / π⁰.7 | Flow Matching + 跨本体 | 通用策略，完全开源 |
| [google-deepmind](../entities/google-deepmind.md) | RT-2 / Gemini Robotics | VLA + 大模型 | 算法基础研究+知识贡献 |
| [nvidia-isaac](../entities/nvidia-isaac.md) | Isaac Sim/Lab + GR00T | 仿真基础设施 | 卖铲人，生态清道统一 |
| [unitree](../entities/unitree.md) | G1 / H1 | 传统控制+学习 | 极致性价比 ($13,500) |
| [agility-robotics](../entities/agility-robotics.md) | Digit | 分层控制 LIPM+ZMP+MPC | 物流仓储专用 |
| [apptronik](../entities/apptronik.md) | Apollo | 硬件+合作 AI | 通用平台，Google Gemini |
| [enchanted-tools](../entities/enchanted-tools.md) | Miroki | 服务/社交场景 | Pepper/Nao 原班人马 |
| [genesis-ai](../entities/genesis-ai.md) | GENE-26.5 | 声称 Human-Level | 信息稀缺，待验证 |

**公司分类**

- **端到端神经网络**: Figure AI, Tesla, Apptronik
- **分层控制**: Boston Dynamics, Agility Robotics
- **通用策略开源**: Physical Intelligence (Open Source)
- **平台+合作AI**: Apptronik, Enchanted Tools
- **极致性价比**: Unitree, Enchanted Tools
- **家用/柔性交互**: 1X Technologies, Enchanted Tools
- **物流/工业**: Agility Robotics

> 具体技术分派的差异分析见：[robotics-technical-factions](robotics-technical-factions.md)

**产业核心问题**
- 数据飞轮闭环: 部署 → 采集 → 训练 → 再部署 如何打通？
- 安全等级: 微软和 ISO 安全认证标准如何应用于 AI 驱动的机器人？
- 成本与可靠性: 元件效率、维修性、MTBF 如何达到工业级？
- 法规与责任: 放开操作权限、敏感数据收集、事故追溯

---

---

## 1. 物理仿真器与数字孪生 (Physics Simulators)

**为什么重要:** 具身智能的"训练场"。仿真器的保真度、速度、可扩展性直接决定了策略的上限。

**关键项目:**
- [genesis-world](../entities/genesis-world.md) — 生成式世界，支持差分运算与大规模并行 (28.7k ⭐)
- [nvidia-isaac](../entities/nvidia-isaac.md) / [IsaacLab](https://github.com/isaac-sim/IsaacLab) — GPU加速，企业级训练框架 (7.1k ⭐)
- [Habitat](https://github.com/facebookresearch/habitat-sim) — Meta 开源，偏重室内导航与任务 (3.7k ⭐)
- [SAPIEN](https://github.com/haosulab/SAPIEN) / [BEHAVIOR-1K](https://github.com/StanfordVL/BEHAVIOR-1K) / [Holodeck](https://github.com/allenai/Holodeck) / [RoboVerse](https://github.com/RoboVerseOrg/RoboVerse)

**核心问题:**
- 差分仿真 vs 零差分仿真：[Genesis](https://github.com/Genesis-Embodied-AI/Genesis) 用可微分物理引擎，支持梯度优化，但稳定性如何？
- 扩散性：如何从单一 GPU 扩展到上万节点的集群训练？
- 多物理引擎联合：刚体、液体、气体、软体的统一仿真
- 仿真-to-真实 (Sim2Real Gap) 的量化评估

**可研究细分:** 差分碰撞检测、GPU内存优化、大规模并行训练架构、真实物理引擎小身体迁移

---

## 2. 数据集与数据引擎 (Data Engines)

**为什么重要:** 机器人学习的"石油"。目前的瓶颈不是算法，而是高质量、多样化、可扩展的数据。

**关键项目:**
- [lerobot](../entities/lerobot.md) — HuggingFace 端到端数据管理与训练 (23.9k ⭐)
- [Open X-Embodiment](https://github.com/google-deepmind/open_x_embodiment) — 跨本体大规模数据集 (Google DeepMind, 1.8k ⭐)
- [GigaWorld-0](https://github.com/open-gigaai/giga-world-0) — 世界模型作为数据引擎
- [forge](https://github.com/arpitg1304/forge) — 数据集格式转换与可视化

**核心问题:**
- 跨本体数据融合：不同机器人、不同传感器配置的数据如何统一表示？
- 数据质量 vs 规模：大规模低质量数据是否有用？如何筛选/重新采样？
- 合成数据：基于仿真器/世界模型生成无限数据，如何避免域差异？
- 遥操作效率：如何降低人类采集成本？半自主、伪标签、视频到任务 (video2tasks)

**可研究细分:** 数据集格式标准化、自动质量评分、视频理解生成机器人操作、自动数据增强

---

## 3. VLA (Vision-Language-Action) 模型架构

**为什么重要:** 当前最热门的通用机器人策略范式，尝试用单一大模型将视觉+语言理解映射到动作。

**关键项目/模型:**
- [vla-vision-language-action](vla-vision-language-action.md) — 已有概念页面，包含 RT-2/Helix/ππ-X
- [OpenVLA](https://github.com/openvla/openvla) / [SpatialVLA](https://github.com/SpatialVLA/SpatialVLA) (RSS'25) / [NaVILA](https://github.com/AnjieCheng/NaVILA) (腿式导航, RSS'25)
- [CogACT](https://github.com/microsoft/CogACT) (Microsoft) / [InternVLA-M1](https://github.com/InternRobotics/InternVLA-M1) / [VITRA](https://github.com/microsoft/VITRA) (ICRA'26)
- [VLAC](https://github.com/InternRobotics/VLAC) (强化学习细调) / [MemoryVLA](https://github.com/shihao1895/MemoryVLA) (ICLR'26) / [ReconVLA](https://github.com/OpenHelix-Team/ReconVLA)
- [BitVLA](https://github.com/ustcwhy/BitVLA) (1-bit 量化) / [GreenVLA](https://github.com/greenvla/GreenVLA) (分阶段)

**核心问题:**
- 动作表示: 离散 token vs 连续向量 vs Diffusion/Flow Matching
- 空间理解: 大多数 VLA 缺乏 3D 空间感知，[SpatialVLA](https://github.com/SpatialVLA/SpatialVLA) 等尝试补充
- 长程规划: VLA 通常是短视程反射，如何做到多步骤规划？
- 计算效率: 如何在边缘设备上实时运行高频控制 (BitVLA 等)
- 安全对齐: 机器人 VLA 的对齐问题比文本 LLM 更危险

**可研究细分:** 动作 token 化方案、空间增强注意力、VLA+记忆、量化压缩与部署

---

## 4. 世界模型 (World Models for Robotics)

**为什么重要:** 让机器人"在脑子里想"，预测未来观察与奖励，是长程规划与安全决策的基础。

**关键项目:**
- [world-model-robotics](world-model-robotics.md) — 已有概念页面
- [GigaWorld-0](https://github.com/open-gigaai/giga-world-0) — 世界模型作为数据引擎
- 1xgpt — 1X Technologies 世界建模挑战
- Awesome-World-Models (1.6k ⭐)

**核心问题:**
- 视频生成 vs 状态预测: Sora/Veo 风格的视频预测是否必要？
- 交互式世界模型: 机器人动作如何反馈到世界状态？iVideoGPT 等
- 物理一致性: 生成的未来是否遵循物理定律？
- 多时间尺度: 短期精确预测 + 长期意图理解

**可研究细分:** 视频世界模型架构、交互式预测、物理先验知识嵌入

---

## 5. 动作生成: Diffusion / Flow Matching / Transformer

**为什么重要:** VLA 的动作头通常用离散 token 或连续向量，但这些生成式方法能生成更平滑、更符合物理的高频动作。

**关键项目:**
- [flow-matching](flow-matching.md) — 已有概念页面，Physical Intelligence 使用
- [Diffusion Policy](https://github.com/lucidrains/diffusion-policy) — Toyota Research，开启方法论 (135 ⭐)
- [HDP](https://github.com/dyson-ai/hdp) — 层级Diffusion多任务 (CVPR'24)
- [ManiCM](https://github.com/ManiCM-fast/ManiCM) — 实时3D Diffusion via Consistency Model
- Multitask DiT Policy — Boston Dynamics Atlas 同款架构
- [DARE](https://github.com/marmotlab/DARE) — Diffusion探索 (ICRA'25)

**核心问题:**
- 快速采样: Diffusion 需要多步去噪，如何实时控制？Consistency Model / Flow Matching
- 3D 空间动作: 如何在 3D 空间中表示和生成操作轨迹？
- 多任务泛化: 单一策略如何切换不同操作技能？

**可研究细分:** 快速推理、3D动作表示、多任务条件融合

---

## 6. Sim2Real 迁移与域适应

**为什么重要:** 在仿真中训练的策略如何无缝迁移到真实硬件，是机器人学习的"圣杯"。

**关键项目:**
- [sim-to-real](sim-to-real.md) — 已有概念页面
- [PACE](https://github.com/leggedrobotics/pace-sim2real) — ETHZ 系统性Sim2Real，识别执行器动力学 (470 ⭐)
- [humanoid-gym](https://github.com/roboterax/humanoid-gym) — 零样本人形Sim2Real (2.0k ⭐)
- [AwesomeSim2Real](https://github.com/LongchaoDa/AwesomeSim2Real) — 综述资源
- [DexPoint](https://github.com/yzqin/dexpoint-release) — 点云RL Sim2Real灵巧操作

**核心问题:**
- 执行器建模: 如何准确识别真实电机/减速器的动力学参数？
- 域随机化 (Domain Randomization) 的边界: 随机化多少算够？
- 残差策略 (Residual Policy): 在仿真策略上叠加小型真实世界补偿
- 触觉 sim2real: 触觉传感器的仿真难度远高于视觉

**可研究细分:** 执行器系统识别、域随机化策略、在线适应学习 (online adaptation)

---

## 7. 人形机器人运动与全身控制 (Humanoid Locomotion & Whole-Body Control)

**为什么重要:** 人形是最通用的物理形态，也是最难控制的。全身协调涉及移动、操作、平衡的统一。

**关键项目:**
- [humanoid-robot](humanoid-robot.md) — 已有概念页面
- [GMR](https://github.com/YanjieZe/GMR) — 通用运动重定向，人类动作到多种人形 (ICRA'26)
- [ProtoMotions](https://github.com/NVlabs/ProtoMotions) — NVlabs GPU加速数字人/人形仿真 (1.7k ⭐)
- [Dial-MPC](https://github.com/LeCAR-Lab/dial-mpc) — 拓散退火采样MPC (966 ⭐)
- [video2robot](https://github.com/AIM-Intelligence/video2robot) — 视频生成人形运动
- [rl_sar](https://github.com/fan-ziqi/rl_sar) — 足式/轮式/人形 RL 部署

**核心问题:**
- 运动重定向: 如何将人类视频运动迁移到不同结构的人形？
- 全身控制: 手臂操作 + 腿部移动 + 驱干平衡的联合优化
- 接触力控制 (Torque-Level Control): 直接输出关节力矩
- 外界干扰: 不平整地形、被推搓、承载变化

**可研究细分:** 运动重定向算法、全身MPC/强化学习混合、视频模仿学习、多接触点力控制

---

## 8. 开源硬件与低成本平台

**为什么重要:** 降低具身智能研究的硬件门槛，让学术界和爱好者能在实物上验证算法。

**关键项目:**
- [OpenArm](https://github.com/OpenArm/) (2.4k ⭐) — 全开源人形手臂
- Roboto_origin (1.7k ⭐) — 手搓级人形机器人
- HOPEJr (793 ⭐) — 开源灵巧手人形
- [Zeroth-Bot](https://github.com/zeroth-bot) (763 ⭐) — 3D打印，Sim2Real+RL
- Asimov v0/v1 — 开源人形
- Poppy Humanoid (898 ⭐) — 研究/教育用

**核心问题:**
- 成本: 如何在 <$3,000 内构建完整人形？
- 灵巧手: 低成本执行器如何实现精细操作？
- 开放标准: URDF/MJCF 描述的统一与兼容性
- 通用接口: 如何让同一策略跑在不同硬件上？

**可研究细分:** 设计优化、执行器选型、低成本感知、开放控制框架

---

## 9. 基准测试与评估 (Benchmarks)

**为什么重要:** 基准测试是领域的"度量衡"。没有好的基准，就无法区分真进步还是过拟合。当前基准已从单一任务演进到长程组合、跨本体泛化、因果推理和终身学习。

**关键项目:**
- **操作技能**: [ManiSkill](https://github.com/haosulab/ManiSkill) (2860 ⭐), [robosuite](https://github.com/ARISE-Initiative/robosuite) (2405 ⭐), [MetaWorld](https://github.com/Farama-Foundation/Metaworld) (1814 ⭐), [LIBERO](https://github.com/Lifelong-Robot-Learning/LIBERO) (1821 ⭐), [SoftGym](https://github.com/Xingyu-Lin/softgym) (339 ⭐), [FluidLab](https://github.com/zhouxian/FluidLab) (243 ⭐), [CausalWorld](https://github.com/rr-learning/CausalWorld) (242 ⭐), [GarmentLab](https://github.com/GarmentLab/GarmentLab) (161 ⭐)
- **长程任务**: [CALVIN](https://github.com/mees/calvin) (910 ⭐), [BEHAVIOR-1K](https://github.com/StanfordVL/BEHAVIOR-1K) (1457 ⭐), [cap-x](https://github.com/capgym/cap-x) (480 ⭐)
- **多智能体/协作**: [RoboTwin](https://github.com/RoboTwin-Platform/RoboTwin) (2299 ⭐), [VMAS](https://github.com/proroklab/VectorizedMultiAgentSimulator) (565 ⭐), [PARTNR](https://github.com/facebookresearch/partnr-planner) (368 ⭐)
- **跨本体/统一评估**: [RoboVerse](https://github.com/RoboVerseOrg/RoboVerse) (1737 ⭐), [VLA-Eval-Harness](https://github.com/allenai/vla-evaluation-harness) (280 ⭐), [LW-BenchHub](https://github.com/LightwheelAI/LW-BenchHub) (146 ⭐)
- **特殊领域**: [EvoGym](https://github.com/EvolutionGym/evogym) (252 ⭐, 软体机器人), [bigym](https://github.com/NeuracoreAI/bigym) (221 ⭐, 移动双臂), [mshab](https://github.com/arth-shukla/mshab) (190 ⭐, 家庭重排)

**核心问题:**
- 基准过拟合: 模型在基准上好，真实世界失效
- 评估指标单一: 大多数只看成功率，忽略推理过程和恢复能力
- 跨基准可比性: 不同仿真器、动作空间如何公平比较
- VLA 评估困境: 连续动作输出需要新的评估框架
- 具身大脑缺乏基准: 记忆、反事实思维、情感等认知能力几乎无人测试
- 通用性评估: 如何评价策略在未见过的机器人/任务上的表现？

**可研究细分:** 基准设计理论、跨基准比较方法、连续动作评估、真实世界验证协议、跨本体泛化性指标

---

## 10. 可微分机器人学与基础工具 (Differentiable Robotics)

**为什么重要:** 让物理、几何、运动学都可微分，支持端到端梯度优化。

**关键项目:**
- [pypose](https://github.com/pypose/pypose) (1.5k ⭐) — 流形上可微分机器人学
- [NVIDIA warp](https://github.com/NVIDIA/warp) (6.6k ⭐) — GPU加速可微分仿真
- [robot-descriptions](https://github.com/robot-descriptions/robot_descriptions.py) (1.5k ⭐) — 标准化URDF/MJCF

**核心问题:**
- 梯度流经物理引擎：如何让碰撞检测、接触力解算都可微分？
- 流形优化: 旋转、姿态在流形上的优化

**可研究细分:** 差分几何、可微分运动学、梯度优化框架

---

## 11. 具身大脑 (Embodied Brain)

**为什么重要:** 不仅仅是"感知→动作"的反射，而是统一记忆、推理、情感、自我意识的认知架构。让机器人成为能理解上下文、从经验中学习的智能体。

**与 VLA 的区别:** VLA 解决"手怎么动"，具身大脑解决"脑子怎么想"。

**五大认知能力:**
- **[memory](memory.md)** — 四种记忆（工作/情节/语义/程序）的统一架构
- **[cognition](cognition.md)** — 因果推理、反事实思维、常识推理
- **[emotion-and-motivation](emotion-and-motivation.md)** — 情感引擎、内生奖励、人机共情
- **[consciousness](consciousness.md)** — 自我意识、身体图式、动作意图
- **[lifelong-learning](lifelong-learning.md)** — 在线学习、知识回放、灾难性遗忘的解决

**技术路线:**
- 阶段1: 外部记忆补充 (MemoryVLA, MemGPT 思想)
- 阶段2: 认知-动作协同 (CogACT, Reflect-VLM)
- 阶段3: 世界模型作为认知基座 (iVideoGPT)
- 阶段4: 统一认知架构 (CSR, MolmoAct2)
- 阶段5: 情感层与内生动机 (N.E.KO)

**关键项目:**
- [MemoryVLA](https://github.com/shihao1895/MemoryVLA) (236 ⭐, ICLR'26) — 感知-认知记忆
- [N.E.KO](https://github.com/N-E-K-O) (1066 ⭐) — 具身情感引擎
- [CogACT](https://github.com/microsoft/CogACT) (423 ⭐, Microsoft) — 认知与动作协同
- [ReconVLA](https://github.com/OpenHelix-Team/ReconVLA) (254 ⭐) — 重建式感知理解
- [CSR](https://github.com/HP-STEFAN/CSR-Paper-Implementation) — 实时认知引擎
- [MolmoAct2](https://github.com/brjathu/molmoact2) — 动作前推理优化部署
- [LIBERO](https://github.com/Lifelong-Robot-Learning/LIBERO) (1821 ⭐) — 终身机器人学习基准

**核心问题:**
- 记忆架构：工作/情节/语义/程序记忆如何统一？
- 反事实思维：失败后如何反思原因并调整策略？
- 情感与动机：情感是否是通用智能的必要组件？
- 自我意识：机器人如何建立"自己"的边界感？
- 终身可塑性：如何让每次交互都使机器人更聪明？
- 评估缺口：缺乏针对记忆、反事实思维、情感等认知能力的基准

**可研究细分:** 记忆机制、因果推理、反事实思维、情感计算、自我意识架构、终身学习

> 详见 [embodied-brain-framework-comparison](../comparisons/embodied-brain-framework-comparison.md) — 具身大脑框架对比分析

---

## 12. 任务规划与技能组合 (Task Planning & Skill Composition)

**为什么重要:** VLA 解决了"怎么做"，任务规划解决"做什么"。当用户给出高层指令时，机器人需要将其分解为可执行的子任务并调用低层策略逐一执行。长程任务推理是其核心挑战：涉及多个子目标、长时间跨度、因果依赖和世界状态变化。

**关键项目:**
- [task-planning-and-skill-composition](task-planning-and-skill-composition.md) — 已有概念页面
- [VoxPoser](https://github.com/huangwl18/VoxPoser) (804 ⭐) — LLM+VLM 生成体素级复杂值场
- [SMART-LLM](https://github.com/SMARTlab-Purdue/SMART-LLM) (191 ⭐) — 多机器人 LLM 协同规划
- [TypeFly](https://github.com/typefly/TypeFly) (104 ⭐) — 基于 LLM 的机器人任务规划框架
- [AutoTAMP](https://github.com/yongchao98/AutoTAMP) (75 ⭐) — 增强 LLM/VLM 任务与运动规划
- [LIBERO](https://github.com/Lifelong-Robot-Learning/LIBERO) (1821 ⭐) — 终身技能学习基准
- [CALVIN](https://github.com/mees/calvin) (910 ⭐) — 长程语言条件策略基准
- [BEHAVIOR-1K](https://github.com/StanfordVL/BEHAVIOR-1K) (1457 ⭐) — 1000 种室内复杂任务
- [Reflect-VLM](https://github.com/yunhaif/reflect-vlm) (174 ⭐) — 反思式多阶段规划
- [Plan-Seq-Learn](https://github.com/mihdalal/planseqlearn) (127 ⭐, ICLR'24) — LLM 引导长程 RL

**核心问题:**
- 幻觉问题: LLM 可能生成物理上不可行的规划
- 物理基定: 语言级规划如何确保每个子目标都能被低层策略实际执行
- 技能库建设: 如何自动发现、组织和维护大规模技能库
- 失败恢复: 当某个技能失败时如何快速重新规划
- 时效性: LLM 生成规划的延迟较高
- 组合爆炸: 子任务排列组合随长度指数增长
- 中间目标表示: 如何发现合适的中间目标
- 错误恢复: 失败后回退 vs 绕过的判断

**可研究细分:** 分层规划架构、技能发现与组合、LLM 物理基定、多机器人协同规划、长程任务推理

---

## 13. 灵巧操作与触觉感知 (Dexterous Manipulation & Tactile Sensing)

**为什么重要:** 人形机器人的"最后一公里"。双足让它走到目标，灵巧手让它真正与世界交互。多指协调、触觉反馈和精细力控制是实现通用操作的关键。

**关键项目:**
- [dexterous-manipulation](dexterous-manipulation.md) — 已有概念页面
- [hand_dapg](https://github.com/aravindr93/hand_dapg) (316 ⭐) — 灵巧手操作深度模仿学习
- [DexUMI](https://github.com/real-stanford/DexUMI) (213 ⭐) — 用人手作为通用操作界面
- [tactile_envs](https://github.com/carlosferrazza/tactile_envs) (96 ⭐) — 视觉+触觉 MuJoCo 环境
- [digit-design](https://github.com/facebookresearch/digit-design) (209 ⭐) — DIGIT 触觉传感器
- [gsrobotics](https://github.com/gelsightinc/gsrobotics) (185 ⭐) — GelSight 触觉传感器 SDK

**核心问题:**
- 接触富有动力学: 灵巧操作涉及大量不连续接触，难以用传统运动学模型描述
- 视觉遮挡: 手指操作时往往遮挡视觉，必须依赖触觉或本体感受
- 数据稀缺: 灵巧手的人类示范数据远比手臂操作稀缺
- 仿真到真实: 灵巧手的接触和摩擦难以精确仿真
- 维护与可靠性: 灵巧手结构复杂，故障率高于简单夹爪

**可研究细分:** 多指协调控制、触觉增强学习、视觉触觉融合、仿真到真实迁移

---

## 建议的入门路径

**如果你是算法研究者:**
1. 从仿真器入门 (IsaacLab / [Genesis](https://github.com/Genesis-Embodied-AI/Genesis) / [Habitat](https://github.com/facebookresearch/habitat-sim))
2. 接触 VLA 范式 (OpenVLA / [LeRobot](https://github.com/huggingface/lerobot) + 复现)
3. 选择一个子方向深耕 (动作生成 / Sim2Real / 世界模型 / 任务规划与技能组合 / 具身大脑 / 基准设计)

**如果你是系统工程师:**
1. 从 [LeRobot](https://github.com/huggingface/lerobot) 数据管理与部署入门
2. 接触开源硬件 (Zeroth-Bot / [OpenArm](https://github.com/OpenArm/))
3. 构建端到端部署管道

**如果你是理论研究者:**
1. 从综述论文入门 (Embodied-AI-Guide / Awesome-VLA-Robotics)
2. 找到基准中的矛盾或缺口
3. 提出新的统一框架

---

## 参见

- [physics-simulators](physics-simulators.md) — 物理仿真器与数字孪生
- [robotics-data-engines](robotics-data-engines.md) — 数据集与数据引擎
- [vla-vision-language-action](vla-vision-language-action.md) — VLA 模型架构详解
- [world-model-robotics](world-model-robotics.md) — 世界模型
- [humanoid-robot](humanoid-robot.md) — 人形机器人概览
- [cross-embodiment](cross-embodiment.md) — 跨本体学习
- [end-to-end-robotics](end-to-end-robotics.md) — 端到端架构
- [reinforcement-learning-robotics](reinforcement-learning-robotics.md) — 强化学习
- [imitation-learning-robotics](imitation-learning-robotics.md) — 模仿学习
- [sim-to-real](sim-to-real.md) — 仿真到真实迁移
- [genesis-world](../entities/genesis-world.md) — 生成式世界仿真器
- [lerobot](../entities/lerobot.md) — 端到端数据与训练框架
- [embodied-brain](embodied-brain.md) — 具身大脑
- [embodied-benchmarks](embodied-benchmarks.md) — 具身智能基准测试
- [open-hardware-robotics](open-hardware-robotics.md) — 开源硬件与低成本平台
- [differentiable-robotics](differentiable-robotics.md) — 可微分机器人学与基础工具
- [data-flywheel-robotics](data-flywheel-robotics.md) — 数据飞轮
- [dexterous-manipulation](dexterous-manipulation.md) — 灵巧操作与触觉感知
- [task-planning-and-skill-composition](task-planning-and-skill-composition.md) — 任务规划与技能组合
- [robotics-technical-factions](robotics-technical-factions.md) — 机器人技术分派：四大派别本质区别与融合趋势