# Changelog

All notable changes to [PROJECT NAME] are documented here.

## [Unreleased]

### Added
- Operational lessons from a live fomo-f session folded into docs/BACKLOG.md
  and memory/standards.md: mandatory `.gitattributes` line-ending policy in
  PBI-1.1 scaffolding, Chrome PR-fetch cache-busting note in PBI-2.2, a
  refined PBI-4.1 finding (file writes and git ops are separate
  capabilities), and a Review Standard addition on verifying claims
  directly rather than via proxy signals (PR #14)
- Clarified that the `?i=N` PR-URL cache-busting param is Clead's own
  fetch-time responsibility, not something Crog needs to add when
  reporting URLs (docs/BACKLOG.md wording fix) (PR #16)
- Added PBI-P.1 (document the change-control model Adam stated
  2026-07-23) and PBI-P.2 (fix stale changelog.yml wording) to the
  backlog under a new "Process & team documentation" section (PR #17)
- Fixed the stale "push to main" wording in the automated
  changelog-reminder comment in .github/workflows/changelog.yml (now
  reads "Crog: open a PR updating CHANGELOG.md"); closed PBI-P.2 (PR #18)
- Committed two working-tree-only edits carried over uncommitted from a
  2026-06-28 Cowork-Clead session — a GitHub-connector-availability
  check added to CLAUDE.md's session startup routine, and a matching
  session-notes entry in memory/context.md (PR #19)

## [0.1.0] — 2026-06-27

### Added
- Initial project setup from ai-project-template-v2
- Repo-committed memory system (memory/ directory)
- CLAUDE.md dual-audience router (Clead index + Crog stub)
- docs/decisions/ ADR log — ADR 0001 adopted as founding document
- GitHub Actions workflows: CI, review dispatch, changelog trigger
