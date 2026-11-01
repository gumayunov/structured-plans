# structured-plans

Скил для агентов, дополняющий workflow [superpowers](https://github.com/obra/superpowers):
дизайны, планы и прогресс лежат в одном каталоге с номером, а не разложены по датам.

```
docs/designs/
├── 000-widget-auth/         # план без фаз
│   ├── design.md
│   ├── plan.md
│   └── progress.md
└── 001-billing-export/      # план с фазами
    ├── design.md
    ├── phase-001-00.md
    ├── phase-001-01.md
    └── progress.md
```

Что меняет скил:

- куда сохранять дизайн и план: `docs/designs/<DDD>-<slug>/` вместо `docs/superpowers/specs/` и `docs/superpowers/plans/`;
- как нумеровать задачи: ID вида `T003-01-05` (дизайн, фаза, задача);
- где вести прогресс: `progress.md` со сводкой по фазам и чекбоксами задач;
- когда делить план на фазы: больше 10 задач или длиннее 2000 строк.

Содержание дизайна и структура плана остаются по скилам `brainstorming` и `writing-plans`. Старые
каталоги скил не трогает, перенос в `docs/designs/` выполняется по просьбе:
[`references/migration.md`](references/migration.md).

Инструкция для агента — [`SKILL.md`](SKILL.md), на русском, как и шаблоны файлов.

## Требования

- [superpowers](https://github.com/obra/superpowers) 7, установленный в том агенте, где работаете:
  установка у каждого агента своя. Скил опирается на его `brainstorming`, `writing-plans`,
  `executing-plans` и `subagent-driven-development`.
- `git`, `perl` и стандартные утилиты Unix: команды скила рассчитаны на macOS и Linux.

## Установка

```bash
git clone https://github.com/gumayunov/structured-plans.git ~/src/structured-plans
```

Затем ссылка на клон в каталог скилов агента. Имя ссылки должно быть `structured-plans`.

| Агент | Команда |
|-------|---------|
| Claude Code | `ln -s ~/src/structured-plans ~/.claude/skills/structured-plans` |
| Codex | `ln -s ~/src/structured-plans ~/.agents/skills/structured-plans` |
| OpenCode | `ln -s ~/src/structured-plans ~/.config/opencode/skills/structured-plans` |

Перезапустите агента. Обновление: `git -C ~/src/structured-plans pull`.

## Лицензия

[MIT](LICENSE)
