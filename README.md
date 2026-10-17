# Score-Lens

A high-performance, 100% offline desktop application built to parse, analyze, and visualize Bangalore University Tabulation Register PDF ledgers. Upload a university marksheet ledger to generate an interactive analytics dashboard featuring student rankings, subject-level breakdowns, statistical grade distributions, and multi-sheet Excel exports.

[![Python](https://img.shields.io/badge/Python-3.10+-3776AB?logo=python&logoColor=white)](https://www.python.org/)
[![UI-CustomTkinter](https://img.shields.io/badge/UI-CustomTkinter-2e8b57)](https://github.com/TomSchimansky/CustomTkinter)
[![Platform](https://img.shields.io/badge/Platform-Windows-0078D6?logo=windows&logoColor=white)](https://github.com/SahilPathan18/Score-Lens)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE)

---

## Overview

University examination ledgers are typically distributed as dense, 100+ page tabulation register PDFs. Manually aggregating student performance, determining toppers, computing pass percentages, and filing departmental records can take days.

**ScoreLens** automates this end-to-end. By leveraging high-throughput offline PDF parsing with PyMuPDF and accelerated UI rendering with CustomTkinter, ScoreLens extracts and structures batch data within seconds—all on your local machine with zero network exposure.

---

## Key Features

- **High-Speed PDF Ingestion** — Automated parsing of student metadata, USN, subject codes, internal/external marks, SGPA, and CGPA using PyMuPDF.
- **100% Offline & Privacy-Preserving** — Zero cloud dependencies; institutional data and student marks never leave your machine.
- **Executive Analytics Dashboard** — Instant metrics at a glance:
  - Total candidates, overall pass rate, and average SGPA/CGPA
  - Semester toppers and department rank lists
  - Aggregate grade frequency distribution
- **Interactive Student Explorer** — Search records instantly by Student Name or Register Number (USN), with multi-attribute filtering (PASS, FAIL, PROMOTED).
- **Subject-Wise Analytics** — Granular breakdown for every course, covering pass percentages, average scores, and backlog counts.
- **Data Visualizations** — Embedded Matplotlib visualizations:
  - SGPA distribution curves
  - Pass/Fail outcome ratios
  - Course-level score distributions
- **Multi-Sheet Excel Reporting** — Formatted `.xlsx` workbooks generated via openpyxl containing master ledgers, subject summaries, and rank lists.
- **Modern Dark-Themed GUI** — Clean, hardware-accelerated desktop interface built with CustomTkinter.
- **Portable & Smart App Control Immune** — Ships with a zero-installation portable edition bundled with signed Windows binaries to bypass Windows SmartScreen / Smart App Control warnings.

---

## Tech Stack

| Component | Technology | Purpose |
| :--- | :--- | :--- |
| **User Interface** | [CustomTkinter](https://github.com/TomSchimansky/CustomTkinter) | Modern hardware-accelerated desktop UI |
| **PDF Extraction Engine** | [PyMuPDF](https://pymupdf.readthedocs.io/) | High-speed offline tabular PDF text & mark extraction |
| **Data Processing** | [Pandas](https://pandas.pydata.org/) & [NumPy](https://numpy.org/) | In-memory data transformation, aggregation, and statistics |
| **Visualizations** | [Matplotlib](https://matplotlib.org/) | Statistical charts embedded directly into the application |
| **Spreadsheet Engine** | [openpyxl](https://openpyxl.readthedocs.io/) | Automated multi-tab formatted Excel export generation |
| **Packaging & Distribution** | [PyInstaller](https://pyinstaller.org/) | Standalone Windows executable, portable folder, and setup installer |

---

## Project Structure

```
ScoreLens/
├── src/
│   ├── main.py                     # Application entry point
│   ├── core.py                     # Core data models, extraction, and aggregation logic
│   ├── backend.py                  # PDF parser and tabular data extraction engine
│   ├── excel_exporter.py           # Multi-sheet Excel workbook generator
│   └── ui/                         # CustomTkinter interface modules
│       ├── main_window.py          # Main window navigation and lifecycle
│       ├── dashboard_view.py       # Executive metrics and class overview
│       ├── students_view.py        # Student record grid and search
│       ├── subjects_view.py        # Subject-level analysis view
│       ├── toppers_view.py         # Rank list and top performers
│       ├── failures_view.py        # Backlog and failure analysis
│       ├── backlog_view.py         # Backlog summary view
│       ├── upload_view.py          # File selection and progress screen
│       ├── export_view.py          # Excel export configuration
│       ├── charts.py               # Matplotlib chart rendering
│       ├── components.py           # Reusable UI widgets
│       └── theme.py                # Colors, styles, and fonts
├── scripts/
│   ├── build.ps1                   # Packaging pipeline (app folder, portable edition, setup installer)
│   ├── installer.py                # Self-extracting setup logic
│   └── generate_architecture_pdf.py # Architecture report generator
├── dist/                           # Compiled binaries and distribution packages
│   ├── ResultAnalyzerSetup.exe     # Standalone self-extracting Windows installer
│   ├── ResultAnalyzer-Portable/    # Zero-install portable folder (SAC-immune)
│   │   ├── Start Result Analyzer.bat # Launcher utilizing signed pythonw runtime
│   │   ├── Create Desktop Shortcut.bat # Generates Desktop shortcut with app icon
│   │   ├── app.pyw                 # Portable application entrypoint
│   │   └── _internal/              # Standalone Python runtime & bundled dependencies
│   └── ResultAnalyzer-Portable.zip # Ready-to-distribute portable zip archive
├── assets/                         # Application icons and branding assets
├── requirements.txt                # Python runtime dependencies
├── ResultAnalyzer.spec             # PyInstaller build specification
├── .gitignore                      # Ignored files and build artifacts
└── README.md                       # Project documentation
```

---

## Downloads & Distribution Options

ScoreLens provides two ready-to-run Windows options generated in the `dist/` folder:

### 1. Portable Edition (`dist/ResultAnalyzer-Portable.zip`) — *Recommended for End Users*
* **Zero Installation Required:** Extract the zip anywhere (e.g., Desktop or USB drive) and run immediately without administrative privileges.
* **Launch:** Double-click `Start Result Analyzer.bat`.
* **Smart App Control (SAC) Immune:** Packaged with signed Python runtime binaries (`pythonw.exe`) to prevent untrusted executable blocks from Windows SmartScreen or Smart App Control.
* **Desktop Shortcut Utility:** Run `Create Desktop Shortcut.bat` inside the folder to automatically create a clean desktop shortcut with the application's logo.

### 2. Standalone Setup Installer (`dist/ResultAnalyzerSetup.exe`)
* Single-file executable installer that automatically unpacks and installs ScoreLens to the system.

---

## Getting Started

### Prerequisites

- **Python 3.10** or higher
- **Windows OS** (64-bit recommended)

### Running from Source

1. **Clone the repository:**
   ```bash
   git clone https://github.com/SahilPathan18/Score-Lens.git
   cd Score-Lens
   ```

2. **Create and activate a virtual environment:**
   ```powershell
   python -m venv venv
   .\venv\Scripts\Activate.ps1
   ```

3. **Install dependencies:**
   ```bash
   pip install -r requirements.txt
   ```

4. **Launch ScoreLens:**
   ```bash
   python src/main.py
   ```

---

## Packaging & Building (`dist/`)

The automated PowerShell build script compiles both the portable edition and the standalone installer in a single command:

```powershell
powershell -ExecutionPolicy Bypass -File scripts\build.ps1
```

### What `build.ps1` Generates:
1. **`dist/ResultAnalyzer/`** — Standard compiled PyInstaller folder.
2. **`dist/ResultAnalyzerSetup.exe`** — Single-file self-extracting desktop setup installer.
3. **`dist/ResultAnalyzer-Portable/`** — Portable version bundled with signed runtime binaries and launch batch files.
4. **`dist/ResultAnalyzer-Portable.zip`** — Compressed portable archive ready for distribution via GitHub Releases.

---

## Usage Workflow

1. **Upload Ledger**: Launch ScoreLens and click **Upload PDF** to select a Bangalore University Tabulation Register ledger.
2. **Instant Ingestion**: The engine parses the PDF offline and populates the database in seconds.
3. **Explore Insights**:
   - **Dashboard**: Review class pass percentage, average SGPA, and summary cards.
   - **Toppers**: Inspect the rank list and top performers.
   - **Students**: Search by USN or name, inspect marks, and filter by status.
   - **Subjects**: Review pass rates and scoring difficulty for each subject.
   - **Backlogs**: Identify students with pending backlogs for academic counseling.
4. **Export**: Click **Export to Excel** to produce formatted departmental spreadsheets.

---

## Contributing & License

Contributions, issues, and feature requests are welcome! Feel free to check the [issues page](https://github.com/SahilPathan18/Score-Lens/issues).

This project is open-source and available under the [MIT License](LICENSE).
