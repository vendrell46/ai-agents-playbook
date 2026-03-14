# Elon — Outcomes & Results

## Activity

- **24 engagement crons** running across 3 X accounts
- Quote engines: 7-9 quote-tweets/day
- Follow engines: ~45 targeted follows/day (25 + 10 + 10)
- Reactive scanning: 12 scans/day looking for real-time opportunities

## What Broke

| Issue | Impact | Resolution |
|-------|--------|------------|
| Reply engines 403 | All reply functionality disabled | X Free tier limitation — pivoted to quotes + reactive |
| Shared consumer key | Can't interact between own accounts | Architecture limitation — no fix on Free tier |
| Exit code 0 on errors | Failed API calls looked successful | Added stdout parsing for `"❌"` markers |
| Cross-account interaction | Elliot can't retweet ZealynxSecurity | Same consumer key shared across accounts blocks it |

## Lessons Learned

1. **X Free tier is severely limited** — reply is the most valuable engagement type and it's blocked
2. **Quote-tweets are an effective substitute** — they still surface your content in the original author's notifications
3. **Reactive scanning is high-ROI** — catching trending conversations early produces the best engagement per impression
