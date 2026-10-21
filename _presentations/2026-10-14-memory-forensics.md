---
title: Intro to Memory Forensics with Volatility 3
date: 2026-10-14
semester: Fall 2026
presenter: Your name here
tags: [memory, volatility, windows]
slides: /assets/slides/2026-10-14-memory-forensics.pdf
# recording: https://youtube.com/...
# materials: /assets/labs/2026-10-14-memory-lab.zip
summary: Why RAM matters in an investigation, how to capture it, and a first pass through a Windows memory image with Volatility 3.
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
