# IA01: Request flow for Add Client

Status: [REPLACE: implemented / planned, be honest]
Sketch: put the redacted copy here as `request-flow-redacted.jpg` (name and ID covered).

Path: User -> Browser (React app) -> URL /clients -> DNS -> HTTPS -> Django API (`POST /api/v1/clients/`) -> permission check -> serializer validation -> PostgreSQL insert (clients, client_contacts) -> audit log -> JSON 201 -> screen refresh.
Failure point: database down at the insert. Privacy concern: client email and phone.

Write 900-1200 words total. Answer each question in your own words.

1. User device: [REPLACE]
2. Browser or mobile app: [REPLACE]
3. URL / route / screen / endpoint: screen Clients, endpoint `POST /api/v1/clients/`
4. Protocol: [REPLACE: HTTPS in production, HTTP on localhost]
5. Data sent: JSON with client_type, name, email, phone, optional address, city, country, notes, contacts; Bearer token in header
6. Request validation: [REPLACE: front-end checks vs serializer checks vs role check]
7. Database table / service: `clients` (and `client_contacts`)
8. Returned response: 201 with the saved client including reference_no
9. Validation failure: 400 with field errors, nothing saved
10. Database outage: [REPLACE: what you observed or what is planned]
11. 500 concurrent users: [REPLACE: honest answer, planned vs done]
12. Security/privacy concern: [REPLACE]

Video link: [REPLACE]
