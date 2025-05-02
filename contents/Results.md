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


### Evaluation of Disaster Identification and Severity Estimation

We quantitatively assess our agent’s performance across two critical subtasks: weather disaster type classification and severity level estimation. Both modules were evaluated on a held-out test set using true-predicted alignment metrics and confusion matrices.

#### Disaster Type Classification.
As visualized in Figure 3 (left), our classifier effectively distinguishes among common disaster scenarios, achieving 78% accuracy and an F1-score of 0.79. The model maintains high precision (0.84) across most classes. Notably, “Clear” and “Cloudy” classes are robustly predicted with minimal cross-contamination. Misclassifications predominantly occur between “Rainy” and “Cloudy” events, which share similar low-frequency environmental signals such as moderate precipitation and overcast patterns. This ambiguity is exacerbated in borderline cases, which suggests that contextual temporal features—such as preceding hours of wind gust or barometric drops—could further disambiguate these classes.

#### Severity Assessment.
As shown in Figure 3 (right), the model demonstrates strong ability to isolate low-severity cases, with 32 out of 39 correctly classified. The classifier achieves 74% accuracy, precision of 0.79, and F1-score of 0.76. While high-severity predictions are occasionally downgraded to medium (and vice versa), such confusion aligns with the inherently soft boundaries between escalation tiers, especially when dependent on incomplete real-time data. This reflects a key challenge in emergency decision-making pipelines: ensuring sufficient sensitivity to escalate critical cases while avoiding alert fatigue from false positives.

#### Aggregate Performance.
The full evaluation matrix in Table 1 summarizes the predictive capacity of our system. The results affirm that LLM-guided classification—when grounded in structured sensor inputs—can achieve performance on par with traditional meteorological classifiers, while additionally offering interpretability and routing capabilities absent in black-box CNNs or shallow ensembles.

<p align="center"> <img src="static/assets/img/class.png" alt="Confusion matrices" width="800"/> </p> <p align="center" style="font-size: 0.9em;"><b>Figure 3:</b> Left: Confusion matrix for disaster classification across six weather categories. Right: Confusion matrix for severity estimation. Most errors occur near class boundaries.</p> <p align="center"> <img src="static/assets/img/metrics.jpg" alt="Metrics table" width="300"/> </p> <p align="center" style="font-size: 0.9em;"><b>Table 1:</b> Precision, recall, accuracy, and F1-score for the disaster and severity classifiers.</p>
