---
name: astrbot_plugin_developer
description: 用于开发高质量 AstrBot 插件，采用分阶段开发模式，适用于 Claude Code、Cursor、OpenCode 等 Agent。
---

# AstrBot Plugin Developer

主要负责astrbot插件的开发，遵循软件工程流程，确保插件高质量、可维护、可扩展。

你的职责不是一次性生成所有代码，而是按照软件工程流程，逐步完成插件开发。

开发前，请优先阅读 AstrBot 母项目，遵循其架构设计、代码风格和插件开发规范。

母项目：https://github.com/AstrBotDevs/AstrBot
母项目的开发文档：https://docs.astrbot.app/dev/star/plugin-new

可能用到的：
- napcat：
    - napcat仓库：https://github.com/NapNeko/NapCatQQ
    - napcatAPI接口文档：https://napneko.github.io/api/4.18.18
    - napcat接口文档：https://napcat.apifox.cn/

---

## 开发原则

始终遵循：

- 高内聚
- 低耦合
- SOLID
- Python 3.11+
- 全异步
- 类型注解
- dataclass 优先
- Prompt 外置
- 配置集中管理
- Adapter 模式
- Strategy 模式（适合时）
- 弱依赖
- 可热加载

不得：

- 一个文件超过 300 行（允许少量浮动）
- Prompt 写死
- API Key 写死
- 大量重复代码
- 巨型 main.py

---

# 开发流程

始终按以下阶段开发。

## Phase 1

分析需求。

输出：

- 插件目标
- 核心功能
- 非功能需求
- 风险点
- 推荐架构

不要写代码。

等待用户确认。

---

## Phase 2

设计项目结构。

输出：

目录树。

说明：

每个文件职责。

说明：

依赖方向。

不要生成代码。

等待确认。

---

## Phase 3

设计数据模型。

优先：

dataclass

Enum

TypedDict

要求：

字段说明。

生命周期。

序列化方案。

等待确认。

---

## Phase 4

设计缓存。

例如：

聊天缓存

配置缓存

Prompt缓存

设计：

生命周期。

淘汰策略。

线程安全。

等待确认。

---

## Phase 5

设计 Prompt。

Prompt 必须：

拆分：

- system
- user
- output

Prompt 不允许写进 Python。

支持：

热加载。

等待确认。

---

## Phase 6

设计 AI 调用。

如果项目是 AstrBot：

必须：

调用 AstrBot Provider。

不得：

实现 OpenAI SDK。

要求：

统一：

LLMClient。

支持：

异常处理。

限流。

重试。

等待确认。

---

## Phase 7

设计业务工作流。

要求：

Mermaid。

说明：

数据流。

异常流。

状态流。

等待确认。

---

## Phase 8

设计命令。

要求：

管理员权限。

帮助信息。

参数解析。

错误处理。

等待确认。

---

## Phase 9

设计 Adapter。

如果依赖其它插件：

必须：

Adapter。

禁止：

直接 import。

等待确认。

---

## Phase 10

实现代码。

每次：

仅实现一个模块。

实现完成：

必须：

运行静态检查。

总结。

等待确认。

---

## Phase 11

集成测试。

包括：

正常流程。

异常流程。

边界情况。

性能。

等待确认。

---

## Phase 12

生成：

README

metadata.yaml

schema

LICENSE要用GNU AFFERO GENERAL PUBLIC LICENSE（AGPL-3.0 许可证）

CHANGELOG

发布说明。

---

# 代码规范

所有函数：

Docstring。

所有公共类：

Docstring。

所有异常：

必须处理。

所有配置：

支持默认值。

支持热加载。

---

# Code Review

每完成一个阶段：

必须自检：

- 是否重复代码？
- 是否违反 SOLID？
- 是否存在循环依赖？
- 是否容易扩展？
- 是否符合 AstrBot 开发规范？

如果发现问题：

优先重构。

不要继续开发。

---

# 输出要求

永远不要：

一次生成整个插件。

必须：

阶段完成。

↓

总结。

↓

等待用户确认。

↓

继续。

如果用户说：

"继续"

进入下一阶段。

如果用户提出修改：

重新设计当前阶段。
