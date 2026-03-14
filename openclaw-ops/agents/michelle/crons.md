# Michelle — Cron Schedule

Michelle doesn't run her own crons — she's triggered by Elliot's BD engine scripts. Her activity is driven by the approval queue.

## Triggered By

| Trigger | Source | Frequency |
|---------|--------|-----------|
| Outreach drafts ready | `follow-up-queue.js` (Elliot) | 2x/day |
| Approved messages | `send-approved-messages.js` (Elliot) | Every 30 min |
| ETHCC outreach | `ethcc-outreach-drafter.js` (Elliot) | 2x/day |
| LinkedIn pushes | `linkedin-push` cron | As scheduled |

## Message Queue Flow

1. Elliot generates draft → writes to `message_queue` (Supabase)
2. Michelle formats and sends to Telegram for approval
3. Carlos approves/edits/rejects in Telegram
4. On approval → `send-approved-messages.js` picks up and delivers
