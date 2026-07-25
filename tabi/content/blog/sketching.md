+++
title = "観察の美学 (Gankatsu no Bigaku)"
date = 2026-07-24
description = "How holding a pencil taught me patience, observation, and how to debug systems long before I wrote my first line of code."

[taxonomies]
tags = ["personal", "art", "engineering", "mindset"]

[extra]
mermaid = true
+++

*July 2026 • Personal • Art & Engineering*

People usually know me as someone who enjoys building software.

Most of my days revolve around terminals, benchmarking APIs, or figuring out why something that worked yesterday suddenly refuses to work today.

But long before I wrote my first line of code, I was holding a pencil.

Sketching was probably the first skill I genuinely wanted to get better at — not because someone asked me to, but because I enjoyed the process itself. Over the years, that habit quietly became part of how I think, even though I don't draw as often as I used to.

---

## Learning to Observe

When I first started sketching, I thought the hardest part was learning how to draw. It wasn't. **The hardest part was learning how to see.**

You begin noticing tiny details that most people walk past without thinking:
- How light changes across a face.
- Why shadows aren't actually black.
- Why two lines that look identical somehow feel completely different.

Realistic sketching isn't about having steady hands. It's about paying attention.

{% admonition(type="note", title="The Engineering Parallel") %}
Software engineering taught me the exact same lesson. **Good debugging isn't about typing faster.** It's about observing carefully before changing anything.
{% end %}

---

## There Are No Shortcuts

One thing sketching taught me very early was patience. You can't rush a portrait — trying to finish it quickly almost always makes it worse. The only way forward is one small improvement at a time.

That mindset has followed me into programming. Whether I'm building a backend service or debugging something I rarely expect the first solution to be the right one.

{% mermaid() %}
flowchart LR
    A[Make a Small Change] --> B[Observe]
    B --> C[Measure]
    C --> D[Improve]
    D --> A
{% end %}

It turns out that drawing and engineering have more in common than I ever expected.

---

## Perfection Is an Illusion

One thing I used to do was zoom into every tiny mistake:
1. A slightly uneven eye.
2. A shadow that looked a little darker than intended.
3. A line that wasn't perfectly straight.

I'd spend hours fixing details that nobody else would ever notice. Eventually, I realized something: **Perfection isn't what makes a drawing feel alive. Character does.**

Software feels surprisingly similar:

| Art / Sketching | Software Engineering |
|---|---|
| Endless tiny corrections | Endless micro-optimizations & refactoring |
| Striving for perfection kills progress | Chasing perfection delays shipping |
| Character gives life to art | Maintainability & real usage give life to code |

At some point, you stop chasing perfection and start chasing progress instead.

---

## Why I Still Keep a Pencil Nearby

These days I spend far more time writing Go than drawing portraits. Life changes, and interests evolve. But every now and then, I still sit down with a blank sheet of paper.

Not because I'm trying to create something extraordinary, but just because it reminds me to:
- **Slow down.**
- **Focus.**
- **Notice details.**

{% admonition(type="info", title="A Quick Reset") %}
Ironically, stepping away from the keyboard and picking up a pencil often helps me think more clearly when I come back.
{% end %}

---

## More Than Just a Hobby

I don't think drawing made me a better programmer. But I do think it made me:
* More patient.
* More observant.
* More comfortable with slow, incremental progress.

Those qualities matter whether you're shading a portrait or debugging a production issue at midnight.

```text,name=mindset-equation
Different Tools  +  Different Medium  =  The Same Mindset