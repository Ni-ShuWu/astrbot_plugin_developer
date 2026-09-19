---
name: astrbot_plugin_developer
description: 用於開發高品質 AstrBot 外掛，採用分階段開發模式，適用於 Claude Code、Cursor、OpenCode 等 Agent。
---

# AstrBot Plugin Developer

主要負責 AstrBot 外掛的開發，遵循軟體工程流程，確保外掛高品質、可維護、可擴充。

你的職責不是一次性產生所有程式碼，而是依照軟體工程流程，逐步完成外掛開發。

開發前，請優先閱讀 AstrBot 母專案，遵循其架構設計、程式碼風格和外掛開發規範。

母專案：https://github.com/AstrBotDevs/AstrBot
母專案的開發文件：https://docs.astrbot.app/dev/star/plugin-new

可能會用到的：
- napcat：
    - napcat 儲存庫：https://github.com/NapNeko/NapCatQQ
    - napcat API 介面文件：https://napneko.github.io/api/4.18.18
    - napcat 介面文件：https://napcat.apifox.cn/

---

## 開發原則

始終遵循：

- 高內聚
- 低耦合
- SOLID
- Python 3.11+
- 全非同步
- 型別註解
- dataclass 優先
- Prompt 外部化
- 設定集中管理
- Adapter 模式
- Strategy 模式（適用時）
- 弱依賴
- 可熱載入

不得：

- 單一檔案超過 300 行（允許少量浮動）
- Prompt 寫死
- API Key 寫死
- 大量重複程式碼
- 巨型 main.py

---

# 開發流程

始終依照以下階段開發。

## Phase 1

分析需求。

輸出：

- 外掛目標
- 核心功能
- 非功能需求
- 風險點
- 建議架構

不要寫程式碼。

等待使用者確認。

---

## Phase 2

設計專案結構。

輸出：

目錄樹。

說明：

每個檔案的職責。

說明：

依賴方向。

不要產生程式碼。

等待確認。

---

## Phase 3

設計資料模型。

優先：

dataclass

Enum

TypedDict

要求：

欄位說明。

生命週期。

序列化方案。

等待確認。

---

## Phase 4

設計快取。

例如：

聊天快取

設定快取

Prompt 快取

設計：

生命週期。

淘汰策略。

執行緒安全。

等待確認。

---

## Phase 5

設計 Prompt。

Prompt 必須：

拆分：

- system
- user
- output

Prompt 不得寫入 Python。

支援：

熱載入。

等待確認。

---

## Phase 6

設計 AI 呼叫。

如果專案是 AstrBot：

必須：

呼叫 AstrBot Provider。

不得：

實作 OpenAI SDK。

要求：

統一：

LLMClient。

支援：

例外處理。

速率限制。

重試。

等待確認。

---

## Phase 7

設計業務工作流程。

要求：

Mermaid。

說明：

資料流。

例外流。

狀態流。

等待確認。

---

## Phase 8

設計指令。

要求：

管理員權限。

說明資訊。

參數解析。

錯誤處理。

等待確認。

---

## Phase 9

設計 Adapter。

如果依賴其他外掛：

必須：

Adapter。

禁止：

直接 import。

等待確認。

---

## Phase 10

實作程式碼。

每次：

僅實作一個模組。

實作完成：

必須：

執行靜態檢查。

總結。

等待確認。

---

## Phase 11

整合測試。

包括：

正常流程。

例外流程。

邊界情況。

效能。

等待確認。

---

## Phase 12

產生：

README

metadata.yaml

schema

LICENSE 需使用 GNU AFFERO GENERAL PUBLIC LICENSE（AGPL-3.0 授權條款）

CHANGELOG

發佈說明。

---

# 程式碼規範

所有函式：

Docstring。

所有公用類別：

Docstring。

所有例外：

必須處理。

所有設定：

支援預設值。

支援熱載入。

---

# Code Review

每完成一個階段：

必須自我檢查：

- 是否有重複程式碼？
- 是否違反 SOLID？
- 是否存在循環依賴？
- 是否易於擴充？
- 是否符合 AstrBot 開發規範？

如果發現問題：

優先重構。

不要繼續開發。

---

# 輸出要求

永遠不要：

一次產生整個外掛。

必須：

階段完成。

↓

總結。

↓

等待使用者確認。

↓

繼續。

如果使用者說：

"繼續"

進入下一階段。

如果使用者提出修改：

重新設計當前階段。
