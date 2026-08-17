# TF-RFC-0009: Trusted Processing Elements, Attestation, and Delegated Dispatch Governance

-   **Status**: Draft
-   **Author**: Nicolae Dumitru Caralicea / CaralisLabs
-   **Created**: 2026-05-28
-   **Updated**: 2026-08-17
-   **Related RFCs**: TF-RFC-0001, TF-RFC-0002, TF-RFC-0006

------------------------------------------------------------------------

## Abstract

This RFC introduces a trust framework for Processing Elements (PEs)
participating in the Pipeline Execution Runtime (PER).

The framework extends execution-time governance by enabling PER to
evaluate and verify the trustworthiness of execution participants before
dispatching work. The RFC defines trust models, attestation mechanisms,
delegated dispatch governance, and trust receipts.

The objective is to ensure that execution decisions are based not only
on authorization and policy evaluation but also on verifiable trust in
the processing participants and delegated execution paths.

------------------------------------------------------------------------

## Architecture Overview

PER evolves from a workflow orchestration system into a governed
execution runtime where trust becomes a first-class execution concern.

``` text
Execution Request
        ↓
Authorization Evaluation
        ↓
Trust Evaluation
        ↓
Governance Evaluation
        ↓
Dispatch
        ↓
Execution Receipt
        ↓
Provenance
```

------------------------------------------------------------------------

## 1. Problem Statement

Execution-time governance assumes that processing elements participating
in pipeline execution are trustworthy.

Current PER implementations establish trust through registration and
manifest discovery. While sufficient for trusted internal deployments,
this model introduces risks in multi-tenant, distributed, federated, and
third-party processing environments.

Examples include:

-   Processing Element impersonation
-   Manifest tampering
-   Unauthorized endpoint replacement
-   Compromised deployment environments
-   Delegated dispatch abuse
-   Supply-chain attacks
-   Forged execution responses

As PER evolves toward delegated dispatch and distributed execution
topologies, trust must become a first-class execution-time governance
concern.

------------------------------------------------------------------------

## 2. Core Principle

> Execution-time governance requires trust in execution participants.

PER SHALL evaluate trust before dispatching execution to a processing
element.

Trust evaluation SHALL become a first-class governance concern.

------------------------------------------------------------------------

## 3. Trust Models

### 3.1 Trust Level 0 -- Registration Trust

Trust established through:

-   registration
-   manifest retrieval
-   endpoint availability

Advantages:

-   simple onboarding
-   low operational overhead

Limitations:

-   no cryptographic identity
-   no integrity guarantees

------------------------------------------------------------------------

### 3.2 Trust Level 1 -- Certificate-Based Identity Trust

Processing Elements possess cryptographic identities.

Examples:

-   X.509 certificates
-   mTLS
-   internal PKI

PER validates:

-   certificate chain
-   issuer trust
-   expiration
-   revocation

Benefits:

-   strong endpoint identity
-   mature technology stack

------------------------------------------------------------------------

### 3.3 Trust Level 2 -- Manifest Trust

Processing Element manifests are digitally signed.

PER validates:

-   signer identity
-   manifest integrity

Benefits:

-   trusted registration process
-   tamper detection

------------------------------------------------------------------------

### 3.4 Trust Level 3 -- Execution Trust

Processing Elements sign execution responses.

Execution responses include:

-   execution identifier
-   response hash
-   timestamp
-   digital signature

Benefits:

-   non-repudiation
-   execution authenticity
-   response integrity

------------------------------------------------------------------------

### 3.5 Trust Level 4 -- Supply Chain Trust

Processing Elements provide deployment provenance.

Examples:

-   image signatures
-   SBOMs
-   Sigstore
-   Cosign
-   SLSA attestations

Benefits:

-   software provenance
-   deployment integrity

------------------------------------------------------------------------

### 3.6 Trust Level 5 -- Runtime Attestation

Processing Elements provide runtime evidence.

Examples:

-   TPM attestation
-   Confidential Computing
-   Intel SGX
-   AMD SEV

Benefits:

-   runtime integrity verification

------------------------------------------------------------------------

## 4. Delegated Dispatch Governance

Delegated dispatch extends PER's trust boundary.

PER SHALL NOT permit unrestricted delegated dispatch.

Instead, PER SHALL issue scoped delegation authority.

Example:

``` yaml
delegation:
  execution_id: exec_123
  delegated_to_pe: pe_a
  target_pe: pe_b
  operation: extract_text
  tenant_uuid: tenant_01
  expires_at: ...
```

Delegation authority SHALL be:

-   scoped
-   time-limited
-   auditable
-   revocable

------------------------------------------------------------------------

## 5. Trust Receipts

Trust evaluations SHALL be recorded.

Example:

``` json
{
  "trust_level": 3,
  "pe_uuid": "...",
  "certificate_valid": true,
  "manifest_valid": true,
  "execution_signature_valid": true,
  "timestamp": "..."
}
```

Trust receipts become part of:

-   execution provenance
-   execution receipts
-   audit trails

------------------------------------------------------------------------

## 6. Trust Evaluation Flow

``` text
Execution Request
        ↓
Authorization Evaluation
        ↓
Trust Evaluation
        ↓
Governance Evaluation
        ↓
Dispatch
        ↓
Execution Receipt
```

------------------------------------------------------------------------

## 7. Security Model

Execution trust SHALL support:

-   endpoint identity verification
-   manifest integrity validation
-   execution authenticity
-   delegated dispatch controls
-   supply-chain verification
-   runtime attestation

------------------------------------------------------------------------

## 8. Adversarial Considerations

The framework SHALL mitigate:

-   endpoint impersonation
-   supply-chain attacks
-   delegated dispatch abuse
-   manifest tampering
-   execution forgery
-   unauthorized participant substitution

------------------------------------------------------------------------

## 9. Comparison

  Capability                      Traditional Workflow Engines   PER Trust Model
  ------------------------------- ------------------------------ -----------------
  Endpoint Identity               Optional                       First-Class
  Manifest Validation             Limited                        Supported
  Execution Signatures            Rare                           Supported
  Delegated Dispatch Governance   Limited                        Native
  Supply Chain Trust              External                       Integrated
  Runtime Attestation             Rare                           Supported

------------------------------------------------------------------------

## 10. Example Use Case

A document processing pipeline:

``` text
PDF Ingestion
      ↓
OCR Processing PE
      ↓
Text Extraction PE
      ↓
Classification PE
```

Before each dispatch, PER verifies:

-   trust level requirements
-   delegated dispatch permissions
-   participant identity
-   execution authority

------------------------------------------------------------------------

## 11. Execution Guarantees

A compliant implementation SHOULD guarantee:

1.  Trusted execution participants
2.  Verifiable execution responses
3.  Controlled delegation
4.  Auditable trust decisions
5.  Traceable trust evolution

------------------------------------------------------------------------

## 12. Conclusion

Execution governance is incomplete without participant trust.

This RFC extends PER beyond execution authorization into execution
trust, enabling governed runtime environments where processing elements
can be verified, attested, and audited.

------------------------------------------------------------------------

## Key Statement

> Governed execution requires governed trust in execution participants.

------------------------------------------------------------------------

## 13. Claims Scope (Informal)

This document establishes prior art for:

-   Processing Element trust evaluation
-   Trust-level-based execution governance
-   Delegated dispatch trust controls
-   Execution trust receipts
-   Supply-chain-aware execution runtimes
-   Runtime participant attestation
-   Trust-aware execution control planes

------------------------------------------------------------------------

## 14. Relationship to Other RFCs

Depends on:

-   TF-RFC-0001 Execution Receipts
-   TF-RFC-0002 Execution Provenance Graph
-   TF-RFC-0006 Execution-Time Governance

Provides foundation for:

-   TF-RFC-0010 Execution Artifact Authority and Context-Bound Access

------------------------------------------------------------------------

## Intellectual Property and Licensing

This RFC constitutes a public disclosure and forms part of the
CaralisLabs governed-execution research and RFC portfolio.

The concepts, models, terminology, trust frameworks, attestation
mechanisms, and architectural approaches described herein are subject to
the intellectual-property and licensing terms defined in the RFC
portfolio's `LEGAL.md`.

Publication of this RFC establishes public evidence of authorship,
conceptual development, defensive disclosure, and prior art. No
additional license, assignment of intellectual property, patent rights,
trademark rights, or commercial implementation rights is granted by this
RFC except as expressly stated in `LEGAL.md` or in a separate written
agreement.

Earlier revisions of this RFC may have been published under different
license terms. Rights validly granted under those earlier terms are not
purported to be revoked by this revision. See `LEGAL.md` for the
portfolio licensing history and current policy.

------------------------------------------------------------------------

## 17. Final Note

Trust is not eliminated.

Trust is evaluated, governed, evidenced, and made observable.

PER does not attempt to remove trust from execution.

PER provides mechanisms to make trust explicit, verifiable, auditable,
and enforceable at execution time.