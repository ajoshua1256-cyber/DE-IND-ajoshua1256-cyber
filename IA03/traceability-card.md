# IA03: Use-case-to-story traceability card

Team / project / client domain: 
Date: 21/10/26
Source statement or requirement ID: 


## Use case: Register a client
- Actor: Project Manager or Admin
- Goal:  Register a client so their details and projects can be tracked under one record.
- Trigger: A new person or organisation becomes a customer.
- Preconditions:  A client record exists with a reference number, the creator’s details, and an audit entry.
- Main flow: 1) Open Clients. 2) Add. 3) Fill the form. 4) Submit. 5) System validates and saves. 6) System assigns a reference number. 7) List refreshes.
- Alternate flow: The user clicks Cancel before submitting the form. The registration stops, and nothing is saved.
- Exception flow:  The user submits a form with missing required details, an invalid email, or an email that already exists. 
- Postconditions: After successful registration, the client is saved with a unique reference number. 

## Story
As a Project Manager, I want to register a client so that their details and projects can be tracked under one record.

## Acceptance criteria
AC1 (success): Given I am logged in as an Admin or Project Manager, when I submit valid client details with an unused email, then the system saves the client, assigns a unique reference number, and displays the client in the list.
## NFR
At least 95% of add-client requests should finish in under 2 seconds with up to 50 concurrent users.
## Traceability row
| Source | Use case | Story | NFR | Issue title and URL | AC | Test name | Status |
|---|---|---|---|---|---|---|---|
| IA02 requirement memo | Register client | Project Manager registers a client to track their details and projects | 95% of requests under 2 seconds with up to 50 concurrent users | Register client with unique email and reference number; issue URL not yet linked | AC1, AC2 | Valid client registration; duplicate email rejection | Planned |

## Request-flow reasoning
Device and interface: Staff laptop using Chrome and the React application.

Screen and endpoint: Clients screen; POST /api/v1/clients/.

Data sent: Client type, name, email, phone, and any optional details entered, with a Bearer login token in the request header.

Validation: The form checks required fields. The API checks field requirements, email format, email uniqueness, and whether the user is an Admin or Project Manager.

Storage: The clients table, with related contact records in client_contacts when contacts are provided.

Response: HTTP 201 with the saved client details and generated reference number.

Validation failure: HTTP 400 with field errors; no new client is saved.

Outage: If the database is unavailable, saving fails and the user receives a server error.

Protected data and action: Client contact information is personal data. Only authorised roles may register clients, and the system records the action in the audit log.
