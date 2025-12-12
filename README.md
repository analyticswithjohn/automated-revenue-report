Revenue Report Automation Pipeline
Overview

This repository contains a multi-phase Python automation system designed to transform, reconcile, validate, and publish the corporate revenue reporting package.
The automation replaces a historically manual, Excel-heavy workflow that relies on complex formulas, cross-file lookups, and tight quarter-end deadlines — a combination that frequently leads to human error and rework.

By shifting core logic into Python, the workflow becomes:

Repeatable

Auditable

Deterministic

Fast

Resilient against manual mistakes

Scalable for future enhancements (e.g., Power BI / Tableau dashboards)

The automation performs:

Data ingestion from multiple SAP/Salesforce-derived reports

Data transformations (structure, enrichment, category mapping, sign handling, PIT/OT assignment, etc.)

Automated reconciliations across revenue sources, performance obligations, and RAR data

A built-in Validations View to ensure traceability and accuracy

Summaries for accounting, finance, and SEC reporting

(Future phase) Live reporting through BI tools (Power BI, Tableau)

Time Savings

Historically, preparing the full revenue report manually takes 35–49 hours across ~3 business days during a critical reporting window.
This automation significantly reduces the manual workload, minimizes rework, and accelerates review cycles.

Project Structure
| Phase | Description | Estimated Hours Saved |
|-------|-------------|------------------------|
| **Phase 1 – File Setup & Core Preprocessing** | Import source files, configure workspace, derive key fields (profit center, cost element), create merged dataset, flip revenue signs for reporting, and insert base columns for downstream phases. | **3–5 hours** |
| **Phase 2 – Data Enrichment & RAR Reconciliation** | Pull customer details, contract IDs, and metadata from journal entries and RAR. Perform reconciliation between Merge and RAR, align performance obligations, validate contract-level totals, and run matching algorithms (e.g., customer ID + contract ID keying). | **8–9 hours** |
| **Phase 3 – PIT/OT Alignment & Adjustments** | Load >$50k contract schedule prepared by technical accounting. Assign PIT/OT classification and revenue type to matching contracts. Add adjustment logic, potentially creating new lines when needed, ensuring adjustment columns net to zero while preserving contract ID and cost element constraints. | **7–9 hours** |
| **Phase 4 – Global Parent & Strategic Customer Mapping** | Map customers to Global Parent Name & Country. Identify core strategic customers (used in internal reporting akin to “top accounts” or “key enterprise customers”). | **1–3 hours** |
| **Phase 5 – Financial Reporting Summaries** | Prepare summaries used for financial statements and disclosures including internal narratives (N1, N2, N3) and SEC disclosures such as 10-Q/10-K, ASC 606 disaggregation, and MD&A revenue commentary inputs. | **3–5 hours** |
| **Phase 6 – Comprehensive Validations & Close Activities** | Pull trial balance, re-run reports after reclasses, reconcile movements versus prior periods, and ensure system-to-ledger tie-outs. | **6–8 hours** |
| **Phase 7 – Post-Close Aggregation** | Combine the newly-closed quarter with historical data. Perform continuity checks, consistency audits, and metric alignment. | **4–6 hours** |
| **Phase 8 – BI Publishing (Future Phase)** | Publish validated datasets to a data analytics platform (e.g., Power BI, Tableau). Establish a persistent live data feed for automated refreshes. | **3–4 hours (est.)** |

Technology Stack

Python (pandas, openpyxl, pathlib, numpy)

Excel / CSV source data

Power BI or Tableau (future integration)

GitHub for version control and deployment

Key Benefits
✔ Accuracy

Removes risks associated with manual formula errors and fragile Excel dependencies.

✔ Speed

Reduces the end-to-end workflow from ~35–49 hours to a fraction of the time.

✔ Transparency

Every transformation, calculation, and reconciliation step is explicitly coded and reviewable.

✔ Scalability

New revenue structures, contract types, GL mappings, or reporting enhancements can be integrated without rebuilding the workbook.

✔ Audit-Ready

Built-in validations ensure traceability from raw data to final reporting outputs.
