# Energia Trading Strategy Optimisation

##  Overview
This project focuses on designing and evaluating trading strategies for Energia in the Irish Single Electricity Market (ISEM).  

The objective is to minimise the cost of purchasing **100MW of electricity every 30 minutes**, by selecting the optimal market among:
- DAM (Day Ahead Market)
- IDA1, IDA2, IDA3 (Intraday Markets)
- BM (Balancing Market)

The project is split into two parts:
- **Part 1:** With forecast data available  
- **Part 2:** Without forecast data  

---

##  Key Results

### Part 1 (With Forecasts)
-  Random Forest model achieved **within 4.11% of optimal cost**
-  ~€1.24M difference from optimal strategy
- Rule-based strategies lagged significantly (~43% worse)

### Part 2 (Without Forecasts)
-  Random Forest model achieved **within 18.2% of optimal cost**
-  ~€4.17M difference from optimal strategy
-  Performance dropped significantly without forecasts

---

## Key Insights
- **Balancing Market (BM)** is most frequently the cheapest, but highly volatile  
- Higher wind → lower prices  
- Higher net demand → higher prices  
-  Forecast accuracy is critical for optimal decision-making  
- Forecast errors strongly influence when BM becomes favourable  

---

##  Methodology

### 1. Data Preprocessing
- Merged multiple datasets using timestamps
- Engineered key features:
  - Net Demand (`Demand - Wind`)
  - Time-based features (hour, day, month, weekend)
  - Lagged prices (D-1 data)
- Created:
  - Forecast differences
  - Forecast error features (Part 1 only)

---

### 2. Exploratory Data Analysis (EDA)
- Identified relationships between:
  - Time of day and prices
  - Wind / demand and market behaviour
- Discovered:
  - Strong daily and seasonal trends
  - Volatility patterns in the balancing market

---

### 3. Trading Strategies

####  Strategy 1: Rule-Based Approach
- Built using insights from EDA
- Included:
  - Time-of-day rules
  - Demand and wind conditions
  - Market prioritisation logic

---

####  Strategy 2: Hybrid Approach
- Rule-based system enhanced with a classifier
- Random Forest used to predict when BM is optimal

---

#### Strategy 3: Machine Learning Model
- Random Forest classifier predicting the cheapest market
- Trained using only **D-1 available data**
- Captures complex, non-linear relationships

---

##  Constraints
- No access to future data at decision time (D-1 constraint)
- Forecasts may be inaccurate
- Energy cannot be stored
- Market rules changed between Part 1 and Part 2

---

## Results Comparison

| Strategy              | Part 1 Performance | Part 2 Performance |
|----------------------|------------------|------------------|
| Rule-Based           | ~43% from optimal | ~43.7% from optimal |
| Hybrid               | ~41% from optimal | — |
| Random Forest        | **4.11% from optimal** | **18.2% from optimal** |

---

##  Key Takeaways
- Machine learning significantly outperforms rule-based strategies
- Forecast data is **critical** for high performance
- Market behaviour is highly dependent on:
  - Time
  - Demand
  - Wind conditions
- Volatility in BM presents both opportunity and risk

---

##  Tech Stack
- Python
- Pandas
- Scikit-learn (Random Forest)
- Matplotlib / Seaborn

---


---

##  Future Improvements
- Improve forecast accuracy using advanced models
- Explore time-series models (e.g. LSTM, ARIMA)
- Incorporate probabilistic forecasting
- Develop real-time trading system

---

##  Author
**Andrew Scott**
