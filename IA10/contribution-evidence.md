# IA10: Final individual defence and contribution

Team/project: DE-SEGP-2 / Client Tracking System, Add Client feature.
Repos: Individual — https://github.com/ajoshua1256-cyber/My-DCIT208-Individual-portfolio. Team repository — link not yet recorded.
Final release tag: Not yet confirmed.

## My contribution (one real thing)
What I did and why it mattered: I prepared the Add Client API test plan, documenting inputs and expected responses for successful registration, invalid input, missing authentication, incorrect permissions, duplicate emails, and database failure. This gives the team clear checks to carry out before accepting the feature.

Linked requirement/story/NFR/issue: The requirement is to register a client with a unique email and an automatically generated reference number. The linked story is: As a Project Manager, I want to register a client so that their details and projects can be tracked under one record. IA03 records the traceability. An issue link has not yet been recorded.

Evidence (issue, PR, commit, review comment, test, release): The test-plan document is available at https://github.com/ajoshua1256-cyber/My-DCIT208-Individual-portfolio/blob/main/IA05/TEST_PLAN.md. The related error model is in IA05/ERROR_MODEL.md. A specific commit or PR link still needs to be recorded.

## System impact and verification
Where it fits (request flow, risk reduced, users and value): My test plan covers the request from the Add Client form to POST /api/v1/clients/ and the response returned by the server. The checks target duplicate records, unauthorised creation, and unclear failure responses. They support reliable registration for Admin and Project Manager users.

Test, review or validation evidence: The test plan records seven planned checks, including whether a successful response contains reference_no. Execution results and review evidence have not yet been attached, so I am not claiming that the tests have passed.

One honest limitation: The test plan describes expected behaviour, but it does not yet provide execution evidence showing how the API actually behaves.

One realistic next improvement: Run the planned checks against the local API, record actual responses, compare them with expectations, and attach evidence with login tokens and personal information removed.

## D10 cross-reference (non-confidential)
Role, commits, PRs, reviewed PRs, issues owned, documents, tests, team contributions: This contribution focuses on test planning and validation documentation. Documents include IA05/TEST_PLAN.md and IA05/ERROR_MODEL.md. Seven API checks are planned. Commit links, PRs, reviewed PRs, and owned issues have not yet been recorded here. My contribution supports the team's verification of the Add Client feature.

Problem solved / designed / implemented / tested / would improve: I addressed the need for clear API verification checks by documenting test inputs and expected outcomes. This contribution concerns test design and documentation. API execution remains planned. I would improve it by adding recorded results and checking duplicate emails with different capital letters.

One code file, one test file, one requirement, one design decision I can defend: Code file — the exact Add Client serializer or view file must still be identified in the team repository. Test file — IA05/TEST_PLAN.md, which is a manual test plan rather than an automated test file. Requirement — register a client with a unique email and reference number. Design decision — use a Django REST Framework API with a React front end, as documented in IA04/adr.md.

Responsible AI use and what I learned without AI: I used ChatGPT to help draft explanations and improve the wording of portfolio entries. AI-generated suggestions still require checking against the actual project. I have not yet recorded a specific example of work completed independently without AI.
