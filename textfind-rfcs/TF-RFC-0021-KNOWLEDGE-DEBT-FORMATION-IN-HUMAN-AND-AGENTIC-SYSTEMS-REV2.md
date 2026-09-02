# TF-RFC-0021 — Knowledge Debt Formation in Human and Agentic Systems

**Status:** Draft  
**Category:** Foundational / Conceptual Architecture  
**Date:** 2026-09-02  
**Organization:** CaralisLabs  
**Author:** Nicolae Caralicea  

---

## Abstract

Modern engineering depends on abstraction. Engineers routinely operate systems whose internal implementations they do not know in detail, yet this does not necessarily represent a loss of knowledge. Mature black boxes can hide enormous implementation complexity while preserving the conceptual, causal, and predictive models required for humans to reason about their behavior.

This RFC introduces **Knowledge Debt** as a distinct concept: the accumulated deficit between the consequential knowledge embodied in a system and the human or institutional capacity to maintain a sufficiently accurate conceptual, causal, and predictive model of that system over time.

Knowledge Debt predates artificial intelligence. Organizations have always been capable of creating systems faster than they document, understand, standardize, or transfer knowledge about them. Autonomous and semi-autonomous AI agents, however, change the dynamics of Knowledge Debt formation. Agents can generate consequential decisions, implementation, abstractions, and interactions at rates that are no longer naturally coupled to human participation in their creation. Agent spawning can further scale this production horizontally while human assimilation and intuition formation remain bounded.

This RFC develops a conceptual mathematical model for Knowledge Debt before and after agentic systems. It distinguishes implementation opacity from epistemic opacity, treats abstraction as knowledge compression rather than knowledge elimination, introduces intuition and standardization as time-dependent forms of retained understanding, and proposes conditions under which agentic execution creates structural pressure toward Knowledge Debt accumulation.

The central proposition is:

> **Time transforms opacity either into intuition or into debt.**

---

## 1. Motivation

A common criticism of AI-assisted engineering is that humans may stop understanding the code being produced for them. This framing is incomplete.

Humans have been deliberately reducing their exposure to implementation details throughout the history of computing. High-level languages hide machine instructions. Operating systems hide hardware mechanics. Database systems hide storage structures. Network APIs hide protocol implementation. Virtualization and cloud platforms hide substantial infrastructure complexity.

This is not normally considered a failure of engineering. It is one of engineering's greatest achievements.

The important question is therefore not:

> How much of the implementation does the human know?

The more useful question is:

> Does the human retain enough conceptual, causal, and predictive understanding to know what to expect from the system, why those expectations are reasonable, and when observed behavior violates them?

This distinction becomes increasingly important as AI systems move from generating isolated artifacts to autonomously interpreting objectives, choosing architectures, creating abstractions, introducing dependencies, testing outcomes, responding to failures, and delegating work to additional agents.

The problem is not that AI allows humans to know less about implementation. Computing has been doing that successfully for decades.

The problem begins when machines create consequential complexity and decide which parts of the reasoning can disappear behind abstractions faster than humans and institutions can determine what they still need to understand.

---

## 2. Scope

This RFC is a conceptual model, not an empirically calibrated measurement standard.

It seeks to:

1. distinguish healthy black-box abstraction from Knowledge Debt;
2. describe how human intuition forms around systems over time;
3. explain the role of standards and collective knowledge in mature abstractions;
4. characterize Knowledge Debt formation before autonomous agents;
5. characterize the structural changes introduced by agentic systems;
6. provide mathematical expressions that make the proposed relationships explicit;
7. identify observable implications and possible future measurements;
8. provide a foundation for future engineering and governance mechanisms intended to control Knowledge Debt.

The equations in this RFC are conceptual. Their purpose is to make assumptions, relationships, and predictions explicit enough to be criticized, refined, and eventually tested.

---

## 3. Terminology

### 3.1 Implementation Knowledge

**Implementation Knowledge**, denoted `K_I(t)`, is detailed knowledge of how a system internally performs its work: algorithms, source code, internal state transitions, protocol mechanics, data structures, runtime behavior, and similar implementation details.

A low value of `K_I(t)` does not by itself imply Knowledge Debt.

### 3.2 Conceptual Knowledge

**Conceptual Knowledge**, denoted `K_C(t)`, is understanding of what a system is, the responsibilities of its components, its important boundaries, and the abstractions through which it should be reasoned about.

### 3.3 Predictive Knowledge

**Predictive Knowledge**, denoted `K_P(t)`, is the ability to form useful expectations about system behavior under relevant conditions.

A person need not know exactly which function executes a behavior in order to know that the behavior is inconsistent with the architecture.

### 3.4 Causal Model

A **Human Causal Model**, denoted `C_H(t)`, is the human's usable model of consequential relationships within the system: what causes what, which boundaries matter, where failures can propagate, and which assumptions connect components or behaviors.

### 3.5 Intuition

**Human Intuition**, denoted `I_H(t)`, is accumulated predictive and causal understanding formed through meaningful exposure to decisions, outcomes, failures, explanations, corrections, and repeated interaction with a system.

Intuition is treated in this RFC as compressed experience rather than as unexplained instinct.

### 3.6 Collective Knowledge and Standardization

**Collective Knowledge**, denoted `S_K(t)`, is understanding available outside an individual through standards, shared terminology, education, documentation, known patterns, known failure modes, community practice, and accumulated institutional or industry experience.

### 3.7 Consequential Knowledge

**Consequential Knowledge Content**, denoted `C(t)`, is the set or quantity of system knowledge whose absence can materially impair the ability to reason about, operate, modify, govern, diagnose, or take responsibility for the system.

It explicitly excludes implementation details that can safely remain hidden behind a sufficiently meaningful abstraction.

### 3.8 Implementation Opacity

**Implementation Opacity** is the degree to which internal mechanics are hidden from a user or operator.

Implementation opacity is expected and often desirable.

### 3.9 Epistemic Opacity

**Epistemic Opacity**, denoted `O_E(t)`, is the degree to which consequential reasoning, assumptions, decisions, causal relationships, or behavioral expectations are unavailable to or unassimilated by responsible humans.

Implementation opacity and epistemic opacity MUST NOT be treated as equivalent concepts.

### 3.10 Retained Meaning

**Retained Meaning**, denoted `M(t)`, is the decision-relevant conceptual, causal, and predictive information preserved across an abstraction boundary.

### 3.11 Knowledge Debt

**Knowledge Debt**, denoted `D_K(t)`, is the accumulated deficit between consequential knowledge embodied in a system and the effective understanding available to the humans or institutions responsible for that system.

---

## 4. The Black Box Is Not the Problem

Consider a system transformation:

```text
x(t) -> F_t -> y(t)
```

where `F_t` may contain substantial hidden implementation complexity.

The human does not need an exact internal representation of `F_t`. Instead, the human maintains an approximate model:

```text
F̂_H,t
```

Healthy abstraction does not require:

```text
F̂_H,t = F_t
```

It requires the human model to be sufficiently accurate over the consequential operational domain:

```text
F̂_H,t(x) ≈ F_t(x)
```

for the behaviors that matter.

Therefore a healthy black box may exhibit:

```text
K_I(t) << 1
K_C(t) ≈ 1
K_P(t) ≈ 1
```

The implementation can be almost completely opaque while conceptual and predictive understanding remain strong.

This RFC therefore rejects the proposition:

```text
Implementation Opacity => Knowledge Debt
```

Instead:

```text
Implementation Opacity != Epistemic Opacity
```

and:

```text
Implementation Opacity != Knowledge Debt
```

---

## 5. Abstraction as Knowledge Compression

A useful abstraction does not merely remove information. It compresses implementation knowledge while preserving decision-relevant meaning.

Let `K_I` represent implementation knowledge beneath an abstraction and `M` represent the meaning retained above the abstraction boundary.

A successful abstraction performs conceptually:

```text
K_I --abstraction--> M
```

where:

```text
|M| << |K_I|
```

while the decision-relevant value remains approximately preserved:

```text
V(M) ≈ V(C_required)
```

where `V` represents explanatory and predictive value for the decisions the user is expected to make.

Define the **Abstraction Retention Ratio**:

```text
                 V(M_t)
ρ_A(t) = ------------------------
          V(C_required,t)
```

A mature abstraction seeks:

```text
ρ_A(t) -> 1
```

while exposed implementation complexity may approach zero.

Knowledge Debt therefore cannot be inferred from the amount of hidden code. A highly opaque implementation can remain epistemically healthy when `ρ_A` is high.

---

## 6. Historical Example: Network Programming

The evolution of network programming illustrates the distinction.

Early application programmers working with low-level socket APIs were exposed to substantial networking machinery. Creating networked clients and servers required dealing directly with addresses, ports, connection state, buffers, blocking behavior, threading, errors, and protocol mechanics.

Higher-level APIs progressively reduced this burden. Java and later frameworks simplified common networking operations. Modern languages and libraries can reduce an HTTP request to only a few lines of application code.

The reduction in visible code did not imply a corresponding destruction of useful knowledge.

What survived was a compressed causal model:

```text
client
  -> request
  -> endpoint/network
  -> server
  -> response
```

Alongside it survived important expectations:

- endpoints may be unavailable;
- requests may time out;
- communication can fail;
- authentication may be required;
- DNS, routing, TLS, proxies, or application behavior may affect outcomes;
- a request and its response are not guaranteed to succeed as a single indivisible event.

Over time, standards, textbooks, documentation, libraries, operational practice, and collective experience strengthened this conceptual model even while application-level implementation exposure decreased.

Thus the historical trajectory could be:

```text
visible implementation knowledge ↓
collective conceptual knowledge  ↑
abstraction quality              ↑
```

The few lines of modern application code sit on top of decades of accumulated knowledge compressed into mature abstractions.

The code was not what needed to survive.

The mental model was.

---

## 7. Intuition Formation

Intuition develops through time and meaningful participation.

Let:

- `E_H(t)` = meaningful human exposure;
- `F_H(t)` = quality of feedback from real outcomes;
- `R_H*(t)` = degree to which observed outcomes are connected to their reasons;
- `α` = assimilation effectiveness.

Then a conceptual intuition formation model is:

```text
 dI_H
------ = α E_H(t) F_H(t) R_H*(t)
  dt
```

and accumulated intuition is:

```text
           T
I_H(T) = ∫ α E_H(t) F_H(t) R_H*(t) dt
           0
```

The sequence:

```text
decision
  -> implementation
  -> result
  -> failure
  -> explanation
  -> correction
```

creates substantially more intuition than repeatedly observing:

```text
request -> result
```

This distinction is central to AI-assisted engineering.

A human may delegate large quantities of implementation while remaining inside the decision, failure, explanation, and correction loops. In that case implementation knowledge may decline while intuition and conceptual understanding continue to increase.

---

## 8. Effective Human Understanding

Define effective human understanding as:

```text
H(t) = w_c K_C(t)
     + w_p K_P(t)
     + w_i I_H(t)
     + w_h C_H(t)
     + w_s S_K(t)
```

where the weights reflect the importance of each dimension for a particular system or responsibility.

This formulation intentionally does not require exhaustive implementation knowledge.

A system can therefore satisfy:

```text
K_I(t) low
H(t)   high
```

without significant Knowledge Debt.

---

## 9. The Surprise Test

A practical indicator of effective understanding is whether a responsible human can recognize behavior that violates the system's expected model.

Let:

```text
A_H(x,t) = |F_t(x) - F̂_H,t(x)|
```

represent the difference between actual behavior and human-predicted behavior.

The critical capability is not exact prediction. It is the ability to recognize when `A_H` is materially large.

A healthy black box permits a responsible human to say:

> This behavior is surprising. It contradicts what I understand about the system.

A system with severe Knowledge Debt may instead produce:

> I do not know whether this behavior is surprising.

The latter condition indicates the absence of a sufficiently useful predictive model.

---

## 10. Knowledge Debt Before Agents

Knowledge Debt existed long before AI agents.

Examples include undocumented systems, lost architectural rationale, employee turnover, acquisitions of poorly understood technology, rushed implementations, abandoned standards, and systems whose complexity outgrew their maintainers' understanding.

The general formation condition was already:

```text
R_C(t) > R_H(t)
```

where:

```text
R_C(t) = dC/dt
```

is the rate of consequential system evolution and:

```text
R_H(t) = dH/dt
```

is the rate of effective understanding formation.

Historically, however, consequential complexity creation and human understanding were often partially coupled.

Humans designing a subsystem were exposed to the design decisions.

Humans debugging it encountered its failure modes.

Humans creating abstractions participated in the reasoning that produced them.

Thus, as a structural tendency rather than a universal law:

```text
corr(R_C, R_H) > 0
```

Creation required human cognitive participation, and that participation generated at least some understanding as a side effect.

---

## 11. The Classical Abstraction Cycle

Many mature abstractions historically developed through a process resembling:

```text
Implementation
    -> Experience
    -> Failure
    -> Understanding
    -> Patterns
    -> Standardization
    -> Compression
    -> Abstraction
```

The sequence is not universal, but it captures an important temporal property: abstraction often matured after substantial human and institutional experience existed around the underlying system.

Collective understanding could therefore grow with time:

```text
 dS_K
------ = f(E_collective, feedback, standardization, education)
  dt
```

A stable abstraction gave humans and institutions time to learn what could safely disappear behind the boundary and what meaning needed to remain visible.

---

## 12. The Agentic Transition

An autonomous agent can perform more than a predefined transformation.

It may:

```text
interpret objective
  -> decompose problem
  -> select architecture
  -> introduce dependencies
  -> implement
  -> test
  -> observe failure
  -> revise architecture
  -> create new abstraction
```

Therefore the transformation itself can evolve:

```text
F_(t+1) = G(F_t, x_t, A_t)
```

where `A_t` represents agent-generated decisions.

A subsequent agent can operate upon the resulting system:

```text
F_(t+2) = G_2(F_(t+1), A_(t+1))
```

The black box is no longer necessarily only performing a hidden transformation.

It can participate in deciding what the transformation should be.

This creates the possibility that the intellectual lineage of a system becomes hidden behind the abstraction boundary.

---

## 13. The Agentic Inversion

The classical abstraction sequence can be summarized as:

```text
Experience
  -> Understanding
  -> Compression
  -> Abstraction
```

Agentic systems can produce a different sequence:

```text
Machine Decision
  -> Machine Implementation
  -> Machine Compression
  -> Abstraction
  -> Human Understanding ?
```

The question mark is the central concern of this RFC.

Agent-generated abstraction can precede human understanding.

Define **Epistemic Lag**:

```text
L_E = t_human-understanding - t_system-creation
```

A positive epistemic lag is not inherently harmful. Humans routinely learn systems after they are created.

Debt pressure appears when consequential system evolution continues before earlier epistemic lag has been closed.

---

## 14. Agent Spawning and the Assimilation Asymmetry

Let `N(t)` represent the number of concurrently active agents.

Let agent `i` generate consequential change at rate `r_i(t)`, with consequentiality `q_i(t)` and epistemic opacity `o_i(t)`.

Define agent-generated consequential change as:

```text
               N(t)
R_AC(t) =       Σ r_i(t) q_i(t) o_i(t) + Λ(t)
                i=1
```

where `Λ(t)` represents additional epistemic burden created by interactions among independently generated decisions.

Agent spawning is explicitly intended to increase parallel production. Therefore, under ordinary assumptions:

```text
∂R_AC / ∂N > 0
```

Human assimilation does not automatically scale with agent count.

For a given human or bounded organization:

```text
R_H(t) <= H_max
```

and potentially:

```text
∂R_H / ∂N ≈ 0
```

Under excessive coordination or review load, it is even possible that:

```text
∂R_H / ∂N < 0
```

because human attention shifts from participating in reasoning to processing and approving outputs.

This creates an **Assimilation Asymmetry**:

```text
machine consequential decision throughput scales horizontally
human intuition formation remains bounded
```

Agent spawning therefore creates structural pressure toward Knowledge Debt even though it does not logically guarantee it.

---

## 15. Decision Interaction Burden

The epistemic burden of multiple agents is not necessarily additive.

If agents independently introduce decisions `d_i`, the required understanding may include both the decisions and their interactions:

```text
             N                N
Burden ≈     Σ d_i  +         Σ I(d_i,d_j)
             i                i,j
```

where `I(d_i,d_j)` represents consequential interaction between decisions.

In highly interconnected systems the potential interaction space may grow substantially faster than the number of agents, although this RFC does not assert a universal quadratic growth law.

The relevant proposition is narrower:

> Agent parallelism scales production, agent interaction can increase the relationships requiring understanding, and human assimilation does not automatically scale with either.

---

## 16. Abstraction Mutation and Intuition Formation

Let:

```text
R_M(t)
```

represent the rate of consequential abstraction mutation, and:

```text
R_I(t)
```

represent the rate of human and collective intuition formation.

A stable abstraction can permit:

```text
R_I(t) > R_M(t)
```

for long enough that understanding catches up and collective knowledge accumulates.

A rapidly agent-generated system may instead sustain:

```text
R_M(t) > R_I(t)
```

so that before sufficient intuition forms around abstraction `A_t`:

```text
A_t -> A_(t+1) -> A_(t+2)
```

The abstraction may therefore fail to remain stable long enough for human or institutional intuition to mature.

This leads to a central proposition:

> **Knowledge Debt can form not because an abstraction is intrinsically difficult to understand, but because it changes faster than reliable understanding can form around it.**

---

## 17. Knowledge Debt as Accumulated Divergence

The simplest static formulation is:

```text
D_K(t) = [ C(t) - H(t) ]+
```

where:

```text
[x]+ = max(0,x)
```

However, Knowledge Debt is fundamentally temporal.

A basic formation model is:

```text
 dD_K
------ = [ R_C(t) - R_H(t) ]+
  dt
```

This expresses Knowledge Debt as accumulated divergence between consequential system evolution and understanding formation.

The time dimension is essential because a temporary understanding deficit may be harmless if humans subsequently catch up, whereas a persistent deficit compounds.

---

## 18. Refined Knowledge Debt Formation Model

The model can be refined to account for abstraction quality, epistemic opacity, abstraction mutation, human assimilation, and standardization.

Define:

- `R_Q(t)` — rate of consequential knowledge entering or changing in the system;
- `O_E(t)` — epistemic opacity of that consequential knowledge;
- `ρ_A(t)` — abstraction retention ratio;
- `R_M(t)` — consequential abstraction mutation rate;
- `R_H(t)` — human assimilation and intuition-formation rate;
- `R_S(t)` — rate at which standardization and collective knowledge make the system more comprehensible.

Then define the instantaneous Knowledge Debt formation pressure:

```text
                  [
 dD_K             [ R_Q(t) O_E(t) (1 - ρ_A(t))
------ =          [ + R_M(t)
  dt              [ - R_H(t)
                  [ - R_S(t)
                  ]+
```

or compactly:

```text
Ḋ_K(t) = [R_Q(t)O_E(t)(1-ρ_A(t)) + R_M(t) - R_H(t) - R_S(t)]+
```

Accumulated Knowledge Debt over `[0,T]` is:

```text
                     T
D_K(T) = D_K(0) +   ∫ Ḋ_K(t) dt
                     0
```

This equation is a conceptual model rather than a validated physical law.

Its purpose is to capture several important relationships simultaneously.

---

## 19. Model Interpretation

### 19.1 Mature Black Box

A mature black box may have very high implementation opacity while preserving meaning:

```text
implementation opacity -> high
ρ_A                   -> high
R_M                   -> low
R_S                   -> positive
R_H                   -> adequate
```

Therefore:

```text
Ḋ_K ≈ 0
```

The black box is not Knowledge Debt.

### 19.2 Traditional Knowledge Debt

A legacy system may have disappearing human knowledge, weak documentation, and poorly preserved rationale:

```text
ρ_A ↓
R_H ↓
R_S ↓
```

while consequential complexity remains.

Therefore:

```text
Ḋ_K > 0
```

This demonstrates that Knowledge Debt predates AI.

### 19.3 Continuous Human–AI Collaboration

AI may generate implementation at very high rates while humans remain involved in consequential decisions, failures, architectural reasoning, and corrections.

Then:

```text
implementation generation >> human implementation production
```

while:

```text
R_H ↑
I_H ↑
C_H ↑
ρ_A high
```

Knowledge Debt can remain low even when much of the implementation behaves as a black box to the human.

### 19.4 Aggressive Autonomous Agent Spawning

With many autonomous agents:

```text
R_Q ↑
R_M ↑
Λ   ↑
```

while human exposure to intermediate reasoning may decrease:

```text
E_H ↓
R_H ↓ or bounded
```

and newly created abstractions may lack mature collective knowledge:

```text
R_S ≈ 0 initially
```

If this state persists:

```text
Ḋ_K > 0
```

and accumulated Knowledge Debt increases with time.

---

## 20. The Knowledge Assimilation Threshold

Assume, for illustration, `N` similar agents each generate consequential change at average rate `r_a`, with average consequentiality `q` and epistemic opacity `o`.

Then:

```text
R_AC(N) ≈ N r_a q o + Λ(N)
```

Let human and institutional assimilation capacity be bounded by:

```text
R_H + R_S <= A_max
```

There exists a conceptual threshold `N*` such that when:

```text
N r_a q o + Λ(N) > A_max
```

Knowledge Debt formation pressure becomes positive unless compensating mechanisms reduce consequentiality, opacity, mutation, or interaction burden.

This is the **Knowledge Assimilation Threshold**.

The model does not claim that every additional agent necessarily creates debt. It predicts that sufficiently scalable consequential machine decision throughput eventually exceeds bounded assimilation capacity unless the surrounding epistemic architecture scales as well.

---

## 21. Pre-Agent and Agentic Formation Compared

The principal difference is not that humans understood all pre-agent systems and fail to understand agent-generated systems.

They did not.

The difference is structural.

Before agents:

```text
human creation effort
      ↕ partial coupling
human exposure
      ↓
intuition formation
```

With autonomous agents:

```text
machine creation effort --------> scales with agents

human exposure -----------------> may remain flat or fall

human intuition formation ------> bounded
```

Thus autonomous agents weaken the natural coupling between the creation of consequential complexity and the formation of human understanding.

This is the principal mechanism by which agentic systems change Knowledge Debt formation.

---

## 22. Core Propositions

This RFC proposes the following propositions.

**P1 — Implementation Opacity Proposition**  
Low implementation knowledge does not by itself constitute Knowledge Debt.

**P2 — Retained Meaning Proposition**  
A healthy abstraction preserves sufficient decision-relevant conceptual, causal, and predictive meaning despite hiding implementation complexity.

**P3 — Intuition Proposition**  
Human intuition develops through repeated exposure to consequential decisions, outcomes, failures, explanations, and corrections over time.

**P4 — Standardization Proposition**  
Stable abstractions can become more epistemically usable over time as collective knowledge, standards, education, terminology, and known failure modes accumulate.

**P5 — Historical Coupling Proposition**  
Before autonomous agents, consequential system creation generally required substantial human cognitive participation, producing a partial coupling between complexity creation and understanding formation.

**P6 — Agentic Decoupling Proposition**  
Autonomous agents can increase consequential system creation without proportionally increasing human participation in the reasoning that creates it.

**P7 — Agent Spawning Proposition**  
Agent spawning creates structural pressure toward Knowledge Debt because consequential machine decision throughput can scale horizontally while human intuition formation remains bounded.

**P8 — Mutation Proposition**  
Knowledge Debt pressure increases when consequential abstractions mutate faster than human and collective intuition can form around them.

**P9 — Temporal Accumulation Proposition**  
Knowledge Debt is not merely an instantaneous knowledge deficit; persistent divergence between consequential system evolution and understanding formation accumulates over time.

**P10 — Surprise Proposition**  
A useful operational signal of low Knowledge Debt is the ability of responsible humans to recognize when observed behavior violates their conceptual and predictive model, even when they cannot immediately identify the implementation cause.

---

## 23. Non-Claims

This RFC does **not** claim that:

- all AI-generated code creates Knowledge Debt;
- autonomous agents necessarily create Knowledge Debt in every deployment;
- humans must inspect or understand every line of generated code;
- implementation opacity is inherently undesirable;
- mature black boxes should be dismantled in the name of transparency;
- human cognition must remain involved in every machine action;
- the mathematical expressions in this RFC are already empirically calibrated;
- agentic development should be rejected.

The stronger and more defensible claim is:

> **Agent spawning structurally increases Knowledge Debt formation pressure when it scales consequential decisions, abstraction mutation, and decision interaction faster than human and institutional understanding can form.**

---

## 24. Design Implications

If the model is directionally correct, systems using autonomous agents SHOULD NOT treat output correctness alone as sufficient evidence of epistemic health.

Agentic systems SHOULD seek to preserve consequential reasoning in forms that can contribute to human understanding rather than merely recording exhaustive machine traces.

Architectures SHOULD distinguish between implementation details that can safely disappear behind abstractions and consequential decisions whose meaning must remain recoverable.

Systems with high agent concurrency SHOULD consider mechanisms for detecting when machine decision throughput is exceeding human or institutional assimilation capacity.

Long-lived abstractions SHOULD be preferred where stability permits intuition, standards, and collective knowledge to form, unless the benefits of mutation justify the associated epistemic cost.

Human participation SHOULD be concentrated around consequential boundaries rather than indiscriminately required for all implementation activity.

The objective is not maximum human involvement.

The objective is preservation of sufficient human and institutional understanding.

---

## 25. Possible Future Measurements

Future work may attempt to operationalize the model using proxies such as:

- frequency with which responsible engineers can correctly predict system behavior;
- ability to identify surprising behavior before consulting an agent;
- time required to reconstruct architectural rationale after a failure;
- proportion of consequential changes whose rationale is understood by accountable humans;
- abstraction mutation rate;
- human participation rate in consequential decision loops;
- number and interaction density of independently agent-generated decisions;
- time between system creation and adequate human understanding;
- stability and maturity of conceptual interfaces;
- availability of shared standards and known failure models;
- recovery time when the AI systems that originally created or maintained a component are unavailable.

A future RFC may define an empirical **Knowledge Debt Index** from measurable proxies.

---

## 26. Organizational Scale

Knowledge Debt can exist at several scales.

At the individual scale, a person may own systems whose consequential behavior exceeds their mental model.

At the team or corporate scale, knowledge may be distributed across people and documentation sufficiently to compensate for individual gaps. Conversely, rapid agent-generated evolution can create corporate Knowledge Debt even when every individual artifact is well documented.

At the industry scale, systems can become dependent upon abstractions generated and modified across organizations faster than common standards and collective intuition form around them.

At societal scale, increasingly machine-mediated chains of reasoning in software, science, medicine, finance, law, infrastructure, government, and other domains could create forms of epistemic dependency in which society possesses highly capable systems without retaining proportionate independent human capacity to reconstruct the reasoning embodied within them.

These larger-scale forms remain hypotheses requiring further study.

---

## 27. Relationship to Knowledge Compounding Theory (TF-RFC-0013)

This RFC is related to **TF-RFC-0013 — Knowledge Compounding Theory (KCT)**, but addresses a different side of the knowledge lifecycle.

KCT asks which forms of knowledge persist, transfer, connect, and compound across experiences and domains. It treats Experience Extraction as a mechanism through which repeated technologies, projects, successes, failures, and other experiences can yield Durable Concepts whose value survives the implementation context in which they were learned.

Knowledge Debt asks a complementary question:

> What happens when consequential system knowledge is created or changed faster than the responsible humans and institutions can extract, assimilate, preserve, and connect the concepts required to reason about it?

The relationship can be expressed conceptually as:

```text
Experience
   -> Experience Extraction
   -> Durable Concepts
   -> Knowledge Compounding
```

while insufficient extraction or assimilation can produce:

```text
Consequential Change
   -> Unassimilated Reasoning
   -> Epistemic Lag
   -> Knowledge Debt
```

KCT therefore describes a positive knowledge-formation process, while this RFC describes a deficit that can emerge when that process does not keep pace with consequential system evolution.

The relationship is particularly important to the time-dependent model. Experience does not automatically become intuition. For experience to contribute to `I_H(t)` or collective knowledge `S_K(t)`, consequential observations must be connected to reasons and compressed into reusable conceptual structures. In KCT terminology, Experience Extraction contributes to the formation of Durable Concepts. In this RFC, those same processes increase effective understanding `H(t)` and can reduce Knowledge Debt formation pressure.

This suggests a broader relationship:

```text
                     Experience Extraction
                              |
                              v
Consequential Change -> Human Understanding -> Durable Concepts
        |                     |                    |
        |                     v                    v
        |                Intuition           Compounding
        |                     |
        +---- if assimilation lags ----------+
                              |
                              v
                        Knowledge Debt
```

The two theories are therefore not opposites. Knowledge Compounding and Knowledge Debt can occur simultaneously in different parts of the same system or organization. A team may accumulate highly transferable architectural intuition while also acquiring debt around rapidly changing implementation or agent-generated decisions.

A future research direction MAY investigate whether the Knowledge Compounding Index or related KCT concepts can inform measurements of Knowledge Debt repayment, resilience, or epistemic maturity.

---

## 28. Knowledge Debt and Execution Systems

Execution systems provide a particularly useful environment for studying Knowledge Debt because consequential changes can become observable through execution rather than being inferred only from final artifacts.

A governable execution architecture can potentially preserve:

```text
intent
 -> requester / actor
 -> authority
 -> policy / admissibility
 -> resolution
 -> execution plan
 -> capability selection
 -> target / resource selection
 -> execution
 -> evidence
 -> result
```

This creates an opportunity for **execution observability to contribute to epistemic observability**.

Execution evidence cannot directly prove that a human understands a system. Human understanding remains partly cognitive and cannot be inferred safely from telemetry alone. Execution systems may, however, expose measurable proxies for the formation conditions described by this RFC, including:

- rate of autonomous consequential change;
- number and concurrency of agent-mediated executions;
- agent-to-agent handoffs;
- frequency of consequential abstraction or deployment changes;
- human participation at consequential decision boundaries;
- elapsed time between machine-created change and human review or assimilation signals;
- decision provenance and dependency lineage;
- stability of capability and execution contracts;
- frequency with which machine-generated artifacts become inputs to subsequent autonomous executions.

These signals could contribute to estimates of `R_Q(t)`, `R_M(t)`, `O_E(t)`, epistemic lag `L_E(t)`, and related variables without pretending to directly measure cognition.

Governed execution systems may also provide mechanisms for reducing Knowledge Debt formation pressure. They can preserve decision-relevant provenance, constrain autonomous execution behind stable capability contracts, require human participation at selected consequential boundaries, and retain evidence that allows later reconstruction of why an execution occurred and what assumptions or authority shaped it.

This creates a potential research progression:

```text
Execution Observability
        ->
Decision Provenance
        ->
Knowledge Debt Formation Indicators
        ->
Epistemic Risk Assessment
        ->
Possible Knowledge Debt Controls
```

This RFC does not claim that PER, Kubepath, TextFind, or any current CaralisLabs system presently measures Knowledge Debt. It establishes a conceptual research direction in which execution infrastructure MAY provide evidence and controls useful to future Knowledge Debt measurement.

---

## 29. Research Questions
---

## 28. Research Questions

The model raises several questions suitable for future research:

1. Can consequential knowledge content be measured independently from implementation complexity?
2. Can predictive understanding be measured through controlled surprise or prediction tests?
3. At what agent concurrency does assimilation capacity become a meaningful bottleneck?
4. How does decision interaction density affect Knowledge Debt formation?
5. Which forms of machine-generated explanation actually increase human intuition rather than merely increasing available information?
6. How quickly does intuition decay when humans cease participating in system evolution?
7. Can standards and stable capability contracts allow highly autonomous systems to remain low-debt?
8. Can AI itself help humans repay Knowledge Debt without creating recursive dependency on the same AI?
9. What forms of decision provenance are sufficient for reconstructing understanding after the original agents are unavailable?
10. How should organizations decide which knowledge can safely be compressed and which consequential knowledge must remain humanly assimilated?

---

## 30. Falsifiability and Limitations

A useful theory must permit evidence against it.

The agentic Knowledge Debt hypothesis would be weakened if highly autonomous, rapidly mutating, multi-agent systems were repeatedly shown to preserve or improve responsible humans' predictive and causal understanding without requiring proportional increases in human participation, standardization, or other compensating mechanisms.

It would also be weakened if human assimilation capacity were shown to scale approximately with agent-generated consequential complexity through machine-assisted explanation alone.

Conversely, evidence supporting the theory would include increasing inability of responsible humans to predict system behavior, reconstruct consequential rationale, recognize abnormal behavior, or safely modify systems as agent concurrency and autonomous decision throughput increase.

The present equations should therefore be interpreted as a framework for generating measurable hypotheses, not as established quantitative laws.

---

## 31. Central Thesis

The history of computing is not simply a history of humans knowing progressively less.

It is, in significant part, a history of discovering **what humans no longer needed to know while preserving what they still needed to understand**.

Successful abstractions hid implementation details while retaining conceptual and predictive meaning. Time allowed experience to accumulate. Failures produced intuition. Standards stabilized expectations. Education transferred collective understanding. Increasingly complex machinery could therefore disappear behind increasingly simple interfaces without necessarily creating equivalent Knowledge Debt.

Agentic systems alter this relationship because they can create complexity, make consequential decisions, discover abstractions, compress those abstractions, and modify them again before equivalent human intuition has had time to form.

The fundamental risk is therefore not machine-generated code.

It is a sustained inequality:

```text
rate of consequential machine-created change
    >
rate of human + institutional understanding formation
```

When that inequality persists over time:

```text
D_K(T) ↑
```

Knowledge Debt accumulates.

The challenge of agentic engineering is therefore not to preserve human knowledge of every implementation detail.

It is to preserve enough human and institutional conceptual, causal, and predictive understanding that the people responsible for a system continue to know what to expect, recognize when reality violates those expectations, and reconstruct the reasons that matter when they need to go deeper.

> **Time transforms opacity either into intuition or into debt.**

---

## 32. Future Work

Potential follow-on documents include:

- **Knowledge Debt Index and Measurement Framework**
- **Knowledge Debt Controls for Agentic Software Engineering**
- **Decision Provenance as an Epistemic Control**
- **Knowledge Assimilation Thresholds in Multi-Agent Systems**
- **Human–AI Epistemic Loops and Collaborative System Development**
- **Knowledge Debt in Governed Execution Systems**
- **Corporate, Industry, and Societal Knowledge Debt**

---

## 33. References

- **TF-RFC-0013 — Knowledge Compounding Theory (KCT), REV2.** CaralisLabs, 2026. Establishes Experience Extraction, Durable Concepts, Knowledge Lifecycle and Portfolio models, Knowledge Network Effects, the Knowledge Compounding Index, Domain Transferability, and the AI Amplification Hypothesis.
- **TF-RFC-0021 — Knowledge Debt Formation in Human and Agentic Systems.** This document.

The mathematical model and Knowledge Debt terminology in this RFC are proposed by this document and should not be interpreted as established scientific measures without empirical validation.

For conventional use of normative requirement terminology in RFC-style specifications, see IETF BCP 14, RFC 2119 and RFC 8174.

---

## 34. Claims Scope

This document establishes public disclosure, conceptual lineage, defensive disclosure, and prior art for the Knowledge Debt research framework described herein, including, without limitation:

- Knowledge Debt as an accumulated, time-dependent deficit between consequential system knowledge and effective human or institutional understanding;
- the distinction between Implementation Opacity and Epistemic Opacity;
- Retained Meaning and the Abstraction Retention Ratio;
- the treatment of abstraction as knowledge compression rather than knowledge elimination;
- the Human Causal Model, Predictive Knowledge, and Human Intuition as components of effective understanding;
- the time-dependent Intuition Formation model;
- the Surprise Test as an operational indicator of predictive understanding;
- the distinction between pre-agent Knowledge Debt formation and agentic Knowledge Debt formation;
- the Classical Abstraction Cycle and Agentic Inversion;
- Epistemic Lag;
- Assimilation Asymmetry;
- Decision Interaction Burden;
- consequential Abstraction Mutation versus Intuition Formation;
- the Knowledge Debt Formation Model and accumulated-divergence formulation;
- the Knowledge Assimilation Threshold;
- the propositions concerning agent spawning and structural Knowledge Debt formation pressure;
- the relationship between Knowledge Compounding Theory and Knowledge Debt formation;
- the use of execution observability, decision provenance, execution evidence, and related execution-system signals as potential proxies for Knowledge Debt formation;
- Knowledge Debt formation and analysis at individual, organizational, industry, and societal scales; and
- related epistemic-risk, measurement, control, repayment, and governance approaches derived from these concepts.

The mathematical expressions in this RFC are conceptual research models. Inclusion in the Claims Scope establishes the disclosed conceptual relationships and terminology; it does not represent a claim that the expressions are empirically calibrated scientific laws.

---

## 35. Intellectual Property and Licensing

This RFC constitutes a public disclosure and forms part of the CaralisLabs research and RFC portfolio.

The concepts, terminology, mathematical and conceptual models, Knowledge Debt framework, Implementation Opacity and Epistemic Opacity distinction, Retained Meaning, Abstraction Retention Ratio, Human Causal Model, Intuition Formation model, Surprise Test, Classical Abstraction Cycle, Agentic Inversion, Epistemic Lag, Assimilation Asymmetry, Decision Interaction Burden, Abstraction Mutation model, Knowledge Debt Formation Model, Knowledge Assimilation Threshold, agent-spawning propositions, Knowledge Debt formation indicators, execution-observability and decision-provenance approaches, and related epistemic-risk and governance approaches described herein are subject to the intellectual-property and licensing terms defined in the RFC portfolio's `LEGAL.md`.

These concepts constitute pre-existing intellectual work of the author and are published to establish authorship, public disclosure, conceptual lineage, defensive disclosure, and prior art.

Publication of this RFC does not transfer ownership of the disclosed work and does not grant any additional license, assignment of intellectual property, patent rights, trademark rights, or commercial implementation rights except as expressly stated in `LEGAL.md` or in a separate written agreement.

This RFC defines conceptual research frameworks rather than specific implementations. Future software systems, execution systems, observability mechanisms, analytical frameworks, Knowledge Debt measurement systems, Knowledge Debt indices, agentic controls, governance mechanisms, commercial products, academic implementations, or other systems derived from or informed by this research may be separately licensed, proprietary, open source, commercial, academic, or otherwise independently governed.

Earlier revisions of this RFC may have been published under different terms. Rights validly granted under any earlier terms are not purported to be revoked by this revision. See `LEGAL.md` for the portfolio licensing history and current policy.

---

## 36. Summary

A black box hides mechanics.

A good abstraction compresses knowledge while preserving meaning.

Intuition forms when humans repeatedly connect decisions to outcomes and outcomes back to reasons.

Standards allow that intuition to become collective and transferable.

Knowledge Debt existed before AI whenever consequential system complexity outpaced human and institutional understanding.

Autonomous agents introduce a new structural condition: consequential decision production can scale independently of human understanding formation.

Agent spawning amplifies this asymmetry through concurrency and interaction.

The resulting risk is not that humans stop knowing the code.

The risk is that humans stop possessing a sufficiently accurate mental model of the systems for which they remain responsible.

**Time transforms opacity either into intuition or into debt.**
