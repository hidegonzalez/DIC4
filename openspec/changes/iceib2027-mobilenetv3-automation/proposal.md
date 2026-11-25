# Change Proposal: `iceib2027-mobilenetv3-automation`

## Why
The user needed to populate the `ICEIB2027-IEEE` starter template with a real AI paper, deploy and compile it on Overleaf without manual intervention, record the browser workflow, document all troubleshooting steps and reusable Agent instructions, and publish everything to a new GitHub repository (`DIC4`) in OpenSpec format.

## Scope
### In-Scope
- Populate `ICEIB2027-IEEE/` with verified MobileNetV3 / MobileNetV2 content and build `ICEIB2027-IEEE-MobileNetV3.zip`.
- Set up Chrome, Node.js LTS, and `chrome-devtools-mcp` (`--autoConnect`).
- Deploy and compile on Overleaf via Blank Project + web editor population.
- Create GitHub repository `DIC4` and push all artifacts, recording, `README.md`, `conversation_export.md`, and `openspec/` specs.

### Out-of-Scope
- Generating custom vector diagrams for `figures/architecture.pdf` (placeholder retained).
- Bypassing MCP `upload_file` workspace-root security checks.
