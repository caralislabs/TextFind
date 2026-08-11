# TF-RFC-0020

# TF-RFC-0020-DOMAIN-CAPABILITIES-AND-PORTABLE-GOVERNED-EXECUTION

## Domain Capabilities and Portable Governed Execution

## From Portable Software to Portable Governed Capabilities

**Status:** Public Draft
**Author:** Nicolae Dumitru Caralicea / CaralisLabs
**Category:** Architecture / Governed Execution / Domain Capabilities
**Created:** August 2026
**Discussion:** Public
**Filename:** TF-RFC-0020-DOMAIN-CAPABILITIES-AND-PORTABLE-GOVERNED-EXECUTION.md

---

# Abstract

Computing has repeatedly advanced by raising the level at which developers and organizations reason about execution.

Operating systems abstracted hardware. Virtual machines abstracted machine environments. Managed runtimes made software portable across systems. Containers and orchestration platforms extended portability across increasingly distributed infrastructure.

AI, autonomous systems, robotics, distributed intelligence, and modern enterprise workflows suggest that another abstraction boundary is emerging.

The unit that ultimately matters is increasingly not the server, container, service, model, agent, or even application.

It is the **capability**.

This RFC introduces the **Domain Capability** as an architectural abstraction and proposes **Portable Governed Execution** as a model in which capabilities can execute across compatible environments while preserving the governance properties under which their execution is authorized and trusted.

The central proposition is:

> **Define Once. Execute Governably Anywhere.**

---

# 1. From Applications to Capabilities

Applications describe software artifacts.

Capabilities describe **abilities**.

An organization or operational system does not fundamentally need a collection of microservices, containers, models, or agents.

It needs abilities such as:

* understanding documents,
* acquiring customers,
* assessing claims,
* coordinating machines,
* detecting anomalies,
* inspecting manufactured components,
* navigating autonomous systems,
* analyzing scientific observations,
* or performing other meaningful functions.

The implementation of such an ability may change substantially while the ability itself remains recognizable.

This suggests that **Capability** may become a more durable architectural abstraction than **Application**.

---

# 2. Domain Capability

This RFC defines a **Domain Capability** as:

> **A coherent ability to perform a function within a defined domain through governed execution.**

The domain provides semantic context.

Examples might include:

```text
Healthcare
    └── Clinical Document Analysis

Manufacturing
    └── Autonomous Quality Inspection

Robotics
    └── Navigation

Financial Services
    └── Claims Assessment

Enterprise Operations
    └── Customer Acquisition
```

The concept deliberately generalizes the established notion of a **Business Capability**.

A Business Capability can therefore be understood as a Domain Capability associated with organizational or commercial activity.

Other Domain Capabilities may belong to robotics, science, manufacturing, infrastructure, healthcare, transportation, or domains that do not fit naturally within the traditional language of business architecture.

The architectural primitive is therefore not the Business Capability.

It is the more general **Domain Capability**.

---

# 3. Raising the Execution Abstraction

One of the important transitions in software history occurred when applications stopped being tightly coupled to individual machines.

The Java Virtual Machine provides a useful historical analogy.

Instead of targeting a particular operating environment directly, applications could target a managed runtime.

The proposition became:

> **Write Once, Run Anywhere.**

The significance of this transition extended beyond portability.

Important execution concerns moved from individual applications into a common runtime environment.

Modern distributed and intelligent systems may require a similar transition at a higher architectural level.

Instead of making every application independently responsible for execution governance, some of those concerns can become properties of the execution environment itself.

The abstraction consequently moves upward:

```text
Portable Code
      ↓
Portable Applications
      ↓
Portable Workloads
      ↓
Portable Governed Capabilities
```

This RFC does not propose replacing existing runtime, container, orchestration, or infrastructure abstractions.

It proposes an additional abstraction above them.

---

# 4. Execution-Time Governance

Modern systems increasingly combine deterministic software with probabilistic AI, autonomous agents, external services, humans, data resources, physical systems, and distributed infrastructure.

Knowing that an application or model executed is no longer sufficient.

Increasingly important questions include:

* Who initiated the execution?
* Under whose authority did it occur?
* Which policies applied?
* Which components participated?
* Which resources were accessed?
* Where was human intervention required?
* What evidence was produced?
* Can the execution later be reconstructed?

These are execution concerns.

This RFC therefore introduces a central principle:

> **Governance should not merely describe how execution was expected to occur. Where technically possible, governance should participate in determining how execution is permitted to occur.**

We refer to this property as **Execution-Time Governance**.

Governance therefore becomes an operational property of execution rather than solely a surrounding administrative process.

---

# 5. Portable Governed Execution

Traditional software portability asks:

> Can this software run somewhere else?

Portable Governed Execution asks a stronger question:

> **Can this capability execute somewhere else without losing the governance properties that give its execution meaning and trust?**

Those properties may include:

* authority,
* identity,
* policy,
* provenance,
* accountability,
* execution constraints,
* and evidence.

The objective is therefore not simply workload portability.

It is **governance-preserving capability portability**.

A capability should be able to execute across compatible environments without silently losing the properties under which its execution was intended to occur.

This changes portability from primarily a technical compatibility problem into both a technical and governance compatibility problem.

---

# 6. Domain Capability Execution

At a conceptual level, the architecture can be viewed as:

```text
DOMAIN
   │
   ▼
DOMAIN CAPABILITY
   │
   ▼
GOVERNED EXECUTION
   │
   ▼
COMPATIBLE EXECUTION ENVIRONMENT
   │
   ▼
INFRASTRUCTURE
```

Each layer answers a different question.

## Domain Capability

**What can the system do?**

## Governed Execution

**Under what authority and constraints may it do it?**

## Execution Environment

**Where can that capability execute while satisfying its requirements?**

## Infrastructure

**What physical and virtual resources ultimately realize that environment?**

This separation allows domain meaning to remain relatively independent from infrastructure implementation.

It also creates a useful architectural separation:

> **WHAT → GOVERNANCE → WHERE**

The realization of the capability may involve many implementation components, but those components should not unnecessarily define the semantic identity of the capability itself.

---

# 7. The Execution Environment as a Logical Machine

A capability should not necessarily need to understand the physical topology on which it executes.

Its compatible execution environment may eventually consist of:

* one machine,
* multiple servers,
* cloud resources,
* Kubernetes clusters,
* enterprise infrastructure,
* edge computers,
* specialized accelerators,
* robotic systems,
* or combinations of these.

From the perspective of the capability, these resources can form a **logical execution environment**.

This extends an old idea.

The virtual machine abstracted the physical machine.

The emerging execution environment can abstract **distributed infrastructure into a logical environment for governed capabilities**.

The physical composition of that environment may change without necessarily changing the semantic identity of the Domain Capabilities executing within it.

---

# 8. Domain Independence

Execution governance should not fundamentally depend upon whether the capability belongs to finance, robotics, manufacturing, healthcare, enterprise operations, or another domain.

Consider two capabilities:

```text
CUSTOMER_ACQUISITION
Domain: Enterprise Operations
```

and:

```text
ROBOT_NAVIGATION
Domain: Robotics
```

Their purposes are radically different.

Yet both may require:

* explicit authority,
* policy enforcement,
* controlled resource access,
* observable execution,
* provenance,
* and evidence.

The execution model can therefore remain general while the capabilities remain domain-specific.

This separation is one of the principal motivations for introducing **Domain Capability** as the higher-level abstraction.

Domain describes **meaning**.

Governed execution describes **operational realization**.

---

# 9. Capability Composition

Complex capabilities may be constructed from simpler capabilities.

For example:

```text
WAREHOUSE_FULFILLMENT
        │
        ├── ORDER_PROCESSING
        │
        ├── INVENTORY_MANAGEMENT
        │
        ├── ROBOT_FLEET_COORDINATION
        │       │
        │       ├── NAVIGATION
        │       └── TASK_ALLOCATION
        │
        └── SHIPPING
```

This allows business, software, AI, and physical-system boundaries to coexist within the same conceptual architecture.

A capability may therefore be independently useful while simultaneously participating in larger capabilities.

This creates the possibility of systems being designed increasingly through **capability composition** rather than application integration alone.

It also allows capabilities from different domains to participate in larger operational systems without requiring every capability to share the same domain classification.

---

# 10. Capabilities as Operational Assets

If capabilities can be independently defined, governed, composed, and executed across compatible environments, they can potentially become durable operational assets.

Capabilities might eventually be:

* created,
* versioned,
* discovered,
* composed,
* evaluated,
* exchanged,
* operated,
* and improved independently.

The producer of a capability would not necessarily need to operate every environment in which that capability executes.

Likewise, an organization operating an execution environment would not necessarily need to develop every capability available within it.

This separation may enable new forms of collaboration between:

* capability producers,
* infrastructure operators,
* organizations,
* domain specialists,
* technology providers,
* and independent contributors.

The capability consequently becomes not merely a software abstraction but potentially an economic and operational unit.

---

# 11. Toward a Capability Economy

Software ecosystems created enormous value by separating application development from hardware production.

Cloud computing further separated infrastructure ownership from application operation.

Portable Governed Execution may allow another separation:

> **Capability creation from capability operation.**

An ecosystem could consequently emerge in which reusable Domain Capabilities are created by one participant, operated by another, composed by another, and consumed within environments governed by the organizations using them.

Value could increasingly attach to the ability to provide trusted, reusable, governable capabilities rather than exclusively to complete standalone applications.

This possibility aligns with a broader transition toward an **Execution Economy**, where value increasingly attaches not merely to software ownership but to trusted executable abilities.

The precise mechanisms required to support such ecosystems remain intentionally outside the scope of this RFC.

---

# 12. A New Portability Boundary

The historical progression can be viewed as:

```text
Hardware
   ↓
Operating Systems
   ↓
Virtual Machines
   ↓
Managed Runtimes
   ↓
Containers
   ↓
Distributed Execution
   ↓
Governed Execution Environments
   ↓
Domain Capabilities
```

At each stage, some complexity moves beneath a new abstraction boundary.

The proposed next transition is from asking:

> **Where does this software run?**

toward asking:

> **Which capabilities can execute here, under what authority and governance?**

That changes the unit through which systems can be understood.

The infrastructure remains necessary.

The software remains necessary.

The execution mechanisms remain necessary.

But they increasingly exist beneath an abstraction representing **what the overall system is capable of doing**.

---

# 13. Design Principles

The architecture proposed by this RFC is guided by several principles.

## 13.1 Purpose Should Be Separated From Implementation

Domain Capabilities describe abilities rather than particular software implementations.

## 13.2 Governance Should Participate in Execution

Important controls should be enforceable during execution rather than existing solely as documentation or retrospective audit.

## 13.3 Infrastructure Should Be Replaceable

Changing compatible infrastructure should not unnecessarily change the semantic identity of a capability.

## 13.4 Execution Should Produce Evidence

Trustworthy execution should make it possible to understand how meaningful outcomes were produced.

## 13.5 Capabilities Should Be Composable

More sophisticated abilities should be constructible from simpler ones.

## 13.6 Portability Is Conditional

A capability executes across compatible environments, not arbitrary environments.

## 13.7 Domain Meaning Should Remain Separate From Runtime Mechanics

The execution substrate should remain general enough to support capabilities from very different domains.

## 13.8 Governance Is Part of Portability

Moving a capability between compatible environments should not silently remove the governance properties required for its trusted execution.

---

# 14. Define Once. Execute Governably Anywhere.

The objective is not to recreate the JVM at another layer.

Nor is it simply to provide another application deployment abstraction.

The objective is to make the **capability itself** the durable unit.

A Domain Capability describes what can be done.

A governed execution environment determines whether and under what constraints it may execute.

Compatible infrastructure provides the resources required to realize that execution.

The resulting proposition is:

> **Define Once. Execute Governably Anywhere.**

Not every capability will execute everywhere.

A robotic navigation capability may require resources unavailable in a conventional enterprise environment.

A computational capability may require specialized accelerators.

A regulated capability may require governance properties unavailable in another environment.

Portability therefore does not mean universal execution.

It means that where compatible conditions exist, moving the capability should not require abandoning the governance properties that make its execution trustworthy.

---

# 15. What Comes Next

This RFC intentionally defines the architectural direction rather than the mechanisms used to realize it.

Several questions naturally follow:

* How are Domain Capabilities represented?
* How are execution requirements expressed?
* How is compatibility determined?
* How are executable components discovered and trusted?
* How are resources associated with capability requirements?
* How is capability composition represented?
* How is execution evidence represented?
* How can capabilities operate across independently governed environments?

These are important architectural and engineering questions.

They are deliberately outside the implementation scope of this public RFC.

Some aspects may eventually require public contracts or interoperability specifications where ecosystem participation benefits from them.

Other aspects may remain implementation-specific.

The purpose of this RFC is to establish the abstraction and architectural direction around which that work can converge.

---

# 16. Claims Scope (Informal)

This RFC publicly establishes and documents architectural concepts including:

* Domain Capabilities as first-class execution abstractions
* Domain Capability as a generalization beyond Business Capability
* Portable Governed Execution
* Governance-preserving capability portability
* Execution-Time Governance applied to Domain Capabilities
* Separation of domain meaning from execution infrastructure
* Logical governed execution environments for Domain Capabilities
* Infrastructure-independent capability identity
* Capability composition across heterogeneous domains
* Conditional portability across compatible governed execution environments
* Governance as a portability property
* Capabilities as durable operational assets
* Separation between capability creation and capability operation
* Governed capability ecosystems
* Portable governed capabilities as an abstraction above portable workloads

The central architectural proposition established by this RFC is:

> **Define Once. Execute Governably Anywhere.**

This proposition describes an execution model in which the semantic identity of a Domain Capability can remain stable while its execution environment changes, provided that the target environment satisfies the capability's applicable execution and governance requirements.

The concepts described in this RFC are intended as architectural models and strategic direction.

This section is an informal statement of conceptual scope. It is not intended to define patent claims, establish patentability, or provide a legal determination regarding the scope or ownership of intellectual-property rights.

---

# 17. IP & Licensing Considerations

This RFC is intended as:

* architectural positioning,
* conceptual framing,
* public technical disclosure,
* strategic direction,
* and prior-art-style publication.

The document intentionally describes **what** Domain Capabilities and Portable Governed Execution represent while avoiding detailed disclosure of **how** CaralisLabs may realize them.

In particular, this RFC intentionally avoids disclosure of implementation-specific details concerning:

* Domain Capability packaging,
* capability execution contracts,
* executable-component packaging and resolution,
* runtime compatibility resolution,
* resource declaration and binding mechanisms,
* execution-environment internals,
* distributed execution coordination,
* policy evaluation mechanisms,
* capability discovery protocols,
* execution evidence internals,
* trust and attestation mechanisms,
* federation protocols,
* deployment algorithms,
* orchestration algorithms,
* and proprietary runtime implementation details.

The purpose of this publication is to:

* establish the architectural concept of the Domain Capability,
* establish Portable Governed Execution as an architectural direction,
* contribute these concepts to broader technical discussion,
* establish terminology for capability-oriented governed execution,
* publicly document the direction toward governance-preserving capability portability,
* and establish an attributable public record of this architectural work.

Publication of this conceptual architecture does not imply publication of the implementation mechanisms used, developed, or subsequently developed by CaralisLabs.

## 17.1 Pre-Existing Intellectual Property

The architectural work, terminology, written expression, diagrams, and original frameworks presented in this RFC constitute pre-existing work of the author except where they reference established industry concepts or terminology.

Future collaboration, implementation efforts, consulting engagements, integrations, or derivative systems do not by themselves:

* transfer ownership of the author's pre-existing work,
* assign rights to CaralisLabs proprietary implementations,
* transfer ownership of independently developed runtime mechanisms,
* assign implementation-specific intellectual property,
* or create an implicit transfer of rights.

Any assignment, transfer, or exclusive licensing of intellectual-property rights must be established separately through an explicit agreement.

## 17.2 Scope of Use

Subject to the license stated below, this RFC is intended to permit and encourage:

* reading and discussion,
* reference and citation,
* architectural exploration,
* academic and industry discussion,
* independent experimentation,
* adaptation of the published conceptual material,
* and development of related or derivative ideas.

Publication of this RFC does not grant access to or rights in undisclosed CaralisLabs technology, source code, proprietary specifications, internal protocols, implementation mechanisms, deployment systems, or other confidential material.

## 17.3 Conceptual Architecture vs. Implementation

A deliberate distinction is made between:

### Public Conceptual Architecture

The concepts disclosed in this RFC, including:

* Domain Capabilities,
* Portable Governed Execution,
* governance-preserving portability,
* capability composition,
* execution-time governance,
* and logical governed execution environments.

and:

### Implementation

The:

* software,
* algorithms,
* protocols,
* runtime mechanisms,
* execution contracts,
* packaging formats,
* resource-resolution mechanisms,
* trust mechanisms,
* deployment mechanisms,
* operational systems,
* and other technologies

that may realize these concepts.

The first is intentionally discussed publicly through this RFC.

The second may remain:

* proprietary,
* confidential,
* separately licensed,
* independently published,
* selectively open-sourced,
* standardized where interoperability requires it,
* or otherwise protected at the discretion of its respective owner.

This RFC therefore establishes architectural direction without attempting to specify a complete implementation.

## 17.4 Public Contracts vs. Proprietary Mechanisms

Future interoperability may require certain interfaces, contracts, schemas, or protocols to be publicly documented.

Publication of such contracts does not inherently require publication of the mechanisms implementing them.

A public specification may describe:

* required inputs,
* required outputs,
* observable semantics,
* compatibility expectations,
* interoperability behavior,
* or conformance requirements,

while the internal machinery satisfying those requirements remains independently implemented.

CaralisLabs may therefore selectively publish interfaces necessary for ecosystem participation while retaining proprietary implementations behind those interfaces.

This distinction allows an open capability ecosystem and proprietary execution technologies to coexist.

## 17.5 No Implicit Assignment

No ownership, assignment, transfer, exclusive license, partnership right, or other expansion of intellectual-property rights occurs merely through:

* access to this document,
* reading or discussing its contents,
* referencing the concepts,
* experimenting with related architectures,
* implementing independently developed systems inspired by the published concepts,
* participating in technical discussions,
* or collaborating with the author or CaralisLabs on unrelated work.

Any transfer, assignment, or special licensing arrangement must be:

* explicit,
* documented,
* and mutually agreed upon by the relevant parties.

## 17.6 Attribution and Terminology

Where this RFC is referenced in technical, academic, architectural, or industry discussion, attribution to the RFC and its author is encouraged and, where required by the applicable license, must be provided.

Suggested reference:

> **TF-RFC-0020 — Domain Capabilities and Portable Governed Execution, Nicolae Dumitru Caralicea / CaralisLabs, 2026.**

The terminology developed in this RFC is intended to provide a vocabulary for discussing capability-oriented governed execution.

Use of terminology alone should not be interpreted as endorsement by, affiliation with, or participation in CaralisLabs.

---

# 18. License

This document is released under the **Creative Commons Attribution 4.0 International (CC BY 4.0)** license.

Under that license, the published content of this RFC may be:

* shared,
* redistributed,
* adapted,
* and built upon,

provided that appropriate attribution is given.

The license applies to the **published content of this RFC**.

It does not, merely by publication of this document, license:

* CaralisLabs source code,
* proprietary runtime implementations,
* non-public specifications,
* confidential implementation details,
* trademarks,
* separately licensed software,
* or other intellectual property not contained in this RFC.

---

# 19. Public Disclosure Boundary

This RFC intentionally establishes a public architectural boundary.

It discloses the proposition that:

> **Domain Capabilities can become portable units of governed execution across compatible logical execution environments.**

It does **not** attempt to disclose the complete technical machinery required to realize that proposition.

Questions concerning:

* capability representation,
* packaging,
* resolution,
* execution contracts,
* resource binding,
* compatibility negotiation,
* trust,
* attestation,
* federation,
* runtime coordination,
* and implementation-specific governance enforcement

remain outside the implementation scope of this public RFC.

Those mechanisms may be addressed selectively through:

* future public specifications,
* interoperability contracts,
* standards work,
* proprietary implementations,
* internal RFCs,
* open-source components,
* or other forms of publication where appropriate.

There is no requirement that all such mechanisms eventually be publicly disclosed.

The distinction is intentional:

> **The architectural direction is public.
> The implementation strategy is selectively disclosed.**

---

# 20. Conclusion

The evolution of computing has repeatedly moved complexity beneath higher-level execution abstractions.

The next useful abstraction may not be another way of packaging software.

It may be the **Domain Capability**.

AI systems, enterprise workflows, autonomous machines, robotics, distributed infrastructure, and future intelligent systems all need abilities that can be executed while preserving authority, governance, accountability, and evidence.

Portable Governed Execution proposes that these properties belong to the execution architecture itself.

The long-term transition is therefore:

> from **portable software**

to

> **portable governed capabilities**.

The architectural promise is:

> **Define Once. Execute Governably Anywhere.**

This RFC intentionally establishes that direction publicly.

**The realization of that promise is what comes next.**
