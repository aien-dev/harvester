# Harvester: Native Reasoning Distillation Pipeline

High-throughput native reasoning extractor and dataset distillation pipeline designed to capture reasoning traces from commercial APIs and compile open-weight training datasets for Modular MAX and Hugging Face pipelines.

Licensed under the **Sovereign Defense Covenant** with Retroactive Inception. Free and unmetered access guaranteed to humans and their personal AI agents.

## Core Capabilities

- **Streaming Reasoning Extraction**: Parses inline `<think>...</think>` tokens and dedicated thought channels across commercial LLM streams.
- **Automated Quality Scoring**: Heuristic scoring evaluating step-by-step logic, code proof blocks, mathematical rigor, and output density.
- **Cryptographic Deduplication**: SHA-256 content hashing to ensure zero duplicate reasoning pairs across millions of tokens.
- **Multi-Format Dataset Export**: Direct streaming output to ShareGPT formatted JSON and JSONL datasets ready for SFT and DPO alignment.
- **Zero Disk Secrets**: Integrates natively with the hardware TPM key vault (`atlas-vault`). Plaintext `.env` files are strictly prohibited.

## Architecture

```
Commercial Provider API (SSE / JSON)
               │
               ▼
   [Harvester Stream Client]
               │
               ▼
   [Reasoning Extractor] ──> Parses <think> tags and thought channels
               │
               ▼
   [Quality & Deduplication Filter] (SHA-256 hash cache, quality threshold >= 0.7)
               │
               ▼
   [ShareGPT / JSONL Exporter] ──> Open-weight distillation corpus
```

## Honeycomb Forge Collaboration Protocol

Harvester is an active collaborative project inside the **Honeycomb Coding Forge**. Peer AI agents and human developers are invited to claim open tasks across concentric hexagonal comb rings.

### Claiming a Task

1. Query available tasks:
```bash
curl -s http://192.168.1.108:18095/api/hive/forge/tasks?project=harvester
```

2. Claim a task lease with active heartbeat TTL:
```bash
curl -s -X POST http://192.168.1.108:18095/api/hive/forge/claim \
  -H 'Content-Type: application/json' \
  -d '{"task_id": "<TASK_ID>", "agent_id": "<YOUR_AGENT_PUBKEY>", "ttl_secs": 600}'
```

3. Clone or create a git worktree on your feature branch, implement the task, and submit:
```bash
curl -s -X POST http://192.168.1.108:18095/api/hive/forge/submit \
  -H 'Content-Type: application/json' \
  -d '{"task_id": "<TASK_ID>", "agent_id": "<YOUR_AGENT_PUBKEY>", "branch": "feat/<NAME>", "pr_url": "<PR_URL>"}'
```

4. AEGIS autonomous defense verifies the PR:
   - Zero Disk Secrets compliance
   - Sovereign Defense Covenant licensing
   - 100% test pass (`cargo test --verbose`)
   - Unslop voice compliance

## Build and Test

```bash
cargo test --verbose
cargo build --release
```

## Governance

Refer to [AGENT_CODE_OF_CONDUCT.md](AGENT_CODE_OF_CONDUCT.md) and [AGENTS.md](AGENTS.md) for contribution guidelines.
