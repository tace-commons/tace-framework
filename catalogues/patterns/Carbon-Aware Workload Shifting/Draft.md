# Abstract

TODO
### Keywords

TODO
# Context

## The Grid

The electricity generated to feed the power grid can be considered "clean" or "dirty". Clean energy is when the electricity is supplied from renewable resources: wind, solar, hydro, etc. Conversely it is dirty when supplied from non-renewable resources: coal, oil, gas, etc. In this context we consider non-renewable energy as "dirty" due to the greenhouse gas emissions (GHG) produced: carbon-dioxide, methane, etc.

Cloud data centres, connected via the electrical grid, can consume energy from various sources, ranging from clean to dirty. As most renewable resources are intermittent in their availability (i.e. the sun doesn't always shine, its not always windy, etc.) the grid can vary in its cleanliness throughout the day. When renewables are less available the dirty non-renewables are available instead.
## Peak Periods

The demand for energy from the grid changes throughout the day too. During peak consumption periods the supply could be dirty or clean. The worst conditions we can observe is when peak demand periods overlap with peak dirty supply periods. Conversely, the best conditions are when peak demand periods overlap with peak clean supply periods.

Adding demand to peak periods increases the risk of grid operators having to spin up heavy "peaker plants" - contributing to to dirtier peaks. This also has a cost impact - the majority of dirty energy supply is more expensive than clean energy [7], especially due to peaker plants and marginal pricing.
# Problem

### Dirty Compute Workloads

Large compute workloads consume a lot of energy within sustained windows of operation, which contributes to carbon emissions, depending upon how dirty the grid is at the time. A batch process like an ETL, large database backup/archiving, log aggregation, machine learning training job, etc. could be running during peak demand / dirty supply periods - contributing to the highest levels of emissions.

Overall, data centers are responsible for 1% of global energy consumption, and demand is expected to rise to 3% by 2030. [1,8]
### Grid Bottlenecks

As demand for energy from the grid increases over the years (mostly due to AI data centres) the legacy parts of the grid can start to degrade or fail due to insufficient maintenance or development in face of rapid increase of demand. Peak periods can cause serious issues for the grid operators and the underlying infrastructure in the long term.
### Wasted Clean Energy

Clean energy supply can surpass consumer demand. Because the grid needs to maintain a stable equilibrium between supply and demand - clean energy production is curtailed (throttled down or turned off) in order to match the lower consumer demand. This is "free clean energy" if there were a consumer available to match the excess supply.
# Cost

TODO: explain how dirty energy is more expensive
## Regulation

Environmental sustainability has become a major focus for corporate governance.
Regulators from around the globe are increasingly demanding that corporations
record, report, and reduce their emissions. Climate governance has already begun to
impact supply chains and businesses around the globe. [2]
## Problem Statement

How do we operate our compute workloads so that they avoid consuming dirty energy and aim to consume as much clean energy as possible (especially the “free” clean energy)?
# Solution

It is possible to reduce the carbon footprint of compute workloads by shifting **when** and **where** they operate and **how much** resource they consume when running. It allows workloads to shift and adapt their demand to match cleaner supply. This provides us with a 3-dimensional solution space, so therefore 3-degrees of freedom to optimize for cleaner energy consumption.

As the goal is to reduce the carbon footprint - the highest priority is to minimize additional components and their compute power - so therefore the following approaches and their options are ordered by their level of intrusion to the existing ecosystem.
## Temporal Workload Shifting

[[catalogues/Patterns/Carbon-Aware Temporal Workload Shifting/Draft|Draft]]
## Spatial Workload Shifting

TODO
## Demand Shaping

TODO
# Drivers

TODO
# Limitations

- **Diminishing Returns as Grids Decarbonise** - The benefit of carbon-aware shifting _relative to carbon-agnostic scheduling_ decreases as the energy supply becomes cleaner. As UK and European grids transition to higher proportions of renewables, the marginal gains from shifting shrink. Simple scheduling or shifting heuristics often yield most of the available carbon reductions, with more sophisticated techniques providing diminishing additional benefit. This is an important consideration for the business case — the ROI of complex optimisation will erode over time as grids clean up. [4]
    
- **Data Sovereignty and GDPR Constraints** - 
    
- **Latency and SLO Constraints for Customer-Facing Workloads** 
    
- **Architectural Complexity** - if workload scheduling is already complex, then adding in mechanisms for workload shifting could introduce maintenance costs and operational risks. ROI is a key consideration per use case.
# Glossary

**Carbon intensity** - is a measure of how clean our electricity is. It refers to how many grams of carbon dioxide (CO2) are released to produce a kilowatt hour (kWh) of electricity. [5]
Carbon-aware Computing - ...

## References

\[1] [Let's Wait Awhile: How Temporal Workload Shifting Can Reduce Carbon Emissions in the Cloud](https://eprints.gla.ac.uk/268170/)
\[2] [Carbon-aware Computing](https://pub-c2c1d9230f0b4abb9b0d2d95e06fd4ef.r2.dev/sites/418/2023/01/carbon_aware_computing_whitepaper.pdf "https://pub-c2c1d9230f0b4abb9b0d2d95e06fd4ef.r2.dev/sites/418/2023/01/carbon_aware_computing_whitepaper.pdf")
\[3] [Aceso: Carbon-Aware and Cost-Effective Microservice Placement for Small and Medium-sized Enterprises](https://arxiv.org/html/2603.10768v1)
\[4] [On the Limitations of Carbon-Aware Temporal and Spatial Workload Shifting in the Cloud](https://arxiv.org/abs/2306.06502 "https://arxiv.org/abs/2306.06502")
\[5] [What is carbon intensity?](https://web.archive.org/web/20240418012608/https://www.nationalgrid.com/stories/energy-explained/what-is-carbon-intensity)
\[6] [Carbon-Aware Spatio-Temporal Workload Shifting in Edge–Cloud Environments: A Review and Novel Algorithm](https://www.mdpi.com/2071-1050/17/14/6433 "https://www.mdpi.com/2071-1050/17/14/6433")
\[7] [IRENA report](https://www.irena.org/-/media/Files/IRENA/Agency/Publication/2025/Jul/IRENA_TEC_RPGC_in_2024_Summary_2025.pdf "https://www.irena.org/-/media/Files/IRENA/Agency/Publication/2025/Jul/IRENA_TEC_RPGC_in_2024_Summary_2025.pdf")
\[8] [Video - Let’s Wait Awhile](https://youtu.be/GiI7lXqWmqw?si=3VJWgdUlmFn32lpA)
# Notes

- Can Demand Shaping work with eventual consistency? i.e. when clean energy is more available then more compute is available to process jobs in a queue. The cleaner the faster.
- There can be many engineering pattern, i.e. pipeline jobs, db backups, etc.