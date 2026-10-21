# IA08: Deployment readiness, release and rollback

Team/project: [REPLACE]. Related issue/PR/release: [REPLACE]
Honest status: deployed / staging-ready / local only with a plan: [REPLACE]
Sketch: put the redacted copy here as `deployment-sketch-redacted.jpg`.

## Configuration (placeholders only, never real secrets)
| Variable | Purpose | Secret? | Placeholder |
|---|---|---|---|
| DJANGO_SECRET_KEY | signing | yes | <set on platform> |
| DATABASE_URL | database | yes | <set on platform> |
| ALLOWED_HOSTS | host allow-list | no | [REPLACE] |
| CORS_ALLOWED_ORIGINS | front-end origin | no | [REPLACE] |
(Match this to `.env.example` in the project.)

## Build and run
[REPLACE: the exact commands you ran, migration notes, platform settings, deployment URL if any]

## Smoke tests (6+)
1. [REPLACE: valid add returns 201]
2. [REPLACE: invalid input returns 400]
3. [REPLACE: access control]
4. [REPLACE: system error expectation]

## Failure and rollback
Symptom, likely cause, evidence to inspect, immediate response, rollback, how recovery is confirmed: [REPLACE]

## Release evidence
Tag, release note, commit hash, PR, CI: [REPLACE]
Logs, health checks, backups, support notes, known limitations: [REPLACE]

Video link: [REPLACE]
