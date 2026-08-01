# Cleanup — Calibration (template)

Copy this to **one** of the three lookup locations and fill it in:

```
1. <repo>/.claude/calibration/cleanup.local.md
2. ~/.claude/calibration/operational.local.md     # usual home; serves every skill
3. CALIBRATION.local.md beside SKILL.md
```

**Never commit the result.**

If you also use `session-rituals`, keep **one** copy of the surface list and the
store operations — its close phase delegates to this skill, and two lists
describing one truth is the failure this skill exists to catch. A machine-wide
register (rung 2) is the natural single home.

---

## Sweep Scope

Which repository, namespace and tracker belong to the programme being swept, and
which are explicitly **out of scope** from this machine. A programme with no row
is not swept: stop and say so rather than improvising.

## Durable-Claim Surfaces

Everything that asserts something a reader would act on. Anything not listed
here will not be examined, so an omission is silent.

| Surface | Path | Notes |
|---|---|---|
| Entry-point doc | `README.md` | First contact; highest cost when wrong. |
| Agent instructions (tracked) | | |
| Agent instructions (local/gitignored) | | **Reached by no CI or review gate** — a sweep is the only thing that finds drift here. |
| Design / strategy / process docs | | Quietly superseded by later decisions. |
| Skills, commands and their READMEs | | |
| Published interface descriptions | | Read by clients as authoritative. |
| Example or starter projects | | Copied by newcomers, so errors propagate. |

Add the agent's own persistent memory directory and its index — recalled as
background context, so it drifts invisibly.

## Records — Never "Correct" These

List the documents and fields that answer *"this is what happened"*: sprint
histories, retrospectives, session and sweep logs, approved briefs, completion
reports, dated evaluations. Correcting one falsifies history; annotate alongside
instead, and re-read immediately before appending because shared narrative
fields usually have more than one author.

Note also that a **reference** document can contain **record lines** — a
provenance line naming where something was first published is history, and a
find-and-replace sweep that "fixes" it turns a true statement false.

## Store Operations

Which tool reads, writes and retires a fragment; whether a write overwrites the
whole body (if so, read first, always); the size cap and the archive procedure
when a record approaches it; and whether a curated index must be updated in the
same pass when something is retired.

For plain-file memory: correct with an edit, retire by deleting the file **and**
its line in the index. Removing one without the other is how the two drift
apart.

## Claims That Assert External State

The class this skill cannot check by reading the tree — and for each, **how to
check it**:

- Credentials, tokens, expiries, account and connector bindings.
- Published package or image versions versus what is on the default branch.
- Advisory waivers and their review-by dates, across every file that restates
  them (they must agree).
- The required-check list versus the jobs that actually exist.
- Anything a third party can change without telling you.

Record any scanner or CLI invocation that needs a specific flag to be truthful,
and what a wrong invocation looks like — a misleading pass or an invented
failure is worse than no check.

## Reporting

Where the sweep result is written, and when relative to a retrospective or
planning session. Mirror durable corrections into the shared store in the same
pass.
