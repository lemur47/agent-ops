# Anonymisation — Calibration (template)

Copy this to **one** of the three lookup locations and fill it in:

```
1. <repo>/.claude/calibration/anonymisation.local.md
2. ~/.claude/calibration/operational.local.md     # usual home; serves every skill
3. CALIBRATION.local.md beside SKILL.md
```

**Never commit the result.** This is the overlay where committing the file would
do the exact damage the skill exists to prevent: it names the parties, the
agreements and the people. Unlike the others, the harm here is not staleness —
it is disclosure.

Values here are usually **single-organisation** rather than
single-repository, so one copy serves every repository you work from.

---

## Audience

Who the public writing is actually for, and what they already know. This decides
how much context can be cut before an example stops being useful — the
temptation under an anonymisation rule is to strip until the piece says nothing.

## Sign-Off

**Who owns the confidentiality decision**, and at which point they see the
material. Name a person or role, not a process. If the answer is "the author",
say so explicitly rather than leaving it unstated.

Also: what happens when the author and the sign-off owner disagree. The default
is that the material does not ship.

## Binding Agreements

The agreements that actually constrain you — non-disclosure terms, client
contracts, employment or partnership clauses, platform or professional-body
rules. For each, note anything unusual: a longer tail after an engagement ends,
a named-party restriction that survives indefinitely, a sector where even the
*category* identifies the client.

Note any engagement whose details are so distinctive that no amount of
generalisation is safe. That is a real category, and the honest answer for it is
"do not write about this one".

## Identifying Detail in Your Context

Beyond names, what would identify a party **to your readers**? Typically some
combination of sector, scale, geography, timeline and a distinctive technical or
organisational fact. Small markets are the hard case: "a mid-sized insurer in
<small market>, 2023" can be a unique identifier even with every name removed.

List the specific combinations that are unsafe for you, since this is entirely
context-dependent and a general rule cannot capture it.

## Default Fallback

What to do when an example cannot be made safe. Give a concrete order of
preference — for example: generalise to the pattern and drop the case entirely;
merge several engagements into a composite and label it as one; replace with a
constructed example and say that it is constructed; or cut the section.

**The fallback must never be "publish it and hope".** Write down what the
floor is, so the decision is not made under deadline pressure.
