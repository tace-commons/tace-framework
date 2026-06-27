# Operational Qualities

Operational qualities describe how a system behaves, survives, and is managed in production, spanning correctness under load, survival under failure, recovery from disruption, and the human ability to understand and operate it effectively.

## Description

Operational qualities form a cohesive layer of system design concerned with _runtime reality_: what happens when systems are under stress, when components fail, when humans intervene, and when recovery is required. They are not independent properties but interlocking concerns that define whether a system is dependable in practice rather than just in design.

At a high level, they can be understood as four interacting dimensions:
- **Steady-state behavior**: reliability and availability determine whether the system is correct and accessible under normal conditions.
- **Failure behavior**: resiliency and continuity determine how the system behaves under partial or systemic disruption.
- **Recovery behavior**: recoverability determines how the system returns to a known good state after failure.
- **Human operability layer**: observability, operability, and supportability determine how well humans can understand, control, and sustain the system.

These dimensions are tightly coupled. A system cannot be meaningfully resilient without observability, nor recoverable without operability. Likewise, availability without reliability produces systems that are “up but wrong,” while reliability without availability produces systems that are “correct but inaccessible.”

Together, they form a closed loop: **observe → operate → survive → recover → improve**, with reliability and availability anchoring steady-state correctness and accessibility.

# Operational

- [[Reliability]]
- [[Resiliency]]
- [[Recoverability]]
- [[Availability]]
- [[Continuity]]
- [[Observability]]
- [[Operability]]
- [[Supportability]]
