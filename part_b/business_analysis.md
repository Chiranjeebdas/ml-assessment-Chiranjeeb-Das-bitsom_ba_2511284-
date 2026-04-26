### B1. Problem Formulation

(a) This is a supervised machine learning regression problem where the target variable is items_sold. The input features include store_id, store_size, location_type, promotion_type, is_weekend, is_festival, competition_density, and date-based features. Regression is chosen because the target variable is continuous.

(b) Items sold is a better target than revenue because it directly measures demand without being affected by price variations. Revenue can be misleading due to discounts or pricing changes. This highlights the importance of choosing a target variable that aligns with the business objective.

(c) Instead of a single global model, we can use segmented models based on location_type or store clusters, or include interaction features. This helps capture different customer behaviors across locations.


### B2. Data and EDA Strategy

(a) The tables can be joined using store_id and transaction_date. The final dataset will have one row per store per day. Aggregations may include total items_sold per day and merging store attributes and promotion details.

(b) EDA steps:
- Distribution of items_sold to check skewness and outliers
- Sales comparison across promotion types
- Trend analysis over time (daily/monthly sales)
- Impact of weekend and festival on sales

These insights help in feature engineering and model selection.

(c) Since 80% of data has no promotion, the model may become biased. To handle this, we can use techniques like resampling, adding class weights, or ensuring balanced representation during training.


### B3. Model Evaluation and Deployment

(a) A temporal train-test split should be used, where older data is used for training and recent data for testing. Random split is inappropriate because it breaks time dependency. Evaluation metrics include RMSE and MAE.

(b) Feature importance helps explain why different promotions are recommended. For example, seasonal or monthly trends may influence different recommendations for the same store.

(c) The model can be deployed as a pipeline saved using joblib. New monthly data is processed using the same pipeline to generate predictions. Monitoring includes tracking prediction errors and retraining the model when performance drops.
