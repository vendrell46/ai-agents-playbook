# Elliot — Outcomes & Results

## BD Pipeline Results

- **5 lead scanners** operational — DeFiLlama, CryptoRank, ChainPlay, RootData, GitHub Scout
- **64 contacts** enriched through Apollo
- **22 RootData leads** discovered, 18 promoted to deals
- **15 outreach drafts/day** generated and sent to Telegram for approval
- 9-stage deal pipeline with weighted scoring

## GitHub Scout Results

- Scan cache prevents duplicate evaluation (30-day expiry)
- Scoring formula (28-point max) with hard gates and blocklists (~70 orgs)
- Qualification pass adds multi-source research (GitHub, website, Twitter, RootData)

## What Broke

| Issue | Impact | Resolution |
|-------|--------|------------|
| Apollo bad data | 12 of 32 contacts had wrong emails | Added validation pass, cleaned pipeline |
| Bootstrap bloat | 48K chars truncated to 20K, wasting tokens | Restructured into vault + reference docs |
| Billing errors | OpenClaw silently disables agent | Manual clear required, added to playbook |
| Vault auto-loader | Intermittent MODULE_NOT_FOUND | Open issue — module resolution in gateway |
