# [PROJECT NAME]

## Setup

1. Clone this repo
2. Open Cowork and set your working folder to this repo clone
3. Open `CLAUDE.md` — Clead will orient from there
4. Tell Clead what today's work is

No dump file. No paste ritual. Everything Clead needs is in the repo.

## The team

| Role | Who | Surface |
|---|---|---|
| Product Owner | [PO NAME] | Cowork chat |
| Tech Owner / Reviewer | Clead (Claude) | Cowork |
| Implementer | Crog (Claude Code) | Terminal / Routines |

## Workflow

Adam describes the next PBI. Clead specs it. Adam approves intent.
Crog implements TDD-first. GitHub Actions triggers Clead review.
Clead posts verdict to PR. Adam merges. Crog updates changelog.

## Branch protection

`main` is protected. Nothing merges without CI green and Adam's approval.

## Reference implementation

This template was built from the lessons of sugose/ai-project-template.
See `docs/decisions/0001-rebuild-workflow.md` for the full rationale.
