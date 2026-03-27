# 🧠 OpenClaw Weekly Memory Skill

Automated weekly maintenance for OpenClaw's memory, including archiving and merging daily logs.

![OpenClaw Skill](https://img.shields.io/badge/OpenClaw-Skill-blue) ![Status](https://img.shields.io/badge/Status-Active-green)

---

## Overview

The `weekly-memory` skill ensures that your OpenClaw agent's memory remains optimized and manageable over time. By automatically archiving older memory files and merging daily logs on a weekly basis, it helps to prevent memory bloat, improve retrieval efficiency, and maintain a clean workspace. This skill is crucial for long-running agents that accumulate a significant amount of conversational and operational data.

## Features

*   **Memory Archiving**: Moves older, less frequently accessed memory files to an archive, keeping the active memory lean.
*   **Daily Log Merging**: Consolidates daily operational logs into a more compact format, streamlining data review.
*   **Automated Maintenance**: Designed to run as a scheduled cron job, requiring no manual intervention.
*   **Efficiency**: Contributes to the overall performance and cost-effectiveness of your OpenClaw deployment by managing memory usage.

## Installation

To install the `weekly-memory` skill, copy its directory into your OpenClaw workspace's `skills` folder:

```bash
cp -R weekly-memory ~/.openclaw/workspace/skills/
```

## Usage

The `weekly-memory` skill is intended to be executed as a scheduled cron job. It leverages `cron_runner.py` to orchestrate memory cleanup and merging scripts.

1.  **Schedule the Cron Job**:
    ```bash
    cd ~/.openclaw/workspace && python3 scripts/cron_runner.py --script 'python3 scripts/memory-cleanup.py --archive --json' --script 'python3 scripts/memory-merger.py --merge --json' --name weekly-memory
    ```

    > [!NOTE]
    > This command assumes the presence of `memory-cleanup.py` and `memory-merger.py` within your `scripts` directory. These scripts are typically part of the OpenClaw core distribution or the `jarvis-memory-architecture` skill.

2.  **Report Summary**: After execution, the skill will provide a concise, one-line summary of the memory maintenance operations.

## Configuration

The core logic for memory archiving and merging resides in the `memory-cleanup.py` and `memory-merger.py` scripts (which are external to this specific skill's directory but are usually available in the OpenClaw `scripts` folder). The `weekly-memory` skill itself acts as an orchestrator via `SKILL.md` for scheduling these operations. No direct configuration files are within this skill's directory beyond `SKILL.md`.

## File Structure

The `weekly-memory` skill consists of the following file:

```
weekly-memory/
└── SKILL.md
```
