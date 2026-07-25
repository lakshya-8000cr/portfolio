+++
title = "Why I Never Refactor My Real Project Anymore"
date = 2026-07-23
description = "Using isolated workspaces for safer large-scale refactoring."

[taxonomies]
tags = ["Go", "CLI", "Software Engineering", "Architecture", "Developer Tools"]

[extra]
mermaid = true
+++

There was a time when I used to make every architectural change directly inside my main project. It felt natural — open the project, create a new branch, start moving files, rename packages, split modules, fix imports, repeat.

Until one day I started migrating one of my projects, **Forge**, from a monolithic architecture to microservices. That's when I realized how dangerous this workflow actually was.

---

## The Problem

Breaking a project into multiple services isn't just moving folders around. You end up changing almost everything:

{% admonition(type="warning", title="Everything is on the table") %}
- Directory structure
- Go packages
- Imports
- Docker files
- Environment variables
- Configuration
- Service boundaries
{% end %}

One wrong decision halfway through, and suddenly nothing builds anymore. Yes, Git exists — but Git only helps *after* you've already modified your repository. What I really wanted was a place where I could experiment without touching the original project at all.

---

## That's Why I Built Veil

Instead of modifying the actual project, Veil creates an isolated workspace — a disposable copy of your project.

```bash,name=terminal
veil create forge-workspace
```

Inside that workspace I could do anything:

- Delete files
- Move packages
- Split services
- Rewrite configurations
- Experiment with architecture

{% admonition(type="note", title="If everything failed") %}
I simply deleted the workspace. The original project never changed.
{% end %}

---

## The Workflow

Instead of the usual gamble:

```text
Project → Modify → Hope it works
```

I started doing this:

{% mermaid() %}
flowchart TD
    A[Project] --> B[Create Workspace]
    B --> C[Experiment Freely]
    C --> D[Run & Test]
    D --> E{Everything Works?}
    E -->|No| F[Delete Workspace]
    E -->|Yes| G[Apply Changes]
{% end %}

That small difference completely changed how I approached large refactors.

---

## The Best Part

Once the migration worked, I simply ran:

```bash,name=terminal
veil apply
```

{% admonition(type="tip", title="One command, full sync") %}
Veil synchronized the workspace back to my original project — every file, every rename, every modification, every deletion — without me manually copying anything.
{% end %}

---

## Why Git Wasn't Enough

People often ask: *why not just use Git?*

| | Git | Veil |
|---|---|---|
| Solves | Version control | Experimentation |
| Assumes | You're already working inside the repo | You don't want to touch the repo yet |
| Rollback | After the fact, via history | Never happened in the first place |

They're solving different problems.

---

## Where I Use It Today

I don't only use Veil for architecture migrations anymore. Now I use it for:

- Large refactors
- AI-generated code experiments
- Dependency upgrades
- Legacy code cleanup
- Prototype implementations
- Risky feature development

Basically, anything where I don't want to gamble with the original codebase.

---

### Final Thoughts

Building Veil wasn't about creating another CLI. It came from a real engineering problem I kept facing.

{% admonition(type="tip", title="The real payoff") %}
Sometimes the best developer tools aren't the ones that save milliseconds. They're the ones that give you the confidence to try something you would've otherwise avoided.
{% end %}