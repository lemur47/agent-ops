# Ship — Calibration (template)

Copy this to **one** of the three lookup locations and fill it in:

```
1. <repo>/.claude/calibration/ship.local.md
2. ~/.claude/calibration/operational.local.md     # usual home; serves every skill
3. CALIBRATION.local.md beside SKILL.md
```

**Never commit the result.**

A note specific to this skill: rung 3 is the shape it is most likely to get
wrong. `ship` is invoked *from* a repository, so an overlay sitting beside the
skill looks local when it is machine-wide — run the loop in a second repository
and it will silently apply the first one's required-context list and approval
authority. Prefer rung 2, and give each repository its own section.

Most of what the loop needs is **discovered, not configured**: gate invocations
live in the workflow files and the hook config, and reading them is the point.
This file holds only what cannot be read off the repository — plus the traps
that have already cost you time.

---

## Approval

**Who merges.** The loop terminates at green-awaiting-approval and never merges,
including for a documentation-only change. Name the approver, and say whether
anything is ever exempt.

## Required Contexts and Merge Sequencing

Per repository:

- **The required checks, named** — and the command to re-read them from the
  host rather than trusting this list. Checks that are *required* and checks
  that merely *exist* are different sets, and calling the wrong one blocking
  wastes a wait.
- **Whether branch protection is strict / up-to-date.** If it is, a prerequisite
  merge voids every other branch's green: merge the prerequisite, update this
  branch, then wait for the **full** set to re-run.
- **Checks that are conditional**, and on what. A preview deploy that only runs
  when the change touches a particular directory will be absent on other
  changes — absence is not a missing check.
- **Checks that report a misleading intermediate state** — anything that reads
  as skipped or failed while it is still resolving, and how to confirm properly.
- **Branch and merge conventions** — naming, whether commits on the default
  branch are ever acceptable, squash versus merge, and how to recover a commit
  that landed on the default branch by accident.

## Gate Traps Already Paid For

The point of this section is that each entry cost someone real time once.

For each: **what goes wrong, what it looks like, and what the correct
invocation or response is.** Especially worth recording —

- Scanners needing an explicit config flag to be truthful, where the wrong
  invocation produces a convincing false failure whose tempting "fix" would
  weaken a working control.
- Tools that fetch rules or advisory data live, so a gate can go red with no
  change to the repository.
- Two gates that restate the same waivers in different files and must be kept in
  step.
- Configuration that silently prevents hooks from installing at all, while the
  install output still reports success.
- Known pins or deferrals with an expiry date, and what goes red when it passes.

State each fact **once**. If a trap is already recorded in a shared section for
another skill, cross-reference it rather than copying it.

## Deviations

How a bypass is recorded — a bypass is never silent. Typically: the reason goes
in the commit message *and* the pull request body, the underlying problem is
raised as its own piece of work rather than folded into an unrelated change, and
the tracker report carries an explicit deviations line either way.
