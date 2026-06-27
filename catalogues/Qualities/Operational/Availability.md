Availability is the proportion of time a system is operational and accessible when required.

## Description

Availability measures whether a system is *up* and able to serve requests at any given moment. It is typically expressed as a percentage over time (e.g., 99.9% uptime). Unlike reliability, which focuses on correctness, availability focuses on accessibility. A system may be available yet unreliable if it returns incorrect results. High availability systems are designed to minimize downtime through redundancy, failover, and fault tolerance. It is particularly critical in systems that provide real-time services or support operational decision-making.

## Risks

Without sufficient availability, systems fail to meet user expectations and operational demands, even if they are otherwise correct.

* Loss of service during critical operations
* Missed real-time insights or decisions
* Breach of service-level agreements (SLAs)
* Economic or environmental impact due to downtime
* Reduced stakeholder confidence and adoption

## Symptoms

Systems with poor availability exhibit frequent or prolonged interruptions in service.

* Frequent outages or downtime windows
* Slow or unresponsive services under normal load
* Scheduled maintenance causing service disruption
* Inconsistent access across regions or users
* Dependence on manual intervention to restore service

## Causes

Availability issues often arise from insufficient redundancy or poor operational practices.

* Single points of failure in infrastructure
* Lack of failover mechanisms
* Poor capacity planning
* Inefficient deployment or maintenance strategies
* Over-reliance on synchronous dependencies

## Development

Improving availability requires designing systems that remain accessible despite failures.

* Introduce redundancy across components and regions
* Implement automated failover and load balancing
* Use rolling deployments and blue-green strategies
* Monitor uptime and enforce SLAs
* Design for horizontal scalability

## Maturity

A highly available system operates continuously with minimal interruption, even during failures or maintenance. Traffic is seamlessly routed around failures, and users experience little to no disruption. Availability targets are clearly defined, measured, and consistently met.

At advanced maturity, availability becomes an intrinsic property of the system architecture. Multi-region deployments, active-active configurations, and automated orchestration ensure that failures are effectively invisible to end users. Maintenance activities occur without downtime, and systems scale dynamically to meet demand.

## Trade-offs

* Increased infrastructure and operational costs
* Complexity in distributed system design
* Potential for data consistency challenges (e.g., CAP theorem trade-offs)
* Overhead in monitoring and orchestration

## Example

A disaster warning system designed to alert coastal communities relied on a single regional data center. During a storm event, connectivity to the data center was lost, rendering the system unavailable when it was needed most.

The system was redesigned with multi-region deployment, edge-based alerting, and redundant communication channels (e.g., satellite and mobile networks). Availability improved significantly, ensuring that alerts could be delivered even during infrastructure disruptions. The system became a reliable safeguard for vulnerable communities.

## Summary

Availability ensures that systems are accessible when needed, forming a critical user-facing quality. It works closely with resiliency and continuity to ensure sustained operation and complements reliability by ensuring correct services are also reachable.