# 适用于ASTRBOT插件开发的SKILL-astrbot_plugin_developer

基于分阶段开发模式的 AstrBot 插件开发 Skill，适用于 Claude Code、Cursor、OpenCode 等 AI 编程助手

## 功能介绍

本 Skill 引导 AI 严格按照软件工程流程，分 12 个阶段完成高质量 AstrBot 插件的开发，确保代码：

- 高内聚、低耦合
- 符合 SOLID 原则
- 全异步、类型安全
- 配置集中、Prompt 外置
- 可热加载、易于维护与扩展

## 使用方式

1. 将 [SKILL-CN/SKILL.md](SKILL-CN/SKILL.md) 内容作为 Skill 导入你的Agent执行器（其他语言见下方「多语言版本」）
2. 向Agent描述你想要开发的 AstrBot 插件需求
3. Agent将从 Phase 1 开始逐步分析、设计并实现插件
4. 每个阶段结束后，Agent会等待你的确认，再进入下一阶段

## 多语言版本

| 语言 | 文件 |
|------|------|
| 简体中文 | [SKILL-CN/SKILL.md](SKILL-CN/SKILL.md) |
| English | [SKILL-EN/SKILL.md](SKILL-EN/SKILL.md) |
| 繁體中文 | [SKILL-TW/SKILL.md](SKILL-TW/SKILL.md) |
| 日本語 | [SKILL-JA/SKILL.md](SKILL-JA/SKILL.md) |
| 한국어 | [SKILL-KO/SKILL.md](SKILL-KO/SKILL.md) |
| Русский | [SKILL-RU/SKILL.md](SKILL-RU/SKILL.md) |
| Español | [SKILL-ES/SKILL.md](SKILL-ES/SKILL.md) |
| Français | [SKILL-FR/SKILL.md](SKILL-FR/SKILL.md) |
| Deutsch | [SKILL-DE/SKILL.md](SKILL-DE/SKILL.md) |
| Português | [SKILL-PT/SKILL.md](SKILL-PT/SKILL.md) |

各语言版本结构完全一致（383 行，章节与 Phase 一一对应），内容以简体中文版为准。

## 开发流程总览

| 阶段 | 内容 |
|------|------|
| Phase 1  | 需求分析 |
| Phase 2  | 项目结构设计 |
| Phase 3  | 数据模型设计 |
| Phase 4  | 缓存设计 |
| Phase 5  | Prompt 设计 |
| Phase 6  | AI 调用设计 |
| Phase 7  | 业务工作流设计 |
| Phase 8  | 命令设计 |
| Phase 9  | Adapter 设计 |
| Phase 10 | 代码实现 |
| Phase 11 | 集成测试 |
| Phase 12 | 文档与发布 |

## 适用环境

- AstrBot 母项目：https://github.com/AstrBotDevs/AstrBot
- AstrBot 插件开发文档：https://docs.astrbot.app/dev/star/plugin-new

## 插件检查

-检查插件网络安全并核验本插件是否符合astrbot社区规范
    - https://docs.astrbot.app/dev/plugin-market/2026-06-27.html


## 注意事项

- 指令必须标有注释和此指令的功能
- 所有代码严格遵循 AstrBot 开发规范
- 禁止一次性生成完整插件，必须逐步推进，除非用户授权直接跳过
- 每完成一个阶段，Agent会进行代码审查，发现问题会重构
- 不要忽略Agent的提问
- 初次生成完后可能出现代码不完整或有错误的情况，请将报错和报错内容反馈给Agent，Agent会进行修复和重构
---

通过本 Skill，你可以像与资深开发者结对编程一样，系统性地完成插件开发