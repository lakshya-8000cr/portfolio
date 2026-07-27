+++
title = "fahride"
description = "FahRide is a student-focused carpooling platform that connects riders and drivers within the campus community, serving 200+ students with a simple, reliable, and cost-effective way to commute."
date = 2026-07-23

[extra]
local_image = "fah.png"
link_to = "https://fahride.app/"

[taxonomies]
tags = ["backend", "microservices", "gRPC", "PostgreSQL", "Docker", "Kubernetes"]
+++

Forge is a production-style application that was incrementally migrated from a monolithic architecture to microservices.

## Problem

The original monolith moved quickly early on, but scaling specific capabilities independently became difficult. Service boundaries were unclear, and changes in one area could increase deployment risk in another.

## Solution

I migrated backend communication to gRPC-based services and moved deployment workflows toward containerized, orchestrated infrastructure with Docker and Kubernetes.

## Key engineering decisions

- Defined service boundaries around operational responsibilities instead of only code modules.
- Standardized service-to-service contracts using gRPC and protobuf.
- Tuned PostgreSQL connection pooling per service to reduce contention under load.
- Added observability-oriented checks for latency and reliability during rollout.
- Validated sustained database-backed gRPC throughput of over 4,000 requests/second on a single service instance using ghz.
- Benchmarked approximately 1,000 concurrent HTTPS requests in controlled runs to evaluate edge and API behavior under pressure.

## Technology stack

- Go and Java (service components)
- gRPC and Protocol Buffers
- PostgreSQL
- Docker
- Kubernetes
- Linux-based deployment environment

## Outcome

Forge became easier to evolve safely: services can be tested and deployed with clearer isolation, performance characteristics are measurable, and infrastructure decisions are driven by repeatable load-testing results.

#### [View on GitHub](https://github.com/lakshya-8000cr/Forge) {.centered-text}
