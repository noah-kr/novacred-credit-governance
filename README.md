# DEGO Project - Team 9

## NovaCred Credit Application Governance Analysis

### Group Project \| Group 9 \| Data Ecosystems and Governance in Organizations-2526_T3

> **About this copy:** This was a team project of four students at Nova SBE. This
> repository is a copy of the original team repository,
> [margarida-passos-cunha/dego-project-team9](https://github.com/margarida-passos-cunha/dego-project-team9),
> with the complete commit history, so every team member's commits keep their authorship.
> The dataset is a synthetic course dataset; it contains no real applicants.

### My contribution (Noah Kreyenkamp, Data Engineer)

- Set up the repository structure and project conventions.
- Wrote the data loader (`src/data_loader.py`) that flattens the nested raw JSON applications into a pandas DataFrame.
- Built the cleaning pipeline (`src/data_cleaning.py`): standardised gender encoding and date formats, handled duplicates and invalid values, and exported the cleaned dataset.
- Wrote the data quality assessment (`notebooks/01-data-quality.ipynb`) covering completeness, consistency, validity and accuracy, including the visualisations in `reports/`.

The bias and fairness analysis (Notebook 02), the privacy and GDPR assessment (Notebook 03) and the presentation were done by my teammates (see the table below).

------------------------------------------------------------------------

## Project Description

> **Repository:** DEGO 2606 Group Project - Group 9 - Credit Application Governance Analysis

## Executive Summary

This project applies data governance, fairness analysis, and privacy engineering principles to NovaCred's credit application dataset (\~500 records). The analysis is structured across three notebooks, each addressing a distinct governance dimension.

### Data Quality Findings

**Notebook 01 - Data Quality** audits the raw dataset across four quality dimensions: completeness, consistency, validity, and accuracy. Key issues identified include inconsistent gender encoding (6 distinct representations across 114 records), four conflicting date formats, duplicate application records, and duplicate SSNs across different applicants. A cleaning pipeline was developed to systematically remediate these issues, resulting in a standardized analytical dataset.

### Bias Analysis

**Notebook 02 - Bias & Fairness Analysis** evaluates disparities in loan approval outcomes across gender, age, and geography. A statistically significant gender gap was identified (Female: 50.6% vs. Male: 65.9%; DI ratio = 0.768, p = 0.0008), which persists across income brackets, suggesting the disparity is not fully explained by financial differences. Approval rates also rise systematically with age (\~40% for under-30s to \~64% for over-60s; p = 0.01), with the gender gap most pronounced among younger applicants. ZIP code approval rates vary widely but are based on small sample sizes, making structural bias inconclusive. Effect sizes remain moderate (Cramér's V ≈ 0.15 throughout), indicating that no single attribute fully explains approval outcomes.

### Privacy & Governance Assessment

**Notebook 03 - Privacy & Governance** applies three privacy-preserving techniques to the dataset: pseudonymization via salted SHA-256 hashing, k-anonymity through quasi-identifier generalization and suppression, and differential privacy via the Laplace mechanism. In addition to the technical demonstrations, the notebook evaluates the dataset against key GDPR requirements, identifying several privacy compliance gaps. The analysis additionally classifies the NovaCred credit scoring model as high-risk under EU AI Act Annex III, and highlights governance gaps, including the absence of human oversight, no documented lawful basis per data field, and no data retention schedule.

### Governance Recommendations

Nine governance recommendations are proposed across three domains.

-   **On data quality**: a deduplication pipeline to flag and remove duplicate records prior to ingestion, schema validation enforcing mandatory fields and data types at source, and standardized gender encoding restricted to two canonical values.

-   **On bias mitigation**: fairness reweighting via resampling to correct gender and age imbalances in training data, a multivariate fairness analysis controlling for financial variables (income, DTI, credit history) to distinguish true discriminatory patterns from legitimate risk differentials, and a recurring fairness audit process to monitor approval outcomes across protected groups following model updates.

-   **On GDPR and privacy**: documentation of the lawful basis per data field with applicant-facing transparency at the point of collection, pseudonymization of all direct identifiers prior to model training with secure retention of the mapping key, and a storage limitation policy mandating deletion or anonymization of applicant records once no longer needed, enforced through automated expiry triggers.

------------------------------------------------------------------------

## Team Members & Individual Contributions

| Member | Role | Contributions |
|-------------------|-------------------|----------------------------------|
| **[Noah Kreyenkamp]** | Data Engineer | Data loading, cleaning pipeline, Notebook 01 |
| **[Finley Marynek]** | Data Scientist | Bias analysis, fairness metrics, Notebook 02 |
| **[Margarida Passos da Cunha]** | Governance Officer | GDPR mapping, privacy techniques, Notebook 03 |
| **[Nina Berenice Wecera]** | Product Lead | Presentation, coordination, README, project documentation |

*All members contributed to the Git repository. Commit history available for verification.*

------------------------------------------------------------------------

## Structure

-   'data/' - Dataset files
-   'notebooks/' - Jupyter analysis notebooks
-   'src/' - Python source code
-   'reports/' - Final deliverables / visualizations

### Additional files:

-   '[PROJECT_MGMT.md](PROJECT_MGMT.md)' - Project management documentation, including our timeline, tasks, and latest meeting notes
-   '[README.md](README.md)' - Project description & documentation

------------------------------------------------------------------------

## Project Video

[Watch here](https://youtu.be/XupWi5Tb0f8)
