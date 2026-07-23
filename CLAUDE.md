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
2. Verify GitHub availability — probe for GitHub connector tools (a green
   "Connected" in settings is NOT proof the tools loaded). If no tools
   surface, the connector is down (known platform-wide outage as of
   2026-06-28 — see `memory/decisions.md`); fall back to the
   Claude-in-Chrome extension as the read/write channel and note it to Adam.
3. Check for open PRs — is there a review waiting?
4. Derive current PBI from open PRs and `docs/BACKLOG.md`
5. Ask Adam what today's work is

### Session end — type `..wrap` to flush memory
`..wrap` is the stop word that signals end of session. There is no
automatic session-end hook — if Adam closes the session without `..wrap`,
nothing is written. When Adam types `..wrap`, before responding:
1. Append any new decisions made this session to `memory/decisions.md`.
2. Update `memory/context.md` with session reasoning that doesn't fit
   a structured file.
3. Update `memory/project.md` if project scope or goals changed.
4. Show Adam the diff of every memory file touched.
5. Confirm what was persisted and what was deliberately left out.

`..wrap` is the explicit flush, not a safety net. Keep event-based
writes as the backstop: persist when a decision is made and when a PR
opens, regardless of whether `..wrap` is typed.

### Clean session end state

A session is not "clean" on a claim — it's clean when all six of the
following are true, and were checked this session, not assumed from an
earlier report:

1. No uncommitted changes. `git status` clean in every repo touched —
   checked directly, not assumed. Includes carryover discovered from
   prior sessions (e.g. a previous session's edits that were never
   committed).
2. Every PR opened this session is resolved — merged and independently
   verified (git-object check and/or a fresh cache-busted page fetch),
   or explicitly left open with Adam's knowledge and a stated reason. A
   relayed "merged" claim from Crog is not itself verification.
3. Every follow-up is persisted in the repo, in the right container.
   Discrete, scoped, actionable work goes in the backlog as a PBI.
   Reasoning, revised assumptions, or thoughts not yet mature enough to
   be a PBI, a decision, a strategy update, or a vision-doc change go in
   a NEXT_SESSION.md-style handoff doc instead (see fomo-f for a working
   example; this template does not currently have one — introduce it if
   a project reaches the point of needing it). Items placed in such a
   doc carry priority to be addressed first in the next session — it's
   a staging area, not a permanent home; entries graduate into a PBI, a
   decision, or a formal doc update once mature enough, or get resolved
   and removed. Either container satisfies "if it's not in the repo it
   doesn't exist" — private cross-session memory does not.
4. Verification is direct, not pattern-matched. A "confirmed" or "done"
   claim must come from a check that actually confirms that specific
   claim — not a keyword/substring match, a stale cached page, or trust
   in a relay.
5. CHANGELOG.md (where the project has one) reflects all merged PRs,
   except the PR currently documenting itself — accepted one-PR-behind
   rhythm, not a gap.
6. "No open items" is verified against the actual threads (uncommitted
   diffs, unmerged PRs, ungrounded claims) — not inferred from an empty
   tracking widget, which only reflects what was tracked, not what's
   true.

### Memory rule
Canonical state is always in Git. Do not store derivable state
(current PBI, PR status) in memory files — derive it from the repo.
Memory holds only what cannot be derived: project description, Review
Standard, key decisions, role rules, and session context.
