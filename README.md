# Velora Hotel Revenue & Booking Intelligence Dashboard

## 📊 Business Performance Overview
An enterprise-grade hospitality operations solution built for **Velora Hotel** to optimize room yield management, break down guest distribution channels, and analyze revenue capture behaviors. Processing operational transactions from **September 2024 to November 2024**, this dashboard consolidates key performance drivers to protect revenue margins against cancellations and maximize customer loyalty programs.

<p align="center">
  <img src="Hotel Booking Dashboard.jpg" width="100%" alt="Velora Hotel Dashboard View" />
</p>

### 🔗 Public Interactive Link
* [👉 Click Here to View the Live Interactive Hospitality Dashboard Portfolio](YOUR_POWER_BI_SERVICE_OR_NOVYPRO_LINK_HERE) *

---

## 📈 Strategic KPI Matrix & Business Insights

### 1. Macro Core Performance Metrics
* **Inflow Metrics:** Tracks **$1M in Gross Revenue** across **5K Total Bookings** yielding **9K Total Room Nights**.
* **Operational Risk Warning:** Identifies a significant **28.7% Cancellation Percentage**, highlighting a vital area for front-desk deposit policy adjustments.
* **Pricing Yields:** Calculates an **Average Room Rate (ADR) of $147.8**, establishing a clear pricing benchmark.

### 2. Temporal & Seasonality Demand Analysis
* **Stay Velocity Trends:** Line chart visualizing daily occupancy waves. It displays an intense peak of over **130 concurrent stays** in mid-October 2024.
* **Weekday vs. Weekend Utilization:** A side-by-side distribution analysis showing steady room demand from Tuesday through Friday, tapering off predictably on Sundays.

### 3. Guest Cohorts & Lead-Time Metrics
* **Booking Window Ingestion:** A breakdown chart revealing that the vast majority of guests (**~2,500 bookings**) complete reservations **"Before a week"** of arrival, whereas long-range planners (>4 weeks) make up a secondary operational cohort.
* **Loyalty Tier Distribution:** Isolates user volume by member tier, uncovering that **Non-members (2,038 bookings)** represent the largest transaction channel, followed directly by **Essential-tier members (1,036)**.

### 4. Cross-Tabulated Channel Matrix Table
* Features a granular matrix visual mapping **Loyalty Levels** against **Booking Mediums (App, At the hotel, Connected Wholesaler, GDS, Phone, Velora.com)**. This quickly reveals that direct bookings on *Velora.com* are highly active among top-tier "Preferred" members (259 bookings), minimizing third-party fee leakage.

---

## 🛠️ Advanced ETL & Structural Modeling Data Engine
* **Star Schema Architecture:** Enforces optimized data propagation by separating transactional booking fact tables from dimension lookups (`Dim_Dates`, `Dim_LoyaltyTiers`, and `Dim_Channels`).
* **ETL Transformations:** Managed date ranges using explicit parameters, bucketed raw numeric "Days in Advance" values into explicit categorical text ranges (e.g., *1. Before a week*, *2. Before 2 weeks*), and handled string standardization for member classifications.

### Centralized Explicit DAX Showcase

#### Dynamic Cancellation Rate Logic
```dax
Cancellation Rate % = 
VAR TotalBookings = COUNT('Fact_Bookings'[BookingID])
VAR CancelledBookings = CALCULATE(COUNT('Fact_Bookings'[BookingID]), 'Fact_Bookings'[Status] = "Cancelled")
RETURN
DIVIDE(CancelledBookings, TotalBookings, 0)
