# API contract: Add client

Team issue: [REPLACE]. Requirement/story: [REPLACE]. NFR: [REPLACE]

Operation: create client
Method and endpoint: `POST /api/v1/clients/`
Caller: React front end. Provider: Django REST API.
Authentication: Bearer JWT. Authorization: Admin and Project Manager only.
Headers: Authorization, Content-Type: application/json

## Request fields
| Field | Type | Required | Meaning |
|---|---|---|---|
| client_type | string (individual, company) | yes | kind of client |
| name | string, max 200 | yes | client name |
| email | string, valid email, max 254, unique | yes | contact email |
| phone | string, max 20 | yes | contact phone |
| address, city | string | no | [REPLACE] |
| country | string | no | default Ghana |
| notes | string | no | free text |
| contacts | list | no | nested contact records |

(Check each row against `backend/apps/clients/serializers.py` before keeping it.)

## Validation rules
| # | Rule | Type | Checked by |
|---|---|---|---|
| 1 | client_type must be individual or company | format | serializer |
| 2 | name required, max 200 | format | serializer |
| 3 | email valid format | format | serializer |
| 4 | email must be unique | business | serializer validator + database |
| 5 | role must be Admin or Project Manager | business | permission class |

## Success
Status 201. Body: see examples/success-response.json. Explain each field: [REPLACE]. Next UI display: [REPLACE]

## Duplicates and retries
[REPLACE: explain the unique email constraint, double-click behaviour, and when retry is safe or unsafe]

## Open question or trade-off
[REPLACE]
