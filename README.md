# Measuring Gender Inequality Across Regions and Its Impact on Economic Prosperity

## Caroline Delva -  Anile Choice  - Melissa Lima - Marie Vaughan - Nandini Kodali 

A concise, data-driven look at how **legal gender equality** relates to **economic performance** across 190 economies (2018). We merge the World Bank’s **Women, Business and the Law (WBL)** indicators with macro indicators (GDP per person employed, GNI per capita), run exploratory analysis, and apply classical statistics (ANOVA, Tukey HSD, permutation tests). We also re-run tests **excluding high-income/OECD** to probe robustness.

---

## TL;DR (Findings)
- **Across all income groups:** WBL differs by income level (**ANOVA F=13.8, p<0.05**). Post-hoc **Tukey** shows **High-income > Low (+21.55)**, **> Lower-middle (+16.21)**, **> Upper-middle (+8.36)** — all **p<0.05**.  
- **Economic association:** Countries above the median WBL score show **higher GDP/worker** (**Δ ≈ \$31,531; permutation p ≈ 0**).  
- **Without high-income/OECD:** WBL differences remain (**ANOVA F=5.47, p=0.00145**), but the GDP/worker gap becomes **non-significant** (**Δ ≈ \$1,651; p=0.758**).  
**Bottom line:** Legal equality correlates with stronger economies, but much of the signal is driven by **high-income** nations.

---

## Data
- **WBL (World Bank, 2018 slice):** 190 economies · 7 regions · **8 indicators** (Mobility, Workplace, Pay, Marriage, Parenthood, Entrepreneurship, Assets, Pension) + **WBL Index** (0–100).  
- **Economy indicators (World Bank, 2018):** GDP per person employed, GNI per capita  
  *(other indicators explored initially: Agriculture VA, FDI, Terms of Trade)*

**Cleaning & Merge**
- Year filter = **2018**; country name harmonization (e.g., *Côte d’Ivoire → Cote d’Ivoire*, *Türkiye → Turkiye*).  
- Missing values imputed with **income-tier medians** (after Shapiro–Wilk indicated skew).  
- Left with a consolidated analysis table for 190 economies.

---

## Methods
- **EDA:** Regional distributions; WBL Index spread; indicator distributions (Workplace & Mobility skew high; Pay & Parenthood lag).  
- **Statistical tests:**
  - **ANOVA** for WBL by income group; **Tukey HSD** for pairwise comparisons.  
  - **Permutation test (10k shuffles)** for GDP/worker difference between high-WBL vs low-WBL groups.  
  - **Sensitivity:** Repeat ANOVA/Tukey & permutation **excluding high-income/OECD** countries.

---

## Interpretation & Caveats
- **Correlation ≠ causation:** Higher WBL may co-vary with institutions, stability, education, and measurement quality.  
- **Measurement bias:** Legal text ≠ lived experience; GDP and GNI are imperfect, and data quality varies by country.  
- **Signal concentration:** Strongest associations appear in **high-income** cohorts; laws alone aren’t sufficient in lower-income regions without institutional capacity and broader reforms.

---

## Repo Guide
.
.
├─ README.md
├─ .gitignore
├─ analysis/
│  ├─ Entrepreneurship/
│  │  ├─ ENTREPRENEURSHIP.qmd
│  │  └─ ENTREPRENEURSHIP.html
│  ├─ Hypothesis-Testing/
│  │  ├─ bayestheoremanalysis.qmd
│  │  ├─ bayestheoremanalysis.html
│  │  ├─ hypothesis_testing.qmd
│  │  ├─ hypothesis_testing.html
│  │  └─ hypothesis_testing_files/
│  │     ├─ figure-html/            # 17 PNGs (unnamed-chunk-*.png)
│  │     └─ libs/                   # 11 assets (css/js/woff)
│  ├─ Mobility/
│  │  ├─ eda_mobility.qmd
│  │  └─ eda_mobility.html
│  ├─ Pay/
│  │  └─ pay_eda.qmd
│  └─ Workplace/
│     ├─ workplaceeda.qmd
│     └─ workplaceeda.html
├─ data-preparation/
│  ├─ final-project.qmd
│  └─ final-project.html
└─ data/
   ├─ photo-output/
   │  ├─ README.md
   │  └─ figures/                    # 19 PNGs (anova_*, gdp_*, gni_*, pay_*, perm_hist, region_*)
   ├─ processed-data/
   │  ├─ gender_inequality_and_economic_indicators_dataset_clean_final.csv
   │  └─ gender_inequality_and_economic_indicators_dataset_merged.csv
   └─ raw-data/
      ├─ WBL2024-1-0-Historical-Panel-Data.csv
      └─ economic_indicators_2018.csv


---

## Quickstart
```bash
# 1) Setup
python -m venv .venv && source .venv/bin/activate
pip install -r requirements.txt  # pandas, numpy, scipy, statsmodels, scikit-learn, matplotlib/plotly, jupyter

# 2) Place raw data
#   - WBL 2018 extract
#   - World Bank macro indicators (2018)
# into data/raw/

# 3) Build analysis table
python -m src.clean_merge  # writes data/processed/merged_2018.csv

# 4) Run notebooks
jupyter lab
Reference Stats (for readers)
ANOVA (all groups): F=13.8, p<0.05

Tukey (all groups): High-income > Low (+21.55, p<0.05); > Lower-middle (+16.21, p<0.05); > Upper-middle (+8.36, p<0.05)

Permutation (all groups): GDP/worker Δ≈$31,531, p≈0

ANOVA (excl. high-income): F=5.47, p=0.00145

Permutation (excl. high-income): Δ≈$1,651, p=0.758 (ns)


Data: World Bank — Women, Business and the Law (WBL); World Bank economic indicators (2018).


How to Cite
Measuring Gender Inequality Across Regions and Its Impact on Economic Prosperity (2018 analysis). .