+++
title = "Why \"10,000 Requests per Second\" Doesn't Mean Your Backend is Fast"
date = 2026-07-24
description = "Why throughput alone is misleading, and how latency, error rate, and bottlenecks tell a better performance story."

[taxonomies]
tags = ["performance", "PostgreSQL", "gRPC", "backend"]

[extra]
mermaid = true
+++

*July 2026 • Performance Engineering • Backend • gRPC*

A few weeks ago, I started benchmarking the backend of one of my projects. Like most people, I initially had a simple goal in mind:

> How many requests per second can my server handle?

At first glance, it seems like a reasonable metric — higher RPS must mean a faster backend, right? Not really. After spending hours benchmarking HTTP endpoints, migrating services to gRPC, profiling the application, and tuning PostgreSQL connection pools, I realized that a single RPS number says almost nothing about the actual performance of a system. This post is about that realization.

---

## The 10K RPS Illusion

{% admonition(type="note", title="First target: a health check") %}
No database queries. No business logic. Just a small response confirming the service was alive.
{% end %}

The benchmark looked fantastic — thousands of requests per second with extremely low latency. If I wanted to, I could proudly write:

> **"My backend handles 10,000 requests per second."**

{% admonition(type="warning", title="Technically true, still misleading") %}
Nobody builds production systems around health endpoints. Real applications spend most of their time talking to databases, validating data, making network calls, or coordinating multiple services. **That's where performance actually matters.**
{% end %}

---

## Real Endpoints Tell a Different Story

The next benchmark targeted an endpoint that fetched project information from PostgreSQL. Same machine, same service, same benchmarking tool — completely different results.

```text,name=benchmark-output
health-check    →  12,483 req/s   |  avg 3ms    |  0.0% errors
projects-fetch  →   1,942 req/s   |  avg 187ms  |  2.1% errors
```

Nothing was wrong with Go. Nothing was wrong with gRPC. The bottleneck had simply moved to another layer of the stack.

That was the first time I stopped asking *"How many requests can my server handle?"* and started asking *"What exactly is my server doing for every request?"* Those are very different questions.

---

## Throughput Isn't the Whole Story

When people compare backend performance, they often focus on one number: `requests/sec`. But production systems are usually evaluated on several metrics together — average latency, p95/p99 latency, error rate, resource utilization, and throughput.

Imagine two services:

| Metric | Service A | Service B |
|---|---|---|
| Throughput | 10,000 RPS | 4,000 RPS |
| Latency | 150 ms | 4 ms |
| Failure rate | 8% | 0% |

{% admonition(type="tip", title="Which one would you deploy?") %}
The answer becomes obvious once reliability enters the conversation.
{% end %}

---

## Every Layer Has Its Own Limit

Every optimization simply exposes the next bottleneck:

{% mermaid() %}
flowchart LR
    A[HTTP overhead] -->|migrated to gRPC| B[gRPC]
    B -->|throughput improved| C[PostgreSQL pool]
    C -->|tuned connection pooling| D[Database itself]
    D -->|new limiting factor| E[Next bottleneck...]
{% end %}

Performance engineering isn't about finding a magic optimization. It's about continuously discovering what limits the system next.

---

## Benchmarks Need Context

{% admonition(type="info", title="Questions I ask now") %}
- Was the endpoint hitting a database?
- Was it reading from cache?
- Was it CPU-bound or I/O-bound?
- How many concurrent clients were used?
- What was the latency distribution?
- Were there any failed requests?
{% end %}

Without that context, an RPS number is just a number. It doesn't tell the whole story.

---

## What I Learned

This small benchmarking exercise changed how I think about backend performance. Today, I care much less about chasing impressive RPS numbers, and much more about understanding **why** a system performs the way it does.

Good benchmarks don't just tell you something is fast — they explain **what becomes slow next.** That's usually where the real engineering begins.

---

### Final Thoughts

{% admonition(type="tip", title="TL;DR") %}
`Profile it → Measure latency → Check error rates → Look at resource usage → Find the bottleneck → Fix it → Benchmark again`

Performance isn't a destination — it's an iterative process of understanding your system a little better every time.
{% end %}