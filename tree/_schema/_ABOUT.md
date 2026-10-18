---
type: about
status: active
created: {{autodoc.date}}
tags: [kb, about, _schema]
abstract: "What belongs in _schema/: the frontmatter schema this KB's documents are checked against."
---

# _schema/

- **Holds:** `frontmatter.yaml`, the KB's frontmatter schema (AutoDoc's version 2: a `common` block, and fields per `type`).
- **Rules:** AutoDoc validates every document against it and reports a diagnostic; it never blocks a write or rewrites a file. Change it to fit how you work: it is this KB's own, not AutoDoc's.
