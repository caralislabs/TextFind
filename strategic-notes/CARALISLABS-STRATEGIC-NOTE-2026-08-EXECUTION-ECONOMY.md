# What Exactly Is CaralisLabs Building?

**CaralisLabs Strategic Note**  
**Status:** Public  
**Date:** August 2026  
**Subject:** Execution Economy, Domain Capabilities, Deployment Units, Portable Governed Execution, Federation, and Ecosystem Development

> This document captures the current direction of CaralisLabs research and development. It is a strategic architectural perspective rather than an implementation specification. Implementation mechanisms are intentionally outside its scope.

---

# Some Insight from Inside Our Laboratories

We've been asked a few times:

**What exactly is CaralisLabs doing?**

It's a fair question.

We publish research around execution governance, authority, capabilities, federation, and what we call the **Execution Economy**. At the same time, a significant part of our effort goes into engineering work that isn't always visible from the outside.

Increasingly, however, the research and the engineering are becoming parts of the same story.

So this seems like a good moment to share some insight from inside our laboratories — what we're researching, what we're building, and where we hope others may eventually participate.

---

# From Intelligence to Execution

For some time, we've been using the term **Execution Economy** to describe a shift we believe is taking place as AI becomes more capable, less expensive, and more widely available.

Our starting observation is relatively simple.

If increasingly capable intelligence becomes available to almost everyone, access to intelligence alone becomes less differentiating.

The important question gradually moves from:

> **What can the AI tell us?**

to:

> **What can we reliably do with that intelligence?**

That takes us from intelligence to **execution**.

But execution, as we see it, means much more than connecting an AI model to a few tools and allowing an agent to perform actions.

The moment intelligence begins participating in real operations, other questions become unavoidable.

Who authorized the work?

Under which policies was it performed?

What was the system allowed to do?

Which AI models, software components, humans, and resources participated?

Where did the execution take place?

What evidence was produced?

And afterward, can we reconstruct what actually happened?

A significant part of the research and development at CaralisLabs is focused on these questions.

---

# Intelligence Is Not Authority

These questions led us toward **Execution-Time Governance**.

Governance shouldn't exist only around execution as documentation, organizational policy, approval processes, and retrospective audit.

Where technically possible, we believe governance should participate in determining how execution is permitted to occur.

That also led us to a distinction we consider fundamental:

> **Intelligence is not authority.**

A system may possess enough intelligence to determine what should happen.

That doesn't automatically give it the authority to make it happen.

As AI moves from generating information toward participating in consequential operational processes, this distinction becomes increasingly important.

The question is no longer simply whether an AI system *can* perform an action.

We need architectures capable of determining whether that execution is **authorized, governed, observable, attributable, and reconstructable**.

This is part of what we mean by **governed execution**.

---

# What Is Actually Being Executed?

As we continued building, another question emerged.

What is the meaningful thing being executed?

An application?

An AI model?

An agent?

A container?

A workflow?

All of these remain useful implementation concepts.

But increasingly, we believe there is a more durable abstraction:

> **the Domain Capability.**

A Domain Capability represents an ability to accomplish something meaningful within a particular domain.

Document Intelligence can be a capability.

Claims Assessment can be a capability.

Customer Acquisition can be a capability.

Autonomous Inspection can be a capability.

Robot Navigation can be a capability.

The implementation may change.

The models may change.

The infrastructure may change.

But the capability itself can remain conceptually stable.

A Business Capability therefore becomes one kind of Domain Capability.

Other Domain Capabilities may belong to robotics, healthcare, manufacturing, science, infrastructure, transportation, finance, or domains we haven't considered yet.

This thinking recently led us to publish:

**TF-RFC-0020 — Domain Capabilities and Portable Governed Execution**

The RFC asks a question that goes beyond traditional software portability:

> **Can a capability execute somewhere else without losing the governance properties that give its execution meaning and trust?**

Our proposition is:

> **Define Once. Execute Governably Anywhere.**

---

# From Domain Capabilities to Deployment Units

Once we started thinking about portable governed capabilities, another architectural question became unavoidable:

**Where do those capabilities execute?**

This is where another concept emerging from our engineering work becomes important:

**the Deployment Unit.**

A Deployment Unit is how we're beginning to think about a **logical governed execution environment**.

Underneath it may be one machine or several machines.

Those machines may eventually exist on dedicated servers, private infrastructure, cloud infrastructure, edge environments, specialized hardware, or combinations of these.

From the perspective of a Domain Capability, however, much of that physical complexity shouldn't necessarily matter.

The capability should see a compatible environment in which it can execute under the required governance.

Conceptually:

**Domain Capability**  
↓  
**Governed Execution**  
↓  
**Deployment Unit**  
↓  
**Physical Infrastructure**

This gives us an abstraction boundary between the ability being provided and the machines that ultimately realize its execution.

It is somewhat analogous to earlier transitions in computing where increasingly complex physical environments disappeared beneath higher-level execution abstractions.

Only now, the abstraction we are interested in isn't merely portable code.

It is **portable governed capability execution**.

---

# Sovereignty Becomes an Architectural Property

Deployment Units also give the increasingly important discussion around **digital and AI sovereignty** a more concrete architectural meaning.

Sovereignty is often discussed primarily in terms of geography or cloud-provider selection.

Those considerations matter.

But we believe the architectural question is broader.

A Deployment Unit can establish an execution boundary around infrastructure, resources, identity, governance, data, and operational control.

That boundary might belong to an organization.

It might exist within a particular jurisdiction.

It might run entirely on dedicated infrastructure.

It might operate on infrastructure controlled by a customer or partner.

It might eventually extend toward edge or physical systems.

Different Deployment Units may therefore represent different operational and sovereignty boundaries.

This also means sovereignty doesn't necessarily have to imply isolation.

Independently controlled Deployment Units could eventually collaborate through federation while preserving their respective authority, infrastructure, data, and governance boundaries.

An organization should not necessarily have to surrender control of its execution environment in order to participate in a larger execution ecosystem.

---

# The Sandbox Is a Deployment Unit

This is where much of the infrastructure engineering currently happening inside CaralisLabs fits into the larger picture.

We're building a **sandbox**.

But architecturally, the sandbox isn't a special category of infrastructure.

> **The sandbox is a Deployment Unit configured for experimentation, development, testing, and collaboration.**

That distinction matters.

Because once Deployment Units become reproducible, the same architectural model can potentially support many purposes.

A Deployment Unit could eventually be:

- a development sandbox,
- a dedicated organizational environment,
- a sovereign execution environment,
- a specialized operational environment,
- an edge environment,
- or another form of governed execution environment.

So we're not simply automating the creation of a sandbox.

We're working toward the ability to create **reproducible governed execution environments**.

And we're getting close to having the first sandbox Deployment Unit available.

---

# Starting Small — Then Reproducing

We expect to open the first sandbox to a **limited number of participants**.

That's deliberate.

The first participants won't simply be users of a finished product.

We see them as early collaborators in an environment that is still evolving — people interested in experimenting, building, challenging assumptions, and helping us understand what becomes possible when governed execution and Domain Capabilities are placed in the hands of others.

As we learn from the first environment, improve the tooling, and make Deployment Units increasingly reproducible, we can create additional sandbox Deployment Units and gradually onboard more participants.

That gives us a different scaling model from simply putting everyone into one increasingly large centralized sandbox.

Instead, we can potentially grow through:

**one Deployment Unit**  
↓  
**several Deployment Units**  
↓  
**more participants**  
↓  
**different operational boundaries**  
↓  
**eventual federation**

Over time, that could become much more interesting than a single shared development environment.

It could become a growing collection of governed execution environments in which people build, experiment, and collaborate.

---

# But Where Do the Capabilities Live?

Once different people and organizations begin creating Domain Capabilities, another question immediately appears:

**How do those capabilities become discoverable?**

This is why another part of our direction involves **Domain Capability Registries**.

A registry could provide a common place where capabilities are published, described, discovered, evaluated, and eventually made available for use across compatible Deployment Units.

Some capabilities might be open source.

Some might be commercial.

Some might be created by CaralisLabs.

Many could be created independently by developers, companies, researchers, domain specialists, or community contributors.

The registry doesn't need to own those capabilities.

Its role is different.

It can become part of the connective tissue of the ecosystem by helping participants understand:

- What capabilities exist?
- Who provides them?
- What do they do?
- What do they require?
- Under what conditions can they execute?
- Which environments are compatible with them?

That gives us a useful separation:

> **Domain Capability Registry** — What capabilities are available?

> **Deployment Unit** — Where can they execute?

> **Governed Execution** — Under what authority and constraints may they execute?

> **Federation** — How can execution eventually span independently controlled environments?

These are different concerns, but together they begin to form an ecosystem architecture.

---

# A Community That Creates Capabilities

This is also where our idea of community becomes more concrete.

We aren't simply interested in creating a community around a software product.

We would like to create a community around **building Domain Capabilities and the governed environments in which those capabilities execute**.

A developer might create a Processing Element or Domain Capability and eventually publish it through a registry.

A domain specialist might bring knowledge about a problem that technologists don't possess.

A researcher might explore execution governance, provenance, federation, trust, or attribution.

An infrastructure specialist might experiment with Deployment Units.

Someone else might compose several capabilities into something none of their original creators anticipated.

Some capabilities could become open-source building blocks.

Others could become commercial intellectual property.

Some could remain internal to an organization.

The important thing is that the ecosystem doesn't depend on CaralisLabs creating everything.

In fact, it shouldn't.

---

# Companies and Organizations Have a Role Too

This isn't intended only for individual developers or researchers.

We're equally interested in conversations with **companies and organizations** that see potential intersections between this work and what they are building, operating, or trying to accomplish.

Those conversations don't need to fit a predefined partnership model.

A company might bring a real operational problem around which a Domain Capability could be developed.

Another might be interested in governed AI execution.

An organization might want to explore a dedicated or sovereign Deployment Unit within its own operational boundary.

An infrastructure provider might be interested in hosting, supporting, or eventually operating Deployment Units.

A technology company might have models, software, services, hardware, or other components that could participate in larger governed capabilities.

A research institution might want to investigate governance, provenance, trust, federation, or execution economics.

And organizations with deep expertise in particular industries may bring precisely the domain knowledge required to create capabilities that CaralisLabs would never attempt to define alone.

Some relationships may remain exploratory.

Others could eventually become technical collaborations, research projects, capability development, infrastructure partnerships, integrations, joint initiatives, or commercial relationships.

We don't want to decide in advance what every partnership should look like.

A much more interesting starting question is:

> **What could we build together that neither organization would build as effectively alone?**

---

# We Don't Intend to Own Everything

The future ecosystem we're imagining isn't one in which CaralisLabs creates every capability, owns every Deployment Unit, and solves every domain problem.

Quite the opposite.

We see an ecosystem in which different participants contribute different forms of value:

**Domain expertise.**

**Capabilities.**

**Technology.**

**Infrastructure.**

**Research.**

**Operation.**

**Integration.**

Those contributions can remain independently created while participating in larger governed executions.

A company could create a specialized capability and make it discoverable through a registry.

Another organization could operate the Deployment Unit where it executes.

Other capabilities could participate in the same execution.

And the consuming organization could retain control over its own operational boundary.

That is much closer to the ecosystem we want to explore.

---

# From Deployment Units to Federated Execution

As Deployment Units multiply, another part of our research becomes increasingly relevant:

**Federated Execution.**

Imagine one organization operating a Deployment Unit under its own governance boundary.

Another organization operates another.

A capability comes from a third participant.

Another capability comes from somewhere else.

Yet those capabilities may eventually participate in a larger execution without requiring every participant to surrender control of its infrastructure or governance.

Conceptually:

**Domain Capability Registries**  
↓  
**Domain Capabilities**  
↓  
**Governed Execution**  
↓  
**Deployment Units**  
↓  
**Federation**  
↓  
**Cross-Boundary Execution**

This raises difficult questions around identity, authority, trust, policy, evidence, compatibility, attribution, and interoperability.

Those are exactly the kinds of questions we're interested in researching and eventually realizing through architecture.

---

# Where the Execution Economy Appears

If capabilities can be independently created, discovered, governed, composed, and executed across compatible environments, something economically interesting begins to happen.

A capability might be created by one participant.

Operated by another.

Composed with capabilities created by others.

Executed inside an organization's sovereign Deployment Unit.

And contribute to an outcome consumed somewhere else.

Execution can produce evidence.

Contributions can become attributable.

Outcomes can become measurable.

And value can potentially flow between the participants who create capabilities, operate Deployment Units, provide infrastructure, compose capabilities, and consume the resulting outcomes.

This is where the **Execution Economy** becomes more than a description of AI automation.

It becomes a potential economic architecture.

The unit of value is no longer necessarily just software ownership, compute consumption, model access, or human effort.

Value can increasingly attach to **trusted executable capabilities and their contribution to outcomes**.

That is the larger direction we're investigating.

---

# The Architecture Is Starting to Connect

Increasingly, what once looked like separate research topics is becoming one architecture:

**Intelligence**  
↓  
**Authority**  
↓  
**Execution-Time Governance**  
↓  
**Domain Capabilities**  
↓  
**Domain Capability Registries**  
↓  
**Deployment Units**  
↓  
**Portable Governed Execution**  
↓  
**Federated Execution**  
↓  
**Execution Evidence & Attribution**  
↓  
**Economic Value**  
↓  
**Execution Economy**

This is why our research, RFCs, platform engineering, infrastructure automation, sandbox work, and ecosystem thinking increasingly reinforce one another.

We're investigating a fundamental question:

> **What architecture will be required when intelligence becomes abundant, but trusted execution remains scarce?**

---

# Intellectual Property and Public Disclosure

This Strategic Note intentionally describes the **architectural direction, conceptual models, and research perspective** of CaralisLabs at a public level.

Its publication is intended to encourage discussion, research, collaboration, interoperability, experimentation, and the development of an ecosystem around governed execution and Domain Capabilities.

Publication of these ideas should not be interpreted as publication of the complete mechanisms through which CaralisLabs implements or intends to implement them.

---

## Public Conceptual Scope

This Strategic Note publicly discusses concepts including, among others:

- the Execution Economy,
- Execution-Time Governance,
- Authority to Execute,
- Domain Capabilities,
- Domain Capability Registries,
- Deployment Units,
- sovereign execution boundaries,
- Portable Governed Execution,
- Federated Execution,
- Execution Evidence and Attribution,
- capability-oriented ecosystems,
- and execution economics.

These concepts form part of the public architectural vocabulary through which CaralisLabs describes its research and development direction.

The purpose of discussing these concepts publicly is to establish a visible architectural direction and provide a basis for technical, research, industry, and ecosystem discussion.

This section describes conceptual scope only.

It is not intended to define patent claims, establish patentability, or provide a legal determination regarding the ownership or scope of intellectual-property rights.

---

## Implementation Mechanisms

The mechanisms used to realize the architectural concepts described in this document are intentionally outside its scope.

This may include, without limitation:

- internal protocols,
- algorithms,
- execution semantics,
- orchestration mechanisms,
- runtime internals,
- security mechanisms,
- policy evaluation and enforcement mechanisms,
- capability representation and packaging,
- executable-component packaging and resolution,
- capability composition mechanisms,
- resource declaration, discovery, and binding,
- compatibility determination and negotiation,
- Deployment Unit provisioning and lifecycle mechanisms,
- infrastructure automation,
- registry internals,
- trust and attestation mechanisms,
- execution-evidence internals,
- federation protocols,
- distributed execution coordination,
- economic and attribution mechanisms,
- and other implementation-specific technologies.

Some of these mechanisms may eventually be published through RFCs, interoperability specifications, open-source projects, technical documentation, standards work, research, or other forms of public disclosure.

Others may remain proprietary or confidential.

Publication of an architectural concept does not imply a commitment to disclose every implementation mechanism required to realize it.

---

## Pre-Existing Intellectual Property

The architectural work, terminology, written expression, diagrams, research models, software, platform technologies, infrastructure mechanisms, and other independently developed work associated with CaralisLabs remain subject to the intellectual-property rights of their respective owners.

Participation in discussions, sandbox activities, research, experimentation, capability development, integrations, partnerships, or other forms of collaboration does not by itself:

- transfer ownership of pre-existing intellectual property,
- assign rights to CaralisLabs proprietary implementations,
- assign rights to technology independently developed by another participant,
- transfer ownership of independently developed Domain Capabilities,
- transfer ownership of Deployment Unit implementations or infrastructure technologies,
- or create an implicit assignment or exclusive license.

Any assignment, transfer, exclusive license, or other change in ownership of intellectual-property rights must be established separately through an explicit agreement between the relevant parties.

---

## Open and Proprietary Domain Capabilities

The ecosystem described in this Strategic Note is intentionally compatible with different intellectual-property models.

A Domain Capability may be:

- open source,
- publicly specified but privately implemented,
- proprietary,
- commercially licensed,
- organization-internal,
- collaboratively developed,
- research-oriented,
- or distributed under other terms determined by its creator or rights holder.

Participation in a Domain Capability Registry should not, by itself, imply transfer of ownership of a registered capability.

Registration is conceptually concerned with **discovery and ecosystem participation**, not automatic transfer of intellectual property.

Likewise, execution of a capability within a Deployment Unit should not inherently imply transfer of intellectual property between the capability provider, Deployment Unit operator, infrastructure provider, consuming organization, or other participants.

A capability creator should be able to retain rights in a capability while allowing it to participate in compatible governed execution environments under appropriate terms.

This separation is important to the ecosystem model described in this document.

---

## Public Contracts vs. Proprietary Mechanisms

An open or federated capability ecosystem may eventually require certain interfaces, contracts, schemas, protocols, or observable semantics to be publicly documented.

Interoperability does not necessarily require every implementation to be public.

A public contract might describe:

- required inputs,
- required outputs,
- observable semantics,
- capability metadata,
- compatibility expectations,
- conformance requirements,
- interoperability behavior,
- or other externally visible properties.

The mechanisms implementing those contracts may remain independently developed.

They may be proprietary, open source, confidential, separately licensed, standardized, or implemented differently by different participants.

CaralisLabs may therefore selectively publish interfaces or specifications necessary for ecosystem participation while retaining proprietary implementations behind those interfaces.

Other ecosystem participants may do the same with technologies they independently own.

This distinction allows **open interoperability and proprietary innovation to coexist**.

---

## Collaboration and Intellectual Property

CaralisLabs intends to explore different forms of collaboration with individuals, companies, research institutions, infrastructure providers, technology providers, domain specialists, and other participants.

Collaboration does not imply that all resulting work must become public or open source.

Different collaborations may involve different intellectual-property arrangements depending on the nature of the work, the contributions of the participants, commercial requirements, research objectives, confidentiality requirements, and applicable agreements.

Where collaboration progresses beyond exploratory discussion, matters such as:

- ownership,
- licensing,
- confidentiality,
- publication rights,
- commercialization rights,
- jointly developed intellectual property,
- independently developed intellectual property,
- data rights,
- and use of resulting artifacts

should be established explicitly between the participating parties where appropriate.

In particular, participation in a CaralisLabs sandbox, Deployment Unit, Domain Capability Registry, research activity, technical discussion, or community initiative does not by itself transfer ownership of intellectual property between participants.

Where jointly developed intellectual property arises, the applicable ownership and licensing arrangements should be established separately through explicit agreement.

---

## No Implicit Assignment

No ownership, assignment, transfer, exclusive license, partnership right, joint ownership interest, or other expansion of intellectual-property rights occurs merely through:

- access to this document,
- reading or discussing its contents,
- referencing the concepts,
- participating in public technical discussions,
- experimenting with related architectures,
- participating in a sandbox,
- using a Deployment Unit,
- publishing or registering a Domain Capability,
- independently implementing systems inspired by the public concepts,
- entering exploratory discussions with CaralisLabs,
- or collaborating on unrelated work.

Any transfer, assignment, exclusive licensing arrangement, joint ownership arrangement, or other special intellectual-property relationship must be explicit, documented, and mutually agreed upon by the relevant parties.

---

## Attribution

Where this Strategic Note is referenced in technical, academic, architectural, research, or industry discussion, attribution to CaralisLabs and this document is encouraged and, where required by the applicable license, must be provided.

Suggested reference:

> **CaralisLabs Strategic Note — What Exactly Is CaralisLabs Building? Execution Economy, Domain Capabilities, Deployment Units, and Portable Governed Execution. CaralisLabs, August 2026.**

The terminology and conceptual models discussed in this document are intended to contribute to a broader vocabulary around governed execution, Domain Capabilities, Deployment Units, and the Execution Economy.

Use of terminology alone should not be interpreted as endorsement by, affiliation with, partnership with, or participation in CaralisLabs.

---

## License

This document is released under the **Creative Commons Attribution 4.0 International (CC BY 4.0)** license.

Under that license, the published content of this Strategic Note may be shared, redistributed, adapted, and built upon, provided that appropriate attribution is given.

The license applies to the **published content of this document**.

It does not, merely through publication of this Strategic Note, license:

- CaralisLabs source code,
- proprietary runtime implementations,
- Deployment Unit implementation technologies,
- infrastructure automation,
- non-public specifications,
- internal protocols,
- confidential implementation details,
- proprietary Domain Capabilities,
- separately licensed software,
- trademarks,
- trade secrets,
- or other intellectual property not contained in this document.

Capabilities, software, specifications, and other artifacts referenced by this document may be subject to their own licenses and terms.

---

## Public Disclosure Boundary

This Strategic Note intentionally establishes a public architectural and strategic boundary.

It publicly describes a direction in which:

> **Domain Capabilities can become discoverable, governable, portable units of execution operating across compatible Deployment Units and, eventually, across federated execution environments.**

It also publicly describes the possibility that such capabilities, environments, and execution evidence may form the foundations of a broader **Execution Economy**.

It does **not** attempt to disclose the complete technical machinery required to realize that direction.

Questions concerning:

- capability representation,
- packaging,
- resolution,
- execution contracts,
- resource binding,
- compatibility negotiation,
- policy enforcement,
- trust,
- attestation,
- registry implementation,
- Deployment Unit internals,
- runtime coordination,
- federation,
- evidence representation,
- attribution,
- economic mechanisms,
- and implementation-specific security

remain outside the implementation scope of this public Strategic Note.

Those mechanisms may be addressed selectively through future public specifications, RFCs, interoperability contracts, standards work, proprietary implementations, internal research, open-source components, or other forms of publication where appropriate.

There is no requirement that all such mechanisms eventually be publicly disclosed.

The distinction is intentional:

> **The architectural direction is public.  
> The implementation strategy is selectively disclosed.**

---

## Evolution of the Research

The ideas described in this document represent the current state of an evolving research and development program.

Terminology, architectural boundaries, protocols, implementation approaches, ecosystem models, economic models, and operational structures may change as the work progresses.

Future RFCs, specifications, implementations, experiments, research publications, and collaborations may refine, replace, or extend portions of this Strategic Note.

The purpose of publishing this document is therefore not to freeze the architecture.

It is to make the **direction visible while the realization continues to evolve**.

---

# Opening the Laboratories

We're approaching an important transition.

> **The research is becoming architecture.**

> **The architecture is becoming infrastructure.**

> **The infrastructure is becoming reproducible Deployment Units.**

And soon, the first of those Deployment Units should become a place where others can begin building and experimenting with us.

We'll start with a **limited number of participants**.

The reason is practical: we want to learn from the first environment, improve the experience, understand how people use it, and continue developing the mechanisms around it.

As we learn and create additional sandbox Deployment Units, we'll gradually be able to open participation to more people.

We're interested in developers, researchers, architects, domain specialists, infrastructure specialists, technology providers, research institutions, companies, and other organizations interested in exploring this direction with us.

You don't need to arrive with a formal proposal.

If you're an individual interested in participating in the first sandbox group, tell us what interests you and what you might like to explore.

If you're part of an organization and see a potential connection between your work and ours, we'd like to hear that too.

Bring a problem.

Bring domain expertise.

Bring technology.

Bring infrastructure.

Bring a capability idea.

Bring a research question.

Or simply bring curiosity.

**A conversation is enough to start.**

We won't be able to onboard everyone into the first sandbox Deployment Unit.

But the whole point of making Deployment Units reproducible is that:

> **The first environment doesn't have to be the last.**

As more environments become available, the community can grow with them.

Organizational collaborations may also take entirely different forms.

They might involve dedicated Deployment Units, sovereign environments, research collaborations, capability development, technology integrations, infrastructure partnerships, joint initiatives, commercial relationships, or models we haven't considered yet.

We don't intend to prescribe the ecosystem before people begin participating in it.

We would rather provide the foundations and discover what emerges.

We're still early.

That's precisely why we believe this is an interesting time to begin these conversations.

We have an architectural direction.

We're building the execution environments.

We're preparing the capability ecosystem.

And soon, we want to see what happens when other people and organizations begin building with us.

> **We are preparing the environments for what comes next.**

Because when intelligence becomes abundant, we believe **execution becomes the value boundary**.

And CaralisLabs is researching, building, and beginning to open the architecture we believe that new boundary will require.

**If that direction resonates with you, we'd like to hear from you. Let's start with a conversation.**