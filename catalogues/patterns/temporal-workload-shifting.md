### Temporal Workload Shifting

We want to avoid consuming energy when the grid is operating under peak consumption, especially when the supply is dirty and tipping over onto peaker plants. We also want to aim for consuming energy when there is surplus supply of clean energy (green windows).

https://www.compute-gardener.com/

# Limitations

- Schedules are bound to a strict Maximum Delay SLA Boundary (e.g., “This task must run within the next 24 hours”). The system queries forecast data to pinpoint the cleanest operational window within that period. If the boundary approaches and a green window hasn't occurred, the job executes out of necessity to preserve business requirements.
