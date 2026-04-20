# RTK: использование префикса в командах

Этот документ описывает **как** вызывать команды в терминале, когда в окружении доступен [RTK](https://github.com/rtk-ai/rtk) (Rust Token Killer): какие команды нужно явно префиксовать `rtk`, чем заменить `cat`/`grep`, и когда префикс не нужен.

Установка, инициализация под Cursor и диагностика — в отдельном файле: [`.cursor/rtk-setup.md`](../.cursor/rtk-setup.md).

## Зачем префикс

RTK перехватывает вывод типичных CLI-команд, **сжимает и фильтрует** его перед тем, как текст попадёт в контекст агента. Ожидаемый эффект: **меньше токенов (порядка 60–90%)** при небольшой задержке (заявлено менее 10 ms).

В этом репозитории для выполнения команд агентом принято использовать варианты с префиксом `rtk`, когда это возможно.

## Общее правило

Перед перечисленными ниже утилитами указывайте префикс **`rtk`**:

```text
rtk <исходная_команда_и_аргументы>
```

Если `rtk` не установлен или конкретная команда не распознаётся обёрткой, выполняйте **обычную** команду без префикса.

## Файловые операции

| Назначение | Пример |
|------------|--------|
| Список | `rtk ls` |
| Чтение файла | `rtk read <file>` |
| Поиск по шаблону | `rtk grep <pattern> <path>` |
| Поиск файлов | `rtk find <glob> <path>` |
| Сравнение | `rtk diff <a> <b>` |

**Замены:** используйте `rtk read <file>` вместо `cat`, `head` или `tail`. Используйте `rtk grep` вместо `grep` или `rg`.

## Git

`rtk git status`, `rtk git diff`, `rtk git log`, `rtk git add`, `rtk git commit`, `rtk git push`, `rtk git pull`.

## GitHub CLI

`rtk gh pr list`, `rtk gh pr view <n>`, `rtk gh issue list`, `rtk gh run list`.

## Тесты

`rtk cargo test`, `rtk pytest`, `rtk go test`, `rtk vitest run`, `rtk playwright test`.

## Сборка и линтеры

`rtk lint`, `rtk tsc`, `rtk cargo build`, `rtk cargo clippy`, `rtk ruff check`, `rtk golangci-lint run`, `rtk prettier --check .`, `rtk next build`.

## Контейнеры и Kubernetes

`rtk docker ps`, `rtk docker images`, `rtk docker logs <id>`, `rtk kubectl pods`, `rtk kubectl logs <pod>`.

## Пакетные менеджеры

`rtk pnpm list`, `rtk pip list`, `rtk pip outdated`, `rtk prisma generate`.

## Данные и окружение

`rtk json <file>`, `rtk curl <url>`, `rtk log <file>`, `rtk env`.

## Исключения (префикс не добавлять и не менять)

- Команда **уже** начинается с `rtk`.
- Конструкции с **heredoc** (`<<`): их не переписывать ради префикса.

## См. также

- [`.cursor/rtk-setup.md`](../.cursor/rtk-setup.md) — установка RTK, `rtk init` для Cursor, `rtk gain`, конфиг, типичные ошибки.
- Правило для агента: `.cursor/rules/rtk-usage.mdc`.
