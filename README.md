# Score-Lens

A high-performance, 100% offline desktop application built to parse, analyze, and visualize Bangalore University Tabulation Register PDF ledgers. Upload a university marksheet ledger to generate an interactive analytics dashboard featuring student rankings, subject-level breakdowns, statistical grade distributions, and multi-sheet Excel exports.

[![Python](https://img.shields.io/badge/Python-3.10+-3776AB?logo=python&logoColor=white)](https://www.python.org/)
[![UI-CustomTkinter](https://img.shields.io/badge/UI-CustomTkinter-2e8b57)](https://github.com/TomSchimansky/CustomTkinter)
[![Platform](https://img.shields.io/badge/Platform-Windows-0078D6?logo=windows&logoColor=white)](https://github.com/SahilPathan18/Score-Lens)

![Score-Lens Dashboard Preview](assets/dashboard_preview.png)

---

## Features

- **High-Speed PDF Ingestion** — Automated parsing of student metadata, USN, course marks, SGPA, and CGPA from dense PDF registers using PyMuPDF.
- **100% Offline & Private** — Operates entirely locally with zero cloud dependencies; student records stay secure on your machine.
- **Analytics Dashboard** — Instant class pass rates, average SGPA/CGPA, semester toppers, and embedded Matplotlib visual distributions.
- **Student Record Explorer** — Instant search by Student Name or Register Number (USN) with multi-attribute filtering (PASS, FAIL, PROMOTED).
- **Subject-Wise Breakdown** — Granular course analysis covering pass percentages, averages, and backlog lists.
- **Multi-Sheet Excel Export** — Direct generation of formatted `.xlsx` workbooks containing master ledgers, subject summaries, and rank lists via openpyxl.

---

## Quick Start

### 1. Portable Edition (No Python Required)
1. Download or build `ResultAnalyzer-Portable.zip`.
2. Extract the archive.
3. Double-click **`Start Result Analyzer.bat`** to run.
*(Optional: Run `Create Desktop Shortcut.bat` inside the folder to add a desktop shortcut with the app icon).*

### 2. Run from Source

**Prerequisites:** Python 3.10+ on Windows.

```bash
# Clone the repository
git clone https://github.com/SahilPathan18/Score-Lens.git
cd Score-Lens

# Create and activate virtual environment
python -m venv venv
.\venv\Scripts\Activate.ps1

# Install dependencies and run
pip install -r requirements.txt
python src/main.py
```

---

## Building Packages (`dist/`)

To compile the standalone setup installer (`ResultAnalyzerSetup.exe`) and the zero-install portable zip (`ResultAnalyzer-Portable.zip`):

```powershell
powershell -ExecutionPolicy Bypass -File scripts\build.ps1
```

All compiled binaries will be generated in the `dist/` directory.

---

## Tech Stack

- **UI:** [CustomTkinter](https://github.com/TomSchimansky/CustomTkinter)
- **PDF Extraction:** [PyMuPDF](https://pymupdf.readthedocs.io/)
- **Data Processing:** [Pandas](https://pandas.pydata.org/) & [NumPy](https://numpy.org/)
- **Visualizations:** [Matplotlib](https://matplotlib.org/)
- **Excel Generation:** [openpyxl](https://openpyxl.readthedocs.io/)
- **Packaging:** [PyInstaller](https://pyinstaller.org/)
