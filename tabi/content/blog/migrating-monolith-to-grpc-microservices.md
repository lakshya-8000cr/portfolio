+++
title = "The Part Nobody Talks About in Open Source"
date = 2026-07-24
description = "Writing the code is the easy part — documentation, releases, and positioning are what make a project usable."

[taxonomies]
tags = ["Open Source", "GitHub", "Engineering", "Go"]
+++

When people look at an open-source project, they usually see one thing: the code. I used to think the same — as long as the code worked, the project was "done." I couldn't have been more wrong.

While building my recent CLI tools, I realized that writing the code is often the easiest part of open source. Everything around it is what actually makes a project usable.

---

## The First Mistake I Made

The first version of one of my projects had exactly what you'd expect: source code, a README, and that's it. I thought people would clone it, build it, and use it.

{% admonition(type="warning", title="The question that changed everything") %}
"Would I actually use someone else's project if it looked like this?" Probably not — not because the code was bad, but because I didn't know how it worked.
{% end %}

---

## Documentation Isn't Optional

Once I started treating documentation as part of the product, things changed. Instead of writing one long README, I started documenting different aspects separately:

```text,name=docs/
Architecture
Internals
Design Decisions
Installation
Benchmarks
Contributing
Security Policy
```

The interesting part wasn't writing the documentation — it was the fact that documenting the project exposed flaws I hadn't noticed while coding.

{% admonition(type="note", title="Documentation became a design review") %}
If I couldn't explain a design decision clearly, there was a good chance I hadn't thought it through enough.
{% end %}

---

## Shipping Is a Different Skill

Then came releases. I thought creating a GitHub repository was enough. It wasn't. I learned about:

- Semantic Versioning
- GitHub Releases
- Cross-platform binaries
- Checksums
- Release automation
- GoReleaser

{% admonition(type="tip", title="None of it touched functionality") %}
But it completely changed how easy it was for someone else to actually use the project.
{% end %}

---

## Open Source Isn't Just for You

One lesson kept repeating itself: every time I made something convenient for myself, I had to ask *"Would someone seeing this project for the first time understand it?"* That changed how I wrote everything.

| Before | After |
|---|---|
| Long, dense README | Shorter, scannable README |
| Minimal examples | Clearer examples |
| Ad-hoc commands | Predictable commands |
| Generic errors | Descriptive error messages |

Small details started mattering.

---

## Reviews Changed My Perspective

Submitting one of my projects to the Krew plugin index was an eye-opener. The feedback wasn't about syntax errors or missing semicolons — it was about:

- Naming
- Discoverability
- User expectations
- Existing alternatives
- Project positioning

{% admonition(type="info", title="Code vs. product") %}
Open source isn't just evaluated as code. It's evaluated as a **product**. People don't just ask *"Does it work?"* — they ask *"Why should this exist?"* Answering that is much harder than writing another feature.
{% end %}

---

## What I'll Do Differently

Every project I build now starts with a simple checklist:

- Is the purpose obvious?
- Can someone install it easily?
- Is the documentation complete?
- Can I explain why it exists in one sentence?
- Would I use this if someone else built it?

If the answer to any of those is "no," the project isn't finished yet.

---

### Final Thoughts

Writing code teaches you how to solve problems. Open source teaches you how to communicate those solutions. The more projects I build, the more I realize that good software isn't just about implementation — it's about making your ideas understandable, maintainable, and useful to people you've never met.

{% admonition(type="tip") %}
Code gets a project working. Everything around the code makes people trust it.
{% end %}