# Ralph - Claude Code Agent Loop

Ralph is an autonomous agent that runs Claude Code repeatedly until all PRD stories complete.

## Quick Start

```bash
# Generate a PRD
/project:prd [feature description]

# Convert PRD to prd.json
/project:ralph [path/to/prd.md]

# Run the autonomous loop
./ralph.sh [max_iterations]
```

## Commands

- `/project:prd` - Generate a Product Requirements Document
- `/project:ralph` - Convert PRD markdown to prd.json format

## Key Files

- `ralph.sh` - Main loop script that spawns Claude Code instances
- `prompt.md` - Instructions given to each Claude Code iteration
- `prd.json` - Task tracking (generated, shows which stories are complete)
- `progress.txt` - Learnings log (generated, persists context between iterations)
- `.claude/commands/` - Custom commands for PRD generation and conversion

## How It Works

1. Each iteration spawns a **fresh Claude Code instance** with `--chrome` for browser automation
2. Memory persists via git history, `progress.txt`, and `prd.json`
3. Stories must be small enough to complete in one context window
4. Always update AGENTS.md with discovered patterns for future iterations

## Flowchart

Interactive visualization: https://snarktank.github.io/ralph/
