# Timeseries-Forcasting-Case-Studty-Analysis

### Exploratory Data Analysis

The German electricity demand series exhibited strong annual seasonality, with demand peaks consistently occurring during winter months and lower demand during summer periods. This behaviour reflects increased heating and lighting requirements during colder seasons.

The hourly series contained substantial short-term fluctuations caused by daily consumption patterns and industrial activity. Aggregating the data to daily and weekly resolutions reduced this noise and exposed the underlying seasonal structure more clearly.

Seasonal decomposition confirmed the presence of trend, seasonal and residual components within the weekly series. Stationarity testing using the Augmented Dickey-Fuller (ADF) and KPSS tests indicated that the weekly demand series was sufficiently stationary for autoregressive modelling.

Autocorrelation analysis revealed strong seasonal behaviour around lag 52 weeks, supporting the use of seasonal forecasting methods such as SARIMA.

---

### Benchmark Models

Four benchmark forecasting models were implemented:

- Mean Forecast
- Naive Forecast
- Seasonal Naive Forecast
- Drift Forecast

The Seasonal Naive model achieved the best benchmark performance, demonstrating that German electricity demand follows highly repetitive annual cycles and contains strong seasonal information.

---

### SARIMA

SARIMA successfully captured annual seasonal behaviour but did not outperform the Seasonal Naive benchmark. This suggests that much of the variation within the electricity demand series can already be explained by historical yearly demand patterns.

---

### SARIMAX

Temperature variables improved forecasting accuracy, confirming the importance of weather conditions in electricity demand modelling.

Heating degree days were particularly informative because electricity demand increases during colder periods due to heating requirements. Holiday variables produced smaller improvements because annual seasonal patterns already captured much of the reduction in industrial electricity demand during public holidays.

---

### Feature-Based Regression

The feature-based model combined:

- Lag variables
- Rolling averages
- Fourier seasonal features
- Calendar variables
- Temperature information

This model achieved the best performance among the weekly forecasting models by capturing nonlinear relationships that could not be represented by SARIMA models.

---

### LSTM

The LSTM model achieved the lowest numerical RMSE and successfully captured short-term hourly demand dynamics.

However, the LSTM evaluation used a rolling one-step-ahead hourly forecasting strategy and therefore was not directly comparable with the fixed-origin two-year weekly forecasts used by the remaining models.

---

### Final Findings

The analysis demonstrates that increasing model complexity does not always improve forecasting performance.

- Seasonal Naive proved to be a strong benchmark due to the repetitive annual demand cycle.
- Weather information improved forecasting accuracy.
- Feature engineering provided substantial benefits for machine learning models.
- The LSTM achieved the lowest numerical RMSE.
- The feature-based model provided the best balance between forecasting accuracy, interpretability and computational efficiency for weekly forecasting applications.

For operational weekly forecasting, the feature-based regression model is recommended.
