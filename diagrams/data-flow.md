# Proposed Data Flow Diagram

```mermaid
flowchart TD
    A[Application Status Update] --> B{Notification Required?}
    B -- No --> C[Continue Core Workflow]
    B -- Yes --> D[Validate Beneficiary and Contact]
    D --> E{Valid and Authorized?}
    E -- No --> F[Reject Request and Log Event]
    E -- Yes --> G[Create Minimal Notification]
    G --> H[Send to Approved Gateway]
    H --> I{Delivery Accepted?}
    I -- Yes --> J[Record Sent / Delivery Status]
    I -- No --> K[Record Failure]
    K --> L[Controlled Retry or Manual Handling]
    J --> M[Beneficiary]
```

## Data-Minimization Principle

Only information required for the notification should cross the integration boundary. The design should avoid sending unnecessary beneficiary details to the communication provider.
