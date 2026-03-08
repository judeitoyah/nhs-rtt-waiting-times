# nhs-rtt-waiting-times
NHS RTT Waiting Times Analysis – December 2025 | Provider, Specialty &amp; Long-Waiter Insights
# NHS RTT Waiting Times – December 2025 Analysis

This project analyses NHS Referral to Treatment (RTT) waiting times for December 2025, focusing on provider‑level and specialty‑level performance, long‑waiter backlogs, and 18‑week RTT standards. The notebook follows a clear, stepwise analytical workflow aligned with NHS reporting practice and is designed to be readable for both technical and non‑technical audiences.

---

## Objectives

- Understand RTT 18‑week performance across providers
- Identify highest‑ and lowest‑performing organisations
- Analyse RTT performance by treatment function (specialty)
- Quantify long waits (18+, 52+, and 78+ weeks where available)
- Summarise system‑wide pressures in a clear, decision‑ready narrative

---

## Data

- **Source:** NHS RTT waiting times extract (December 2025)
- **Level:** Provider × Treatment Function × RTT Part Type
- **Key fields used:**
  - Reporting period (`Period`, cleaned to `Period_clean`)
  - Provider and commissioner identifiers
  - Treatment Function Code and Name
  - Week‑band waiting time fields (e.g. `Gt 00 To 01 Weeks SUM 1`, …, `Gt 104 Weeks SUM 1`)
  - Derived fields: `Total`, `Over_18_Weeks`, `Over_52_Weeks`, `RTT_18_Week_Performance`

---

## Workflow Overview

1. **Data loading & structure checks**
   - Load raw CSV
   - Inspect columns, dtypes, and missing values
   - Generate full descriptive statistics

2. **Data cleaning & preparation**
   - Clean and convert `Period` → `Period_clean` (datetime)
   - Rebuild `Total` from week‑band columns
   - Derive `Over_18_Weeks` and `Over_52_Weeks`
   - Create an essential analysis dataset (`df_essential`)

3. **RTT 18‑week performance calculation**
   - Compute:
     \[
     RTT\_18\_Week\_Performance = \left(1 - \frac{Over\_18\_Weeks}{Total}\right) \times 100
     \]
   - Summarise performance by month

4. **Provider‑level analysis**
   - Rank providers by RTT 18‑week performance
   - Identify highest‑ and lowest‑performing providers
   - Visualise:
     - Top 10 providers
     - Bottom 10 providers
     - Distribution of performance across all providers (boxplot)

5. **Specialty‑level analysis**
   - Calculate average RTT performance by Treatment Function Name
   - Highlight highest‑ and lowest‑performing specialties
   - Interpret patterns (medical vs surgical specialties)

6. **Long‑waiter summary**
   - Summarise total patients waiting:
     - Over 18 weeks
     - Over 52 weeks
     - Over 78 weeks (if present)
   - Relate long waits back to provider and specialty patterns

7. **Final insight summary**
   - Overall RTT position
   - Provider‑level insights
   - Specialty‑level insights
   - Long‑waiter summary
   - System‑level interpretation

---

## Key Findings

- **Overall RTT position:**  
  Median RTT 18‑week performance sits in the mid‑70% range, with most providers between 60% and 90%, but a long tail of underperforming organisations.

- **Provider‑level variation:**  
  Some providers achieve **100%** RTT performance, while others fall below **25%**, with one provider at **0%**, indicating severe long‑wait pressures.

- **Specialty‑level patterns:**  
  Medical and community‑based specialties (e.g. Elderly Medicine, General Internal Medicine, Ophthalmology) perform strongly, while high‑demand surgical specialties (e.g. General Surgery, Urology, ENT, Trauma & Orthopaedics) show much lower performance.

- **Long waits:**  
  - Over **7.7 million** patients are waiting more than 18 weeks.  
  - Over **570,000** patients are waiting more than 52 weeks.  
  - No 78‑week waits are recorded in this extract.

- **System‑level insight:**  
  RTT pressures are concentrated in high‑demand surgical specialties and a subset of providers with significant operational challenges.

---

## Tools & Technologies

- **Language:** Python  
- **Libraries:** `pandas`, `numpy`, `matplotlib`, `seaborn`  
- **Environment:** Jupyter Notebook

---

## How to Use This Repository

- Open the main notebook (e.g. `01_exploration.ipynb`).
- Run cells in order:
  - Data loading
  - Cleaning and preparation
  - RTT performance calculation
  - Provider‑level analysis
  - Specialty‑level analysis
  - Long‑waiter summary
  - Final insight summary
- Use the visualisations and narrative commentary as a template for RTT performance reporting.

---

## Possible Extensions

- Add time‑series analysis across multiple months
- Incorporate 78‑week waits where available
- Build interactive dashboards (e.g. Power BI, Plotly, Streamlit)
- Segment performance by region, provider type, or specialty groupings

---

## Author

**Jude Isememe Itoyah**  
Data Analyst & BI Professional skilled in Python, SQL, Tableau, data modelling, and insight generation across diverse industries.
