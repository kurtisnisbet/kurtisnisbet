<div align="center">

# Kurtis Nisbet

**Environmental scientist turned data scientist** · Brisbane, Australia

[![LinkedIn](https://img.shields.io/badge/LinkedIn-0A66C2?style=for-the-badge&logo=linkedin&logoColor=white)](https://www.linkedin.com/in/kurtisnisbet)
[![Email](https://img.shields.io/badge/Email-D14836?style=for-the-badge&logo=gmail&logoColor=white)](mailto:kurtisnisbet@outlook.com)
[![GitHub](https://img.shields.io/badge/GitHub-181717?style=for-the-badge&logo=github&logoColor=white)](https://github.com/kurtisnisbet)

</div>

---

## About

Eight years of environmental research (including a co-authored front-cover publication in *Nature*) followed by a Master of Data Science, completed while working full-time. I build end-to-end ML systems at the intersection of environmental science and modern data engineering: bioacoustics classifiers, computer-vision regression, production pipelines, MLOps infrastructure, and analytics dashboards.

Currently a Data Scientist at SkyNation Publishing · open to applied ML and data science roles.

---

## Skills

**Languages & ML**

![Python](https://img.shields.io/badge/Python-3776AB?style=flat&logo=python&logoColor=white)
![SQL](https://img.shields.io/badge/SQL-4479A1?style=flat&logo=postgresql&logoColor=white)
![R](https://img.shields.io/badge/R-276DC3?style=flat&logo=r&logoColor=white)
![PyTorch](https://img.shields.io/badge/PyTorch-EE4C2C?style=flat&logo=pytorch&logoColor=white)
![scikit-learn](https://img.shields.io/badge/scikit--learn-F7931E?style=flat&logo=scikit-learn&logoColor=white)
![XGBoost](https://img.shields.io/badge/XGBoost-189ABF?style=flat&logoColor=white)
![AutoGluon](https://img.shields.io/badge/AutoGluon-276DC3?style=flat&logoColor=white)

**MLOps & Infrastructure**

![MLflow](https://img.shields.io/badge/MLflow-0194E2?style=flat&logo=mlflow&logoColor=white)
![Docker](https://img.shields.io/badge/Docker-2496ED?style=flat&logo=docker&logoColor=white)
![Azure ML](https://img.shields.io/badge/Azure%20ML-0078D4?style=flat&logo=microsoftazure&logoColor=white)
![FastAPI](https://img.shields.io/badge/FastAPI-009688?style=flat&logo=fastapi&logoColor=white)
![PostgreSQL](https://img.shields.io/badge/PostgreSQL-4169E1?style=flat&logo=postgresql&logoColor=white)
![GitHub Actions](https://img.shields.io/badge/GitHub%20Actions-2088FF?style=flat&logo=githubactions&logoColor=white)
![Git](https://img.shields.io/badge/Git-F05032?style=flat&logo=git&logoColor=white)

**Visualisation & Reporting**

![Power BI](https://img.shields.io/badge/Power%20BI-F2C811?style=flat&logo=powerbi&logoColor=black)
![Streamlit](https://img.shields.io/badge/Streamlit-FF4B4B?style=flat&logo=streamlit&logoColor=white)
![Matplotlib](https://img.shields.io/badge/Matplotlib-11557C?style=flat&logoColor=white)
![Seaborn](https://img.shields.io/badge/Seaborn-4C72B0?style=flat&logoColor=white)

---

## Featured Projects

### [Pasture Biomass Predictor — Multi-Modal Deep Learning](https://github.com/kurtisnisbet/pasture-biomass-predictor)

Predicts four components of pasture biomass (green, dead, clover, total GDM in grams) from a single smartphone photograph combined with tabular field measurements. Trained on the CSIRO Pasture Biomass dataset (357 observations across five Australian states).

- **Late-fusion multi-modal architecture** with AutoGluon `MultiModalPredictor`, a pretrained vision encoder processes the image, a parallel branch handles NDVI, sward height, season, state, and one-hot species presence, and the two representations are concatenated before the regression head
- **Backbone comparison** across the AutoGluon default, Swin-Base, and EfficientNet-B4 identified the best encoder per target, the default backbone won on the commercially-relevant `GDM_g` (R² = 0.825), Swin-Base won on the low-signal `Dry_Dead_g`
- **Log1p target transform** stabilises training on heavily right-skewed, zero-inflated targets
- **5-fold cross-validation** on 357 samples yields a mean R² of 0.726 ± 0.036 on total green dry matter, i.e. the target most relevant to farm management
- **Azure ML GPU training** (Tesla T4 cluster, ~35× speedup over local CPU) with MLflow experiment tracking

`Python` `AutoGluon` `PyTorch` `Azure ML` `MLflow` `scikit-learn` `pandas` `matplotlib`

---

### [Full-Stack Machine Learning Pipeline — Australian Rainfall Prediction](https://github.com/kurtisnisbet/Full-Stack-Machine-Learning-Pipeline)

End-to-end supervised learning pipeline predicting next-day rainfall from 145,000 Australian weather observations. Built from scratch without AutoML to develop a thorough understanding of each pipeline component.

- Config-driven YAML architecture; no hardcoded parameters anywhere in the pipeline
- Time-aware chronological train/val/test splits to prevent data leakage
- Multi-model grid search across Logistic Regression, Random Forest, and XGBoost with TimeSeriesSplit CV
- Decision-threshold optimisation on the validation set to maximise F1
- SHAP feature importance and probability-calibration diagnostics, humidity at 3 pm surfaces as the single strongest predictor
- Interactive Streamlit prediction app, pytest unit tests, GitHub Actions CI

**Test-set ROC-AUC: 0.85**

`Python` `scikit-learn` `XGBoost` `SHAP` `pandas` `Parquet` `Streamlit` `pytest` `GitHub Actions`

---

### [Health Analytics Queensland — Rural Healthcare Fragmentation](https://github.com/kurtisnisbet/Health-Analytics-Queensland)

Applied-analytics portfolio from a USQ industry placement examining healthcare access across four rural LGAs in South-West Queensland (Maranoa, Murweh, Quilpie, Western Downs).

- Integrated ABS Census, NDIS, and National Health Survey data into a 480-record, 116-variable dataset
- Linear regression predicting need for core assistance (R² = 0.57), with intervention simulations showing that NDIS provider increases alone produce near-zero effect without addressing geographic access
- K-means + PCA clustering of Maranoa postcodes identified three structurally distinct subregions, Roma hub, mid-size remote, small remote — each with radically different practitioner-to-population ratios (1:172 vs 1:310 vs 1:129)
- Statistical validation via Spearman, Kruskal-Wallis, and chi-square tests confirms the clustering captures genuine workforce inequity rather than noise

`Python` `scikit-learn` `scipy.stats` `pandas` `seaborn` `KMeans` `PCA`

---

### [Global Layoffs Analysis — SQL & Power BI](https://github.com/kurtisnisbet/Global-Layoffs-Analysis)

End-to-end analytics project examining 527,000 layoff records across 1,500+ companies and 31 industries (2020–2024), contextualised within the macroeconomic conditions of the period.

- Multi-stage SQL cleaning pipeline using staging tables, `ROW_NUMBER()` deduplication, and self-joins for null propagation
- Exploratory analysis across time, industry, geography, and funding stage
- Key finding: 51 companies with $10 B+ in collective funding still underwent 100% workforce reduction, capital raised is a poor predictor of survival
- Power BI dashboard surfacing temporal trends, sector rankings, and geographic distribution

`SQL` `MySQL` `Power BI` `Data Cleaning` `EDA`

---

### [Stacked-Ensemble Depth-of-Anaesthesia Prediction](https://github.com/kurtisnisbet/Stacked-Ensemble-Depth-of-Anaesthesia)

Stacked ensemble model for real-time depth-of-anaesthesia monitoring from EEG data, benchmarked against the clinical Bispectral Index (BIS) standard.

- **RFECV with SVR** reduces 7 EEG features to the 3 most predictive
- **MLP** (2 hidden layers, early stopping) captures non-linear relationships that SVR misses
- **Stacking ensemble** (MLP + SVR → linear meta-model) weights NN at 63% and SVR at 37%, indicating complementary model strengths, while keeping inference cheap enough for real-time surgical use
- Outperforms the SVR baseline: R² 0.85 vs 0.78, MSE 64 vs 92

`Python` `scikit-learn` `MLPRegressor` `SVR` `StackingRegressor` `RFECV` `GridSearchCV`

---

## Education

**Master of Data Science (Machine Learning and AI)** — *Distinction* · 2026
University of Southern Queensland

**Bachelor of Science (Honours) — First Class** · 2018
Griffith University · Australian Rivers Institute
Honours thesis: *Effects of flooding on plant invasion pathways in subtropical riparian ecosystems (Logan River, QLD)* — supervised by Drs Samantha Capon and Catherine Leigh.

---

## Work Experience

**Data Scientist** — *SkyNation Publishing* · Sep 2024 – present *(independent contractor)*
Built an end-to-end analytics ecosystem from scratch, i.e. automated ingestion, preprocessing, feature engineering, and reporting across sales, market, and customer-behaviour datasets. Contributed to a 22% profit margin increase and a title acquisitions.

**Senior Scientific Officer** — *Griffith University* · Oct 2025 – Jan 2026

- Co-led a three-stage automated ML pipeline for freshwater bioacoustics, i.e. signal-processing pre-segmentation, deep-learning species recognition on hand-labelled spectrograms, and ensemble waterway-health classification (findings in preparation for publication)
- Deployed an Azure ML pipeline (Event Hub, Data Lake, Data Factory, Synapse, Power BI) to classify field-collected samples into one of the fifteen Australian soil types, replacing manual laboratory workflows

**Scientific Officer & Technical Officer** — *Griffith University, School of Environmental Science* · Jun 2018 – Oct 2025
Contributed as analyst and researcher across approximately forty research projects spanning freshwater ecology, riparian ecosystems, wetland monitoring, and soil science. Co-authored a front-cover publication in *Nature* (597, 77–81, 2021) identifying a previously unknown component of the global carbon cycle, with a companion piece in *The Conversation* (2021).

---

## Publication & Thesis

### Publication

[**Read on Nature →**](https://www.nature.com/articles/s41586-021-03740-8)

**The contribution of insects to global forest deadwood decomposition** — *Nature* **597**, 77–81 (2021)

Co-authored front-cover paper identifying a previously unknown component of the global carbon cycle. Companion article published in *The Conversation* (2021).

### Honours Thesis

**Effects of flooding on plant invasion pathways in subtropical riparian ecosystems** — Griffith University · Australian Rivers Institute, 2018

Bachelor of Science (Honours) thesis supervised by Drs Samantha Capon and Catherine Leigh. Investigated how extreme flooding shapes each stage of the plant-invasion pathway, i.e. transport, colonisation, establishment, and landscape spread, in the subtropical riparian zone of the Logan River, southeast Queensland.

Combined three field surveys before and after a major flood, soil-seed-bank germination trials, a glasshouse experiment isolating non-flood stressors (allelochemicals and leaf-litter cover), and a hydrochory buoyancy experiment across five native and two invasive species (*Lantana camara*, *Ricinus communis*). Flooding reduced the extent and abundance of *L. camara* but promoted rapid colonisation by the highly buoyant *R. communis*, yielding directly actionable recommendations for post-flood weed management.


---

## Talks & Presentations

**Australian Freshwater Sciences Society** — Adelaide, 2018
Presented honours research on flood-driven vegetation dynamics in subtropical riparian ecosystems. Awarded Best Honours Presentation.

**Ecological Society of Australia** — Brisbane, 2018
Presented honours research on plant invasion pathways in the flood-impacted riparian ecosystems of the Logan River.

---

<div align="center">

### Let's connect

[![LinkedIn](https://img.shields.io/badge/LinkedIn-0A66C2?style=for-the-badge&logo=linkedin&logoColor=white)](https://www.linkedin.com/in/kurtisnisbet)
[![Email](https://img.shields.io/badge/Email-D14836?style=for-the-badge&logo=gmail&logoColor=white)](mailto:kurtisnisbet@outlook.com)

</div>
