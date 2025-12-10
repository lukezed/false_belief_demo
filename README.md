# Replication & Optimization: Social Reward and False Belief

This project provides a reproduction and methodological optimization of the data analysis originally presented in:

> Stengelin, R., Petrović, L., Thiele, M., Hepach, R., & Haun, D. B. (2024). Social reward predicts false belief understanding in Namibian Hai||om children. *Social Development*, 33(4), e12767.

While the original study established a link between social reward responsivity and Theory of Mind, this demo aims to make the analytical workflow more rigorous, transparent, and interpretable through a Bayesian framework.

## 🚀 Key Improvements & Modifications

I tried to make the entire analysis process more rigorous and comprehensive, so I made some necessary modifications to the original workflow. These include:

* **Preprocessing:** Fixed variable formatting (e.g., centering instead of scaling) for better interpretability.
* **Priors:** Applied more reasonable weakly informative priors.
* **Missing Data:** Performed multiple imputation to handle missing data.
* **Interpretation:** Provided more intuitive results and explanations.
* **Sensitivity Check:** Added a prior sensitivity analysis to verify robustness.

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
## 📊 Data Access
Note: The raw data is not included in this repository to comply with distribution policies.

To reproduce this analysis, please follow these steps:

Visit the Supporting Information section of the original paper at Wiley Online Library.

Download the file sode12767-sup-0002-suppmat.csv.

Place the file inside the data/ folder in your local project directory.

## 🛠️ Requirements
To run the analysis, ensure you have R installed with the following key packages:

Modeling: brms, rstan, cmdstanr, mice

Data & Plotting: tidyverse, patchwork, ggdist, bayestestR

## 📝 How to Run
Open false_belief_demo.Rproj in RStudio.

Ensure the data file is placed correctly in data/.

Open analysis.Rmd.

Click Knit to generate the PDF report and run the full pipeline.

Note: The models/ folder contains cached model fits to save compilation time. If you wish to refit the models from scratch, delete the .rds files in the models/ directory.

## Author
Chi Zhang Replication Demo - December 2025
