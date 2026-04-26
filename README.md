# streaming-economics-infrastructure-trade-offs

The work here is not academic. Every framework was built under real P&L constraints, with actual budget decisions depending on the output.

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

Marketing budget allocated by volume targets, not marginal returns — plans with LTV/CAC below 4x were receiving spend while 
high-return plans were underfunded Infrastructure cost per user (~R$7–10/month) was invisible to marketing decisions, 
distorting true ROAS High churn (9–12%) made acquisition scaling economically fragile without retention improvements

Platform characteristics:

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

💰 Cost Structure 
(Estimated and discreted by cost types)

💰 Revenue Structure 
(Estimated and discreted by revenue flows: suscriptions, rentals, movie purchases)

📊 Unit Economics

+ Cost per User: ~R$ 7–10 per user/month (infra only)

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
