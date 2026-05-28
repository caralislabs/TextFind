# TF-RFC-0010: Execution Artifact Authority and Context-Bound Access

* **Status**: Draft
* **Author**: Nicolae Dumitru Caralicea / CaralisLabs
* **Created**: 2026-05-28
* **Updated**: 2026-05-28
* **Related RFCs**: TF-RFC-0001, TF-RFC-0002, TF-RFC-0006, TF-RFC-0009

---

## Abstract

This RFC introduces the Execution Artifact Authority (EAA), a governed runtime service responsible for storing, retrieving, and enforcing access controls on execution artifacts generated during Pipeline Execution Runtime (PER) operations.

The EAA establishes a separation between execution authority and artifact enforcement. PER remains the sole authority responsible for evaluating execution-time governance decisions, while the EAA enforces scoped, signed, time-bound capabilities issued by PER.

This RFC defines context-bound artifact access, execution-scoped artifact governance, delegated artifact retrieval, and artifact access receipts.

---

## Architecture Overview

```text
PER
 ↓ evaluates authorization
 ↓ evaluates governance
 ↓ issues capability
Execution Artifact Authority
 ↓ validates capability
 ↓ returns artifact
Processing Element
```

---

## 1. Problem Statement

As PER evolves toward:

* delegated dispatch
* large document processing
* execution branching
* pipeline resumption
* rollback workflows
* execution working sets

execution artifacts become first-class runtime resources.

Examples include:

* OCR results
* PDF page extractions
* embeddings
* intermediate model outputs
* generated reports
* execution snapshots
* context assembly artifacts

Traditional cache systems are insufficient because they lack execution-aware governance.

---

## 2. Core Principle

> Runtime services enforce authority; PER issues authority.

The Execution Artifact Authority SHALL NOT make independent execution authorization decisions.

Execution authority SHALL originate from PER.

---

## 3. Architectural Motivation

Without a governed artifact authority:

```text
PE
 ↓
Redis/S3/GridFS
 ↓
Artifact
```

each runtime component becomes responsible for authorization decisions.

This creates:

* duplicated authorization logic
* inconsistent enforcement
* trust boundary violations
* delegated dispatch risks

---

## 4. Execution Artifact Authority

The EAA is a dedicated runtime service responsible for:

* artifact storage
* artifact retrieval
* capability enforcement
* artifact lifecycle management
* artifact auditability

The EAA is NOT responsible for:

* execution authorization
* policy evaluation
* governance decisions

These responsibilities remain with PER.

---

## 5. Artifact Model

Example:

```yaml
artifact:
  artifact_id: artifact_001
  tenant_uuid: tenant_01
  execution_id: exec_123
  producer_step_uuid: step_2
  content_type: application/pdf
  created_at: ...
  expires_at: ...
```

Artifacts are execution resources.

Artifacts SHALL be execution-scoped.

---

## 6. Capability-Based Access

PER issues capabilities.

Example:

```yaml
artifact_capability:
  capability_uuid: cap_001
  artifact_id: artifact_001
  tenant_uuid: tenant_01
  execution_id: exec_123
  grantee_pe_uuid: pe_text_extractor
  purpose: successor_input_assembly
  expires_at: ...
```

Capabilities SHALL be:

* scoped
* time-bound
* auditable
* revocable

---

## 7. Context-Bound Access

Artifact access SHALL be bound to execution context.

The EAA validates:

* artifact identifier
* tenant identifier
* execution identifier
* requesting PE identity
* capability validity
* expiration

Access SHALL be denied if context validation fails.

---

## 8. Delegated Dispatch Support

Delegated dispatch introduces additional artifact access requirements.

Example:

```text
PE-A
 ↓
Build Successor Context
 ↓
Fetch Artifact
 ↓
Invoke PE-B
```

PER MAY issue delegated artifact capabilities allowing PE-A to assemble successor inputs.

Delegated capabilities SHALL remain:

* execution-bound
* purpose-bound
* time-bound

---

## 9. Artifact Access Receipts

Artifact access events SHALL be recorded.

Example:

```json
{
  "artifact_id": "artifact_001",
  "execution_id": "exec_123",
  "pe_uuid": "pe_text_extractor",
  "capability_valid": true,
  "timestamp": "..."
}
```

Receipts become part of:

* execution provenance
* audit trails
* governance evidence

---

## 10. Execution Working Set

Artifacts collectively form an execution working set.

The execution working set represents all governed runtime artifacts associated with an execution.

Examples:

* cached outputs
* intermediate transformations
* execution snapshots
* successor input artifacts

---

## 11. Execution Flow

```text
Execution Request
        ↓
PER Governance Evaluation
        ↓
Capability Issuance
        ↓
Artifact Access Request
        ↓
EAA Capability Validation
        ↓
Artifact Retrieval
        ↓
Access Receipt
```

---

## 12. Security Considerations

This RFC addresses:

* unauthorized artifact access
* tenant boundary violations
* delegated dispatch abuse
* context assembly attacks
* cache poisoning risks

---

## 13. Claims Scope (Informal)

This document establishes prior art for:

* Execution Artifact Authorities
* Context-bound artifact access
* Execution-scoped artifact governance
* Capability-based artifact retrieval
* Delegated artifact access controls
* Execution working sets
* Artifact access receipts

---

## 14. Relationship to Other RFCs

Depends on:

* TF-RFC-0001 Execution Receipts
* TF-RFC-0002 Execution Provenance Graph
* TF-RFC-0006 Execution-Time Governance
* TF-RFC-0009 Trusted Processing Elements

Extends:

* Delegated Dispatch Governance
* Runtime Trust Models

---

## IP & Licensing Considerations

This document is a public disclosure intended to:

- establish prior art for the concepts described herein
- document authorship and evolution of the proposed models
- enable open discussion and architectural exploration

### Pre-Existing Intellectual Property

All intellectual property described in this document constitutes pre-existing work of the author.

### Scope of Use

This document permits discussion, implementation, adaptation, and extension of the concepts described herein.

### Implementation Distinction

A distinction is made between conceptual models and implementation-specific systems.

### No Implicit Assignment

No rights are assigned implicitly through access, discussion, or implementation of the concepts described herein.

---

## License

This document is released under the Creative Commons Attribution 4.0 International (CC BY 4.0) license.

---

## 17. Final Note

Execution artifacts are not cache entries.

Execution artifacts are governed execution resources.

The Execution Artifact Authority ensures that artifacts remain bound to execution context, governed by PER-issued authority, and auditable throughout their lifecycle.
