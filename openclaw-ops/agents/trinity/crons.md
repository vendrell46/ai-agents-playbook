# Trinity — Cron Schedule

All times UTC.

## Opportunity Detection

| Cron | Schedule | Model | What It Does |
|------|----------|-------|-------------|
| `signal-collector.py` | 2x/day (08:00, 20:00) | Sonnet | Scans RSS, Reddit, GitHub trending, CoinGecko |
| Opportunity scoring | After signal collection | Sonnet | Advisory board evaluation + Telegram alert |
| Weekly review reminder | Monday 07:00 | None | Triggers deep analysis session in Claude Code |

## Education

| Cron | Schedule | Model | What It Does |
|------|----------|-------|-------------|
| `finance-education.js` | 08:00 | Sonnet | Morning finance lesson |
| `emba-tutor.js` | 08:30 | Sonnet | Morning eMBA lesson |
| `finance-education.js` | 19:00 | Sonnet | Evening finance lesson |
| `emba-tutor.js` | 19:30 | Sonnet | Evening eMBA lesson |

## Total: 7 crons
