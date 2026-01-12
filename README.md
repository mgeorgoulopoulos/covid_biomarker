# COVID-19 Biomarker Discovery
Finding a lab-ready 10-protein signature using Olink proteomics.

## The Strategy
* **Goal:** Identify markers that actually work in a lab setting.
* **Selection:** Prioritized **abundant** proteins with **strong Log2FC**. This ensures detection by standard tests, though Olink’s **PEA (PCR-amplified)** method remains the gold standard for sensitivity.
* **Stats:** Mann-Whitney U tests with **FDR (Benjamini-Hochberg)** correction.
* **Pruning:** Used **LASSO** to cut noise and isolate the most predictive features.

## The Model
* **Non-linear Synergy:** Used **XGBoost** for the final classifier. Unlike LASSO, it captures protein interactions (synergy) that linear models miss.
* **Rank Product:** Balanced p-values, fold change, abundance and predictive power into a single utility score for final selection.

## Results
* **Performance:** 95% accuracy and 0.86 AUC on the test set.
* **Imbalance:** Applied weighted loss to maintain sensitivity despite a 9:1 class split.
* **Validation:** Top hit was **DDX58 (RIG-I)**—the primary sensor for SARS-CoV-2. The math matches the biology.