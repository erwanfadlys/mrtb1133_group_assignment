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
- **Rising Crime Rates:** Rapid urbanization, population growth, and socio-economic changes have contributed to evolving crime patterns across Malaysia
- **Data Availability:** The Department of Statistics Malaysia provides crime-related data through its official portal, presenting historical crime statistics via charts and graphs
- **BI Implementation:** Business Intelligence has been successfully deployed across various sectors by local governments for analysis and visualization

### The Gap
Despite the availability of crime data and BI tools, **crime analytics remain limited**:
- ✗ Static format presentations
- ✗ Data only available up to 2018
- ✗ Historical focus without predictive capabilities
- ✗ Limited year-over-year comparisons
- ✗ Descriptive analytics only—no future forecasting

---

## ⚠️ Problem Statement

**Despite the use of Business Intelligence dashboards in various sectors by Malaysian local government and the availability of crime-related data, crime analytics remain limited in analytical capability.**

The existing crime data is primarily used in **static formats** focusing solely on **historical trends**, without predictive or forecasting capabilities. This restricts local government's ability to:
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

## 🔬 Methodology

### Architecture Overview
```
┌─────────────────────────────────────────────────────────────┐
│                     DATA COLLECTION                          │
│              (Department of Statistics Malaysia)             │
└────────────────────────┬────────────────────────────────────┘
                         │
                         ▼
┌─────────────────────────────────────────────────────────────┐
│                   DATA PREPROCESSING                         │
│        • Data Cleaning    • Feature Engineering             │
│        • Transformation   • Quality Validation              │
└────────────────────────┬────────────────────────────────────┘
                         │
         ┌───────────────┴───────────────┐
         │                               │
         ▼                               ▼
┌──────────────────┐          ┌──────────────────────┐
│  DESCRIPTIVE BI  │          │   PREDICTIVE AI/ML   │
│    (PowerBI)     │          │      (Python)        │
├──────────────────┤          ├──────────────────────┤
│ • Visualizations │          │ • Time Series        │
│ • Trend Analysis │          │   Forecasting        │
│ • KPI Dashboards │          │ • Clustering         │
│ • Interactive    │          │ • Classification     │
│   Maps           │          │ • Pattern Mining     │
└────────┬─────────┘          └──────────┬───────────┘
         │                               │
         └───────────────┬───────────────┘
                         │
                         ▼
┌─────────────────────────────────────────────────────────────┐
│            INTEGRATED INTELLIGENT DASHBOARD                  │
│        Historical Insights + Predictive Forecasts            │
└─────────────────────────────────────────────────────────────┘
```

### Process Flow

**1. Data Collection**
- Source: Department of Statistics Malaysia Crime Statistics
- Coverage: Police districts, states, crime categories/types
- Time Period: Historical data (multi-year)

**2. Data Preprocessing**
- Data cleaning and validation
- Missing value treatment
- Outlier detection and handling
- Feature engineering (temporal, geographical, categorical)
- Data integration from multiple sources

**3. Exploratory Data Analysis (EDA)**
- Statistical summaries
- Distribution analysis
- Correlation identification
- Pattern discovery

**4. Business Intelligence Development (PowerBI)**
- Interactive dashboards
- Geographical crime mapping
- Temporal trend visualization
- Comparative analysis (state/district/category)
- Key Performance Indicators (KPIs)

**5. AI/ML Analytics Development (Python)**

| Technique | Algorithm | Purpose | Output |
|-----------|-----------|---------|--------|
| **Time Series Forecasting** | ARIMA/SARIMA/Prophet | Predict future crime counts | 6-12 month forecasts |
| **Clustering** | K-Means/DBSCAN | Identify crime hotspots | Risk zone classifications |
| **Classification** | Random Forest/XGBoost | Categorize district risk levels | High/Medium/Low risk labels |
| **Association Mining** | Apriori Algorithm | Discover crime correlations | Crime pattern rules |

**6. Model Evaluation**
- Performance metrics (RMSE, MAE, Accuracy, Precision, Recall, F1-Score)
- Cross-validation
- Model comparison and selection

**7. Dashboard Integration**
- Embed ML insights into PowerBI
- Create predictive analytics views
- Enable drill-down from predictions to raw data

**8. Insights & Recommendations**
- Actionable insights for policymakers
- Resource allocation recommendations
- Crime prevention strategies

---

## 🛠️ Technology Stack

### Business Intelligence
- **PowerBI** - Interactive dashboards and visualizations
- **DAX** - Data modeling and calculations

### Artificial Intelligence / Machine Learning
- **Python 3.x** - Core ML development
- **Libraries:**
  - `pandas` - Data manipulation
  - `numpy` - Numerical computing
  - `scikit-learn` - ML algorithms
  - `statsmodels` - Time series analysis
  - `prophet` - Forecasting
  - `matplotlib`, `seaborn` - Visualization
  - `mlxtend` - Association rule mining

### Data Storage
- **CSV** - Crime district data
- **Power Query** - Data transformation

---

## 📊 Key Performance Indicators (KPIs)

| KPI | Description | Measurement |
|-----|-------------|-------------|
| **Total Crime Count** | Aggregate crimes across regions | Count |
| **Crime Rate per 100K Population** | Normalized crime metric | Rate |
| **High-Risk Districts** | Districts exceeding threshold | Count/Percentage |
| **Crime Trend Direction** | Increasing/Decreasing patterns | Percentage Change |
| **Forecast Accuracy** | ML model performance | RMSE/MAE |
| **Hotspot Coverage** | Districts requiring intervention | Percentage |

---

## 📈 Expected Deliverables

### 1. PowerBI Dashboard
- Multi-page interactive dashboard
- Geographical crime heatmaps
- Time series trend charts
- Comparative state/district analysis
- Drill-through capabilities

### 2. Python ML Models
- Trained and validated models
- Model performance reports
- Prediction outputs (CSV/JSON)
- Jupyter notebooks with analysis

### 3. Documentation
- Methodology report
- User guide for dashboard
- Technical documentation
- Limitations and future work

---

## 🚧 Challenges & Limitations

### Data Challenges
- **Data Quality:** Missing values, inconsistencies in reporting
- **Data Availability:** Limited to historical data up to 2018
- **Data Granularity:** Varying levels of detail across districts
- **Update Frequency:** Irregular data refresh cycles

### Technical Challenges
- **Model Accuracy:** Crime is influenced by numerous socio-economic factors
- **Overfitting Risk:** Limited temporal data for robust forecasting
- **Integration Complexity:** Embedding Python ML into PowerBI
- **Computational Resources:** Large datasets require optimization

### Ethical Considerations
- **Privacy:** Ensuring anonymization of sensitive crime data
- **Bias:** Addressing potential algorithmic bias in risk classification
- **Transparency:** Making ML predictions interpretable for policymakers

---

## 👥 Team

**Group Project - MSc Business Intelligence & Analytics**
- **Course:** MRTB1133 - Business Intelligence
- **Institution:** Universiti Teknologi Malaysia
- **Semester:** 1, Year 2025/2026
- **Team Member:** Shantini, Sri, Rosmaili, and Erwan

---

## 📚 References

Department of Statistics Malaysia. (2019). *Crime Statistics Malaysia 2019*. Retrieved January 3, 2026, from https://www.dosm.gov.my/portal-main/release-content/crime-statistics-malaysia-2019

OECD. (2025). *Governing with Artificial Intelligence*. OECD Publishing. https://doi.org/10.1787/795DE142-EN

Zaini, N. E., Zakaria, S., Rahman, N. A., & Alwi, W. S. W. (2021). A statistical inference analysis on crime rates in Peninsular Malaysia using Geographical Weighted Regression. *Journal of Mathematical Sciences and Informatics, 1*(1), 45–58. https://doi.org/10.46754/JMSI.2021.12.005

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
