# RTK setup

Этот файл нужен, если в проекте используют RTK и вам сказали "поставь RTK", "инициализируй RTK для Cursor" или "посмотри, почему не работает `rtk gain`".

## Что такое RTK

RTK (`Rust Token Killer`) помогает экономить токены при работе AI-инструментов, перехватывая и переписывая команды.

Если совсем коротко:
- ставите `rtk`
- инициализируете его под нужный AI-инструмент
- перезапускаете терминал или Cursor
- проверяете, что всё работает

## Когда это нужно

Используйте эту инструкцию, если:
- команда `rtk` не найдена
- `rtk gain` падает или работает странно
- нужно подключить RTK к Cursor
- нужно проверить, что RTK вообще установлен правильно

## Важно

Если устанавливаете через Cargo, не используйте:

```bash
cargo install rtk
```

Это другой пакет.

Правильный вариант:

```bash
cargo install --git https://github.com/rtk-ai/rtk
```

## Установка

### Windows

Рекомендуемый путь на Windows:

1. Скачайте Windows-архив с `rtk.exe` из репозитория:

```text
https://github.com/rtk-ai/rtk
```

2. Распакуйте архив, например в:

```text
C:\Tools\rtk
```

3. Добавьте папку с `rtk.exe` в `PATH`.

4. Перезапустите PowerShell.

5. Проверьте установку:

```powershell
rtk --version
```

Ожидаемый результат: команда отрабатывает и показывает версию `rtk`.

### macOS / Linux

Через Homebrew:

```bash
brew install rtk
```

Быстрая установка:

```bash
curl -fsSL https://raw.githubusercontent.com/rtk-ai/rtk/refs/heads/master/install.sh | sh
```

Если нужно, добавьте путь в `PATH`:

```bash
echo 'export PATH="$HOME/.local/bin:$PATH"' >> ~/.zshrc
source ~/.zshrc
```

### Установка из исходников через Cargo

```bash
cargo install --git https://github.com/rtk-ai/rtk
```

## Как подключить RTK к Cursor

После установки выполните:

```bash
rtk init -g --agent cursor
```

После этого:
- перезапустите Cursor
- откройте новый терминал
- проверьте, что команды проходят через RTK

Пример:

```bash
git status
```

Если RTK настроен правильно, команда должна обрабатываться через него.

## Инициализация для разных AI-инструментов

Если вам нужен не только Cursor, а другой AI-инструмент, используйте один из вариантов ниже:

```bash
# 1. Install for your AI tool
rtk init -g                     # Claude Code / Copilot (default)
rtk init -g --gemini            # Gemini CLI
rtk init -g --codex             # Codex (OpenAI)
rtk init -g --agent cursor      # Cursor
rtk init --agent windsurf       # Windsurf
rtk init --agent cline          # Cline / Roo Code
```

Для этого проекта обычно нужен именно такой вариант:

```bash
rtk init -g --agent cursor
```

## Быстрая проверка

Запустите:

```bash
rtk --version
```

```bash
rtk gain
```

Что должно быть:
- `rtk --version` показывает установленную версию
- `rtk gain` не падает с ошибкой и показывает статистику

## Если `rtk gain` не работает

Самая частая причина: установлен не тот пакет.

Если ставили через Cargo и видите странное поведение, удалите и поставьте заново:

```bash
cargo uninstall rtk
```

Затем:

```bash
cargo install --git https://github.com/rtk-ai/rtk
```

Если ставили через Homebrew:

```bash
brew uninstall rtk
```

Потом установите заново.

## Где лежит конфиг

- Linux: `~/.config/rtk/config.toml`
- macOS: `~/Library/Application Support/rtk/config.toml`
- Windows: `%AppData%\rtk\config.toml`

Пример:

```toml
[hooks]
exclude_commands = ["curl", "playwright"]

[tee]
enabled = true
mode = "failures"
max_files = 20
```

## Полезные команды

```bash
rtk gain
```

Показывает общую статистику экономии токенов.

```bash
rtk gain --graph
```

Показывает ASCII-график по истории.

```bash
rtk gain --history
```

Показывает недавнюю историю.

```bash
rtk discover
```

Помогает найти команды, где RTK мог бы дать экономию.

## Если нужно удалить RTK

Homebrew:

```bash
brew uninstall rtk
```

Cargo:

```bash
cargo uninstall rtk
```

## Полезные ссылки

- Repository: `https://github.com/rtk-ai/rtk`
- Troubleshooting: `https://github.com/rtk-ai/rtk/blob/master/docs/TROUBLESHOOTING.md`
- Architecture: `https://github.com/rtk-ai/rtk/blob/master/ARCHITECTURE.md`
