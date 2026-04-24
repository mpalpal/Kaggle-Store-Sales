# Store Sales - Time Series Forecasting

This repository contains my solution for the Kaggle competition:  

https://www.kaggle.com/competitions/store-sales-time-series-forecasting

---

## Overview

The goal of this competition is to predict sales for the Ecuadorian retailer Corporation Favorita using time series forecasting. Accurate forecasts help optimize inventory and improve customer satisfaction.

This notebook builds a robust forecasting pipeline that emphasizes **"Store Maturity"**—the idea that the number of years a store has been operating significantly influences its sales patterns and stability.

The final prediction is generated using a sophisticated **Linear Regression** model incorporating time-based features and store-specific metadata.

---

## Approach

### Feature Engineering: The Power of "Store Maturity"

The cornerstone of this solution is the creation of the **Store Maturity** feature. 
- **Rationale**: Newly opened stores often exhibit volatile sales as they establish a customer base, while older, "mature" stores show more stable, predictable seasonal patterns.
- **Implementation**: By calculating the number of years since each store's opening, the model can distinguish between these different growth phases, leading to more nuanced and accurate predictions.

### Data Preprocessing & Additional Features

- **Time-Based Features**: Extracted year, month, day of the week, and "days of the month" to capture seasonality.
- **Holiday Integration**: Incorporated national, regional, and local holidays to account for significant sales spikes.
- **Oil Prices**: Integrated daily oil prices as a proxy for Ecuador's economic health, which correlates with consumer spending power.
- **Log Transformation**: Applied to the target variable (`sales`) to stabilize variance and minimize the impact of outliers.

### Modeling Strategy

**Deterministic Process & Linear Regression**
- Used `DeterministicProcess` to capture the underlying time trend.
- Linear Regression was chosen for its interpretability and effectiveness in capturing the relationship between store characteristics (like Maturity) and sales volume.
- The model effectively combines "Time-step" features (trend) and "Lag" features (seasonal cycles).



---

## Result

- **Public Leaderboard Score (RMSLE):** 0.42599
- **Competition Status:** Ongoing / Learning Phase
- **Key Metric:** Root Mean Squared Logarithmic Error (RMSLE)

---

## Discussion

This project demonstrated that **domain-driven feature engineering** (like Store Maturity) can be just as powerful as complex algorithms. By recognizing that a store’s age acts as a proxy for its market penetration and operational stability, the model achieved a competitive score of **0.42599**.

Key takeaways:
1. **Economic Context Matters**: In the Ecuadorian market, external factors like oil prices provide a crucial "macro" signal that simple time-series models might miss.
2. **Simplicity vs. Complexity**: While many participants use boosted trees (XGBoost/LightGBM), a well-featured Linear Regression remains a strong baseline for time series, offering high interpretability and faster iteration.
3. **Maturity Signal**: The results confirmed that store age is a significant predictor of sales volume, helping the model generalize better across different store locations.

Future improvements will focus on implementing **Hybrid Models** (combining Linear Regression for trend and XGBoost for residuals) and exploring deeper moving average features to capture short-term fluctuations more precisely.

---

## License

This notebook is for educational purposes.  
The dataset belongs to the Kaggle competition and must be downloaded from the official Kaggle page.

## Data

Download the dataset from Kaggle:  

https://www.kaggle.com/competitions/store-sales-time-series-forecasting/data  

Kaggle Notebook:

https://www.kaggle.com/code/harukimurai/the-power-of-store-maturity
