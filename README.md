# Heat_Pump_Installation_Forecasting
*Forecasting the Future of Heat Pumps in Switzerland*

Heat pumps have become one of the most important technologies in Europe’s transition to clean and efficient heating. Switzerland, in particular, has seen rapid adoption as older fossil-based heating systems are replaced with renewable, electricity-powered alternatives.

For this project, I set out to examine how heat pump installations have evolved in Switzerland, and more importantly, where the trend is headed in the next decades.

Using official datasets from the Swiss Federal Office of Energy (SFOE), I built a complete workflow—data cleaning, exploratory analysis, regression, and ARIMA time-series forecasting—to project installations up to 2050.
**Why This Project?**

Energy transition is one of the defining challenges of our time. Heat pumps sit at the center of Switzerland’s long-term energy and climate strategy, making it an ideal case study for:

- Understanding renewable technology growth

- Practicing real-world time-series forecasting

- Working with government open data

- Drawing policy-relevant insights

*This project blends data science and sustainability, showcasing how statistical tools help us interpret and forecast complex energy dynamics.*

### 1. Data Collection & Preparation

SFOE publishes extensive annual energy statistics, including:

- Number of heat pump installations

- Thermal and electrical power

- Electricity consumption

- Renewable heat contributions

- Total heat production

These values were provided in an Excel file (Elektrowarmepumpe.xlsx).

I cleaned and transformed the dataset by:

- Converting French column names to English

- Ensuring numeric types

- Removing missing entries

- Setting the year as a proper datetime index

This created a high-quality time series suitable for modeling.

### 2. Exploring the Trend

Plotting the historical data immediately revealed a clear pattern.  Heat pump installations in Switzerland have accelerated sharply over time. A simple line chart showed transition from modest annual installations in early years to steep growth in more recent periods. This growth reflects both policy incentives and broader electrification trends.

### 3. Regression: Understanding the Drivers

Before forecasting, I explored what factors were statistically associated with installation numbers using an Ordinary Least Squares (OLS) model.

**Key findings:**

- Thermal Power had a strong positive relationship

- Electric Power had a negative relationship

- Residuals were autocorrelated → a pure regression model was inadequate

*This confirmed that the data had sequential dependence, making time-series models more appropriate.*

### 4. Time-Series Modeling with ARIMA

To build a robust forecast:

**1- Stationarity Check:**

Using the Augmented Dickey–Fuller test, I tested whether the installation series was stationary.

**Result:**

The series was non-stationary, consistent with a long-term growth trend.

I applied differencing (d = 1) to stabilize the series.

**2- ACF & PACF Analysis**

These plots suggested an ARIMA model with low-order AR and MA components.

**3- Final Model**

I fit an ARIMA(1, 1, 1) model, which performed well and yielded a clean residual structure.

### 5. Forecasting to 2030 and 2050

Using the model, I forecasted the next 30 years.

The result included:

- Installations continue rising rapidly

- The model predicts that Switzerland will exceed 400,000 installations per year by 2028

- Growth continues beyond 2030, reflecting strong structural momentum in adoption

- By 2050, annual installations could reach even higher levels like six times more than 25 years before, depending on policy and technological shifts

While forecasts always carry uncertainty, the overall direction is clear:

**Heat pump adoption in Switzerland is on a steep upward trajectory.**


### 6. Model Diagnostics

Residual analysis showed that residuals were random and centralized. There was no major autocorrelation remaining. This points to a good model fit for long-term forecasting. This supports the reliability of the ARIMA approach for capturing the trend.

### Conclusion

This project demonstrates how open energy data and statistical modeling can yield important insights into renewable technology adoption. If current trends continue, heat pumps will become the dominant heating technology long before 2050.


### Want to Explore the Code?

The full workflow is available in the repository’s Jupyter Notebook.
Feel free to explore, fork, or build upon the analysis.


**Folder Structure**

├── README.md

├── hp_installations.ipynb               #  Jupyter Notebook

├── Elektrowarmepumpe.xlsx       # SFOE dataset

└── requirements.txt
