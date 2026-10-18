# slipbox.kb

**Slip-box**: a knowledge-base type for [AutoDoc](https://github.com/yongjohnlee80/autodoc).

A slip-box, after Sönke Ahrens's *How to Take Smart Notes*: every permanent note goes into one flat box, named by ID, with no folders inside it. Order comes only from links and from index entry points. Reference notes keep the bibliography; project folders hold the writing that draws on the box.

## Install it in AutoDoc

You need [AutoDoc](https://github.com/yongjohnlee80/autodoc) v0.2.0 or later ([install AutoDoc](https://github.com/yongjohnlee80/autodoc#install)).

**A new KB:**

1. In AutoDoc, open **Go › Manage workspaces…** and press **Add…**.
2. Type a **root** for the KB, then press **New Folder** to create it (or **Browse…** to pick an empty folder).
3. In **KB type**, choose **Slip-box**. AutoDoc shows its folders below.
4. Press **Save**. AutoDoc creates the folders and files, and starts indexing.

**An existing workspace:** open it, then run the command `kbtype.apply slipbox.kb`.

**From this repository's URL** (a fork, or a type not in the list): choose **Custom URL…** in **KB type**, paste `https://github.com/yongjohnlee80/slipbox.kb`, and press **Stage**.

AutoDoc only ever creates files. It never overwrites or deletes one you have, so applying a type to a folder that already has notes adds what is missing and leaves everything else as it is. Nothing in this repository runs on your machine: AutoDoc reads its text files and copies them.

## What you get

```text
<your KB>/
├── AGENTS.md         # the agent contract: how agents work in this KB
├── ABOUT.md          # what this KB is, and which type and commit it came from
├── CLAUDE.md         # points Claude Code at AGENTS.md
├── GEMINI.md         # points Gemini CLI at AGENTS.md
├── KB_OPERATIONS.md  # AutoDoc's manual for searching and writing (added by AutoDoc)
├── RULES.md          # your own standing rules; agents read them first
├── inbox/            # fleeting notes, emptied often
│   └── ABOUT.md
├── slipbox/          # every permanent note, one flat folder, named by ID
│   └── ABOUT.md
├── references/       # one note per source, with its bibliographic details
│   └── ABOUT.md
├── projects/         # drafts that draw on the slip-box, one folder per project
│   └── ABOUT.md
├── _templates/       # a template per note type
│   ├── _ABOUT.md
│   ├── capture.md
│   ├── draft.md
│   ├── reference.md
│   └── slip.md
└── _schema/          # the frontmatter types this KB validates
    ├── _ABOUT.md
    └── frontmatter.yaml
```

## The folders

| Folder | What it is for |
|---|---|
| `inbox/` | fleeting notes, emptied often |
| `slipbox/` | every permanent note, one flat folder, named by ID |
| `references/` | one note per source, with its bibliographic details |
| `projects/` | drafts that draw on the slip-box, one folder per project |
| `_templates/` | a template per note type |
| `_schema/` | the frontmatter types this KB validates |

Every folder has an `ABOUT.md` (`_ABOUT.md` in the folders starting with `_`). It says what belongs there, how files are named, and which document type they use. Agents and people read the same descriptions.

## How it works

1. **Jot** fleeting notes in `inbox/` as they come.
2. **Note sources** in `references/`: one per source, with its bibliographic details and what you took from it.
3. **Write slips** into `slipbox/`: one idea each, in your own words, named by ID, and linked to the slips it relates to. There are no subfolders: the links are the structure.
4. **Write** in `projects/`: a draft assembled from slips. When it's done, its slips stay in the box.

It differs from the Zettelkasten type on purpose: there, each kind of note has a folder; here, every permanent note shares one flat box.

## Notes and their frontmatter

Each note starts with YAML frontmatter. Its `type` says what kind of note it is:

| `type` | Used for |
|---|---|
| `capture` | a fleeting note in the inbox, before it becomes a slip or a reference |
| `slip` | a permanent note in the slip-box, named and identified by its `id`; `kind: index` makes it an entry point |
| `reference` | a source's citation (`citekey`) and what you took from it |
| `draft` | writing in progress for a project, drawing on the slips |
| `about` | a folder's description: its `ABOUT.md` |
| `kb` | the KB's own files: `AGENTS.md`, `RULES.md`, `KB_OPERATIONS.md`, the pointers |

- `_schema/frontmatter.yaml` defines the fields of each type. AutoDoc checks every note against it and shows what's missing. It never blocks a save, and it never rewrites your files.
- `_templates/` has a template per type. Start a note from one, and its frontmatter starts valid.
- The schema is this KB's own: change it to fit how you work.

## How agents help manage this KB

AI agents (Claude Code, Codex, Gemini CLI, and others) work in this KB through the files at its root:

1. **`RULES.md` first:** your standing rules. Only you edit it, and agents follow it before anything else.
2. **`AGENTS.md`:** the agent contract for this type. It covers the hard rules, searching before writing, the frontmatter, and what goes in each folder.
3. **`KB_OPERATIONS.md`:** AutoDoc's manual for searching, reading and writing through AutoDoc. AutoDoc writes and updates it.
4. **Each folder's `ABOUT.md`:** what belongs in that folder.

`CLAUDE.md` and `GEMINI.md` exist only to point those tools at `AGENTS.md`.

What `AGENTS.md` asks of an agent:

- **Search before writing:** use AutoDoc's search, then extend or link an existing note rather than writing a near-duplicate.
- **Cite, don't fabricate:** every claim points at its source.
- **Ask before restructuring:** never move, rename or merge your notes on its own.
- **No secrets:** never write credentials into the KB.

- **Link, don't copy.** Connect a note to the ones it builds on with `[[wikilinks]]`; a link is part of the note's meaning.
- **The box stays flat.** Never create folders inside `slipbox/`; propose an index slip instead.

Agents started from AutoDoc's agent panel get `$AUTODOC_WORKSPACE` and `$AUTODOC_ROOT`, so they search and write in this KB through AutoDoc. Add your own rules for them in `RULES.md`, or below the last section of `AGENTS.md`.

## Make your own type

Every AutoDoc KB type is a repository with the same layout:

```text
kbtype.toml    the type: its name, title, folders and their purposes, and the workspace settings it proposes
tree/          the KB as it is created: every file here is copied into the new KB
README.md      this file (never copied)
```

To make your own, fork this repository and change `kbtype.toml` and `tree/` together:
- every `[[folder]]` needs its `ABOUT.md` in `tree/`;
- every folder in `tree/` needs its `[[folder]]`.

Check it with `autodoc --check-kbtype .`, then give AutoDoc your repository's URL.

## License

Apache License 2.0. See [LICENSE](LICENSE).
