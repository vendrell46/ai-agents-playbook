# Elliot — Cron Schedule

All times UTC. Elliot manages the most crons of any agent — primarily BD and lead generation.

## BD Engine

| Cron | Schedule | Model | What It Does |
|------|----------|-------|-------------|
| `lead-source-aggregator.js` | Weekly (Sunday) | Opus | Scans DeFiLlama, CryptoRank, ChainPlay for new protocols |
| `follow-up-queue.js` | 2x/day | Opus | Generates follow-up drafts for overdue deals |
| `send-approved-messages.js` | Every 30 min | None | Sends messages Carlos has approved in Telegram |
| `client-monitor.js` | Weekly (Wednesday) | Opus | Monitors past clients — GitHub activity, TVL changes |
| `bd-analytics-cron.js` | Weekly (Monday 08:30) | None | Generates funnel metrics + sends Telegram brief |

## GitHub Scout

| Cron | Schedule | Model | What It Does |
|------|----------|-------|-------------|
| `github-scout.js` | Daily (08:00) | Sonnet | Finds new unaudited Solidity repos |
| `scout-qualify.js` | Daily (08:30) | Sonnet | Multi-source research, scores and classifies leads |

## ETHCC Campaign

| Cron | Schedule | Model | What It Does |
|------|----------|-------|-------------|
| `ethcc-event-monitor.js` | Every 6h | Sonnet | Polls Luma for new attendees |
| `ethcc-attendee-intel.js` | Wed + Sun (09:00) | Sonnet | Deep research on classified attendees |
| `ethcc-apollo-enrich.js` | Daily | None | Apollo enrichment (100/day limit) |
| `ethcc-outreach-drafter.js` | 2x/day | Sonnet | Drafts outreach messages (20/run) |
| `ethcc-x-monitor.js` | 4x/day | Sonnet | Monitors X for ETHCC-related engagement |
| `ethcc-sprint-analytics.js` | Daily | None | Campaign metrics digest |

## System

| Cron | Schedule | Model | What It Does |
|------|----------|-------|-------------|
| `system-watchdog` | Periodic | Haiku | Health checks, disk space, service status |
