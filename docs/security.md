# Part 2 – Security Evaluation

## Information Used

- beneficiary identifier
- application identifier
- application status
- authorized contact channel
- notification type
- delivery status
- timestamps
- technical failure information

The notification service should not receive unrelated beneficiary information.

## Main Risks and Controls

### Unauthorized Access
**Risk:** An unauthorized person or service accesses beneficiary or application information.

**Control:** authentication, RBAC, least privilege, and protected service credentials.

### Wrong Recipient
**Risk:** Incorrect or outdated contact information exposes an application status to another person.

**Control:** use verified contact information and validate the beneficiary/contact association.

### Sensitive Information Exposure
**Risk:** A message reveals more personal information than necessary.

**Control:** use short status-oriented messages and avoid unnecessary personal, financial, or case details.

### Transmission Exposure
**Risk:** Information is exposed between system components.

**Control:** HTTPS/TLS and secure provider connections.

### Excessive Privileges
**Risk:** The notification service has more permissions than needed.

**Control:** narrowly scoped service accounts and API/database permissions.

### Missing Audit Trail
**Risk:** Administrators cannot determine what happened to a notification.

**Control:** retain appropriate operational audit records without unnecessary sensitive data.

### Provider Failure
**Risk:** An SMS/email provider becomes unavailable.

**Control:** failure logging, controlled retries, monitoring, and separation from the core transaction.

## Security Controls

| Control | Purpose |
|---|---|
| Authentication | Prevent unauthorized access |
| RBAC | Restrict functions by role |
| Verified contacts | Reduce misdirected notifications |
| Data minimization | Limit information exposure |
| HTTPS/TLS | Protect data in transit |
| Least privilege | Limit service permissions |
| Audit logs | Support accountability |
| Retry/failure handling | Improve reliability |
| Secret management | Protect provider credentials |
| Input validation | Reduce malformed/unauthorized requests |

## Security Principles

1. **Confidentiality** – protect beneficiary information.
2. **Integrity** – notifications correspond to legitimate status changes.
3. **Availability** – notification failures do not bring down the core workflow.
4. **Accountability** – retain appropriate operational records.
5. **Privacy by Design** – expose only the minimum information necessary.

## Validation Checklist

- [ ] Authorized users/services only
- [ ] Verified beneficiary contact details
- [ ] Minimal notification content
- [ ] Encrypted communication
- [ ] Secure API credentials
- [ ] No unnecessary sensitive data in logs
- [ ] Failed notifications recorded
- [ ] Controlled retries
- [ ] Limited service permissions
- [ ] Auditable notification events
