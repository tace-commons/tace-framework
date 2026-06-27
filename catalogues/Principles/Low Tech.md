


## Principle: Frugal Design (Low-Tech & Appropriate Technology)

- Statement: Technical solutions must prioritize minimal hardware expense, zero proprietary licensing, and maximum operational accessibility. High-tech infrastructure is an anti-pattern unless explicitly justified by data volume or safety requirements.
- Rationale: Environmental and frontline organizations operate in resource-constrained environments. A brilliant system that requires an active enterprise AWS budget or high-spec hardware will immediately fail field adoption. Low-tech system coupling reduces external dependencies and lowers maintenance overhead. [9, 11]
- Implications:
    
    - Blueprints must favor consumer-grade or commoditized edge hardware (e.g., Raspberry Pi, ESP32 microcontrollers, or existing field smartphones) over proprietary enterprise gear.
    - Data storage patterns should favor lightweight, file-based options (e.g., SQLite or flat CSV/Parquet files) over heavy, containerized relational database server clusters when operating at the edge.
    - User interfaces must be designed for low-literacy or offline-first operational conditions. [9, 12]
    

---

## 🪵 How this drives the TACE ADR Change Log

Including "Low-Tech" as a non-negotiable principle gives your contributors a framework to judge architecture trade-offs during their 1-to-4-hour sprints. For example:

- `ADR-005: Reject Managed Cloud Database for Flat Parquet Files`
    
    - _Context_: A tool needs to store regional soil moisture metrics for Reporting (the R layer in MRV).
    - _Decision_: We reject a managed cloud data warehouse solution (like BigQuery or Snowflake). Instead, the pattern will append data directly to compressed Apache Parquet files stored inside a standard open object registry.
    - _Justification via Principle_: In accordance with the Frugal Design Principle, using flat Parquet files brings cloud hosting costs down to near-zero and allows smaller NGOs to run complex data analytics locally using free, open-source python scripts, bypassing corporate monthly billing. [13, 14]
    

Integrating this principle cleanly connects your Technology Landscape (like Edge Computing and Data Commons) back to the harsh, real-world constraints of the Problem Space. [6]

To continue building out the repository guidelines, let me know if you would like to:

- Incorporate this principle into a complete "TACE Core Architectural Principles" markdown file.
- Draft a Component Audit Checklist that contributors use to grade whether a piece of software is "Low-Tech" enough to be added to the Commons.

  

[1] [https://www.linkedin.com](https://www.linkedin.com/pulse/low-tech-architecture-sustainable-socially-path-alberto-zancanella-3kwpf)

[2] [https://aws.amazon.com](https://aws.amazon.com/blogs/architecture/achieving-frugal-architecture-using-the-aws-well-architected-framework-guidance/)

[3] [https://www.youtube.com](https://www.youtube.com/watch?v=2uzXR3U6JiA&t=587)

[4] [https://medium.com](https://medium.com/@ikppramesh/embracing-frugal-software-architecture-maximizing-value-on-a-budget-6af53f44d76c)

[5] [https://bool.dev](https://bool.dev/blog/detail/the-frugal-architect)

[6] [https://permies.com](https://permies.com/t/132509/Technology)

[7] [https://www.newamerica.org](https://www.newamerica.org/insights/collaborative-design-strategies-for-community-technology/)

[8] [https://www.climate-chance.org](https://www.climate-chance.org/en/best-pratices/developing-low-tech-community-belgium/)

[9] [https://sas-dhrh.github.io](https://sas-dhrh.github.io/dhcc-toolkit/toolkit/minimal-computing.html)

[10] [https://dev.to](https://dev.to/okoye_ndidiamaka_5e3b7d30/building-for-low-bandwidth-environments-how-to-optimize-your-web-experience-for-slower-internet-4140)

[11] [https://github.com](https://github.com/zalando/engineering-principles)

[12] [https://blog.logrocket.com](https://blog.logrocket.com/product-management/why-you-shouldnt-ignore-niche-app-user-types/)

[13] [https://www.visionet.com](https://www.visionet.com/blog/data-lakehouse-the-future-of-modern-data-warehousing-analytics)

[14] [https://www.sarasanalytics.com](https://www.sarasanalytics.com/blog/snowflake-and-snowflake-architecture)

https://sas-dhrh.github.io/dhcc-toolkit/toolkit/minimal-computing.html