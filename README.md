# postanovka

Скилл для Claude Code: пишет **Постановку** задачи по уже состоявшемуся обсуждению
и публикует её в локальный трекер (`.scratch/<slug>/spec.md`).

Разделы артефакта: Цель, Контекст, Процесс AS-IS (опционально), Процесс TO-BE,
Требования, Критерии приёмки, Открытые вопросы. Язык — русский. Без интервью:
скилл синтезирует то, что уже сказано, а не собирает требования заново.

Подробности флоу, отличия от `/to-spec` и правила публикации — в
[postanovka/README.md](postanovka/README.md).

## Установка

```bash
git clone https://github.com/Qloker/claude-skill-postanovka.git /tmp/claude-skill-postanovka && mkdir -p ~/.claude/skills && cp -R /tmp/claude-skill-postanovka/postanovka ~/.claude/skills/
```

Проверить: перезапустить сессию Claude Code и ввести `/postanovka`.

Альтернатива — держать репозиторий в постоянной папке и поставить симлинк, тогда
`git pull` сразу обновляет скилл:

```bash
ln -s "$PWD/postanovka" ~/.claude/skills/postanovka
```

## Обновление

```bash
git pull && cp -R postanovka ~/.claude/skills/
```

При установке симлинком достаточно `git pull`.

## Состав

| Файл | Назначение |
| --- | --- |
| `postanovka/SKILL.md` | Сам скилл. Единственный файл, который читает модель |
| `postanovka/README.md` | Документация для человека: флоу, команды, структура артефакта |

`disable-model-invocation: true` — скилл не запускается сам, нужен явный ввод
`/postanovka`. Артефакт пишется в файл, и самопроизвольная запись нежелательна.
