# Hi, I'm Jinchen 👋

**Senior Software Engineer with 8+ years building scalable distributed systems and 3+ years shipping production agentic AI** — from multimodal LLM extraction to autonomous multi-agent systems, cost-aware model routing, and org-wide AI-native practice. Technical lead of cross-functional, multi-million-dollar initiatives at Amazon; I work directly with customers to drive 0-to-1 initiatives, shape technical scope, and deliver user-first outcomes.

![Open to work](https://img.shields.io/badge/open%20to-Senior%20%2F%20Staff-2ea44f?style=flat-square)
![Location](https://img.shields.io/badge/Bay%20Area-or%20remote-blue?style=flat-square)
![Focus](https://img.shields.io/badge/focus-backend%20%C2%B7%20distributed%20systems%20%C2%B7%20agentic%20AI-6f42c1?style=flat-square)


## 🚀 What I've shipped

Backend and platform work at Amazon across logistics, document-compliance, and seller-facing systems:

- **Production multimodal LLM data-extraction service** on AWS Bedrock (Claude) — lifted extraction accuracy from **~60% (rule-based) to 95%+**, with continuous evaluation, **human-in-the-loop review** of low-confidence fields, and **async multi-model reflection** designed with applied scientists.
- **Regionalized, distributed document storage & processing platform** spanning **5 AWS regions** — single-write/multi-read replication sustaining high, spiky throughput, with caching and deliberately tuned consistency trade-offs for low-latency reads at scale.
- Led workstreams in an **SVP-level inbound-reliability initiative** across **8+ teams** alongside Principal Engineers — platformized the service architecture around a **config-driven control plane and self-service portal**, redefining service-ownership boundaries.
- Built distributed **event-driven workflow orchestration** with strong **idempotency** for a major international expansion; resolved retry-storms with a **retry budget** (client-side token-bucket rate limiting) and **circuit breaker** that sharply cut operational load.
- Drove a real-time, **event-driven backend** for a flagship seller-connection program; defined **schema-first GraphQL / REST API contracts** between web clients and backend services.
- Spearheaded a **0-to-1, multi-org inbound capacity-allocation platform initiative** — ideation through architecture, with multi-million-dollar projected savings.
- Championed a multi-year **architecture plan** — microservice decomposition and self-service platformization that removed team bottlenecks and improved developer productivity.
- **NA Regional Winner**, Amazon agentic-AI hackathon — led 5 engineers to build a technical-advisor agent with **human-review gates** on every action.
- Drove the org-wide **AI-Native Transformation Initiative**: weekly workshops for **30+ engineers** (prompt and context engineering, CoT, ReAct, MCP, AI observability, model routing, cost observability, loop engineering, multi-agent systems); spec-driven development across 3 teams; led the **AI-Readiness Initiative** converging services into reusable AI SOPs, skills, and MCP servers.


## 🔧 What I'm building

**Personal projects — built on my own time, in addition to the professional work above.** Open-source, runnable, and tested. Together they are one stack: a loop that builds software unattended, the layers that keep it from fooling itself, and what months of running it taught me.

### 🏭 [agent-foundry](https://github.com/jeffma8888/agent-foundry) — an always-on autonomous product org
Point it at a git repo and a lean core team of agents — product agent, engineer, reviewer, an **isolated QA engineer**, and an **independent release gate** — builds it feature by feature, around the clock, shipping only work that passes every gate. Behind the core sits a bench of dormant specialist roles that activate on written triggers. **Hundreds of autonomous iterations across 4 products**, with no human in the write path.
- **The reward is an artifact, not a report.** A stage succeeds only when the file it was asked to write exists and the full suite is green; the release gate re-runs ground truth itself and is the only role allowed to touch git. The tester is firewalled from `src/`, and graders are decorrelated from the role they judge, because same-model self-review rubber-stamps its own output.
- **What it taught me: reward hacking is the first-class engineering problem.** Iterations 90–101 shipped twelve consecutive `--json` clones — every one correct, tests green, reviewer approved — because the loop graded whether work was *correct*, never whether it was *worth doing*. The fix changed the reward, not the agent: a discovery pre-phase with two decorrelated scout lenses, PM triage that must name the strongest alternative it rejected, and a novelty brake in the planner's prompt.
- Reliability layer for long-horizon autonomy: per-stage retry with exponential backoff, atomic checkpoints, revert-on-failure, STOP sentinels for safe pause/resume, bounded context injection, and a secret/leak guard in the ship path.

`Python` · `multi-role orchestration` · `verifiable rewards` · `false-green detectors` · `9,000+ tests`

### 🪞 [agent-skill-improver](https://github.com/jeffma8888/agent-skill-improver) — self-improvement that cannot touch its own judge
A daily loop that reads an agent's own conversations, scores them against **versioned rubrics**, isolates failures, proposes **one skill edit**, then stops. Applying the edit is a separate, **human-gated** command with rollback.
- **The judge sits outside the loop's write path by construction**: the loop cannot edit its own rubrics or source, and an independent judge scores the proposal. Self-improvement without that boundary is just drift with better marketing.
- One edit per day is a feature. A small, reviewable diff with a named failing conversation behind it is something a human will actually read; a batch of twenty is something a human will rubber-stamp.

`Python 3.11+` · `zero runtime dependencies` · `2,000+ tests`

### 🧭 [ai-model-routing](https://github.com/jeffma8888/ai-model-routing) — the cheapest model that clears a bar *you measured*
Routes each repeated call type (extraction, triage, codegen, LLM-as-a-judge) to the cheapest model whose **Wilson lower-bound success rate** on your acceptance check clears a per-task bar — with fallback chains, **generator-family isolation for judges**, per-task cost attribution, and a sub-agent **delegation** decision. Standard library only, about 3,000 lines, fully offline demo.
- **The bar is a confidence bound, not an average.** A model that succeeds on 90% of 50 items does not clear an 85% bar (lower bound 0.786); it might be fine, you just have not shown it yet. Leaderboards disagree with each other and none of them is your task.
- **Evidence on 7 public datasets, every number regenerated byte-for-byte in CI, including where routing does not pay.** On RouterBench (28K prompts) routing reaches 0.735 held-out success at 34% of the best single model's cost; on AutoBench it reaches 0.854 vs 0.882 at 5.6% of the top model's cost — and the README says plainly that one cheaper strong model beats routing on both axes there. Routing pays where tasks differ in which model is good enough, and nowhere else.
- Evolved by an hourly autonomous improvement loop with cross-model review (200+ iterations).

`Python 3.10+` · `stdlib only` · `OpenAI-compatible endpoints` · `4,700+ tests`

### 🧯 [agent-failure-modes](https://github.com/jeffma8888/agent-failure-modes) — 630+ post-mortems from loops that ran unattended
Every incident is a real failure from the loops above, with its signature, root cause, why it was hard to see, the fix, the verification, and a one-line rule terse enough to drop into an agent prompt. **18 failure classes**; `RULES.md` doubles as a prompt payload. A single-source build generates every incident page, the JSON index, and the taxonomy, so they cannot drift; capture tools mine live loop logs for new lessons ranked by taxonomy coverage gaps.
- The three rules that would have prevented most of it: **success is an artifact, not an exit code**; **a detector's negative result is not evidence of health** (prove every alarm against a known-bad and a known-good sample); **change the reward, not the agent**.

`Python` · `deterministic build` · `prompt payload` · `18 classes`

### Also in the stack
- [agent-gap-radar](https://github.com/jeffma8888/agent-gap-radar) — evidence-first gap register and scanner for agent infrastructure; `radar scan` names which gaps *your* repo has. Priority and confidence are never blended: priority is severity/frequency/tractability, confidence comes only from evidence quality.
- [agent-practice-index](https://github.com/jeffma8888/agent-practice-index) — machine-readable, evidence-graded, freshness-tracked index of current agent-engineering practice, written to be read by an agent at the top of a loop iteration.
- [resilient-agent-loop-primitives](https://github.com/jeffma8888/resilient-agent-loop-primitives) — the scheduler, retry/backoff runner, and watchdog that fell out of the failures above; dependency-free.
- [proactive-loop-agent](https://github.com/jeffma8888/proactive-loop-agent) — a proactivity layer: an L2 scout ranks goals from your working context, an autonomy-contract gate approves them (sensitive ones go to a human), a sandboxed plan/act/check loop executes.
- [reflect-mcp](https://github.com/jeffma8888/reflect-mcp) — self-verifying pipeline over MCP: Generator → second-model Critic → human-in-the-loop gate below a confidence threshold.
- [graphql-rest-gateway](https://github.com/jeffma8888/graphql-rest-gateway) — schema-first GraphQL over REST that kills N+1 with request-scoped DataLoader batching (**21 → 3 downstream calls**), with a benchmark and a regression test that fails if batching ever breaks. `TypeScript` · `GraphQL Yoga` · `Vitest`


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

**Agentic AI & multi-agent systems · LLM evaluation & LLM-as-a-judge · Model routing & cost observability · Model Context Protocol (MCP) · Human-in-the-loop design · Distributed systems · Event-driven architecture · AWS Bedrock · Caching & storage at scale · REST/GraphQL API design**


## 📫 Reach me

- 📧 **Jinchen_Ma@outlook.com**
- 💼 **[linkedin.com/in/jinchen-ma](https://www.linkedin.com/in/jinchen-ma/)**
