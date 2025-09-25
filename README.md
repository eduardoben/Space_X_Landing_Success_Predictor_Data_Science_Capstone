# Space X Landing Success Predictor — Data Science Capstone

## Abstract
This project delivers an end-to-end data science workflow around SpaceX Falcon 9 launches, with the primary objective of **prediction**: modeling the probability that the first stage successfully lands based on launch characteristics (payload mass, orbit, launch site, flight number, etc.). The work spans data collection (API + scraping), cleaning and feature engineering, EDA (visual and SQL), geospatial analysis, supervised learning for classification, and an **interactive Plotly Dash dashboard** for stakeholders to explore patterns and model insights.

---

## Introduction
Reusable rockets have reshaped launch economics, and Falcon 9 first-stage landings are central to that shift. Predicting landing success has value for understanding operational drivers and for building educational data apps. This capstone organizes a transparent pipeline—from raw external sources to a runnable dashboard—so others can reproduce results and extend the models.

---

## Dataset
- **Sources**
  - SpaceX REST API (programmatic launch metadata).
  - Public web pages (HTML tables) scraped to enrich attributes such as orbit or site-level context.
- **Derived Tables**
  - Cleaned, merged datasets after wrangling and feature engineering (e.g., standardized dates, binned payloads, categorical encodings).
- **Target Variable**
  - First-stage landing outcome (success vs. non-success).

> All collection and processing steps are reproducible through the notebooks listed in **Reproduction Steps** below.

---

## Methodology
1. **Data Collection**
   - Pull structured launch data via the SpaceX API.
   - Scrape supplementary fields from public pages; normalize and align schemas.
2. **Wrangling & Feature Engineering**
   - Handle missing values, normalize units and categories, and derive predictors (e.g., payload bins, cumulative flight number).
3. **Exploratory Data Analysis**
   - Visual EDA (distributions, relationships).
   - SQL EDA (aggregations/joins) to validate assumptions.
4. **Geospatial Analysis**
   - Folium maps to visualize launch sites and outcomes.
5. **Modeling**
   - Compare several classifiers (e.g., Logistic Regression, Decision Tree/KNN/SVM or equivalent).
   - Cross-validation and hold-out evaluation with clear metrics.
6. **Delivery**
   - Plotly Dash app for interactive exploration of findings and model behavior.

---

## Evaluation Metrics
We report the following for model selection and comparison:
- Accuracy
- Precision, Recall, and F1-score (per class and macro/weighted)
- (Optional) ROC-AUC for threshold-independent performance

> Emphasis can be tuned depending on stakeholder goals (e.g., prioritize Recall to minimize false negatives).

---

## Results
Summarize and/or paste your final metrics here after running the modeling notebook (see **Reproduction Steps**). A suggested table format:

| Metric                | Logistic Regression | Decision Tree | KNN     | SVM     |
|----------------------:|---------------------|---------------|---------|---------|
| Overall Accuracy      | —                   | —             | —       | —       |
| Precision (Success)   | —                   | —             | —       | —       |
| Recall (Success)      | —                   | —             | —       | —       |
| F1 (Success)          | —                   | —             | —       | —       |
| ROC-AUC (optional)    | —                   | —             | —       | —       |

**Conclusion (template):**  
Briefly interpret which model performed best and why (e.g., most balanced Precision/Recall, best ROC-AUC), and relate that to operational relevance.

---

## Limitations and Future Work
- Potential label noise or schema drift across sources.
- Limited covariates—external factors (weather, vehicle configuration) may improve performance.
- **Future**:
  - Add calibrated probabilities and cost-sensitive learning.
  - Integrate SHAP for model explainability in the dashboard.
  - Automate data pulls and packaging (CLI + Docker).
  - Track experiments with MLflow and persist best models.

---

## Repository Structure
```
Data_Science_Capstone/
├─ Build a Dashboard with Plotly Dash.py
├─ Data_Collection_SpaceX_API.ipynb
├─ Data Collection - Scraping.ipynb
├─ Data Wrangling.ipynb
├─ EDA with Data Visualization.ipynb
├─ EDA with SQL.ipynb
├─ Launch Sites Locations Analysis with Folium.ipynb
├─ Predictive Analysis (Classification).ipynb
├─ Capstone_Results_Report.pdf
└─ Capstone_Results_Report.pptx
```

---

## Quickstart

### 1) Clone
```bash
git clone https://github.com/eduardoben/Data_Science_Capstone.git
cd Data_Science_Capstone
```

### 2) Environment
Create and activate a clean environment (conda shown; `python -m venv .venv` also works):
```bash
conda create -n spacex-capstone python=3.10 -y
conda activate spacex-capstone
```

### 3) Install Dependencies
(If you don’t yet provide `requirements.txt`, install common libs used across notebooks/app.)
```bash
pip install pandas numpy scikit-learn matplotlib seaborn plotly dash folium             requests beautifulsoup4 lxml sqlalchemy ipython-sql
# Optional for mapping/geocoding
pip install geopy shapely
```

---

## Reproduction Steps
Run the notebooks in order (save outputs so downstream steps can read artifacts):

1. **Data_Collection_SpaceX_API.ipynb** — API data pull  
2. **Data Collection - Scraping.ipynb** — HTML scraping and normalization  
3. **Data Wrangling.ipynb** — cleaning, merging, feature engineering  
4. **EDA with Data Visualization.ipynb** — visual EDA  
5. **EDA with SQL.ipynb** — SQL-based EDA  
6. **Launch Sites Locations Analysis with Folium.ipynb** — geospatial views  
7. **Predictive Analysis (Classification).ipynb** — model training & evaluation

---

## Interactive Dashboard
Run locally:
```bash
python "Build a Dashboard with Plotly Dash.py"
```
Then open the printed local URL (default: http://127.0.0.1:8050) to interact with filters and plots.

---

## License
**MIT** (recommended). Add a `LICENSE` file at the repository root if not already present.
