# Commands

Slash commands that run *the ritual around the work*, not the work itself.

They pair with the [skills](../skills/README.md): the command is the thin,
invocable entry point; the skill holds the method. Commands are version-tracked
here and activated by symlink into the user scope, so they are available from
**every** repository rather than one.

| Command | Purpose |
|---------|---------|
| [`/boot-ritual`](boot-ritual.md) | Open a session — read shared memory, verify it against repository and tracker ground truth, correct what drifted, classify inbound pull requests, report, and hand into planning or execution. |
| [`/close-ritual`](close-ritual.md) | Close a session — write changes back to shared memory, sweep durable claims for staleness, open a documentation pull request if needed, and log a handover the next session or machine can start from. |
| [`/ship`](ship.md) | Drive the current change to a merge-ready pull request — reproduce the gates as CI runs them, triage any red, sequence the merge, and stop at green-awaiting-approval. |

The first two invoke [`session-rituals`](../skills/session-rituals/SKILL.md); the
third invokes [`ship`](../skills/ship/SKILL.md). All three read their
organisation's values from an uncommitted calibration overlay, resolved by the
three-rung lookup described in the [repository README](../README.md#method-is-public-your-values-are-not).

## Activation

See [Installing](../README.md#installing) in the repository README — the symlink
commands are given once, there, for both skills and commands together.

**Verify in a fresh session rather than assuming.** A command only ever fires
when it is invoked; the symlink makes it *available*, not automatic.

## A Note on Scope

These commands read and reconcile. They do not merge pull requests, start
approved work, or change behaviour. The only commit a ritual makes is
documentation, on its own branch, for someone else to merge.
