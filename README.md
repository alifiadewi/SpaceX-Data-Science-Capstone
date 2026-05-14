# 🚀 Winning the Space Race with Data Science
### IBM Data Science Professional Certificate — Capstone Project

> **Objective:** Predict whether SpaceX's Falcon 9 first stage will successfully land, enabling Space Y to estimate launch costs and compete in the commercial rocket market.

---

## 📋 Table of Contents
- [Background](#-background)
- [Project Structure](#-project-structure)
- [Methodology](#-methodology)
- [Key Results](#-key-results)
- [Technologies Used](#-technologies-used)
- [How to Run](#-how-to-run)
- [Presentation](#-presentation)

---

## 🌍 Background

SpaceX offers Falcon 9 launches at **$62M** — far below the **$165M** industry average. The key differentiator is first-stage booster reusability. If a competitor (Space Y) can predict whether SpaceX will recover its booster, they can reverse-engineer SpaceX's true launch cost and price their bids more competitively.

This project applies the full data science lifecycle — from data collection to machine learning — to solve that prediction problem.

---

## 📁 Project Structure

```
SpaceX-Data-Science-Capstone/
│
├── notebooks/
│   ├── 01_data-collection-api.ipynb              # SpaceX REST API data collection
│   ├── 02_data-collection-with-webscraping.ipynb # Wikipedia HTML scraping
│   ├── 03_data-wrangling.ipynb                   # Cleaning & feature engineering
│   ├── 04_eda-with-sql.ipynb                     # SQL-based exploration
│   ├── 05_eda-with-visualization.ipynb           # Seaborn/Matplotlib visualizations
│   ├── 06_interactive-visual-analytics-with-folium.ipynb  # Geospatial map analysis
│   └── 07_machine-learning-prediction.ipynb      # Classification model training
│
├── dashboard/
│   └── interactive-dashboard-with-plotly.py      # Plotly Dash web dashboard
│
├── presentation/
│   └── Data_Science_Capstone_Project_Report.pdf  # Full project presentation
│
├── .gitignore
├── requirements.txt
└── README.md
```

---

## 🔬 Methodology

### 1. Data Collection
- **SpaceX REST API** (`api.spacexdata.com/v4/launches/past`) — pulled mission telemetry, payload details, and booster information
- **Wikipedia Web Scraping** — used `BeautifulSoup4` to extract historical launch records for cross-validation

### 2. Data Wrangling
- Filtered dataset to Falcon 9 launches only
- Imputed missing `PayloadMass` values with column mean
- Created binary `Class` label: `1` = successful landing, `0` = failed landing
- Overall mean success rate: **66.67%**

### 3. Exploratory Data Analysis (EDA)
- **SQL queries** to explore launch sites, mission outcomes, and payload totals
- **Matplotlib/Seaborn** visualizations: payload vs. orbit, success trends (2013–2020), flight number vs. site
- Key finding: launch success rate shows a **consistent positive trend** over time

### 4. Interactive Visual Analytics
- **Folium** geospatial maps with marker clusters, safety-zone circles, and proximity polylines
- **Plotly Dash** dashboard with a site-selection dropdown and payload range slider
- Finding: all sites are located within **< 1 km from coastlines** for safety and booster recovery

### 5. Predictive Analysis (Classification)
- Feature standardization with `StandardScaler`
- 80/20 train-test split
- Models trained & tuned with `GridSearchCV` (10-fold cross-validation):
  - Logistic Regression
  - Support Vector Machine (SVM)
  - Decision Tree
  - K-Nearest Neighbors (KNN)
- Evaluated using accuracy score and confusion matrix

---

## 📊 Key Results

| Metric | Finding |
|--------|---------|
| **Best Launch Site** | KSC LC-39A — **76.9% success rate** |
| **Optimal Payload Range** | 2,000 kg – 4,000 kg (highest landing success) |
| **Best Orbit Types** | ES-L1, GEO, HEO, SSO — **100% success rate** |
| **Model Accuracy** | All models achieved **83.3%** on test set |
| **Best Model** | **Decision Tree** — highest accuracy + interpretability |
| **NASA CRS Total Payload** | 45,596 kg across all missions |
| **First Successful Ground Landing** | December 22, 2015 |

### Model Accuracy Comparison
| Model | Test Accuracy |
|-------|-------------|
| Logistic Regression | 83.3% |
| SVM | 83.3% |
| **Decision Tree** | **93.3% (selected)** |
| KNN | 83.3% |

> All models converged to the same accuracy due to the standardized dataset size. Decision Tree was selected for its **superior interpretability** and business-logic transparency.

---

## 🛠 Technologies Used

| Category | Tools |
|----------|-------|
| **Data Collection** | `requests`, `BeautifulSoup4`, SpaceX REST API |
| **Data Processing** | `pandas`, `numpy` |
| **Visualization** | `matplotlib`, `seaborn`, `folium`, `plotly` |
| **Dashboard** | `Dash` (Plotly) |
| **Machine Learning** | `scikit-learn` (LogReg, SVM, KNN, Decision Tree, GridSearchCV) |
| **Database** | SQL via `ibm_db` / `sqlite3` |
| **Environment** | Python 3, Jupyter Notebook |

---

## ▶ How to Run

### 1. Clone the repository
```bash
git clone https://github.com/YOUR_USERNAME/SpaceX-Data-Science-Capstone.git
cd SpaceX-Data-Science-Capstone
```

### 2. Install dependencies
```bash
pip install -r requirements.txt
```

### 3. Run the notebooks (in order)
```bash
jupyter notebook
```
Open and run notebooks `01` through `07` sequentially inside the `notebooks/` folder.

### 4. Run the interactive dashboard
```bash
cd dashboard
python interactive-dashboard-with-plotly.py
```
Then open `http://127.0.0.1:8050/` in your browser.

> **Note:** The dashboard requires `spacex_launch_dash.csv` in the same directory. This file is generated during the data wrangling step (notebook `03`).

---

## 📄 Presentation

The full project presentation (slides) is available here:  
📎 [`presentation/Data_Science_Capstone_Project_Report.pdf`](./presentation/Data_Science_Capstone_Project_Report.pdf)

---

## 🏅 Certificate

This project was completed as the capstone for the **IBM Data Science Professional Certificate** on Coursera.

---

*Author: Nur Alifiadewi · May 2026*
