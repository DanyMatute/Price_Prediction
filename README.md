
## **Overview**

> *"This project predicts the sale price of bulldozers sold at auctions using historical auction data and a RandomForestRegressor, applying feature engineering, model tuning, and performance evaluation."*

---

## **1. Problem & Dataset**

* Briefly describe:

  * **Goal** → Predict the sale price of bulldozers sold at auctions.
  * **Source** → [Kaggle](https://www.kaggle.com/competitions/bluebook-for-bulldozers/overview).
  * **Size** & type of data (rows = 412697, features = 53, mix of numerical & categorical, presence of missing values).

---

## **2. Data Preparation**

  * **Data cleaning**: standardized date formats.
  * **Feature engineering**: extracted year/month, created binary indicators for missing values to retain information.
  * **Categorical handling**: converted non-numeric columns to categorical codes.
  * **Missing data**: encoded nulls without losing patterns.

---

## **3. Model Development**

* **Initial model**: trained on entire dataset with default `RandomForestRegressor` parameters (baseline).
* **Hyperparameter tuning**: tested multiple parameter combinations on subsets of data to find optimal ones.
```
# most ideal hyperparameters
ideal_model = RandomForestRegressor(n_estimators = 90,
                                    min_samples_leaf= 15,
                                    min_samples_split=10, 
                                    max_features= None,
                                    n_jobs = -1,
                                    max_samples= None, 
                                    random_state = 42)
```
* **Final model**: trained with best parameters on all training data.

---

## **4. Evaluation**

* Metrics:

  * **MAE** → measures average error in same units as price.
  * **RMSLE** → penalizes underestimation & works well with skewed price data.
  * **R²** → shows proportion of variance explained by the model.
* Final scores:
  ```
  Training MAE  : 4176.68
   Validation MAE  : 6337.73
   Training RMSLE  : 0.1996
   Validation RMSLE  : 0.2625
   Training R^2  : 0.9153
   Validation R^2  : 0.8615
  ```

---

## **5. Feature Importance**

* Briefly explain which features were most predictive (e.g., "Year of manufacture, machine hours, and product size were the top three predictors").
* Possibly include a small bar chart.
!(Feature Importance)[/feature_importance.png]
---

## **6. Conclusion & Next Steps**

* **Summary**: “The tuned RandomForestRegressor successfully predicted bulldozer prices with high accuracy.”
* **Limitations**: 
* **Future improvements**:

  * Try gradient boosting models (e.g., XGBoost, LightGBM)
  * Explore more domain-specific feature engineering
  * Test time-series-aware validation splits
