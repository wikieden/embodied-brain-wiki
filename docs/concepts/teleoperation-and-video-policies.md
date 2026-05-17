---
title: Teleoperation and Video-Based Robot Policies
created: 2026-05-11
updated: 2026-05-11
type: concept
tags: [teleoperation, imitation-learning, robotics, video-policy, manipulation, data-collection, diffusion-policy]
sources: []
confidence: high
---

# Teleoperation and Video-Based Robot Policies

遥操作（Teleoperation）是具身智能数据飞轮的核心引擎，为模仿学习提供高质量示范数据。视频动作策略（Video-based Robot Policy）则以原始视觉观测为输入、直接输出机器人动作。二者共同构成现代机器人学习的数据飞轮。

---

## 1. 遥操作方法分类

### 1.1 VR / 沉浸式遥操作

| 代表工作 | 特点 |
|---------|------|
| **Open-TeleVision** (2024, CMU/UCSD) | 沉浸式主动视觉反馈，支持人形机器人全身遥操作，操作员通过头显获得第一人称视角 |
| **AnyTeleop** (2023, UCSD) | 通用视觉遥操作，支持任意机械臂-灵巧手组合，利用 VR 手柄控制末端执行器 |

**优点**：沉浸感强、单操作员可远程控制；**缺点**：VR 设备成本高、延迟敏感、长时间操作易疲劳。

### 1.2 低成本视觉遥操作

| 代表工作 | 特点 |
|---------|------|
| **ALOHA** (2023, Stanford) | 低成本双臂遥操作硬件（< $5k），通过同构主臂直接控制从臂 |
| **Mobile ALOHA** (2024, Stanford) | 在 ALOHA 基础上增加移动底盘与全身控制，实现移动操作数据采集 |
| **UMI** (2024, Stanford) | 手持式夹具 + GoPro，将人类手部操作直接迁移到机器人，无需机器人本体参与数据采集 |

**优点**：成本极低、部署快、非专家可采集；**缺点**：自由度受限（如 ALOHA 只能记录同构动作）、精度低于专业动捕。

### 1.3 动作捕捉遥操作

| 代表工作 | 特点 |
|---------|------|
| **DexCap** (2024, Columbia) | 可扩展的便携式手部动作捕捉，利用手腕佩戴摄像头和 SLAM 重建手部运动 |
| **HumanPlus** (2024, Stanford) | 通过 RGB 相机捕捉人体全身姿态，实时映射到人形机器人进行影子学习 |

**优点**：可捕捉高自由度（DoF）动作，适合人形机器人；**缺点**：传感器标定复杂、存在人与机器人形态差异（morphology gap）。

### 1.4 伪遥操作 / 仿真生成

| 代表工作 | 特点 |
|---------|------|
| **MimicGen** (NVIDIA, 2023) | 在仿真中通过少量真人示范自动生成大量变体数据 |
| **Video Imitation Learning** | 从互联网人类操作视频提取动作，实现零样本或少量样本迁移 |

**优点**：可无限扩展、无硬件磨损；**缺点**：仿真到现实的鸿沟（sim-to-real gap）、视频到动作映射歧义大。

### 1.5 自主数据采集

| 代表工作 | 特点 |
|---------|------|
| **AutoRT** (Google) | LLM 指导任务生成，机器人自主尝试并保留成功轨迹 |
| **Dobb-E** (NYU/Meta, 2024) | 利用手持设备采集少量数据后，通过自监督扩展数据集 |

**优点**：人力成本极低，可持续扩展；**缺点**：数据质量参差、需要安全机制、冷启动困难。

---

## 2. 视频动作策略核心进展

### 2.1 扩散策略（Diffusion Policy）

由 Columbia 于 2023 年提出，将机器人动作生成视为去噪扩散过程，天然支持多模态动作分布。**3D Diffusion Policy**（Columbia, 2024）引入点云/深度信息，在跨视角、跨物体泛化上显著优于 2D 版本。

### 2.2 基础模型与 VLA

| 模型 | 机构 | 特点 |
|-----|------|------|
| **RT-2 / RT-X** (Google DeepMind) | VLM 直接输出动作 token | 语义推理与机器人控制的端到端融合；RT-X 在 22 种机器人上联合训练 |
| **Octo** (Berkeley/Stanford/Google) | Transformer 架构 | 开源通才策略，支持多摄像头输入与语言指令 |
| **OpenVLA** (Stanford/Berkeley/TRI) | Llama + DINOv2 | 开源 VLA，支持消费级 GPU 微调，在多种真机任务上表现强劲 |
| **π0 (Pi-Zero)** (Physical Intelligence) | Flow Matching | 强调通用机器人控制与长程复杂任务 |

---

## 3. 关键论文

### 遥操作与数据采集

1. **Mobile ALOHA: Learning Bimanual Mobile Manipulation with Low-Cost Whole-Body Teleoperation**  
   Zipeng Fu, Tony Z. Zhao, Chelsea Finn. Stanford. Jan 2024.  
   [arXiv:2401.02117](https://arxiv.org/abs/2401.02117) · [GitHub](https://github.com/MarkFzp/mobile-aloha)  
   → 将 ALOHA 扩展到移动底盘，实现全身遥操作与移动操作学习，硬件成本 <$20k。

2. **ALOHA: A Low-cost Open-source Hardware System for Bimanual Teleoperation**  
   Tony Z. Zhao et al. Stanford. 2023.  
   [arXiv:2304.13705](https://arxiv.org/abs/2304.13705)  
   → 低成本开源双臂遥操作硬件，通过同构主臂直接控制从臂。

3. **Open-TeleVision: Teleoperation with Immersive Active Visual Feedback**  
   Xianyi Cheng et al. CMU / UC San Diego. 2024.  
   [arXiv:2407.01512](https://arxiv.org/abs/2407.01512) · [GitHub](https://github.com/OpenTeleVision/TeleVision)  
   → VR 头显提供沉浸式主动视觉反馈，支持人形机器人全身遥操作。

4. **DexCap: Scalable and Portable Hand Motion Capture for Humanoid Robot Teleoperation**  
   Chen Wang et al. Columbia. RSS 2024.  
   [arXiv:2406.09546](https://arxiv.org/abs/2406.09546)  
   → 手腕佩戴摄像头的便携式手部动捕，将人手动作实时映射到人形机器人。

5. **UMI: Data-Driven Interface for Transferring Human Manipulation to Robots**  
   Yifan Hou et al. Stanford. RSS 2024.  
   [arXiv:2402.10329](https://arxiv.org/abs/2402.10329) · [GitHub](https://github.com/real-stanford/umi)  
   → 手持式夹具 + GoPro 采集人类操作数据，通过 6-DoF 位姿与夹爪开合直接生成机器人示范。

6. **AnyTeleop: A General Vision-Based Dexterous Robot Arm-Hand Teleoperation System**  
   Yuzhe Qin et al. UC San Diego. RSS 2023.  
   [arXiv:2307.04577](https://arxiv.org/abs/2307.04577)  
   → 单摄像头估计人手姿态，控制任意机械臂与多指灵巧手。

7. **HumanPlus: Humanoid Shadowing and Imitation from Humans**  
   Shadow Team / Stanford. 2024.  
   [arXiv:2405.17940](https://arxiv.org/abs/2405.17940)  
   → 通过 RGB 相机捕捉人体全身姿态，实时映射到人形机器人进行影子学习。

8. **Dobb-E: Learning to Robotic Manipulate from Home Data**  
   Shikhar Bahl et al. NYU / Meta. ICRA 2024.  
   [arXiv:2311.16099](https://arxiv.org/abs/2311.16099)  
   → 利用手持设备在家中采集数据，通过自监督与模仿学习实现家居操作。

### 模仿学习与视频动作策略

9. **Diffusion Policy: Visuomotor Policy Learning via Action Diffusion**  
   Cheng Chi et al. Columbia. RSS 2023 / T-RO 2024.  
   [arXiv:2303.04137](https://arxiv.org/abs/2303.04137) · [GitHub](https://github.com/columbia-ai-robotics/diffusion_policy)  
   → 将扩散模型引入机器人策略学习，解决行为克隆中多模态动作分布建模难题。

10. **3D Diffusion Policy: Generalizable Visuomotor Policy Learning via Simple 3D Representations**  
    Yanjie Ze et al. Columbia / SJTU. RSS 2024.  
    [arXiv:2403.03954](https://arxiv.org/abs/2403.03954) · [GitHub](https://github.com/columbia-ai-robotics/3d_diffusion_policy)  
    → 用 3D 点云替代 2D 图像作为策略输入，在跨视角、跨物体泛化上显著优于 2D DP。

11. **Octo: An Open-Source Generalist Robot Policy**  
    Dibya Ghosh et al. Berkeley / Stanford / Google DeepMind et al. RSS 2024.  
    [arXiv:2405.12213](https://arxiv.org/abs/2405.12213) · [GitHub](https://github.com/octo-models/octo)  
    → 开源通才策略，基于 Transformer 架构，在 Open X-Embodiment 数据集上预训练，支持多机迁移。

12. **OpenVLA: An Open-Source Vision-Language-Action Model**  
    Moo Jin Kim et al. Stanford / Berkeley / TRI. CoRL 2024.  
    [arXiv:2406.09246](https://arxiv.org/abs/2406.09246) · [GitHub](https://github.com/openvla/openvla)  
    → 开源 VLA 模型，基于 Llama 与 DINOv2，支持自然语言指令与视觉输入，可在消费级 GPU 上微调。

13. **RT-2: Vision-Language-Action Models**  
    Anthony Brohan et al. Google DeepMind. RSS 2023.  
    [arXiv:2307.15818](https://arxiv.org/abs/2307.15818)  
    → 将 VLM 直接输出动作 token，实现语义推理与机器人控制的端到端融合。

14. **π0: A Vision-Language-Action Flow Model for General Robot Control**  
    Physical Intelligence. 2024.  
    [arXiv:2410.24159](https://arxiv.org/abs/2410.24159) · [GitHub](https://github.com/Physical-Intelligence/openpi)  
    → 基于流匹配（Flow Matching）的 VLA 模型，强调长程复杂任务与灵巧操作。

15. **MimicGen: A Data Generation System for Scalable Robot Learning using Human Demonstrations**  
    Ajay Mandlekar et al. NVIDIA. NeurIPS 2023.  
    [arXiv:2310.17596](https://arxiv.org/abs/2310.17596) · [GitHub](https://github.com/NVlabs/mimicgen)  
    → 在仿真中自动扩展人类示范数据，通过改变物体位姿与场景配置生成大规模数据集。

---

## 4. 关键开源项目

| 项目 | Stars | 描述 | 链接 |
|-----|-------|------|-------|
| **LeRobot** | 23.9k+ | Hugging Face 开源机器人学习框架 | [huggingface/lerobot](https://github.com/huggingface/lerobot) |
| **diffusion_policy** | 2.5k+ | Diffusion Policy 官方实现 | [columbia-ai-robotics/diffusion_policy](https://github.com/columbia-ai-robotics/diffusion_policy) |
| **Mobile ALOHA** | 4.5k+ | 移动双臂遥操作 | [MarkFzp/mobile-aloha](https://github.com/MarkFzp/mobile-aloha) |
| **Open-TeleVision** | 1.5k+ | 沉浸式 VR 遥操作 | [OpenTeleVision/TeleVision](https://github.com/OpenTeleVision/TeleVision) |
| **Octo** | 1.5k+ | 通才机器人策略 | [octo-models/octo](https://github.com/octo-models/octo) |
| **OpenVLA** | 1.2k+ | 开源 VLA 模型 | [openvla/openvla](https://github.com/openvla/openvla) |
| **robosuite** | 2.4k+ | 模块化机器人仿真平台 | [ARISE-Initiative/robosuite](https://github.com/ARISE-Initiative/robosuite) |
| **DexCap** | 800+ | 手部动捕与遥操作 | [columbia-ai-robotics/dexcap](https://github.com/columbia-ai-robotics/dexcap) |
| **AnyTeleop** | 600+ | 通用视觉遥操作 | [dvlab-research/AnyTeleop](https://github.com/dvlab-research/AnyTeleop) |
| **MimicGen** | 500+ | 仿真数据自动生成 | [NVlabs/mimicgen](https://github.com/NVlabs/mimicgen) |

---

## 5. 方法对比与前沿趋势

### 5.1 遥操作范式对比

| 维度 | VR 遥操作 | 低成本视觉遥操作 | 动捕遥操作 | 伪遥操作/仿真 |
|-----|----------|----------------|----------|--------------|
| 硬件成本 | 高 | 极低 | 中 | 低 |
| 操作自由度 | 中 | 低-中 | 高 | 任意 |
| 沉浸感 | 极高 | 低 | 中 | 无 |
| 数据质量 | 中 | 高 | 高 | 低-中 |
| 规模化 | 难 | 易 | 中 | 极易 |
| 适用场景 | 远程危险作业、人形全身 | 双臂精细操作、家居 | 灵巧手、人形全身 | 大规模预训练 |

### 5.2 当前最前沿方向

1. **低成本、可复制的遥操作硬件生态** — Mobile ALOHA、UMI 等推动了「机器人数据民主化」。未来趋势是进一步降低硬件成本（<$1k）并标准化接口。
2. **通扏策略与 VLA** — Octo、OpenVLA、π0 代表「一个模型控制多种机器人」的方向。核心挑战：异构本体迁移与长程任务规划。
3. **人手-机器人灵巧手映射** — DexCap、AnyTeleop 探索将人手高自由度动作迁移到机器人灵巧手。开放问题：如何建立语义/功能层面的映射而非几何映射？
4. **Video-to-Action 学习** — 从互联网视频（YouTube、Ego4D）直接学习操作技能，无需机器人本体采集。动作估计精度仍不足以支撑精密任务。
5. **Sim-to-Real + 仿真扩展** — MimicGen、DexVerse 等通过仿真扩展数据。结合高保真仿真（NVIDIA Isaac Sim/Gym）与域随机化，正在缩小 sim-to-real gap。

### 5.3 开放问题

- **域差异（Domain Gap）**：不同遥操作硬件采集的数据格式、动作空间不一致，如何统一表示（如 LeRobot 的标准化努力）？
- **数据隐私与伦理**：家庭场景遥操作涉及隐私视频采集。
- **长时间自主 vs 人在回路**：当前遥操作主要用于数据采集，未来机器人在多大程度上可以脱离遥操作自主运行？
- **评估标准缺失**：遥操作界面与视频策略缺乏统一的可用性与泛化性基准。

---

## 6. 关系

- 与 [data-flywheel-robotics](data-flywheel-robotics.md) 紧密相关：遥操作是数据飞轮的「入口」，视频策略是「引擎」。
- 与 [imitation-learning-robotics](imitation-learning-robotics.md) 相互依存：遥操作数据通常通过模仿学习进行策略训练。
- 与 [sim-to-real](sim-to-real.md) 相互补充：仿真生成是遥操作数据的重要补充。
- 与 [vla-vision-language-action](vla-vision-language-action.md) 紧密关联：VLA 模型通常在大规模遥操作/仿真数据上预训练。
- 与 [humanoid-robot](humanoid-robot.md) 相关：人形机器人全身控制极度依赖全身遥操作。
