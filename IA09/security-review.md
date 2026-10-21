# IA09: Security, privacy and maintainability review

Team/project: DE-SEGP-2 / Client Tracking System, Add Client feature.

Issue/PR: Not yet linked.

Requirement/story and two acceptance criteria:
As a Project Manager, I want to register a client so that their details and projects can be tracked under one record.

AC1: An authenticated Admin or Project Manager can submit valid details with an unused email, creating a client with a unique reference number and an audit entry.

AC2: A Staff or Auditor user attempting to create a client receives HTTP 403, and no client record is created.

Sketch: Add the redacted architecture sketch as sketch-redacted.jpg. Remove real client details, credentials, and tokens before uploading.

## Data inventory (synthetic only)

| Item | Purpose | Sensitivity | Storage | Access | Synthetic? |
|---|---|---|---|---|---|
| name | Identify the client | Medium | clients | Internal roles can view; Admin and Project Manager can edit | yes |
| email | Contact the client and enforce email uniqueness | High | clients | Internal roles can view; Admin and Project Manager can edit | yes |
| phone | Contact the client | High | clients | Internal roles can view; Admin and Project Manager can edit | yes |

Use made-up records only. Client users access their own information through separately scoped endpoints.

## Access matrix

The entries below follow the project documentation and still require verification against backend/apps/accounts/permissions.py and the relevant endpoints. Delete means deactivate. Export permissions are not confirmed.

| Role | Create | View | Update | Delete | Export |
|---|---|---|---|---|---|
| Admin | Yes | Yes | Yes | Yes, deactivate | Unverified |
| Project Manager | Yes | Yes | Yes | Yes, deactivate | Unverified |
| Staff | No | Yes | No | No | Unverified |
| Auditor | No | Yes | No | No | Unverified |

## Abuse case

A Project Manager could create fake clients or change a contact email to redirect notifications. This could produce inaccurate records or expose information to the wrong person.

Role permissions restrict who can make changes. Audit logging records the actor and activity so suspicious changes can be investigated. Authorised users can still misuse their access, so regular audit review is necessary. Requiring approval for sensitive contact changes is a possible future improvement.

## Failure

If a login token expires while the form is open, the API returns HTTP 401 and the application should refresh the token or request login. The rejected request should create no client record, and existing records should remain unchanged.

Whether the form preserves unsaved entries needs testing. Authentication failures should be logged without recording tokens or personal information. After login, the user should check whether the client already exists before resubmitting.

## Checks (5+)

All checks below are planned unless execution evidence is attached.

1. Submit valid details as an Admin or Project Manager; expect HTTP 201 and a reference number.
2. Attempt creation as Staff; expect HTTP 403 and no new record.
3. Attempt creation as Auditor; expect HTTP 403 and no new record.
4. Submit without a token or with an expired token; expect HTTP 401 and no new record.
5. Submit an existing email; expect HTTP 400 and no additional record.
6. Submit the same email with different capital letters; verify that it is rejected without HTTP 500.
7. Confirm that successful creation produces an audit entry identifying the actor.
8. Confirm that a client user cannot access the general client list or another client's information.
9. Check that repository files contain no passwords, secret keys, or login tokens.
10. Confirm that production errors do not expose stack traces when DJANGO_DEBUG=false.

## Maintainer handoff note

Configuration: Review authentication, role permissions, database settings, allowed origins, and production logging. Keep secrets outside the repository. Set DJANGO_DEBUG=false and MONITOR_ALLOW_PRIVATE_URLS=false in production.

Limitation: Phone numbers are required but their format and uniqueness are not enforced. Export permissions and preservation of unsaved form entries remain unverified.

Technical debt: Email uniqueness checking may treat capital letters differently before email addresses are lowercased during saving. This needs testing. The endpoint relies on the default rate throttle rather than a dedicated limit.

Future improvement: Make email normalisation and uniqueness checks consistent, agree on phone-validation requirements, and add automated permission and failure tests. Review rate limits using measured usage.

Video link: Not yet recorded.
