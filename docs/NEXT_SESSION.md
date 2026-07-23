# [PROJECT NAME] — Next Session Planning

**Last Updated:** [never — this is a fresh scaffold]
**Author:** Clead (Tech Owner)
**Purpose:** Staging area for reasoning, revised assumptions, and
plan-adaptation thoughts that aren't yet mature enough to be a PBI, a
decision, a strategy update, or a vision-doc change. Complements
`docs/BACKLOG.md` — it does not replace it. Discrete, scoped, actionable
work belongs in the backlog as a PBI, not here.

**The rule that keeps this useful, not a junk drawer:** every entry below
must get a disposition each session it's touched — promoted to a PBI, a
decision, or a formal doc update; re-affirmed as still-next; or deleted as
resolved/obsolete. This file is read and triaged at the start of every
session (see `CLAUDE.md` session-start routine). It is not a substitute
for the backlog — it's where things live before they're ready to become
backlog items.

---

## Current situation summary

*(One or two paragraphs: where the project actually stands right now —
what's built, what's proven, what the next concrete milestone is. Replace
this each time it goes stale — don't just append below it.)*

---

## What needs adapting

*(Numbered entries, one per thought. Use this shape as a starting point,
not a rigid template — capturing the reasoning matters more than filling
every field:)*

### Triaged — 2026-07-23

Raw items from earlier in the day, dispositioned this session:

1. ~~do you remember Copi?~~ — **Closed 2026-07-23.** Already fully
   documented: `memory/decisions.md` open question #4 and
   `docs/BACKLOG.md` PBI-4.5 (Copi reactivated as Layer 3 reviewer for
   complex src PRs, invoked by Clead's explicit per-PR judgment, not by
   default). Nothing new to capture — answered directly to Adam in chat,
   Adam confirmed closed.

2. ~~are pr_dumps still used between Crog and Clead / needed for Clead's
   review?~~ — **Promoted 2026-07-23.** Answer is no (already established
   in `memory/decisions.md` 2026-06-27/2026-06-28 entries), but Adam asked
   for this to be made explicit and final in the decision log rather than
   left implicit. Crog prompt fired (`CROG PROMPT 10:52 #2`) to add a
   dedicated decision-log entry closing this out. Delete this entry once
   that PR merges.

3. ~~i want to index Crog prompts~~ — **In flight, being addressed
   directly (not via this file).** Adam clarified scope 2026-07-23: every
   Crog prompt delimiter carries a session-unique incrementing ID
   (`CROG PROMPT HH:MM #N`, starting at `#1` per session, Clead-maintained).
   Cowork auto-memory (`[[crog-prompt-delimiters]]`) updated; doc-only PR
   in flight for `docs/ROUTINES.md` via Crog prompt `CROG PROMPT 10:47 #1`.
   Delete this entry once that PR merges and CHANGELOG reflects it.

4. ~~Formalizing the PIN workflow~~ — **Promoted 2026-07-23.** Not the
   same as python-blackjack's "conceptual pin" (checked — no value in
   porting that repo's `HOW_WE_WORK.md` wholesale; roles/decision-authority
   already covered better in `memory/roles.md`, and its Session Rhythm/PR
   Flow sections describe v1-specific mechanics v2 deliberately replaced).
   Adam defined this fresh for v2: a transient, in-context-only list for
   mid-session ideas not yet worth a file write — pinned via natural
   language ("pin that"), surfaced on request ("what's pinned?"), never
   persisted directly. Every pin must be dispositioned (promoted or
   explicitly dropped) before session end — Adam added this as condition 7
   of the Clean session end state checklist, since pins can't be allowed
   to silently lapse. Crog prompt fired (`CROG PROMPT 11:08 #3`) to add
   a "The PIN workflow" section to `CLAUDE.md` plus the new condition 7.
   Delete this entry once that PR merges.

### N. [Short title] — [new / revised / superseded]

**Previous assumption:** ...
**Revised assessment:** ...
**Impact on plan:** ...
**Action:** ... (what a future session should actually do about this)

---

## Items that do not change

*(Short bullet list — things confirmed still valid, so a future session
doesn't waste time re-deriving them. Prune entries here once they're
foundational enough to belong in `docs/decisions/` or
`memory/decisions.md` instead.)*
