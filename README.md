# Banking UI A/B Testing Framework

## Project Overview
This repository provides a comprehensive end-to-end A/B testing suite designed for the credit and banking industry. Instead of relying on simple conversion rates, this framework utilizes a **Risk-Adjusted Decisioning** approach to evaluate whether a new UI (Treatment) performs better than the existing version (Control), while ensuring we do not inadvertently attract subprime (higher risk) borrowers.

## 📊 Experimental Results
After analyzing 15,000 banking leads, the experiment resulted in a **Neutral-to-Negative** outcome. The global results are summarized below:

| Metric | Frequentist (Z-Test) | Bootstrap (5k) | Bayesian Analysis |
| :--- | :--- | :--- | :--- |
| **P-Value / Prob** | 0.4812 | 0.7606 | **23.57% (P > 0)** |
| **Lift / Cred. Int.** | - | [-0.84%, 0.42%] | [-0.85%, 0.40%] |
| **Conclusion** | Not Significant | Not Significant | Stop (Expected Loss > 0) |



## Methodology Highlights
* **Bayesian Posterior Analysis:** We modeled the conversion rates as Beta-Binomial distributions. The resulting **Expected Loss (0.0026)** provided a clear quantitative signal to halt the rollout, protecting the business from potential conversion degradation.
* **Risk Profile Integrity:** We monitored for **Adverse Selection** by plotting the credit score density of successful converters. Ensuring the credit score distribution of the treatment group does not shift toward lower scores is critical for banking compliance.

* **Segmented Analysis (Simpson's Paradox):** While the global result was negative, our segmented analysis revealed performance variations across age demographics, preventing a "blanket" rejection of the design and highlighting areas for future iteration.

* **Languages:** Python
* **Libraries:** `Pandas`, `NumPy`, `Statsmodels`, `SciPy`, `Seaborn`, `Matplotlib`
* **Statistical Methods:** Frequentist (Z-test), Non-parametric (Bootstrapping), Bayesian (Beta-Binomial)

# Banking A/B Testing Results

## Visual Analysis
To understand why our experiment failed, we performed a deep-dive analysis.
### 1. Risk Profile (Adverse Selection Check)
This plot confirms that our UI change did not attract higher-risk borrowers, as the credit score distributions remain balanced.
![Risk Profile Plot](images/risk_profile.png)
### 2. Segmented Performance
The global lift was negative, but this plot reveals the "hidden story": the new UI worked for younger users but failed significantly for the Senior segment.
![Segmented Lift](images/segmented_lift.png)

