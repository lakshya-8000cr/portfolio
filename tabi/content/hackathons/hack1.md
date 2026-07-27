+++
title = "Google Hackathon 2024"
description = "Achieved **Top 30 Semi-Finalist out of 1500 teams** placement globally building a real-time voice & legal query system under tight 48-hour sprint constraints."
date = 2024-10-15

[extra]
local_image = "nyay.png"
link_to = "https://github.com/adityasharma0903/Nyay-GPT"

[taxonomies]
tags = ["AI", "LLM", "Telephony", "Node.js", "Hackathon"]
+++

Achieved **Top 30 Semi-Finalist out of 1500 teams** placement globally building a real-time voice & legal query system under tight 48-hour sprint constraints.

## Problem

Legal documents and jargon are extremely hard for everyday citizens to understand, and existing AI solutions require high-speed internet access that millions in rural areas lack.

## Solution

Built an AI voice assistant accessible over toll-free telephone networks using Exotel and OmniDimension, allowing users to ask legal queries in their native language via simple phone calls.

## Key engineering decisions & Chaos

- Designed low-latency LLM streaming over telephony channels so user voice feedback felt instant.
- Decoupled the voice processing engine from the core LLM pipeline for modular failover.
- **The Hackathon Vibe:** Survived on caffeine and 2 hours of sleep, debugging WebSocket audio streaming drops at 3 AM right before judge evaluations.

## Technology stack

- **Backend:** Node.js, Express, WebSockets
- **AI & Voice:** OmniDimension, Exotel Telephony API, LLM Streaming
- **Infrastructure:** Linux, Cloud-native pipelines

## Outcome & Learnings

 Reached the Top 30 globally out of thousands of teams. Taught me how to optimize for sub-second streaming latency and keep cool when core pipelines break under high-pressure demo deadlines.

#### [View Project Details](https://github.com/lakshya-8000cr) {.centered-text}