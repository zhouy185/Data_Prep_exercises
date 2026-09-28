# SwiftParcel Shipment Data — Exercise

## Scenario

You're handed one file from SwiftParcel, a package courier. Every shipment
from the past several weeks is recorded, along with whether the customer
later reported damage. Your manager wants to know: **are damaged shipments
a real problem, and if so, where is it concentrated?**

## The data (`swiftparcel_shipments_small.csv`)

| Column | Description |
|---|---|
| `shipment_id` | Unique shipment identifier |
| `customer_id` | Customer identifier |
| `hub` | Sorting hub the shipment was processed through |
| `ship_date` | Date the shipment was sent |
| `package_type` | Category of package (Fragile, Electronics, Clothing, Household) |
| `weight_kg` | Package weight |
| `declared_value` | Declared value of the package contents |
| `method` | Shipping method: `ground` or `express` |
| `delivered_on_time` | Whether the shipment arrived by its promised date |
| `damage_reported` | Whether the customer reported damage (the outcome of interest) |

Some rows are missing values in `delivered_on_time` and `damage_reported`.
Figuring out *why* each column has gaps — and whether it's safe to drop
those rows — is part of the exercise, not a data-quality accident.

## Questions

### Q1 — Load, inspect, diagnose

Load the file and run the basic inspection habit (`.info()`,
`.isnull().sum()`). Two columns have missing values: `delivered_on_time`
and `damage_reported`. For each one:

- How many rows are missing?
- Where do the missing rows fall in `ship_date` — scattered throughout, or
  clustered near the end of the date range?

### Q2 — Clean and compute the headline number

- Drop the rows missing `damage_reported`, then cast the column to boolean
  (in that order — explain why the order matters).
- Compute the overall damage rate.

### Q3 — Group your way to the real story

Using the cleaned data, compute count, sum, and rate for damage reports:

- Grouped by `package_type`
- Grouped by `method`
- Grouped by `["package_type", "method"]` together

Report the sample size (`n`) alongside every rate — a high rate on a small
n means something different than the same rate on a large n. Identify
where the problem actually concentrates, and explain why the two-column
grouping tells a different (and more useful) story than either single-column
grouping alone.

