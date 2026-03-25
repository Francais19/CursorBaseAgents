# /review

Используй перед релизом/мерджем или после серии изменений.

## Workflow
1. Reviewer анализирует diff или указанные файлы.
2. При security-сигналах подключай Security Auditor.
3. Для must-fix находок подключай Debugger только после явного подтверждения пользователя.
4. Test Runner проверяет систему после фиксов.

## Выход
- findings by severity
- must-fix / should-fix / nice-to-have
- verification summary
