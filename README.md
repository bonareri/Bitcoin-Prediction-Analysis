# Cryptocurrecncy Price Prediction and Risk Analysis
---

## 1. Introduction

This project aims to build a Cryptocurrency Price Prediction system to help traders and investors make data-driven decisions. Cryptocurrency markets are highly volatile, and predicting price movements can minimize risks, maximize profits, and enhance trading strategies.

Unlike traditional markets, cryptocurrencies operate 24/7 and are influenced by factors such as social media trends and global regulations. The project utilizes techniques such as:

- **Machine Learning Models** (LSTMs, Random Forest, XG-Boost, ARIMA, SARIMA, PROPHET)
- **Statistical Analysis** (Moving averages, time series analysis)

These techniques will provide accurate insights to aid cryptocurrency traders and investors.

---

## 2. Problem Statement 

Cryptocurrency prices are highly volatile, making it difficult for traders and investors to make informed decisions. This volatility leads to financial losses, market manipulation, and investment uncertainty. The project aims to address these challenges by predicting future prices using machine learning and statistical analysis, providing data-driven insights, and reducing uncertainty in cryptocurrency trading.

## 3. Objectives

This project aims to achieve the following goals:

- **Analyzing Historical Price Trends** – Study past price trends to understand market behavior and identify patterns.
- **Implementing Machine Learning Models for Prediction** – Develop and train models like LSTMs, Random Forest, and ARIMA to predict future cryptocurrency prices.
- **Evaluating Model Accuracy and Improving Predictions** – Assess the performance of different models and fine-tune them to improve prediction accuracy.

By accomplishing these objectives, the project will provide reliable and data-driven predictions for cryptocurrency price movements.


## 4. Data Collection and Preprocessing

### Data Source

The data for this project is sourced using the following APIs:

- **Price Data:**  
  - **Source:** Yahoo Finance API via the `yfinance` library  
  - **Data:** Open, high, low, close, and volume metrics.

### Features in the Dataset

The dataset includes the following key features:

- **Open** – The price at which the cryptocurrency opened during a specific time period.
- **Close** – The price at which the cryptocurrency closed during the specific time period.
- **High** – The highest price during the time period.
- **Low** – The lowest price during the time period.
- **Volume** – The total number of units traded during the time period.
- **Exponential Moving Averages (EMA):**
  - **EMA_50** – Short-term trend indicator (50-day EMA).
  - **EMA_200** – Long-term trend indicator (200-day EMA).
- **Daily Return:** Measures the percentage change in closing prices between consecutive days.
- **Relative Strength Index (RSI):** Identifies overbought (>70) or oversold (<30) conditions.

### Preprocessing Steps

To prepare the dataset for analysis and model training, the following preprocessing steps were performed:

- **Feature Engineering:** I created additional features such as Exponential Moving Averages (EMA_50, EMA_200), Daily Return, and RSI to gain deeper insights into the price trends.
- **Normalization/Standardization:** Since the 'Close' prices were not normally distributed, I applied the **Min-Max Scaler** to normalize the data. This transformed the values into a range between 0 and 1, ensuring the model could better learn from the data.
- **Splitting Data into Training & Testing Sets:** The data was split into **80% training** and **20% testing**. This division allowed the model to learn from the majority of the data while being evaluated on a separate testing set, ensuring it can generalize well to new, unseen data.

---

## 5. Exploratory Data Analysis

### Cryptocurrency Price Statistics 

|       | Close      | High       | Low        | Open       | Volume        | Market Cap      |
|-------|-----------|-----------|-----------|-----------|--------------|---------------|
| **count** | 8231.000000 | 8231.000000 | 8231.000000 | 8231.000000 | 8.231000e+03 | 8.231000e+03 |
| **mean**  | 9992.823821 | 10207.195049 | 9745.294258 | 9981.369649 | 1.341688e+10 | 2.547583e+11 |
| **std**   | 18816.012464 | 19201.542903 | 18371.163929 | 18793.123284 | 1.676706e+10 | 3.626204e+11 |
| **min**   | 0.515273   | 0.559759   | 0.505194   | 0.513391   | 6.520200e+05 | 2.516021e+08 |
| **25%**   | 196.810043  | 203.406967  | 188.855286  | 196.756042  | 1.290527e+09 | 1.974679e+10 |
| **50%**   | 1567.398682 | 1604.704102 | 1534.088257 | 1567.179321 | 7.186143e+09 | 1.079808e+11 |
| **75%**   | 8626.275391 | 8791.957031 | 8366.544922 | 8611.597656 | 2.021654e+10 | 3.330086e+11 |
| **max**   | 106146.265625 | 109114.882812 | 105291.734375 | 106147.296875 | 3.509679e+11 | 2.104267e+12 |

### Frequency Distribution

![image](https://github.com/user-attachments/assets/6533cda8-6ee6-4014-8beb-f055908a6ffa)

### Correlation Martix

![image](https://github.com/user-attachments/assets/2c4751e0-4b73-4b84-a3ac-862efc82e0df)

### Closing Price Over Time

![image](https://github.com/user-attachments/assets/29cb6e7b-f119-44f6-8a62-1c12c5f05df3)

**1️⃣ Bitcoin (BTC) Dominates Price Trends**
- **BTC (orange)** remains the highest-priced cryptocurrency.
- Surged past **$100,000 in 2024**, showing strong market confidence.
- **Historical peaks in 2017, 2021, and 2024** indicate repeated bull cycles.

**2️⃣ Ethereum (ETH) Shows Moderate Growth**
- **ETH (blue)** has a much lower price range compared to BTC.
- Peaked around **$5,000** in previous bull cycles.
- **Gradual upward trend**, showing solid adoption.

**3️⃣ Solana (SOL) Remains Relatively Lower in Price**
- **SOL (purple)** shows price spikes after 2021 but remains below BTC & ETH.

### Market Capitalization

![image](https://github.com/user-attachments/assets/a075b274-3c65-460d-a8c6-8daf3e31ab48)

**1️⃣ Bitcoin (BTC) Leads the Market**
- **BTC (orange)** has the highest market capitalization, peaking above **$2 trillion**.
- Significant **growth during bull runs** (2017, 2021, 2024).
- **Recent 2024 surge** suggests renewed investor confidence.

**2️⃣ Ethereum (ETH) Shows Strong Growth**
- **ETH (blue)** follows BTC but at a lower magnitude.
- Peaked around **$500 billion** in 2021 but remains **steadily increasing**.
- Indicates **strong network utility and adoption**.

**3️⃣ Solana (SOL) Gains Traction**
- **SOL (purple)** had a late start but saw significant growth post-2021.
- **Smaller market cap** compared to BTC & ETH but shows steady **adoption and resilience**.

**4️⃣ Market Cycles Are Clearly Visible**
- **Boom and bust cycles** are evident (2021 bull run, 2022 bear market).
- **Post-2023 recovery** shows renewed market interest.

### Trading Volume Analysis

![image](https://github.com/user-attachments/assets/276530bc-8a0d-4b2a-9f33-5579de69bc86)

1️⃣ Bitcoin (BTC) Dominates Trading Volume  
- **BTC (orange)** has the highest trading volume over time, especially during market peaks.  
- Major **spikes align with market cycles** (e.g., 2021 bull run).  

2️⃣ Ethereum (ETH) Has Consistently High Volume  
- **ETH (blue)** follows BTC’s trend but at a lower scale.  
- Shows **sustained liquidity**, indicating strong investor interest.  

3️⃣ Solana (SOL) Gained Traction Post-2020  
- **SOL (purple)** had minimal trading before 2020 but grew rapidly.  
- Lower volume than BTC & ETH, but **trading activity is increasing**.  

 4️⃣ Volume Spikes Correlate with Market Events  
- **2021:** Crypto bull run → **Highest trading activity ever recorded**.  
- **2022:** Market crash → **Sharp spikes, indicating panic selling**.  
- **2024:** Volume stabilizes but remains **volatile, especially for BTC**.

### Daily Returns (Volatility)

![image](https://github.com/user-attachments/assets/92092389-0c3f-4bf9-af2f-571a0c5313c4)

1️⃣ Bitcoin (BTC) Has the Most Stable Daily Returns  
- **BTC (orange)** shows relatively smaller fluctuations compared to ETH & SOL.  
- This suggests **lower risk & more stability**, making it appealing for long-term investors.  

 2️⃣ Ethereum (ETH) Displays Higher Volatility Post-2017  
- **ETH (blue)** starts showing larger daily returns around 2017.  
- Significant **price swings** occur, aligning with major market cycles.  

 3️⃣ Solana (SOL) Has the Most Extreme Daily Swings  
- **SOL (purple)** exhibits **wild daily return fluctuations**, especially after 2020.  
- This suggests **high speculative trading** and market sensitivity.  

4️⃣ Crypto Market Volatility Peaks in Key Events  
- **2018:** Post-bull market crash → Large drops in ETH & BTC.  
- **2021:** Crypto bull run → High returns but also rapid corrections.  
- **2022:** Market downturn → SOL & ETH exhibit extreme drops.

### Volatility Using Rolling Standard Deviation

![image](https://github.com/user-attachments/assets/c7b6f16f-b287-41df-8569-4f8ccd12e42d)

 1️⃣ Bitcoin (BTC) Shows the Most Stability  
- BTC (orange) maintains relatively low volatility over time.  
- This suggests it is more **established** and less reactive to short-term market movements.  

 2️⃣ Ethereum (ETH) and Solana (SOL) Are More Volatile  
- ETH (blue) experiences **moderate fluctuations**, especially during market shifts.  
- SOL (purple) has the **highest volatility**, with frequent sharp spikes.  
- Post-2021, **SOL's volatility exceeds ETH & BTC**, indicating **higher speculative activity**.  

3️⃣ Volatility Spikes Align with Major Market Events  
- 2018: Crypto market crash → Sudden surge in volatility.  
- 2020: Pandemic-driven uncertainty → Increased market swings.  
- 2021: **Bull run & corrections** → Highest volatility levels observed.  

## 7. Implementation

### **Checking for Stationarity**

- **Visual Inspection (Rolling Mean & Standard Deviation):**  
  ![Rolling Statistics](https://github.com/user-attachments/assets/023abafb-c221-466c-b3b5-ded6b156e080)
  
- **ADF Test Results:**  
  - **Original Series:**  
    - ADF Statistic: 0.2040  
    - p-value: 0.9725  
    → *Non-stationary*
    
  - **Differenced Series:**  
    - ADF Statistic: -62.8500  
    - p-value: 0.0000  
    → *Stationary*

---

### **Transformations for Stationarity**

- **Log Transformation:**  
  Stabilizes variance and reduces the impact of outliers.  
  ![Log Transformation](https://github.com/user-attachments/assets/104fc55a-eb2e-410c-81b8-57a15d62c3cf)

- **Differencing:**  
  Removes trends, further stabilizing the series.

- **Seasonality Analysis:**  
  ![Seasonal Decomposition](https://github.com/user-attachments/assets/e7b93bc0-1a5a-4926-a8da-6adfcc496281)

---

### **Time Series Windowing (Sequence Generation)**

For LSTM models, we use a sliding window approach (look_back = 5) to create 3D tensors:
- **Samples:** Number of sequences.
- **Timesteps:** Length of the sliding window.
- **Features:** Number of features per timestep.

---

### **LSTM Model Architecture**

- **LSTM Layers:**  
  - **Layer 1:** 50 units, returns sequences, uses tanh activation with L2 regularization.
  - **Layer 2:** 40 units, final output state, tanh activation with L2 regularization.
  
- **Dropout Layers:**  
  0.3 dropout after each LSTM layer to mitigate overfitting.
  
- **Dense Layers:**  
  - 30-unit dense layer with ReLU activation.
  - Final dense layer with 1 unit for regression.

- **Training Details:**  
  - **Optimizer:** Adam with a learning rate of 0.0005  
  - **Loss Function:** Mean Squared Error (MSE)  
  - **Epochs:** Up to 100 with early stopping (patience = 10, restore best weights)  

  ![image](https://github.com/user-attachments/assets/fcde4ce9-27a3-4c25-84fe-fe95598f7249)

---

### **Data Splitting**

- **Chronological Order:**  
  Data is sorted by date to preserve temporal relationships.

- **80/20 Split:**  
  - **Training Set (80%):** Earliest data for model learning.  
  - **Test Set (20%):** Most recent data for evaluation.  
  ![Data Splitting](https://github.com/user-attachments/assets/4890909f-c3c7-41bf-b97c-669e3033f895)

---

## 7. Model Predictions

### **Random Forest**
- **Actual vs Predicted Prices:**
  ![image](https://github.com/user-attachments/assets/19c0219e-ea12-4dd2-b137-9eacc25564a6)

### **XGBoost**
- **Actual vs Predicted Prices:**  
  ![image](https://github.com/user-attachments/assets/718be5c9-da6c-4366-950b-443795705611)

### **ARIMA**
- **Actual vs Predicted Prices:**  
  ![ARIMA Results](https://github.com/user-attachments/assets/538a5c17-332f-4bf5-8eb5-6fba4045cca9)

### **SARIMAX**
- **Actual vs Predicted Prices:**  
  ![SARIMAX Results](https://github.com/user-attachments/assets/54e9f8a0-04fa-45f6-a9f2-c7d5ce7e519e)

### **Hyperparameter Tuning (SARIMAX)**
- **Results:**  
  ![Tuned SARIMAX Results](https://github.com/user-attachments/assets/0d8e1b5d-8e8e-4520-b97d-5f318e961b1f)

### **PROPHET**
- **Results:**  
  ![image](https://github.com/user-attachments/assets/bd371742-e43c-4c9c-8b9c-80892b4f343b)

### **LSTM**
- **Results:**  
  ![image](https://github.com/user-attachments/assets/0e9d6d2c-d174-47de-98be-0903172e3d12)
  
  ![image](https://github.com/user-attachments/assets/517cb312-e6ac-48a1-b753-257d219168ba)

  ![image](https://github.com/user-attachments/assets/6d238d5c-a5e3-47d5-ac7d-b9c677610d17)

---

## 8. Model Evaluation

### **Metrics**

- **Mean Absolute Error (MAE):**  
  - Represents the average absolute difference between predicted and actual values.
  - Less sensitive to outliers.

- **Root Mean Squared Error (RMSE):**  
  - Gives higher weight to larger errors.
  - In the same units as the target variable, allowing direct comparison.

### **Performance Summary**

| **Model**          | **MAE**    | **RMSE**   |
|--------------------|------------|------------|
| **LSTM**           | 2147.02    | 2832.39    |
| **Random Forest**  | 4853.04    | 11581.81   |
| **XGBoost**        | 5498.91    | 12441.40   |
| **Prophet**        | 11342.16   | 15621.58   |
| **ARIMA**          | 26449.34   | 34524.33   |
| **SARIMA**         | 15283.65   | 20759.14   |
| **Tuned SARIMA**   | 30186.72   | 38668.71   |

**LSTM Crypto model evaluation**

| **Model**          | **MAE**    | **RMSE**   |
|--------------------|------------|------------|
| **Bitcoin**        | 2147.02    | 2832.39    |
| **Ethereum**       |  125.98    | 174.23     |
| **Solana**         |  10.47     | 13.71      |

**Conclusion:**  
Based on these metrics, **LSTM** emerges as the best-performing model for forecasting Bitcoin prices with the lowest MAE and RMSE values.

---

## 9. Model Deployment: 

  
