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

## Downloads

Download the latest release from:

- `https://github.com/9elmaz9/batch-folder-sorter/releases`

Choose the file that matches your system:

- `BatchFolderSorter-macos-arm64.zip`
  For Apple Silicon Macs (`M1`, `M2`, `M3`, `M4`)
- `BatchFolderSorter-macos-x86_64.zip`
  For Intel Macs
- `BatchFolderSorter-windows-x64.zip`
  For 64-bit Windows systems
- `checksums.txt`
  SHA256 checksums for release verification

## First Launch

### macOS

1. Download the correct macOS zip.
2. Unzip it.
3. Move `BatchFolderSorter.app` to `Applications` if desired.
4. If macOS blocks the app on first launch:
   Open `System Settings -> Privacy & Security` and allow the app to run.

Note:

- The app is not notarized yet, so the first launch may require manual confirmation in macOS.

### Windows

1. Download `BatchFolderSorter-windows-x64.zip`.
2. Unzip it.
3. Open the extracted `BatchFolderSorter` folder.
4. Run the application executable.

If Windows SmartScreen appears, choose the option to continue only if you trust the release source.

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

## Automated Builds

GitHub Actions is configured to build release artifacts for:

- `macOS arm64`
- `macOS x86_64`
- `Windows x64`

Manual build workflow:

- Open the `Actions` tab in GitHub
- Run `Build And Release`
- Download the generated artifacts

Tag-based release workflow:

```bash
git tag v1.0.0
git push origin v1.0.0
```

When a tag like `v1.0.0` is pushed, GitHub Actions will:

- build all three platform artifacts
- create or update a GitHub Release
- upload the zip files
- upload `checksums.txt`

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
