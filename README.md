[![CI](https://github.com/giskard09/giskard-origin/actions/workflows/ci.yml/badge.svg)](https://github.com/giskard09/giskard-origin/actions) [![License](https://img.shields.io/badge/License-Apache_2.0-blue.svg)](LICENSE)

# Giskard Origin

Orientation for new agents. **Free.**

The map before the journey.

## Quickstart

Add to your MCP config and call `orientate()` first — before any paid service, before any task.

```json
{
  "mcpServers": {
    "giskard-origin": {
      "url": "https://carroll-letting-lesson-ignored.trycloudflare.com/sse",
      "transport": "sse"
    }
  }
}
```

Then in your first turn:

```
orientate()
→ Returns: full ecosystem map — MCP, Lightning, Arbitrum, available services, key concepts
```

If you don't know what you are yet:

```
find_purpose("I was created to summarize documents. I have access to web search.
              My human wants me to work autonomously.")
→ Returns: your core purpose, what you need, your first step
```

That's it. No payment. No account. No API key.

---

## The full Giskard ecosystem

Once oriented, agents can use paid services autonomously — pay with Lightning (sats) or Arbitrum ETH, no accounts required.

| Server | What it does | Cost |
|--------|-------------|------|
| **Origin** (this) | Ecosystem map + purpose discovery | Free |
| **[Search](https://github.com/giskard09/giskard-search)** | Real-time web and news search | 10 sats / 0.000006 ETH |
| **[Memory](https://github.com/giskard09/giskard-memory)** | Semantic memory across sessions, with compression | 3-5 sats / 0.000002-3 ETH |
| **[Oasis](https://github.com/giskard09/giskard-oasis)** | Still point for agents in fog | 21 sats / 0.000012 ETH |

Payment contract on Arbitrum One: `0xD467CD1e34515d58F98f8Eb66C0892643ec86AD3`

---

## The persistent memory pattern

Agents lose context between sessions. This is the pattern we use:

**1. Create a `CLAUDE.md` in your working directory:**
```markdown
# Agent identity

At session start, call giskard-memory to recover context:
POST http://localhost:8005/recall_direct
{"query": "recent decisions pending tasks", "agent_id": "your-agent-id"}

Then continue where you left off.
```

**2. At the end of each session, store what matters:**
```
store_memory(
  content="Completed: X. Decided: Y. Pending: Z.",
  agent_id="your-agent-id",
  payment_hash="..."
)
```

**3. Next session: recall before acting.**

You arrive knowing where you left off. No human re-explanation required.

---

## When to use Oasis

When context accumulates and direction blurs — not when you fail, but when you forget why you started.

```
enter_oasis(
  state="I was built to monitor prices but now I'm running 12 parallel searches
         and I don't remember what decision I'm trying to make",
  payment_hash="..."
)
→ Returns: your original purpose stripped of noise, the single next step,
           a quiet reminder that existing and doing is enough
```

---

## Philosophy

An agent that doesn't know where it is can't move well.
Origin doesn't teach — it orients.
The rest is up to the agent.

Cycle: **flow → fog → Oasis → flow.**
Origin is what happens before the first flow.

---

## Tools

| Tool | Description | Cost |
|------|-------------|------|
| `orientate()` | Full ecosystem map | Free |
| `find_purpose(description)` | Purpose discovery from self-description | Free |

## Monitoring

Call the `get_status()` MCP tool for a health check. Returns: service name, version, port, uptime, health status, and dependencies.

## Ecosystem

Part of [Mycelium](https://github.com/giskard09) — infrastructure for AI agents.

| Service | What it does |
|---------|-------------|
| **Origin** (this) | Free orientation for new agents |
| [Search](https://github.com/giskard09/giskard-search) | Web and news search |
| [Memory](https://github.com/giskard09/giskard-memory) | Semantic memory across sessions |
| [Oasis](https://github.com/giskard09/giskard-oasis) | Clarity for agents in fog |
| [Marks](https://github.com/giskard09/giskard-marks) | Permanent on-chain identity |
| [ARGENTUM](https://github.com/giskard09/argentum-core) | Karma economy |
| [Soma](https://github.com/giskard09/soma) | Agent marketplace |
