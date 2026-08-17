# TF-RFC-0015

# From Authority to Operate to Authority to Execute

## Operational Assurance and Autonomous Execution Assurance in Autonomous AI Systems

**Status:** Draft\
**Author:** Nicolae Dumitru Caralicea / CaralisLabs **Version:** 0.1\
**Updated:** 2026-08-17

------------------------------------------------------------------------

## Abstract

Artificial intelligence is undergoing a fundamental transition.

For decades, software systems primarily responded to explicit human
instructions. Today, AI systems increasingly perform autonomous work by
invoking APIs, executing code, orchestrating workflows, interacting with
enterprise systems, and making operational decisions with limited human
intervention.

Current security and compliance frameworks provide mechanisms for
establishing confidence that an environment is suitable for hosting
sensitive workloads. Authorities to Operate (ATO), FedRAMP, ISO 27001,
SOC 2, and related frameworks evaluate whether the operational
environment satisfies the required security and operational controls.

These frameworks answer an essential question:

> **Can this environment be trusted to operate?**

As AI systems become increasingly autonomous, a complementary question
emerges:

> **Can every autonomous action performed within that environment be
> trusted?**

This document introduces the distinction between **Operational
Assurance** and **Autonomous Execution Assurance**, arguing that future
AI systems will require both.

Operational Assurance establishes trust in the environment.

Autonomous Execution Assurance establishes trust in autonomous
execution.

Rather than replacing existing security frameworks, Autonomous Execution
Assurance extends them by introducing deterministic runtime mechanisms
capable of authorizing, validating, tracing, and producing evidence for
autonomous actions.

------------------------------------------------------------------------

# 1. Introduction

Historically, software primarily executed explicit human instructions.
Autonomous AI introduces systems capable of selecting and performing
actions with increasing independence. As the locus of decision-making
shifts toward the runtime, the mechanisms used to establish trust must
evolve accordingly.

------------------------------------------------------------------------

# 2. Operational Assurance

Operational Assurance provides confidence that an environment satisfies
the security, compliance, and operational controls necessary to process
sensitive workloads.

Typical control areas include:

-   Identity and Access Management
-   Encryption of data at rest and in transit
-   Network segmentation
-   Secure key management
-   Logging and monitoring
-   Vulnerability management
-   Patch management
-   Configuration management
-   Incident response
-   Backup and recovery
-   Continuous security monitoring

Collectively these controls establish confidence that an environment is
suitable for operating sensitive systems.

They establish trust **before execution begins**.

------------------------------------------------------------------------

# 3. The Emergence of Autonomous Execution

Modern AI systems increasingly:

-   invoke APIs
-   execute software
-   orchestrate workflows
-   interact with enterprise systems
-   control external tools
-   collaborate with other AI systems

As autonomy increases, organizations must establish confidence not only
in the environment, but also in every autonomous action.

------------------------------------------------------------------------

# 4. The Missing Layer

Execution introduces questions that infrastructure assurance alone does
not answer:

-   Who initiated this action?
-   Which policy authorized it?
-   Was the input valid?
-   Was the output validated?
-   Which model and tools participated?
-   Which artifacts were produced?
-   Can the execution be reconstructed?
-   Can the decision be independently audited?

These are execution-level questions.

------------------------------------------------------------------------

# 5. Autonomous Execution Assurance

Autonomous Execution Assurance establishes confidence that autonomous
actions satisfy organizational requirements while the system is
operating.

Potential runtime mechanisms include:

-   execution authorization
-   policy evaluation
-   execution context propagation
-   schema validation
-   execution provenance
-   execution receipts
-   runtime data classification
-   artifact governance
-   deterministic replay
-   policy-aware routing
-   runtime enforcement

Unlike Operational Assurance, which is assessed periodically, Execution
Assurance is evaluated continuously.

------------------------------------------------------------------------

# 6. Operational Assurance vs. Autonomous Execution Assurance

  Operational Assurance         Autonomous Execution Assurance
  ----------------------------- --------------------------------------
  Environment-oriented          Execution-oriented
  Infrastructure controls       Runtime controls
  Evaluated before deployment   Evaluated for every execution
  Periodic assessment           Continuous assessment
  Trusts the environment        Trusts individual autonomous actions

------------------------------------------------------------------------

# 7. Relationship to Existing Frameworks

Autonomous Execution Assurance does not replace existing frameworks such
as NIST RMF, FedRAMP, ISO 27001, or SOC 2.

Instead, it complements them by extending trust from the operational
environment into runtime autonomous execution.

------------------------------------------------------------------------

# 8. Toward Authority to Execute

Authorities to Operate establish confidence that an environment
satisfies required operational controls.

Autonomous systems introduce the possibility of a complementary concept:

**Authority to Execute.**

Rather than certifying the environment alone, future systems may
increasingly require evidence that every autonomous action:

-   was authorized
-   complied with policy
-   satisfied validation requirements
-   is attributable
-   is traceable
-   can be independently verified

This document introduces the architectural distinction but does not
define a certification process.

------------------------------------------------------------------------

# 9. Looking Forward

Future trustworthy AI systems may require two complementary layers:

``` text
Operational Assurance
        ↓
Trusted Environment
        ↓
Autonomous Execution
        ↓
Autonomous Execution Assurance
        ↓
Trusted Autonomous Actions
```

------------------------------------------------------------------------

# Research Roadmap

This document establishes the conceptual distinction between
**Operational Assurance** and **Autonomous Execution Assurance**.

It intentionally does not prescribe a specific implementation,
certification model, or runtime architecture.

Future work will progressively explore these topics in greater detail,
including but not limited to:

## Runtime Assurance Mechanisms

Possible runtime mechanisms that contribute to Autonomous Execution
Assurance, including:

-   execution authorization
-   execution policy evaluation
-   execution context propagation
-   execution provenance
-   execution receipts
-   runtime data classification
-   policy-aware routing
-   artifact governance
-   deterministic replay
-   execution audit trails

## Mapping to Existing Security Frameworks

Analysis of how Autonomous Execution Assurance complements existing
standards and control frameworks, including:

-   NIST Risk Management Framework (RMF)
-   NIST SP 800-53
-   FedRAMP
-   ISO 27001
-   SOC 2
-   EU AI Act
-   other AI governance frameworks

## Evidence Models

Investigation of the evidence required to establish confidence in
autonomous execution, including:

-   execution receipts
-   provenance graphs
-   execution artifacts
-   policy evaluation records
-   validation evidence
-   runtime audit trails

## Authority to Execute

Exploration of whether future autonomous systems may require a
complementary concept to Authority to Operate (ATO):

**Authority to Execute (ATX)**

including possible assessment models, certification approaches, and
operational implications.

## Runtime Governance

Research into deterministic runtime mechanisms capable of enforcing
organizational policies before, during, and after autonomous execution.

## Architectural Patterns

Comparative analysis of possible implementation approaches, including:

-   execution runtimes
-   policy enforcement layers
-   governance kernels
-   trusted execution components
-   distributed execution architectures

## Data Classification

Runtime handling of sensitive information through policy-aware
mechanisms such as:

-   automatic redaction
-   tokenization
-   anonymization
-   selective disclosure
-   policy-driven routing

## Trustworthy Autonomous Systems

Investigation of architectural models capable of establishing confidence
in autonomous systems operating continuously within enterprise and
governmental environments.

------------------------------------------------------------------------

The concepts introduced in this document are intentionally
technology-independent.

Their purpose is to establish a conceptual foundation for future
research into trustworthy autonomous execution rather than to prescribe
a particular implementation or product.

------------------------------------------------------------------------

# Intellectual Property, Prior Art, and Licensing

## Purpose of Disclosure

This RFC constitutes a public disclosure and forms part of the
CaralisLabs governed-execution research and RFC portfolio.

Publication establishes public evidence of authorship, conceptual
development, defensive disclosure, and prior art for the concepts,
terminology, architectural distinctions, assurance models, and
governance approaches described herein.

This publication is intended to support research, discussion, and
examination of trustworthy autonomous execution while preserving the
intellectual-property position defined in the RFC portfolio's
`LEGAL.md`.

------------------------------------------------------------------------

## Scope of the Contribution

This RFC introduces and develops the distinction between two
complementary layers of trust for autonomous AI systems:

-   **Operational Assurance** --- confidence that an environment
    satisfies the security, compliance, and operational controls
    required to host sensitive workloads.
-   **Autonomous Execution Assurance** --- confidence that autonomous
    actions performed within that environment are authorized, governed,
    validated, attributable, traceable, auditable, and capable of
    producing execution evidence at runtime.

It further introduces **Authority to Execute (ATX)** as a complementary
concept to Authority to Operate (ATO), while intentionally leaving
future assessment models, certification approaches, and implementation
mechanisms open for further research.

These concepts form part of the broader CaralisLabs research into
execution-time governance, runtime assurance, execution provenance,
execution receipts, policy-driven autonomous systems, distributed
execution architectures, and trustworthy AI infrastructure.

------------------------------------------------------------------------

## Intellectual Property and Licensing

The concepts, terminology, assurance models, architectural distinctions,
Authority to Execute (ATX), Autonomous Execution Assurance, runtime
governance models, evidence models, and related architectural approaches
described herein are subject to the intellectual-property and licensing
terms defined in the RFC portfolio's `LEGAL.md`.

These concepts constitute pre-existing intellectual work of the author
and are published to establish authorship, public disclosure, conceptual
lineage, defensive disclosure, and prior art.

Publication of this RFC does not transfer ownership of the disclosed
work and does not grant any additional license, assignment of
intellectual property, patent rights, trademark rights, or commercial
implementation rights except as expressly stated in `LEGAL.md` or in a
separate written agreement.

------------------------------------------------------------------------

## Conceptual Framework vs. Implementation

This RFC intentionally establishes a technology-independent conceptual
foundation rather than prescribing a particular implementation,
certification process, product, or runtime architecture.

Future implementations may include execution runtimes,
policy-enforcement layers, governance kernels, trusted execution
components, evidence systems, certification systems, distributed
execution architectures, or commercial products. Such implementations
may be separately licensed, proprietary, open source, governmental,
academic, commercial, or otherwise independently governed.

Publication of the conceptual framework should not be interpreted as
disclosure or licensing of proprietary runtime internals, operational
methods, implementation-specific algorithms, deployment strategies, or
other undisclosed CaralisLabs know-how.

------------------------------------------------------------------------

## No Implicit Assignment

Access to this RFC, discussion of its contents, citation, permitted use,
or participation in future collaborative work does not constitute
transfer or assignment of intellectual-property rights.

Any assignment, commercial license, implementation license, or broader
grant of rights must be explicit, documented, and authorized by the
applicable rights holder.

------------------------------------------------------------------------

## Licensing History

Earlier revisions of this RFC may have been published under the
**Creative Commons Attribution 4.0 International (CC BY 4.0)** license.

This revision does not purport to revoke rights validly granted under
earlier license terms for copies or revisions distributed under those
terms.

For this revision and future revisions, the terms stated in the RFC
portfolio's `LEGAL.md`, together with any explicit notice contained in
the applicable revision, govern publication.