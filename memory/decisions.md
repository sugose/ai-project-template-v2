# Key Architectural Decisions

All major decisions made in the session of 2026-06-27 that produced
this template. Full rationale in docs/decisions/0001-rebuild-workflow.md.

| Date | Decision | Rationale |
|---|---|---|
| 2026-06-27 | Rebuild from scratch rather than iterate on v1 | v1 complexity was proportional to workarounds, not to the problem |
| 2026-06-27 | Memory files are repo-committed, not Cowork-local | Self-contained vision + single source of truth rule. A fresh clone must find Clead fully oriented. Local Cowork memory breaks this. |
| 2026-06-27 | Do not store derivable state in memory | Current PBI derives from open PRs + BACKLOG.md. Memory holds only what cannot be derived. |
| 2026-06-27 | GitHub Actions drives the review loop | Chat sessions cannot poll. Actions is consistent with single-source-of-truth and keeps the PR thread as the coordination log. |
| 2026-06-27 | Reviewer runs as separate invocation with scoped inputs | Structural isolation required. Same-session context reset explicitly rejected — context remains in window and will influence review. |
| 2026-06-27 | Loop cap at 3 review cycles, then escalate to Adam | Safety control re-added. The v1 hard-stop rule carried this function as a side effect. Discarding relay mechanics must not discard the safety function. |
| 2026-06-27 | Cowork is the primary Clead surface | Cowork has GitHub connector, persistent working folder, and chat. Covers both execution and thinking sessions. |
| 2026-06-27 | CLAUDE.md serves both Clead and Crog with clear demarcation | Crog auto-loads CLAUDE.md via Claude Code. File must serve both audiences without conflating them. |
| 2026-06-27 | Bootstrap wizard branches on migration vs new project | Any team migrating from a previous workflow hits the same questions. Baked into wizard so it gets asked every time. |
| 2026-06-27 | Ported code is subject to v2 review standard | v2 spec is the target; source repo is reference only. Porting is not copying. |
| 2026-06-27 | pr_dump.sh retained as non-load-bearing fallback | May be useful for Chat-only sessions. Not load-bearing infrastructure in v2. |

## Open questions (unresolved as of 2026-06-27)
1. Can the GitHub connector write PR comments, or only fetch diffs?
   Load-bearing for full autonomy. Must be confirmed before claiming
   two Adam touchpoints.
2. Timeline for Routines secret injection from Anthropic.
   Until this lands, Adam fires Crog manually (one paste, not relay).
3. Spec-author blind spot: Clead writes the spec and reviews against it.
   A flawed spec passes compliance invisibly. Adam's intent gate helps
   but does not fully resolve this. Tracked as open.
4. Copilot's role in v2 — Copilot is absent from the v2 skeleton by
   deliberate starting position, not permanent exclusion. In v1, Clead
   and Copilot covered different blind spots: Clead reviewed from the
   diff only (pr_dump.sh constraint), Copilot read full files. In v2,
   Clead fetches diffs and files directly via GitHub connector, which
   may eliminate the structural reason for Copilot's complementary role.
   Question to answer on a real project: what does Copilot catch that
   Clead misses in v2? If Clead can fetch full files on demand, the
   blind spot may not exist. If it does, the v1 label-based model is
   documented in sugose/ai-project-template/docs/COPILOT_LIMITATIONS.md
   and ready to pick up. Decision deferred until Clead's solo review
   performance is observed on a real v2 project.
