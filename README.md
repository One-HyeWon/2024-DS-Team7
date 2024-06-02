# 2024-DS-Team7

## Predicting Food Truck Success at Seoul Subway Stations

### Project Overview

This project aims to develop a model that predicts the suitability of operating a food truck at Seoul subway stations based on hourly passenger boarding and alighting data. We will explore various combinations of preprocessing and model training methods to identify the best performing combinations.

### Data

* **Data Source:** Seoul Subway Line-Specific Station-Specific Hourly Boarding and Alighting Passenger Information (CSV file)
* **Data Description:** Contains hourly passenger boarding and alighting information for each station on Seoul subway lines 1 through 8, spanning 10 years (January 2013 to December 2022).

### Methodology

1. **Data Preprocessing:**
    * **Missing Value Handling:** Missing values are replaced with 0.
    * **Data Aggregation:** Hourly boarding and alighting passenger counts are combined to calculate total passenger traffic.
    * **One-hot Encoding:** 'Line' information is one-hot encoded to transform categorical variables into numerical variables.
    * **Data Scaling:** StandardScaler, MinMaxScaler, and RobustScaler are used to scale numerical features.

2. **Clustering:**
    * **PCA (Principal Component Analysis):** PCA is applied to reduce the dimensionality of the data.
    * **KMeans Clustering:** KMeans clustering is performed based on the PCA results to group stations with similar characteristics.
    * **Cluster Evaluation:** Elbow Method and Silhouette Analysis are used to determine the optimal number of clusters.

3. **Model Training and Evaluation:**
    * **Models:** Decision Tree, SVC, and Random Forest classification models are used.
    * **Train-Test Split:** Data is split into training and testing sets with a 7:3 ratio.
    * **Model Training:** Models are trained using various combinations of scalers and models.
    * **Evaluation Metrics:** Accuracy, Precision, Recall, and F1-score are used to evaluate model performance.
    * **Confusion Matrix:** Confusion matrices are generated to visualize the prediction results of each model.

### Results

#### Cluster
![클러스터](https://github.com/One-HyeWon/2024-DS-Team7/assets/101498350/91d9192b-5062-4cfa-bed6-f50b16a30015)

</br>

#### Optimal K
![elmow](https://github.com/One-HyeWon/2024-DS-Team7/assets/101498350/0ac95c36-1f97-42d3-866d-fe66eaf89fbd)
![sil](https://github.com/One-HyeWon/2024-DS-Team7/assets/101498350/9f1f2f8f-d5d1-481a-8883-2e1cb31118e7)



After training and evaluating models using various combinations of preprocessing methods (scaling, encoding) and models (Decision Tree, SVC, Random Forest), the top 5 performing combinations are as follows:

| Rank | Scaler | Model | Accuracy | Precision | Recall | F1-score |
|---|---|---|---|---|---|---|
| 1 | StandardScaler | SVC | 0.997037 | 0.997700 | 0.999372 | 0.998535 |
| 2 | RobustScaler | SVC | 0.997037 | 0.997700 | 0.999372 | 0.998535 |
| 3 | MinMaxScaler | SVC | 0.996934 | 0.997074 | 0.999372 | 0.998222 |
| 4 | StandardScaler | RandomForestClassifier | 0.987738 | 0.992860 | 0.990364 | 0.991611|
| 5 | MinMaxScaler | RandomForestClassifier | 0.987738 | 0.992860 | 0.990364 | 0.991611 |


</br>

##### HeatMap

1. StandradScaler + SVC
![stand+svc](https://github.com/One-HyeWon/2024-DS-Team7/assets/101498350/c39de4c4-c534-4ccd-bfe5-8939b51e8232)

2. RobustScaler + SVC
![rob+svc](https://github.com/One-HyeWon/2024-DS-Team7/assets/101498350/efb42287-ab43-49a3-bf21-92b8cb2589ba)

3. MinMaxScaler + SVC
![mm+svc](https://github.com/One-HyeWon/2024-DS-Team7/assets/101498350/a43948ab-1a9d-4d63-af1a-dc0ca9ef4d18)

4. StandardScaler + RandomForestClassifier
![stand+rdf](https://github.com/One-HyeWon/2024-DS-Team7/assets/101498350/e81066fe-d596-4294-b2e8-bf7d509923e6)

5. MinMaxScaler + RandomForestClassifier
![mm+rdf](https://github.com/One-HyeWon/2024-DS-Team7/assets/101498350/3fb094d6-01f2-45c3-b0bf-f10d95313072)


### Conclusion

The SVC model generally outperformed other models, achieving the best results when used with StandardScaler and RobustScaler. This suggests that the SVC model effectively classifies the data, and both StandardScaler and RobustScaler contribute to better model training by effectively adjusting the data distribution. 


### Future Research Directions

* **Additional Feature Engineering:** Model performance can be further improved by incorporating additional features such as surrounding population density, commercial area information, day of the week, and holiday status.
* **Hyperparameter Tuning:** GridSearchCV or RandomizedSearchCV can be used to optimize model hyperparameters.
* **Alternative Clustering Algorithms:** Explore other clustering algorithms (e.g., DBSCAN, Hierarchical Clustering) and compare their performance to KMeans.
* **Deep Learning Models:** Deep learning models can be employed to learn more complex patterns and potentially improve prediction accuracy.
