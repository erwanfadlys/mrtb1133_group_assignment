
# 🚨 Intelligent Crime Analytics Dashboard for Malaysia
## Leveraging AI and BI for Strategic Crime Prevention

[![PowerBI](https://img.shields.io/badge/PowerBI-Dashboard-yellow?style=flat-square&logo=powerbi)](https://powerbi.microsoft.com/)
[![Python](https://img.shields.io/badge/Python-ML%20Analytics-blue?style=flat-square&logo=python)](https://www.python.org/)
[![License](https://img.shields.io/badge/License-Academic-green?style=flat-square)](LICENSE)

---

## 📋 Project Overview

This project develops an **Intelligent Crime Analytics Dashboard** that combines **Business Intelligence (BI)** and **Artificial Intelligence (AI)** to enhance crime analysis and prevention strategies for Malaysian local government agencies.

### 🎯 Theme
**"The Next Frontier: Leveraging AI and BI for Strategic Growth and Innovation"**

Public safety and crime prevention remain critical responsibilities of Malaysian local government. With Malaysia's crime rate increasing by an average of **16.5% year-over-year** (Zaini et al., 2021), there is an urgent need for advanced analytical tools to monitor and predict crime patterns.

---

## 🔍 Background

### Current Landscape
- **Rising Crime Rates:** Rapid urbanization, population growth, and socio-economic changes have contributed to evolving crime patterns across Malaysia.
- **Data Availability:** The Department of Statistics Malaysia provides crime-related data through its official portal, presenting historical crime statistics via charts and graphs.
- **BI Implementation:** Business Intelligence has been successfully deployed across various sectors by local governments for analysis and visualization.

### The Gap
Despite the availability of crime data and BI tools, **crime analytics remain limited**:
- ✗ Static format presentations  
- ✗ Data only available up to 2018  
- ✗ Historical focus without predictive capabilities  
- ✗ Limited year-over-year comparisons  
- ✗ Descriptive analytics only—no future forecasting[web:192][web:210]

---

## ⚠️ Problem Statement

**Despite the use of Business Intelligence dashboards in various sectors by Malaysian local government and the availability of crime-related data, crime analytics remain limited in analytical capability.**

The existing crime data is primarily used in **static formats** focusing solely on **historical trends**, without predictive or forecasting capabilities.[web:192] This restricts local government's ability to:
- Analyze future crime patterns  
- Support proactive decision-making  
- Implement preventive measures  
- Compare trends across multiple years effectively

**Solution Required:** An integrated analytics approach combining **Business Intelligence** and **Artificial Intelligence** to transform crime analysis from descriptive to predictive, enabling Malaysian local government to prevent crimes through data-driven insights.

---

## 🎯 Objectives

| # | Objective | Type |
|---|-----------|------|
| **1** | Develop an intelligent crime analytics dashboard using BI tools to **visualize crime data** across states and police districts in Malaysia | Descriptive |
| **2** | Analyze historical crime data by **crime category and type** to identify trends and patterns | Descriptive |
| **3** | Identify **high crime rate states and districts** using quantitative crime metrics | Diagnostic |
| **4** | Apply **data mining and predictive analytics** to forecast future crime trends and support data-driven decision-making | Predictive |

---

## 📂 Datasets Used

| Dataset | What it is | How it is used |
|--------|------------|----------------|
| `crime_district_raw.csv` | Original crime statistics by police district and state from official Malaysian crime publications. | Serves as the **base input** for preprocessing, feature engineering, and aggregation before analytics and dashboarding. |
| `district_profiles.csv` | One row per police district/state with engineered temporal, geographical, and statistical features (totals, averages, growth rates, volatility, ratios). | Used as the **main ML feature table** for risk modelling and classification of districts into High/Medium/Low risk levels. |
| `state_timeseries.csv` | Multi-year crime counts per state (panel structure: state × year). | Feeds the **time series forecasting** models (e.g., ARIMA/SARIMA/Prophet) to generate state-level crime forecasts and trend directions visualised in Power BI. |
| `national_timeseries.csv` | Aggregated national crime totals by year for Malaysia. | Used to build the **national crime trend and forecast**, providing headline KPIs and overall trend visuals in the dashboard. |
| `state_clusters.csv` | One row per state with summary crime metrics and a cluster ID/label. | Output of **K-Means clustering** that segments states into groups (e.g., higher-volume vs lower-volume crime states) for prioritisation and policy grouping. |

---

## 🔬 Methodology | CRISP-DM

### Architecture Overview 
```text
┌─────────────────────────────────────────────────────────────┐
│                     DATA COLLECTION                         │
│              (Department of Statistics Malaysia)            │
└────────────────────────┬────────────────────────────────────┘
                         │
                         ▼
┌─────────────────────────────────────────────────────────────┐
│                   DATA PREPROCESSING                        │
│        -  Data Cleaning    -  Feature Engineering           │
│        -  Transformation   -  Quality Validation            │
└────────────────────────┬────────────────────────────────────┘
                         │
         ┌───────────────┴───────────────┐
         │                               │
         ▼                               ▼
┌──────────────────┐          ┌──────────────────────┐
│  DESCRIPTIVE BI  │          │   PREDICTIVE AI/ML   │
│    (PowerBI)     │          │      (Python/WEKA)   │
├──────────────────┤          ├──────────────────────┤
│ -  Visualizations│          │ -  Time Series       │
│ -  Trend Analysis│          │   Forecasting        │
│ -  KPI Dashboards│          │ -  Clustering        │
│ -  Interactive   │          │ -  Classification    │
│   Maps           │          │ -  Pattern Mining    │
└────────┬─────────┘          └──────────┬───────────┘
         │                               │
         └───────────────┬───────────────┘
                         │
                         ▼
┌─────────────────────────────────────────────────────────────┐
│            INTEGRATED INTELLIGENT DASHBOARD                 │
│        Historical Insights + Predictive Forecasts           │
└─────────────────────────────────────────────────────────────┘
```

### Process Flow

**1. Data Collection**  
- Source: Department of Statistics Malaysia Crime Statistics.
- Coverage: Police districts, states, crime categories/types.  
- Time Period: Historical data (multi-year).  

**2. Data Preprocessing**  
- Data cleaning and validation.  
- Missing value treatment.  
- Outlier detection and handling.  
- Feature engineering (temporal, geographical, categorical).  
- Data integration from multiple sources.

**3. Exploratory Data Analysis (EDA)**  
- Statistical summaries.  
- Distribution analysis.  
- Correlation identification.  
- Pattern discovery.

**4. Business Intelligence Development (PowerBI)**  
- Interactive dashboards.  
- Geographical crime mapping.  
- Temporal trend visualization.  
- Comparative analysis (state/district/category).  
- Key Performance Indicators (KPIs).

**5. AI/ML Analytics Development (Python)**

| Dataset / Stage           | Algorithm | Purpose (what this shows) | How this dataset can be used |
|---------------------------|----------|----------------------------|------------------------------|
| `state_timeseries.csv`    | ARIMA    | Forecast total crime counts at **state** level over time. | Demonstrates classical **time series forecasting**: the dashboard can show historical vs forecast lines, confidence bands, and how different states are expected to move (up/down/flat) in the next periods. |
| `national_timeseries.csv` | ARIMA    | Forecast **national** crime trend over time. | Provides a single national curve used for a **headline predictive KPI**; useful for showing Malaysia’s overall direction and validating ARIMA modelling concepts on aggregate data. |
| `state_clusters.csv`      | K-Means  | Group states into **crime-risk tiers** based on volume/trend features. | Demonstrates **unsupervised learning**: this dataset gives each state a cluster label (e.g., higher-volume vs lower-volume), which can be used in the dashboard to highlight priority states and compare profiles between clusters. |
| `district_profiles.csv`   | J48      | Classify districts into **High/Medium/Low risk** based on engineered features. | Demonstrates **supervised classification**: this dataset contains the engineered features plus a `risk_level` field where J48 achieved high accuracy, so the dashboard can colour maps/tables by risk and drill down to feature-driven explanations. |
| Technique                 | Algorithm | Main dataset          | Output field / artifact      |
|---------------------------|-----------|------------------------|------------------------------|
| **Time Series Forecasting** | ARIMA     | `state_timeseries.csv`, `national_timeseries.csv` | Forecasted crime values and trend direction. |
| **Clustering**           | K-Means   | `state_clusters.csv`  | Cluster ID / risk-tier label per state. |
| **Classification**       | J48       | `district_profiles.csv` | `risk_level` (High/Medium/Low) per district. |


**6. Model Evaluation**  
- Performance metrics (RMSE, MAE, Accuracy, Precision, Recall, F1-Score).  
- Cross-validation where applicable.  
- Model comparison and selection for deployment.[web:212][web:215]

**7. Dashboard Integration**  
- Embed ML insights into PowerBI.  
- Create predictive analytics views.  
- Enable drill-down from predictions to raw data.[web:209][web:213]

**8. Insights & Recommendations**  
- Actionable insights for policymakers.  
- Resource allocation recommendations.  
- Crime prevention strategies informed by patterns and forecasts.[web:200]

---

## 🛠️ Technology Stack

### Business Intelligence
- **PowerBI** – Interactive dashboards and visualizations.[web:209][web:213]  
- **DAX** – Data modeling and calculations.

### Artificial Intelligence / Machine Learning
- **Python 3.x** – Core ML development.  
- **Libraries:**
  - `pandas` – Data manipulation.  
  - `numpy` – Numerical computing.  
  - `scikit-learn` – ML algorithms.  
  - `statsmodels` – Time series analysis.  
  - `prophet` – Forecasting.  
  - `matplotlib`, `seaborn` – Visualization.  
  - `mlxtend` – Association rule mining. 
- **WEKA 3.8.6 Explorer**.  

### Data Storage
- **CSV** – Crime district and aggregated data.  
- **Power Query** – Data transformation and loading into Power BI.[web:209]

---

## 📊 Key Performance Indicators (KPIs)

| KPI | Description | Measurement |
|-----|-------------|-------------|
| **Total Crime Count** | Aggregate crimes across regions | Count |
| **Crime Rate per 100K Population** | Normalized crime metric | Rate |
| **High-Risk Districts** | Districts exceeding threshold | Count/Percentage |
| **Crime Trend Direction** | Increasing/Decreasing patterns | Percentage change |
| **Forecast Accuracy** | ML model performance | RMSE/MAE |
| **Hotspot Coverage** | Districts requiring intervention | Percentage |

---

## 📈 Expected Deliverables

### 1. PowerBI Dashboard
- Multi-page interactive dashboard.  
- Geographical crime heatmaps.  
- Time series trend charts.  
- Comparative state/district analysis.  
- Drill-through capabilities.[web:209][web:213]

### 2. Python ML Models
- Trained and validated models.  
- Model performance reports.  
- Prediction outputs (CSV/JSON) aligned to the datasets above.  
- Jupyter notebooks with analysis.[web:215]

### 3. Documentation
- Methodology report.  
- User guide for dashboard.  
- Technical documentation.  
- Limitations and future work.[web:200]

---

## 🚧 Challenges & Limitations

### Data Challenges
- **Data Quality:** Missing values and inconsistencies in reporting.  
- **Data Availability:** Many official releases provide crime data only up to 2018.  
- **Data Granularity:** Varying levels of detail across districts.  
- **Update Frequency:** Irregular data refresh cycles.[web:192][web:210][web:198]

### Technical Challenges
- **Model Accuracy:** Crime is influenced by numerous socio-economic factors.  
- **Overfitting Risk:** Limited temporal data for robust forecasting.  
- **Integration Complexity:** Embedding Python ML into PowerBI.  
- **Computational Resources:** Larger datasets require optimisation.[web:215]

### Ethical Considerations
- **Privacy:** Ensuring anonymization of sensitive crime data.  
- **Bias:** Addressing potential algorithmic bias in risk classification.  
- **Transparency:** Making ML predictions interpretable for policymakers.[web:197]

---

## 👥 Team

**Group Project - MSc Business Intelligence & Analytics**  
- **Course:** MRTB1133 - Business Intelligence  
- **Institution:** Universiti Teknologi Malaysia  
- **Semester:** 1, Year 2025/2026  
- **Team Member:** Shantini, Sri, Rosmaili, and Erwan  

---

## 📚 References

Department of Statistics Malaysia. (2019). *Crime statistics, Malaysia, 2019*. Retrieved January 3, 2026, from https://www.dosm.gov.my/portal-main/release-content/crime-statistics-malaysia-2019[web:192]

Governing with Artificial Intelligence. (2025). *Governing with Artificial Intelligence*. OECD. https://doi.org/10.1787/795DE142-EN[web:197]

Hyndman, R. J., & Athanasopoulos, G. (2021). *Forecasting: Principles and practice* (3rd ed.). OTexts. https://otexts.com/fpp3/[web:215]

Schröer, C., Kruse, F., & Gómez, J. M. (2021). A systematic literature review on applying CRISP-DM process model. *Procedia Computer Science, 181*, 526–534. https://doi.org/10.1016/j.procs.2021.01.199[web:215]

Zaini, N. E., Zakaria, S., Rahman, N. A., & Alwi, W. S. W. (2021). A statistical inference analysis on crime rates in Peninsular Malaysia using Geographical Weighted Regression. *Journal of Mathematical Sciences and Informatics, 1*(1), 45–58. https://doi.org/10.46754/JMSI.2021.12.005[web:212]

---

## 📝 License

This project is developed for academic purposes as part of the MRTB1133 Business Intelligence course.

---

## 🤝 Contributing

This is a group project. All team members equally contribute to different aspects:
- **BI Development:** Dashboard design and visualization  
- **ML Analytics:** Predictive modeling and data mining  
- **Documentation:** Report writing and presentation  
- **Data Management:** Collection, cleaning, and preprocessing  

---

<div align="center">

**Made with 💙 for safer communities in Malaysia**

*Transforming Data into Actionable Insights for Crime Prevention*

</div>
```

[1](https://ppl-ai-file-upload.s3.amazonaws.com/web/direct-files/attachments/146578248/d93e3680-0c09-4834-acda-64d34922d611/temporal_features.csv)
[2](https://ppl-ai-file-upload.s3.amazonaws.com/web/direct-files/attachments/146578248/b77bb28f-4d7c-46be-bf64-b0aa33bcf46a/national_timeseries.csv)
[3](https://ppl-ai-file-upload.s3.amazonaws.com/web/direct-files/attachments/146578248/f076ac1f-6c51-48f6-a720-7f0c01e602a0/district_profiles.csv)
[4](https://ppl-ai-file-upload.s3.amazonaws.com/web/direct-files/attachments/146578248/9bbf2b20-dfd1-40d4-b306-931788ea28fb/crime_data_cleaned.csv)
[5](https://ppl-ai-file-upload.s3.amazonaws.com/web/direct-files/attachments/146578248/9a564ea2-6178-4931-8af3-3c15f4c0afb2/02_ETL_Data_Preparation.ipynb)
[6](https://ppl-ai-file-upload.s3.amazonaws.com/web/direct-files/attachments/images/146578248/609a2950-85db-4c3c-98db-e251215945c1/image.jpg)
[7](https://ppl-ai-file-upload.s3.amazonaws.com/web/direct-files/attachments/images/146578248/f576f62a-4fb2-452b-a59e-99b668a37aaa/image.jpg)
[8](https://ppl-ai-file-upload.s3.amazonaws.com/web/direct-files/attachments/images/146578248/77ddd35f-63eb-44ca-8124-3c6a8e68a98f/image.jpg)
[9](https://ppl-ai-file-upload.s3.amazonaws.com/web/direct-files/attachments/images/146578248/f387d499-a868-4390-a0f3-595641894a56/image.jpg)
[10](https://ppl-ai-file-upload.s3.amazonaws.com/web/direct-files/attachments/images/146578248/29037180-e80c-4357-892e-5c787808cc70/image.jpg)
[11](https://ppl-ai-file-upload.s3.amazonaws.com/web/direct-files/attachments/images/146578248/b38836ea-0458-4f8d-873c-b2d685221dab/image.jpg)
[12](https://ppl-ai-file-upload.s3.amazonaws.com/web/direct-files/attachments/images/146578248/efd2c4b8-66f3-45ac-885b-deddd7076cd5/image.jpg)
[13](https://ppl-ai-file-upload.s3.amazonaws.com/web/direct-files/attachments/146578248/f26d499f-deac-443d-8f2a-df6792abfb5c/03_ML_Forecasting.ipynb)
[14](https://ppl-ai-file-upload.s3.amazonaws.com/web/direct-files/attachments/146578248/65f45bc5-6fc9-41d9-964f-c4c9843fd8f5/04_Clustering.ipynb)
[15](https://ppl-ai-file-upload.s3.amazonaws.com/web/direct-files/attachments/146578248/551802ea-1bcd-471c-a9cd-b9f1a0bfc984/03_ML_Forecasting.ipynb)
[16](https://ppl-ai-file-upload.s3.amazonaws.com/web/direct-files/attachments/images/146578248/e2bad06b-e8e7-4e7d-a169-ef898f9ec2fa/image.jpg)
[17](https://ppl-ai-file-upload.s3.amazonaws.com/web/direct-files/attachments/images/146578248/a97eaf7f-9537-4d2a-88cf-f7088f7b81f3/image.jpg)
[18](https://ppl-ai-file-upload.s3.amazonaws.com/web/direct-files/attachments/images/146578248/0ffa025c-99d7-4173-9804-776be2932f5e/image.jpg)
