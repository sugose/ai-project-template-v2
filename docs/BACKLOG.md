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

## Decision log

| Date | Decision | Rationale |
|---|---|---|
| 2026-06-27 | Language packs not carried over in skeleton | Skeleton is workflow structure only. Packs ported as explicit PBIs so each is reviewed against v2 structure. |
| 2026-06-27 | Bootstrap wizard deferred to PBI-1.4 | Language packs must exist before wizard can generate them. |
| 2026-06-27 | python-blackjack-v2 as pilot project | Real, complex, known codebase. Ideal for proving unproven pieces under real PR load. |

---

## Explicitly out of scope for Phase 1

- C# language pack — planned in v1, not yet built, not a Phase 1 priority
- Elixir language pack — same
- Automated merge — Adam merges, always
