# Coffee Production Forecasting: A Time-Series Machine Learning Approach

## 🎯 Project Overview

This project develops a **machine learning pipeline for forecasting annual coffee production** across the world's top 5 coffee-producing nations (Brazil, Colombia, Vietnam, Indonesia, Ethiopia). Using historical data from 1960-2025, we build predictive models that significantly outperform baseline methods, achieving **73.5% reduction in RMSE** compared to naive forecasting.

## ✨ Key Innovations & Highlights

### 🔬 **Rigorous Temporal Validation**
- **Strict time-series cross-validation** using `TimeSeriesSplit` to prevent data leakage
- **Per-country lag feature engineering** ensuring no cross-country contamination
- **Temporal split verification** confirming each country's data is properly segmented chronologically

### 📊 **Comprehensive Model Interpretability**
- **Three distinct global feature importance methods**:
  - Linear coefficients (Ridge) - directional importance
  - MDI importance (Random Forest) - structural importance  
  - Permutation importance (XGBoost) - predictive power
- **SHAP values** for local feature importance explanations
- **Detailed feature analysis** identifying most/least important predictors

### 🏆 **Model Performance**
- **Best Model**: Lasso Regression (RMSE: 3,964.47)
- **73.5% improvement** over baseline (DummyRegressor)
- **8.06 standard deviations** above baseline performance
- Benchmarked 4 algorithms: 2 linear (Ridge, Lasso) and 2 non-linear (Random Forest, XGBoost)

### 🌍 **Domain Knowledge Integration**
- **Stock-to-Use (STU) Ratio**: Domain-specific feature capturing supply tightness
- **Multi-lag features**: 1, 2, and 3-year lags capturing biennial production cycles
- **Focus on top 5 producers**: Captures 80%+ of global production while reducing noise

## 📈 What We Built

### Problem Statement
Predict annual coffee production for major producing nations to support:
- Global supply chain optimization
- Price stability forecasting
- Agricultural planning and policy decisions

### Solution Approach
1. **Data Engineering**: Transform long-format USDA data into wide format with lag features
2. **Feature Engineering**: Create domain-specific features (STU ratio) and temporal lags
3. **Model Training**: Benchmark multiple algorithms with strict temporal validation
4. **Model Interpretation**: Comprehensive feature importance analysis using multiple methods
5. **Performance Evaluation**: Compare against baseline with statistical significance testing

## 🛠️ Technical Implementation

### Dataset
- **Source**: USDA Production, Supply and Distribution (PSD) Database
- **Scale**: 85,937 records, 94 countries, 66 years (1960-2025)
- **Focus**: Top 5 producers (Brazil, Colombia, Vietnam, Indonesia, Ethiopia)
- **Attributes**: 19 market metrics (production, consumption, trade, stocks)

### Methodology
- **Task Type**: Time-Series Regression
- **Evaluation Metric**: RMSE (Root Mean Squared Error)
- **Validation Strategy**: TimeSeriesSplit (5 folds) + 80/20 temporal hold-out
- **Feature Engineering**: 
  - Lag features (1, 2, 3 years) calculated per-country
  - Stock-to-Use ratio (domain knowledge feature)
  - 18 lag features total

### Models Evaluated
1. **Lasso (Linear)** - Best performer (RMSE: 3,964.47)
2. **Ridge (Linear)** - RMSE: 4,324.53
3. **Random Forest (Non-linear)** - RMSE: 4,754.57
4. **XGBoost (Non-linear)** - RMSE: 4,903.39

### Key Findings
- **Linear models outperform non-linear**: Lasso achieves best RMSE, suggesting primarily linear relationships
- **Lag-2 and Lag-3 features dominate**: Validates biennial production cycles (especially Brazil)
- **Exports more predictive than domestic consumption**: International trade dynamics crucial
- **Feature importance varies by model**: Different models capture different aspects of production dynamics

## 📁 Project Structure & Reproducibility

```
coffee_or_tea/
├── data/                            # Raw and preprocessed data
│   └── psd_coffee.csv               # Raw USDA PSD coffee data
├── figures/                         # All generated figures (300 dpi)
│   ├── production_trends.png        # Time series trends by country
│   ├── correlation_heatmap.png      # Feature correlation analysis
│   ├── autocorrelation_brazil.png   # Temporal dependency validation
│   ├── fig1_dist_comparison.png     # Target distribution (original vs log)
│   ├── prediction_vs_actual.png     # Model predictions vs actual values
│   ├── shap_summary.png             # SHAP feature importance
│   ├── model_performance_comparison.png      # Model benchmarking
│   └── comprehensive_feature_importance.png  # Three-method comparison
├── results/                         # Model outputs and metrics
│   └── model_comparison.csv         # Cross-validated performance summary
├── report/                          # Final report (PDF and any LaTeX sources)
├── src/                             # Source code and notebooks
│   └── coffee_production_pipeline.ipynb
├── .gitignore
├── LICENSE                          # Project license (MIT)
├── requirements.txt                 # Python package requirements (pip)
├── environment.yml                  # Conda environment for full reproducibility
└── README.md
```

### Environment & Versions

- **Python version**: 3.10 (tested)
- **Environment file**: `environment.yml` (conda)  
  - Provides exact Python version and all required packages so others can recreate the environment with:

```bash
conda env create -f environment.yml
conda activate coffee_or_tea
```

- **Package requirements (pip)**: `requirements.txt`
  - Mirrors the same dependencies for users who prefer `venv` + `pip`.

## 🚀 Quick Start

### Prerequisites
- Python 3.8+
- Jupyter Notebook

### Installation

```bash
# Clone or download the project
cd coffee_or_tea

# Create virtual environment
python -m venv venv
source venv/bin/activate  # On Windows: venv\Scripts\activate

# Install dependencies
pip install -r requirements.txt

# Launch Jupyter Notebook
jupyter notebook src/coffee_production_pipeline.ipynb
```

### Running the Pipeline

1. **Data Loading** (Cell 3): Load and inspect USDA coffee data
2. **EDA** (Cell 4): Explore production trends and correlations
3. **Feature Engineering** (Cell 5): Create lag features and STU ratio
4. **Data Splitting** (Cell 6): Temporal train/test split with verification
5. **Model Training** (Cell 7): Train and benchmark 4 models
6. **Visualization** (Cell 8): Generate predictions and SHAP plots
7. **Analysis** (Cell 9): Comprehensive results discussion

## 📊 Results Summary

| Model | RMSE | Improvement | Std Devs Above Baseline |
|-------|------|-------------|-------------------------|
| **Lasso (Linear)** | **3,964.47** | **73.5%** | **8.06** |
| Ridge (Linear) | 4,324.53 | 71.1% | 11.59 |
| Random Forest | 4,754.57 | 68.2% | 13.35 |
| XGBoost | 4,903.39 | 67.2% | 7.11 |
| Baseline | 14,956.49 | - | - |

## 🔍 Key Features

- ✅ **No Data Leakage**: Strict temporal validation ensures future data never used for past predictions
- ✅ **Per-Country Lagging**: Features calculated within each country's timeline
- ✅ **Multiple Interpretability Methods**: Three global + one local (SHAP) feature importance
- ✅ **Domain Knowledge**: STU ratio captures agricultural supply dynamics
- ✅ **Comprehensive Evaluation**: Baseline comparison with statistical significance testing

## 📝 Requirements

See `requirements.txt` for full dependencies. Key packages:
- pandas, numpy (data manipulation)
- scikit-learn (machine learning)
- xgboost (gradient boosting)
- shap (model interpretability)
- matplotlib, seaborn (visualization)

## 📚 References

- **Dataset**: USDA Foreign Agricultural Service (FAS) Production, Supply and Distribution Database
- **Evaluation Framework**: Time-series cross-validation best practices
- **Interpretability**: SHAP (SHapley Additive exPlanations) for model explanations

## 👥 Authors

Machine Learning Project - Coffee Production Forecasting

---

**Note**: This project demonstrates best practices in time-series forecasting, including proper temporal validation, feature engineering, and comprehensive model interpretability analysis.
