# Trinity — Opportunity Detection + Education (Personal)

Trinity is a personal agent — not business-facing. Two jobs: find the next business opportunity worth building, and deliver structured daily education.

## Role

- **Opportunity detection**: Scans signals from multiple sources, scores them through an AI advisory board, surfaces only high-confidence opportunities
- **Education**: Delivers 4 personalized lessons per day — finance and eMBA curriculum

## Model

- **Primary**: Claude Sonnet 4.6 (both systems)

## Communication

- **Channel**: Telegram (dedicated bot)
- **Purpose**: Signal alerts, education lessons, weekly review reminders

## Opportunity Detection

```
Sources                      Pipeline                      Output
┌──────────────┐           ┌──────────────┐            ┌──────────┐
│ RSS feeds    │           │              │            │          │
│ Reddit       │── scan ──►│ Stage 1:     │            │ Telegram │
│ GitHub       │           │ Extract      │── score ──►│ alert    │
│ trending     │           │ signals      │            │ (≥16/20) │
│ CoinGecko   │           │ (Sonnet)     │            │          │
└──────────────┘           │              │            └──────────┘
                           │ Stage 2:     │
                           │ Advisory     │
                           │ board scores │
                           └──────────────┘
```

### Advisory Board (AI Personas)

Each opportunity is scored from 5 perspectives:

| Advisor Persona | Lens |
|-----------------|------|
| Growth strategist | Demand, market timing |
| Business model expert | Unit economics, offer design |
| Leverage thinker | Scalability, asymmetric upside |
| Indie builder | Ship speed, solo-founder fit |
| Value investor | Risk, moat, long-term value |

**Scoring**: Demand / Edge / Ship / Automation — each 1-5 (max 20)
- **≥16**: Send to Telegram immediately
- **14-15**: Mention in weekly review
- **<14**: Cut

### Weekly Review

Every Monday — deep analysis with Opus. Cross-reference signals, update world model, log or kill ideas in the Idea Ledger.

**Philosophy**: BUILD only. No passive investing ideas (stocks, ETFs, bonds).

## Education System

4 structured lessons per day, delivered to Telegram:

| Time (UTC) | Subject | What It Covers |
|-----------|---------|---------------|
| 08:00 | Finance | Investing, tax optimization, portfolio management |
| 08:30 | eMBA | Business strategy, operations, leadership |
| 19:00 | Finance | Evening continuation |
| 19:30 | eMBA | Evening continuation |

### Finance Track
- Adaptive daily lessons based on progress
- Tracks: investing fundamentals, tax strategy, portfolio construction
- Progress tracked in local JSON

### eMBA Track
- 8 modules, 112 topics covering core MBA curriculum
- User profile tracks learning style and knowledge gaps
- Adaptive difficulty based on comprehension
