# orchestration

Используй для `/orchestrate` и сложных Python-изменений: feature, subsystem, migration-heavy task, auth, billing, queues, integrations.

## Фазы
1. План: разбей задачу на подзадачи с ID и критериями приемки.
2. Исполнение: делай по одной подзадаче за раз.
3. Проверка: после каждой подзадачи запускай tests/review.
4. Фиксы: при падениях или review findings исправляй до лимита попыток.
5. Финализация: подготовь итоговый отчет и список рисков.

## Правила
- каждая подзадача должна иметь observable result
- если задача слишком большая, выделяй phases и safe checkpoints
- для risky changes предлагай feature flag или staged rollout
