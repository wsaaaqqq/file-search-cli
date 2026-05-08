---
name: everything-find
description: Use when needing to quickly locate files on Windows by name, path, extension, size or date modified
---

# Everything Find

## Overview

Use Everything's `es.exe` CLI to rapidly search for files by name, path, extension, size, or modification date. Requires Everything to be running.

## Prerequisites

1. **Download and install Everything**: https://www.voidtools.com/zh-cn/downloads/
2. **Download ES (CLI)**: From the same page, scroll to "ES (Command line interface)" section and download `es.exe`
3. **Add es.exe to PATH**: Move es.exe to a directory in your system PATH, or use full path
4. **Everything must be running** in the background for IPC to work

## Quick Reference

```bash
# Basic search (finds files containing text in name)
es.exe <search_term>

# Find by extension
es.exe *.pdf
es.exe *.py

# Limit results
es.exe <search> -n 20

# Sort results
es.exe <search> -sort size       # by size (largest first)
es.exe <search> -sort dm         # by date modified
es.exe <search> -sort name       # by name (default)

# Search in specific path
es.exe <search> -path "C:\Projects"

# Only files or only folders
es.exe <search> /a-d              # files only
es.exe <search> /ad              # directories only

# Regex search
es.exe -r "file\d+\.txt"

# Case sensitive
es.exe -i "MyFile"

# Show only results with path
es.exe <search> -p

# Export formats
es.exe <search> -csv > results.csv
es.exe <search> -txt > results.txt
es.exe <search> -efu results.efu

# Combine options
es.exe "*.py" -path "C:\src" -n 50 -sort dm
```

## Common Patterns

| Task | Command |
|------|---------|
| Find by extension | `es.exe *.md` |
| Find in folder | `es.exe notes -path "C:\Users"` |
| Largest files | `es.exe * -sort size -n 10` |
| Recent files | `es.exe * -sort dm -n 20` |
| Find by size | `es.exe /a尺寸 > 10MB` |
| Only files | `es.exe <search> /a-d` |
| Only folders | `es.exe <search> /ad` |

## Options

| Option | Description |
|--------|-------------|
| `-n <num>` | Limit to num results |
| `-sort size` | Sort by size |
| `-sort dm` | Sort by date modified |
| `-sort name` | Sort by name |
| `-sort dc` | Sort by date created |
| `-sort-ascending` | Ascending order |
| `-sort-descending` | Descending order |
| `-path <path>` | Search under path |
| `-parent <path>` | Search in parent only |
| `-r` | Regex mode |
| `-i` | Case sensitive |
| `-p` | Match path and filename |
| `-o <offset>` | Offset for pagination |
| `-csv` | CSV output |
| `-txt` | Text output |
| `-efu` | Everything File List |
| `/a-d` | Files only |
| `/ad` | Directories only |
| `/a[attributes]` | Filter by attributes |
| `-timeout <ms>` | Wait for DB load |
| `-pause` | Pause on full screen |
| `-hide-empty-search-results` | Hide results if no search text |

## Return Codes

| Code | Meaning |
|------|---------|
| 0 | Success |
| 1 | Failed to register window class |
| 2 | Failed to create listening window |
| 3 | Out of memory |
| 4 | Missing argument |
| 5 | Failed to create export file |
| 6 | Unknown argument |
| 7 | IPC query failed |
| 8 | Everything IPC window not found (ensure Everything is running) |

## Tips

- Omit `-n` to get all results
- Use `-timeout 5000` if database is still loading
- Add `-save-settings` to remember your preferences
- For PowerShell, escape special chars with backtick: `^`
- Default sort is ascending for size/date, alphabetical for name

## Troubleshooting

**"Everything IPC window not found"**
→ Ensure Everything is running in the background

**No results**
→ Check if Everything has indexed the location (Options → Indexes)
