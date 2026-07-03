# Riposte — companion service downloads

This repo hosts the Windows installer for the **Riposte** companion service —
the local background app that the [Riposte Chrome extension](https://chromewebstore.google.com/)
talks to in order to generate LinkedIn reply suggestions using **your own
Claude subscription** (not a billed API, and not anyone else's account).

Riposte doesn't run your AI usage through a shared server. Instead, this
small Windows app runs on your own PC, using your own `claude` CLI login, so
your Claude usage stays yours — no per-request billing to the extension's
developer, no third party in the loop.

## Install

1. Download the latest release below and unzip it.
2. Make sure you have:
   - **Windows 10 or 11**
   - **Node.js** (to install the Claude Code CLI): https://nodejs.org
   - A **Claude Pro or Max subscription**
3. Install the Claude Code CLI and log in with your own subscription:
   ```
   npm install -g @anthropic-ai/claude-code
   claude login
   ```
4. Run `Install-Riposte.ps1` (right-click → Run with PowerShell, or open
   PowerShell in the extracted folder and run
   `powershell -ExecutionPolicy Bypass -File Install-Riposte.ps1`).
5. It'll print a **pairing code** — copy it.
6. Install the Riposte extension from the Chrome Web Store, click its
   toolbar icon, paste the pairing code under "Pairing code", and click Save.

That's it — the service now starts automatically every time you log in to
Windows.

## Uninstall

Run `Uninstall-Riposte.ps1` from the same folder. This stops the service and
removes its auto-start entry. Your pairing code and logs stay at
`%LOCALAPPDATA%\Riposte` in case you reinstall later.

## A note on the SmartScreen warning

Windows will likely show "Windows protected your PC" the first time you run
`Riposte.exe` or the installer — this is standard for any app that isn't
digitally code-signed, not a sign of a problem. Click **More info** → **Run
anyway** to proceed.

## Platform support

Windows only for now. Mac/Linux support may come later if there's demand.

## Source

The extension and service source code are maintained privately. This repo
exists solely to host built release downloads.
