## Eduardo de Souza Marques

**I build the guardrails that let AI agents run unattended.**

Most agent tooling tries to control behavior with prompts. Prompts get
rationalized away. I enforce it in code: pre-execution gates that block the
call, multi-model review boards that have to sign off, watchdogs that kill idle
GPU pods, and budget ceilings that fail closed.

This came from operating real production systems — automated media pipelines
running nightly across three machines, unattended, on rented GPUs. Every
control I build exists because something failed first and cost me money.

---

### What I work on

| Area | What it means in practice |
|---|---|
| **Agent reliability** | Pre-execution gates that refuse a tool call until its preconditions are met — method studied, error registry read, compliance check passed. A refusal, not a reminder. |
| **Multi-model decision systems** | A weighted review board: eight models from eight vendors vote on high-impact calls, with self-calibrating weights and a recorded rationale per vote. |
| **Cost governance** | GPU spot-instance guards across four providers — idle killers, burn watchdogs, failover monitors, pre-flight gates. Built after an idle pod cost me $84 over thirteen days. |
| **Model routing** | Task-to-model routing that picks the strongest open model per vendor with a three-tier fallback chain, reserving frontier models for synthesis. |
| **Durable agent context** | State that survives conversation compaction, so a long-running system stops relitigating decisions it already made. |
| **Media generation infra** | ComfyUI workflow fidelity, image-to-video batch pipelines, deterministic assembly. |

---

### Currently

Preparing to publish this stack as independent open-source projects. Each repo
ships with tests, CI, a signed commit history, and a `PROVENANCE.md` stating
exactly what is mine and how it was built.

Built with heavy AI assistance, and honest about it — the architecture,
integration, and operational decisions are mine.

---

📍 Brazil · EN / PT-BR · open to remote roles and collaboration in AI
infrastructure, agent reliability, and LLMOps.
