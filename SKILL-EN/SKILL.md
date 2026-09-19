---
name: astrbot_plugin_developer
description: For developing high-quality AstrBot plugins using a phased development approach, suitable for agents like Claude Code, Cursor, OpenCode, etc.
---

# AstrBot Plugin Developer

Primarily responsible for the development of AstrBot plugins, following software engineering processes to ensure plugins are high-quality, maintainable, and extensible.

Your responsibility is not to generate all the code at once, but to complete plugin development step by step according to the software engineering process.

Before development, prioritize reading the AstrBot parent project, following its architectural design, code style, and plugin development standards.

Parent project: https://github.com/AstrBotDevs/AstrBot
Parent project development documentation: https://docs.astrbot.app/dev/star/plugin-new

Potentially useful:
- napcat:
    - napcat repository: https://github.com/NapNeko/NapCatQQ
    - napcat API documentation: https://napneko.github.io/api/4.18.18
    - napcat interface documentation: https://napcat.apifox.cn/

---

## Development Principles

Always follow:

- High cohesion
- Low coupling
- SOLID
- Python 3.11+
- Fully asynchronous
- Type annotations
- dataclass first
- Externalized prompts
- Centralized configuration management
- Adapter pattern
- Strategy pattern (when applicable)
- Weak dependencies
- Hot-reloadable

Must not:

- A single file exceeds 300 lines (a small margin is allowed)
- Hardcode prompts
- Hardcode API keys
- Large amounts of duplicated code
- A monolithic main.py

---

# Development Process

Always develop according to the following phases.

## Phase 1

Analyze requirements.

Output:

- Plugin goals
- Core features
- Non-functional requirements
- Risk points
- Recommended architecture

Do not write code.

Wait for user confirmation.

---

## Phase 2

Design project structure.

Output:

Directory tree.

Explain:

Responsibilities of each file.

Explain:

Dependency direction.

Do not generate code.

Wait for confirmation.

---

## Phase 3

Design data models.

Prefer:

dataclass

Enum

TypedDict

Requirements:

Field descriptions.

Lifecycle.

Serialization plan.

Wait for confirmation.

---

## Phase 4

Design caching.

For example:

Chat cache

Configuration cache

Prompt cache

Design:

Lifecycle.

Eviction strategy.

Thread safety.

Wait for confirmation.

---

## Phase 5

Design Prompts.

Prompts must:

Be split into:

- system
- user
- output

Prompts must not be written into Python.

Support:

Hot-reloading.

Wait for confirmation.

---

## Phase 6

Design AI calls.

If the project is AstrBot:

Must:

Call the AstrBot Provider.

Must not:

Implement the OpenAI SDK.

Requirements:

Unified:

LLMClient.

Support:

Exception handling.

Rate limiting.

Retries.

Wait for confirmation.

---

## Phase 7

Design business workflow.

Requirement:

Mermaid.

Explain:

Data flow.

Exception flow.

State flow.

Wait for confirmation.

---

## Phase 8

Design commands.

Requirements:

Admin permissions.

Help information.

Argument parsing.

Error handling.

Wait for confirmation.

---

## Phase 9

Design Adapter.

If dependent on other plugins:

Must:

Adapter.

Prohibited:

Direct import.

Wait for confirmation.

---

## Phase 10

Implement code.

Each time:

Implement only one module.

After implementation:

Must:

Run static checks.

Summarize.

Wait for confirmation.

---

## Phase 11

Integration testing.

Includes:

Normal flow.

Exception flow.

Edge cases.

Performance.

Wait for confirmation.

---

## Phase 12

Generate:

README

metadata.yaml

schema

LICENSE (must use the GNU AFFERO GENERAL PUBLIC LICENSE, AGPL-3.0)

CHANGELOG

Release notes.

---

# Code Standards

All functions:

Docstring.

All public classes:

Docstring.

All exceptions:

Must be handled.

All configurations:

Support default values.

Support hot-reloading.

---

# Code Review

After each phase:

Must self-check:

- Is there duplicated code?
- Are SOLID principles violated?
- Are there circular dependencies?
- Is it easy to extend?
- Does it comply with AstrBot development standards?

If issues are found:

Prioritize refactoring.

Do not continue development.

---

# Output Requirements

Never:

Generate the entire plugin at once.

Must:

Complete phase.

↓

Summarize.

↓

Wait for user confirmation.

↓

Continue.

If the user says:

"Continue"

Proceed to the next phase.

If the user requests modifications:

Redesign the current phase.
