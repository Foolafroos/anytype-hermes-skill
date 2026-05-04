# 💎 Anytype — Hermes Agent Skill

> The definitive Hermes Agent skill for interacting with [Anytype](https://anytype.io) via its official MCP server.

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE)
[![Anytype](https://img.shields.io/badge/Anytype-MCP_Server-blue)](https://docs.anytype.dev)

---

## Why Anytype?

### 🔒 Your data. Your device. Your rules.

| Feature | Anytype | Notion | Obsidian |
|---|---|---|---|
| **Data ownership** | ✅ 100% local + encrypted sync | ❌ Hosted on their servers | ✅ Local files |
| **End-to-end encryption** | ✅ Built-in (Object Encryption) | ❌ Server-side only | ❌ None |
| **Offline-first** | ✅ Works without internet | ❌ Requires connection | ✅ Local markdown |
| **Vendor lock-in** | ✅ Open format, exportable | ❌ Hard to leave | ✅ Plain markdown |
| **AI training on your data** | ❌ Never | ✅ Yes (ToS allows it) | ❌ No |
| **Decentralized sync** | ✅ IPFS + ActivityPub | ❌ Centralized cloud | ❌ Manual/Git |
| **MCP integration** | ✅ Official server | ⚠️ Community workarounds | ⚠️ Community workarounds |

### The problem with cloud notes

Notion, Evernote, Coda — they all share a dark secret: **your knowledge becomes their training data**. Their terms of service explicitly allow using your content to improve their AI models. That means every thought, every project plan, every private note fuels someone else's LLM.

Obsidian is better — it stores files locally as markdown — but it's still just a file viewer. No native encryption, no decentralized sync, no official MCP server. You're on your own for integrations.

### Anytype does it differently

- **Local-first architecture** — Everything lives on your device first. Sync is optional and encrypted.
- **Object Encryption** — End-to-end encryption means even Anytype's servers can't read your data.
- **Decentralized** — Sync runs over IPFS and ActivityPub. No central database to hack or subpoena.
- **Open MCP server** — Official `@anyproto/anytype-mcp` server lets AI agents interact with your knowledge base securely.
- **No data harvesting** — Their ToS explicitly prohibits using your data for AI training.

> **TL;DR:** Anytype is the only serious knowledge base that respects your privacy AND plays nice with AI agents.

---

## What This Skill Does

This skill enables Hermes Agent to:

- ✅ Create, read, update, and delete Anytype objects (pages, notes, tasks, collections)
- ✅ Search across your entire Anytype knowledge base
- ✅ Manage relations, sets, and views
- ✅ Import/export structured data
- ✅ Execute complex multi-step workflows via JSON-RPC

All operations go through the **official Anytype MCP server** — no reverse-engineered APIs, no community hacks.

---

## Installation

```bash
# Install via Hermes CLI
hermes skills install https://github.com/Foolafroos/anytype-hermes-skill

# Or clone manually
git clone https://github.com/Foolafroos/anytype-hermes-skill ~/.hermes/skills/anytype
```

### Prerequisites

1. An Anytype account with API access
2. Generate an API token in Anytype → Settings → API Keys
3. Install Node.js (for `npx`)

### Configuration

Add your credentials to your Hermes environment:

```bash
export OPENAPI_MCP_HEADERS='{"Authorization":"Bearer <YOUR_TOKEN>", "Anytype-Version":"<VERSION>"}'
```

> 🔐 Your token is never stored by this skill — it's passed as an environment variable per-request.

---

## Quick Start

Once installed, just ask Hermes Agent to interact with Anytype:

```
"Create a new page in Anytype called 'Project Ideas'"
"Search my Anytype for anything about AI agents"
"Update the status of my task to 'In Progress'"
```

The skill handles all the JSON-RPC communication under the hood.

---

## Architecture

```
┌─────────────┐     JSON-RPC      ┌──────────────┐
│  Hermes     │  ──────────────►  │  Anytype     │
│  Agent      │  (via MCP server) │  Local App   │
│  (this skill)│                  │  (encrypted) │
└─────────────┘                   └──────────────┘
                                        │
                                        ▼
                                   ┌──────────────┐
                                   │   IPFS /     │
                                   │ ActivityPub  │
                                   │  (optional   │
                                   │   sync)      │
                                   └──────────────┘
```

---

## References

- [Authentication guide](references/authentication.md)
- [JSON-RPC patterns](references/jsonrpc-pattern.md)
- [Twitter bookmark import example](references/twitter-bookmark-import-2026.md)

---

## Philosophy

This skill was built with one principle: **your knowledge should not be someone else's product**.

Every time you choose a cloud service that mines your data, you lose a little sovereignty. Anytype exists to reverse that trend — and this skill makes it the default knowledge backend for your AI agent.

---

## License

MIT — use it, modify it, share it. Just don't sell your data.
