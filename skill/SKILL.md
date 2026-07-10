---
name: ddd-practice
description: >
  Practice docs-driven development the ddd-practice way: adopt DDD in an
  existing project (declare, bootstrap, reconcile) and operate day-to-day
  with agents (doc-first changes, conformance loop, divergence
  classification). Use when asked to "adopt ddd-practice", "make this
  project docs-driven", "run the adoption moves", or when operating in a
  repo that names ddd-practice as its practiced design.
---

# ddd-practice

Governing docs: `docs/practice.md` in
https://github.com/Reblexis/ddd-practice (one specification: this is a
specific way to practice the docs-driven idea — adopting it in existing
projects and developing with AI agents). This skill is implementation of
that practice, like the repo's `implementation/` documents, which are
the authoritative elaboration:

- `implementation/adoption.md` — the three moves for an existing
  project: **declare** (docs govern, stated in `./docs`; README becomes
  a derived summary), **bootstrap** (build the hierarchy under `./docs`
  from existing docs, code, and the owner's intent — promote, don't
  duplicate), **reconcile** (run the first conformance audit
  immediately and fix what it finds).
- `implementation/operating.md` — the day-to-day loop: every behavior
  change starts as a doc edit; a non-author verifies conformance; each
  divergence is classified (code bug / doc bug / ambiguity /
  unspecified) and fixed on its own side; learned rules get promoted
  into the docs; the human is spoken to in docs and observable
  behavior, with decisions framed as proposed doc edits. The repo
  keeps a human-readable HTML mirror of `./docs` (exact — nothing
  added, nothing missing), outside `./docs`, updated in the same
  commit as any doc change; the README ends with a footer naming the
  practice (linked), the `./docs` structure, and the mirror location —
  and mentions the practice nowhere else (the repo reads like any repo
  with docs). `./docs` states that anyone developing or contributing
  follows the practice: docs first, everything else conforms. A repo
  created by copying a practicing repo (a fork, a template) inherits
  derived artifacts that describe the source and are wrong from the
  moment the copy exists: regenerate the README and mirror against the
  new repo's own `./docs` at creation, and update any doc that governs
  the new repo's existence elsewhere (a parent's member list, a
  registry) in the same stroke.

When executing, follow those two documents; where they and any project's
own docs differ, the project's docs win. Where anything here contradicts
`docs/practice.md` or the docs-driven idea, this skill is wrong.

## Installing this skill for an agent

Copy (or symlink) this `skill/` folder into the agent's skills
directory as `ddd-practice/`, e.g.:

    git clone https://github.com/Reblexis/ddd-practice
    ln -s "$PWD/ddd-practice/skill" ~/.claude/skills/ddd-practice
