# ai-project-template-v2 Product Backlog

**Status:** Living document
**Owner:** Adam with Clead

---

## How to read this backlog

| Marker | Meaning |
|---|---|
| [NOW] | Active — being worked on |
| [NEXT] | Queued — ready to start after current work |
| [LATER] | Confirmed future work, not yet scheduled |
| [IDEA] | Unvalidated — needs discussion |
| [BLOCKED] | Waiting on dependency or decision |
| [DONE] | Completed and merged |

---

## Phase 1 — Language packs and bootstrap wizard

**Goal:** Make v2 a fully usable template — clone it, run the wizard,
get a working project in any supported language.

- **[NEXT] PBI-1.1** — Port Python language pack from v1
  (`languages/python/`) — ci.yml, code-standards.md, pyproject.toml,
  requirements.txt, requirements-dev.txt, pre-commit-config.yaml,
  gitignore, vscode settings, placeholder test. Adapt to v2 structure.
  Also create `docs/DEV_INFRASTRUCTURE.md` covering:
  - Language-agnostic content: new machine setup sequence, CI/CD
    philosophy, branch protection runbook, commit message convention
  - Python-specific content: venv setup (macOS and Windows),
    pip install sequence, pre-commit install, pytest run, ruff check,
    always run as module not script (`python -m src.<module>.main`),
    the MagicMock Python 3.14 gotcha (construct mock before patch
    context, not inside it — see v1 docs/DEV_INFRASTRUCTURE.md
    section 5 for full detail)
  PBIs 1.2 and 1.3 extend DEV_INFRASTRUCTURE.md for their languages.
  Reference: sugose/ai-project-template `docs/DEV_INFRASTRUCTURE.md`
  for the full v1 content to inform (not copy) this document.

- **[NEXT] PBI-1.2** — Port Node/TypeScript language pack from v1
  (`languages/node/`) — ci.yml, code-standards.md, package.json,
  tsconfig.json, biome.json, gitignore, vscode settings, placeholder
  test. Adapt to v2 structure.

- **[NEXT] PBI-1.3** — Port React Native / Expo language pack from v1
  (`languages/react-native/`) — ci.yml, code-standards.md, package.json,
  app.json, tsconfig.json, biome.json, gitignore, vscode settings,
  placeholder test. Adapt to v2 structure.

- **[LATER] PBI-1.4** — Write the v2 bootstrap wizard (`BOOTSTRAP.md`)
  — guided setup via Claude chat, branches on new project vs migration
  from existing project, generates all project files for chosen language,
  produces Crog setup prompt. Migration branch must ask: source repo,
  Adam's WHAT call on v1 backlog items, sequencing (spec first, then
  tests, then src).

- **[LATER] PBI-1.5** — Write `languages/README.md` — how to add a
  new language pack to v2.

---

## Phase 2 — Validate unproven pieces

**Goal:** Prove the two load-bearing assumptions before claiming full
autonomy. Use a real project (python-blackjack-v2) as the pilot.

- **[LATER] PBI-2.1** — Confirm GitHub connector write access: verify
  that Cowork's GitHub connector can post PR comments, not just fetch
  diffs. The `review.yml` workflow posts a marker comment — confirm
  this fires correctly and Clead can read it to trigger review.

- **[LATER] PBI-2.2** — Wire Clead review invocation: once write access
  is confirmed, replace the manual "Adam pastes PR URL to Clead" step
  with an automated trigger. Clead's review Routine receives the PR
  diff, SPEC.md, and Review Standard as scoped inputs only.

- **[LATER] PBI-2.3** — Confirm Routines secret injection timeline with
  Anthropic. Once available, wire Clead→Crog trigger so Adam is no
  longer involved in firing Crog.

---

## Phase 3 — python-blackjack-v2 migration

**Goal:** Migrate python-blackjack from v1 to v2, proving the template
works on a real, complex project.

- **[LATER] PBI-3.1** — Bootstrap python-blackjack-v2 from v2 template

- **[LATER] PBI-3.2** — Populate python-blackjack-v2 with specs,
  processes, and docs — written fresh, informed by v1, adapted to v2
  philosophy. Adam reviews v1 backlog (done and not-done) and makes
  WHAT call on each item. Completed v1 work may be revisited.

- **[LATER] PBI-3.3** — Port test suite from python-blackjack v1 with
  v2 spec as target. Each test evaluated: does this behaviour belong in
  v2 spec? Does it express it in v2 terms? Rewrite or discard if not.
  All red is the correct end state.

- **[LATER] PBI-3.4** — Port src from python-blackjack v1 with v2 spec
  as target. Adapt, do not copy. Make tests green.

---

## Phase 4 — Autonomous PR loop and Copi reactivation

**Goal:** Eliminate Adam's remaining manual touchpoints for doc-only
changes and session-end writes, and reactivate Copi as a specialist
third-layer reviewer for complex src PRs.

- **[LATER] PBI-4.1** — Verify Cowork direct file write capability.
  Test whether Cowork-Clead can write files, commit, push, and open
  a PR directly from its working folder without going through Crog.
  If confirmed: doc-only changes (memory files, backlog, CHANGELOG,
  session-end writes) bypass Crog and the review gate entirely.
  Cowork-Clead is both author and committer. Adam merges or,
  once trust is established, Cowork merges directly.

- **[LATER] PBI-4.2** — Implement session-end autonomous write via
  Cowork schedule skill.

  ## What we want to achieve
  When a Cowork-Clead session goes idle (Adam leaves without saying
  goodbye, or says "gn, kisses" explicitly), Cowork-Clead should
  automatically:
  1. Assemble what changed during the session that isn't yet in the
     memory files
  2. Write to the appropriate files (decisions.md, context.md,
     project.md per the session-end routine in CLAUDE.md)
  3. Commit, push to a branch, open a PR
  4. Adam merges when back

  Zero Routine executions. Zero Crog involvement. Zero Adam
  touchpoints except merge.

  ## What needs to be investigated first

  **Investigation A — Schedule skill capabilities:**
  Ask Cowork-Clead directly:
  1. Can the schedule skill detect inactivity (no user input for N
     minutes) or does it only run on fixed schedules (every hour
     at :00)?
  2. If scheduled on inactivity, can Cowork write to files in the
     working folder and commit as part of that scheduled task?
  3. Can a scheduled task open a PR, or does it only have file
     system access?

  The answers determine whether inactivity-triggered session-end
  is feasible today or requires a different mechanism.

  **Investigation B — Trigger mechanisms:**
  Two triggers needed, not one:
  - **Explicit:** Adam says "gn, kisses" (or any agreed phrase).
    Cowork-Clead recognises it as a session-end signal and runs
    the persist routine immediately.
  - **Implicit:** No user input for N minutes (default: 60).
    Schedule skill fires, Cowork-Clead runs the persist routine
    automatically. Covers the "football came on" scenario.

  Determine whether both triggers can be wired via the schedule
  skill, or whether the implicit trigger needs a different approach
  (e.g. GitHub Actions cron that checks last memory file commit
  timestamp and fires a prompt if stale).

  **Investigation C — What "session-end persist" actually writes:**
  The session-end routine (to be added to CLAUDE.md per the
  session-end PR already in progress) defines what goes where.
  Verify that Cowork-Clead can reliably determine what is new
  versus what is already in the files — to avoid duplicating
  existing content on every scheduled run.

  ## Implementation plan (once investigations complete)

  **Step 1 — Explicit trigger:**
  Add recognised session-end phrases to CLAUDE.md ("gn", "gn kisses",
  "bye", "wrap up", "closing down"). When Cowork-Clead detects any
  of these, run the session-end persist routine immediately before
  the session goes idle.

  **Step 2 — Implicit trigger (inactivity):**
  If schedule skill supports inactivity detection: configure a
  scheduled task that fires after 60 minutes of no user input and
  runs the session-end persist routine.
  If schedule skill only supports fixed schedules: configure an
  hourly check that reads the last memory file commit timestamp,
  compares to current time, and only runs the persist routine if
  the gap suggests an unclean session end.

  **Step 3 — File write and PR:**
  Cowork-Clead writes directly to working folder files (no Crog),
  commits, pushes to branch `session/persist-<timestamp>`, opens PR.
  PR title: "Session persist — [DATE] [TIME]"
  PR body: summary of what was written and why.

  **Step 4 — Adam merges when back:**
  No review gate on session persist PRs — Cowork is both author
  and the content source. Adam's merge is the only touchpoint.
  If Adam trusts the routine sufficiently, auto-merge on CI green
  is a further simplification (future consideration).

  ## Success criteria
  - Adam closes laptop mid-session without saying anything
  - 60 minutes later, a PR appears in GitHub with the session's
    key decisions and context written to memory files
  - Adam merges next morning
  - Cowork-Clead starts the next session fully oriented with no
    gap to bridge

  ## Prerequisite
  PBI-4.1 (Cowork direct file write capability) confirmed.

- **[LATER] PBI-4.3** — Verify GitHub connector write access.
  Confirm Cowork's GitHub connector can post PR comments, not just
  fetch diffs. Load-bearing for the autonomous review trigger (PR
  comment as event bus signal). If confirmed, enables Cowork-Clead
  to post verdicts, fix prompts, and approval comments directly to
  PRs without Adam relay. See also memory/decisions.md open
  question #1.

- **[LATER] PBI-4.4** — Wire autonomous src PR loop (Path B).
  GitHub Actions holds Crog's bearer token as an Actions secret.
  Cowork-Clead posts a task marker comment on a PR or sentinel
  location. Actions detects marker, fires Crog with clean task
  (no embedded credentials). Crog implements, opens PR, posts
  pr_done. Actions fires Cowork-Clead review Routine with scoped
  inputs {diff, SPEC.md, Review Standard}. Clead reviews, posts
  approval. Actions fires Crog merge instruction. Adam asleep.
  Prerequisites: PBI-4.1, PBI-4.3 confirmed.
  Reference: memory/decisions.md open question #2 (Path B) for
  full findings and dead ends already investigated.

- **[LATER] PBI-4.5** — Reactivate Copi as Layer 3 reviewer for
  complex src PRs.
  Three-layer review model:
  - Layer 1: Cowork-Clead alone — doc-only, memory writes (no review)
  - Layer 2: Crog implements, Clead reviews — standard src PRs
  - Layer 3: Copi added — large/complex/multi-file src PRs where
    cross-file consistency is the real risk
  Copi invoked by Clead's explicit decision per PR, not by default.
  Label-based trigger model from v1 applies unchanged.
  Reference: sugose/ai-project-template docs/COPILOT_LIMITATIONS.md
  for all operational lessons — do not re-investigate dead ends
  already documented there.
  Decision criteria for Layer 3: multi-file changes, interface
  changes, significant new components, any PR where Clead's
  diff-only review flags uncertainty about cross-file consistency.

---

## Decision log (updated)

| Date | Decision | Rationale |
|---|---|---|
| 2026-06-27 | Language packs not carried over in skeleton | Skeleton is workflow structure only. Packs ported as explicit PBIs so each is reviewed against v2 structure. |
| 2026-06-27 | Bootstrap wizard deferred to PBI-1.4 | Language packs must exist before wizard can generate them. |
| 2026-06-27 | python-blackjack-v2 as pilot project | Real, complex, known codebase. Ideal for proving unproven pieces under real PR load. |
| 2026-06-27 | Doc-only changes owned by Cowork-Clead, no review gate | Cowork is both author and reviewer for its own memory writes — review adds no value. Review gate reserved for src changes where Crog implements and Clead reviews independently. |
| 2026-06-27 | Copi reactivated as Layer 3 only for complex src PRs | Copi's value is cross-file consistency on large/complex changes. Default reviewer role removed — called in deliberately by Clead's judgment. |
| 2026-06-27 | Session-end autonomous write via Cowork schedule skill | Inactivity timeout replaces "gn, kisses" as primary trigger. Same mechanism, no Routine executions, no Crog, no relay. |

---

## Explicitly out of scope for Phase 1

- C# language pack — planned in v1, not yet built, not a Phase 1 priority
- Elixir language pack — same
- Automated merge — Adam merges, always
