# TF-RFC-0023

## Independent Submission, Evidence, and Delegated Representation (ISEDR)

### A Conceptual Framework for Durable Claims, Reciprocal Evidence, and Authorized Representation

**Status:** Draft — REV0.1

**Author:** Nicolae Dumitru Caralicea

**Organization:** CaralisLabs

**Created:** 2026-09-29  
**Updated:** 2026-09-29

**Related Work:** TF-THESIS-0001 (Execution Economy), TF-RFC-0019 (Federated Execution Operator Ecosystems), TF-RFC-0020 (Domain Capabilities and Portable Governed Execution), TF-RFC-0022 (Computational Organizational Dynamics), PER execution receipts, CaralisLabs identity and authorization architecture, Deployment Units, delegated-operator architecture

------------------------------------------------------------------------

## Abstract

This RFC proposes **Independent Submission, Evidence, and Delegated Representation (ISEDR)**, a conceptual framework for enabling individuals to create durable evidence of consequential communications or claims directed toward institutions, even when the institution does not provide an adequate authenticated submission, acknowledgement, or tracking channel.

The framework separates several concerns that are frequently collapsed in existing institutional workflows:

- custody of information
- visibility of information
- evidence of submission
- evidence of notification or delivery
- authority to access information
- authority to represent a person
- institutional acknowledgement
- aggregate pattern discovery

A user may create a sealed or encrypted submission, receive a durable receipt, identify the institution to whose attention the submission is directed, and optionally provide non-confidential structured metadata describing the category and nature of the matter.

The user may later delegate scoped authority to a lawyer, advocate, professional, or other representative to access some or all of the protected material and act on the user's behalf.

The framework further considers how independent submissions may eventually interact with registered institutional channels, producing reciprocal evidence for individuals and institutions while enabling privacy-preserving identification of recurring interaction failures.

ISEDR may be realized as a vertical platform operating on one or more **Deployment Units**. Deployment Units may provide technical, operational, trust, governance, data-sovereignty, and jurisdictional boundaries within which the platform, capabilities, institutional channels, representatives, and policies are resolved for a particular environment. The same conceptual platform may therefore be deployed across jurisdictions without requiring identical execution in every jurisdiction.

The central principle is:

> No consequential interaction should depend exclusively on one party's ability or willingness to remember that it occurred.

------------------------------------------------------------------------

## 1. Motivation

Many consequential interactions between individuals and institutions begin with a simple need:

> I need this institution to officially receive something from me and I need evidence that I submitted it.

Examples include:

- requesting medical records or diagnostic images
- submitting medical documents
- disputing a financial transaction
- questioning an interest rate or contractual term
- submitting a complaint
- requesting correction of information
- providing evidence relevant to an existing case
- communicating a time-sensitive concern
- requesting escalation or review

Institutions increasingly provide conversational interfaces, telephone support, generic email addresses, web forms, or other customer-service mechanisms. These mechanisms may be useful for answering questions while providing weak support for consequential submissions.

A user may be unable to establish:

- exactly what was submitted
- when it was submitted
- to whom it was directed
- whether it was received
- whether a case was created
- whether responsibility was assigned
- what happened afterward

The institution may retain internal records while the individual possesses little or no corresponding evidence.

This creates an evidentiary asymmetry.

ISEDR explores an independent layer through which an individual can establish durable evidence without requiring the independent layer to possess unrestricted visibility into the confidential contents of the submission.

------------------------------------------------------------------------

## 2. Core Principles

### 2.1 No Consequential Request Without a Receipt

When an identified party initiates a consequential action, durable evidence should be produced that the action entered a defined submission or execution boundary.

### 2.2 Reciprocal Evidence

> No consequential interaction without reciprocal evidence.

Where practical, each participant should possess evidence appropriate to its role in the interaction.

The institution should not be the exclusive custodian of evidence concerning an interaction involving another party.

### 2.3 Evidence Is Not Adjudication

Evidence that a submission existed or was transmitted does not establish that the assertions contained within it are true.

ISEDR distinguishes:

- proof of existence
- proof of submission
- proof of notification
- proof of delivery or acknowledgement
- proof of content integrity
- validity of the underlying claim

The last of these generally requires separate evaluation or adjudication.

### 2.4 Privacy by Separation

The infrastructure that establishes evidence need not automatically possess authority to read the protected content.

Custody, visibility, authorization, representation, and evidence should be independently expressible properties.

### 2.5 User-Controlled Delegation

Authority to disclose protected content or act on behalf of a user originates with the user or another legally authorized party, subject to applicable law.

Delegation should be explicit, scoped, observable, and revocable for future actions where legally and operationally possible.

------------------------------------------------------------------------

## 3. Definitions

### 3.1 Claim

A **Claim** is a user-created package representing a consequential communication, request, complaint, dispute, notice, or other matter intended for the attention of an institution or another identified party.

The term does not imply that the assertions within the claim have been verified.

### 3.2 Sealed Submission

A **Sealed Submission** is protected content whose integrity can be established while its contents remain inaccessible to parties that have not been granted appropriate access.

Encryption is one possible mechanism. This RFC does not prescribe a specific cryptographic implementation.

### 3.3 Claim Metadata

**Claim Metadata** is structured information that may be processed separately from protected claim content.

Examples may include:

- intended institution
- claim category
- general nature of the issue
- original interaction date
- whether acknowledgement was received
- elapsed waiting time
- requested type of response

Metadata should be minimized and designed to avoid unnecessary disclosure.

### 3.4 Receipt

A **Receipt** is durable evidence associated with an event in the lifecycle of a claim.

A receipt may identify, where appropriate:

- claim or execution identifier
- event type
- timestamp
- actor or authority
- intended recipient
- integrity reference or content hash
- relevant status

A receipt does not inherently constitute legal proof of service or legally recognized delivery.

### 3.5 Representative

A **Representative** is a party to whom a user has delegated defined authority concerning a claim.

Representatives may include, depending on context and applicable law:

- lawyers
- patient advocates
- consumer advocates
- accountants
- authorized professionals
- nonprofit organizations
- other qualified or authorized parties

### 3.6 Delegation

A **Delegation** is an explicit grant of authority from an authorized party to another party for a defined scope, purpose, duration, or set of actions.

### 3.7 Institutional Channel

An **Institutional Channel** is a mechanism through which an institution can receive, acknowledge, respond to, or otherwise participate in claims or related events.

------------------------------------------------------------------------

## 4. Conceptual Claim Lifecycle

A minimal lifecycle may be represented as:

**CREATED → SEALED → RECEIPT_ISSUED → INSTITUTION_DESIGNATED → NOTIFICATION_ATTEMPTED**

Where an institution participates in the protocol, additional states may include:

**DELIVERED → ACKNOWLEDGED → ASSIGNED → RESPONDED → RESOLVED**

Where representation is involved:

**DELEGATION_GRANTED → REPRESENTATIVE_ACCESSED → REPRESENTATIVE_ACTED → DELEGATION_REVOKED/EXPIRED**

Not every claim requires every state.

The lifecycle is intended to make consequential transitions observable rather than to prescribe one universal institutional workflow.

------------------------------------------------------------------------

## 5. Independent Evidence Layer

The initial system does not require institutional participation in order to provide some value.

An individual could:

1. create a claim
2. protect the confidential content
3. identify the intended institution
4. optionally provide limited structured metadata
5. receive a durable receipt
6. request that the institution be notified that a submission exists

The independent layer can then establish evidence concerning actions it actually performed.

For example, it may be able to establish that:

- a particular protected payload existed at a particular time
- its integrity reference has not changed
- the user designated a particular institution
- a notification was attempted through a particular channel
- a particular representative was granted access at a particular time

The layer must not represent evidence of submission as evidence of institutional receipt when institutional receipt has not been established.

------------------------------------------------------------------------

## 6. Institutional Participation

The framework becomes stronger when institutions voluntarily participate.

An institution could register one or more authenticated channels for receiving claims or notifications.

Conceptually, an institution may provide:

- an authenticated endpoint
- a secure inbox
- a public encryption key
- routing metadata
- acknowledgement capabilities
- status capabilities

A participating institution could then issue its own acknowledgement.

This creates reciprocal evidence:

**User receipt → transmission evidence → institutional acknowledgement → subsequent status evidence**

Institutional participation may also reduce operational burden by replacing unstructured calls, emails, and repeated explanations with standardized intake and traceable interactions.

------------------------------------------------------------------------

## 7. Delegated Representation

Delegated representation is a central extension of the framework.

A user may choose to authorize another party to access protected information and/or act concerning a claim.

A conceptual delegation may contain:

**Principal:** User U  
**Representative:** R  
**Claim:** C  
**Permissions:** defined actions  
**Purpose:** defined purpose  
**Institution:** optional recipient scope  
**Validity:** defined period  
**Revocation:** applicable conditions

Possible permissions may include:

- view protected content
- download evidence
- communicate with an institution
- submit additional material
- receive responses
- request escalation

The framework should avoid treating delegation as unrestricted account sharing.

Delegation is authority over defined actions and resources.

------------------------------------------------------------------------

## 8. Professional and Legal Representation

Lawyers and other qualified professionals may participate as representatives where appropriate.

Their role is distinct from the infrastructure provider.

The infrastructure may provide:

- identity
- authorization
- delegation
- secure exchange
- execution
- receipts
- evidence history

A lawyer or other professional may provide:

- professional judgment
- advice
- representation
- communication with institutions
- escalation
- legal action where appropriate

The infrastructure provider should not implicitly become a law firm, adjudicator, regulator, or representative merely by operating the system.

------------------------------------------------------------------------

## 9. Privacy-Preserving Pattern Discovery

Users may optionally provide structured, non-confidential metadata describing their claims.

This metadata can enable identification of aggregate patterns without requiring general access to protected claim contents.

For example, the system might observe a pattern such as:

- institution: X
- category: medical-record request
- number of user-classified submissions: N
- number reporting no acknowledgement: M
- observed or user-reported waiting-time distribution

Such aggregation must be described precisely.

The existence of multiple claims does not establish that the allegations within those claims are true.

Public reporting should distinguish among:

- user-submitted classifications
- system-observed events
- institution-confirmed events
- independently verified facts

------------------------------------------------------------------------

## 10. Collective Visibility

Where multiple users independently identify similar interaction failures, the framework may allow authorized representatives or participating organizations to identify a recurring operational pattern.

This may enable communication such as:

> Multiple users have independently submitted matters categorized under the same institutional process and report difficulty obtaining acknowledgement.

The purpose is not to create an unmoderated public accusation system.

The purpose is to make recurring interaction failures observable while preserving the distinction between reported claims and established facts.

Institutions should have mechanisms to participate, respond, correct factual metadata where appropriate, and establish better channels.

------------------------------------------------------------------------

## 11. Trust Boundaries

ISEDR introduces multiple trust relationships that must remain explicit.

Potential participants include:

- users
- representatives
- institutions
- infrastructure operators
- capability providers
- auditors
- regulators or courts where legally applicable

The framework should avoid assuming that any single participant is universally trusted.

Important separations include:

**Custody ≠ Visibility**  
**Visibility ≠ Authority**  
**Authority ≠ Representation**  
**Submission ≠ Delivery**  
**Delivery ≠ Acceptance**  
**Receipt ≠ Validation of Claim**

These distinctions are fundamental to the model.

------------------------------------------------------------------------

## 12. Security and Abuse Considerations

A production implementation would require substantial work beyond this conceptual RFC.

Areas requiring explicit treatment include:

- identity assurance
- impersonation
- fraudulent claims
- spam and denial-of-service behavior
- malicious file uploads
- encryption and key management
- key loss and recovery
- metadata leakage
- unauthorized delegation
- representative verification
- delegation revocation
- data retention
- deletion requirements
- subpoenas and lawful access demands
- cross-jurisdictional operation
- defamation risk
- harassment and abusive submissions
- institutional authentication
- evidentiary integrity
- compromised endpoints

This RFC does not define solutions to these issues.

------------------------------------------------------------------------

## 13. Legal and Regulatory Considerations

The framework does not assume that an independent submission constitutes legally recognized notice, service, delivery, consent, complaint filing, or regulatory submission.

Those effects depend on jurisdiction, applicable law, contractual arrangements, institutional participation, and the nature of the interaction.

Implementations must distinguish technical evidence from legal conclusions.

Likewise, the ability to delegate access technically does not establish that a representative is legally authorized to perform every possible action.

Legal and regulatory analysis is therefore an implementation requirement rather than an assumption of the framework.

------------------------------------------------------------------------

## 14. Deployment Units and Jurisdictional Execution

ISEDR does not require a single globally centralized platform.

A platform implementing this framework may operate within one or more **Deployment Units**, where each Deployment Unit provides a defined technical, operational, trust, governance, and potentially jurisdictional boundary.

This is particularly relevant to submission, representation, and institutional interaction because requirements concerning identity, privacy, consent, delegation, professional representation, evidence, retention, institutional communication, data handling, and recognized channels may vary between jurisdictions.

For example, a Deployment Unit operating in Canada may host an ISEDR platform configured for Canadian institutions, representatives, policies, languages, and applicable regulatory environments. Deployment Units operating in European jurisdictions may host compatible instances configured for their respective national and European legal, institutional, linguistic, and operational environments.

The underlying platform and Domain Capabilities may remain conceptually portable while their policies, bindings, implementations, institutional registries, representative registries, and execution constraints vary according to the environment in which execution occurs.

A foundational principle is therefore:

> **Portable governed execution does not require identical execution everywhere.**

Portability requires preservation of the relevant authority, governance, provenance, accountability, and evidence properties while execution is resolved according to the applicable environment.

### 14.1 Jurisdiction as Execution Context

Jurisdiction-specific requirements should not need to be embedded indiscriminately into the common platform core.

They may instead be expressed through jurisdiction-specific combinations of:

- policies
- capability bindings
- institutional registries
- representative or professional registries
- identity and assurance requirements
- retention and data-handling constraints
- notification and acknowledgement mechanisms
- language and localization
- application specifications
- other locally governed configuration

This creates a separation between the common architectural capability and the conditions under which that capability may execute in a particular environment.

Conceptually:

**Common Platform → Deployment Unit → Jurisdictional Policy and Bindings → Local Capabilities → Governed Execution → Evidence**

### 14.2 Ecosystem Participants

A governed execution may involve many participants, including:

- infrastructure providers
- Deployment Unit operators
- platform providers
- capability developers
- model providers
- professional or domain representatives
- institutional participants
- users

These participants need not be controlled by a single organization. Their authority, responsibilities, contributions, and access may differ according to role and execution context.

Deployment Units may enable local operators and domain specialists to contribute jurisdiction-specific knowledge, capabilities, institutional relationships, and operational services without requiring the common platform provider to become the expert or operator for every jurisdiction.

### 14.3 Cross-Deployment-Unit Interaction

Some interactions may cross Deployment Unit or jurisdictional boundaries.

For example, a user associated with a Canadian Deployment Unit may need to interact with an institution or representative operating through a Deployment Unit in a European jurisdiction.

Conceptually:

**User → Originating Deployment Unit → Governed Federation → Destination Deployment Unit → Local Capability → Institution**

The originating environment may establish or contribute identity, intent, evidence, and delegated authority. The destination environment may resolve the local capability, applicable constraints, institutional channel, and permissible execution.

Both environments may contribute evidence to the resulting interaction.

This model does not imply that authority granted in one jurisdiction is automatically valid in another. Federation must preserve the distinction between transporting evidence or intent and establishing authority to execute within a destination environment.

### 14.4 Deployment Units as Execution-Economy Boundaries

Within the broader Execution Economy, a Deployment Unit may serve simultaneously as a:

- technical boundary
- operational boundary
- trust boundary
- governance boundary
- data-sovereignty boundary
- jurisdictional execution boundary
- economic participation boundary

This allows ISEDR to be treated as a vertical platform within the Execution Economy rather than as a globally uniform complaint service.

Local operators, capability developers, professional representatives, institutional participants, and infrastructure providers may contribute different forms of value while operating through a common governed-execution architecture.

The specific commercial, licensing, certification, compensation, federation, and operator mechanisms are outside the scope of this RFC.

### 14.5 Implementation Independence

This RFC does not define:

- how jurisdiction is technically resolved
- how policy selection or capability binding is implemented
- how Deployment Units establish trust
- how cross-Deployment-Unit authorization is transported or evaluated
- how federation protocols operate
- how institutional endpoints are discovered or authenticated
- how local legal requirements are encoded or verified
- how economic participation is calculated or settled

Those mechanisms may be defined by separate specifications, implementations, agreements, or proprietary systems.

------------------------------------------------------------------------

## 15. Relationship to CaralisLabs Architecture

ISEDR is conceptually compatible with several existing CaralisLabs architectural directions.

### 15.1 Identity

Participants require identities appropriate to their roles and assurance requirements.

### 15.2 Authorization

Access to claims, evidence, and institutional capabilities can be governed through explicit authorization.

### 15.3 Delegation

User-controlled authority can be expressed as scoped delegation rather than credential sharing.

### 15.4 Capabilities

Actions such as submission, notification, acknowledgement, representation, escalation, or institutional response may be exposed as capabilities.

### 15.5 PER and Governed Execution

Consequential operations can execute through defined pipelines with observable execution events and receipts.

### 15.6 Deployment Units

ISEDR may operate as a vertical platform on Deployment Units. Different organizations or operators may host compatible platform instances within separately controlled technical, operational, governance, trust, sovereignty, jurisdictional, and economic-participation boundaries.

### 15.7 Federation

Users, representatives, operators, and institutions may exist in different administrative domains, Deployment Units, and jurisdictions. Federation may therefore become relevant to identity, authorization, delegated authority, capability invocation, institutional routing, and evidence exchange. Federation does not itself confer destination-side execution authority.

The conceptual relationship can be summarized as:

**Person → Identity → Claim/Capability → Authorization/Delegation → Governed Execution → Institution/Representative → Receipt/Evidence**

------------------------------------------------------------------------

## 16. Potential Evolution

ISEDR can be explored incrementally rather than requiring universal institutional adoption.

### Phase 1 — Independent Evidence

- protected submissions
- integrity references
- timestamps
- receipts
- intended-recipient designation

### Phase 2 — Notification

- notification attempts
- delivery evidence where technically available
- claim-status tracking

### Phase 3 — Delegated Representation

- scoped access
- representatives
- access evidence
- representative actions

### Phase 4 — Institutional Participation

- registered institutional channels
- authenticated delivery
- acknowledgements
- responses
- status transitions

### Phase 5 — Federated Interaction Network

- multiple operators and jurisdiction-specific Deployment Units
- institutional capabilities
- cross-domain and cross-DU authorization resolution
- governed federation
- interoperable receipts
- aggregate operational insights

These phases are conceptual and do not constitute a committed product roadmap.

------------------------------------------------------------------------

## 17. Non-Goals

This RFC does not:

- create a legal definition of notice or service
- determine whether a user's claim is true
- replace courts, regulators, ombudsmen, lawyers, or institutional complaint processes
- prescribe a specific cryptographic implementation
- prescribe a specific identity provider
- prescribe a specific storage architecture
- define a public complaint or reputation-scoring service
- establish legal representation merely through technical delegation
- require institutions to recognize independent submissions
- define a complete commercial product

------------------------------------------------------------------------

## 18. Design Principles

The following principles summarize the framework:

1. **No consequential request without a receipt.**
2. **No consequential interaction without reciprocal evidence where reciprocal participation exists.**
3. **Evidence of submission is not evidence that a claim is valid.**
4. **Evidence of notification is not automatically evidence of legally recognized delivery.**
5. **Custody does not imply visibility.**
6. **Visibility does not imply authority.**
7. **Authority should be explicitly delegable and scoped.**
8. **Users should retain evidence concerning their own consequential interactions.**
9. **Private claims and aggregate operational patterns should remain distinct.**
10. **AI may assist interaction, but consequential actions should cross explicit execution boundaries.**
11. **Portable governed execution does not require identical execution everywhere.**
12. **Federation can transport intent and evidence without automatically conferring destination-side authority.**
13. **Jurisdiction-specific execution should be resolved through governed policies, bindings, capabilities, and local context rather than indiscriminately embedded into the common platform core.**

------------------------------------------------------------------------

## 19. Intellectual Property and Licensing

This RFC constitutes a public disclosure and forms part of the CaralisLabs research and RFC portfolio.

The concepts, terminology, research models, Independent Submission, Evidence, and Delegated Representation (ISEDR) framework, reciprocal-evidence principles, independent evidence layer, sealed-submission model, claim lifecycle, user-controlled delegated representation model, institutional-channel model, privacy-preserving pattern-discovery approach, Deployment-Unit-based jurisdictional execution model, jurisdiction-aware capability and policy resolution concepts, cross-Deployment-Unit interaction model, Execution-Economy vertical model, and related execution-and-evidence approaches described herein are subject to the intellectual-property and licensing terms defined in the RFC portfolio's `LEGAL.md`.

These concepts constitute pre-existing intellectual work of the author and are published to establish authorship, public disclosure, conceptual lineage, defensive disclosure, and prior art.

Publication of this RFC does not transfer ownership of the disclosed work and does not grant any additional license, assignment of intellectual property, patent rights, trademark rights, or commercial implementation rights except as expressly stated in `LEGAL.md` or in a separate written agreement.

This RFC defines a conceptual research and systems framework rather than a specific implementation. Any future implementations, protocols, cryptographic mechanisms, receipt formats, delegation systems, identity or authorization mechanisms, institutional gateways, applications, services, analytics, software, APIs, operational processes, or commercial applications may be separately licensed, proprietary, open source, commercial, academic, or otherwise independently governed.

The conceptual disclosure intentionally does not require disclosure of private implementation details, security mechanisms, operational configurations, algorithms, protocol internals, source code, Deployment Unit internals, jurisdiction-resolution mechanisms, policy-resolution mechanisms, capability-binding mechanisms, federation internals, deployment architecture, or other implementation-specific know-how that may constitute separate intellectual property or trade secrets.

Earlier revisions of this RFC may be published under different terms. Rights validly granted under any earlier terms are not purported to be revoked by this revision. See `LEGAL.md` for the portfolio licensing history and current policy.

------------------------------------------------------------------------

## 20. Conclusion

Digital systems increasingly mediate consequential relationships between individuals and institutions.

Yet sophisticated digital interfaces do not necessarily provide individuals with durable evidence that consequential requests were submitted, received, acknowledged, or acted upon.

ISEDR proposes a different starting point:

> A person should be able to establish durable evidence of a consequential submission without depending exclusively on the institution to preserve or acknowledge that evidence.

From that foundation, additional capabilities become possible:

**Submission → Evidence → Delegation → Representation → Institutional Participation → Reciprocal Evidence → Aggregate Insight**

Deployment Units add another dimension:

**Common Platform → Jurisdictional Deployment Unit → Local Capabilities and Policies → Governed Interaction → Evidence**

This allows the framework to evolve as a vertical of the Execution Economy: conceptually portable across environments while remaining governable according to local execution conditions.

The objective is not to create another complaint website.

The objective is to explore infrastructure through which individuals and institutions can participate in consequential digital interactions with clearer authority, stronger evidence, greater privacy, and more accountable execution.

------------------------------------------------------------------------

## Final Note

A request without acknowledgement is an unreliable protocol.

> If something important happens, there should be evidence that it happened.
