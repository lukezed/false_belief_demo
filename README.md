# Replication & Optimization: Social Reward and False Belief

This project provides a reproduction and methodological optimization of the data analysis originally presented in:

> Stengelin, R., Petrović, L., Thiele, M., Hepach, R., & Haun, D. B. (2024). Social reward predicts false belief understanding in Namibian Hai||om children. *Social Development*, 33(4), e12767.

While the original study established a link between social reward responsivity and Theory of Mind, this demo aims to make the analytical workflow more rigorous, transparent, and interpretable through a Bayesian framework.

## 🚀 Key Improvements & Modifications

In this replication, several critical changes were made to the original analytical pipeline to address methodological limitations and enhance the robustness of the results:

1.  **Refined Preprocessing & Variable Formatting:**
    * Departed from the original "Z-score standardization" for Age and Sex.
    * **Age:** Centered but kept in natural units (years) to allow for intuitive interpretation (e.g., "log-odds change per year" vs. "per SD").
    * **Sex:** Implemented sum-to-zero contrasts (`contr.sum`) to ensure the model intercept represents the grand mean rather than a specific reference group.

2.  **Reasonable Weakly Informative Priors:**
    * Replaced default or overly broad priors with scientifically grounded, regularizing priors.
    * Applied `normal(0, 0.5)` for monotonic social reward effects to prevent overfitting in the small sample ($N=59$) and `normal(0, 1)` for Age to allow for realistic developmental trajectories.

3.  **Handling Missing Data:**
    * Implemented **Multiple Imputation** (using the `mice` package) to address missing values, ensuring unbiased estimates compared to listwise deletion.

4.  **Intuitive Result Interpretation:**
    * Results are reported using **Odds Ratios (OR)** and probabilities for "average" and "extreme" cases, making the magnitude of the effects (e.g., adult social reward vs. age) immediately understandable.

5.  **Prior Sensitivity Analysis:**
    * Included a sensitivity check comparing the main model against "Tight" (SD=0.3) and "Wide" (SD=1.5) priors to verify the robustness of the posterior estimates.

## 📂 Project Structure

```text
.
├── analysis/                    # Additional analysis scripts or outputs
├── analysis.Rmd                 # Main analysis script (RMarkdown)
├── analysis.pdf                 # Compiled report
├── data/                        # Data folder (Empty in repo, see Data Access)
│   └── sode12767-sup-0002-suppmat.csv
├── figure/                      
│   └── slender_plot.png         # Prior vs. Posterior density plots
├── models/                      # Cached compiled Bayesian models (.rds)
│   ├── demo_FB_model_adult_age.rds
│   ├── demo_FB_model_age.rds
│   ├── demo_FB_model_null.rds
│   ├── demo_FB_model_peer_age.rds
│   ├── sens_model_adult_tight.rds
│   └── sens_model_adult_wide.rds
└── false_belief_demo.Rproj      # RProject file
```
📊 Data Access
Note: The raw data is not included in this repository to comply with distribution policies.

To reproduce this analysis, please follow these steps:

Visit the Supporting Information section of the original paper at Wiley Online Library.

Download the file sode12767-sup-0002-suppmat.csv.

Place the file inside the data/ folder in your local project directory.

🛠️ Requirements
To run the analysis, ensure you have R installed with the following key packages:

Modeling: brms, rstan, cmdstanr, mice

Data & Plotting: tidyverse, patchwork, ggdist, bayestestR

📝 How to Run
Open false_belief_demo.Rproj in RStudio.

Ensure the data file is placed correctly in data/.

Open analysis.Rmd.

Click Knit to generate the PDF report and run the full pipeline.

Note: The models/ folder contains cached model fits to save compilation time. If you wish to refit the models from scratch, delete the .rds files in the models/ directory.

Author
Chi Zhang Replication Demo - December 2025
