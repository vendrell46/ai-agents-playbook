# Dobby — Outcomes & Results

## Health Tracking

- **43K+ health data rows** from Jan 2023 to present
- Automated sleep alerts catch <6h nights
- Workout nudges maintain accountability
- Weekly brief shows trends (sleep avg, HRV trajectory, RHR)

## Finance Tracking

- **2K+ transactions** categorized from bank CSV imports
- Automated bill reminders prevent missed payments
- Monthly tax reserve calculations
- Net worth snapshots create long-term trajectory
- Mid-month spending velocity catches overspending early

## AI Insights

- **~$0.50/mo** for 3 weekly AI-generated insights
- Spending diary surfaces patterns in recent transactions
- Habits review cross-references health and spending data
- Smart money tips suggest actionable optimizations

## What Broke

| Issue | Impact | Resolution |
|-------|--------|------------|
| Cash runway cron | Schema mismatch with Supabase table | Disabled — needs schema migration |
| Health webhook downtime | Gaps in data collection | Added systemd service with auto-restart |
| CSV import lag | Stale financial data | Sunday reminder cron to export CSVs |
