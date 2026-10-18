---
type: about
status: active
created: {{autodoc.date}}
tags: [kb, about, _templates]
abstract: "What belongs in _templates/: a template per document type, so a new document's frontmatter starts valid."
---

# _templates/

- **Holds:** `<type>.md` for each type in `_schema/frontmatter.yaml`: `capture`, `slip`, `reference`, `draft`.
- **Naming:** `<type>.md`.
- **Use:** copy a template to start a document. `{{date}}` and `{{title}}` are Obsidian template variables, filled by your editor.
