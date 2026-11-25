# Specification: `chrome-mcp-setup`

## Purpose
Define the Windows installation and configuration steps required for Antigravity's `browser` subagent to control an already-logged-in Google Chrome session.

## Requirements

### Requirement: Chrome & Remote Debugging Readiness
The system SHALL ensure Google Chrome is installed and remote debugging is enabled so `DevToolsActivePort` is available.

#### Scenario: Winget Download Stalls or Fails
- **GIVEN** `winget install Google.Chrome` hangs, times out on `msstore`, or hits file lock `0x80070020`
- **WHEN** installing Chrome on Windows
- **THEN** the agent SHALL fall back to downloading `https://dl.google.com/chrome/install/latest/chrome_installer.exe` via `curl.exe` and launch the interactive installer for UAC confirmation.

#### Scenario: DevToolsActivePort Verification
- **WHEN** Chrome remote debugging is enabled via `chrome://inspect/#remote-debugging`
- **THEN** `%LOCALAPPDATA%\Google\Chrome\User Data\DevToolsActivePort` MUST exist before invoking `list_pages`.

### Requirement: Node.js & Global MCP Configuration
The system SHALL install Node.js LTS and configure `~/.gemini/config/mcp_config.json` for `chrome-devtools-mcp`.

#### Scenario: Configure `chrome-devtools` MCP
- **GIVEN** `chrome-devtools-plugin` only bundles skills without `.mcp.json`
- **WHEN** Node.js LTS is installed
- **THEN** `~/.gemini/config/mcp_config.json` MUST define `chrome-devtools` using `C:\Program Files\nodejs\npx.cmd` with `["-y", "chrome-devtools-mcp@latest", "--autoConnect"]`, followed by an Antigravity restart.
