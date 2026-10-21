# IA07: Test evidence, PR review and CI

Team/project: DE-SEGP-2 / Client Tracking System, Add Client feature.

Feature status: Implementation is described in the project documentation; verification is planned.

Related issue and PR: Not yet linked.

## Feature context

User: Admin or Project Manager.

Requirement: Register a client with a unique email and an automatically generated reference number.

Story: As a Project Manager, I want to register a client so that their details and projects can be tracked under one record.

Acceptance criteria:
AC1: Valid details submitted by an authorised user create a client, return HTTP 201, and include a unique reference number.
AC2: An existing email is rejected with HTTP 400, and no additional client record is created.
AC3: A Staff user cannot create a client and receives HTTP 403.

Client value: The feature keeps customer details organised and allows projects to be associated with the correct client.

## Test cases

| # | Type | Starting condition | Action | Test data | Expected | Evidence | Status |
|---|---|---|---|---|---|---|---|
| 1 | Normal | Project Manager logged in; email unused | Submit valid details to POST /api/v1/clients/ | Synthetic company, unused email, and phone | HTTP 201; saved client includes reference_no | Not yet attached | Planned |
| 2 | Invalid input | Project Manager logged in | Submit an invalid email | Synthetic email: invalid-email | HTTP 400; email field error; no client saved | Not yet attached | Planned |
| 3 | Edge | Project Manager logged in; email unused | Submit a name containing exactly 200 characters | Synthetic 200-character name; other fields valid | HTTP 201; full name saved | Not yet attached | Planned |
| 4 | Authorization / security | Staff user logged in | Submit otherwise valid client details | Synthetic client and unused email | HTTP 403; no client saved | Not yet attached | Planned |
| 5 | Failure / dependency | Development database stopped; authorised token available | Submit valid client details | Synthetic client details | Server error; no misleading success response or new client record | Not yet attached | Planned |
| 6 | Regression | A client with info@test-company.example already exists | Submit INFO@TEST-COMPANY.EXAMPLE for another client | Synthetic email differing only in capitalisation | Duplicate rejected with HTTP 400; no HTTP 500 or additional record | Not yet attached | Planned |

Use "Run" only for tests actually executed, with evidence attached. Record the actual result and whether it passed or failed.

## Test data

Synthetic only. Use Test Company Ltd, info@test-company.example, and a made-up phone value within the permitted length.

These values allow repeatable checks without exposing real client information. Use separate unused emails for independent success tests. Reuse an email deliberately for duplicate tests. Generate the 200-character name precisely so the boundary test is repeatable.

## PR review checklist

Requirement fit: Confirm that the change supports client registration and its acceptance criteria.

Validation: Check required fields, email format, length limits, duplicate handling, and reference-number generation.

Tests: Check normal, invalid, boundary, permission, dependency-failure, and regression scenarios. Separate expected behaviour from observed results.

Data risk: Confirm that test fixtures and screenshots contain synthetic information and that failed requests do not leave partial client records.

Security: Check server-side permissions, authentication, account scoping, and safe error responses. Confirm that no credentials or tokens are committed.

Documentation: Check that API examples, error descriptions, and setup instructions match the change.

AI disclosure: Record AI assistance and explain how suggestions were checked against the project.

System impact: Review effects on the client list, related contacts, audit logging, database changes, and existing API consumers.

Review evidence: No completed PR review is claimed until a real review comment or review link is attached.

## CI

No CI run has been verified.

Proposed commands, run from the backend directory with project dependencies and test settings configured:

python manage.py check
python manage.py makemigrations --check --dry-run
python manage.py test

These commands check Django configuration, detect model changes without migrations, and run discovered tests. The team must confirm the actual test runner and ensure the Add Client checks exist as automated tests.

The CI workflow should provide a disposable test database, use synthetic data, and report failures on pull requests. Attach a real workflow-run link and inspect its results before claiming a pass.

## Likely defect

Reproduction: Create a client with info@test-company.example, then submit another client using INFO@TEST-COMPANY.EXAMPLE.

Possible user-visible result: The earlier duplicate check may accept the differently capitalised email. Lowercasing during saving could then cause a database uniqueness error and HTTP 500 instead of a helpful validation response.

Evidence: This is a concern identified in the project documentation. Reproduction evidence has not yet been attached.

Fix or test: Normalise emails consistently before checking uniqueness, enforce the agreed uniqueness rule at the database level, and handle conflicts safely. Add a regression test confirming that the second request returns HTTP 400 and creates no additional record.

## Video link

Not yet recorded.
