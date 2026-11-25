# Project Context (`openspec/project.md`)

## Overview
`DIC4` is an end-to-end automated workflow project for populating an **ICEIB 2027 IEEEtran** conference paper template (`ICEIB2027-IEEE/`), deploying and compiling it on **Overleaf**, recording the browser automation, exporting the full troubleshooting & conversation log, and publishing the workspace to **GitHub**.

## Tech Stack & Environment
- **OS**: Windows (PowerShell 5.1)
- **Document Format**: LaTeX (`IEEEtran` conference class, `pdfLaTeX`, TeX Live 2026 on Overleaf)
- **Browser Automation**: Google Chrome (Remote Debugging via `chrome://inspect/#remote-debugging`) + `chrome-devtools-mcp@latest` (`--autoConnect`) + Node.js LTS (`v26.13.1`)
- **Version Control**: Git CLI (`git init`, `git push`) + GitHub Web UI

## Conventions & Constraints
1. **No Fabricated Results**: Any AI paper content populated into `ICEIB2027-IEEE/` MUST cite verified published sources (e.g., Howard et al., ICCV 2019; Sandler et al., CVPR 2018) and explicitly label sample entries.
2. **Respect Sandbox / Access Boundaries**: Never bypass `chrome-devtools` MCP `upload_file` workspace-root restrictions; use sanctioned UI workflows (Overleaf **Blank Project** + web editor) or local Git CLI instead.
3. **UTF-8 Encoding**: All Markdown exports and LaTeX files MUST be saved as UTF-8 without BOM.
