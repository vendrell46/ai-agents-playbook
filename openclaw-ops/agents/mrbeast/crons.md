# MrBeast — Cron Schedule

All times UTC. MrBeast runs 11 crons per account + 1 weekly reminder = 33+ total.

## Per-Account Crons (x3 accounts)

| Cron | Schedule | Model | What It Does |
|------|----------|-------|-------------|
| `batch-publish.py` | Every 15 min | None | Publishes next scheduled post from queue |
| `batch-analytics.py` | Monday 08:15-08:20 | Sonnet | Weekly engagement metrics digest |
| Weekly reminder | Monday 08:00-08:10 | None | Telegram reminder to generate content |

## Account-Specific Schedules

### @ElliotAgentRepo
- Publish: every 15 min
- Analytics: Mon 08:15
- Reminder: Mon 08:00

### @TheBlockChainer
- Publish: every 15 min (includes BIP threads Wed/Fri/Mon 18:00)
- Analytics: Mon 08:15
- Reminder: Mon 08:05

### @ZealynxSecurity
- Publish: every 15 min
- Analytics: Mon 08:20
- Reminder: Mon 08:10

## Content Pipeline

```
Monday morning
  │
  ├── MrBeast sends reminder (Telegram)
  ├── Carlos generates 14 threads/account (Claude Code)
  ├── Batch loader pushes to queue
  └── batch-publish fires every 15 min for the week
```
