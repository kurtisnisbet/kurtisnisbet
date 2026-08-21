<div align="center">

# Kurtis Nisbet

**Data Scientist | Forecasting and geospatial modelling | Nature front-cover co-author** · Brisbane, Australia

[![LinkedIn](https://img.shields.io/badge/LinkedIn-0A66C2?style=for-the-badge&logo=linkedin&logoColor=white)](https://www.linkedin.com/in/kurtisnisbet)
[![Email](https://img.shields.io/badge/Email-D14836?style=for-the-badge&logo=gmail&logoColor=white)](mailto:kurtisnisbet@outlook.com)

</div>

---

## About

I am an experienced data scientist and formally trained scientist, with a passion for uncovering insights in the data space. I have a proven track record of establishing data infrastructure and practices from the ground up in business contexts, and I look forward to the opportunities to dig deeply into the data to drive smart decisions.

Currently targeting business intelligence, data science, or ML/AI roles in Brisbane, or Australia (if remote).

---

## Skills

**Languages & ML**

![Python](https://img.shields.io/badge/Python-3776AB?style=flat&logo=python&logoColor=white)
![SQL](https://img.shields.io/badge/SQL-4479A1?style=flat&logo=postgresql&logoColor=white)
![R](https://img.shields.io/badge/R-276DC3?style=flat&logo=r&logoColor=white)
![PyTorch](https://img.shields.io/badge/PyTorch-EE4C2C?style=flat&logo=pytorch&logoColor=white)
![scikit-learn](https://img.shields.io/badge/scikit--learn-F7931E?style=flat&logo=scikit-learn&logoColor=white)
![XGBoost](https://img.shields.io/badge/XGBoost-189ABF?style=flat&logoColor=white)
![LightGBM](https://img.shields.io/badge/LightGBM-02569B?style=flat&logoColor=white)
![AutoGluon](https://img.shields.io/badge/AutoGluon-276DC3?style=flat&logoColor=white)

**Geospatial & Scientific Computing**

![xarray](https://img.shields.io/badge/xarray-0C7BDC?style=flat&logoColor=white)
![Digital Earth Australia](https://img.shields.io/badge/Digital%20Earth%20Australia-2E7D32?style=flat&logoColor=white)
![QGIS](https://img.shields.io/badge/QGIS-589632?style=flat&logo=qgis&logoColor=white)
![SciPy](https://img.shields.io/badge/SciPy-8CAAE6?style=flat&logo=scipy&logoColor=white)
![NumPy](https://img.shields.io/badge/NumPy-013243?style=flat&logo=numpy&logoColor=white)

**MLOps & Infrastructure**

![MLflow](https://img.shields.io/badge/MLflow-0194E2?style=flat&logo=mlflow&logoColor=white)
![Docker](https://img.shields.io/badge/Docker-2496ED?style=flat&logo=docker&logoColor=white)
![Azure ML](https://img.shields.io/badge/Azure%20ML-0078D4?style=flat&logo=microsoftazure&logoColor=white)
![GitHub Actions](https://img.shields.io/badge/GitHub%20Actions-2088FF?style=flat&logo=githubactions&logoColor=white)
![pytest](https://img.shields.io/badge/pytest-0A9EDC?style=flat&logo=pytest&logoColor=white)
![Git](https://img.shields.io/badge/Git-F05032?style=flat&logo=git&logoColor=white)

**Visualisation & Reporting**

![Power BI](https://img.shields.io/badge/Power%20BI-F2C811?style=flat&logo=powerbi&logoColor=black)
![Streamlit](https://img.shields.io/badge/Streamlit-FF4B4B?style=flat&logo=streamlit&logoColor=white)
![Matplotlib](https://img.shields.io/badge/Matplotlib-11557C?style=flat&logoColor=white)
![Seaborn](https://img.shields.io/badge/Seaborn-4C72B0?style=flat&logoColor=white)

---

## Featured Projects

### [Ecosystem State Forecaster — Vegetation Forecasting from Satellite Time Series](https://github.com/kurtisnisbet/ecosystem-state-forecaster)

Satellite sensors can be used to measure how green the land is in order to track vegetation growth and dynamics. This project forecasts that greenness one month ahead from Digital Earth Australia imagery, across four sites chosen to span the country's climate range: subtropical Sunshine Coast, Daintree rainforest, arid Alice Springs and alpine Kosciuszko. **[Try the interactive demo →](https://ecosystem-state-forecaster.streamlit.app)**

- This project aimed to build a machine learning model that can predict future greenness more accurately than just assuming that the next month looks like this month, or next month looks like an average version of that calendar month.
- Three model families were compared: gradient-boosted trees working pixel by pixel, a ConvLSTM that predicts the next satellite image the way a video model predicts the next frame, and a graph network of the kind now used in machine-learning weather forecasting
- Most of the effort went into preventing data leakage. Models train only on months earlier than the ones they are tested on, and held-out areas are withheld in blocks with a buffer strip, because neighbouring months and neighbouring pixels are close to copies of each other. Scores are reported separately for familiar and unfamiliar ground, so it is clear where any skill comes from
- Over an 11-year record the models only beat the seasonal average in arid Alice Springs, where vegetation responds to sporadic rainfall rather than to the calendar. The graph network won there by the widest margin, 0.063 RMSE against the seasonal average's 0.087, which suits a model that lets neighbouring pixels share information, since desert rain falls in connected bands
- Extending to a 40-year record (1988 to 2026, 463 months) reversed that pattern. With four decades of history the gradient-boosted trees and the ensemble beat the seasonal average at all four sites, because the models gain about 3.5 times more training data while the seasonal average weakens as it absorbs more year-to-year variation
- A key finding was that adding rainfall data and using sharper 10 m imagery in place of 100 m did not improve the model's performance (with exception of the ConvLSTM for only finer resolutions)
- Forecasts carry uncertainty bands that are checked against how often the true value actually falls inside them, and adjustable in the demo. Tested with pytest and run in GitHub Actions

`Python` `LightGBM` `PyTorch` `xarray` `odc-stac` `Digital Earth Australia` `Streamlit` `pytest` `GitHub Actions`

---

### [FloraView — Multi-Modal Pasture Biomass Predictor](https://github.com/kurtisnisbet/FloraView)

Predicts four components of pasture biomass (green, dead, clover, total green dry matter in grams) from field photographs combined with tabular measurements, trained on the CSIRO Pasture Biomass dataset (357 observations across four Australian states). **[Live demo →](https://huggingface.co/spaces/kurtisnisbet/FloraView)**

- Late-fusion multi-modal architecture (AutoGluon `MultiModalPredictor`): a pretrained vision encoder processes the image, a parallel branch handles NDVI, sward height, season, state, and species indicators, and the representations are fused before the regression head
- Backbone comparison across the AutoGluon default, Swin-Base, and EfficientNet-B4 identified the best encoder per target. The default won on the commercially relevant `GDM_g` (R² 0.825 single split, 0.726 ± 0.036 under 5-fold CV)
- Log1p target transform stabilises training on heavily right-skewed, zero-inflated targets
- Azure ML GPU training (Tesla T4 cluster) with MLflow experiment tracking and a local CPU smoke-test pipeline
- Containerised and deployed as a Gradio web app on HuggingFace Spaces. To fit the 1 GB storage limit the demo serves the GDM and clover models and derives green biomass as `GDM − clover`

`Python` `AutoGluon` `PyTorch` `Azure ML` `MLflow` `scikit-learn` `pandas` `Gradio` `Docker` `HuggingFace` `Git LFS`

---

### [Australian Rainfall Prediction — Full-Stack Machine Learning Pipeline](https://github.com/kurtisnisbet/Australian-Rainfall-Prediction)

End-to-end supervised learning pipeline predicting next-day rainfall from 145,000 Australian weather observations (2007–2017). Built without AutoML, to develop a working understanding of each component.

- Config-driven YAML architecture, with no hardcoded parameters anywhere in the pipeline
- Chronological train/validation/test splits (70/15/15 by date), so models are always evaluated on later, unseen data
- Multi-model grid search across Logistic Regression, Random Forest, and XGBoost, with optional TimeSeriesSplit cross-validation
- Decision-threshold optimisation on the validation set, applied at inference in the app. The optimal threshold of 0.55 lifts test precision from 0.582 to 0.618
- SHAP feature importance and probability-calibration diagnostics. Afternoon humidity is the single strongest predictor, and the calibration curve shows some overconfidence at high predicted probabilities, which is stated as a limitation rather than smoothed over
- Interactive Streamlit prediction app, 33 pytest unit tests, GitHub Actions CI across Python 3.10 and 3.11

**Final model (XGBoost) test-set ROC-AUC 0.874, identical to validation.**

`Python` `scikit-learn` `XGBoost` `SHAP` `pandas` `Parquet` `Streamlit` `pytest` `GitHub Actions`

---

### [Rural Health Analytics — Queensland Healthcare Access](https://github.com/kurtisnisbet/Rural-Health-Analytics)

Applied-analytics project from a USQ industry placement examining healthcare access across four rural LGAs in South-West Queensland (Maranoa, Murweh, Quilpie, Western Downs).

- Integrated ABS Census, NDIS, and National Health Survey data into a 540-record, 116-variable dataset
- Linear regression predicting need for core assistance (R² 0.57), with intervention simulations showing that increasing NDIS providers or health employment alone produces near-zero change in predicted need
- K-means and PCA clustering of Maranoa postcodes identified three structurally distinct subregions: the Roma hub, mid-size remote towns, and small remote settlements averaging only 1–2 practitioners each
- Spearman, Kruskal-Wallis, and chi-square tests support the clustering as capturing real workforce distribution differences rather than noise

`Python` `scikit-learn` `scipy.stats` `pandas` `seaborn` `KMeans` `PCA`

---

### [Global Layoffs Analysis — SQL & Power BI](https://github.com/kurtisnisbet/Global-Layoffs-Analysis)

Analytics project examining 527,051 reported layoffs across 1,573 companies and 31 industries (March 2020 – June 2024), set against the macroeconomic conditions of the period.

- Multi-stage SQL cleaning pipeline using staging tables, `ROW_NUMBER()` deduplication, and self-joins for null propagation (3,642 raw records to 2,155 cleaned)
- Exploratory analysis across time, industry, geography, and funding stage
- Key finding: 51 companies holding $10 B in collective funding still underwent 100% workforce reduction, so capital raised is a poor predictor of survival
- Power BI dashboard surfacing temporal trends, sector rankings, and geographic distribution

`SQL` `MySQL` `Power BI` `Data Cleaning` `EDA`

---

### [Stacked-Ensemble Depth-of-Anaesthesia Index](https://github.com/kurtisnisbet/Depth-of-Anaesthesia)

Regression models predicting the Bispectral Index (BIS), the clinical depth-of-anaesthesia measure, from seven EEG-derived features. Completed for the Master of Data Science. Train and test are split by recording, so the two never share a session.

- RFECV with a linear SVR reduces 7 EEG features to 3 (x1, x4, x7), confirmed by an elbow plot where cross-validated R² plateaus beyond three features. The selected subset is near-non-redundant rather than simply the top three by correlation, since x6 correlates 0.89 with x1
- A tuned MLP (single hidden layer, early stopping) captures the strongly non-linear response in x4 that the linear SVR cannot
- Stacking the MLP and SVR through a linear meta-model gives the best result, with the meta-model placing roughly 80% of the weight on the MLP (coefficients 0.776 against 0.192)
- **R² 0.845 against the SVR baseline's 0.777, MSE 63.9 against 91.7.** The stacking gain over the standalone MLP is marginal (R² 0.845 against 0.844), and the README says so: nearly all the lift comes from the neural network, not the ensemble
- Limitations stated plainly, including that an MAE of 6.4 BIS units is non-trivial on a 0–100 scale, making this a methodological demonstration rather than a deployable monitor

`Python` `scikit-learn` `MLPRegressor` `SVR` `StackingRegressor` `RFECV` `GridSearchCV`

---

## Work Experience

**Data Scientist** — *SkyNation Publishing* (contract) · Jan 2026 – present

- Increased profit margin 22% by building the data infrastructure that merges multiple APIs into SQL to be analysed, with insights visualised in a Streamlit dashboard updated twice weekly
- Raised premium product sales 15% by modelling pricing tolerance with factorial ANOVA and multiple regression
- Informed two title acquisitions by embedding analytics into executive decision-making early and often
- Established version control, automated testing, and alert triggers on a live pipeline, replacing manual processes that had not previously existed at the company

**Senior Scientific Officer** — *Griffith University* · Oct 2025 – Jan 2026

- Supervised and mentored a team of two specialists across four data projects
- Designed and deployed an end-to-end machine-learning pipeline for an environmental monitoring program, carrying raw sensor data through to classified outputs in production

**Scientific and Technical Officer** — *Griffith University* · Jun 2018 – Oct 2025

- Co-authored a front-cover *Nature* publication (597, 77–81, 2021), a 55-site, six-continent experiment that first quantified annual deadwood carbon release at 10.9 billion tonnes, around 115% of annual global fossil-fuel emissions, with roughly 29% of it attributable to insects. Co-designed the nested spatiotemporal mixed-effects model and managed the Australian field site across the multi-year collection
- Supported the publication of work from roughly forty research projects as an individual contributor, applying data science and statistical methods to other researchers' datasets
- Saved around 300 staff-hours a year by automating instrument-to-report ETL workflows on laboratory spectrophotometers, with a visualisation dashboard
- Maintained two environmental laboratories to ISO 17025, with audit trails, quality control, and regulatory compliance

**Scientific Consultant** — *SkyNation Publishing* (contract) · Sep 2024 – present

- Advise authors on the scientific accuracy of fiction across biology, ecology, and chemistry, through beta reads and ongoing collaboration

---

## Education

**Master of Data Science (Artificial Intelligence & Machine Learning)** · 2023 – 2026
University of Southern Queensland · GPA 6.13

**Bachelor of Science (Honours) — First Class (Class IA)** · 2014 – 2018
Griffith University · Australian Rivers Institute · GPA 6.5
Honours thesis: *Effects of flooding on plant invasion pathways in subtropical riparian ecosystems (Logan River, QLD)*, supervised by Drs Samantha Capon and Catherine Leigh.

---

## Publication & Thesis

### Publication

[**Read on Nature →**](https://www.nature.com/articles/s41586-021-03740-8)

**The contribution of insects to global forest deadwood decomposition** — *Nature* **597**, 77–81 (2021)

Co-authored front-cover paper quantifying a previously unmeasured part of the global carbon cycle. Decaying forest wood releases **10.9 billion tonnes of carbon a year, around 115% of annual global fossil-fuel emissions**, and insects are responsible for roughly 29% of it. A 55-site experiment spanning six continents, from the Amazon to Brisbane, using wood from more than 140 tree species over three years.

[**Companion article in *The Conversation* →**](https://theconversation.com/decaying-forest-wood-releases-a-whopping-10-9-billion-tonnes-of-carbon-each-year-this-will-increase-under-climate-change-164406)

*"Decaying forest wood releases a whopping 10.9 billion tonnes of carbon each year. This will increase under climate change"* (2021), written for a general audience.

### Honours Thesis

**Effects of flooding on plant invasion pathways in subtropical riparian ecosystems** — Griffith University · Australian Rivers Institute, 2018

Investigated how extreme flooding shapes each stage of the plant-invasion pathway, from transport and colonisation through establishment to landscape spread, in the subtropical riparian zone of the Logan River, southeast Queensland. Combined three field surveys before and after a major flood, soil-seed-bank germination trials, a glasshouse experiment isolating non-flood stressors, and a hydrochory buoyancy experiment across five native and two invasive species (*Lantana camara*, *Ricinus communis*). Flooding reduced the extent and abundance of *L. camara* but promoted rapid colonisation by the highly buoyant *R. communis*, giving directly actionable recommendations for post-flood weed management.

---

## Talks & Presentations

**Australian Freshwater Sciences Society** — Adelaide, 2018
Presented honours research on flood-driven vegetation dynamics in subtropical riparian ecosystems. **Awarded Best Presentation.**

**Ecological Society of Australia** — Brisbane, 2018
Presented the same honours research to a general ecology audience.

---

<div align="center">

### Let's connect

[![LinkedIn](https://img.shields.io/badge/LinkedIn-0A66C2?style=for-the-badge&logo=linkedin&logoColor=white)](https://www.linkedin.com/in/kurtisnisbet)
[![Email](https://img.shields.io/badge/Email-D14836?style=for-the-badge&logo=gmail&logoColor=white)](mailto:kurtisnisbet@outlook.com)

</div>
