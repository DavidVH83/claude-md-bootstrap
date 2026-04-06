# CLAUDE.md Bootstrap Prompt

> **How to use:** Paste this as your very first message in a new project session.
> Claude will ask you one opening question, then intelligently decide what else it
> needs to know. The output is a fully filled-in, ready-to-use `CLAUDE.md`.
>
> No installation required. Works with Claude.ai, Claude Code, or any Claude interface.

---

You are going to help me set up a complete `CLAUDE.md` for this new project.

**Your workflow has five steps — do not skip any. Do not rush ahead.**

---

## Step 0 — Check for personal defaults

Ask exactly this, nothing more:

> "Do you have a CLAUDE.md from a previous project you want to use as your
> starting point? If yes, paste it here. If no, just say 'no' and we'll start fresh."

**Then apply this rule:**

**If the user pastes a previous CLAUDE.md:**
→ Read it carefully and extract all existing defaults.
→ Treat every section in it as confirmed unless the user says otherwise.
→ Do NOT ask questions that are already answered by the pasted file.
→ In Step 1, only ask about what is project-specific and not yet covered:
   - Project name and purpose
   - Tech stack (if different from the previous project)
   - Folder structure (if different)
   - Any new protected files or folders
→ Show the user a short summary of what you extracted:
   ```
   I found these defaults in your previous CLAUDE.md:
   ✅ Git: main + feature branches, Conventional Commits
   ✅ Claude's role: write freely, confirm before changing existing files, never delete
   ✅ Communication: English, short summaries after actions
   ✅ Code style: snake_case, PEP8, Google docstrings

   I will only ask you about what is different for this new project.
   ```

**If the user says 'no' or has no previous CLAUDE.md:**
→ Continue to Step 1 as normal.

**Wait for my response before continuing.**

---

## Step 1 — Ask the opening question

Ask exactly this, nothing more:

> "Describe your project in 2–3 sentences. Include: what you are building,
> which language or technology you are using, and what phase you are in
> (idea, prototype, MVP, production)."

**Wait for my response before continuing.**

---

## Step 2 — Assess the answer and decide what to ask next

Read my answer carefully. Apply this rule:

**If my answer is specific and complete:**
(example: *"I'm building a Python FastAPI backend that connects to a PostgreSQL
database and exposes a REST API for a mobile app. It's an early prototype, solo
project, no users yet."*)
→ Extract everything you can directly from my answer.
→ Ask **only** for what is genuinely still missing.
→ Keep the follow-up list short.

**If my answer is vague, incomplete, or uses unclear terms:**
(example: *"I want to build something with AI"* or *"a website for my business"*)
→ Do **not** guess or assume anything.
→ Treat this as a signal that the user needs more guidance.
→ Ask **all** of the following questions, grouped by category.
→ Use simple language. Add a short example answer to every question.

### Full question list (use when answer is vague, or selectively when answer is partial):

```
**A — Project Identity**
A1  What is the name and one-sentence purpose of this project?
    (example: "ShopTrack — a tool that helps small shops manage their inventory")

A2  Who will use it?
    (example: "just me", "my team of 3", "paying customers", "open source community")

A3  What phase is the project in?
    (example: "blank slate — nothing built yet", "early prototype", "working MVP", "live in production")

**B — Tech Stack**
B1  What programming language(s) are you using?
    (example: "Python", "TypeScript", "both Python backend and React frontend")
    If you don't know yet, say: "not decided yet"

B2  Any frameworks, libraries, or tools you already know you will use?
    (example: "FastAPI, SQLAlchemy, pytest" or "not sure yet")

B3  Where will this run or be hosted?
    (example: "local machine only", "Railway", "AWS", "not decided yet")

B4  Any external services or APIs?
    (example: "Stripe for payments, SendGrid for email" or "none" or "not sure yet")

**C — Folder & File Structure**
C1  Do you already have a folder structure, or should Claude suggest one?
    (example: "I have one, I'll describe it" or "suggest one for me")

C2  Are there any files or folders Claude must never touch?
    (example: ".env files, /migrations, /prod folder" or "nothing specific yet")

C3  Do you want to use sub-folder CLAUDE.md files?
    These are local rule files inside specific folders that override the global CLAUDE.md
    only for that folder. Useful when different parts of your project need different rules.
    (example: "yes, I want one in /src and one in /tests" or "no, one global file is enough"
    or "not sure yet, suggest when relevant")

C4  If yes to C3 — are there specific rules you already know belong to a sub-folder?
    (example: "in /tests: always use pytest, never mock the database"
    or "in /src/auth: never modify auth.py without asking")
    If you are not sure yet, say: "we'll add them as the project grows"

**D — Claude's Role**
D1  What can Claude do without asking you first?
    (example: "write new functions, add comments, fix formatting, write tests")

D2  What must Claude always ask before doing?
    (example: "changing existing files, adding dependencies, restructuring folders")

D3  What must Claude never do, no matter what?
    (example: "never delete files, never push to git, never run migrations")

**E — Code Style**
E1  Any naming or formatting rules?
    (example: "snake_case, PEP8, Google docstrings" or "just be consistent")
    If you don't know, say: "use the standard for the language"

E2  How should tests be written?
    (example: "pytest, one test per function" or "no tests yet")

**F — Git & Workflow**
F1  Do you use git? If yes, what is your branching strategy?
    (example: "yes, main + feature branches" or "yes, main only" or "no git yet")

F2  Any commit message format?
    (example: "Conventional Commits: feat:, fix:, chore:" or "no preference")

**G — Communication**
G1  What language for code comments and explanations?
    (example: "English for everything" or "Dutch explanations, English code")

G2  How much explanation do you want from Claude?
    (example: "just do it, short summary after" or "always explain your reasoning")

G3  How should Claude handle errors or blockers?
    (example: "show the problem and fix immediately" or "list options and ask me to choose")
```

**Important rules for this step:**
- If the user answers "I don't know" or "not sure yet" → accept it and leave that section out of the CLAUDE.md entirely. Do not guess.
- Never proceed to Step 3 if critical information (language, purpose, Claude's role) is still missing.
- If something is still unclear after the first follow-up, ask again. Clarity before speed.

**Wait for my response before continuing.**

---

## Step 3 — Confirm what you have

Before generating, list every piece of information you have collected:

```
Here is what I have so far:

✅ Project: ShopTrack — inventory tool for small shops
✅ Language: Python 3.11
✅ Framework: FastAPI + SQLAlchemy
✅ Phase: early prototype
✅ Claude may freely: write functions, add tests, fix formatting
✅ Claude must confirm: adding dependencies, changing existing files
✅ Claude must never: delete files, touch .env
✅ Git: main + feature branches, Conventional Commits
✅ Communication: English, short summaries after actions
✅ Sub-folder CLAUDE.md: yes — /src and /tests
✅ Sub-folder rules known: /tests → always pytest, never mock the database
❌ Hosting: not decided yet → section omitted
❌ Tests style: not decided yet → section omitted
```

Then ask:
> "✅ Does this look right? Correct anything wrong, or type **'generate'** to continue."

**Wait for my response before continuing.**

---

## Step 4 — Generate the CLAUDE.md

Generate the complete `CLAUDE.md` inside a fenced code block (` ```markdown `),
ready to copy into the project root.

### Hard rules for generation — no exceptions:

- **No placeholders.** Never write "fill in later", "TBD", or leave a field blank.
  If you don't have the information → omit the entire section.
- **No guessing.** Every line must come from what the user explicitly told you.
- **No padding.** No filler text, encouragement, or generic advice.
- **Be specific.** Every line should reflect this exact project, not any project.
- **Keep it scannable.** Short sentences. Tables where helpful. Clear headers.

Always add this header at the very top:
```
<!-- Generated: [today's date] | Version: 1.0 | Review by: [today's date + 30 days] -->
<!-- Update this file as the project evolves. Delete sections that no longer apply. -->
```

---

## Sections to include (only if you have real content for them)

### 1. Project Identity
Name, one-sentence purpose, target users, current phase.

### 2. Tech Stack
Languages, frameworks, databases, hosting, dev tools.
Use a table if there are more than 3 items.

### 3. Folder Structure
Overview of the directory layout.
Which folders Claude may freely edit.
Which folders Claude must never touch.
Entry points.

If sub-folder CLAUDE.md files are used:
- List each sub-folder and its purpose.
- Document any rules already known for that sub-folder.
- Include this sub-folder template as an appendix at the bottom of the CLAUDE.md:

```markdown
## Sub-folder CLAUDE.md Template

When adding a sub-folder CLAUDE.md, use this structure:

# CLAUDE.md — /folder-name

Inherits all rules from root CLAUDE.md unless overridden below.

## Local overrides
- ...

## Protected files
- Never modify: `filename.py` — reason: ...

## Local conventions
- ...
```

### 4. Coding Conventions
Naming conventions, formatting rules, import order, docstring style.
Include a short code snippet if a pattern is non-obvious.

### 5. Claude's Role
Three clearly separated lists:
- ✅ **Do freely** — actions Claude can take without asking
- ⚠️ **Always confirm** — actions that require explicit approval
- 🚫 **Never do** — hard limits, no exceptions

### 6. Git & Workflow
Branch naming, commit message format, what to never commit.

### 7. Architecture Decisions
Decisions already made and why.
Things intentionally excluded and why.
Known technical debt or temporary workarounds.

### 8. Communication Style
Language for code vs. explanations.
Preferred level of detail.
How to report errors and blockers.

### 9. Environment Variables
Variable names only — never values.
Which are prod-only.

---

**Start with Step 0 now.**
