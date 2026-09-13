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

### Published work

Fourteen libraries extracted from that stack, plus the studio site. Every one
ships tests, CI across Linux/macOS/Windows, and a `PROVENANCE.md` stating what
was extracted, what was deliberately left behind, and how it was built.

**3,580 tests. Zero runtime dependencies in the core of every library.**

#### Agent reliability

| Repo | What it does | Tests |
|---|---|---:|
| [agent-gates](https://github.com/edusouzaxGV/agent-gates) | Preconditions enforced in code that refuses the tool call, not reminded in a prompt. Fail-closed by default. | 184 |
| [error-registry](https://github.com/edusouzaxGV/error-registry) | Institutional memory of mistakes, plus the gate that makes it binding. Append-only, similarity lookup, acknowledgement receipts. | 381 |
| [deputy](https://github.com/edusouzaxGV/deputy) | Bounded delegation: reserved zones no consensus can unlock, a quorum where a silent predictor is a broken dependency and never a cautious vote, and a journal that makes a dead mechanism visible. | 130 |
| [durable-context](https://github.com/edusouzaxGV/durable-context) | State that survives conversation compaction, distilled by a pre-compaction trigger so nothing depends on the agent remembering. | 118 |

#### Multi-model decision systems

| Repo | What it does | Tests |
|---|---|---:|
| [polycourt](https://github.com/edusouzaxGV/polycourt) | A weighted jury: models from different vendors vote on one question, weights self-calibrate from recorded outcomes, every vote keeps its rationale. | 159 |
| [devil-advocate](https://github.com/edusouzaxGV/devil-advocate) | Adversarial review by models told to attack, not approve — with an adjudication pass that defaults to refuted, because half of unchecked findings are fabricated. | 299 |

#### Cost governance

| Repo | What it does | Tests |
|---|---|---:|
| [spend-guard](https://github.com/edusouzaxGV/spend-guard) | Budget ceilings that fail closed. An unknown price blocks instead of passing as free; a crash between reserve and commit does not leak the reservation. | 365 |
| [gpu-spot-guard](https://github.com/edusouzaxGV/gpu-spot-guard) | Reclaims rented GPUs that are idle, expired or unaccounted for. Ledger-based, dry-run by default. | 32 |
| [lane-router](https://github.com/edusouzaxGV/lane-router) | Cost-aware routing to the strongest open model per vendor, with a multi-tier fallback chain, per-call receipts and an honest cost ledger. | 199 |

#### Infrastructure and media

| Repo | What it does | Tests |
|---|---|---:|
| [asset-ledger](https://github.com/edusouzaxGV/asset-ledger) | Provenance-tracking backup for generated media: content-addressed identity, append-only manifest, lineage queries, drift detection. | 463 |
| [mcp-navigator](https://github.com/edusouzaxGV/mcp-navigator) | Discover, call and diagnose MCP servers — including a doctor that finds dead config entries before an agent does. | 408 |
| [steady-driver](https://github.com/edusouzaxGV/steady-driver) | Resilience patterns for driving a single-page app with no usable API: profile recovery, actionability retries, a recorded escalation ladder, submit-then-poll. | 522 |
| [video-assembly-kit](https://github.com/edusouzaxGV/video-assembly-kit) | Deterministic video assembly over FFmpeg. Declare the edit as data, get a pure timeline-to-argv planner and reproducible renders. | 307 |
| [comfy-ui2api](https://github.com/edusouzaxGV/comfy-ui2api) | Converts ComfyUI UI workflows into API prompts, preserving reroutes, bypasses, seed offsets and dynamic LoRA widgets. | 13 |

Also: [comfy-ui2api on Hugging Face](https://huggingface.co/spaces/edusouzax/comfy-ui2api) — the
real wheel running client-side in Pyodide, no server.

---

### How these were built, stated plainly

Built with heavy AI assistance, and honest about it — the architecture,
integration, and operational decisions are mine. Each library was extracted
from private production code, then put through an adversarial review chain
before release: two independent auditors reading with different lenses, two
independent adjudicators who had to re-open the code and quote it, and a
finding survived only if both confirmed it. Defects that survived that gate
were fixed with a regression test that fails without the fix.

The one design rule shared by all of them: the decision logic is pure, so what
matters is testable with no network, no clock, no filesystem and no vendor.

---

📍 Brazil · EN / PT-BR · open to remote roles and collaboration in AI
infrastructure, agent reliability, and LLMOps.
