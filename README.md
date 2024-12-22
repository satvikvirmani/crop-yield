# Crop Yield Prediction in Indian States

Objective:
The goal is to predict the yield of crops in India based on historical yield records, leveraging a dataset that provides comprehensive information about crops, regions, and associated factors.

---

Dataset Description:
- Dataset Source: [Kaggle Crop Yield Dataset](http://www.kaggle.com/datasets/akshatgupta7/crop-yield-in-indian-states-dataset)
- Number of Entries: 19,689 rows
- Features:
  - `Crop`: Type of crop (string)
  - `Crop-Year`: Year of yield (integer)
  - `Season`: Growing season (string)
  - `State`: Indian state (string)
  - `Area`: Area cultivated (numeric)
  - `Production`: Crop production (numeric)
  - `Annual-Rainfall`: Annual rainfall (numeric)
  - `Fertilizer`: Fertilizer usage (numeric)
  - `Pesticide`: Pesticide usage (numeric)
  - `Yield`: Crop yield (target variable, numeric)

---

Data Cleaning:
1. String Cleanup:
   - Stripped leading and trailing whitespace for string-based features (`Crop`, `Season`, `State`).
   - Ensures consistent access and avoids referencing errors.
2. Unique Categories:
   - Crops: 55 unique types.
   - Seasons: 6 unique growing seasons.
   - States: 30 unique states in India.

---

Exploratory Data Analysis (EDA):
1. Count Plots:
   - Created count plots to visualize the frequency of each crop, season, and state. This helps in understanding the data distribution.
2. Segmentation by Crop:
   - Segmented the dataset into smaller datasets corresponding to individual crops for detailed analysis.
3. Yield Distribution by Season:
   - Used boxplots to analyze the distribution of crop yield for each season. This reveals season-wise variations in yield and helps detect outliers.

---

Data Preprocessing:
1. String to Numeric Conversion:
   - Features such as `Season` and `State` are categorical and need numerical encoding for machine learning models.
   - Used Label Encoding:
     - Assigned unique numerical values to each category of `Season` and `State`.
     - Reference: [Label Encoder Documentation](https://scikit-learn.org/1.5/modules/preprocessing_targets.html#label-encoding).
2. Correlation Analysis:
   - Computed correlations between features to identify relationships and insights.
3. Data Normalization:
   - As the dataset includes variables on different scales, normalization was applied using Standard Scaler:
     - Formula: \((x - \mu) / \sigma\)
     - Reference: [Standard Scaler Documentation](https://scikit-learn.org/1.5/modules/generated/sklearn.preprocessing.StandardScaler.html#sklearn.preprocessing.StandardScaler).
4. Correlation of Scaled Data:
   - Re-calculated correlations after normalization to ensure consistent feature relationships.

---

Data Splitting:
- Train-Test Split:
  - Split the dataset into training (80%) and testing (20%) subsets.

---

Model Training and Evaluation

Trained the data using multiple regression and ensemble techniques. The performance of each model was evaluated using Mean Absolute Error (MAE), Mean Squared Error (MSE), and R² Score.

| Model                          | MAE  | MSE  | R² Score |
|-------------------------------------|----------|----------|--------------|
| Linear Regression                  | 0.6906   | 0.8382   | 0.3134       |
| Ridge Regression (L2 Regularization) | 0.6835   | 0.8117   | 0.3351       |
| Decision Tree Regressor            | 0.3274   | 0.3097   | 0.7463       |
| Random Forest Regressor            | 0.2929 | 0.2066 | 0.8307   |
| Gradient Boosting Regressor        | 0.3097   | 0.2238   | 0.8167       |
| Multi-Layer Perceptron Regressor   | 0.3559   | 0.2745   | 0.7752       |

Observations:
1. Random Forest Regressor:
   - Achieved the best performance with the highest R² Score (0.8307) and lowest MSE (0.2066).
   - Demonstrates the strength of ensemble learning for this dataset.
2. Gradient Boosting Regressor:
   - Performed competitively with an R² Score of 0.8167 and an MSE of 0.2238.
3. Decision Tree Regressor:
   - Achieved an R² Score of 0.7463, highlighting its potential for non-linear relationships.
4. Linear Regression Models:
   - Basic Linear Regression and Ridge Regression showed lower performance, indicating the data's complexity and the presence of non-linear patterns.
5. MLP Regressor:
   - Neural network-based regression achieved moderate results but underperformed compared to Random Forest and Gradient Boosting, likely due to the dataset size and lack of fine-tuning.

---

Summary:
- The Random Forest Regressor performed the best among all models, achieving the highest R² Score of 0.8307 and the lowest MSE of 0.2066.
- Gradient Boosting Regressor and Decision Tree Regressor also showed competitive results, with good performance metrics.
- Linear Regression and MLP Regressor exhibited relatively lower accuracy, possibly due to the complexity of the data and non-linear relationships between features.

More to do:
1. Fine-tune hyperparameters for ensemble models (e.g., Random Forest, Gradient Boosting) to further improve performance.
2. Explore additional advanced techniques like XGBoost or CatBoost.
3. Incorporate external datasets (e.g., weather data or soil quality) to enhance prediction accuracy.

---
