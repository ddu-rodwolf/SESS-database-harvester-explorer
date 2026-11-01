# SIOS SESS Recommendation Explorer & Ingestion Pipeline

## ⚠️ Disclaimer

This tool is designed to automate the harvesting, parsing, and enrichment of scientific recommendations from the **SESS ([State of Environmental Science in Svalbard](https://sios-svalbard.org/SESSreport#PurposeoftheSESSreport))** reports published by the [SIOS Knowledge Centre](https://sios-svalbard.org/). 

While currently leveraging a hybrid setup with Excel Power Queries and Python, the architecture is evolving into a standalone Python-driven backend meant to support automated ingestion, database reconstruction, and analytics for a **Drupal-based knowledge database**.

---

## 🧭 Overview

The **SESS Recommendation Explorer** is an integrated data pipeline and desktop toolkit built to transform text-heavy PDF reports into structured, searchable data. It bridges web-scraping/API enrichment workflows with a robust Python desktop application (`tkinter`) designed for seamless collaboration across machines and colleague accounts (via OneDrive sync).

### ✨ Core Capabilities
- **Automated Harvesting:** Scrapes SESS issue metadata and summary PDF links directly from web markup or Excel workbooks.
- **Smart PDF Parsing:** Uses `pdfplumber` with geometric bounding-box content detection and colour-fallback strategies to isolate recommendation blocks reliably.
- **Metadata Enrichment:** Queries the Zenodo REST API to retrieve author lists, publication years, keywords, and usage metrics (`unique_downloads`, `unique_views`).
- **Interactive UI (`sess_issue_selector.py`):** Provides live workbook inspection, issue filtering, and persistent settings management.
- **Reporting & Analytics:** Generates structured Excel tables, pivot tables, and statistical overviews to track impact, historical snapshots, and support founder reporting.

---

## 🏗️ Workflow Architecture

1. **Source & Ingestion:** Pulls report structures either from web endpoints or Excel configuration workbooks (`.xlsm`) utilizing advanced Power Query M-code.
2. **Processing & Extraction:** The Python engine downloads, explores pages, and parses recommendations into structured records.
3. **Target Ingestion:** Prepares clean, faceted datasets ready for ingestion into a Drupal knowledge database interface.

---

## 📂 Project Structure

```text
SIOS-SESS-Recommendation-Explorer/
│
├── sess_recommendations.py       # Core PDF harvesting, parsing, and text extraction engine
├── sess_issue_selector.py        # Tkinter UI for issue selection, settings, and live logging
├── Harvest_PQ - stable.xlsm      # Excel workbook containing Power Query M-code pipelines
└── README.md                     # Project documentation
