# streaming-economics-infrastructure-trade-offs

The work here is not academic. Every framework was built under real P&L constraints, with actual budget decisions depending on the output.
Headline result: Portfolio ROAS improved from 5.4x → 8.5x with 8% lower spend by reallocating budget from low-return plans (LTV/CAC < 4x) to high-return plans (LTV/CAC up to 17x).

🎯 Objective

Understand how infrastructure cost + churn + pricing define a Video Streaming Platform business viability.

🧠 Context

A Video Streaming LTV CAC ROAS budget-allocation churn unit-economics infra-costs framework.

Business context: Video+, a Brazilian SVOD/TVOD platform (~900K MAUs, R$193M annual revenue, 50K VOD catalog, 120+ live channels). 
The platform operated 4 subscription plans with vastly different unit economics — but marketing and infrastructure decisions were being made in isolation, 
without a shared model of business viability.

Core insight: Growth is constrained not only by marketing efficiency, but by infrastructure economics. CDN delivery alone represented the largest cost 
driver (R$25M–60M/year), making every acquisition decision implicitly an infrastructure decision.

Problems addressed:

1. Marketing budget allocated by volume targets, not marginal returns — plans with LTV/CAC below 4x were receiving spend while high-return plans were underfunded
2. Infrastructure cost per user (~R$7–10/month) was invisible to marketing decisions, distorting true ROAS
3. High churn (9–12%) made acquisition scaling economically fragile without retention improvements

Platform characteristics:

```
| Metric | Value | Notes |
|---|---|---|
| Monthly Active Users | ~900K | |
| Playbacks / month | 12M | VOD + Live combined |
| VOD Catalog | 50K titles | SVOD subscription plans |
| Live Channels | 150+ | LIVE subscription plans |
| Video Quality | HD 720p / SD 480p | No 4K |
| Subscription Plans | ~4 core plans | Família, Premiere, HBO, Telecine |
| Monthly Churn | 9–12% | High — key viability constraint |
| Delivery Infrastructure | CDN-based | Largest single cost driver |
| Estimated CDN Cost | R$25M–60M/year | ~46–56% of total cost base |
| Total Estimated Costs | R$54.5M–108M/year | Infra + Engineering + Content + Marketing |
```

💰 Cost Structure (Estimated)

```
| # | Domain | Description | FTEs | Monthly Cost | Annual Cost (est.) |
|---|---|---|---|---|---|
| 1 | Engineering | Backend + BFF + Frontend squads | 35 | R$1.4M | R$12M–20M |
| 2 | Cloud & Backend Infra | APIs, ingestion, storage | 3 | R$750K | R$8M–18M |
| 3 | CDN | Video delivery — HD/SD streaming | 3 | R$2.5M | **R$25M–60M** |
| 4 | Data & Analytics | Pipelines, tracking, BI | 2 | R$167K | R$5M–12M |
| 5 | Product | App (TV, mobile, web), UX/UI, features | 6 | R$350K | R$4M–6M |
| 6 | Marketing & Growth | Paid media, acquisition, CRM, retargeting | 6 | R$2.0M | R$20M–28M |
| 7 | Content | Licensing (Telecine, Premiere+), catalog strategy | 8 | R$4.0M | R$40M–60M |
| 8 | Admin | HR, IT, FinOps | 8 | R$400K | R$4M–6M |
| | **Total** | | **71** | **~R$11.6M** | **R$54.5M–108M** |
```

💰 Revenue Structure 

```
| # | Stream | Plan / Type | Active Subscribers | Price (R$/mo) | Monthly Revenue |
|---|---|---|---|---|---|
| 1.1 | Subscription | Plano Família | ~122,800 | R$121 | R$14.9M |
| 1.2 | Subscription | Plano Premiere | ~5,800 | R$90 | R$520K |
| 1.3 | Subscription | Plano Telecine | ~4,300 | R$40 | R$173K |
| 1.4 | Subscription | Plano HBO | ~11,600 | R$40 | R$462K |
| 2 | Rentals | Individual title rentals | ~3,500 | R$8 avg | R$29K |
| 3 | Purchases | Movie purchases (TVOD) | ~500 | R$26 avg | R$13K |
| | **Total** | | **~148,500** | | **~R$16.1M/mo (R$193M/yr)** |
```

📊 Unit Economics

```
| Metric | Value | Notes |
|---|---|---|
| Cost per user / month (infra only) | R$7–10 | CDN + Cloud + Engineering allocated per MAU |
| LTV range by plan | R$175 – R$1,513 | Compras/Alugueis (lowest) → Família (highest) |
| LTV/CAC range by plan × channel | 3x – 17x | HBO/Google (3x) → Família/Google (17x) |
| Payback period (Família, Meta) | ~1.4 months | At optimized CAC of R$75 |
```

Approach:
Case 1 — Unit Economics & LTV Modeling

Built LTV model per plan using churn-adjusted revenue: LTV = ARPU / churn_rate
Calculated CAC by plan × channel (Google Ads, Meta, TikTok)
Identified LTV/CAC ratios from 3x (HBO) to 17x (Família) — driving reallocation logic

Case 2 — Budget Optimization & ROAS Modeling

Modeled marginal return curves by plan × channel
Built current vs. optimized budget scenarios
Result: portfolio ROAS improved from 5.4x → 8.5x with 8% lower spend, by concentrating on Família (Meta) and Premiere (Google Ads)

Case 3 — Infrastructure Economics & Strategic Simulations

Modeled three core trade-offs:

Quality improvement (CDN/player): ↓ churn, ↑ infra cost
Acquisition scaling: ↑ revenue, ↑ infra cost
Bundle push (Família plan): ↑ LTV, ↑ content/licensing cost
Simulated: reducing churn by 2pp → +25% LTV; retention improvements outperform acquisition scaling under current cost structure

```
Files:

01-streaming-economics/
├── README.md                              # Project-level context and decisions
├── data/
│   └── streaming_economics_anonymized.xlsx  # Source data (anonymized)
├── notebooks/
│   ├── 01_ltv_churn_modeling.ipynb        # LTV by plan with confidence intervals
│   ├── 02_cac_channel_analysis.ipynb      # CAC efficiency by plan × channel
│   ├── 03_budget_optimizer.ipynb          # Marginal return curves + scenario modeling
│   ├── 04_funnel_diagnostics.ipynb        # Drop-off analysis across 6 funnel stages
│   └── 05_infra_economics_simulation.ipynb # CDN cost × churn × growth trade-offs
└── outputs/
    └── budget_recommendation.pdf          # Executive summary (decision layer)
```

🔗 How the 3 Cases Connect

Case	Focus	Role
Case 1	Core Models / Decision foundation
Case 2	Causality	Validate impact
Case 3	Economics	Ensure sustainability

🚀 Final Takeaways

Marketing Science is not just modeling → it's decision systems
Retention, acquisition, and infra are interdependent
The best insights come from connecting layers, not isolating them

Status: 🔄 In progress — converting from Excel to Python notebooks
