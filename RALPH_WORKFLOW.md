# How Ralph Works with Claude Code

**Autonomous AI agent loop for completing PRDs**

---

## Workflow

### 1. You write a PRD

Define what you want to build.

### 2. Convert to prd.json

Break into small user stories. Each story follows this structure:

```json
{
  "id": "US-001",
  "title": "Add priority field to database",
  "acceptanceCriteria": [
    "Add priority column to tasks table",
    "Generate and run migration",
    "Typecheck passes"
  ],
  "passes": false
}
```

### 3. Run ralph.sh

Starts the autonomous loop.

### 4. Claude Code picks a story

Finds next story where `passes: false`.

### 5. Implements it

Writes code, runs tests.

### 6. Commits changes

If tests pass.

### 7. Updates prd.json

Sets `passes: true` for the completed story.

### 8. Logs to progress.txt

Saves learnings. Also updates `AGENTS.md` with patterns discovered, so future iterations learn from this one.

### 9. More stories?

```
┌─────────────────┐
│  More stories?  │
└────────┬────────┘
         │
    ┌────┴────┐
    │         │
   Yes        No
    │         │
    ▼         ▼
 Step 4     Done!
```

- **Yes** → Return to step 4 (pick next story)
- **No** → All stories complete

---

## Visual Flow

```
┌──────────────────────┐
│    You write a PRD   │
└──────────┬───────────┘
           ▼
┌──────────────────────┐
│  Convert to prd.json │
└──────────┬───────────┘
           ▼
┌──────────────────────┐
│     Run ralph.sh     │
└──────────┬───────────┘
           ▼
┌──────────────────────┐
│ Claude Code picks a  │◄─────────────┐
│       story          │              │
└──────────┬───────────┘              │
           ▼                          │
┌──────────────────────┐              │
│    Implements it     │              │
└──────────┬───────────┘              │
           ▼                          │
┌──────────────────────┐              │
│   Commits changes    │              │
└──────────┬───────────┘              │
           ▼                          │
┌──────────────────────┐              │
│  Updates prd.json    │              │
└──────────┬───────────┘              │
           ▼                          │
┌──────────────────────┐              │
│ Logs to progress.txt │              │
└──────────┬───────────┘              │
           ▼                          │
     ┌───────────┐                    │
    /  More       \      Yes          │
   /   stories?    \─────────────────►┘
   \               /
    \             /
     └─────┬─────┘
           │ No
           ▼
    ┌─────────────┐
    │    Done!    │
    └─────────────┘
```

---

## Key Concepts

| Component      | Purpose                                                           |
| -------------- | ----------------------------------------------------------------- |
| `prd.json`     | Stores user stories with acceptance criteria and pass/fail status |
| `ralph.sh`     | Shell script that orchestrates the autonomous loop                |
| `progress.txt` | Log file capturing learnings from each implementation             |
| `AGENTS.md`    | Documentation of discovered patterns for future AI iterations     |

---

## Self-Improving Loop

This creates a self-improving loop where Claude Code:

1. **Autonomously** works through your PRD
2. **Learns** from each implementation
3. **Documents** patterns for future sessions

Each iteration makes the next one smarter.
