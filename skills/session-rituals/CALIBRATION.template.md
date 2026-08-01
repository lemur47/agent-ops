# Session Rituals — Calibration (template)

Copy this to **one** of the three lookup locations and fill it in:

```
1. <repo>/.claude/calibration/session-rituals.local.md
2. ~/.claude/calibration/operational.local.md     # usual home; serves every skill
3. CALIBRATION.local.md beside SKILL.md
```

**Never commit the result.** It will carry tracker identifiers, memory
namespaces and machine ownership. The `.gitignore` refuses `*.local.md`, but do
not rely on the backstop.

If you keep several skills' values in one machine-wide file (rung 2), make each
skill a section of it rather than creating one file per skill — the register's
whole job is to be the single place these questions are answered.

---

## Programme Register

One row per programme. **Resolve the programme from the working directory.** A
directory matching no row, or more than one, is a question to ask — not a
default to pick.

| | **<programme-a>** | **<programme-b>** |
|---|---|---|
| Repo | `<path>` | `<path>` |
| Remote | `<host/org/repo>` (public\|private) | |
| Default branch | `<branch>` | |
| Memory namespace | `<namespace>` | |
| Boot fragments, in order | `<first>` → `<second>` → `<third>` | |
| Other streams | `<names>` | |
| Work tracker | `<system + workspace>` | |
| Runbook / instruction file | `<filename>` | |
| Session log | `<where the close phase appends>` | |

State which machine each programme is worked on from, and which programmes are
**not** served here at all. A programme with no row is not swept: the ritual
stops and says so.

## Precedence and Scope

- Which surface wins per question — the skill states the default; record any
  deviation your setup needs.
- **Sweep the resolved programme only**: its repository, its namespace, its
  tracker. One programme at a time, whichever one you resolved.

## Durable-Claim Surfaces

One list per programme — the sweep scope for the close phase.

| Surface | Path | Notes |
|---|---|---|
| Entry-point doc | `README.md` | |
| Agent instructions (tracked) | | |
| Agent instructions (local/gitignored) | | **No CI or review gate touches this** — only a sweep finds drift here. |
| Design / strategy docs | | |
| Skills, commands, other tracked prose | | |

Also list, per programme, which documents are **records** — anything answering
"this is what happened" rather than "this is how things are". Those are
append-only and must never be "corrected".

## Store Operations

Which tool reads, writes and retires a memory fragment; whether a write
overwrites the whole body (if so, always read first); any size cap and what to
do when a record reaches it (archive verbatim, never truncate); and whether a
curated index exists that must be updated when a fragment is retired.

## Claims That Assert External State

The things no repository can notice going stale — credentials and expiries,
published package versions versus the tree, advisory waivers and their review-by
dates, the required-check list versus the jobs that exist, third-party account
or connector state. Say **how to check each one**, not just that it exists.

## Tracker Detail

Where identifiers, field names and status values live; which status means
"approved and safe to start"; where reports are written (a record's comments
versus its body); and any query quirk that silently returns nothing when you get
it wrong. If two trackers are in play, state plainly that they have different
vocabularies.

## Gates

Approval authority — **who merges**, given the ritual never does. Then the
repository-specific controls: required contexts, secret and identifier scanning,
commit-message hooks, and any configuration that must *not* be set because it
silently disables a hook.

## Reporting

Where each phase's result goes: the tracker, the session log, the shared store —
and the rule that a correction made in the repository is mirrored into the store
in the same pass. A sweep that fixes one and leaves the other has moved the
problem, not solved it.

## Cross-Machine

Which handovers belong in which namespace, and any **deliberate** divergence
between machines that must not be "reconciled" by a future sweep. Record why,
or someone will helpfully undo it.
