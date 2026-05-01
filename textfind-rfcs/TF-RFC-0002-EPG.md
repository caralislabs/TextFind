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

## License

This document is released under the Creative Commons Attribution 4.0 International (CC BY 4.0) license.

You are free to share and adapt this material for any purpose, provided appropriate credit is given to the author.