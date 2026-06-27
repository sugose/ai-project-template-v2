# [PROJECT NAME]

## Setup

### Prerequisites
- Claude desktop app with Cowork available
- GitHub connector connected to your GitHub account
- Claude Code CLI installed (`npm install -g @anthropic-ai/claude-code`)
- GitHub CLI installed and authenticated (`gh auth login`)

### First-time setup (one-off)

**1. Clone the repo**
```bash
git clone https://github.com/sugose/ai-project-template-v2.git
cd ai-project-template-v2
```

**2. Create a Cowork project**
In the Claude desktop app, create a new Cowork project for this repo.
- Set the project name to match the repo (e.g. `ai-project-template-v2`)
- Set the project save location to your local repo clone folder
- This is the working folder Cowork reads from — the repo files are
  Clead's memory, not Cowork's internal storage

**3. Connect the GitHub connector**
In the Cowork project settings, connect the GitHub connector to your
GitHub account. This gives Clead direct read access to PRs and diffs.
Write access (posting PR comments) is an unconfirmed assumption —
see `docs/RELEASE_NOTES.md` known issues.

**4. Verify memory loaded correctly**
Before giving Clead any task, ask it to summarise `memory/context.md`.
If it can accurately describe the project, the decisions made, and the
current state of open questions, the memory files loaded correctly and
Clead is oriented.

If it cannot, check that the project save location points to the correct
repo folder and that `CLAUDE.md` and the `memory/` directory are present.

**5. Start working**
Tell Clead what today's work is. Everything it needs is in the repo.

No dump file. No paste ritual. No orientation script.

### Starting subsequent sessions

Open the Cowork project. Clead loads from the repo automatically.
The first thing you say is the first thing that matters.

### One Cowork project per repo

Each repo you work on should have its own Cowork project with its own
save location pointing to that repo's clone. This gives isolation —
what Clead learns in one project never bleeds into another. See
`docs/decisions/0001-rebuild-workflow.md` §6 for the full rationale.

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
