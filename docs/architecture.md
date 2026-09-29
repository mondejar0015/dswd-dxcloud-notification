# Part 3 – System Integration and Architecture

## Architectural Goal

Add a notification integration around the existing application-status process. The notification component should be loosely coupled so communication failures do not interrupt beneficiary application processing.

## Components

### Authorized System / DSWD Personnel
Responsible for authorized application processing and status changes.

### dxCLOUD
Represents the existing application/data environment used as the source of authorized application-status information for this academic design.

### Notification Service
A proposed integration component that receives approved status-change events, validates requests, selects a channel, prepares a minimal message, communicates with the provider, and records outcomes.

### Communication Gateway
An SMS, email, or other approved digital communication provider.

### Beneficiary
The intended recipient of the status notification.

## Integration Pattern

```text
Application Status Change
          |
          v
       dxCLOUD
          |
          v
 Notification Service
       /       \\
      v         v
 SMS Gateway  Email Service
       \\       /
          v   v
     Delivery Status Log
```

## Logical Responsibilities

| Component | Responsibility |
|---|---|
| dxCLOUD | Maintain/process authorized application information |
| Notification Service | Validate and route notification requests |
| Gateway | Deliver notification |
| Notification Log | Record operational outcome |
| Monitoring | Detect failures and abnormal behavior |

## Loose Coupling

The core application should not depend on successful SMS/email delivery to complete its own transaction.

```text
Application Update
      |
      +----> Core transaction completes
      |
      +----> Notification request queued
                    |
                    +----> Sent
                    |
                    +----> Failed -> Logged -> Retry/Manual Handling
```

## Proposed API-Level Interaction

A future implementation could use an internal endpoint such as `POST /notifications`.

Example conceptual request:

```json
{
  "application_id": "APP-000001",
  "beneficiary_id": "BEN-000001",
  "event_type": "STATUS_UPDATED",
  "status": "UNDER_REVIEW",
  "channel": "SMS"
}
```

This is illustrative only and does not represent an actual dxCLOUD API.

## Data Minimization

The notification service should receive only what it needs to determine the recipient, approved status message, communication channel, and operational record. It should not copy an entire beneficiary profile unless explicitly required and authorized.

## Scalability

Future extensions may include message queues, retry workers, multiple providers, monitoring dashboards, rate limiting, provider failover, and notification templates.
