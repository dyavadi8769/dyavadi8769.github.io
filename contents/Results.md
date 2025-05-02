Reliable estimation of key meteorological variables is essential for downstream tasks in disaster identification and severity classification. We evaluate our model’s performance on two core variables  temperature and wind speed  by comparing model predictions with ground-truth measurements collected from recent weather events.

#### Temperature Prediction (RMSE = 3.36°C)

<p align="center"> <img src="static/assets/img/temp.png" alt="Figure 1: True vs Predicted Temperature" width="600"/><br> <b>Figure 1: True vs Predicted Temperature</b> </p>

In Figure 1, the model demonstrates a strong correlation between predicted and true temperature values, with a Root Mean Square Error (RMSE) of 3.36°C. The regression line closely follows the ideal fit, indicating that the model successfully captures thermal dynamics even under moderate environmental noise. Slight deviations at the extremities suggest a need for broader calibration across high-variance urban microclimates.

#### Wind Speed Prediction (RMSE = 2.70 km/h)

<p align="center"> <img src="static/assets/img/wind.png" alt="Figure 2: True vs Predicted Wind Speed" width="600"/><br> <b>Figure 2: True vs Predicted Wind Speed</b> </p>
As shown in Figure 2, the model’s wind speed predictions exhibit an RMSE of 2.70 km/h, with predictions clustering around the ideal line. The spread increases slightly at higher speeds — a common trait in wind modeling due to sparse high-intensity event data. Nevertheless, the model remains sufficiently calibrated to distinguish between benign and risk-prone wind conditions, critical for triggering wind-sensitive response workflows such as civil defense or public works alerts.

#### Implications for Disaster Reasoning
These predictive outputs serve as foundational inputs to the agent’s LLM-driven disaster type classification and severity assessment modules. Accurate forecasting of temperature and wind enables the system to:

* Detect early signals of heatwaves, storms, or floods based on domain thresholds.

*  Quantify event severity with greater confidence and trigger the correct departmental response via conditional StateGraph routing.

*  Reduce reliance on post-facto social signals by anchoring initial classification in real-time meteorological evidence.

The agent's end-to-end architecture thus benefits from low regression error, which translates directly into more precise, interpretable, and verifiable disaster response planning.
