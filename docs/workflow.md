# Part 4 – Proposed System Workflow

## Normal Flow

1. An authorized process updates an assistance application's status.
2. The system determines whether the new status requires notification.
3. The notification service validates the application, beneficiary, notification type, and authorized contact channel.
4. An approved minimal message is generated.
5. The message is sent through the selected provider.
6. The provider returns an operational result.
7. The notification record is updated with the result and timestamp.

## Failure Flow

```text
Send Request
     |
     v
 Provider Failure
     |
     v
 Record Failure
     |
     +----> Controlled Retry
     |
     +----> Manual Review if Retry Limit Reached
```

A notification failure should not reverse or block the underlying application-status update.

## Duplicate Notification Protection

A future implementation should use an idempotency mechanism or unique notification key to reduce accidental duplicate messages.

Example conceptual key:

`application_id + status + notification_type`

## Example Notification Templates

**Application Received**

> Your assistance application has been received. Please wait for further updates through the official communication channel.

**Under Review**

> Your assistance application is currently under review. Please wait for the next update.

**Additional Information Required**

> Your assistance application requires additional information. Please follow the official instructions provided by the responsible office.

**Approved**

> Your assistance application has been approved. Please follow the official instructions for the next step.

These are sample academic templates only. Final wording should follow the organization's approved communication policy.

## Audit Events

Potential events include:

- notification_requested
- notification_validated
- notification_queued
- notification_sent
- notification_delivered
- notification_failed
- notification_retried

Logs should contain only operational information required for security, monitoring, and troubleshooting.
