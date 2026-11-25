# Specification: `overleaf-deployment`

## Purpose
Define how the LaTeX project is deployed and compiled on Overleaf via the `browser` subagent.

## Requirements

### Requirement: Sanctioned Overleaf Deployment
The system SHALL deploy the LaTeX project to Overleaf and verify `pdfLaTeX` compilation without bypassing `upload_file` sandbox restrictions.

#### Scenario: `upload_file` Access Denied Workaround
- **GIVEN** `upload_file` fails with `Access denied: path ... is not within any of the configured workspace roots`
- **AND** the user cannot perform manual file selection
- **WHEN** deploying to `https://www.overleaf.com/project`
- **THEN** the `browser` subagent SHALL create a **Blank Project** (`ICEIB2027-IEEE-MobileNetV3`), create `sections/` and `tables/` folders, populate all 9 `.tex`/`.bib` files directly in the web editor, verify `Compiler = pdfLaTeX` and `Main document = main.tex`, and run **Recompile** until 0 errors are confirmed.
