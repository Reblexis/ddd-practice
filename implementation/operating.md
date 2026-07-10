# Operating: developing with agents in a docs-driven project

Implementation of [docs/practice.md](../docs/practice.md) — elaboration is this document's freedom; where it overlaps the [idea](https://github.com/Reblexis/docs-driven-development/blob/master/docs/idea.md), the idea is the source and wins. This is the day-to-day discipline once a project is adopted: the human programs in docs, agents make reality match them.

## The change flow

Every behavior change starts as a doc edit.

1. **Find the governing sentence.** Before changing what the software does, locate the doc sentence that owns that behavior.
2. **Change the doc first.** If the desired behavior contradicts the sentence, edit the sentence — or propose the edit to whoever owns that doc layer. If the docs are silent and the change is internal to one component, that silence is freedom: just build it. If the docs are silent and the change crosses a boundary other components or agents depend on, write the missing sentence at the right layer before building.
3. **Conform the code.** Agents implement whatever the changed doc now requires — in the same commit as the doc change at the latest, never after. Whether they evolve the existing code or rewrite it is purely a cost question; if the result satisfies the docs, either path was correct.

Code-only behavior changes are violations, even good ones. A fix worth keeping is worth a doc sentence.

## The conformance loop

Periodically — after significant churn, on a schedule, or on demand — verify that the code still satisfies the docs. The party that verifies must not be the party that wrote the code: a separate agent, a separate session, anything without the author's blind spots. Self-graded conformance is how "docs-driven" degrades into "docs-adjacent".

The auditor reads the governing docs fully, lists every checkable claim (the precise ones first), and checks each against the implementation. Every divergence gets classified, and the classification decides which side gets fixed:

- **Code bug** — the doc is right, the code fails it. Fix the code.
- **Doc bug** — the code's behavior is sensible, the doc describes reality wrongly or stalely. Fix the doc.
- **Ambiguity** — two readings are plausible and the code picked one. Tighten the one sentence that was underspecified — nothing more. Resist the reflex to make the whole document rigid because one sentence was loose.
- **Unspecified** — the code does something significant the docs never mention. If other components or agents depend on it, write it into the docs (or remove the behavior — that choice is the owner's when it touches intent). If it is internal, leave it alone; that is the freedom the docs granted.

The auditor also reports what verified as conforming, so clean areas are known and trust in the docs is earned rather than assumed.

## Layers and where precision lives

Docs form a hierarchy: broad intent at the top, contracts in the middle, component detail at the bottom. Lower layers must be consistent with higher ones; a conflict is resolved upward — the higher layer wins and the lower doc gets fixed.

Precision concentrates at boundaries. Ambiguity inside one component is free, because nobody else depends on those choices. Ambiguity at an interface — a protocol, a payment rule, a message format — is where two correct implementations collide. When agents diverge or integrations break, the failure names the sentence that was too loose; tighten that sentence and nothing else.

## The human-readable mirror

Humans read the HTML rendering, not `./docs` — so the mirror is maintained like code: any commit that changes a doc updates the rendering in the same commit, and the conformance loop checks mirror-vs-docs exactness the same way it checks code-vs-docs (a stale or embellished mirror is a divergence; the docs win). Keep the rendering outside `./docs`, organized as the repo's browsing entry (e.g. `index.html` at the root, or a `browse/` folder for multi-page renderings).

## Promotion: how the docs learn

When a bug fix, an incident, or a discovered edge case encodes a real behavioral rule, promote the rule into the docs at the layer where it belongs. Code remembers nothing across a rewrite; docs remember everything. A rule that lives only in code is one regeneration away from being lost.

This is also how ambiguity gets resolved permanently: each divergence event ends with either a corrected artifact or a tightened sentence, and the tightened sentence prevents the whole class of divergence, not just the instance.

## Talking to the human

The human reads docs, not code. Report in terms of docs and observable behavior: which doc claims held, which were violated and how it showed, what changed and in which document. Never ask the human to read or judge code.

Decisions that belong to the human — anything that changes intent rather than corrects drift — are brought as proposed doc edits: here is the sentence, here is what it would become, here is why. The human's answer is an edit, and the edit is the decision. Everything below the abstraction level the human chose to write at is not their problem; that is the point.
