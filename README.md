
# SIOS SESS Recommendation Explorer

## ⚠️ Project Overview

The SIOS SESS Recommendation Explorer is a Python desktop application designed to harvest, explore and extract scientific recommendations from the **SESS (State of Environmental Science in Svalbard)** reports published by the [SIOS Knowledge Centre](https://sios-svalbard.org/).

The project aims to transform recommendations embedded in PDF reports into structured, searchable information that can eventually support a dedicated knowledge database.

The application is currently evolving from an initial Excel and Power Query solution towards a standalone Python-based harvesting and processing system.

## 🧭 Current Application

The Python application provides an integrated workflow for retrieving SESS issue information, downloading PDF reports and extracting individual recommendations.

### Core capabilities

- **SESS Issue Harvesting:** Retrieves issue numbers, report titles, webpage URLs and Summary PDF download links.
- **Issue Selection:** Provides a Tkinter interface to select issues and configure processing actions.
- **PDF Downloading:** Downloads selected SESS PDF reports into a configurable working directory.
- **PDF Exploration:** Scans PDF pages to identify chapter headings and potential recommendation sections.
- **Recommendation Extraction:** Uses `pdfplumber`, geometric bounding-box detection and colour-based fallback detection to identify recommendation boxes and extract their contents.
- **Structured Export:** Generates CSV datasets containing individual recommendations and extraction diagnostics.

## 🏗️ Application Architecture

The application consists of three principal Python modules:

| Module | Responsibility |
|---|---|
| `sess_issue_harvest.py` | Retrieves SESS issue information and generates `SESS_Issues.csv` |
| `sess_issue_selector.py` | Provides the graphical interface for issue selection and workflow configuration |
| `sess_recommendations.py` | Coordinates PDF downloading, exploration and recommendation extraction |

The application is launched through:

```bash
python sess_recommendations.py
```

The main processing workflow is:

1. Harvest SESS issue information.
2. Select the issues to process.
3. Configure the desired actions.
4. Download the corresponding PDF reports.
5. Optionally explore PDF pages.
6. Extract individual recommendations.
7. Generate structured CSV outputs.

Exploration and extraction can be performed independently or together.

## 📊 Data Outputs

The application currently generates three principal CSV datasets.

| File | Content |
|---|---|
| `SESS_Issues.csv` | SESS issue metadata and Summary PDF URLs |
| `recommendations_clean.csv` | Individual extracted recommendations and source references |
| `extraction_log.csv` | PDF detection results and raw extracted text |

Downloaded PDF reports are retained in the configured working directory.

The extracted recommendation dataset provides the foundation for subsequent database integration.

## 📚 Project Documentation

Detailed technical documentation is maintained in the `docs/` directory.

| Document | Description |
|---|---|
| `STRUCTURE.md` | Project organization and module inventory |
| `WORKFLOW.md` | Application execution workflow |
| `architecture/PROCESSING_PIPELINE.md` | PDF exploration and recommendation extraction mechanisms |
| `architecture/DATA_FLOW.md` | Information flow between processing stages |

Additional documentation describes the individual Python modules and their implementation.

## 📈 Project Evolution and Future Development

The project originated from an Excel-based solution using Power Query and VBA macros.

The workbook `Harvest_PQ - stable.xlsm` provides the foundation for the current development, particularly its Power Query harvesting mechanisms and its approach to exploring structured recommendation data.

Its statistical and dashboard concepts, including the analysis of chapter downloads from the Zenodo portal, also remain useful sources of inspiration.

The longer-term objective is to develop a standalone Python-based harvesting and parsing system connected to a structured database.

Planned development includes:

- Automated harvesting and updating of SESS source information.
- A structured relational database for issues, chapters and recommendations.
- Metadata enrichment using external sources such as the Zenodo API.
- Database maintenance and update mechanisms.
- Analytics and reporting.
- Integration with a Drupal-based knowledge database.

These are development objectives rather than capabilities of the current Python application.

## 🛠️ Technologies

- Python
- Tkinter
- pdfplumber
- pandas
- requests
- CSV and JSON data handling
- Excel Power Query and VBA (original project foundation)

## ⚙️ Installation and Execution

Install the required Python dependencies:

```bash
pip install pandas pdfplumber requests
```

Run the application from its project directory:

```bash
python sess_recommendations.py
```

The application opens the SESS issue-selection interface.

The working directory for downloaded PDFs and generated extraction files can be configured through the interface.

