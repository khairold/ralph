# Ralph Agent Instructions

These patterns apply to all Ralph iterations. Read this before starting work.

## Commit Conventions

- **Format**: `feat: [US-XXX] - Story title`
- **Scope**: One story per commit
- **Prerequisite**: All quality checks must pass before committing
- **Include**: ALL changed files (code, prd.json, progress.txt)

## Memory Layers

| Layer | File | What Goes There |
|-------|------|-----------------|
| Task state | `prd.json` | Story completion status (`passes: true/false`) |
| Session learnings | `progress.txt` | Story-specific details, gotchas, implementation notes |
| Permanent patterns | `AGENTS.md` | Reusable knowledge for future iterations |
| Project docs | `CLAUDE.md` | User-facing documentation, quick start |

**Rule**: Only promote to AGENTS.md if the pattern is reusable across multiple stories.

## Quality Gates

Before committing, ensure:
- [ ] Typecheck passes
- [ ] Lint passes
- [ ] Tests pass
- [ ] Frontend changes verified in browser (if applicable)

## Story Sizing

Stories should be:
- Small enough to complete in one context window
- Independent (no dependencies on incomplete stories)
- Testable with clear acceptance criteria

## File Update Order

1. Implement the story
2. Run quality checks
3. Update AGENTS.md (if reusable patterns discovered)
4. Commit all code changes
5. Update `prd.json` to set `passes: true`
6. Append to `progress.txt`

## What NOT to Add Here

- Story-specific implementation details (→ progress.txt)
- Temporary workarounds
- Information already in CLAUDE.md
- One-time fixes

See [CLAUDE.md](CLAUDE.md) for project documentation and quick start guide.
