# OpenClaw Ops — AI Agent Business Platform

A production AI agent system that runs [Zealynx Security](https://zealynx.io)'s operations autonomously. Built in 40 days using [OpenClaw](https://openclaw.dev) + Claude Code.

One founder. Six agents. Seven interconnected systems. Running 24/7 on a single VPS.

---

## Architecture

```
┌─────────────────────────────────────────────────────────────────────────┐
│  TIER 1 — ELLIOT (OpenClaw Gateway)                                     │
│  Autonomous orchestration · 24/7 on VPS · Sonnet 4.6 + Haiku 4.5       │
│                                                                         │
│  Business Agents: Michelle · MrBeast · Elon                             │
│  Personal Agents: Trinity · Dobby                                       │
│                                                                         │
│  40+ cron jobs · Telegram routing · Multi-account X automation          │
├─────────────────────────────────────────────────────────────────────────┤
│  TIER 2 — CLAUDE CODE (Interactive)                                     │
│  Strategy · Research · Content generation · Infrastructure              │
│  Opus 4.6 (Max plan, zero API cost) · Full SSH to VPS                   │
├─────────────────────────────────────────────────────────────────────────┤
│  TIER 3 — MCP SERVER (Tool Bridge)                                      │
│  15 tools via Cloudflare tunnel                                         │
│  Vault · Sessions · Config · Health · Bootstrap                         │
├─────────────────────────────────────────────────────────────────────────┤
│  DATA LAYER                                                             │
│  Supabase (realtime) · Vault (32+ files) · Session transcripts          │
└─────────────────────────────────────────────────────────────────────────┘
```

### How the Tiers Work Together

- **Tier 1** handles everything that should happen without human intervention — scheduled content, lead scanning, follow-ups, health alerts, system monitoring
- **Tier 2** handles work that needs human judgment — strategy, deep research, content approval, architecture decisions
- **Tier 3** bridges them — Claude Code can read Elliot's vault, check system health, and query session history through MCP tools

### Agent Roster

Each agent has its own directory with detailed documentation — role, crons, and outcomes.

**Business Agents**:

| Agent | Role | Channel | Docs |
|-------|------|---------|------|
| **[Elliot](agents/elliot/)** | System orchestrator, main agent | Telegram (system alerts) | [role](agents/elliot/README.md) · [crons](agents/elliot/crons.md) · [outcomes](agents/elliot/outcomes.md) |
| **[Michelle](agents/michelle/)** | BD/outreach/sales | Telegram (sales messages) | [role](agents/michelle/README.md) · [crons](agents/michelle/crons.md) · [outcomes](agents/michelle/outcomes.md) |
| **[MrBeast](agents/mrbeast/)** | X growth automation | Telegram (content alerts) | [role](agents/mrbeast/README.md) · [crons](agents/mrbeast/crons.md) · [outcomes](agents/mrbeast/outcomes.md) |
| **[Elon](agents/elon/)** | X engagement + reactive scanning | Internal | [role](agents/elon/README.md) · [crons](agents/elon/crons.md) · [outcomes](agents/elon/outcomes.md) |

**Personal Agents**:

| Agent | Role | Channel | Docs |
|-------|------|---------|------|
| **[Trinity](agents/trinity/)** | Opportunity detection + education | Telegram (signals, lessons) | [role](agents/trinity/README.md) · [crons](agents/trinity/crons.md) · [outcomes](agents/trinity/outcomes.md) |
| **[Dobby](agents/dobby/)** | Health + finance tracking | Telegram (health, finance) | [role](agents/dobby/README.md) · [crons](agents/dobby/crons.md) · [outcomes](agents/dobby/outcomes.md) |

---

## The Seven Systems

### 1. X Growth Engine (3 Accounts, 33+ Crons)

Fully automated content publishing, engagement, and audience growth across three X accounts — each with distinct voice, audience, and strategy.

```
┌──────────────────┐  ┌──────────────────┐  ┌──────────────────┐
│  @ElliotAgentRepo │  │ @TheBlockChainer  │  │ @ZealynxSecurity  │
│  AI Agent Voice   │  │ Founder Voice     │  │ Company Voice     │
│                   │  │                   │  │                   │
│  2 threads/day    │  │ 1 post/day        │  │ 1 post/day        │
│  9 replies        │  │ 6 replies         │  │ 9 replies         │
│  9 quotes         │  │ 4 quotes          │  │ 4 quotes          │
│  25 follows       │  │ 10 follows        │  │ 10 follows        │
│  Reactive scanner │  │ Reactive scanner  │  │ Reactive scanner  │
└──────────────────┘  └──────────────────┘  └──────────────────┘
```

**Per account**: 11 cron jobs + 1 weekly reminder = 33 total across accounts

**Pipeline**:
1. Weekly content generation (Claude Code, Opus) → 14 threads per account
2. Batch loader pushes to `batch-queue.json`
3. `batch-publish.py` fires every 15 minutes, publishes next scheduled post
4. Engagement engines run 2-4x/day: replies, quotes, follows
5. Reactive scanner checks 4x/day for real-time engagement opportunities
6. Weekly analytics digest every Monday

**Build-in-Public** (founder account): 3 threads/week documenting this system — architecture, costs, results, failures. Rotating content pillars.

**Models**: Opus 4.6 for engagement engines (~$6/mo across accounts), Haiku 4.5 for reactive scanning (~$0.50/mo)

**What broke**: Reply engines disabled across all accounts — X Free tier returns 403. Shared consumer key blocks cross-account interaction. Scripts return exit code 0 on API errors (had to add stdout checking for `"❌"`).

---

### 2. BD Engine (Lead-to-Deal Pipeline)

End-to-end business development automation with human approval gates at every customer-facing step.

```
Lead Sources                    CRM (Supabase)              Outreach
┌─────────────┐                ┌──────────────┐            ┌──────────────┐
│ DeFiLlama   │───┐            │              │            │              │
│ CryptoRank  │───┤  Scanners  │  9-stage     │  Drafts    │  Telegram    │
│ ChainPlay   │───┼──────────► │  pipeline    │──────────► │  (approval)  │
│ RootData    │───┤            │              │            │              │
│ GitHub Scout│───┘            │  Weighted    │  Approved  │  Email /     │
│             │                │  scoring     │──────────► │  LinkedIn /  │
│ Apollo      │◄── Enrichment  │              │            │  Twitter     │
└─────────────┘                └──────────────┘            └──────────────┘
```

**Deal stages**: discovered → researched → contacted → engaged → proposal → negotiation → won → signed → lost

**Automation**:
- 5 lead source scanners (weekly, different data sources)
- Apollo enrichment (email, LinkedIn, company data)
- AI-drafted follow-ups for overdue deals (2x/day)
- Approved messages auto-sent every 30 minutes
- Weekly analytics digest with funnel metrics
- Past client monitoring (GitHub activity, TVL changes)

**Safety rules** (non-negotiable):
- Max 3 unanswered outbound → stop + flag
- Reply detected → pause auto-follow-ups
- First contact → always manual approval
- ALL messages require human approval before sending

**Dashboard**: Real-time Kanban view, message approval queue, funnel analytics — all at `studio.zealynx.io`

---

### 3. GitHub Scout (Automated Lead Discovery)

Finds unaudited Solidity projects, qualifies them, and feeds the BD pipeline.

```
08:00 UTC          08:30 UTC           Manual
┌──────────┐      ┌──────────┐       ┌──────────┐
│  Scout   │      │ Qualify  │       │  Krait   │
│          │      │          │       │  Scan    │
│ Find new │─────►│ Research │──────►│          │
│ Solidity │      │ score +  │       │ Extract  │
│ repos    │      │ classify │       │ findings │
└──────────┘      └──────────┘       └──────────┘
```

**Scoring formula** (max 28 points):
- No prior audit (+5), contract count (+4), active development (+3)
- High-value protocol type (+3), wants audit signals (+3)
- Organization (+2), website (+2), complexity (+2), socials (+2)
- Deployed (+1), pre-launch (+1), GitHub stars (+1)

**Hard gates**: Must have `.sol` files, no existing audit, no Rust/Cairo/Move only

**Blocklist**: ~70 organizations (L1/L2 chains, major protocols, competitors, infrastructure)

**Scan cache**: 30-day expiry prevents re-evaluating the same repo

---

### 4. ETHCC Campaign Engine (Event-Driven Outreach)

Full-stack referral campaign for ETHCC Cannes (March 27 - April 5, 2026). Two segments: audit prospects and referral connectors.

```
Data Ingestion          Classification         Multi-Channel Outreach
┌──────────────┐       ┌──────────────┐       ┌──────────────┐
│ Luma scrape  │       │              │       │ Email        │
│ EthCC speakers│──────►│ 3 rules:     │──────►│ LinkedIn     │
│ ETHGlobal    │       │ exclude /    │       │ Twitter      │
│              │       │ lead /       │       │ Telegram     │
│ Apollo       │◄──────│ connector    │       │              │
│ enrichment   │       │              │       │ All require  │
│ (100/day)    │       └──────────────┘       │ approval     │
└──────────────┘                              └──────────────┘
```

**9 VPS scripts**: event monitor (6h), attendee intel (2x/week), speaker scrape, classification, Apollo enrichment (daily), outreach drafter (2x/day, 20/run), X monitor (4x/day), ConvertKit enrollment, analytics

**Referral program**: $1k base + 20% commission per closed audit (min $5k audit value, $50k aggregate cap)

**Landing pages** (all deployed): `/ethcc-referral`, `/ethcc-referral/toolkit`, `/referred`, `/terms`, `/privacy`

---

### 5. Trinity (Signal Detection + Personal Education)

Two-part system: opportunity detection and structured daily learning.

**Opportunity Detection**:
```
Signals (RSS, Reddit, GitHub, CoinGecko)
         │
         ▼
┌─────────────────────────────┐
│  Stage 1: Scan (Sonnet)     │
│  2x/day → extract signals   │
├─────────────────────────────┤
│  Stage 2: Score (Sonnet)    │
│  5 virtual advisors score   │
│  Demand/Edge/Ship/Auto      │
│  ≥16/20 → send to Telegram  │
└─────────────────────────────┘
```

**Advisory board** (5 AI personas): each scores opportunities from a different lens — demand, unit economics, leverage, ship speed, long-term value.

**Education** (4 lessons/day):
- Finance (investing, tax, portfolio) — morning + evening
- eMBA (8 modules, 112 topics) — morning + evening

**Weekly review**: Monday deep analysis with Opus — cross-reference signals, update world model, log or kill ideas.

---

### 6. Dobby (Personal Assistant)

Health + finance tracking with 13 automated crons.

**Health pipeline**:
```
Apple Health → iOS Export App → Webhook → Supabase (43K+ rows)
                                              │
                                    ┌─────────┼──────────┐
                                    ▼         ▼          ▼
                              Sleep alerts  Workout   Weekly
                              (daily 7:30)  nudges    health brief
                                            (daily)   (Monday)
```

**Finance pipeline**:
- Bank CSV imports → Supabase (2K+ transactions)
- Automated: spending alerts, bill reminders, tax reserve calculations, net worth snapshots
- AI insights (Haiku, ~$0.50/mo): spending diary, habit analysis, smart money tips

---

### 7. Krait (AI Security Tooling)

AI-powered smart contract auditor — the product Zealynx is building on top of the agent infrastructure.

**CLI Agent**: 4-phase adversarial pipeline (Recon → Detection → State Analysis → Verification). Blind-tested against 40 Code4rena contests. 90% precision at v6.4 with 0.2 false positives per contest.

**Web Platform** ([krait.zealynx.io](https://krait.zealynx.io)): Protocol-specific security assessment — 39 DeFi verticals, 845+ security checks, auto-generated architectural observations.

**Kill Gates**: 8 automatic filters that try to disprove every finding before it reaches the report. Never killed a true positive across 40 contests.

Full details: [github.com/ZealynxSecurity/krait](https://github.com/ZealynxSecurity/krait)

---

## Operations Dashboard

Custom real-time dashboard at `studio.zealynx.io` — React 19 + Vite + Tailwind + Supabase realtime.

```
┌─────────────────────────────────────────────────────┐
│  Zealynx OS Dashboard                               │
├──────────┬──────────────────────────────────────────┤
│          │                                           │
│  Home    │  System health, cron stats, errors        │
│  Ops     │  Agent status, sessions, cron logs        │
│  X       │  3-account engagement metrics             │
│  BD      │  Kanban pipeline, message queue, funnel   │
│  Content │  Build-in-public, course system           │
│  Trinity │  Signals, education progress              │
│  Settings│  Config, maintenance                      │
│          │                                           │
└──────────┴──────────────────────────────────────────┘
```

68 components, 7 sidebar categories, 20+ tabs. Auto-deploys on push to main.

---

## Infrastructure

| Component | Spec |
|-----------|------|
| VPS | Ubuntu 24, Hetzner, 7.6GB RAM |
| AI Models | Sonnet 4.6 (agents), Haiku 4.5 (routine), Opus 4.6 (interactive) |
| Database | Supabase (realtime subscriptions) |
| MCP | 15 tools via Cloudflare tunnel |
| Dashboard | React 19 + Vite + Vercel |
| Bots | Telegram (4 bots, channel-based routing) |
| X API | Free tier (3 accounts, shared consumer key) |
| Enrichment | Apollo (Basic plan, 2500 credits/mo) |

**Monthly AI cost**: ~$8-12 (Sonnet for agents + Haiku for routine tasks). Interactive work on Claude Code Max plan = $0 additional.

---

## What Broke (And What I Learned)

| System | What Happened | Fix / Lesson |
|--------|--------------|--------------|
| X reply engines | Free tier returns 403 on replies | Disabled — pivoted to quotes + reactive scanning |
| Bootstrap bloat | 48K char context file, truncated to 20K | Restructured into vault files + reference docs |
| BD scanners | 5 different data sources, 5 different failure modes | Built individual error handling, scan cache with expiry |
| Apollo enrichment | Bad data (12 of 32 contacts had wrong emails) | Added validation pass, cleaned pipeline |
| Auth system | Two config locations override each other silently | Documented both, always check both on debugging |
| Vault auto-loader | Intermittent MODULE_NOT_FOUND | Open issue — module resolution in OpenClaw gateway |
| Billing errors | OpenClaw silently disables agents on billing issues | Manual clear required — added to debugging playbook |
| X API error codes | Scripts exit 0 even on HTTP 403 | Check stdout for error markers, not just exit codes |
| Cross-account X | Shared consumer key blocks interactions between own accounts | Architecture limitation — no fix on Free tier |
| Session bloat | Largest transcript hit 1.5M characters | Periodic cleanup needed, added to maintenance routine |

---

## Numbers (40 Days In)

- **6** autonomous agents running 24/7 (4 business + 2 personal)
- **40+** cron jobs across all systems
- **3** X accounts with automated content + engagement
- **7** interconnected systems (X, BD, Scout, ETHCC, Trinity, Dobby, Krait)
- **15** MCP tools bridging interactive and autonomous tiers
- **68** dashboard components across 20+ tabs
- **43K+** health data rows tracked
- **2K+** financial transactions categorized
- **~$8-12/mo** total AI agent cost (excluding interactive work)

---

## Tech Stack

| Layer | Technology |
|-------|-----------|
| Agent Framework | [OpenClaw](https://openclaw.dev) |
| Interactive AI | [Claude Code](https://docs.anthropic.com/en/docs/claude-code) (Opus 4.6) |
| AI Models | Claude Sonnet 4.6, Haiku 4.5, Opus 4.6 |
| Database | Supabase (PostgreSQL + realtime) |
| Dashboard | React 19 + Vite 7 + Tailwind 3 + Recharts |
| Hosting | Hetzner VPS (Ubuntu 24) + Vercel (dashboard) |
| Tunneling | Cloudflare (MCP server) |
| Messaging | Telegram Bot API (4 bots) |
| Social | X API v2 (Free tier) |
| Lead Enrichment | Apollo.io API |
| Email Sequences | ConvertKit |
| Scripts | Python (X engines) + Node.js (BD, Scout, Trinity, Dobby) |

---

## Author

**Carlos Vendrell** — Founder, [Zealynx Security](https://zealynx.io)

Smart contract auditor. Security researcher contractor at Pashov Audit Group, Cyfrin, Sherlock, and Immunefi. 35+ protocols audited across EVM and Solana. Building AI-powered security tooling and autonomous business systems.

[Twitter/X](https://x.com/TheBlockChainer) · [GitHub](https://github.com/vendrell46) · [Zealynx](https://zealynx.io)
