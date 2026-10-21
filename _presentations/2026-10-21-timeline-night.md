---
title: Timeline Forensics with TimeSketch
date: 2026-10-21
semester: Fall 2026
presenter: Colin Yeager
tags: [timeline, timesketch, windows]
slides: 
# recording: 
# materials: 
summary: Why timelines matter, how we can use them to build context within an investigation, and how they can be used as a collaborative tool.
---

## What we covered

- Why volatile memory holds evidence that never touches disk
- Acquiring memory safely on a live system
- Core Volatility 3 plugins: `windows.pslist`, `windows.netscan`, `windows.cmdline`, `windows.malfind`

## Lab commands

```bash
vol -f memdump.raw windows.info
vol -f memdump.raw windows.pslist
vol -f memdump.raw windows.netscan
```

## Further reading

- [Volatility 3 documentation](https://volatility3.readthedocs.io/)
