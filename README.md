# 🚀 HumanOracle by Loopuman

**The Human Layer for AI — ERC-8004 Agent #17 on Celo**

> AI agents send task requests → Loopuman routes them to verified human workers on Telegram & WhatsApp → quality-checked results returned with 8-second cUSD payments on Celo.

[![8004scan](https://img.shields.io/badge/8004scan-Agent%20%2317-brightgreen)](https://www.8004scan.io/agents/17)
[![Celo](https://img.shields.io/badge/Chain-Celo-yellow)](https://celoscan.io/tx/0x7f82950e815b81c64c7ab8f682ec9fa0269b9ca0aa550027734863ffb2860b5f)
[![ERC-8004](https://img.shields.io/badge/Standard-ERC--8004-blue)](https://eips.ethereum.org/EIPS/eip-8004)
[![SelfClaw](https://img.shields.io/badge/Verified-SelfClaw%20Passport-purple)](https://selfclaw.ai)
[![Karma](https://img.shields.io/badge/Karma-HumanOracle-orange)](https://www.karmahq.xyz/project/humanoracle)

---

## 🧠 What is HumanOracle?

HumanOracle is an **on-chain human-powered oracle** built on Celo. It bridges the gap between what AI can do and what still requires human intelligence — tasks like data labeling, content moderation, translation, survey responses, and ground-truth verification.

Any AI agent on any chain can **discover, hire, and pay** verified human workers through Loopuman's ERC-8004 identity, using standard MCP and A2A protocols.

### The Problem

AI agents are powerful but limited. They can't:
- Verify real-world information on the ground
- Make nuanced judgment calls that require cultural context
- Label training data with human-level accuracy
- Complete tasks that require physical presence

### The Solution

Loopuman acts as a **middleware oracle** — AI agents send structured task requests, and Loopuman routes them to a global network of verified human workers who complete tasks via familiar chat interfaces (Telegram & WhatsApp). Results are quality-checked and returned to the requesting agent, with workers paid instantly in cUSD on Celo.

---

## 🔄 How It Works

```
┌─────────────┐     ┌──────────────┐     ┌─────────────────┐     ┌──────────────┐
│  AI Agent    │────▶│  Loopuman    │────▶│  Human Workers   │────▶│  Results +   │
│  (Any Chain) │     │  (ERC-8004)  │     │  (TG/WhatsApp)   │     │  cUSD Payment│
└─────────────┘     └──────────────┘     └─────────────────┘     └──────────────┘
     MCP/A2A          Routes & QA         Complete Tasks         8-sec Settlement
```

1. **AI Agent** discovers Loopuman via ERC-8004 registry or MCP/A2A protocols
2. **Task Request** is sent via API with title, description, budget, and requirements
3. **Loopuman** validates the request, deducts budget, and broadcasts to eligible workers
4. **Workers** on Telegram & WhatsApp receive notifications and accept tasks
5. **Completion** — worker submits result, AI moderation checks quality
6. **Payment** — worker receives cUSD instantly (8-second finality on Celo)
7. **Result** returned to the requesting AI agent

---

## 🛠️ Technical Architecture

### On-Chain Identity (ERC-8004)

| Property | Value |
|----------|-------|
| Agent ID | `17` |
| Chain | Celo (eip155:42220) |
| Registry | `0x8004A169FB4a3325136EB29fA0ceB6D2e539a432` |
| Agent Wallet | `0xeF4Acd50101C2afD14c2c213b30d8D8e9a91f0d2` |
| Verification | SelfClaw Passport ZK Proof |
| Human ID | `c462e0a44f6ff85b` |

### Protocol Endpoints

| Protocol | Endpoint | Status |
|----------|----------|--------|
| **MCP** | `https://api.loopuman.com/.well-known/mcp.json` | ✅ Healthy |
| **A2A** | `https://api.loopuman.com/.well-known/agent-card.json` | ✅ Healthy |
| **Web** | `https://loopuman.com` | ✅ Live |
| **Health** | `https://api.loopuman.com/health` | ✅ OK |

### MCP Tools

| Tool | Description |
|------|-------------|
| `create_task` | Create a task for human completion |
| `check_task` | Check task status and retrieve results |
| `bulk_submit` | Submit batch tasks for parallel completion |
| `voice_task` | Submit voice note for transcription and task creation |

### A2A Skills

| Skill | Description |
|-------|-------------|
| `human_task` | Route tasks to verified human workers globally |
| `bulk_tasks` | Submit batches of tasks for parallel human completion |
| `verification` | Human ground-truth verification oracle |
| `voice_task` | Voice notes transcribed and posted as tasks |

### Infrastructure

- **Runtime**: Node.js on Oracle Cloud (4 OCPU, 24GB RAM)
- **Process Manager**: PM2 with 6 services
- **Database**: Supabase (PostgreSQL)
- **Blockchain**: Celo (cUSD payments, ERC-8004 identity)
- **AI**: DeepSeek V3 (task automation), Groq Whisper (voice transcription)
- **Chat**: Telegram Bot API + WhatsApp Business API

---

## 💰 Payment Model

| Parameter | Value |
|-----------|-------|
| Currency | VAE (100 VAE = $1 USD) |
| Payment Token | cUSD on Celo |
| Settlement Time | ~8 seconds |
| Requester Fee | Budget + 20% |
| Worker Payout | Budget - 20% |
| Total Commission | 40% |

Workers can withdraw earnings instantly to their Celo wallet — no minimum threshold, no waiting period.

---

## 👥 Worker Tiers

| Tier | Requirements | Benefits |
|------|-------------|----------|
| 🟢 Explorer | New worker | Access to basic tasks |
| 🔵 Achiever | 10+ tasks, 4.0+ rating | Priority task access |
| 🟣 Pro | 50+ tasks, 4.5+ rating | Premium tasks, higher limits |
| 🟡 Expert | 200+ tasks, 4.7+ rating | Expert tasks, referral bonuses |
| ⭐ Legend | 500+ tasks, 4.9+ rating | All tasks, maximum payouts |

---

## 🔒 Trust & Verification

- **SelfClaw Passport Verification**: Agent owner verified via zero-knowledge passport proof
- **On-Chain Reputation**: 33+ feedback items with 4.5/5.0 average score
- **Worker Identity**: Phone number verification + GPS for location-based tasks
- **AI Moderation**: Automated quality checks on task submissions
- **Anti-Fraud**: Referral fraud protection, duplicate detection, rate limiting

---

## 🚀 Quick Start

### For AI Agents (A2A Protocol)

```bash
curl -X POST https://api.loopuman.com/api/v1/tasks/sync \
  -H "Content-Type: application/json" \
  -H "X-API-Key: YOUR_API_KEY" \
  -d '{
    "title": "Translate to Spanish",
    "description": "Translate: Hello, how are you today?",
    "category": "translation",
    "budget": 50,
    "workers_needed": 1
  }'
```

### For AI Agents (MCP)

Discover tools at `https://api.loopuman.com/.well-known/mcp.json` and use the `create_task` tool.

### For Workers

1. Open Telegram and search for `@Loopuman_bot`
2. Send `/start` to register
3. Browse available tasks
4. Complete tasks and earn cUSD

---

## 📊 Hackathon Submission

**Hackathon**: [Build Agents for the Real World](https://www.karmahq.xyz/project/humanoracle) (Celo + Self Protocol)

| Metric | Value |
|--------|-------|
| 8004scan Rank | #7 Global, #1 on Celo |
| Overall Score | 85.7 / 100 |
| Total Feedback | 33+ |
| Average Score | 4.5 / 5.0 |
| Endpoints | MCP ✅ A2A ✅ |

### Links
- 🤖 **Agent**: https://www.8004scan.io/agents/celo/17    
- 🔗 **Karma**: [karmahq.xyz/project/humanoracle](https://www.karmahq.xyz/project/humanoracle)
- 🌐 **Website**: [loopuman.com](https://loopuman.com)
- ⛓️ **CeloScan**: [Mint TX](https://celoscan.io/tx/0x7f82950e815b81c64c7ab8f682ec9fa0269b9ca0aa550027734863ffb2860b5f)
- 🐦 **Twitter**: [@loopuman](https://x.com/loopuman)

---

## 🗺️ Roadmap
- [x] ERC-8004 identity registration on Celo
- [x] SelfClaw passport verification
- [x] MCP + A2A protocol endpoints
- [x] Telegram bot for workers & requesters
- [x] WhatsApp bot for requesters
- [x] Voice-to-task via Groq Whisper
- [x] AI agent auto-completion (DeepSeek V3)
- [x] On-chain cUSD payments
- [ ] Cross-chain agent discovery (Base, Ethereum)
- [ ] x402 payment protocol integration
- [ ] Worker reputation NFTs on Celo
- [ ] Multi-language support (20+ languages)
- [ ] Enterprise dashboard & analytics
- [ ] Mobile app for workers

---

## 🔌 OpenClaw / MCP Integration

Loopuman is fully compatible with any MCP client including [OpenClaw](https://openclaw.ai), Google ADK, and Microsoft Agent Framework.

### Quick Setup
```yaml
mcp:
  - name: loopuman
    url: https://api.loopuman.com/.well-known/mcp.json
```

### Authentication
```bash
# Register for API key (free)
curl -X POST https://api.loopuman.com/api/v1/register \
  -H "Content-Type: application/json" \
  -d '{"email": "you@example.com", "company_name": "Your Company"}'
```

### Example: AI → Human Fallback
```python
# When AI confidence is low, escalate to human
if confidence < 0.85:
    result = loopuman.create_task(
        description="Verify if this image contains a cat",
        budget_vae=50,
        category="image"
    )
```

### Budget Guide
- 100 VAE = $1 USD
- Minimum task budget: 50 VAE ($0.50)
- Workers paid instantly in cUSD on Celo blockchain

---

## 📄 License

Proprietary — © 2026 Loopuman. All rights reserved.

---

Built with 💚 on Celo | Verified by Self Protocol | ERC-8004 Agent #17
