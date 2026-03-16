# Batch Folder Sorter

Desktop tool for preparing ingest batches from CSV metadata.

The app supports two workflows:

- `Standard mode`
  Sorts files by `Mapnaam` from the CSV into `ROOT/<IE>/<extension>/`.
- `Artwork batch mode`
  Matches artwork-style filenames to IE identifiers from the CSV and sorts them into:
  `ROOT/<IE>/Bewerkt_8bit/` and `ROOT/<IE>/Masters_16bit/`.

## Features

- Desktop GUI built with `PySide6`
- Background processing with responsive UI
- CSV validation before moving files
- `_EXTRA_FILES` handling for unmatched files
- `Undo` for the last successful batch
- PyInstaller spec for packaging

## Requirements

- Python 3.9+

Install dependencies:

```bash
python3 -m venv venv_gui
source venv_gui/bin/activate
pip install -r requirements.txt
```

## Run

```bash
source venv_gui/bin/activate
python gui.py
```

## Build

```bash
source venv_gui/bin/activate
pyinstaller BatchFolderSorter.spec
```

## CSV

The CSV must contain a `Mapnaam` column.

Example:

```csv
Mapnaam
24
25
26
```

## Notes

- `Artwork batch mode` keeps original filenames.
- `Undo` restores the last successful batch only.
- The repository ignores local builds, test samples, and virtual environments.
