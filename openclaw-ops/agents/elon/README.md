# Elon — X Engagement Agent

Elon handles the engagement side of X — replies, quotes, follows, and reactive scanning. While MrBeast publishes content, Elon makes sure it gets seen.

## Role

- Runs reply engines across all 3 X accounts
- Runs quote engines (strategic quote-tweets of relevant content)
- Runs follow engines (targeted audience building)
- Runs reactive scanners (real-time engagement with trending conversations)

## Model

- **Primary**: Claude Opus 4.6 (reply/quote engines — needs quality)
- **Reactive scanning**: Claude Haiku 4.5 (volume, cost optimization)

## Communication

- **Channel**: Internal (no direct Telegram channel)
- Engagement results feed into MrBeast's weekly analytics

## How It Works

```
          ┌─────────────────────────────────────┐
          │           ELON                       │
          │                                      │
          │  ┌──────────┐    ┌──────────┐       │
          │  │ Reply    │    │ Quote    │       │
          │  │ Engine   │    │ Engine   │       │
          │  │ 3x/day   │    │ 2-3x/day│       │
          │  └──────────┘    └──────────┘       │
          │                                      │
          │  ┌──────────┐    ┌──────────────┐   │
          │  │ Follow   │    │ Reactive     │   │
          │  │ Engine   │    │ Scanner      │   │
          │  │ 1x/day   │    │ 4x/day       │   │
          │  └──────────┘    └──────────────┘   │
          │                                      │
          └─────────────────────────────────────┘
```

## Engagement Strategy

| Engine | Purpose | Targeting |
|--------|---------|-----------|
| **Reply** | Join conversations, add value | Accounts in niche (DeFi, security, AI) |
| **Quote** | Amplify + add perspective | Relevant tweets from followed accounts |
| **Follow** | Build audience | Founders, devs, protocols in target verticals |
| **Reactive** | Real-time engagement | Trending topics matching keywords |

## Current Status

**Reply engines are disabled** across all 3 accounts — X Free tier returns HTTP 403 on reply attempts. Pivoted to quotes + reactive scanning as primary engagement.

## Cost

- Opus engines: ~$6/mo across 3 accounts
- Haiku reactive: ~$0.50/mo
- Total: ~$6.50/mo
