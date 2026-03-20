---
title: Teaching the LLM the Weeztix setup
type: 'content'
order: 7
---

- With microservices, the LLM needs to know where things live — which repo does what, how services talk to each other, how to run and test them
- This goes in AGENTS.md: tooling context, service names, docker setup, test commands
- It's always a work in progress — you add to it as gaps show up

I've started ours. Two things worth highlighting:

- **Database** — giving it schema awareness
- **Dockerized** — teaching it how our containers work
