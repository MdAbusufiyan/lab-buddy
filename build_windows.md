# Windows Build Instructions

This document describes how the LAB Buddy Windows executable is built.
It is intended for maintainers and reviewers.

## Build Environment
- Operating System: Windows 10 / 11
- Python Version: 3.11
- Build Tool: PyInstaller

## Dependencies
Install dependencies before building:

## Build Command
From the repository root:

## Output
- The compiled executable is generated in the `dist/` directory.
- The executable is distributed via GitHub Releases.
- The executable is not committed to the repository.

## Notes
- Tkinter is bundled with Python and does not require separate installation.
- The build process does not include auto-update functionality.
