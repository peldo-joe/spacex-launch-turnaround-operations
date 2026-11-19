# SpaceX Falcon 9 Booster Turnaround & Pad Cadence Operations Analysis

End-to-end Python aerospace operations analysis of **90 SpaceX Falcon 9 missions across 53 unique booster cores**, evaluating fleet refurbishment turnaround cycle times, **Block 5** hardware learning curves, **Starlink (`VLEO`)** payload standardization, and launch complex throughput across **CCAFS SLC-40, KSC LC-39A, and VAFB SLC-4E**.

## 1. Executive Summary & Operational Problem
High-cadence launch operations depend on two distinct turnaround cycles: **Booster Refurbishment Turnaround** (calendar days for a specific booster serial number like `B1058` or `B1060` to refly) and **Launch Pad Reset Cadence** (calendar days between consecutive launches at the same pad). Using production Falcon 9 telemetry, this model quantifies the operational bottlenecks across hardware generations, flight-count maintenance gates, and launch sites.

## 2. Key Operational Findings
* **The Block 5 Step-Change:** Transitioning from early reusable boosters (`Block 3.0` median turnaround: **`195.0` days**) to **`Block 5.0`** (`27` reflown missions) cut median booster refurbishment turnaround by **48% to `102.0` days**, with record turnarounds reaching **`51.0` days (`B1058` & `B1060`)**.
* **Flight-Count Maintenance Gate & Learning Curve:** Booster turnaround holds steady across Flights 2–3 (`123.0–125.5` median days, `51.0`-day best), experiences a scheduled deep-maintenance recertification spike at **Flight 4 (`156.0` median / `210.5` mean days)**, and accelerates in the "Fleet Leader" regime on **Flights 5–6 (`138.5` down to `127.0` days, `75.0`-day best)**.
* **Vertical Integration Advantage (`Starlink VLEO` vs. External Customers):** Reflown boosters assigned to internal **Starlink (`VLEO`)** missions achieve a **`113.0`-day median turnaround** compared to **`145.0` days** for external customer payloads—a **32-day (`22%`) cycle-time reduction** enabled by standardized internal payload integration.
* **Launch Complex Specialization & Pad Reset Cadence:**
  * **`CCAFS SLC 40` (High-Cadence Workhorse):** Handled **61% of fleet launches (`55` missions, `305.2 metric tons` to orbit)** with a **`27.5`-day median pad reset** and a **`9.0`-day record pad turnaround**.
  * **`KSC LC 39A` (Heavy-Lift Specialist):** Delivered a **37% heavier average payload (`7,606.5 kg`/flight)** with the fleet's highest booster landing recovery rate (**`77.3%`**) and a **`12.0`-day record pad reset**.

## 3. Repository Contents
* **`spacex_falcon9_turnaround_model.ipynb`** — Python data pipeline (`pandas`, `numpy`) calculating per-serial booster lag diffs (`.groupby("Serial").diff()`), Block generation benchmarks, flight-count learning curves, and pad reset cadence.
