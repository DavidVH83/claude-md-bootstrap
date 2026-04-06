# CLAUDE.md Bootstrap

> Paste one prompt. Get a complete, project-specific `CLAUDE.md` in one conversation.

---

## What is this?

A structured prompt that turns Claude into a guided interview.
It asks you the right questions about your project and outputs a ready-to-use `CLAUDE.md` — fully filled in, no placeholders, no guessing.

A `CLAUDE.md` tells Claude who you are, what your project does, how you work, and what it should never touch. The better your `CLAUDE.md`, the better Claude performs across every session.

---

## Why does this exist?

Setting up a `CLAUDE.md` from scratch is:
- Easy to forget sections
- Hard to know what to include
- Repetitive across projects

This prompt solves that. One paste. One conversation. Done.

---

## How to use

1. Open a **new conversation or project** in Claude (claude.ai or Claude Code)
2. Open `CLAUDE_md_bootstrap.md` and **copy the entire contents**
3. **Paste it as your very first message**
4. Claude will guide you through the rest — answer its questions
5. At the end, copy the generated `CLAUDE.md` into the root of your project

No installation. No setup. Works with any Claude interface.

---

## Example output

<details>
<summary>Click to see a generated CLAUDE.md example</summary>
```markdown
# CLAUDE.md — ML Testproject

## 1. Project Identity
| Veld     | Waarde                                                         |
|----------|----------------------------------------------------------------|
| Naam     | ML Testproject                                                 |
| Doel     | Verschillende ML-technieken leren kennen door ze uit te testen |
| Gebruiker| Alleen ikzelf                                                  |
| Fase     | Begin — losse experimenten, nog geen vaste structuur           |

## 5. Claude's Role
### ✅ Do freely
- Write new scripts or notebooks
- Set up experiments for a new ML technique

### ⚠️ Always explain — no exceptions
> Claude does nothing without explaining WHAT it does and WHY.

### 🚫 Never do
- Delete files
- Commit data to git
- Take any action without explanation
```

</details>

---

## What the prompt covers

| Section | What it captures |
|---|---|
| Project Identity | Name, purpose, users, phase |
| Tech Stack | Languages, frameworks, hosting, APIs |
| Folder Structure | Layout, protected files, sub-folder rules |
| Coding Conventions | Naming, formatting, docstrings |
| Claude's Role | What it can do, must confirm, must never do |
| Git & Workflow | Branching, commit format, what to never commit |
| Communication Style | Language, detail level, error handling |

---

## Design principles

- **No placeholders** — if you don't know it, the section is omitted
- **No guessing** — every line comes from what you explicitly said
- **No padding** — only what this exact project needs
- **Iterative** — start simple, grow the file as the project evolves

---

## Contributing

Found a missing section? A question that should be asked differently?
Open an issue or submit a pull request. All feedback welcome.

---

## License

MIT — use it, adapt it, share it.
