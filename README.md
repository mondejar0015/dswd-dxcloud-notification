# DSWD dxCLOUD Beneficiary Notification Feature

## IT PROF EL 4 – Advanced System Integration and Architecture

**Semester Project – Week 6 Documentation Submission**

- Partner 1: Eric Charls M. Mondejar
- Partner 2: Reymar Obenza
- Program / Block: BS-IT, Block-A
- Proposed System: DSWD dxCLOUD
- Proposed Feature: Beneficiary Notification Feature
- Project Stage: Planning, Security Evaluation, and Architecture

## Project Overview

This project proposes an additional beneficiary notification feature for DSWD dxCLOUD. The feature is intended to automatically inform authorized beneficiaries about the status of their assistance application through SMS or another approved digital communication channel.

This repository is a Week 6 planning and architecture deliverable. It does not claim to implement or modify the actual DSWD dxCLOUD production system.

## Problem

Beneficiaries may have difficulty knowing whether an assistance application has been received, processed, approved, or requires further action. The proposed feature provides status updates when an authorized application status changes.

## Proposed Objective

1. Detect relevant application-status changes.
2. Verify authorized beneficiary contact information.
3. Send minimal status notifications through an approved digital service.
4. Record notification attempts and delivery status.
5. Keep notification failures from disrupting the core application process.

## Security Considerations

- Authentication and role-based access control
- Verified contact information
- Data minimization
- HTTPS/TLS for communication
- Least-privilege service access
- Audit and delivery logs
- Secure secret management
- Failure isolation and controlled retries

## Proposed Architecture

**Authorized System Process → dxCLOUD → Notification Service → SMS/Email Gateway → Beneficiary**

See the [System Architecture](diagrams/system-architecture.md) and [Data Flow](diagrams/data-flow.md).

## Repository Structure

```text
dswd-dxcloud-notification/
├── README.md
├── .gitignore
├── docs/
│   ├── planning.md
│   ├── security.md
│   ├── architecture.md
│   └── workflow.md
└── diagrams/
    ├── system-architecture.md
    └── data-flow.md
```

## Scope and Limitation

This Week 6 repository contains planning, security evaluation, architecture, workflow, and data-flow documentation. It does not contain production credentials, real beneficiary information, live SMS credentials, or access to a production environment.

A future implementation phase can use mock data and a sandbox notification provider for testing.
