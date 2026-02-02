# Fabrication Material List Generator

An automated desktop application that streamlines the generation of fabrication material lists from CAD data. This tool is designed to process electrical tray, hanger, and bracket information from fabrication files and produce comprehensive material reports.

## 🎯 Overview

**Fabrication Material List Generator** (PyAutoFab) automates the tedious process of extracting and organizing material requirements from fabrication project files. It provides a user-friendly GUI interface for drag-and-drop file processing, validation, and automated report generation.

## ✨ Key Features

- **Drag-and-Drop Interface** - Simply drag files into the application for processing
- **Automated Data Extraction** - Intelligently parses CAD data files to extract material information
- **Multi-Component Support** - Handles electrical trays, hangers, and brackets
- **File Validation** - Validates input files for correct format and data integrity
- **Batch Processing** - Process multiple files efficiently
- **Excel Integration** - Exports results to Excel format using xlwings
- **Real-Time Feedback** - Visual progress indicators during processing
- **Windows Integration** - Native Windows application with system tray support

## 📋 Prerequisites

- **Python** 3.7 or higher
- **Windows** operating system (uses Windows COM for Excel integration)
- Dependencies listed in `requirements.txt`

## 🚀 Installation

### 1. Clone the Repository
```bash
git clone <repository-url>
cd Fabrication-Material-List-Generator
```

### 2. Install Dependencies
```bash
pip install -r requirements.txt
```

### 3. Generate GUI Resources
```bash
pyside6-rcc resources.qrc -o resources_rc.py
```

## 💻 Usage

### Running the Application

**Option 1: Direct Python**
```bash
python app.py
```

**Option 2: Using Main Entry Point**
```bash
python main.py
```

### Workflow

1. **Launch the Application** - Start the GUI application
2. **Drag Input File** - Drop a fabrication data file (`.txt` format) into the designated area
3. **Automatic Validation** - The system validates the file format and structure
4. **Processing** - Click "Process" or the application auto-processes the file
5. **Output** - Material lists are generated and saved to the output folder
6. **Excel Export** - Results are formatted and exported to Excel

### Input File Format

Input files should follow the naming convention:
```
{SHIP}_{SPACE_TYPE}_{AREA}.txt
```

Example: `SC407_CW_ER.txt`
- `SC407` - Ship identifier
- `CW` - Space type
- `ER` - Area designation

## 📁 Project Structure

```
├── app.py                          # Main application entry point
├── gui/
│   ├── main_window.ui             # Qt Designer UI file
│   └── ui_main_window.py          # Generated UI classes
├── modules/
│   ├── dragdrop/
│   │   └── drag_and_drop.py       # Drag-and-drop functionality
│   ├── verify/
│   │   ├── verify_dropped.py      # File validation logic
│   │   └── input_checker.py       # Data integrity checks
│   ├── transform/
│   │   └── transform_data.py      # CAD data parsing and transformation
│   ├── file_manager/
│   │   └── manage.py              # File operations and management
│   └── threads/
│       └── thfl_process.py        # Main processing thread
├── data/
│   ├── _raw_data_input_copy/      # Backup of raw input files
│   ├── _thfl_output_files/        # Generated output files
│   ├── _verification_data/        # Validation intermediate files
│   └── _template_files/           # Template files for output
└── resources.qrc                   # Qt resource file
```

## 🔧 Core Modules

### Transform Module (`modules/transform/transform_data.py`)
Parses raw CAD data and extracts:
- **Electrical Trays** - Size, lugs, rotation angle information
- **Hangers** - Size, height, type, and length specifications
- **Brackets** - Support codes and numbering

### Verify Module (`modules/verify/`)
- Validates file format and naming conventions
- Checks data structure and required fields
- Ensures file compatibility

### File Manager (`modules/file_manager/manage.py`)
- Organizes input and output files
- Manages file paths and directory structures
- Handles file copying and organization

### Thread Processing (`modules/threads/thfl_process.py`)
- Executes main processing pipeline
- Manages multi-step transformations
- Coordinates between modules

## 📦 Dependencies

- **PySide6** - Modern Qt6 Python bindings for the GUI
- **pandas** - Data manipulation and analysis
- **numpy** - Numerical computing
- **xlwings** - Excel integration and automation
- **pywin32** - Windows COM interface

See `requirements.txt` for complete dependency list with versions.

## 🛠️ Development

### Building Executable
The project uses PyInstaller for creating standalone executables:
```bash
pyinstaller Py-AutoFab.spec
```

### GUI Updates
If you modify the Qt Designer UI file:
```bash
pyside6-uic gui/main_window.ui -o gui/ui_main_window.py
pyside6-rcc resources.qrc -o resources_rc.py
```

## 📝 Example Data Files

Sample input files are provided in `data/` directory:
- `SC405_CW_ACC.txt` - Example file format
- `SC405_CW_ER.txt` - Another example

Use these as reference for your input file structure.

## 🐛 Troubleshooting

### Issue: "INVALID FILE FORMAT"
- Check that your file follows the naming convention: `{SHIP}_{TYPE}_{AREA}.txt`
- Ensure the file is a valid text file with proper CAD data structure

### Issue: Excel Integration Fails
- Verify Microsoft Excel is installed on your system
- Check that `xlwings` is properly installed
- Ensure Windows COM services are properly initialized

### Issue: Import Errors
- Regenerate Qt resources: `pyside6-rcc resources.qrc -o resources_rc.py`
- Reinstall dependencies: `pip install -r requirements.txt --upgrade`

## 📄 License

See LICENSE file for details.

## 👨‍💻 Author

**jlendio** - Initial development and maintenance

## 📞 Support

For issues, questions, or contributions, please open an issue in the repository.

---

**Last Updated**: February 2026