# OpenSpec Agent Instructions (`openspec/AGENTS.md`)

This repository follows **OpenSpec** (Spec-Driven Development). Any AI agent working in this repository MUST read `openspec/project.md` and the relevant `openspec/specs/<capability>/spec.md` files before making changes.

## Standard Agent Execution SOP (End-to-End Pipeline)

### 1. LaTeX Paper Population (`openspec/specs/latex-paper-pipeline/spec.md`)
- Inspect `ICEIB2027-IEEE/` (`main.tex`, `references.bib`, `sections/*.tex`, `tables/*.tex`).
- Populate sections only with verified, citation-backed content and metrics; never fabricate experimental results.
- Package `ICEIB2027-IEEE\*` into `ICEIB2027-IEEE-MobileNetV3.zip` without overwriting `ICEIB2027-IEEE.zip`.

### 2. Chrome + `chrome-devtools` MCP Setup (`openspec/specs/chrome-mcp-setup/spec.md`)
- On Windows, if `winget install Google.Chrome` hangs or hits `msstore` timeout (`0x80072ee2`) / lock (`0x80070020`), download `https://dl.google.com/chrome/install/latest/chrome_installer.exe` via `curl.exe` and run the interactive installer.
- Install **Node.js LTS** (`winget install --id OpenJS.NodeJS.LTS -e --source winget --accept-package-agreements --accept-source-agreements`).
- Configure `~/.gemini/config/mcp_config.json` with `C:\Program Files\nodejs\npx.cmd` and `["-y", "chrome-devtools-mcp@latest", "--autoConnect"]`, then restart Antigravity.
- Ensure Chrome remote debugging is enabled at `chrome://inspect/#remote-debugging` and `%LOCALAPPDATA%\Google\Chrome\User Data\DevToolsActivePort` exists before calling `list_pages`.

### 3. Overleaf Deployment (`openspec/specs/overleaf-deployment/spec.md`)
- Never bypass `upload_file` workspace-root restrictions.
- If `upload_file` returns `Access denied`, create a **Blank Project** on Overleaf (`https://www.overleaf.com/project`), create `sections/` and `tables/` folders, populate all 9 `.tex`/`.bib` files directly in the web editor, verify `Compiler = pdfLaTeX` and `Main document = main.tex`, and run **Recompile** (0 errors).

### 4. GitHub Sync (`openspec/specs/github-sync/spec.md`)
- Use the `browser` subagent to create an empty repository at `https://github.com/new` and configure its About description.
- Use local Git CLI (`git init -b main`, `git add .`, `git commit`, `git push -u origin main`) to push the workspace.
