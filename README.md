# cursor rules for golang

# Cursor Rules

Единые правила работы с Cursor для стандартизации разработки и повышения качества генерируемого кода.

## 📋 Оглавление

- [Описание](#описание)
- [Структура](#структура)
- [Использование](#использование)
- [Категории правил](#категории-правил)
- [Добавление новых правил](#добавление-новых-правил)
- [Обновление правил](#обновление-правил)

## Описание

Этот набор правил настраивает Cursor AI для генерации кода, соответствующего стандартам проекта:
- Clean Architecture
- Go best practices
- Единые стилистические соглашения
- Автоматизация процессов разработки

Правила версионируются в Git вместе с кодом, что гарантирует актуальность для всех членов команды.



## Категории правил

### 🏗️ Архитектура (`architecture/`)

**`architecture.mdc`**
- Правила Clean Architecture
- Слоистая структура (handlers, services, repositories)
- Dependency injection
- Разделение ответственности

**`business-func.mdc`**
- Чистые функции без побочных эффектов
- Unit-тесты для бизнес-логики
- Хранение логики в service-слое
- Комментирование функций

### 🐹 Golang (`golang/`)

**`context.mdc`** — Работа с `context.Context`
- Передача как первый параметр
- Timeout и cancellation
- Propagation через слои
- Проверка `ctx.Done()`

**`database.mdc`** — Безопасная работа с БД
- Параметризованные запросы
- `QueryContext`/`ExecContext`
- `defer rows.Close()`
- Транзакции и connection pooling

**`defer-resources.mdc`** — Управление ресурсами
- Закрытие файлов, rows, транзакций
- Закрытие HTTP bodies
- Unlock мьютексов

**`errors.mdc`** — Обработка ошибок
- Немедленная проверка ошибок
- Wrapping через `%w`
- Использование `errors.Is`/`errors.As`
- Structured logging ошибок

**`go-proverbs.mdc`** — Следование Go Proverbs
- Zero value
- Малые интерфейсы
- Копирование vs зависимости
- Каналы для коммуникации

**`graceful-shutdown.mdc`** — Graceful shutdown
- Обработка SIGINT/SIGTERM
- `http.Server.Shutdown`
- `sync.WaitGroup`
- Закрытие клиентов

**`interfaces.mdc`** — Работа с интерфейсами
- Accept interfaces, return structs
- Малые интерфейсы
- Определение в месте использования
- Суффикс `-er` для интерфейсов

**`logs.mdc`** — Структурированное логирование
- Key-value пары через zap
- Уровни логирования
- Контекст операций
- Замена `fmt.Println`

**`main.mdc`** — Общие правила для Go API
- Использование `net/http`
- Go 1.23 ServeMux
- RESTful design
- Middleware, валидация, безопасность

**`naming.mdc`** — Соглашения по именованию
- Короткие локальные имена
- PascalCase для экспорта
- Суффикс `-er` для интерфейсов
- Глаголы для функций

**`testing.mdc`** — Правила тестирования
- Table-driven tests
- `t.Parallel()`
- Mocks для зависимостей
- Покрытие edge cases
- `testify/assert`

### 🔄 Workflow (`workflow/`)

**`commit.mdc`** — Генерация commit-сообщений
- Conventional Commits формат
- Типы: `feat`/`fix`/`refactor`
- Формат `[TASK-NUM]`
- Активация через `@Commit [TASK-NUM]`

**`review.mdc`** — Проведение code review
- Анализ изменений через `git diff`
- Проверка соответствия правилам
- Структурированный отчет
- Группировка по severity
- Активация через `@review`

**`review-evaluation-criteria.mdc`** — Критерии оценки кода
- Design & Architecture
- Complexity & Maintainability
- Functionality & Correctness
- Readability & Naming
- Best Practices
- Test Coverage
- Security
- Performance
- Observability

## Добавление новых правил

1. Определите категорию правила (архитектура/golang/workflow)
2. Создайте файл `название.mdc` в соответствующей папке
3. Опишите правило в формате Markdown
4. Добавьте ссылку на правило в `.cursorrules` (если нужно)
5. Создайте PR с описанием изменений

## Обновление правил

Правила обновляются итеративно на основе:
- Опыта команды
- Найденных проблем в code review
- Изменений в стандартах проекта
- Обратной связи разработчиков

### Процесс обновления

1. Создайте issue с описанием проблемы или предложением
2. Обсудите изменение с командой
3. Внесите изменения в соответствующий `.mdc` файл
4. Протестируйте на реальной задаче
5. Создайте PR с описанием изменений и примерами

## Полезные ссылки

- [Cursor Documentation](https://docs.cursor.com/)
- [Cursor Rules](https://docs.cursor.com/context/rules)
- [Cursor System Prompts (GitHub)](https://github.com/labac-dev/cursor-system-prompts)

## FAQ

**Q: Нужно ли настраивать что-то дополнительно?**  
A: Нет, правила применяются автоматически при работе с репозиторием.

**Q: Что делать, если Cursor игнорирует правило?**  
A: Используйте явное упоминание `@.cursorrules` в промпте или `@название-правила.mdc`.

**Q: Как проверить, что правило работает?**  
A: Попросите Cursor сгенерировать код и проверьте соответствие правилу в code review.

**Q: Можно ли отключить правило для конкретной задачи?**  
A: Да, укажите в промпте исключение, но это должно быть обосновано.

---

**Последнее обновление:** 10.11.2025

**Поддерживается командой разработки**

# Полезные ссылки

## Cursor

### Официальная документация
- [Cursor Documentation](https://docs.cursor.com/) - Основная документация Cursor
- [Cursor Rules](https://docs.cursor.com/context/rules) - Документация по правилам Cursor
- [Cursor CLI Cookbook - Code Review](https://docs.cursor.com/ru/cli/cookbook/code-review) - Практики code review с Cursor
- [Cursor Composer](https://docs.cursor.com/composer) - Документация по Composer mode

### Статьи и туториалы
- [Cursor System Prompts (GitHub)](https://github.com/labac-dev/cursor-system-prompts) — коллекция системных промптов для Cursor
- [The Anatomy of a Cursor Prompt (Medium)](https://medium.com/@johnmunn/the-anatomy-of-a-cursor-prompt-f7146f9bdd4e) — разбор устройства промптов для AI-инструментов
- [System Prompts and Models of AI Tools (GitHub)](https://github.com/x1xhlol/system-prompts-and-models-of-ai-tools?tab=readme-ov-file) — различные промпты и модели AI-инструментов
- [Cursor AI Code Review Tutorial (Medium)](https://medium.com/@yonatanmh/cursor-ai-code-review-tutorial-cc652aaab92e) — туториал по использованию Cursor для code review
- [Cursor CLI Cookbook - Code Review (docs.cursor.com)](https://docs.cursor.com/ru/cli/cookbook/code-review) — официальная документация по code review в Cursor

---

## Актуальные видеоматериалы и статьи по Cursor для командной разработки

### Видео

1. **[My Ultimate AI Coding Workflow (GitHub + Cursor Agents Setup) — GritAI Studio](https://www.youtube.com/watch?v=AggITrydtwk)**  
   Описание: GitHub MCP с Cursor Agents: идеи в Issues, параллельные агенты, PR review.

2. **[How I reduced 90% errors for my Cursor (Part 2) — AI Jason](https://www.youtube.com/watch?v=dF4uCZAY1tk)**  
   Описание: TDD и Memory Bank для минимизации ошибок в AI-кодировании.

3. **[L-12 | Code Review and Rules with Cursor AI — CTO Bhaiya](https://www.youtube.com/watch?v=ed0ymMUvbQk)**  
   Описание: Автоматизированный code review и создание custom .cursor/rules для команды.

4. **[Cursor AI workflow that will 10x your coding productivity — ZeroToProduct](https://www.youtube.com/watch?v=fOBWYsWJ_gk)**  
   Описание: Workflow для командной разработки: документация, APIs, БД, отладка.

5. **[Master Cursor AI IDE in 30 minutes: A Beginner's Guide to Advanced Development Workflows](https://www.youtube.com/watch?v=oFqBfWpWpfg)**  
   Описание: Быстрый гайд по продвинутым техникам Cursor и режиму Agent.

---

### Статьи и гайды

6. **[We Switched Our 5-Person Team to Cursor 2.0: ROI Report & Config Files — Skywork AI](https://skywork.ai/blog/agent/we-switched-our-5-person-team-to-cursor-2-0-roi-report-config-files/)**  
   Описание: Отчёт о миграции на Cursor: метрики, ROI 1233%, конфигурации.

7. **[Cursor 1.7 Collaboration Best Practices 2025: Slack, GitHub & Team Rules — Skywork AI](https://skywork.ai/blog/cursor-1-7-collaboration-best-practices-slack-github-team-rules/)**  
   Описание: Настройка Cursor для команды: Slack+GitHub, Team Rules, YAML конфиги.

8. **[Streamline Your Development Workflow with Cursor Slash Commands — Ezra Blocki](https://ezablocki.com/posts/cursor-slash-commands/)**  
   Описание: Slash Commands: кодирование процессов в .cursor/commands/ как Markdown.

9. **[Ultimate Cursor AI IDE Guide: Team Collaboration & Best Practices — Geeks Kai](https://geekskai.com/blog/ai/cursor-ide-tutorial-ai-powered-development-best-practices/)**  
   Описание: Комплексный гайд по Cursor для команд: features, MCP, best practices.

10. **[Manage Repos & Large Codebases in Cursor — Instructa.ai (Kevin Kern)](https://www.instructa.ai/blog/cursor-ai/how-to-multiple-repository-and-large-codebase-in-cursor)**  
    Описание: Работа с большими кодобазами: multi-root workspaces, Git worktrees.

11. **[AI-Enhanced Code Review | Developer Toolkit — Developer Toolkit AI](https://developertoolkit.ai/en/cursor-ide/lessons/code-review/)**  
    Описание: Code review с Cursor: стайл-гайды, GitHub MCP, Linear/Jira интеграция.

12. **[How to Reduce Errors in Cursor and Other AI Coding IDEs by 90% — Honest AI Engine](https://honestaiengine.com/how-to-reduce-errors-in-cursor-and-other-ai-coding-ides-by-90)**  
    Описание: Структурированное управление задачами для минимизации ошибок AI-кодирования.

13. **[Automatic Pull Request Reviewing with Cursor's Bugbot — Made with Love](https://madewithlove.com/blog/automatic-pull-request-reviewing-with-cursors-bugbot/)**  
    Описание: Bugbot: автоматизированный code reviewer от Cursor, $40/месяц.

14. **[Understanding Cursor Rules — Cursor 101](https://cursor101.com/cursor/rules)**  
    Описание: Синтаксис Cursor Rules: MDC формат, нумерация файлов, динамическая загрузка.

15. **[Git Integration in Cursor | Cursor.fan](https://cursor.fan/tutorial/HowTo/git-integration-in-cursor/)**  
    Описание: Git в Cursor: commit management, AI-генерация сообщений, @Git для diffs.

16. **[Cursor Pro – Master AI‑Powered Development](https://www.cursorpro.ai)**  
    Описание: Платная платформа с видеоуроками по Cursor для команд.

