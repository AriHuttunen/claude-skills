---
name: repo-why
description: Analyse a software project's purpose using Simon Sinek's Start With Why framework (Why/How/What). Use when the user asks to evaluate a repo's purpose, mission, "why it exists", what a codebase does, or wants to understand a project's reason for being. Works on a local directory, the current working directory, or a GitHub/GitLab/etc. repository URL.
---

# Repo Why

Analyse a local software repository to understand its reason for existing, its design approach, and what it actually does — using Simon Sinek's **Start With Why** framework applied to code.

## Philosophy

Most repositories jump straight into installation instructions without ever explaining *why* the software exists. A newcomer needs a mental model before they can evaluate whether a project is right for them — and that mental model comes from purpose, not features.

This skill applies Sinek's Why → How → What to software projects. The goal is to articulate what the project is about — not to grade or rate it.

## When to run

The user will point you at a local directory, the current working directory, or a repository URL. They might say:
- "What is the purpose of this repo?"
- "What does this project do?"
- "Analyse this repo's purpose"
- "What's the mission of this codebase?"
- "What does https://github.com/foo/bar do?"

**If given a URL:** Clone the repository to a temporary directory (e.g. `/tmp/repo-why-{name}`) first, then proceed with the same analysis steps. Clean up afterwards unless the user asks to keep it.

## Step 1: Gather sources

Scan the repository root and common documentation locations. Read files if they exist — do not fail if some are missing.

**Primary sources (read fully):**
- `README.md` (or `README`, `README.rst`, `readme.md`, etc.)
- `CONTRIBUTING.md`, `GOVERNANCE.md`
- `VISION.md`, `MISSION.md`, `PURPOSE.md` (rare)
- `CLAUDE.md`

**Secondary sources (scan for relevant content):**
- `docs/` or `documentation/` — index/overview pages, architecture docs, design docs
- `DESIGN.md`, `ARCHITECTURE.md`, `PHILOSOPHY.md`
- `package.json`, `Cargo.toml`, `pyproject.toml`, `go.mod`, `*.gemspec` — description and keywords fields
- `CHANGELOG.md` or `HISTORY.md` — early entries often reveal original motivation
- `ROADMAP.md` if present

**Practical approach:**
1. List the repo structure (limit depth to 3 levels)
2. Read primary sources in full
3. Skim secondary sources — focus on introductions, overviews, and any content that reveals purpose or philosophy
4. For tiny projects with no docs, glance at the main entry point
5. Check git log for early commits — they often reveal original intent

## Step 2: Analyse using Start With Why

Think through each dimension internally. Use these guiding questions during analysis but do not reproduce them in the output.

### The Why (Problem & Motivation)
- What problem does this software solve?
- What was broken, missing, or frustrating before it existed?
- Is the motivation genuine and specific, or vague and generic?
- If not explicitly stated, can you infer it from the design choices?

### The How (Approach & Design Philosophy)
- What design trade-offs does the project make?
- What does it optimise for and what does it deliberately sacrifice?
- Is there an architectural philosophy (convention over configuration, batteries-included vs minimal, adversarial vs cooperative, etc.)?
- How does it solve the problem differently from how others might?

### The What (Capabilities & Scope)
- What does the software concretely do?
- Is the scope well-defined — can you tell where this project ends?
- What are the key mechanisms or features, described in terms of the problem they solve?

## Step 3: Write the assessment

### Format

```
## {Project Name}

> {One-sentence summary of what this project is and does.}

### Why

{1-2 paragraphs. State the problem or motivation. Explain whether this is
explicitly stated or inferred, and from what evidence.}

### How

{1-2 paragraphs. State the approach and design philosophy. Reference specific
mechanisms, architectural choices, or documented principles.}

### What

{1-2 paragraphs. State what the software concretely does — its capabilities
and scope. Be specific about what it produces or enables.}
```

### Tone guidelines
- Be direct and substantive — state what the Why/How/What *are*, not how well the repo communicates them
- When something is inferred rather than stated, say so briefly and cite the evidence
- Keep each section to 1-2 focused paragraphs
- Do not produce ratings, scores, or grades
- Do not produce recommendations or suggestions — the user will ask follow-up questions if they want those
- Do not include sections beyond Why/How/What unless the user asks
- Quote or reference specific passages when they are particularly illustrative

### Calibration
- For small utility libraries, the Why and What may overlap — that's fine, keep it brief
- For frameworks and platforms, the How section deserves more depth since design philosophy matters most
- For forks, the Why should focus on why it diverged from upstream
- Match depth to project complexity — a 200-line CLI tool doesn't need the same treatment as a distributed database
