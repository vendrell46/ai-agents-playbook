# Elon — Cron Schedule

All times UTC. Elon runs engagement crons for each of the 3 X accounts.

## @ElliotAgentRepo

| Cron | Schedule | Model | What It Does |
|------|----------|-------|-------------|
| `reply-engine.py` | 3x/day | Opus | ~~Reply to relevant tweets~~ (DISABLED — 403) |
| `quote-engine.py` | 3x/day | Opus | Quote-tweet relevant content |
| `follow-engine.py` | 1x/day (12:00) | Opus | Targeted follows with Telegram detail |
| `reactive-scanner.py` | 4x/day (07, 11, 15, 19) | Haiku | Real-time engagement scanning |

## @TheBlockChainer

| Cron | Schedule | Model | What It Does |
|------|----------|-------|-------------|
| `bc-reply-engine.py` | 3x/day | Opus | ~~Reply~~ (DISABLED) |
| `bc-quote-engine.py` | 2x/day | Opus | Quote-tweet |
| `bc-follow-engine.py` | 1x/day | Opus | Targeted follows |
| `bc-reactive-scanner.py` | 4x/day | Haiku | Reactive scanning |

## @ZealynxSecurity

| Cron | Schedule | Model | What It Does |
|------|----------|-------|-------------|
| `zs-reply-engine.py` | 3x/day (09:30, 13:30, 17:30) | Opus | ~~Reply~~ (DISABLED) |
| `zs-quote-engine.py` | 2x/day (11:00, 16:00) | Opus | Quote-tweet |
| `zs-follow-engine.py` | 1x/day (12:00) | Opus | Targeted follows |
| `zs-reactive-scanner.py` | 4x/day (07, 11, 15, 19) | Haiku | Reactive scanning |

## Total: ~24 engagement crons across 3 accounts
