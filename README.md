# slipbox.kb

**Slip-box**, a KB type for [AutoDoc](https://github.com/yongjohnlee80/autodoc).

A slip-box, after Sönke Ahrens's *How to Take Smart Notes*: every permanent note goes into one flat box, named by ID, with no folders inside it. Order comes only from links and from index entry points. Reference notes keep the bibliography; project folders hold the writing that draws on the box.

## Folders

| Folder | Purpose |
|---|---|
| `inbox/` | fleeting notes, emptied often |
| `slipbox/` | every permanent note, one flat folder, named by ID |
| `references/` | one note per source, with its bibliographic details |
| `projects/` | drafts that draw on the slip-box, one folder per project |
| `_templates/` | a template per note type |
| `_schema/` | the frontmatter types this KB validates |

Every folder gets an `ABOUT.md` (`_ABOUT.md` in the `_` folders) saying what belongs there. The root
gets `AGENTS.md` (the agent contract), `ABOUT.md`, `RULES.md` (your own rules), and `CLAUDE.md` and
`GEMINI.md`, which point agents at `AGENTS.md`. AutoDoc adds `KB_OPERATIONS.md`, its own manual for
searching and writing through AutoDoc.

## How it works

1. **Jot** fleeting notes in `inbox/` as they come.
2. **Note sources** in `references/`: one per source, with its bibliographic details and what you took from it.
3. **Write slips** into `slipbox/`: one idea each, in your own words, named by ID, and linked to the slips it relates to. There are no subfolders: the links are the structure.
4. **Write** in `projects/`: a draft assembled from slips. When it's done, its slips stay in the box.

It differs from the Zettelkasten type on purpose: there, each kind of note has a folder; here, every permanent note shares one flat box.

## Use it

In AutoDoc: **Workspace › Add…**, pick a root (or **New Folder**), and choose **Slip-box** as the KB type.
For a workspace you already have: **Apply KB type…** in the workspace manager.

AutoDoc only ever creates files. It never overwrites or deletes one you have, so applying a type to
an existing folder adds what is missing and changes nothing else.

## This repository

Every AutoDoc KB type has the same layout:

```text
kbtype.toml    what the type is, its folders and their purposes, the workspace settings it proposes
tree/          the KB as it is created: every file here is copied into the new KB, create-only
README.md      this file (never copied)
```

Nothing here runs: AutoDoc reads `kbtype.toml` and copies `tree/`'s text files. To make your own
type, fork this repo, change `kbtype.toml` and `tree/` together (every `[[folder]]` needs its
`ABOUT.md` in `tree/`, and every folder in `tree/` needs its `[[folder]]`), and give AutoDoc your
repo's URL.

## License

Apache License 2.0. See [LICENSE](LICENSE).
