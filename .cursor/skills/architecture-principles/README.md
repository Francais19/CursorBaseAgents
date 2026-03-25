# architecture-principles

Архитектурные принципы для Python-проектов.

## Предпочтения
- явные зависимости лучше неявных
- доменная логика отдельно от transport/web слоя
- side effects на краях системы
- pydantic/dataclass models использовать осознанно
- не смешивать orchestration и business rules в route handlers
- prefer composition over god-objects
