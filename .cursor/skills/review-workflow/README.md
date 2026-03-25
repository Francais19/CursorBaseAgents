# review-workflow

Используй для проверки Python-изменений перед релизом/мерджем.

## Смотреть в первую очередь
- correctness
- tests coverage for changed behavior
- typing and interface consistency
- error handling and observability
- complexity and maintainability
- backward compatibility
- docs and migration notes if needed

## Категоризация
- critical: дефект, который может сломать прод, безопасность или данные
- high: высокий риск регрессии или неверный контракт
- medium: поддерживаемость, неочевидный дефект, недостающий тест
- low: style и мелкие улучшения
