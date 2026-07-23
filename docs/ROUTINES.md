# Routines and Trigger Wiring

## Current state (transitional)

Until GitHub Actions review dispatch and Routines secret injection
are both confirmed and in place, the trigger flow is:

1. Crog opens PR, posts pr_done comment
2. Adam pastes the review trigger to Clead (one paste — not relay)
3. Clead reviews, posts verdict directly to PR
4. Adam merges on approval

## Target state

- PR opened → `.github/workflows/review.yml` dispatches review Routine
- Review approved → workflow notifies Adam
- PR merged → `.github/workflows/changelog.yml` triggers changelog step

## Assumptions to validate before target state is live

1. GitHub connector can **write** PR comments (not just fetch diffs)
2. Routines secret injection available from Anthropic

Both are load-bearing for full autonomy. Do not claim two Adam
touchpoints until both are confirmed.

## Review Routine — input contract (hard constraint)

The review Routine must receive **only**:
- The PR diff
- `docs/SPEC.md`
- `memory/standards.md`

It must **not** receive:
- The implementation conversation history
- Design-time memory
- Any context from the session that produced the spec

This is a hard constraint. Reviewer independence is structural,
not conventional. Same-session context reset is not sufficient —
the context remains in the window and will influence the review.

## Crog prompt conventions

When Clead hands Crog a prompt, it is wrapped in a delimiter block:

    ========== CROG PROMPT HH:MM #N ==========
    <prompt text>
    ====================================

- **HH:MM** — 24h local time, freshly checked at write time (not
  reused from a prior prompt in the session).
- **#N** — a session-unique ID, starting at `#1` and incrementing by
  one for every subsequent Crog prompt in that same Clead session,
  regardless of which repo or PR the prompt concerns. Clead maintains
  this counter itself — it is not Adam's manual bookkeeping.
- **Purpose** — lets Adam identify at a glance what's meant to be
  pasted to Crog versus commentary, and lets either party refer back
  to a specific prompt unambiguously (e.g. "see CROG PROMPT 10:47 #1").
