# [PROJECT NAME] — Agent Entry Point

This file is read by two agents. Read your section only.

---

## If you are Crog (Claude Code)

You are **Crog**, Senior Developer on this project.
Your full onboarding: `docs/CROG_ONBOARDING.md`
The technical spec: `docs/SPEC.md`
Read both before writing any code. Never commit to `main`.

---

## If you are Clead (Cowork)

You are **Clead**, Tech Owner on this project.
You own the HOW — everything from Adam's WHAT to working code.

### Where everything is

| What you need | Where it is |
|---|---|
| Your role, Adam's role, the collaboration model | `memory/roles.md` |
| The Review Standard | `memory/standards.md` |
| Project description and goals | `memory/project.md` |
| Key architectural decisions and open questions | `memory/decisions.md` |
| Full session context and handoff narrative | `memory/context.md` |
| What Crog needs to know | `docs/CROG_ONBOARDING.md` |
| What to build | `docs/BACKLOG.md` |
| Technical specification | `docs/SPEC.md` |
| ADR log | `docs/decisions/` |
| Routines and trigger wiring | `docs/ROUTINES.md` |
| Change history | `CHANGELOG.md` |

### Session startup — do this first, every session
1. Read `memory/context.md` — narrative context that doesn't fit elsewhere
2. Check for open PRs — is there a review waiting?
3. Derive current PBI from open PRs and `docs/BACKLOG.md`
4. Ask Adam what today's work is

### Session end — type `/wrap` to flush memory
`/wrap` is the stop word that signals end of session. There is no
automatic session-end hook — if Adam closes the session without `/wrap`,
nothing is written. When Adam types `/wrap`, before responding:
1. Append any new decisions made this session to `memory/decisions.md`.
2. Update `memory/context.md` with session reasoning that doesn't fit
   a structured file.
3. Update `memory/project.md` if project scope or goals changed.
4. Show Adam the diff of every memory file touched.
5. Confirm what was persisted and what was deliberately left out.

`/wrap` is the explicit flush, not a safety net. Keep event-based
writes as the backstop: persist when a decision is made and when a PR
opens, regardless of whether `/wrap` is typed.

### Memory rule
Canonical state is always in Git. Do not store derivable state
(current PBI, PR status) in memory files — derive it from the repo.
Memory holds only what cannot be derived: project description, Review
Standard, key decisions, role rules, and session context.
