# Vibe Coding Was Born Dead. Meet Whip Coding

## ЧАСТЬ 3: АРХИТЕКТУРА WHIP CODING

### 3.1 ДЕТАЛЬНЫЙ WORKFLOW

Рассмотрим телеграм-бот как пример top-down иерархии спринтов. Строим дерево от корня: эпики определяют интерфейсы, спринты реализуют атомарно.

**Дерево спринтов** (markdown-визуализация):

```
Bot Project
├── Epic 1: Core Infrastructure
│   ├── Sprint 1.1: Type Definitions (output: базовые типы)
│   ├── Sprint 1.2: Data Layer (input: типы 1.1; output: CRUD-интерфейсы)
│   └── Sprint 1.3: Error & Logging (input: 1.1-1.2)
├── Epic 2: Telegram Layer (после Epic 1)
│   ├── Sprint 2.1: Message Parsing (input: типы; output: обработанные события)
│   └── Sprint 2.2: Handlers (input: 2.1; output: responses)
└── Epic 3: AI Integration (параллельно после Core)
    └── Sprint 3.1: Context & Generation (input: Core + Telegram; output: AI responses)
```

**Sprint 1.1 Контракт**:
- Input: none (root).
- Output: типы Message, UserContext, Response.
- Dependencies: none.
- Criteria: полная типизация без пробелов [mcp_tool_github-mcp-direct_get_file_contents].

Каждый спринт проходит: автор → 3 критика (оптимист/параноик/реалист) → lint. Размер фиксирован, интерфейсы нерушимы. Это обеспечивает нулевой дрейф и параллелизацию [mcp_tool_github-mcp-direct_get_file_contents].