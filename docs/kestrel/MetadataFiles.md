# `_MMD.txt` File Schema

This document defines the text format for `_MMD` metadata files.
Kestrel is not able to directly integrate into other CAD platforms.
In order to migrate files with metadata into Onshape, temporary plain text metadata files need to be generated.
The files need to be created in "%appdata%/SmartBench Software/" path.
Kestral will read the runfile to find files, and the metadata files in order to upload to Onshape.

Users may either use the provided macro to generate _MMD files, or use their own methods.

## File naming

Use this naming pattern:

`<original-file-name-with-dots-replaced-by-underscores>_MMD.txt`
Files must be place in the "%appdata%/SmartBench Software/" path.

Example:

- Original CAD file: `Gearbox.sldasm`
- Metadata file: `Gearbox_sldasm_MMD.txt`

Note that the extension remains within the filename.

## Format rules

- Plain text file
- One record per line
- Records are identified by fixed prefixes
- Values are unquoted
- Windows paths should be written as full paths when applicable

## Line types

### 1) File path record

```text
---FILEPATH---<source file full path>
```

Use once to identify the source file.

---

### 2) Property record

```text
---PROPERTY===<property name>---VALUE===<property value>
```

Use for metadata properties not specific to a configuration (ie custom properties).
If a property is not found in the configured properties, Kestrel will default to these non-configured properties.

---

### 3) End-of-properties marker

```text
---ENDPROPERTIES---
```

Marks the end of normal property records.

---

### 4) Configuration file path record (optional)

```text
---CONFIGURATION===<configuration name>---PATH===<configuration-specific file path>
```

Use for files that have multiple configurations.
Configured files must have each configuration as a separate file. Each file needs to have the target configuration saved as the active configuration.
Onshape uploads will only look at the active configuration.

---

### 5) Configuration property record (optional)

```text
---CONFIGUREDPROP===<configuration name>---PROPERTY===<property name>---VALUE===<property value>
```

Use when a property value is specific to one configuration.

---

### 6) Configuration-specific component record (optional)

```text
---CONFIGUREDCOMP===<parent configuration name>---COMPONENT===<component name>---PATH===<component file path>---COMPCONFIG===<component configuration>---TRANSFORM===<16 comma-separated transform values>
```

All component lists are defined by configuration - including a default configuration.
All files are uploaded to Onshape with a configuration included.

---

### 7) Drawing PDF path record (optional, drawing files)

```text
---PDF===<exported PDF full path>
```

Use for drawing metadata when a PDF export path is available.

## Minimal valid `_MMD` examples

### Part (minimal)

```text
---FILEPATH---C:\CAD\Bracket.sldprt
---PROPERTY==={filename}---VALUE===Bracket.sldprt
---ENDPROPERTIES---
```

### Drawing with PDF

```text
---FILEPATH---C:\CAD\Bracket.slddrw
---PROPERTY==={filename}---VALUE===Bracket.slddrw
---ENDPROPERTIES---
---PDF===C:\CAD\Bracket.pdf
```

### Assembly with one component

```text
---FILEPATH---C:\CAD\TopLevel.sldasm
---PROPERTY==={filename}---VALUE===TopLevel.sldasm
---ENDPROPERTIES---
---CONFIGUREDCOMP===default---COMPONENT===PartA-1---PATH===C:\CAD\PartA.sldprt---COMPCONFIG===Default---TRANSFORM===1,0,0,0,0,1,0,0,0,0,1,0,0,0,0,1

```
