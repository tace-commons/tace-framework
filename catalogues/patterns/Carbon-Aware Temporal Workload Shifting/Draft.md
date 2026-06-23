# Abstract

Carbon-Aware Temporal Shifting is a workload scheduling pattern that reduces operational carbon emissions by aligning compute execution with periods of lower grid carbon intensity. As electricity grids transition toward higher renewable penetration, carbon intensity becomes temporally variable, creating opportunities to defer non-urgent or flexible compute to cleaner periods. This pattern introduces a structured approach for identifying shiftable workloads based on duration, intensity, and flexibility constraints, and coordinating their execution through a scheduler informed by real-time and forecasted carbon signals.

The pattern distinguishes between manual and automated shifting strategies, balancing implementation simplicity against operational flexibility and scalability. While manual approaches prioritize orthogonality and low system risk, automated approaches enable continuous optimization at the cost of increased system complexity and additional infrastructure dependencies. The effectiveness of the pattern is contingent on workload characteristics, carbon signal accuracy, and system-level coordination, particularly in environments with competing optimization objectives such as cost, latency, and reliability. Overall, Carbon-Aware Temporal Shifting provides a practical foundation for integrating carbon considerations into compute scheduling decisions in modern data center and cloud environments.
### Keywords

Carbon-aware computing, temporal workload shifting, sustainable computing, green scheduling, carbon intensity, workload scheduling, demand response, cloud orchestration, energy-aware systems, carbon optimization
# Context

For an overview of the context please refer to this high-level [[catalogues/Patterns/Carbon-Aware Workload Shifting/Draft|pattern]].

The electrical power grid fluctuates in carbon intensity throughout the day. On one hand you have periods of high carbon intensity and high consumer demand (dirty peaks), on the other hand you have periods of low carbon intensity and excessive clean energy supply.

As data centres continue to grow their share of energy consumption - it becomes more important to understand the impacts of compute and how to responsibly deal with it in the face of the clean energy transition [1].
# Problem

Organisations are often not aware or consider carbon intensity as a factor in their workload scheduling decisions. As a result - excessive carbon emissions are produced during intensive periods - contributing to the changing global climate. Even if there's an incentive to account for carbon in workloads - the industry still does not have sufficient standards and patterns to allow organisations to confidently address the problem.
## Problem Statement

How do we shift compute workloads away from carbon intensive periods and towards cleaner periods?
# Solution

## Workload Properties

Compute workloads have varying degrees of potential to become cleaner. When accessing which workloads to optimize, consider their properties described below. The workloads with the highest potential for shifting are those who operate intensively within dirty periods, over a long duration.
### Initiation

A workload is initiated when it begins execution. This is the moment from when it begins drawing power from the grid.
### Duration

Workloads durations can be broadly categorised into three types:
- **Short-Running** - most workloads are short-running [1] spanning from a few minutes to a few hours. Although they a short-lived, they are the most abundant and frequent.
- **Long-Running** - spanning from hour to days - these workloads may include machine learning training, simulations and analysis. These are less common and less frequent. The longer the workload window the more likely it will be consuming dirty energy as the grid fluctuates between clean and dirty supply. 
- **Continuously-Running** - workloads where there is not a defined end date/time - they operates indefinitely. These workloads are not considered shiftable, so are out of scope for this pattern.
### Intensity

Power hungry workloads are concerning during dirty periods, but are most ideal for when clean supply is in excess - having the potential to consume otherwise curtailed energy.
## Workload Qualities

Even if a workload's properties suggest is has potential to shift, the workload will also need to be assessed in regards to its qualities, list below.
### Shiftable

In order for compute workloads to adapt to cleaner periods they must be shiftable. Some workloads are not shiftable - they have to run at a particular time in order to fulfil one or more SLAs. Others have flexibility in when they are expected to execute. The flexibility window determines the degree of freedom for which a workload can shift.
### Interruptible

For long-running workloads that have the ability to be paused and resumed, they can be interrupted during carbon intensive periods and resumed when conditions are once again optimal. Similarly, if a workload is composed of smaller loads - they can be scheduled separately into cleaner periods.
## Solution Qualities
### Orthogonal

Changing infrastructure to account for a something new (like workload shifting) typically introduces risk to things failing or changing in unforeseen ways. I.e. if delaying a workload fails and therefore fails to run the workload at all. To reduce risk - simple and non-intrusive strategies are preferred.
### Efficient

If additional components are introduced to achieve shifting then there is a risk that these components add to the power consumption from the grid, potentially nullifying the efforts to become cleaner. I.e. adding in a job queue for delayed workloads. So therefore minimising the additional components is preferred.
## Solution Properties

### Manual

Long-running scheduled workloads can be manually shifted by analyzing forecast trends. Upfront analysis can predict carbon savings. A manual solution allows the solution to be technically orthogonal because there are no new components to potentially cause failures to existing components. Due to the absence of new components, manual solutions are efficient. 
### Automatic

Automatic shifting requires additional components, so therefore does tradeoff orthogonality and efficiency with flexibility.
## Components

### Workload

**Role:** Represents the unit of compute to be shifted.
**Responsibilities:**
- Encapsulates execution logic
- Declares flexibility:
    - when it _can_ run (time window)
    - whether it can be delayed or interrupted
- Implies duration and intensity
**Relationships:**
- Submitted to **Scheduler**
- Executed by **Compute Platform**
**Examples:**
- Batch job, ML training task, ETL pipeline, CI job
### Carbon Signal

**Role:** Represents the external environmental input that informs _when_ execution is cleaner.
**Responsibilities:**
- Provides carbon intensity over time (current + forecast)
- Defines “clean” vs “dirty” periods
**Relationships:**
- Consumed by **Scheduler**
**Examples:**
- Grid carbon intensity APIs, energy forecasts
### Scheduler

**Role:** The core component that decides _when_ workloads should run.
**Responsibilities:**
- Matches workload flexibility against carbon signal
- Selects optimal execution time
- Decides:
	- run now
    - delay
    - (optionally) pause/resume
**Relationships:**
- Receives **Workload**
- Consumes **Carbon Signal**
- Dispatches to **Compute Platform**
**Examples:**
- Job scheduler, orchestrator, workflow engine with added logic
## Solution Statement

A **Scheduler** uses a **Carbon Signal** to decide when a **Workload** should run on a **Compute Platform**, within its allowed flexibility window.
# Tradeoffs
## Pros

#### High-impact carbon reduction with minimal architectural change

- Leverages **temporal variability in grid carbon intensity** without requiring hardware or geographic relocation
- Manual approaches preserve **orthogonality** (low risk to existing systems)
#### Strong alignment with workload characteristics

- Maximizes benefit for **long-running, high-intensity, flexible workloads** (highest marginal abatement potential)
- Exploits **otherwise curtailed clean energy**, improving system-level efficiency
#### Incremental and composable adoption

- Can start **manually (low complexity)** and evolve to **automated scheduling**
- Integrates with existing schedulers/orchestrators rather than replacing them
### Cons

#### Limited applicability due to workload constraints

- Many workloads are **non-shiftable (SLA-bound)** or **non-interruptible**
- Short-running jobs—despite being numerous—offer **low individual impact**
#### Dependence on forecast quality and signal choice

- Effectiveness hinges on **accuracy of carbon forecasts**
- Misuse of **average vs marginal carbon signals** can lead to **suboptimal or even counterproductive decisions**
#### Operational and system complexity

- Requires **scheduler enhancements, carbon data integration, and policy logic**
- Introduces risks to **reliability, latency, and job completion guarantees**
#### Rebound and system-level effects

- Load shifting may **create new peaks** or **shift congestion**, reducing net benefit
- Benefits diminish with **widespread adoption** (coordination problem)
#### Overhead vs benefit trade-off

- Additional components (queues, orchestration logic) introduce **compute and energy overhead**
- For low-intensity workloads, **overhead may outweigh carbon savings**
# References

\[1] [What is the clean energy transition?](https://web.archive.org/web/20251118010011/https://www.nationalgrid.com/stories/energy-explained/what-clean-energy-transition)