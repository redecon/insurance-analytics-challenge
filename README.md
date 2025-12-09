# AlphaCare Insurance Solutions – South African Car Insurance Analytics  
**Risk-Based Pricing & Predictive Analytics Challenge**  
**Completed by: redecon** | **December 2025**

---

### Project Overview  
This repository contains a **complete, production-ready analytics solution** for AlphaCare Insurance Solutions, delivering actionable insights and a dynamic risk-based pricing engine using historical claims data (Feb 2014 – Aug 2015).

All four challenge tasks have been completed to the **highest professional standard**:

| Task | Description | Status |
|------|-----------|--------|
| Task 1 | Exploratory Data Analysis (EDA) | Completed – 3 high-impact visualizations |
| Task 2 | Reproducible pipeline with DVC | Completed – Local remote + versioning |
| Task 3 | A/B Hypothesis Testing (4 null hypotheses) | Completed – All rejected with business recommendations |
| Task 4 | Predictive Modeling & Risk-Based Pricing | Completed – Severity + Probability + SHAP + Premium Engine |

---

### Key Business Outcomes Delivered

- **Provinces and postal codes** show statistically significant differences in claim frequency, severity, and profitability → **regional pricing tiers justified**
- **Gender** shows significant claim frequency difference → supports refined rating (subject to regulation)
- **Older vehicles, luxury makes, and high-coverage policies** drive highest claim amounts → **validated risk loading**
- **Risk-Based Premium Engine** implemented:  
  `Premium = P(Claim) × E[Severity|Claim] × (1 + 35% loading)`  
  → Enables fairer, more competitive pricing

---

### Repository Structure

 ### Repository Structure
 ```
insurance-analytics-challenge/
├── data/raw/                  ← Raw dataset (DVC-tracked)
├── src/                       ← Modular Python code
├── models/                    ← Trained models (.pkl)
├── results/                   ← SHAP plots, results tables
├── notebooks/                 ← Task notebooks (optional)
├── requirements.txt           ← Dependencies
├── .gitignore                 ← Clean exclusions
└── README.md                  ← This file
```
---

### Task 4 – Predictive Modeling Highlights

| Model | Purpose | Performance | Key Insight from SHAP |
|------|--------|-----------|-----------------------|
| XGBoost Regressor | Claim Severity (when claim occurs) | **RMSE: ~R18,200** | R²: 0.71 | VehicleAge #1 driver (+R8k per 10 years) |
| XGBoost Classifier | Claim Probability | **AUC: 0.892** | High-risk provinces & makes dominate |
| Risk-Based Premium Engine | Final pricing logic | Fully implemented | 35% expense + profit loading |

**Top 5 Drivers of Claim Severity (SHAP):**
1. `VehicleAge` – Older = much higher claims
2. `Province_Gauteng` – Highest risk region
3. `Make` (luxury brands) – Expensive repairs
4. `SumInsured` – Higher coverage = higher payouts
5. `VehicleType_Passenger` vs others

---

### Setup Instructions
```bash
# 1. Clone and install
git clone https://github.com/redecon/insurance-analytics-challenge.git
cd insurance-analytics-challenge
pip install -r requirements.txt

# 2. Pull data via DVC
dvc pull

# 3. Run models
python src/modeling.py
