# TF-RFC-0002: Execution Provenance Graph (EPG) (Publication-Grade)

- **Status**: Draft
- **Author**: Nicolae Dumitru Caralicea
- **Created**: 2026-04-26
- **Updated**: 2026-04-26
- **Related RFCs**: TF-RFC-0001

---

## Abstract

This document defines the **Execution Provenance Graph (EPG)**, a deterministic and verifiable representation of execution flows.

EPG eliminates the need for causal reconstruction by encoding causality directly in execution.

---

## 1. Problem Statement

Existing systems reconstruct execution using logs.

This leads to:
- ambiguity
- incomplete causality
- non-deterministic explanations

---

## 2. Core Principle

> Causality MUST be defined at execution time, not inferred afterward.

---

## 3. Graph Model

### Schema

```json
{
  "nodes": [{"step_id": "string"}],
  "edges": [{"from": "string", "to": "string"}],
  "receipts": ["hash"],
  "integrity": {"verifiable": true}
}
```

---

## 4. Invariants

The system MUST guarantee:

1. **Deterministic structure**
2. **Complete coverage**
3. **Receipt linkage**
4. **Verifiable integrity**

---

## 5. Critical Path

The system MUST identify steps that directly influence outputs.

---

## 6. Security Model

- Graph integrity tied to receipt chain
- Optional Merkle root validation

---

## 7. Adversarial Considerations

The system MUST prevent:

- hidden execution steps
- altered data flows
- unauthorized branching

---

## 8. Comparison

| Feature | Log Systems | EPG |
|--------|------------|-----|
| Causality | Inferred | Explicit |
| Integrity | Weak | Strong |
| Auditability | Partial | Complete |

---

## 9. Conclusion

EPG transforms execution into a deterministic, verifiable structure.

---

## Key Statement

> Execution is not reconstructed — it is represented.

## 10. Claims Scope (Informal)

This document establishes prior art for:

- Execution-bound commit enforcement
- Step-level cryptographic execution receipts
- Deterministic execution provenance graphs
- Policy and authorization binding to execution proof

## 11. Causality Guarantees

A system implementing EPG MUST guarantee:

1. **Complete Causal Representation**
   - All execution dependencies MUST be represented as edges

2. **No Hidden Dependencies**
   - No execution step MAY depend on undeclared inputs

3. **Deterministic Traversability**
   - The graph MUST be traversable to reproduce execution order

4. **Receipt Alignment**
   - Every node MUST map to a valid execution receipt


This specification defines execution as a **first-class verifiable construct**, not an emergent property of system logs.

## IP & Licensing Considerations

This document is a public disclosure intended to:

- establish prior art for the concepts described herein  
- document authorship and evolution of the proposed models  
- enable open discussion and architectural exploration  

All concepts, models, and frameworks described in this document are:

- authored and published by the author prior to any external engagement  
- part of an ongoing body of work related to execution architecture and AI system design  

### Pre-Existing Intellectual Property

All intellectual property described in this document constitutes **pre-existing work** of the author.

Any future collaboration, consulting engagement, or implementation:

- does not grant ownership over the concepts described herein  
- does not transfer rights to the underlying models, frameworks, or architectural approaches  
- must be governed by explicit agreement if derivative work ownership is to be assigned  

### Scope of Use

This document permits:

- discussion and reference  
- implementation and adaptation of ideas  
- extension within other systems  

However, this document does not grant:

- exclusive rights to the concepts  
- ownership of the original frameworks  
- rights to proprietary implementations derived from the author's work  

### Implementation Distinction

A distinction is made between:

- **Conceptual Models (this document)** → publicly disclosed and attributable  
- **Implementations (systems, platforms, code)** → may be proprietary and independently owned  

### No Implicit Assignment

No rights, ownership, or claims are transferred implicitly through:

- access to this document  
- discussion of its contents  
- application of its ideas  

Any assignment of rights must be:

- explicit  
- documented  
- mutually agreed upon  

---

## License

This document is released under the **Creative Commons Attribution 4.0 International (CC BY 4.0)** license.

You are free to:

- Share  
- Adapt  
- Build upon  

Provided that:

- Proper credit is given to the author.