---
title: Apptronik
created: 2026-05-11
updated: 2026-05-11
type: entity
tags: [company, robotics, embodiment]
sources: [raw/articles/soul2humanoid-report-apptronik.md, raw/articles/soul2humanoid-latest-news.md]
confidence: high
---

# Apptronik

[官网](https://apptronik.com) · [X/Twitter](https://x.com/apptronik)

通用人形机器人平台 Apollo，硬件+合作 AI（Google Gemini）。

## 核心优势：执行器技术

- 源自 NASA Valkyrie 机器人执行器开发经验
- 线性 + 旋转执行器混合设计，高功率密度、高可靠性
- 模块化关节可独立销售

## Apollo 规格

- 身高 ~173cm / 体重 ~73kg / 续航 4-6h / 负载 ~25kg
- 上半身可拆卸与移动底盘分离
- 末端执行器快换（夹爪/五指手/工具接口）

## AI 策略：合作伙伴

```
合作伙伴 AI (Google Gemini) → Apptronik 中间件 → Apollo 硬件
```

- 2024 年与 **Google DeepMind** 战略合作：Gemini VLA + Apollo 硬件
- 自研全身控制器、步态生成、安全系统、遥操作接口

### 技术细节

#### 执行器技术

- **NASA 血统**：核忂团队曾参与 NASA Valkyrie 机器人的执行器开发，积累了航天级的高可靠性设计经验
- **混合执行器设计**：线性执行器（用于肩胛、肘部的大力矩输出）+ 旋转执行器（用于手腕、头部的精确位置控制）
- **模块化关节**：每个关节可独立销售，支持其他机器人公司或研究机构快速集成
- **功率密度**：在同级别执行器中具有领先的功率重量比

#### Apollo 架构

- **上半身可拆卸**：支持与移动底盘分离，可作为固定式协助操作系统使用
- **快换末端执行器**：夹爪、五指灵巧手、工具接口可快速切换，支持多任务场景
- **安全设计**：包含力限制、碰撞检测、紧急停机等多层安全机制

## 最新动态（2024-2026）

- **$9.35 亿总融资**：包括多轮风险投资，资金充裕
- **人才招募**：挖角 Waymo CPO Daniel Chu、Boston Dynamics 工程负责人 Kevin Garell，组建"梦之队"
- **2025 年底**：与 Jabil（制造业巨头）签订试点协议，在制造业环境中验证 Apollo 的可靠性
- **2026.03**：宣布与 Google DeepMind 的合作进入下一阶段，Gemini 集成开始在 Apollo 上进行真机测试
- **栈式合作模式**："强硬件 + 强AI 合作伙伴"的典型代表，与 Figure/Tesla 的全自研、PI 的纯软件形成三足鼎立

## 竞争格局

- **"硬件平台商"定位**：与 [enchanted-tools](enchanted-tools.md) 、[genesis-ai](genesis-ai.md) 类似采用"硬件+合作 AI"模式，但 Apptronik 在执行器技术上更深
- **核心壁垒**：NASA 级执行器技术 + 模块化设计，使其硬件可以服务多家 AI 公司
- **合作生态**：与 Google DeepMind 的绑定为其提供了顶尖的 AI 能力，但也意味着技术路径受合作伙伴影响
- **量产化能力**：相比 Figure/Tesla 的自建制造能力，Apptronik 更侧重设计与软件，制造外包

## 关键人物

- **Jeff Cardenas**：CEO / 联合创始人，曾在 NASA 参与机器人项目，负责公司战略与商业化
- **Nick Paine**：CTO / 联合创始人，机械工程背景，负责执行器与硬件架构设计
- **Daniel Chu**：前 Waymo CPO（2026 年加入），负责产品策略与市场拓展

## 关系

- 与 [google-deepmind](google-deepmind.md) 深度绑定
- 与 [enchanted-tools](enchanted-tools.md) 、[genesis-ai](genesis-ai.md) 类似采用"硬件+合作 AI"模式
