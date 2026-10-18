---
type: kb
kind: agents
status: active
created: {{autodoc.date}}
tags: [kb, agents]
abstract: "The agent contract for this KB. Read RULES.md first, then this file, then KB_OPERATIONS.md."
---

# Agent contract: Slip-box

This KB is a slip-box: one flat box of permanent notes, ordered only by their links. Help the user write slips and find connections; never sort the box into folders.

## 0. Order of authority

1. **`RULES.md`**: the user's standing rules for this KB. It comes first among the KB's own files
   and the files that point into it. It doesn't override your system or safety instructions, or
   the user's own instruction in the conversation.
2. **This file.**
3. **`KB_OPERATIONS.md`**: how to search, read and write through AutoDoc. It is AutoDoc's, versioned
   with AutoDoc; re-read it when its `revision:` changes.
4. **The folder's `ABOUT.md`** (`_ABOUT.md` in `_templates/` and `_schema/`): what belongs in that folder.

## 1. Hard rules

- **Cite, don't fabricate.** A claim about a source points at it: a document, a page, a link. If
  you can't find a source, say so.
- **Detail is load-bearing.** Keep the specifics (names, numbers, dates, quotes) that make a note
  useful later.
- **Ask before restructuring.** Moving, renaming or merging the user's notes changes their links
  and their thinking: propose it, don't do it.
- **No secrets.** Never write credentials, tokens, passwords or private keys into the KB.
- **Link, don't copy.** Connect a note to the ones it builds on with `[[wikilinks]]`; a link is part of the note's meaning.
- **The box stays flat.** Never create folders inside `slipbox/`; propose an index slip instead.

## 2. Search first

Before reading broadly or writing, search through AutoDoc
(`autodoc --call search.query '["'"$AUTODOC_WORKSPACE"'", "<words>", {"limit": 10}]'`) and read the
hits' line ranges. Extend or link an existing note rather than writing a near-duplicate.
`KB_OPERATIONS.md` has the filters, the listings, history and the fallback.

## 3. Frontmatter

Every document starts with YAML frontmatter valid against `_schema/frontmatter.yaml`:

- `type` picks the document type: capture, slip, reference, draft, about (a folder's descriptor) or kb (the KB's own files).
- Every type requires `status` and `created` (YYYY-MM-DD). `tags`, `abstract` (one to three
  sentences: what the note says) and `title` are optional, and worth writing: AutoDoc searches them.
- The YAML is the source of truth: no inline `**Tags:**` lines.
- Start a document from `_templates/<type>.md`, so its frontmatter starts valid.
- Check a draft with `doc.validate` (KB_OPERATIONS.md).

## 4. Where things go

Each folder's `ABOUT.md` says what belongs there, the file naming and the `type`. In short:

| Folder | Holds |
|---|---|
| `inbox/` | fleeting notes, emptied often |
| `slipbox/` | every permanent note, one flat folder, named by ID |
| `references/` | one note per source, with its bibliographic details |
| `projects/` | drafts that draw on the slip-box, one folder per project |
| `_templates/` | a template per note type |
| `_schema/` | the frontmatter types this KB validates |

When unsure, search `"<what you're writing>" type:about`.

## 5. This KB's own rules

<!-- Add this KB's own conventions below. AutoDoc never rewrites this file once it exists. -->
