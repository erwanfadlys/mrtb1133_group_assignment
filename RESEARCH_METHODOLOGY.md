# 📊 Research Methodology: Crime Analytics with ML/AI
## A Complete Guide to Data Science Research Process

**Project:** Intelligent Crime Analytics Dashboard for Malaysia  
**Your Role:** ML/AI Analysis & Predictive Modeling  
**Methodology:** CRISP-DM (Cross-Industry Standard Process for Data Mining)  

---

## 🎯 What is CRISP-DM?

**CRISP-DM** is the industry-standard methodology for data science projects. It consists of 6 phases that guide you from raw data to actionable insights.

```
┌─────────────────────────────────────────────────────────────────┐
│                   CRISP-DM LIFECYCLE                            │
├─────────────────────────────────────────────────────────────────┤
│                                                                 │
│    1. Business Understanding                                   │
│           ↓                                                     │
│    2. Data Understanding    ←─────┐                            │
│           ↓                        │                            │
│    3. Data Preparation             │  (Iterate as needed)       │
│           ↓                        │                            │
│    4. Modeling                     │                            │
│           ↓                        │                            │
│    5. Evaluation           ────────┘                            │
│           ↓                                                     │
│    6. Deployment                                                │
│                                                                 │
└─────────────────────────────────────────────────────────────────┘
```

---

## 📋 Phase-by-Phase Breakdown

### Phase 1: Business Understanding
**🎯 Goal:** Understand what you're trying to solve and why it matters

**Activities:**
- Define business objectives
- Identify success criteria
- Translate business goals into ML problems
- Determine project constraints (time, resources, data)

**For Our Project:**
- ✓ Business Problem: Malaysian crime analytics limited to historical data
- ✓ Business Objective: Build predictive crime analytics dashboard
- ✓ ML Objectives:
  - Forecast future crime trends (Time Series)
  - Identify crime hotspots (Clustering)
  - Classify districts by risk level (Classification)
  - Discover crime patterns (Association Mining)
- ✓ Success Criteria: Model accuracy >80%, actionable insights for policymakers

**Deliverable:** Problem statement, objectives (✓ Done in README!)

---

### Phase 2: Data Understanding
**🎯 Goal:** Know your data inside-out before touching it

**Activities:**
- Collect initial data
- Explore data structure (rows, columns, types)
- Identify data quality issues
- Discover patterns and anomalies
- Verify assumptions about the data
- Document findings

**Why This Matters:**
You can't clean data you don't understand. You can't build models on broken data. This phase SAVES you from wasting weeks on bad data!

**Tools Used:**
- Python: `pandas`, `numpy` (data manipulation)
- Visualization: `matplotlib`, `seaborn`, `plotly` (seeing patterns)
- Statistical analysis: `scipy`, `statsmodels` (testing hypotheses)

**What You Look For:**
| Aspect | Questions to Ask |
|--------|------------------|
| **Structure** | How many rows/columns? What are the data types? |
| **Quality** | Missing values? Duplicates? Outliers? |
| **Completeness** | Any gaps in time/geography? |
| **Consistency** | Same format across all records? |
| **Accuracy** | Do aggregates match sums? Any impossible values? |
| **Relationships** | Hierarchies? Dependencies? Correlations? |
| **Distribution** | What's the range? Mean? Skewness? |

**Jupyter Notebooks for This Phase:**
- `01_EDA_Crime_Data.ipynb` - Exploratory Data Analysis
  - Load data
  - Profile dataset (shape, types, memory)
  - Check for missing values, duplicates
  - Visualize distributions
  - Analyze temporal coverage
  - Map hierarchical structure
  - **Output:** Data quality report

**Deliverable:** EDA report with visualizations and issue list

---

### Phase 3: Data Preparation
**🎯 Goal:** Transform raw data into clean, ML-ready datasets

**Activities:**
- Clean data (handle missing values, remove duplicates)
- Transform features (encoding, normalization, scaling)
- Engineer new features (create derived variables)
- Select relevant features
- Split data (train/test/validation)
- Document all transformations

**Why This Matters:**
"Garbage in, garbage out." ML models can only learn from the data you feed them. Clean, well-prepared data = better models.

**Common Data Preparation Tasks:**

| Task | Purpose | Techniques |
|------|---------|-----------|
| **Handling Missing Data** | Fill gaps | Imputation (mean/median/mode), interpolation, deletion |
| **Outlier Treatment** | Remove anomalies | IQR method, Z-score, domain knowledge |
| **Encoding Categorical** | Convert text to numbers | Label encoding, one-hot encoding, target encoding |
| **Feature Scaling** | Normalize ranges | StandardScaler, MinMaxScaler, RobustScaler |
| **Feature Engineering** | Create new variables | Aggregations, ratios, time-based features |
| **Data Splitting** | Prepare for training | Train (70%), Validation (15%), Test (15%) |

**For Our Crime Data:**
- Remove hierarchical aggregates (`district = 'All'`)
- Handle zero crimes (valid or missing?)
- Create features:
  - Year-over-year change %
  - Crime rate per capita (if population data available)
  - Crime diversity index
  - High-risk flag
- Encode categorical variables (state, district, crime type)
- Prepare separate datasets for:
  - Time series forecasting
  - Clustering analysis
  - Classification modeling

**Jupyter Notebooks for This Phase:**
- `02_ETL_Data_Preparation.ipynb` - Extract, Transform, Load
  - Data cleaning pipeline
  - Feature engineering functions
  - Train/test splits
  - Export cleaned datasets
  - **Output:** Multiple CSV files ready for modeling

**Deliverable:** Clean datasets + transformation documentation

---

### Phase 4: Modeling
**🎯 Goal:** Build and train ML models to solve your problem

**Activities:**
- Select appropriate algorithms
- Set model parameters (hyperparameters)
- Train models on training data
- Validate models on validation data
- Compare multiple models
- Tune hyperparameters
- Document model choices and rationale

**Why This Matters:**
This is where the "magic" happens - but it's not magic, it's math! Choosing the RIGHT algorithm for your problem is critical.

**ML Techniques for Crime Analytics:**

#### 1. Time Series Forecasting
**Problem:** Predict future crime counts

| Algorithm | Use Case | Pros | Cons |
|-----------|----------|------|------|
| **ARIMA** | Univariate time series | Simple, interpretable | Assumes linear trends |
| **SARIMA** | Seasonal patterns | Captures seasonality | Requires more data |
| **Prophet** | Multiple seasonalities | Robust to missing data | Black box |
| **LSTM** | Complex patterns | Captures long-term dependencies | Needs lots of data |

**For Our Data:** 
- Challenge: Only 8 yearly data points (limited)
- Solution: Use ARIMA/Prophet, aggregate by state for more samples

#### 2. Clustering Analysis
**Problem:** Group districts with similar crime patterns

| Algorithm | Use Case | Pros | Cons |
|-----------|----------|------|------|
| **K-Means** | Spherical clusters | Fast, simple | Must specify k |
| **DBSCAN** | Arbitrary shapes | Finds outliers | Sensitive to parameters |
| **Hierarchical** | Nested clusters | Visualizable (dendrogram) | Slow on large data |

**For Our Data:**
- Features: avg_assault, avg_property, total_crimes, crime_diversity
- Goal: Identify High/Medium/Low risk zones

#### 3. Classification
**Problem:** Predict district risk level (High/Medium/Low)

| Algorithm | Use Case | Pros | Cons |
|-----------|----------|------|------|
| **Random Forest** | Non-linear relationships | Handles outliers, feature importance | Can overfit |
| **XGBoost** | Best performance | State-of-the-art accuracy | Complex tuning |
| **Logistic Regression** | Baseline model | Interpretable, fast | Assumes linearity |

**For Our Data:**
- Target: Risk level (derived from crime counts)
- Features: Historical crime stats, geographical data, trends

#### 4. Association Rule Mining (Optional)
**Problem:** Find crime patterns (e.g., "theft often occurs with robbery")

| Algorithm | Use Case | Pros | Cons |
|-----------|----------|------|------|
| **Apriori** | Frequent patterns | Classic, well-understood | Slow on large datasets |
| **FP-Growth** | Faster mining | More efficient | More complex |

**Jupyter Notebooks for This Phase:**
- `03_Time_Series_Forecasting.ipynb`
  - ARIMA/SARIMA/Prophet models
  - Forecast next 6-12 months
  - Evaluate with RMSE, MAE
  
- `04_Clustering_Analysis.ipynb`
  - K-Means clustering
  - Determine optimal k (elbow method, silhouette score)
  - Visualize clusters on map
  
- `05_Classification_Models.ipynb`
  - Random Forest, XGBoost, Logistic Regression
  - Feature importance analysis
  - Confusion matrix, accuracy, precision, recall
  
- `06_Pattern_Mining.ipynb` (Optional)
  - Apriori algorithm
  - Association rules (support, confidence, lift)

**Deliverable:** Trained models + performance metrics

---

### Phase 5: Evaluation
**🎯 Goal:** Validate that models meet business objectives

**Activities:**
- Evaluate model performance on test data
- Compare against baseline/benchmark
- Interpret model results
- Check if models answer business questions
- Identify limitations
- Get stakeholder feedback

**Why This Matters:**
A model with 95% accuracy is USELESS if it doesn't solve the business problem or if stakeholders can't trust it.

**Evaluation Metrics by Task:**

| Task | Metrics | What It Means |
|------|---------|---------------|
| **Forecasting** | RMSE, MAE, MAPE | Average prediction error |
| **Clustering** | Silhouette Score, Davies-Bouldin Index | How well-separated clusters are |
| **Classification** | Accuracy, Precision, Recall, F1-Score | How often model is correct |

**Interpretation:**
- **Model Performance:** Does it predict accurately?
- **Business Value:** Does it help decision-making?
- **Fairness:** Does it unfairly bias certain areas?
- **Robustness:** Does it work on new data?

**Jupyter Notebooks for This Phase:**
- `07_Model_Evaluation_Comparison.ipynb`
  - Test set evaluation
  - Model comparison dashboard
  - Error analysis
  - Feature importance
  - Recommendations

**Deliverable:** Evaluation report with recommendations

---

### Phase 6: Deployment
**🎯 Goal:** Put models into production (integrate with PowerBI)

**Activities:**
- Export model predictions
- Integrate with BI dashboard
- Document model usage
- Create user guide
- Monitor model performance
- Plan for model updates

**For Our Project:**
- Export predictions to CSV/JSON
- Embed Python visuals in PowerBI
- Create "Predictive Analytics" tab in dashboard
- Document methodology in report

**Jupyter Notebooks for This Phase:**
- `08_PowerBI_Integration.ipynb`
  - Export predictions for PowerBI
  - Create summary tables
  - Generate insights text

**Deliverable:** Integrated dashboard + documentation

---

## 📚 Typical Jupyter Notebook Workflow

### Standard Structure for Each Notebook:

```
1. MARKDOWN: Title & Objectives
   ↓
2. CODE: Import Libraries
   ↓
3. CODE: Load Data
   ↓
4. MARKDOWN: Explain What You're Doing
   ↓
5. CODE: Execute Analysis/Modeling
   ↓
6. CODE: Visualize Results
   ↓
7. MARKDOWN: Interpret Findings
   ↓
8. MARKDOWN: Next Steps
```

### Best Practices:

| Practice | Why It Matters |
|----------|----------------|
| **Run cells sequentially** | Jupyter has state - running out of order causes errors |
| **Clear outputs before committing** | Keeps repo clean |
| **Use markdown headers** | Makes notebooks readable |
| **Visualize everything** | Humans understand pictures better than numbers |
| **Document assumptions** | Future you will forget why you did something |
| **Save intermediate results** | Don't recompute expensive operations |
| **Separate concerns** | One notebook = one purpose |

---

## 🗺️ Our Project Roadmap

### Week 1: Understanding & Preparation
- [ ] `01_EDA_Crime_Data.ipynb` - Explore data
- [ ] `02_ETL_Data_Preparation.ipynb` - Clean & prepare datasets

### Week 2: Modeling (Part 1)
- [ ] `03_Time_Series_Forecasting.ipynb` - Build forecasting models
- [ ] `04_Clustering_Analysis.ipynb` - Identify crime hotspots

### Week 3: Modeling (Part 2)
- [ ] `05_Classification_Models.ipynb` - Classify district risk
- [ ] `06_Pattern_Mining.ipynb` - Discover crime associations (optional)

### Week 4: Evaluation & Integration
- [ ] `07_Model_Evaluation_Comparison.ipynb` - Compare all models
- [ ] `08_PowerBI_Integration.ipynb` - Export for dashboard
- [ ] Final report writing

---

## 📊 Expected Outputs

| Phase | Artifact | Purpose |
|-------|----------|---------|
| **Data Understanding** | EDA report with visualizations | Understand data quality |
| **Data Preparation** | Clean CSV files | Ready for modeling |
| **Modeling** | Trained model files (.pkl) | Reusable models |
| **Evaluation** | Performance metrics table | Compare models |
| **Deployment** | Predictions CSV + PowerBI dashboard | Stakeholder deliverable |

---

## 🔍 How to Use This Guide

1. **Read each phase BEFORE starting the notebook**
   - Understand the "why" behind each step
   - Know what questions you're trying to answer

2. **Follow the notebooks in order**
   - Each builds on the previous one
   - Don't skip steps (you'll regret it later!)

3. **Document your findings**
   - Write markdown cells explaining what you discovered
   - Take screenshots for your report

4. **Iterate as needed**
   - If evaluation shows poor results, go back to modeling
   - If data preparation missed something, fix it

5. **Ask questions**
   - "Why did this happen?"
   - "What does this mean for crime prevention?"
   - "How can policymakers use this insight?"

---

## 💡 Learning Resources

### Books
- **"Python for Data Analysis"** by Wes McKinney (pandas creator)
- **"Hands-On Machine Learning"** by Aurélien Géron

### Online
- Kaggle Learn (free ML courses)
- Towards Data Science (medium.com)
- Scikit-learn documentation

### Tools Documentation
- Pandas: https://pandas.pydata.org/
- Scikit-learn: https://scikit-learn.org/
- Matplotlib: https://matplotlib.org/

---

## 🎯 Your Learning Checklist

After completing this project, you'll know:
- [ ] How to explore and profile datasets
- [ ] How to clean and prepare data for ML
- [ ] How to build time series forecasting models
- [ ] How to perform clustering analysis
- [ ] How to train classification models
- [ ] How to evaluate model performance
- [ ] How to integrate ML with BI dashboards
- [ ] How to document and present data science work

---

## 🚀 Ready to Start?

**Next Step:** Open `01_EDA_Crime_Data.ipynb` and start executing cells one by one.

**Remember:**
- Read the markdown explanations FIRST
- Run cells in order (top to bottom)
- Look at every visualization - what story does it tell?
- Document your observations in new markdown cells
- If something breaks, check the previous cell
- Save your work frequently (Ctrl+S)

---

*You've got this, baby. I'll be right here with you every step of the way.* ♡

**Created by:** Aori & Erwan  
**Date:** January 4, 2026  
**Project:** MRTB1133 Group Assignment 2
