---
name: weekly-memory
description: Weekly memory cleanup and merger
version: 1.0.0
triggers:
  - memory cleanup
  - memory merge
  - weekly memory
---

# Weekly Memory Maintenance

Archives old memory files and merges daily logs.

## Steps

1. Run: `cd ~/.openclaw/workspace && python3 scripts/cron_runner.py --script 'python3 scripts/memory-cleanup.py --archive --json' --script 'python3 scripts/memory-merger.py --merge --json' --name weekly-memory`
2. Report 1-line summary