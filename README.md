# Hi, I'm Jinchen 👋

**Software Engineer — 8+ years building large-scale distributed systems.**
Now focused on **agentic AI and production LLM platforms**, with a hard discipline for *verifying* AI output, not just generating it.

![Open to work](https://img.shields.io/badge/open%20to-Senior%20%2F%20Staff-2ea44f?style=flat-square)
![Location](https://img.shields.io/badge/Bay%20Area-or%20remote-blue?style=flat-square)
![Focus](https://img.shields.io/badge/focus-backend%20%C2%B7%20distributed%20systems%20%C2%B7%20agentic%20AI-6f42c1?style=flat-square)

---

## 🚀 What I've shipped

Backend and platform work at Amazon across logistics, document-compliance, and seller-facing systems:

- **Production LLM data-extraction service** on AWS Bedrock (Claude) — lifted extraction accuracy from **~60% (rule-based) to 95%+**, with continuous evaluation and **async multi-model reflection**; partnered with applied scientists on ongoing quality validation.
- **Regionalized, distributed document storage & processing system** spanning **5 AWS regions** — sustaining high, spiky throughput with caching and deliberately tuned consistency trade-offs for low-latency reads at scale.
- Led workstreams in a large **org-wide inbound-reliability initiative** across **8+ teams** alongside Principal Engineers — co-designing the system architecture and redefining service-ownership boundaries into a clean multi-model design.
- Built distributed **event-driven workflow orchestration** with strong **idempotency** for a major international expansion; resolved retry-storms with a service **token-pool** mechanism that sharply cut operational load.
- Drove a real-time, **event-driven backend** for a flagship seller-connection program; defined **schema-first GraphQL / REST API contracts** between web clients and backend services.
- Spearheaded a **0-to-1, multi-org inbound capacity-allocation platform initiative** — ideation through architecture, with multi-million-dollar projected savings.
- Championed a multi-year **architecture plan** — microservice decomposition and self-service platformization that removed team bottlenecks and improved developer productivity.
- **NA Regional Winner**, Amazon agentic-AI hackathon — led 5 engineers to build a technical-advisor agent with **human-review gates** on every action.
- Drove org-wide **agentic-AI adoption** as AI Campaign Owner: weekly workshops for **30+ engineers** (ReAct, MCP, multi-agent, context management, AI observability); established spec-driven AI-native development across 3 teams.

---

## 🔧 What I'm building

**Personal projects — built on my own time, in addition to the professional work above.** Open-source, runnable, and tested; they show how I think about backend systems and AI reliability:

### 🧭 [proactive-loop-agent](https://github.com/jeffma8888/proactive-loop-agent) — agents that find the work, not just do it
A **three-layer autonomous-agent architecture** that flips agentic AI from reactive to proactive. An **L2 scout** continuously scans your working context — active projects, recent activity, unfinished threads — and synthesizes a **ranked slate of targeted goals** you haven't asked for yet; an **autonomy-contract policy gate** auto-dispatches the safe ones and routes sensitive ones for human approval. Approved goals flow to an **L1 plan-act-check goal loop** driving **L0 executors** with exponential-backoff retry and atomic checkpoints — so work completes unattended, surviving model throttling and interruptions with zero lost progress. Fully offline demo (deterministic scripted-LLM double), also live-verified against AWS Bedrock.
`Python` · `Pydantic v2` · `LLM goal synthesis` · `policy-gated autonomy` · `pytest`

### 🤖 [reflect-mcp](https://github.com/jeffma8888/reflect-mcp) — self-verifying agents over MCP
A multi-agent pipeline that **checks its own work before surfacing it**: a *Generator* produces a structured result, a **second-model Critic** scores it field-by-field, and anything below a confidence threshold is routed to a **human-in-the-loop gate** instead of being returned as a silent guess. Deterministic tests around a stochastic core + a golden-file eval harness that measures accuracy, not vibes.
`Python` · `MCP / FastMCP` · `Pydantic` · `pytest`

### 🔗 [graphql-rest-gateway](https://github.com/jeffma8888/graphql-rest-gateway) — schema-first GraphQL that kills N+1
A production-shaped GraphQL gateway that wraps REST backends and eliminates the **N+1 query explosion** with request-scoped **DataLoader** batching. Ships with a benchmark that *proves* the fix — **21 → 3 downstream calls (7×)** for the same query — and a regression test that fails if batching ever breaks. Plus cursor pagination, query depth/complexity limiting, and clean resolver → service → data-source layering.
`TypeScript` · `GraphQL Yoga` · `DataLoader` · `Vitest`

---

## 🛠️ Tech I work with

![Python](https://img.shields.io/badge/Python-3776AB?style=flat&logo=python&logoColor=white)
![Java](https://img.shields.io/badge/Java-ED8B00?style=flat&logo=openjdk&logoColor=white)
![Kotlin](https://img.shields.io/badge/Kotlin-7F52FF?style=flat&logo=kotlin&logoColor=white)
![TypeScript](https://img.shields.io/badge/TypeScript-3178C6?style=flat&logo=typescript&logoColor=white)
![AWS](https://img.shields.io/badge/AWS-232F3E?style=flat&logo=amazonwebservices&logoColor=white)
![Spring](https://img.shields.io/badge/Spring-6DB33F?style=flat&logo=spring&logoColor=white)
![GraphQL](https://img.shields.io/badge/GraphQL-E10098?style=flat&logo=graphql&logoColor=white)
![Docker](https://img.shields.io/badge/Docker-2496ED?style=flat&logo=docker&logoColor=white)
![Linux](https://img.shields.io/badge/Linux-FCC624?style=flat&logo=linux&logoColor=black)

**Distributed systems · Microservices · Event-driven architecture · AWS Bedrock · Model Context Protocol (MCP) · Caching & storage at scale · REST/GraphQL API design**

---

## 📫 Reach me

- 📧 **Jinchen_Ma@outlook.com**
- 💼 **[linkedin.com/in/jinchen-ma](https://www.linkedin.com/in/jinchen-ma/)**
