# Proposed System Architecture Diagram

```mermaid
flowchart LR
    A[Authorized DSWD Personnel / System Process] --> B[dxCLOUD]
    B --> C[Notification Service]
    C --> D[SMS Gateway]
    C --> E[Email / Approved Digital Channel]
    D --> F[Beneficiary]
    E --> F
    C --> G[(Notification Log)]
    G --> H[Monitoring / Audit]
```

## Notes

- dxCLOUD is the source of authorized application-status information for this academic design.
- The Notification Service is the proposed integration layer.
- Communication providers are external delivery components.
- Notification logs support monitoring and auditing.
