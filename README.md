# everything-find

A skill for OpenCode that enables rapid file search on Windows using Everything's `es.exe` CLI.

## What This Skill Does

Enables AI agents to quickly locate files by name, path, extension, size, or modification date using the Everything search engine.

## Prerequisites

1. **Download and install Everything**: https://www.voidtools.com/downloads/
2. **Download ES (CLI)**: From the same page, scroll to "ES (Command line interface)" section and download `es.exe`
3. **Add es.exe to PATH**: Move es.exe to a directory in your system PATH
4. **Everything must be running** in the background for IPC to work

## Installation

```bash
npx skills add wsaaaqqq/everything-find
```

Or install directly from GitHub:

```bash
npx skills add https://github.com/wsaaaqqq/everything-find
```

## Usage Examples

```bash
# Find files by name
es *.py -n 20

# Find in specific path
es opencode -path "C:\Projects" -n 50

# Largest files recently modified
es * -sort dm -n 10

# Only files (no directories)
es <search> /a-d
```

## For AI Agents

When installed, this skill provides AI agents with:
- Complete `es.exe` command syntax
- Search patterns (by extension, path, size, date)
- Filtering options (files only, directories only, attributes)
- Export formats (CSV, TXT, EFU)
- Troubleshooting guide

See [SKILL.md](./SKILL.md) for full documentation.
