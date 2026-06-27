Resiliency is the ability of a system to absorb and adapt to disruptions while continuing to function.

## Description

Resiliency focuses on how a system behaves under stress or failure. Rather than avoiding failure entirely, a resilient system anticipates it and adapts accordingly. It degrades gracefully, isolates faults, and recovers without cascading collapse. Resiliency is about *continuity under adversity*, ensuring that disruptions do not escalate into systemic outages. It often involves redundancy, fault isolation, and adaptive control mechanisms.

## Risks

Without resiliency, small failures can escalate into large-scale system outages.

* Cascading failures across dependent components
* Complete system shutdown from localized faults
* Inability to handle load spikes or infrastructure issues
* Amplified impact of external disruptions (e.g., network outages)
* Increased recovery time and operational stress

## Symptoms

* Sudden and widespread system outages
* Performance collapse under moderate stress
* Tight coupling between components leading to failure propagation
* Inability to isolate or contain faults
* Repeated incidents triggered by similar conditions

## Causes

* Lack of fault isolation boundaries
* Over-reliance on single points of failure
* Synchronous dependencies across services
* Insufficient capacity planning or load management
* Absence of circuit breakers or backpressure mechanisms

## Development

* Introduce redundancy and failover strategies
* Implement circuit breakers and bulkheads
* Design for graceful degradation
* Use asynchronous communication patterns
* Conduct chaos engineering and failure testing

## Maturity

A resilient system is composed of loosely coupled components that can fail independently without bringing down the whole. It dynamically adapts to changing conditions—rerouting traffic, shedding load, or degrading non-critical features. Engineers design systems with the expectation of failure, not its absence.

At higher maturity, resiliency becomes proactive. Systems detect early warning signals and adjust behavior before failures fully manifest. Automated remediation, adaptive scaling, and intelligent routing ensure continuity even in volatile environments.

## Trade-offs

* Increased infrastructure cost due to redundancy
* Higher system complexity and operational overhead
* Potential inefficiencies from over-provisioning
* More complex testing and validation requirements

## Example

A smart grid orchestrator managing renewable energy distribution initially relied on centralized control. When a regional node failed, it caused cascading disruptions across the grid, affecting energy distribution stability.

The system was redesigned with decentralized control, local failover capabilities, and adaptive load balancing. Each node could operate independently and coordinate asynchronously. During subsequent disruptions, failures were contained locally, and the broader system continued functioning with minimal impact. Resiliency transformed the grid from fragile to adaptive.

## Summary

Resiliency complements reliability by addressing behavior under failure conditions. While reliability ensures correctness, resiliency ensures survival. It is tightly linked with availability and continuity, enabling systems to remain functional despite disruptions.