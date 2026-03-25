# security-guidelines

Используй для security review Python/API кода.

## Чеклист
- validation на boundary
- auth/authz
- secrets handling
- unsafe eval/deserialization
- subprocess/shell execution
- SQL queries и ORM filters
- file paths and uploads
- SSRF/open redirect/CORS risks
- logging without secrets
