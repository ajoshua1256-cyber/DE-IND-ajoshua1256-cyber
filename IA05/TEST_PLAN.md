| # | Test | Input | Expected status | Expected response | Status (Run / Planned) |
|---|---|---|---|---|---|
| 1 | Valid request | all fields correct | 201 | matches success example | Planned |
| 2 | Missing or invalid field | no name | 400 | field error | Planned |
| 3 | Unauthorized caller | no token | 401 | authentication error; no client saved | Planned |
| 4 | Wrong role | Staff token | 403 | permission denied; no client saved | Planned |
| 5 | Duplicate | same email twice | 400 | email already registered; no additional client saved | Planned |
| 6 | Dependency failure | database stopped | 500 | safe message | Planned |
| 7 | Response shape | valid request | 201 | includes reference_no | Planned |
