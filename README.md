<div align="center">

# Kurtis Nisbet

**Environmental scientist turned data scientist** · Brisbane, Australia

[![LinkedIn](https://img.shields.io/badge/LinkedIn-0A66C2?style=for-the-badge&logo=linkedin&logoColor=white)](https://www.linkedin.com/in/kurtisnisbet)
[![Email](https://img.shields.io/badge/Email-D14836?style=for-the-badge&logo=gmail&logoColor=white)](mailto:kurtisnisbet@outlook.com)
[![GitHub](https://img.shields.io/badge/GitHub-181717?style=for-the-badge&logo=github&logoColor=white)](https://github.com/kurtisnisbet)

</div>

---

## About

Eight years in the environmental sciences, a front-cover *Nature* publication, followed by a Master of Data Science (AI & Machine Learning). I build end-to-end ML systems that make sense of complex data: multi-modal deep learning, production pipelines, MLOps infrastructure, and analytics dashboards, with a particular interest in applying them to environmental problems.

Currently a Data Scientist at SkyNation Publishing. Exploring roles and collaborations in environmental data science.

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

### [FloraView — Multi-Modal Pasture Biomass Predictor](https://github.com/kurtisnisbet/FloraView)

Predicts four components of pasture biomass (green, dead, clover, total green dry matter in grams) from a smartphone photograph combined with tabular field measurements, trained on the CSIRO Pasture Biomass dataset (357 observations across four Australian states). **[Live demo →](https://huggingface.co/spaces/kurtisnisbet/FloraView)**

- **Late-fusion multi-modal architecture** (AutoGluon `MultiModalPredictor`): a pretrained vision encoder processes the image, a parallel branch handles NDVI, sward height, season, state, and species indicators, and the representations are fused before the regression head
- **Backbone comparison** across the AutoGluon default, Swin-Base, and EfficientNet-B4 identified the best encoder per target — the default won on the commercially relevant `GDM_g` (R² = 0.825 single split; 0.726 ± 0.036 under 5-fold CV)
- **Log1p target transform** stabilises training on heavily right-skewed, zero-inflated targets
- **Azure ML GPU training** (Tesla T4 cluster) with MLflow experiment tracking and a local CPU smoke-test pipeline
- **Containerised and deployed** as a Gradio web app on HuggingFace Spaces (Docker, free CPU tier); to fit the 1 GB storage limit the demo serves the GDM and clover models and derives green biomass as `GDM − clover`

`Python` `AutoGluon` `PyTorch` `Azure ML` `MLflow` `scikit-learn` `pandas` `Gradio` `Docker` `HuggingFace` `Git LFS`

---

### [Australian Rainfall Model - Full-Stack Machine Learning Pipeline](https://github.com/kurtisnisbet/Australian Rainfall Model)

End-to-end supervised learning pipeline predicting next-day rainfall from 145,000 Australian weather observations (2007–2017). Built from scratch without AutoML to develop a thorough understanding of each pipeline component.

- Config-driven YAML architecture; no hardcoded parameters anywhere in the pipeline
- Chronological train/val/test splits so models are always evaluated on later, unseen data
- Multi-model grid search across Logistic Regression, Random Forest, and XGBoost (optional TimeSeriesSplit CV)
- Decision-threshold optimisation on the validation set, applied at inference in the app
- SHAP feature importance and probability-calibration diagnostics — 3 pm humidity surfaces as the single strongest predictor
- Interactive Streamlit prediction app, 33 pytest unit tests, GitHub Actions CI

**Final model (XGBoost) test-set ROC-AUC: 0.874**

`Python` `scikit-learn` `XGBoost` `SHAP` `pandas` `Parquet` `Streamlit` `pytest` `GitHub Actions`

---

### [Health Analytics Queensland — Rural Healthcare Fragmentation](https://github.com/kurtisnisbet/Health-Analytics-Queensland)

Applied-analytics portfolio from a USQ industry placement examining healthcare access across four rural LGAs in South-West Queensland (Maranoa, Murweh, Quilpie, Western Downs).

- Integrated ABS Census, NDIS, and National Health Survey data into a 540-record, 116-variable dataset
- Linear regression predicting need for core assistance (R² = 0.57), with intervention simulations showing that increasing NDIS providers or health employment alone produces near-zero change in predicted need
- K-means + PCA clustering of Maranoa postcodes identified three structurally distinct subregions — the Roma hub, mid-size remote towns, and small remote settlements averaging only 1–2 practitioners each
- Statistical validation via Spearman, Kruskal-Wallis, and chi-square tests supports the clustering as capturing real workforce distribution differences rather than noise

`Python` `scikit-learn` `scipy.stats` `pandas` `seaborn` `KMeans` `PCA`

---

### [Global Layoffs Analysis — SQL & Power BI](https://github.com/kurtisnisbet/Global-Layoffs-Analysis)

End-to-end analytics project examining 527,051 reported layoffs across 1,573 companies and 31 industries (March 2020 – June 2024), contextualised within the macroeconomic conditions of the period.

- Multi-stage SQL cleaning pipeline using staging tables, `ROW_NUMBER()` deduplication, and self-joins for null propagation (3,642 raw records → 2,155 cleaned)
- Exploratory analysis across time, industry, geography, and funding stage
- Key finding: 51 companies with $10 B in collective funding still underwent 100% workforce reduction — capital raised is a poor predictor of survival
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

**Master of Data Science (Artificial Intelligence & Machine Learning)** · 2023 – 2026
University of Southern Queensland

**Bachelor of Science (Honours) — First Class** · 2014 – 2018
Griffith University · Australian Rivers Institute
Honours thesis: *Effects of flooding on plant invasion pathways in subtropical riparian ecosystems (Logan River, QLD)*, supervised by Drs Samantha Capon and Catherine Leigh.

---

## Work Experience

**Data Scientist** — *SkyNation Publishing* · Jan 2026 – present
Replaced manual spreadsheet workflows with automated, version-controlled pipelines across sales, marketing, and customer data. Architected three MLOps pipelines covering social sentiment analysis, audience segmentation, and sales forecasting, and built customer classification and clustering models to inform pricing strategy.

**Scientific Officer & Senior Scientific Officer** — *Griffith University, School of Environmental Science* · Jun 2019 – Jan 2026
Provided scientific and analytical support across more than forty research projects spanning freshwater ecology, riparian ecosystems, wetland monitoring, and soil science. Co-authored a front-cover publication in *Nature* (597, 77–81, 2021) identifying a previously unknown component of the global carbon cycle. Deployed an Azure-based ML pipeline (Event Hub, Data Lake, Azure ML, Data Factory, Synapse, Power BI) to automate soil-type classification, replacing manual laboratory workflows, and co-designed a three-stage automated ML pipeline for freshwater bioacoustics: signal-processing pre-segmentation, deep-learning species recognition on hand-labelled spectrograms, and ensemble waterway-health classification.

**Technical Officer** — *Griffith University* · Jun 2018 – Jun 2019
Supported laboratory operations and teaching across the environmental sciences, delivering training to approximately 300 students in laboratory and field settings and mentoring junior scientists in experimental design, safety, and scientific practice.

**Research Assistant** — *Griffith University* · Sep 2017 – Mar 2018
Contributed to environmental research projects across data collection, statistical analysis, and predictive modelling.

---

## Publication & Thesis

### Publication

[**Read on Nature →**](https://www.nature.com/articles/s41586-021-03740-8)

**The contribution of insects to global forest deadwood decomposition** — *Nature* **597**, 77–81 (2021)

Co-authored front-cover paper identifying a previously unknown component of the global carbon cycle. Companion article published in *The Conversation* (2021).

### Honours Thesis

**Effects of flooding on plant invasion pathways in subtropical riparian ecosystems** — Griffith University · Australian Rivers Institute, 2018

Investigated how extreme flooding shapes each stage of the plant-invasion pathway — transport, colonisation, establishment, and landscape spread — in the subtropical riparian zone of the Logan River, southeast Queensland. Combined three field surveys before and after a major flood, soil-seed-bank germination trials, a glasshouse experiment isolating non-flood stressors, and a hydrochory buoyancy experiment across five native and two invasive species (*Lantana camara*, *Ricinus communis*). Flooding reduced the extent and abundance of *L. camara* but promoted rapid colonisation by the highly buoyant *R. communis*, yielding directly actionable recommendations for post-flood weed management.

---

## Talks & Presentations

**Australian Freshwater Sciences Society** — Adelaide, 2018
Presented honours research on flood-driven vegetation dynamics in subtropical riparian ecosystems. Awarded Best Honours Presentation.

**Ecological Society of Australia** — Brisbane, 2018
As above.

---

<div align="center">

### Let's connect

[![LinkedIn](https://img.shields.io/badge/LinkedIn-0A66C2?style=for-the-badge&logo=linkedin&logoColor=white)](https://www.linkedin.com/in/kurtisnisbet)
[![Email](https://img.shields.io/badge/Email-D14836?style=for-the-badge&logo=gmail&logoColor=white)](mailto:kurtisnisbet@outlook.com)

</div>


### Let's connect

[![LinkedIn](https://img.shields.io/badge/LinkedIn-0A66C2?style=for-the-badge&logo=linkedin&logoColor=white)](https://www.linkedin.com/in/kurtisnisbet)
[![Email](https://img.shields.io/badge/Email-D14836?style=for-the-badge&logo=gmail&logoColor=white)](mailto:kurtisnisbet@outlook.com)

</div>
