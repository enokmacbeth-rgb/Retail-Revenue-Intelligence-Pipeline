# End-to-End Retail Performance & Revenue Intelligence Pipeline

## 📊 Project Overview
This repository contains a production-grade, multi-source Retail Analytics & Business Intelligence Dashboard engineered to transform raw, fragmented, and structurally flawed enterprise data into interactive, executive-level financial insights. 

The project bridges the gap between raw data storage and executive strategic planning. It implements an automated ETL (Extract, Transform, Load) data pipeline, constructs an optimized Star Schema relational database model, applies context-aware analytics calculations, and deploys a one-click VBA automated communication engine.

---

## 🏛️ System Architecture Topology
To maximize computational performance and prevent file bloating, this application completely bypasses legacy Excel lookup formulas (VLOOKUP/XLOOKUP). Instead, it segregates operations into an optimized, high-performance Star Schema relational data model:

*   Fact Table (Global_Sales_Raw): Central transactional ledger containing daily transaction IDs, historical order timelines, quantities sold, and unit prices.
*   Product Dimension (Product_Dim): Connects to the Fact Table via ProductID (1:N relationship) to provide category metadata.
*   Target Dimension (Regional_Targets): Connects to the Fact Table via Country_Key (1:N relationship) to establish quarterly performance baseline thresholds.
*   Time Dimension (Calendar_Dim): Connects to the Fact Table via OrderDate (1:N relationship) to unlock advanced chronological sequences and time hierarchies.

---

## 🛠️ Data Pipeline Engineering (Power Query & M-Code)
The raw enterprise data feeds were intentionally ingested with structural defects, trailing string whitespace, missing records, and conflicting localized formatting to simulate an authentic corporate cleaning workflow.

### 1. Advanced String Normalization & Key Extraction
The regional ledger contained inconsistent geographic identifiers (e.g., mixing "USA", "United States", and an invisible trailing whitespace anomaly "USA "). A robust conditional step was compiled natively in M-Code utilizing string-trimming operations to enforce structural normalization and establish reliable relational database keys:

if Text.Trim([Region]) = "USA" then "US" else if [Region] = "United States" then "US" else if [Region] = "United Kingdom" then "GB" else if [Region] = "UK" then "GB" else if [Region] = "Germany" then "DE" else if [Region] = "GERMANY" then "DE" else if [Region] = "DE" then "DE" else [Region]

### 2. Infinite Calendar Generation
To prevent timeline calculation collapses during period-over-period evaluations, an independent time dimension table was injected via a dedicated Power Query script to generate a continuous, automated chronological sequence supporting time-intelligence functions across 2026.

---

## 🧮 Calculation Engine & Analytical DAX Measures
Because financial targets are stored quarterly but retail sales transaction logs execute daily, standard aggregations distort calculations when viewed at sub-granular rows or unified corporate parent totals. 

To overcome this, a context-aware DAX metrics engine was deployed inside the internal Power Pivot Engine using logical field-state evaluation (HASONEVALUE) to dynamically switch math models between child regions and parent grand total rows. This guarantees that parent rows calculate true weighted corporate percentages instead of a distorted maximum baseline.

---

## 📊 Presentation Layer & Automated Executive UI
The front-end user experience is built on a streamlined dashboard layout utilizing a non-intrusive gray palette with hidden gridlines to emphasize target variance bars.

### Core UI Modules:
1.  **Macro Dashboard Slicers:** Connected cross-filtering controls allowing users to filter multi-source analytics views by geography, category, and date ranges synchronously.
2.  **Strategic Matrix Summary:** Displays total actual revenue, running YTD sums, and target achievements with dynamic formatting indicators.
3.  **High-Value Streaming Audit Log:** A nested transactional tracking matrix utilizing layout overrides ("Allow multiple filters per field" and "Repeat Item Labels") to stream a live, descending record of top-tier VIP customer transactions.

---

## 🔌 One-Click VBA Automation Engine
To streamline the presentation layer, the dashboard contains a custom execution button wired directly to a backend VBA Automation Macro. 

When clicked, the script executes background optimizations: it freezes screen graphics, loops through all canvas shapes and slicer panels to temporarily strip out their Print Object presence (preventing visual clutter on final documents), generates an enterprise-standard PDF report directly inside the local machine's Downloads folder, restores user buttons instantaneously, and automatically instantiates a formatted Microsoft Outlook email draft containing automated messaging, system timestamps, and the report attachment.

---

## 🚀 Key Business Impact & Engineering Takeaways
*   **Zero Manual Preprocessing:** Replaced legacy copy-paste cleaning routines with a single-click Data > Refresh All connection pipeline.
*   **Advanced Filter Optimization:** Resolved nested multi-row layout drop errors by overriding multi-filter field behaviors.
*   **Executive Delivery Velocity:** Reduced report generation and communication loops down to a single physical button click.

---
*Developed as part of an advanced Enterprise Analytics Engineering Portfolio.*
