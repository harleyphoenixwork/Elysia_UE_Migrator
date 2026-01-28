# Elysia Migrator (The "Nuclear Option")

**An external, crash-free asset restructuring tool for bloated Unreal Engine projects.**

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![Platform](https://img.shields.io/badge/Platform-Windows-blue.svg)](https://www.python.org/)

### CRITICAL WARNING
**This tool acts externally on your project files.** It is designed for projects that are too fragile or bloated to reorganize inside the Unreal Editor.
* **ALWAYS BACK UP YOUR PROJECT** (Zip or Source Control) before running this.
* I am not responsible for data loss or broken references.
* This tool is provided "AS-IS" under the MIT License. **Use at your own risk.**

---

## Why Elysia?
Restructuring a 5-year-old Unreal project is a nightmare. Moving a single `GameInstance` or `PlayerController` can cause the Editor to hang for hours or crash entirely due to reference spaghetti.

**Elysia solves this by going around the Editor.**
It calculates moves externally, physically reorganizes your `.uasset` files on the disk, and automatically injects `[CoreRedirects]` into your config. When you restart Unreal, the engine repairs the links for you.

### Key Features
* **Nuclear Migration:** Move 15,000+ assets in seconds without opening the Editor.
* **Crash-Free:** Bypasses Unreal's asset management completely during the move process.
* **Auto-Redirects:** Automatically scans moves and appends the necessary `CoreRedirects` to your `DefaultEngine.ini`.
* **Smart Sorting:** Detects asset packs (Synty, Megascans) and keeps them clustered, while organizing loose files into a clean `ElysiaFramework` structure.
* **Legacy Archiving:** Optional date-based sorting to move unused assets into a `_Legacy` folder.
* **Undo / Restore:** Includes a **Reverse Migration** mode that reads the generated CSV logs to revert files to their original locations.

---

## 📋 The Workflow

1.  **Get References:** Open your project (before closing it), select the messy folders/assets in the Content Browser, press `Ctrl+C`.
2.  **Close Unreal Engine.** (Mandatory).
3.  **Run Elysia:** Select your Project Root and paste the references.
4.  **Dry Run:** Check the log to see where files will go.
5.  **Execute:** The tool will move files and create a CSV log.
6.  **Inject Config:** Click "Auto-Inject to DefaultEngine.ini" to save the redirects.
7.  **Clean Up:** Go to your project folder and delete the `Intermediate` and `Saved` folders. (This forces UE to rebuild the Asset Registry).
8.  **Restart Unreal Engine.**

---

## How to Undo (Reverse Migration)
If the result isn't what you expected:
1.  Relaunch Elysia.
2.  Click **"↺ Reverse / Undo Migration"** on the first screen.
3.  Select the `Elysia_Log_yyyymmdd.csv` file created during the operation.
4.  The tool will move files back and attempt to strip the redirects from your INI.

---

## Contributing
I built this tool to save my own time-starved project. I do not provide active support, but i will try to make improvements as i'm available.

## Support
If this tool saved your project from development hell, consider buying me a coffee!

[![ko-fi](https://ko-fi.com/img/githubbutton_sm.svg)](YOUR_KO_FI_LINK_HERE)
