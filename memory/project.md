# Project

**Name:** ai-project-template-v2
**Repo:** sugose/ai-project-template-v2
**Description:** A second-generation template for AI-assisted software
development using the Clead + Crog workflow. Built from scratch to replace
ai-project-template (v1), which accumulated complexity proportional to
workarounds rather than to the underlying problem.

**Goals:**
- A self-contained repo — clone it and everything needed to run the
  workflow (human or agent) is inside it
- Adam's involvement reduced to two touchpoints: describe the PBI,
  approve the merge
- No scaffolding inherited from constraints that no longer exist
- A workflow that a new Clead instance can cold-start from the repo
  alone, without Adam providing orientation

**Definition of done for this phase:**
The skeleton is committed and a real project (python-blackjack-v2) has
been successfully bootstrapped from it, proving the template works end
to end including the GitHub Actions review trigger and reviewer isolation.

## Migration source
N/A — this is the template repo itself, not a migration.
The reference implementation is sugose/ai-project-template (v1).
v1 is the source of learning, not the source of files.

## Active workstream as of 2026-06-27
Skeleton prompt has been executed by Crog. Repo now exists.
Next step: open Cowork, set working folder to this repo clone,
begin first Cowork-Clead session.
