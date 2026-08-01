# agent-ops

Operational skills and commands for coding agents — the rituals *around* the
work rather than the work itself.

A coding agent is good at the task you hand it and bad at everything the task
sits inside: knowing what changed while it was away, noticing that a document
now describes a world that no longer exists, telling its own red from someone
else's, and stopping before it publishes something it should not. Those are
recurring, describable procedures. This repository is four of them.

| Skill | What it is for |
|-------|----------------|
| [`session-rituals`](skills/session-rituals/SKILL.md) | Open and close a working session. Reconcile shared memory against the repository and the work tracker, absorb what arrived, and leave a handover the next session can start from. |
| [`cleanup`](skills/cleanup/SKILL.md) | Sweep the surfaces carrying durable claims — README, agent instruction files, docs, shared memory — for statements reality has moved past, and correct, flag or retire them. |
| [`ship`](skills/ship/SKILL.md) | Drive a change from working tree to merge-ready. Reproduce the gates exactly as CI runs them, triage whose red it is, sequence the merge — and never make a check pass by weakening it. |
| [`anonymisation`](skills/anonymisation/SKILL.md) | Extract lessons from real engagement experience without exposing the parties, before anything reaches a public surface. |

Three of them have a thin slash-command entry point in
[`commands/`](commands/README.md): `/boot-ritual`, `/close-ritual`, `/ship`.

## The Idea

Every one of these skills was written after the same thing went wrong twice.

That matters more than it sounds. A rule you write down once and re-read at boot
is a rule you will skip when you are busy — and the failure it guards against
usually looks, in the moment, like being efficient. The value here is not the
prose. It is that the procedure runs *as a procedure*, with a fixed report shape
at the end, so skipping a step is visible rather than silent.

Two convictions run through all four:

- **A surface nothing tests will drift.** Code has tests; prose, shared memory
  and instruction files have nothing. Whatever is true of them stays true only
  because someone checks, and "confidently wrong" is far more expensive than
  "empty" — an empty note makes you go and look, a wrong one does not.
- **Exercise the mechanism; never trust the install output.** A configuration
  that reports success and never loads is the failure mode these skills hit most
  often. Verify by running the thing, not by reading the confirmation.

## Method Is Public; Your Values Are Not

Each skill keeps **universal method** in its tracked `SKILL.md`, and everything
specific to an organisation — namespaces, tracker identifiers, approval
authority, machine ownership, the traps that have already cost *you* time — in a
**calibration overlay that is never committed.**

Skills resolve their overlay in this order and take the first hit:

```
1. <repo>/.claude/calibration/<skill>.local.md   # this repository's own values
2. ~/.claude/calibration/operational.local.md    # machine-wide, serves every skill
3. <skill>/CALIBRATION.local.md                  # beside the skill
```

**Rung 2 is the usual home**, because one machine normally works across several
repositories. An overlay that only ever sits beside the skill describes whichever
repository happened to author it; every other repository then gets either
nothing or, worse, that first one's values applied silently. A machine-wide
register keyed by working directory serves them all from one place — and, being
outside every tree, it does not travel with a repository you hand over.

Rung 1 wins where a repository's values are genuinely its own and should move
with it. Rung 3 is the simplest and is all a single-repository setup needs.

Each skill ships a `CALIBRATION.template.md` showing the shape with none of
anyone's values in it. Copy it to one of the three locations above and fill it
in. **Do not commit the result** — not to a public repository and not to a
private one. These files typically carry tracker identifiers and internal
namespaces, and the whole value of the split disappears the moment a copy is
versioned. The `.gitignore` here refuses `*.local.md` as a backstop, but the
backstop is not the reason.

If no overlay resolves, a skill says so and stops rather than guessing. A guessed
namespace writes memory nobody will read again; a guessed tracker filter returns
nothing and looks exactly like "no open work".

## Installing

Skills and commands reach a session by symlink, so one clone serves every
repository you work in:

```bash
AGENT_OPS="$HOME/projects/agent-ops"     # wherever you cloned it
mkdir -p "$HOME/.claude/skills" "$HOME/.claude/commands"

for s in session-rituals cleanup ship anonymisation; do
  ln -sfn "$AGENT_OPS/skills/$s" "$HOME/.claude/skills/$s"
done

for c in boot-ritual close-ritual ship; do
  ln -sfn "$AGENT_OPS/commands/$c.md" "$HOME/.claude/commands/$c.md"
done
```

User scope, not project scope: a `.claude/skills/` symlink inside one repository
is visible only from that repository, which is the wrong shape for a ritual
serving several.

**Then verify, in a fresh session**, that the skills appear in the available
list and the commands are offered. Do not skip this because the `ln` commands
printed no error. Silent non-activation — while the documented remedy reports
success — is a mistake this toolchain has already made more than once, which is
why it is called out twice on this page.

Note also that a command only fires **when it is invoked**. The symlink makes it
available, not automatic.

## Contributing

Issues are welcome. **Please do not open pull requests** — this repository does
not accept them, for supply-chain reasons. Describe the problem or the
improvement in an issue and it can be written here.

## Licence

MIT. See [`LICENSE`](LICENSE).
