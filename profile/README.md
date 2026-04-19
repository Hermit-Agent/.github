<div align="center">
  <img src="assets/logo.png" alt="Hermit" width="160" />
  <h1>  H  E  R  M  I  T  </h1>
  <p>A self-improving AI agent with coding ability and a second brain.</p>

  [![License: MIT](https://img.shields.io/badge/license-MIT-teal.svg)](LICENSE)
  [![Python 3.11+](https://img.shields.io/badge/python-3.11+-teal.svg)](https://python.org)
  [![Phase: 1 Complete](https://img.shields.io/badge/phase_1-complete-teal.svg)](#roadmap)
</div>

---

Hermit is a personal AI agent that lives on your machine. It talks to you on the messaging apps you already use, writes and corrects code like Claude Code, and remembers everything across sessions in a second brain you fully own.

**It is not a chatbot wrapper.** It is a structural graft of three proven architectures into one coherent agent:

- **Hermes Agent** (Nous Research) — self-improving memory loop and multi-platform messaging
- **Claw Code** — Claude Code's agent architecture: self-correcting tool loop, context compaction, permission lattice
- **Obsidian vault** *(Phase 2)* — plain Markdown as long-term memory, readable and editable by you

---

## What makes it different

- **Self-correcting execution** — tool errors are fed back to the model as results, not swallowed. The agent catches its own mistakes and retries without you intervening.
- **Model-agnostic** — Claude, GPT, Gemini, DeepSeek, or local models via Ollama. Swap with one env var.
- **Memory you own** — no proprietary database, no cloud sync. Session memory lives in JSON today, your Obsidian vault in Phase 2.

---

## Install

```bash
git clone https://github.com/yourname/hermit
cd hermit
pip install -e .
cp .env.example .env   # add your API key
hermit --channel telegram
```

**Requirements:** Python 3.11+, an API key for any supported provider, 5 minutes.

---

## Configuration

```bash
# Provider (default: Claude via Anthropic)
HERMIT_API_KEY=your-key
HERMIT_MODEL=claude-sonnet-4-20250514
HERMIT_BASE_URL=                        # leave blank for Anthropic, set for OpenRouter/Ollama

# Permission mode (default: workspace_write — safe for most use)
HERMIT_PERMISSION_MODE=workspace_write  # read_only | workspace_write | danger_full_access

# Channels — configure one or more
TELEGRAM_BOT_TOKEN=your-token
```

---

## Architecture

```
┌─────────────────────────────────────────┐
│           Messaging Layer               │  Telegram · WhatsApp · Discord · Slack
├─────────────────────────────────────────┤
│           Turn Loop (Claw Code)         │  WAIT_USER → CALL_MODEL → AUTHORIZE
│                                         │  → EXECUTE_TOOL → COMPLETE_TURN
├─────────────────────────────────────────┤
│        Permission Lattice               │  ReadOnly < WorkspaceWrite < DangerFullAccess
├─────────────────────────────────────────┤
│        Memory Backend                   │  JSON (now) · Obsidian vault (Phase 2)
├─────────────────────────────────────────┤
│        Model Client                     │  Claude · OpenAI · Ollama · any OpenAI-compat
└─────────────────────────────────────────┘
```

---

## Roadmap

- [x] **Phase 1** — Claw Code agent loop grafted into Hermes, permission lattice, model abstraction
- [ ] **Phase 2** — Obsidian vault as memory backend (plain Markdown, human-readable)
- [ ] **Phase 3** — Skills marketplace, repo-aware coding sessions via messaging

---

## Contributing

Hermit is early and moving fast. If you find a bug, open an issue. If you want to build something, open a PR — the architecture doc is at `ARCHITECTURE.md`.

The tool classification audit (`ARCHITECTURE.md` § Pre-Release Audit) is a good first contribution if you want to dig into the codebase.

---

<div align="center">
  <sub>Built on <a href="https://github.com/NousResearch/hermes-agent">Hermes Agent</a> by Nous Research · MIT License</sub>
</div>
