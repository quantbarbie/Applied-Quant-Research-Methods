# Applied Quant Research Methods: HFT case study

## Objective
This project aims to process, analyze, and model AAPL trading data. The analysis involves cleaning, resampling, feature engineering, and modeling using various machine learning techniques to predict stock price movements and derive insights.

---

## Key Components

### 1. Data Preprocessing
- **Datasets**:
  - **Trade Price Data**: Includes columns `size` (volume) and `price`.
  - **Bid-Ask Data**: Includes columns `bid`, `ask`, `bidsiz`, and `asksiz`.
- **Processing Steps**:
  - Converted timestamps to `datetime` format and set as the index.
  - Removed invalid entries (e.g., `0` or `NaN` values).
  - Resampled data at 1-second intervals and filled missing values.
  - Filtered for regular trading hours (09:30 to 16:00).

---

### 2. Exploratory Data Analysis (EDA)
- **Descriptive Statistics**:
  - Summary statistics showed the distribution of trade sizes, prices, and bid-ask values.
  - Highlighted high skewness and kurtosis in `size`, `bidsiz`, and `asksiz`.
- **Visualizations**:
  - Plotted time series of `price`, `bid`, and `ask`.
  - Histograms for all variables.
  - Correlation heatmap revealed strong relationships between `price`, `bid`, and `ask`.

---

### 3. Feature Engineering
- **Derived Features**:
  - **Bid-Ask Spread**: Difference between `ask` and `bid`.
  - **Volatility**: Rolling standard deviation over 5-second and 10-second windows.
  - **Volume Imbalance**: Difference between `bidsiz` and `asksiz`.
  - **Lagged Features**: 1-second and 3-second lagged volumes.
  - **Time-Based Features**: `hour` and `minute`.

---

### 4. Modeling
#### Regression Models
- **Objective**: Predict `price` using engineered features.
- **Models**:
  - **Linear Regression**: Achieved high accuracy with `R² = 0.995`.
  - **Ridge Regression**: Slightly lower performance than linear regression.
  - **Lasso and Elastic Net**: Struggled with over-regularization.
- **Advanced Models**:
  - **Decision Tree and Random Forest**: High accuracy with Random Forest achieving `R² = 0.998`.
  - **GBM and XGBoost**: Strong performance with XGBoost achieving `R² = 0.9986`.

#### Classification Models
- **Objective**: Predict binary price direction (up/down).
- **Models**:
  - **Logistic Regression**: Moderate accuracy (`~55%`).
  - **Decision Tree, Random Forest, GBM, and XGBoost**: Gradual improvement with GBM achieving the best accuracy (`~61%`).

#### Clustering
- **Objective**: Group data into clusters for pattern recognition.
- **Algorithms**:
  - **K-Means**: Achieved the best silhouette score (`0.46`).
  - **Hierarchical and DBSCAN**: Lower scores due to noise sensitivity.
  - **Gaussian Mixture Model**: Struggled to separate clusters.

#### SVM and k-NN
- **Support Vector Regression**:
  - Linear SVM outperformed RBF kernel with `R² = 0.959`.
- **k-Nearest Neighbors**:
  - Achieved `R² = 0.990` with low MSE.

---

### 5. Extended Analysis
- **Comparative Analysis**:
  - Processed and analyzed data from additional dates (`11-02` and `11-27`).
  - Ensured alignment of time intervals and resampling frequencies.
  - Filtered for regular trading hours to maintain consistency.
- **Results**:
  - Observed consistent trading patterns and price trends across dates.
  - Slight variations in mean and volatility indicated different market conditions.

---

### 6. Key Insights
- **Price Prediction**:
  - Random Forest and XGBoost models are highly effective for short-term price prediction.
  - Feature engineering, especially volatility and lagged volumes, significantly improved model performance.
- **Market Patterns**:
  - High bid-ask spreads and volume imbalance correlate with price volatility.
  - Time-based features reveal intraday trading patterns.

---
