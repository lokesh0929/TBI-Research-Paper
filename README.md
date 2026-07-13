# TBI Causal Effect Analysis

This repository contains an analysis of the **causal effect of surgical interventions (Craniotomy/Craniectomy)** on cognitive and functional outcomes at discharge in patients with Traumatic Brain Injury (TBI), based on the TBIMS dataset.

**Dataset Source:** [TBIMS National Data and Statistical Center](https://www.tbindsc.org/)

---

## 📄 Publication

This work was published in **Frontiers in Neurology** (November 13, 2025):

> Irankhah E, Pagare M, Chetla L, Shen J, Ul Alam MA and Wolkowicz KL (2025). *Machine learning-enhanced causal inference of surgical decisions and rehabilitation strategies in traumatic brain injury.* Front. Neurol. 16:1685335.

- **Full article:** [Frontiers in Neurology](https://www.frontiersin.org/journals/neurology/articles/10.3389/fneur.2025.1685335/full)
- **PubMed:** [PMID 41323220](https://pubmed.ncbi.nlm.nih.gov/41323220/)
- **DOI:** [10.3389/fneur.2025.1685335](https://doi.org/10.3389/fneur.2025.1685335)

We evaluate the **Average Treatment Effect (ATE)** and **Average Treatment Effect on the Treated (ATT)** using stratified estimation. We also compute **Propensity Score Matching (PSM)** effects for robustness and perform Welch’s t-tests for statistical significance.

---

## 📊 Analysis Summary

| Outcome        | ATE Estimate | ATT Estimate | T-Test (p-value) | ATT via PSM |
|----------------|--------------|--------------|------------------|-------------|
| FIMCompD       | -1.27        | -2.49        | 0.2522           | -0.95       |
| FIMMemD        | -1.14        | -2.12        | 0.4637           | -0.85       |
| FIMProbSlvD    | -1.21        | -2.41        | 0.3727           | -0.91       |
| FIMExpressD    | -1.39        | -2.49        | 0.3008           | -1.10       |
| FIMSocialD     | -1.11        | -2.26        | 0.2866           | -0.79       |

> **Note:** All estimates indicate negative effects, suggesting that surgery is associated with *lower* discharge scores. While directionally consistent across methods, no t-tests reached statistical significance (p > 0.05).

---

## 📁 Contents

- `Final_Analysis.ipynb`: Full analysis notebook with preprocessing, group stratification, ATE, ATT, PSM, and validation tests.
- `severity_control_processed.csv`: Cleaned dataset used for all computations.
- `preprocess_data`: The script for getting severity_control_processed.csv

---

## 📚 Methods

- **Confounders:** Stratification and matching based on `SexF`, `SCI`, and `CC_Hypertension`
- **ATE:** Computed for all patients using stratified group mean differences.
- **ATT:** Estimated for severe TBI group (GCS ≤ 8), representing actual treatment group.
- **PSM:** Logistic regression-based propensity scores; 1:1 nearest neighbor matching without replacement.
- **Validation:** Welch’s t-test for treated vs. control groups within valid strata.

---

## 📌 Requirements

- Python ≥ 3.8
- pandas
- numpy
- matplotlib
- seaborn
- scipy
- scikit-learn

Install dependencies using:

```bash
pip install -r requirements.txt
```

---

## 👥 Authors

- **Lokesh Chetla** — [@lokesh0929](https://github.com/lokesh0929)
- **Elyas Irankhah** — [@Elyasirankhah](https://github.com/Elyasirankhah)


