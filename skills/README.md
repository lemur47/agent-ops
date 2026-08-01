# Skills

Four skills that govern *how the work is done*.

They are operational and editorial guardrails applied to the work itself, not
domain logic — there is no library underneath them to verify against, which is
precisely why each one carries its own fixed report shape instead.

| Skill | Purpose |
|-------|---------|
| [session-rituals](session-rituals/SKILL.md) | Open and close a working session: reconcile shared memory against repository and tracker ground truth, absorb what arrived while you were away, and leave a handover the next session or machine can start from. Invoked via [`/boot-ritual` and `/close-ritual`](../commands/README.md). |
| [cleanup](cleanup/SKILL.md) | Sweep the surfaces that carry durable claims — README, agent instruction files, docs, shared memory — for statements reality has moved past, and correct them, mark them unverified, or retire them. |
| [ship](ship/SKILL.md) | Drive a change from working tree to merge-ready: reproduce the gates exactly as CI runs them, triage whose red it is, sequence the merge — and never make a check pass by weakening it. Invoked via [`/ship`](../commands/README.md). |
| [anonymisation](anonymisation/SKILL.md) | Extract lessons from real engagement experience without exposing the parties. Binding the moment material moves toward a public surface. |

`session-rituals` carries two reference files alongside its `SKILL.md` —
[`BOOT.md`](session-rituals/BOOT.md) and [`CLOSE.md`](session-rituals/CLOSE.md),
one per phase — so a session that only opens does not load the closing method.

## How They Relate

`session-rituals` is the spine. Its closing phase delegates the staleness
question to `cleanup` rather than improvising a second version of it, and its
guardrails — records are append-only, the store loses to the working tree,
report in a fixed shape — hold across all four.

`ship` and `anonymisation` are gates rather than sweeps: each sits in front of an
irreversible step (a merge, a publication) and its job is to be willing to stop.

## Calibration

Every skill here keeps universal method in the tracked `SKILL.md` and
organisation-specific values in an uncommitted overlay, resolved by a three-rung
lookup. Each ships a `CALIBRATION.template.md` showing the shape.

The full explanation, the lookup order and the reason rung 2 is usually right
live in the [repository README](../README.md#method-is-public-your-values-are-not).
It is stated once, there, rather than restated per skill — two documents
describing one truth is the exact failure `cleanup` exists to catch.
