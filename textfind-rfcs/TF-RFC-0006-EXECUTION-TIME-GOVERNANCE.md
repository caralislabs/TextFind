# TF-RFC-0006

## Execution-Time Governance for Agentic Systems

### A Runtime Control Architecture for AI Execution

------------------------------------------------------------------------

**Status:** Draft\
**Version:** 1.1\
**Author:** Nicolae Dumitru Caralicea\
**Organization:** CaralisLabs / TextFind\
**Created:** 2026-05-02\
**Updated:** 2026-08-17

------------------------------------------------------------------------

## 1. Abstract

Agentic AI systems introduce a fundamental shift in computing:

-   from output generation\
-   to execution of actions in real-world systems

Existing AI architectures focus on model correctness and pre-deployment
validation. These approaches are insufficient for systems that:

-   plan multi-step actions\
-   invoke external tools\
-   modify external state\
-   adapt during execution

This document defines **Execution-Time Governance (ETG)**:

> A system architecture where all AI-initiated actions are evaluated,
> constrained, and enforced at runtime before execution.

Execution-Time Governance introduces:

-   execution boundaries\
-   runtime policy enforcement\
-   dynamic authority resolution\
-   verifiable execution traces\
-   execution provenance graphs

------------------------------------------------------------------------

## 2. Motivation

Organizations deploying AI agents face:

-   uncontrolled automation\
-   unclear responsibility boundaries\
-   lack of traceability\
-   increasing regulatory exposure

These issues arise from a core gap:

> AI systems are allowed to act without a governing execution layer.

------------------------------------------------------------------------

## 3. Problem Statement

Current architecture:

``` mermaid
flowchart LR
    A[AI Decision] --> B[Direct Execution]
    B --> C[External Systems]
    C --> D[Real-World Effects]
```

This leads to:

-   non-enforceable constraints\
-   implicit execution logic\
-   inability to control runtime behavior\
-   lack of auditability

### Required Shift

``` mermaid
flowchart LR
    A[AI Decision] --> B[Governance Boundary]
    B --> C{Policy Decision}
    C -->|ALLOW| D[Execute Action]
    C -->|DENY| E[Block Action]
    C -->|ESCALATE| F[Human or Role-Based Approval]
    F --> G{Approval Decision}
    G -->|Approved| D
    G -->|Rejected| E
    D --> H[Execution Receipt]
    E --> H
```

------------------------------------------------------------------------

## 4. Design Goals

Execution-Time Governance must provide:

-   **Enforceability** --- actions cannot bypass runtime control\
-   **Observability** --- all actions are traceable\
-   **Determinability** --- governance decisions are explainable\
-   **Adaptability** --- policies react to runtime context\
-   **Composability** --- supports multi-step pipelines and agent
    workflows\
-   **Auditability** --- every action produces evidence

------------------------------------------------------------------------

## 5. Core Concepts

### 5.1 Execution Boundary

A mandatory control layer that intercepts all AI actions before
execution.

``` mermaid
flowchart TB
    A[Agent / Copilot] --> B[Proposed Action]
    B --> C[Execution Boundary]
    C --> D[Policy Evaluation]
    C --> E[Risk Evaluation]
    C --> F[Authority Resolution]
    D --> G[Execution Decision]
    E --> G
    F --> G
    G -->|Allow| H[Action Dispatcher]
    G -->|Deny| I[Blocked Action]
    G -->|Escalate| J[Human Authority]
```

### 5.2 Action-Centric Model

Governance applies to discrete execution actions, not only to prompts,
model outputs, or generated text.

### 5.3 Execution Context

Each action is evaluated using runtime context including:

-   user identity\
-   tenant or organizational scope\
-   resource identifiers\
-   data sensitivity\
-   policy constraints\
-   model confidence\
-   runtime risk signals\
-   prior execution state

------------------------------------------------------------------------

## 6. Specification

### 6.1 Action Model

All AI-generated actions SHOULD be normalized into a structured action
object.

``` json
{
  "action_id": "uuid",
  "action_type": "send_email",
  "actor": {
    "type": "agent",
    "id": "agent_123"
  },
  "requested_by": {
    "type": "user",
    "id": "user_456"
  },
  "target": {
    "resource_type": "email",
    "resource_id": "thread_789"
  },
  "payload": {},
  "context": {
    "tenant_id": "tenant_001",
    "risk_domain": "communications",
    "sensitivity": "external"
  }
}
```

### 6.2 Execution Pipeline

``` mermaid
sequenceDiagram
    participant Agent
    participant Boundary as Execution Boundary
    participant Policy as Policy Engine
    participant Risk as Risk Engine
    participant Authority as Authority Resolver
    participant Dispatcher as Action Dispatcher
    participant Receipt as Receipt Store

    Agent->>Boundary: Propose action
    Boundary->>Boundary: Normalize action
    Boundary->>Boundary: Enrich context
    Boundary->>Policy: Evaluate policies
    Boundary->>Risk: Compute runtime risk
    Boundary->>Authority: Resolve authority requirements
    Policy-->>Boundary: Policy result
    Risk-->>Boundary: Risk score / classification
    Authority-->>Boundary: Required authority
    Boundary->>Boundary: Decide ALLOW / DENY / ESCALATE

    alt ALLOW
        Boundary->>Dispatcher: Execute action
        Dispatcher-->>Boundary: Execution result
    else DENY
        Boundary-->>Agent: Blocked
    else ESCALATE
        Boundary-->>Agent: Requires approval
    end

    Boundary->>Receipt: Store execution receipt
```

### 6.3 Decision Outcomes

Each action MUST result in one of:

-   **ALLOW** --- action may execute\
-   **DENY** --- action is blocked\
-   **ESCALATE** --- action requires human or authority approval before
    execution

### 6.4 Oversight Modes

The system SHOULD support:

-   autonomous execution\
-   monitored execution\
-   approval-based execution\
-   blocked execution

``` mermaid
stateDiagram-v2
    [*] --> Proposed
    Proposed --> Allowed: low risk + policy pass
    Proposed --> Denied: policy fail
    Proposed --> Escalated: authority required
    Escalated --> Allowed: approval granted
    Escalated --> Denied: approval rejected
    Allowed --> Executed
    Denied --> Recorded
    Executed --> Recorded
    Recorded --> [*]
```

------------------------------------------------------------------------

## 7. Dynamic Authority Resolution

Static role checks are insufficient for agentic systems because the
required authority may depend on runtime context.

Authority SHOULD be resolved dynamically based on:

-   action type\
-   affected resource\
-   affected person\
-   regulatory domain\
-   operational risk\
-   confidence level\
-   reversibility of the action\
-   business or legal impact

Example:

``` mermaid
flowchart TD
    A[Proposed Action] --> B{Is action high impact?}
    B -->|No| C[Standard policy evaluation]
    B -->|Yes| D{Is confidence low or ambiguous?}
    D -->|No| E[Require domain owner approval]
    D -->|Yes| F[Require specialist approval]
    F --> G[Human Gate]
    E --> G
    C --> H[Proceed if allowed]
```

------------------------------------------------------------------------

## 8. Execution Receipts

Each governed action SHOULD produce an execution receipt.

### 8.1 Receipt Purpose

Execution receipts provide:

-   accountability\
-   auditability\
-   compliance evidence\
-   forensic reconstruction\
-   debugging support

### 8.2 Receipt Structure

``` json
{
  "receipt_id": "uuid",
  "action_id": "uuid",
  "decision": "ALLOW",
  "policies_applied": [
    "policy.execution.email.external.v1"
  ],
  "risk": {
    "score": 0.41,
    "classification": "medium"
  },
  "authority": {
    "required": false,
    "resolved_by": null
  },
  "execution": {
    "status": "success",
    "timestamp": "2026-05-02T00:00:00Z"
  }
}
```

------------------------------------------------------------------------

## 9. Execution Provenance Graph

Agentic systems often perform multi-step execution. Each action may
depend on prior actions, retrieved data, intermediate outputs, or
approval events.

A provenance graph SHOULD capture causal relationships between actions.

``` mermaid
flowchart TD
    U[User Request] --> P[Plan Generated]
    P --> A1[Action 1: Retrieve Data]
    A1 --> A2[Action 2: Analyze Data]
    A2 --> A3{Governance Gate}
    A3 -->|ALLOW| A4[Action 3: Update System]
    A3 -->|ESCALATE| H[Human Approval]
    H --> A4
    A4 --> R[Execution Receipt]
    A1 --> R1[Receipt 1]
    A2 --> R2[Receipt 2]
    H --> R3[Approval Receipt]
```

The graph enables:

-   tracing why an action occurred\
-   identifying downstream consequences\
-   detecting drift across repeated executions\
-   reconstructing incidents after failure

------------------------------------------------------------------------

## 10. System Architecture

``` mermaid
flowchart TB
    subgraph AgentLayer[Agent Layer]
        A1[Copilot / Agent]
        A2[Planner]
        A3[Tool Selector]
    end

    subgraph GovernanceLayer[Execution-Time Governance Layer]
        B1[Execution Boundary]
        B2[Policy Engine]
        B3[Risk Engine]
        B4[Authority Resolver]
        B5[Receipt Generator]
        B6[Provenance Graph Builder]
    end

    subgraph ExecutionLayer[Execution Layer]
        C1[Action Dispatcher]
        C2[Tool Adapter]
        C3[External API Connector]
    end

    subgraph ExternalSystems[External Systems]
        D1[CRM]
        D2[Email]
        D3[Database]
        D4[Cloud Infrastructure]
        D5[Document Store]
    end

    A1 --> A2
    A2 --> A3
    A3 --> B1
    B1 --> B2
    B1 --> B3
    B1 --> B4
    B2 --> B1
    B3 --> B1
    B4 --> B1
    B1 --> C1
    C1 --> C2
    C2 --> C3
    C3 --> D1
    C3 --> D2
    C3 --> D3
    C3 --> D4
    C3 --> D5
    B1 --> B5
    B5 --> B6
```

------------------------------------------------------------------------

## 11. Security Considerations

Security MUST NOT rely solely on:

-   prompts\
-   model instructions\
-   behavioral alignment\
-   natural-language constraints

Security MUST enforce:

-   API-level controls\
-   least privilege\
-   per-action authorization\
-   execution isolation\
-   credential scoping\
-   audit logging

AI agents must be treated as **non-human identities (NHI)**.

``` mermaid
flowchart LR
    A[Agent Identity] --> B[Scoped Credential]
    B --> C[Specific Action]
    C --> D{Allowed Scope?}
    D -->|Yes| E[Execute]
    D -->|No| F[Block]
    E --> G[Receipt]
    F --> G
```

------------------------------------------------------------------------

## 12. Runtime Behavioral Control

Agents may evolve during execution through:

-   memory updates\
-   tool-use patterns\
-   feedback loops\
-   adaptive planning\
-   repeated interaction with external systems

Systems SHOULD implement:

-   runtime state versioning\
-   policy-bound execution\
-   anomaly detection\
-   drift monitoring\
-   comparison of execution receipts across time

``` mermaid
flowchart TD
    A[Runtime State v1] --> B[Execution]
    B --> C[Receipt]
    C --> D[Observed Behavior]
    D --> E{Within Expected Envelope?}
    E -->|Yes| F[Continue]
    E -->|No| G[Flag Drift]
    G --> H[Escalate / Review / Reassess]
    H --> I[Runtime State v2]
```

------------------------------------------------------------------------

## 13. Transparency and Observability

Systems MUST provide:

-   full execution traceability\
-   decision visibility\
-   outcome linkage\
-   human approval history\
-   policy decision records

Observability must apply to:

-   allowed actions\
-   denied actions\
-   escalated actions\
-   failed actions\
-   partially completed execution chains

------------------------------------------------------------------------

## 14. Regulatory Alignment

Execution-Time Governance aligns with the direction of modern AI
regulation by making runtime action control explicit.

Relevant alignment includes:

-   **EU AI Act**
    -   risk management\
    -   human oversight\
    -   cybersecurity\
    -   logging and transparency
-   **GDPR**
    -   accountability\
    -   access control\
    -   data processing traceability
-   **Cyber Resilience Act**
    -   system-level security\
    -   secure execution behavior

``` mermaid
flowchart TB
    A[AI Agent Action] --> B[Execution-Time Governance]
    B --> C[Risk Management]
    B --> D[Human Oversight]
    B --> E[Cybersecurity]
    B --> F[Logging / Receipts]
    C --> G[Compliance Evidence]
    D --> G
    E --> G
    F --> G
```

------------------------------------------------------------------------

## 15. Anti-Patterns

### 15.1 Direct Execution Agents

``` mermaid
flowchart LR
    A[Agent] --> B[Tool]
    B --> C[External System]
    C --> D[Uncontrolled Effect]
```

### 15.2 Prompt-Based Governance

Prompt-based governance is insufficient because it is:

-   non-enforceable\
-   bypassable\
-   difficult to audit\
-   dependent on model behavior

### 15.3 Static Roles

Static role systems cannot fully adapt to runtime conditions such as:

-   contextual risk\
-   affected persons\
-   dynamic confidence levels\
-   regulatory triggers\
-   action irreversibility

------------------------------------------------------------------------

## 16. Implications

Execution-Time Governance shifts AI systems from:

-   generation systems

to:

-   controlled execution systems

For organizations, this means:

-   governance becomes runtime\
-   compliance becomes continuous\
-   execution becomes observable\
-   responsibility becomes traceable

------------------------------------------------------------------------

## 17. Claims Scope (Informal)

This document establishes prior art for:

-   execution-time governance architectures\
-   runtime enforcement of AI actions\
-   action-centric AI system design\
-   execution boundaries in AI systems\
-   dynamic authority resolution\
-   execution receipts\
-   execution provenance tracking\
-   non-human identity governance for AI agents\
-   runtime drift monitoring through execution evidence

------------------------------------------------------------------------

## 18. Alignment with Related RFCs

This RFC aligns with:

-   **TF-RFC-0001** → Execution Receipts\
-   **TF-RFC-0002** → Execution Provenance Graph\
-   **TF-RFC-0003** → XPO\
-   **TF-RFC-0004** → Execution Governance Model\
-   **TF-RFC-0005** → AI Adoption Guidelines

Together, these documents form a broader execution architecture for
AI-enabled systems.

------------------------------------------------------------------------

## Intellectual Property and Licensing

This RFC constitutes a public disclosure and forms part of the
CaralisLabs governed-execution research and RFC portfolio.

The concepts, models, terminology, and architectural approaches
described herein are subject to the intellectual-property and licensing
terms defined in the RFC portfolio's `LEGAL.md`.

Publication of this RFC establishes public evidence of authorship,
conceptual development, and prior art. No additional license, assignment
of intellectual property, patent rights, trademark rights, or commercial
implementation rights is granted by this RFC except as expressly stated
in `LEGAL.md` or in a separate written agreement.

Earlier revisions of this RFC may have been published under different
license terms. Rights validly granted under those earlier terms are not
purported to be revoked by this revision. See `LEGAL.md` for the
portfolio licensing history and current policy.

------------------------------------------------------------------------

## 19. Final Statement

AI systems must not only decide.

They must be governed at the moment of execution.

> Execution-time governance turns AI from an unconstrained actor into a
> controlled participant in a governed system.