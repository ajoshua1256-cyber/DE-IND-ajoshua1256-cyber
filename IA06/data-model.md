# IA06: Data model for Add Client

Team/project: [REPLACE]. Team issue: [REPLACE]. Repos: [REPLACE]
Sketch: put the redacted ERD here as `erd-redacted.jpg`.

## Entities (check against backend/apps/clients/models.py)
- clients: id PK, reference_no unique, client_type, name, email unique, phone, address, city, country, notes, is_active, created_by FK -> users, created_at, updated_at
- client_contacts: id PK, client FK, full_name, role_title, email, phone, is_primary, timestamps

## Relationships
One client has many contacts. One user creates many clients. [REPLACE: explain in your words]

## Constraints and who enforces them
| Rule | Front end | API | Database |
|---|---|---|---|
| name required | [REPLACE] | [REPLACE] | [REPLACE] |
| email unique | [REPLACE] | [REPLACE] | [REPLACE] |

## Synthetic sample records
SYNTHETIC. [REPLACE: two realistic fake records for two entities]

## State change walkthrough
[REPLACE: input, data touched, rule applied, storage, response]

## Privacy
Sensitive item: [REPLACE]. Who may view/edit: [REPLACE]. What must not enter AI tools: [REPLACE]

## Two data failures
1. [REPLACE]
2. [REPLACE]

## Test ideas (6+)
1. [REPLACE]

Video link: [REPLACE]
