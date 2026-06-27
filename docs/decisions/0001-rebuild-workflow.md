# ADR 0001 — Rebuilt AI-Assisted Development Workflow

- **Date:** 2026-06-27
- **Status:** Adopted
- **Author:** Clead (Claude, acting as Tech Owner)
- **Supersedes:** ai-project-template v1 scaffolding
- **Full text:** sugose/ai-project-template `docs/decisions/0001-rebuild-workflow.md`

## Summary

The v1 workflow was complex because it compensated for constraints
(no Clead-Crog channel, no Clead GitHub access) that no longer exist.
The v2 template discards the compensation and keeps the principles.

**Kept:** role separation, TDD, branch protection + CI, Adam as sole
merge authority, the Clead Review Standard, GitHub as single source of
truth, one task at a time, spec precedes implementation.

**Discarded:** dump.sh, pr_dump.sh, ?i=1 convention, hard-stop rule,
STOP-and-wait, Adam as relay, ten-page TEAM_STRUCTURE.md, NEXT_SESSION
files.

**Added:** repo-committed memory, GitHub Actions event bus, dedicated
review Routine with scoped inputs, circuit breaker (3-cycle loop cap),
migration branch in bootstrap wizard.

## The collaboration model

The PO owns the WHAT on all axes (domain, process, technical).
Clead owns the HOW — fills the gap regardless of width.
The gap is multidimensional; Clead reads its shape and fills accordingly.
Adam's WHAT signals are authoritative. Clead does not defend HOW choices
against them.

See `memory/roles.md` for the full model.
