---
theme: excali-slide
title: AI Augmented Coding with Claude Code
info: |
  ## AI Augmented Coding with Claude Code
  How AI is transforming the developer experience.
class: text-center
drawings:
  persist: false
transition: slide-left
mdc: true
---

# AI Augmented Coding with Claude Code

Transforming how developers build software

<div class="abs-br m-6 text-sm opacity-50">
  2025
</div>

---
transition: fade-out
---

# The Rise of Agentic Coding Tools

**2021** — *"Fancy autocomplete. I still had to drive."*
GitHub Copilot: inline suggestions, you accept or reject

**2023** — *"I was the Context Bridge."*
ChatGPT: copy-paste code, manually shuttle context back and forth

**2025** — *"The Agent drives. I navigate."*
Claude Code: reads files, runs commands, executes plans autonomously

<br>

**Why go headless (CLI)?** Treat the LLM as a collaborator, not a plugin.
Like messaging a senior engineer on Slack.

**Key shift:** Deep search + agentic loop — runs `grep`, `ls`, reads files, plans, executes.

<!--
no autocomplete
-->

---

# Coding Agent Benchmarks

<img src="/swe-bench-leaderboard.webp" class="h-96 mx-auto" />

---
layout: section
---

# Demo

Fresh Slidev repo + CLAUDE.md setup

<!--
explain the repo, what is slidev and how I’ll progressively improve the CC setup on it
- how to see my slide? wrong package manager expected
- make it launch as background process in bash
- fail because of stdin expected    
  - make it investigate on web
  - tail -f /dev/null | pnpm exec slidev —port 3030 &
  - The trick was using tail -f /dev/null | to keep stdin open so Slidev doesn't exit.
- time for a /init, it will take more time to investigate the current setup and do less guesses next time, saving time and tokens (it can focus on the actual task)
- Ok nice, now I want us to rewrite the slides for my real presentation, Je veux créer une présentation sur l'utilisation de l'IA pour le code avec Claude Code. Le titre serait "AI augmented coding with Claude Code", genere uniquement 3 slides pour l'instant
  - => fichier tab courant injecte dans le contexte automatiquement
  - mentionner combien CC est bon pour utiliser les commandes unix, grep par exemple et naviguer dans le systeme de fichier, aucun fichier n’est “indexe” avec CC, contrairement a Cursor par exemple
  - possibilite d’utiliser @ pour preciser des fichiers
  - feedback dans l’IDE directement avec le diff
- faire voir les slides generes
- experimentation: “on passe en mode ASCII, play the slides”
-->

---
transition: fade-out
---

# Planning Mode

- Claude Code has a native plan mode
- Claude explores codebase before coding
- Writes plan to file for approval
- Example: PPT notes extraction PR

<!--
"j'aimerais creer une deuxieme presentation"
-->

---
transition: fade-out
---

# Rewinding

- Checkpoints at each change
- `/rewind` to revert
- Safe experimentation, retry with more insights

---
layout: two-cols
transition: fade-out
---

# Context Window

- Quality degrades with context size
- Progressive disclosure: load only what's needed
- Claude automatically "compacts" to preserve context

::right::

<Tweet id="1993511782150029774" scale="0.55" />

<!--
200k ~ 2 tomes HP, 20k lignes de code, 300 dense A4 pages

show /context
-->

---
transition: fade-out
---

# Skills

Real-life examples:

- **MongoDB pipeline**: Complex aggregation built iteratively
- **Playwright e2e**: Flaky test diagnosed and fixed + Gherkin migration

<!--
show ODC Mongo skill odc/blob/main/.claude/skills/mongodb/SKILL.md

Mongo pipeline investigation odc/pull/24249
-->

---
transition: fade-out
---

# Feedback Loop >&nbsp;&nbsp;

## Background Shell

- `type:watch` in hooks config
- Tests run continuously
- Errors fed back to Claude automatically

<!--
- show sapionote2/blob/main/CLAUDE.md#important-notes
- Example of playwright skill odc/pull/24389/files#diff-4ac5d50bcf457cffeaef971a45c17e1342f42bbc1c2f7004a732cff63db6f1e3
-->

---
layout: two-cols
transition: fade-out
---

# Feedback Loop >&nbsp;&nbsp;   

## Hooks

- Pre/post tool execution
- Formatting on file save
- Linting before commit
- Custom validation logic

::right::

<img src="/claude-code-hooks.png" class="h-96 mx-auto" />

<!--
sapionote2/blob/main/.claude/settings.json
-->

---
layout: two-cols
transition: fade-out
---

# Feedback Loop >&nbsp;&nbsp;  

## MCPs (Model Context Protocol)

- **IDE getDiagnostics**: Type errors in real-time
- **Browser MCP**: Navigate and interact with web apps
- **GitHub MCP**: Pull PR comments directly
- **Support & Monitoring MCPs**: Notion, Sentry, ...

::right::

<img src="/get-diagnostics-ide-mcp.png" class="w-full mt-8 ml-8"/>

<!--
show /mcp, ask to run a getDiagnostics

demo of chrome MCP in sapionote2:
can you run the app and try to login into the dashboard to ensure it's working? Show 
me your progression with ASCII representation of pages
-->

---
transition: fade-out
---

# Commands

- Custom slash commands
- Stored in `.claude/commands/`
- Reusable prompts and workflows
- Team-shareable

<!--
show /describe-pr ODC command
example: odc/pull/24225
-->

---
transition: fade-out
---

# Security Model

- Explicit allowlist / blocklist for commands (incl bash), tools, MCPs
- Sandbox mode? devcontainers? remote dev machines?

<!--
https://code.claude.com/docs/en/security

show sapionote2 settings.local.json
-->

---
transition: fade-out
---

# Pricing & Rate limits

**Plans**
- **Pro** ($20/mo)
- **Max 5×** ($100/mo)
- **Max 20×** ($200/mo)
- **Team** ($30/user/mo): Min 5 users, Pro-level limits
- **Team Premium** ($150/user/mo)

**Rate limits**
- **5-hour rolling window**: resets after last message + 5h
- **Weekly cap**: ~150M tokens
- Opus 4.5 is **more efficient**: 48-76% fewer tokens than Sonnet for same tasks

<!--
- /usage to check current usage
- API: Opus $5/$25 per MTok, Sonnet $3/$15 per MTok
-->

---
transition: fade-out
---

# Interesting Resources

- https://claudelog.com/
- https://www.anthropic.com/engineering/claude-code-best-practices
- https://minusx.ai/blog/decoding-claude-code/

---
transition: fade-out
---

# Transformation of the SWE Role

- From writing code to orchestrating AI
- Architecture (before) and review (after) become critical
- Higher leverage, faster iteration
- New skills: prompting, verification, orchestration, technology watch, tooling, decision making, ...

<!--
- reviewing becomes a blocker
- build vs buy arguments changed
- not only devs are impacted
- /output-style Learning
-->
