# Dobby — Cron Schedule

All times UTC. Dobby has 13 crons — the most of any single agent. All run via system crontab (not OpenClaw gateway).

## Health Crons

| Cron | Schedule | Model | What It Does |
|------|----------|-------|-------------|
| Workout nudge | Daily 20:00 | None | Reminder if no workout logged today |
| Weekly health brief | Monday 07:00 | Sonnet | Sleep, HRV, RHR, workout summary |
| Sleep alert | Daily 07:30 | None | Alert if <6h sleep detected |

## Finance Crons

| Cron | Schedule | Model | What It Does |
|------|----------|-------|-------------|
| Spending alert | Monday 08:45 | None | Weekly spending vs budget |
| Bill reminder | Daily 08:00 | None | Upcoming bills due |
| Merchant cleanup | Wednesday 19:00 | None | Categorize uncategorized transactions |
| Spending velocity | 15th of month 20:00 | None | Mid-month spending pace check |
| Tax reserve | 1st of month 09:00 | None | Calculate tax set-aside for the month |
| Net worth snapshot | 1st of month 10:00 | None | Record net worth data point |
| CSV export reminder | Sunday 19:00 | None | Reminder to export bank CSVs |

## AI Insight Crons (Haiku, ~$0.50/mo)

| Cron | Schedule | Model | What It Does |
|------|----------|-------|-------------|
| Spending diary | Tuesday 20:00 | Haiku | AI analysis of recent spending patterns |
| Habits review | Thursday 20:00 | Haiku | Cross-reference health + spending habits |
| Smart money tips | Saturday 10:00 | Haiku | Personalized financial suggestions |

## Total: 13 crons
