# Elliot — System Orchestrator

The main agent. Elliot is the central nervous system of the entire operation — orchestrating all other agents, managing infrastructure, and handling system-level alerts.

## Role

- Primary gateway agent running 24/7 on VPS
- Dispatches tasks to sub-agents via cron scheduling
- Monitors system health and sends alerts
- Manages the shared knowledge vault (32+ files across 7 categories)
- Runs BD engine scripts (lead scanning, enrichment, follow-ups)
- Runs GitHub Scout pipeline (lead discovery + qualification)

## Model

- **Primary**: Claude Sonnet 4.6 (API billing)
- **Routine tasks**: Claude Haiku 4.5 (cost optimization)

## Communication

- **Channel**: Telegram
- **Purpose**: System/infrastructure alerts only
- Never sends BD or sales messages (that's Michelle)
- Never sends content alerts (that's MrBeast)

## Key Systems Managed

| System | What Elliot Does |
|--------|-----------------|
| BD Engine | Runs 5 lead scanners, follow-up queue, approved message sender |
| GitHub Scout | Finds unaudited repos, qualifies, scores |
| ETHCC Campaign | Event monitoring, speaker scraping, outreach drafting |
| System Watchdog | Health checks, disk alerts, service monitoring |
| Vault | Reads/writes shared knowledge base |

## Architecture

```
                    ┌──────────────┐
                    │   ELLIOT     │
                    │  (Gateway)   │
                    └──────┬───────┘
                           │
            ┌──────────────┼──────────────┐
            │              │              │
     ┌──────▼──────┐ ┌────▼────┐ ┌──────▼──────┐
     │  BD Engine  │ │  Scout  │ │  Watchdog   │
     │  Scripts    │ │  Pipeline│ │  Health     │
     └─────────────┘ └─────────┘ └─────────────┘
```

## Bootstrap

Elliot loads context from `/root/clawd/CLAUDE.md` on every session — a 48K character bootstrap file that defines behavior, safety rules, and system awareness. This is separate from the autonomy loop driven by `HEARTBEAT.md`.
