# 🤖 Sub-агенты FinPulse для Claude Code

Здесь лежат **6 готовых специализированных агентов** для работы с проектом FinPulse в Claude Code.

## Что нужно сделать после установки Claude Code

Claude Code ищет агентов в папке `.claude/agents/` (с точкой). Нужно один раз переместить эту папку:

### macOS / Linux
```bash
cd ~/Documents/Claude/Projects/FinPulse
mkdir -p .claude
mv agents .claude/agents
```

### Windows (PowerShell)
```powershell
cd C:\Users\админ\Documents\Claude\Projects\FinPulse
New-Item -ItemType Directory -Path .claude -Force
Move-Item agents .claude\agents
```

После этого структура станет:
```
FinPulse/
├── .claude/
│   └── agents/
│       ├── ui-designer.md
│       ├── ios-engineer.md
│       ├── api-engineer.md
│       ├── ai-prompts.md
│       ├── security-reviewer.md
│       └── product-manager.md
└── ...
```

## Команда из 6 агентов

| Агент | За что отвечает | Модель |
|---|---|---|
| **`@ui-designer`** | Лендинг, мокапы, дизайн, фирменный стиль, прототипы HTML/CSS | sonnet |
| **`@ios-engineer`** | Swift / SwiftUI, iOS-приложение, Keychain, биометрия, StoreKit | sonnet |
| **`@api-engineer`** | FastAPI / Python, PostgreSQL, AI proxy, биллинг App Store | sonnet |
| **`@ai-prompts`** | Промпты для Lifestyle Mirror и AI-инсайтов | opus |
| **`@security-reviewer`** | Аудит безопасности и приватности (только чтение) | opus |
| **`@product-manager`** | Roadmap, PRD, метрики, конкурентный анализ | sonnet |

## Как вызвать

После установки и переноса агентов запусти Claude Code в папке проекта:

```bash
cd ~/Documents/Claude/Projects/FinPulse
claude
```

И обращайся к агентам:

### Явно через @
```
@ui-designer сделай мне форму регистрации в фирменных цветах
@ios-engineer спроектируй экран Lifestyle Mirror в SwiftUI
@security-reviewer проверь /api/payment.py на уязвимости
```

### Автоматически
Просто описывай задачу — главный Claude сам выберет агента:
```
Нужно сделать API для подписок App Store
```
→ Claude автоматически делегирует `@api-engineer`

### Параллельно
```
Параллельно: @ui-designer сделай экран целей,
@api-engineer добавь endpoint /goals,
@ai-prompts сгенерируй промпт для совета по достижению цели
```

## Что в каждом агенте

Каждый файл — это **markdown с YAML frontmatter**:

```markdown
---
name: ui-designer
description: когда использовать
tools: список инструментов
model: какая модель Claude
---

# Системный промпт
[подробные инструкции и контекст]
```

Все агенты «знают» о бренд-цветах, целевой аудитории, конкурентах, технологическом стеке — потому что прочитают `CLAUDE.md` при первом запуске.

## Куда смотреть дальше

- `CLAUDE.md` — главный контекст проекта (читается каждой сессией Claude Code)
- `README.md` — общая навигация по проекту
- `03_features/features_list.md` — что нужно реализовать в MVP
- `04_calculator/calculator.html` — эталон UI-стиля (живой пример)
- `05_landing/index.html` — эталон лендинга

---

*Создано через Cowork-сессию · Май 2026*
