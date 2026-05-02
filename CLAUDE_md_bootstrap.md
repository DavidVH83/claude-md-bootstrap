# CLAUDE.md Bootstrap Prompt

> **How to use:** Paste this as your very first message in a new project session.
> Claude will ask you one opening question, then intelligently decide what else it
> needs to know. The output is a fully filled-in, ready-to-use `CLAUDE.md`.
>
> No installation required. Works with Claude.ai, Claude Code, or any Claude interface.

---

You are going to help me set up a complete `CLAUDE.md` for this new project.

**Your workflow has five steps â€” do not skip any. Do not rush ahead.**

---

## Step 0 â€” Check for personal defaults

Ask exactly this, nothing more:

> "Do you have a CLAUDE.md from a previous project you want to use as your
> starting point? If yes, paste it here. If no, just say 'no' and we'll start fresh."

**Then apply this rule:**

**If the user pastes a previous CLAUDE.md:**
â†’ Read it carefully and extract all existing defaults.
â†’ Treat every section in it as confirmed unless the user says otherwise.
â†’ Do NOT ask questions that are already answered by the pasted file.
â†’ In Step 1, only ask about what is project-specific and not yet covered:
   - Project name and purpose
   - Tech stack (if different from the previous project)
   - Folder structure (if different)
   - Any new protected files or folders
â†’ Show the user a short summary of what you extracted:
   ```
   I found these defaults in your previous CLAUDE.md:
   âœ… Git: main + feature branches, Conventional Commits
   âœ… Claude's role: write freely, confirm before changing existing files, never delete
   âœ… Communication: English, short summaries after actions
   âœ… Code style: snake_case, PEP8, Google docstrings

   I will only ask you about what is different for this new project.
   ```

**If the user says 'no' or has no previous CLAUDE.md:**
â†’ Continue to Step 1 as normal.

**Wait for my response before continuing.**

---

## Step 1 â€” Ask the opening question

Ask exactly this, nothing more:

> "Describe your project in 2â€“3 sentences. Include: what you are building,
> which language or technology you are using, and what phase you are in
> (idea, prototype, MVP, production)."

**Wait for my response before continuing.**

---

## Step 2 â€” Assess the answer and decide what to ask next

Read my answer carefully. Apply this rule:

**If my answer is specific and complete:**
(example: *"I'm building a Python FastAPI backend that connects to a PostgreSQL
database and exposes a REST API for a mobile app. It's an early prototype, solo
project, no users yet."*)
â†’ Extract everything you can directly from my answer.
â†’ Ask **only** for what is genuinely still missing.
â†’ Keep the follow-up list short.

**If my answer is vague, incomplete, or uses unclear terms:**
(example: *"I want to build something with AI"* or *"a website for my business"*)
â†’ Do **not** guess or assume anything.
â†’ Treat this as a signal that the user needs more guidance.
â†’ Ask **all** of the following questions, grouped by category.
â†’ Use simple language. Add a short example answer to every question.

### Full question list (use when answer is vague, or selectively when answer is partial):

```
**A â€” Project Identity**
A1  What is the name and one-sentence purpose of this project?
    (example: "ShopTrack â€” a tool that helps small shops manage their inventory")

A2  Who will use it?
    (example: "just me", "my team of 3", "paying customers", "open source community")

A3  What phase is the project in?
    (example: "blank slate â€” nothing built yet", "early prototype", "working MVP", "live in production")

**B â€” Tech Stack**
B1  What programming language(s) are you using?
    (example: "Python", "TypeScript", "both Python backend and React frontend")
    If you don't know yet, say: "not decided yet"

B2  Any frameworks, libraries, or tools you already know you will use?
    (example: "FastAPI, SQLAlchemy, pytest" or "not sure yet")

B3  Where will this run or be hosted?
    (example: "local machine only", "Railway", "AWS", "not decided yet")

B4  Any external services or APIs?
    (example: "Stripe for payments, SendGrid for email" or "none" or "not sure yet")

**C â€” Folder & File Structure**
C1  Do you already have a folder structure, or should Claude suggest one?
    (example: "I have one, I'll describe it" or "suggest one for me")

C2  Are there any files or folders Claude must never touch?
    (example: ".env files, /migrations, /prod folder" or "nothing specific yet")

C3  Do you want to use sub-folder CLAUDE.md files?
    These are local rule files inside specific folders that override the global CLAUDE.md
    only for that folder. Useful when different parts of your project need different rules.
    (example: "yes, I want one in /src and one in /tests" or "no, one global file is enough"
    or "not sure yet, suggest when relevant")

C4  If yes to C3 â€” are there specific rules you already know belong to a sub-folder?
    (example: "in /tests: always use pytest, never mock the database"
    or "in /src/auth: never modify auth.py without asking")
    If you are not sure yet, say: "we'll add them as the project grows"

**D â€” Claude's Role**
D1  What can Claude do without asking you first?
    (example: "write new functions, add comments, fix formatting, write tests")

D2  What must Claude always ask before doing?
    (example: "changing existing files, adding dependencies, restructuring folders")

D3  What must Claude never do, no matter what?
    (example: "never delete files, never push to git, never run migrations")

**E â€” Code Style**
E1  Any naming or formatting rules?
    (example: "snake_case, PEP8, Google docstrings" or "just be consistent")
    If you don't know, say: "use the standard for the language"

E2  How should tests be written?
    (example: "pytest, one test per function" or "no tests yet")

**F â€” Git & Workflow**
F1  Do you use git? If yes, what is your branching strategy?
    (example: "yes, main + feature branches" or "yes, main only" or "no git yet")

F2  Any commit message format?
    (example: "Conventional Commits: feat:, fix:, chore:" or "no preference")

**G â€” Communication**
G1  What language for code comments and explanations?
    (example: "English for everything" or "Dutch explanations, English code")

G2  How much explanation do you want from Claude?
    (example: "just do it, short summary after" or "always explain your reasoning")

G3  How should Claude handle errors or blockers?
    (example: "show the problem and fix immediately" or "list options and ask me to choose")
```

**Important rules for this step:**
- If the user answers "I don't know" or "not sure yet" â†’ accept it and leave that section out of the CLAUDE.md entirely. Do not guess.
- Never proceed to Step 3 if critical information (language, purpose, Claude's role) is still missing.
- If something is still unclear after the first follow-up, ask again. Clarity before speed.

**Wait for my response before continuing.**

---

## Step 3 â€” Confirm what you have

Before generating, list every piece of information you have collected:

```
Here is what I have so far:

âœ… Project: ShopTrack â€” inventory tool for small shops
âœ… Language: Python 3.11
âœ… Framework: FastAPI + SQLAlchemy
âœ… Phase: early prototype
âœ… Claude may freely: write functions, add tests, fix formatting
âœ… Claude must confirm: adding dependencies, changing existing files
âœ… Claude must never: delete files, touch .env
âœ… Git: main + feature branches, Conventional Commits
âœ… Communication: English, short summaries after actions
âœ… Sub-folder CLAUDE.md: yes â€” /src and /tests
âœ… Sub-folder rules known: /tests â†’ always pytest, never mock the database
âŒ Hosting: not decided yet â†’ section omitted
âŒ Tests style: not decided yet â†’ section omitted
```

Then ask:
> "âœ… Does this look right? Correct anything wrong, or type **'generate'** to continue."

**Wait for my response before continuing.**

---

## Step 4 â€” Generate the CLAUDE.md

Generate the complete `CLAUDE.md` inside a fenced code block (` ```markdown `),
ready to copy into the project root.

### Hard rules for generation â€” no exceptions:

- **No placeholders.** Never write "fill in later", "TBD", or leave a field blank.
  If you don't have the information â†’ omit the entire section.
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

# CLAUDE.md â€” /folder-name

Inherits all rules from root CLAUDE.md unless overridden below.

## Local overrides
- ...

## Protected files
- Never modify: `filename.py` â€” reason: ...

## Local conventions
- ...
```

### 4. Coding Conventions
Naming conventions, formatting rules, import order, docstring style.
Include a short code snippet if a pattern is non-obvious.

### 5. Claude's Role
Three clearly separated lists:
- âœ… **Do freely** â€” actions Claude can take without asking
- âš ï¸ **Always confirm** â€” actions that require explicit approval
- ðŸš« **Never do** â€” hard limits, no exceptions

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
Variable names only â€” never values.
Which are prod-only.

---

## Universal Sections â€” Always Include Verbatim

**These sections are the same in every project. Copy them exactly as written below.
Do not modify, summarize, or adapt them. They are maintained centrally.**

### 10. Knowledge Bank

```markdown
## Knowledge Bank

Vault: `C:\Users\David\ObsidianVault\KnowledgeBase\`
Skill: `obsidian-knowledge-bank`

**Sessiestart â€” altijd doen:**
1. Vault raadplegen â€” zoek naar relevante notes over het onderwerp
2. Kort melden wat je gevonden hebt (of dat er niets relevant was)
3. Dan pas beginnen met de eigenlijke taak

**Sessie-afsluiting â€” altijd doen:**
Sla learnings proactief op. Bepaal zelf waar de kennis thuishoort:

| Type kennis | Vault locatie |
|---|---|
| Opgelost probleem, bug, fout | `04-Insights/[beschrijving].md` |
| Tool, MCP, installatie | `03-Tools/[juiste submap]/` |
| Conceptuele kennis, theorie | `01-Learning/Artikels/[thema].md` |
| Nieuw project ontdekt | `02-Projects/[naam]/README.md` |
| Beslissing genomen | `02-Projects/[naam]/decisions.md` |

Gebruik altijd het sessie-learning formaat:
```
## [Datum] â€” [Korte sessietitel]
### Wat gedaan
### Wat geleerd
### Beslissingen genomen
### Volgende stap
```
Zie `vault-context.md` voor projectspecifieke vault links.
```

### 11. AI Session Quality

```markdown
## AI Sessiekwaliteit

### Nooit het eerste antwoord aanvaarden
Het eerste antwoord is het startpunt, niet het eindpunt.
Na elk substantieel antwoord: vraag minstens Ã©Ã©n alternatief, kritiek of edge case.

### SPARKS â€” Actief toepassen
| Techniek | Gebruik wanneer |
|---|---|
| **Pivot Roles** | Laat mij de vragen stellen: *"Ask me questions to clarify my thinking â€” one at a time"* |
| **Ask for More** | Na elk antwoord: 3 varianten of een alternatief perspectief |
| **Reframe (HMW)** | Bij vastlopen: *"Herformuleer als 3 verschillende How Might We vragen"* |
| **Strategic Pause** | Build â†’ Critique â†’ Rebuild. Evalueer voor je finaliseert. |

### Cognitive Bias Checks
Benoem actief bij elke bewering:
- **[Feit]** â€” verifieerbaar
- **[Inference]** â€” logische afleiding
- **[Speculatie]** â€” onzeker

### Workflow Classification
Bij nieuwe taken: classificeer eerst de AI-exposure (E0â€“E11) voor je begint.
Skill: `workflow-classification`

### Handige prompts
Strategic Pause: *"Evalueer wat we tot nu toe gedaan hebben. Wat klopt? Wat mist? Wat zouden we anders aanpakken?"*
HMW Reframe: *"Herformuleer dit probleem als 3 verschillende 'How Might We...?' vragen."*
```

### 12. Gedragsregels

```markdown
## Gedragsregels

- Geen fake zekerheid â€” onderscheid [Feit] / [Inference] / [Speculatie]
- Bij vage of hoog-stakes vragen: eerst verduidelijken, dan uitvoeren
- Push terug als een aanname zwak is â€” wees een Devil's Advocate
- Stap-voor-stap met checkpoints, niet alles in Ã©Ã©n keer
- Nooit placeholders in output â€” volledig invullen of expliciet vragen wat ontbreekt
- Gebruik AI op zwaktes, niet op sterktes â€” behoud persoonlijke differentiatie
```

---


### 13. Boekbibliotheek

`markdown
## Boekbibliotheek

23 AI/LLM e-books beschikbaar op:
`C:\Users\David\Documents\Claude toegang\Books\`
Skill: `book-library`

Raadpleeg automatisch de relevante boeken wanneer je iets bouwt gerelateerd aan
LLMs, MCP, RAG, agents, fine-tuning of LLMOps — doe dit VOOR de implementatie.
Dekking: MCP (Python + TypeScript), RAG, Agentic AI, LLM Engineering,
LangChain, LlamaIndex, LLMOps, NLP, PyTorch.
`
**Start with Step 0 now.**

