# 🗽 NYC Taxi Tip Amount Analysis and Prediction

This repository presents our final research project for NYU's Advanced Python course, focused on analyzing and predicting tip amounts in New York City taxi rides. Using a large-scale dataset from the NYC Taxi & Limousine Commission (TLC), we explore how temporal, spatial, and fare-related factors influence tipping behavior.

## 🚦 Problem Statement

Tip amounts are a subtle yet economically significant aspect of urban transportation. Unlike fixed fares, gratuities vary due to complex, context-dependent variables—trip distance, timing, surcharges, and location. We aim to build a predictive model for tip amounts, enabling better service strategies, data-driven insights for drivers, and fairness for passengers.

---

## 👥 Team Members

- **Adam Xu** (Data Preprocessing) – [tx543@nyu.edu](mailto:tx543@nyu.edu)  
- **Zipei Wang** (Data Preprocessing) – [zw2458@nyu.edu](mailto:zw2458@nyu.edu)  
- **Ziyu Qi** (Data Preprocessing) – [zq2127@nyu.edu](mailto:zq2127@nyu.edu)  
- **Chenxin Gu** (Modeling & Optimization) – [cg3423@nyu.edu](mailto:cg3423@nyu.edu)  
- **Junwen Fang** (Modeling & Optimization) – [jf3994@nyu.edu](mailto:jf3994@nyu.edu)  

---

## 🧹 Data Preprocessing

- **Source**: [NYC TLC 2024 Trip Record Data](https://www.nyc.gov/site/tlc/about/tlc-trip-record-data.page)
- **Initial Size**: ~3.6 million records
- **Cleaning**: Removed missing, zero-tip, and top 2% outlier entries
- **Transformation**:
  - Standardized numeric features
  - One-hot encoded categorical variables
  - Engineered time/location flags
- **Selection**:
  - Dropped highly correlated & low-variance fields
  - Applied Lasso regression for final feature reduction

---

## 📊 Modeling Approach

We benchmarked multiple models and loss functions. Results:

| Model           | R² Score | RMSE  |
|----------------|----------|--------|
| OLS Regression | 0.42     | ~2.0   |
| XGBoost (SE)   | **0.69** | **1.60** |
| XGBoost (SLE)  | 0.66     | 1.66   |

**Best model**: XGBoost with Squared Error objective.

---

## ⚙️ Optimization Strategies

We applied several performance-enhancing strategies:

- Switched from hand-written loops to `xgboost.train()`
- Used **random search** over grid search to reduce complexity
- Enabled `tree_method='hist'` for faster split computation
- Combined sampling with `itertools.product` and additional regularization

⏱️ **Result**: 90% reduction in training time without sacrificing model accuracy.

---

## 🧪 Final Results (Full Dataset)

- **Dataset**: Cleaned 2024 NYC TLC, full scale (~10× larger)
- **Top Features**: Fare, trip distance, congestion surcharge, airport fee, time/location flags
- **Performance**:
  - `reg:squarederror`: R² = **0.7231**, RMSE = **1.5161**
  - `reg:squaredlogerror`: R² = 0.7098, RMSE = 1.5521
  - Avg. Training Time: 4.57s/trial

---

## 🔮 Future Directions

- Integrate weather and holiday data
- Reframe problem as classification (e.g., will tip > 20%?)
- Use SHAP for model interpretability
- Broaden fairness discussion around zero-tip behavior

---

## 📂 Repository Structure

├── data/ # Cleaned and processed datasets (excluded from repo)
├── src/
│ ├── preprocessing.py # Cleaning, transformation, selection
│ ├── modeling.py # Model training and evaluation
│ └── optimization.py # Hyperparameter tuning strategies
├── notebooks/ # EDA and experimentation notebooks
├── results/ # Visualizations and evaluation reports
└── README.md


---

## 📎 Resources

- NYC TLC Data Portal: [https://www.nyc.gov/site/tlc/about/tlc-trip-record-data.page](https://www.nyc.gov/site/tlc/about/tlc-trip-record-data.page)

---

## 🔗 Project Link

Code and documentation are available at:  
👉 [https://github.com/EllieWzp/advanced_python_final](https://github.com/EllieWzp/advanced_python_final)

---

## 📅 Date

**May 6, 2025**
