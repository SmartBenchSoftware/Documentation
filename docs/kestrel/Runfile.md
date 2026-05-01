# Runfile Schema

Kestrel utilizes a runfile to manage the metadata extraction and Onshape migration process.
The runfile is a plain text file that any program can edit in order for Kestrel to locate files.
Any metadata extraction process will need to modify or generate the runfile in the format described below.

This document describes the text format used by for `runfile.txt`.

- File name: `runfile.txt`
- Location: `%appdata%/SmartBench Software/runfile.txt`
- Format: line-based text with section headers and prefixed entries

## High-level layout

A valid runfile is written in this order:

1. `---OPTIONSSTART===`
2. Option lines (`KEY=VALUE`)
3. `---OPTIONSEND===`
4. `---FILES`
5. File entry lines

### Example

```
---OPTIONSSTART===
IGNORETOOLBOX=True
UNSUPRESSASSEMBLY=False
DRAWINGSASPDFvDXF=True
---OPTIONSEND===
---FILES
C:\CAD\part1.sldprt
---EXTRACTED===C:\CAD\asm1.sldasm
---MIGRATED===C:\CAD\drawing1.slddrw
---ERROR===C:\CAD\broken.sldprt
---SKIPPED===C:\CAD\skipme.step
```

## Sections

## 1) Options section

### Start/End markers

- Start: `---OPTIONSSTART===`
- End: `---OPTIONSEND===`

### Option lines

Each line is `KEY=VALUE`.


- `IGNORETOOLBOX`
- `UNSUPRESSASSEMBLY`
- `DRAWINGSASPDFvDXF`

## 2) Files section

### Marker

- `---FILES`

All lines after this marker are interpreted as file items.

### Entry types

- **Pending** (no prefix):
  - `C:\path\file.ext`
- **Ready / Extracted**:
  - `---EXTRACTED===C:\path\file.ext`
- **Migrated**:
  - `---MIGRATED===C:\path\file.ext`
- **Error**:
  - `---ERROR===C:\path\file.ext`
- **Skipped**:
  - `---SKIPPED===C:\path\file.ext`



  Kestrel will update the runfile as it processes files, changing their status by adding the appropriate prefix.
  Kestrel only uploads files in the `---EXTRACTED===` state, which indicates they are ready for upload to Onshape.
