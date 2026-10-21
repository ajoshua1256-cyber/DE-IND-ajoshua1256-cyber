| Criterion | A: DRF API + React | B: Server-rendered pages |
|---|---|---|
| Team skill | Requires React, JavaScript, Python, and DRF skills; confirm team experience. | Requires Python, Django templates, HTML, and CSS skills; confirm team experience. |
| Security/privacy | JWT authentication and API permissions; requires secure token handling and CORS configuration. | Django sessions and CSRF protection; requires server-side permission checks. |
| Maintainability | Separates interface and back-end logic; API changes require coordination. | Keeps page rendering and back-end logic together; simpler for a small application. |
| Deployment/cost | Separate front end and back end to deploy; hosting cost needs assessment. | One main application to deploy alongside the database; hosting cost needs assessment. |
| Performance/scale | Front end and API can scale separately; performance requires testing. | Can scale with suitable infrastructure; performance requires testing. |
