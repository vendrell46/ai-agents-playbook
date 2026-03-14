# Dobby — Personal Health + Finance Assistant (Personal)

Dobby is a personal agent — health and finance tracking with automated alerts and insights. Named because he's always watching, always serving.

## Role

- Tracks health metrics from Apple Health (sleep, HRV, resting heart rate, workouts)
- Tracks financial data from bank accounts (spending, bills, tax reserves)
- Sends proactive alerts and reminders
- Generates AI-powered insights on habits and spending patterns

## Model

- **Chat**: Claude Haiku 4.5 (fast, cheap for conversational queries)
- **Cron insights**: Claude Sonnet 4.6 (deeper analysis)
- **LLM insights**: Claude Haiku 4.5 (~$0.50/mo)

## Communication

- **Channel**: Telegram (dedicated bot)
- **Purpose**: Health alerts, finance reminders, habit insights

## Health Pipeline

```
Apple Health → iOS Export App → Webhook → Supabase
  (iPhone)      (auto-sync)    (port 3200)  (43K+ rows)
                                               │
                               ┌───────────────┼───────────────┐
                               ▼               ▼               ▼
                        ┌───────────┐   ┌───────────┐   ┌───────────┐
                        │ Sleep     │   │ Workout   │   │ Weekly    │
                        │ alert     │   │ nudge     │   │ health    │
                        │ (7:30am)  │   │ (8pm)     │   │ brief     │
                        └───────────┘   └───────────┘   └───────────┘
```

**Data**: 43K+ health data rows spanning Jan 2023 - present
**Metrics tracked**: Sleep duration, resting heart rate, HRV, workout frequency, active energy

## Finance Pipeline

```
Bank CSV Import → Supabase → Automated Alerts
                                     (2K+ tx)
                                        │
                        ┌───────────────┼───────────────┐
                        ▼               ▼               ▼
                 ┌───────────┐   ┌───────────┐   ┌───────────┐
                 │ Spending  │   │ Bill      │   │ Tax       │
                 │ alerts    │   │ reminders │   │ reserve   │
                 │ (weekly)  │   │ (daily)   │   │ (monthly) │
                 └───────────┘   └───────────┘   └───────────┘
```

**Supabase tables**: `transactions`, `recurring_bills`, `net_worth_snapshots`, `merchant_categories`, `budget_config`

## Plugin Tools

Dobby has 11 tools available through OpenClaw plugins:

| Category | Tools |
|----------|-------|
| **Health** (4) | Query metrics, list workouts, health summary, metric list |
| **Spending** (2) | Query transactions, spending summary |
| **Financial** (5) | Bill status, tax estimate, net worth, budget check, cashflow |
