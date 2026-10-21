| Case | Code | User message | Logging |
|---|---|---|---|
| Invalid input / duplicate email | `VALIDATION_ERROR` | Please check the highlighted fields. If the email is already registered, use a different email. | Record the validation failure without logging personal details. |
| No or expired token | `AUTHENTICATION_REQUIRED` | Your login is missing or has expired. Please log in again. | Record the authentication failure without logging the token. |
| Staff, Auditor or client user | `PERMISSION_DENIED` | You don’t have permission to add clients. | Record the user ID, attempted action, and access denial. |
| Database failure | `INTERNAL_SERVER_ERROR` | We couldn’t save the client. Please try again later. | Record technical exception details in restricted server logs. |
