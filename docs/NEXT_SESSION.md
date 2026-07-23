# [PROJECT NAME] — Next Session Planning

**Last Updated:** 2026-07-23
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

The Chrome-web-editor direct-commit path for doc-only changes (memory/,
docs/, CHANGELOG.md, CLAUDE.md itself) is proven end-to-end and now
documented in CLAUDE.md's "Change execution model" section (PR #36),
cross-referenced from docs/ROUTINES.md (PR #38). CHANGELOG.md is current
through PR #38. A "verify live state before asserting routing/authority/
process facts" discipline has been added to Clead's role rules in
memory/roles.md (PR #37), ported from local Cowork auto-memory so it's
no longer session-local-only. The six items below were pinned mid-session
on 2026-07-23 and are being promoted here verbatim, unprocessed, because
Adam had to end the session before triaging them — none have been
evaluated or actioned yet.

---

## What needs adapting

### 1. Apply v2 workflows and rules on all other projects — new

**Previous assumption:** n/a — new idea.
**Revised assessment:** not yet evaluated.
**Impact on plan:** unknown — could mean porting CLAUDE.md/memory
structure, the PIN workflow, the Change execution model, etc. to other
repos.
**Action:** discuss scope with Adam — which projects, which parts of the
v2 workflow, and whether "apply" means copy-once or keep-in-sync.

### 2. What can be done from the mobile phone — new

**Previous assumption:** n/a — new idea.
**Revised assessment:** not yet evaluated.
**Impact on plan:** unknown — likely about Cowork/Claude mobile access
to this workflow, not a repo change per se.
**Action:** clarify with Adam what "done" means here (read-only checks?
approvals? full sessions?) before scoping any work.

### 3. Can the AI portions of v2 be ported to another AI than Claude (Cowork/Code) — new

**Previous assumption:** n/a — new idea.
**Revised assessment:** not yet evaluated.
**Impact on plan:** could affect how much of CLAUDE.md/roles.md is
Claude-specific vs. portable; potentially a significant scoping question.
**Action:** discuss with Adam what's driving this (contingency planning?
vendor flexibility?) before analyzing portability.

### 4. De-Adamify the v2 end-product — new

**Previous assumption:** n/a — new idea.
**Revised assessment:** not yet evaluated.
**Impact on plan:** would mean genericizing Adam-specific references
(roles.md, CLAUDE.md, etc.) into a productized template component.
**Action:** clarify scope with Adam — is this about this template repo
specifically, or a downstream product? What stays as example content vs.
becomes configurable?

### 5. Simplifications to process due to no longer needed workflows/workflow steps — new

**Previous assumption:** n/a — new idea.
**Revised assessment:** not yet evaluated. Likely prompted by this
session's discovery that some process steps (e.g. routing doc-only
changes through Crog) were unnecessary/obsolete once the Chrome-direct
path was proven.
**Action:** next session, audit CLAUDE.md/docs/ROUTINES.md for other
steps that may now be redundant given the Change execution model split.

### 6. Graduation and ..wrap workflows — needed or obsolete? — new

**Previous assumption:** the graduation rule (every NEXT_SESSION.md entry
gets a disposition each touched session) and the `..wrap` stop-word flush
are both load-bearing parts of the session-end process.
**Revised assessment:** not yet evaluated — Adam is questioning whether
these are still needed or have become obsolete, possibly given how much
more is now committed directly and verifiably via PRs rather than relying
on end-of-session memory flushes.
**Action:** discuss with Adam what prompted this doubt — likely worth
revisiting once the six items in this file have their first real
graduation cycle, to see if the mechanism still earns its keep.

---

## Items that do not change

- The Chrome-web-editor direct-commit path (edit → commit to new branch →
- PR → verdict comment → squash-merge → delete branch) is confirmed
- working for doc-only changes, no Crog, no local git. See PBI-4.1 in
- docs/BACKLOG.md and memory/decisions.md.
- - Code/src changes still route through Crog (implements TDD-first, opens
  - PR); Clead reviews as a structurally isolated invocation and posts the
  - verdict on the PR.
  - 
