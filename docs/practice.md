# DDD Practice

This repo describes a specific way to practice [docs-driven development](https://github.com/Reblexis/docs-driven-development/blob/master/docs/idea.md): how to adopt it in an existing project, and how to use and develop with it when AI agents write the code.

Everything else in the repo is the implementation of that description. The idea's rules apply here by reference; where the implementation contradicts this document or the idea, the implementation is wrong.

When adopting in a project that already has a `./docs`, the existing docs are not kept as they were: they are reworked into the standard structure, and content that does not belong in the docs moves elsewhere in the repo — described abstractly in the docs where needed.

The repo ships an installable skill for AI agents, at `skill/`: it describes how to practice this — adopting and operating per this repo — consistently with this document, and installs by copying the folder into an agent's skills directory. Everything else about the skill is its implementation.

The docs must be as easy for a human to understand as possible while staying complete: HTML document(s) generated inside the repo render them visually, so the human reads the HTML, not `./docs`. The HTML reflects `./docs` exactly — nothing hallucinated on top, nothing missing. The docs themselves may be whatever format best represents the information: markdown is the base, but HTML, images (e.g. `.png`), or even video belong in `./docs` when they represent it better. The human-readable rendering lives outside `./docs`, properly organized.

Every repo using this practice states at the bottom of its README that it uses this practice (linked), describes how its `./docs` is structured, and says where the human-readable representation lives.
