Continuity is the ability of a system to sustain its essential operations over time despite disruptions.

## Description

Continuity extends beyond availability by focusing on maintaining *business or mission-critical functions* during and after disruptions. It considers not just whether the system is running, but whether it continues to deliver its core value. Continuity planning includes disaster recovery, operational fallback modes, and long-term sustainability of services. It aligns technical capabilities with organizational priorities, ensuring that critical workflows remain intact under adverse conditions.

## Risks

Without continuity, systems may remain operational but fail to deliver meaningful outcomes.

* Disruption of critical workflows
* Inability to meet mission objectives
* Loss of coordination between dependent systems
* Extended operational degradation
* Failure to meet regulatory or societal obligations

## Symptoms

* Core functions unavailable despite system uptime
* Manual workarounds replacing automated processes
* Partial system operation with reduced effectiveness
* Inconsistent service delivery across domains
* Dependency failures impacting critical workflows

## Causes

* Lack of business continuity planning
* Poor prioritization of critical functions
* Tight coupling between essential and non-essential services
* Inadequate disaster recovery strategies
* Insufficient stakeholder alignment

## Development

* Identify and prioritize critical system functions
* Design fallback and degraded operation modes
* Implement disaster recovery and continuity plans
* Decouple critical and non-critical components
* Regularly test continuity scenarios

## Maturity

A system with mature continuity maintains its core mission even under extreme conditions. Non-essential features may be reduced or disabled, but critical operations persist. Teams understand which functions must be preserved and have predefined strategies to ensure their continuity.

At higher maturity, continuity is deeply integrated into system design and organizational processes. Systems can operate in degraded but functional states for extended periods. Decision-making remains informed, and essential services continue without interruption, even in crisis scenarios.

## Trade-offs

* Reduced feature set during degraded operation
* Increased design and planning complexity
* Additional cost for redundancy and fallback mechanisms
* Potential inefficiencies in maintaining multiple operational modes

## Example

A geospatial information system supporting wildfire response provided high-resolution mapping and analytics. During peak demand, the system became overwhelmed, and critical mapping features were delayed.

The system introduced a continuity strategy: during high load, advanced analytics were temporarily disabled, prioritizing core mapping and alerting capabilities. This ensured that responders always had access to essential information. Continuity allowed the system to fulfill its mission even under stress.

## Summary

Continuity ensures that systems deliver their intended value, not just their technical functionality. It bridges the gap between availability and operational impact, ensuring that critical services persist even under adverse conditions.