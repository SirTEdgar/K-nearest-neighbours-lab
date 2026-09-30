# K-nearest-neighbours-lab# Retail Customer Segmentation Using k-Nearest Neighbors

## Project Overview

This project applies the **k-Nearest Neighbors (k-NN)** machine learning algorithm to classify retail customers into five predefined customer segments based on their purchasing behavior, demographics, and engagement metrics.

The project was developed for **RetailIQ**, an e-commerce analytics company, to help an online fashion retailer better understand its customers and support targeted marketing campaigns.

The model evaluates multiple distance metrics to determine how customer similarity should be measured and then optimizes the best-performing k-NN model using hyperparameter tuning.

---

## Customer Segments

The dataset contains five predefined customer segments:

| Segment | Description                                                |
| ------- | ---------------------------------------------------------- |
| 0       | Occasional Shoppers — low frequency and low value          |
| 1       | Loyal Regular Shoppers — high frequency and moderate value |
| 2       | High-Value Enthusiasts — high frequency and high value     |
| 3       | Big Spenders — low frequency and high value                |
| 4       | New Customers — recent first purchase                      |

The objective is to classify new customers into one of these five segments.

---

## Dataset

The project uses the `retail_customer_data.csv` dataset.

### Features

The dataset contains the following customer attributes:

### Purchase Behavior

* `recency` — time since the customer's most recent purchase
* `frequency` — number of purchases made
* `monetary_value` — customer's spending value
* `tenure` — length of the customer relationship

### Engagement

* `website_visits` — number of website visits
* `time_spent` — time spent on the website
* `wishlist_items` — number of wishlist items
* `cart_abandons` — number of abandoned carts

### Demographics

* `age` — customer age
* `income` — customer income

### Target

* `segment` — customer segment ranging from 0 to 4

---

## Objectives

The main objectives of this project are to:

1. Explore and understand the customer dataset.
2. Analyze feature distributions using histograms.
3. Examine relationships between features using a correlation matrix.
4. Prepare the data for distance-based machine learning.
5. Standardize the numerical features.
6. Implement k-NN using different distance metrics.
7. Compare Euclidean, Manhattan, and Chebyshev distances.
8. Implement Mahalanobis distance to account for correlations between features.
9. Use 5-fold cross-validation to compare model performance.
10. Optimize the best-performing model using GridSearchCV.
11. Evaluate the final model on unseen test data.
12. Analyze classification performance using accuracy and a confusion matrix.

---

## Methodology

### 1. Exploratory Data Analysis

The dataset is first examined to understand:

* Feature distributions
* Differences in feature scales
* Potential skewness
* Relationships between variables
* Potential correlations between customer behavior metrics

Histograms are created for the numerical features, while a correlation matrix is used to examine relationships between variables.

---

### 2. Data Preprocessing

The dataset is divided into:

* **Features (`X`)** — customer characteristics
* **Target (`y`)** — customer segment

The data is split into training and testing sets using a 75/25 split with `random_state=42`.

Since k-NN relies on distance calculations, the features are standardized using `StandardScaler`.

The scaler is fitted only on the training data and then applied to both the training and testing data.

---

### 3. Distance Metrics

Several distance metrics are evaluated using k-NN:

#### Euclidean Distance

Measures the straight-line distance between two observations.

#### Manhattan Distance

Measures distance as the sum of the absolute differences between feature values.

#### Chebyshev Distance

Measures the largest absolute difference across any feature.

#### Mahalanobis Distance

Mahalanobis distance accounts for correlations between variables by incorporating the covariance structure of the training data.

---

## Model Evaluation

Each distance metric is evaluated using **5-fold cross-validation**.

The mean cross-validation accuracy is recorded for each metric and compared to determine which distance metric performs best on the training data.

The results are visualized to make the performance differences easier to interpret.

---

## Hyperparameter Tuning

After comparing the distance metrics, the selected metric is optimized using `GridSearchCV`.

The hyperparameters considered include:

* Number of neighbors (`n_neighbors`)
* Weighting scheme (`weights`)

The weighting schemes evaluated are:

* `uniform`
* `distance`

Five-fold cross-validation is used during the grid search.

The best-performing parameter combination is selected based on mean cross-validation accuracy.

---

## Final Model Evaluation

The optimized k-NN model is evaluated using the previously unseen test dataset.

The following evaluation metrics are used:

* Test accuracy
* Confusion matrix
* Precision
* Recall
* F1-score

The confusion matrix shows how accurately the model distinguishes between the five customer segments and identifies which segments are most frequently confused with one another.

---

## Technologies Used

* Python
* Pandas
* NumPy
* Matplotlib
* Seaborn
* Scikit-learn
* Jupyter Notebook / Google Colab

---

## Project Structure

```text
Retail-Customer-Segmentation/
│
├── retail_customer_data.csv
├── kNN_Customer_Segmentation.ipynb
└── README.md
```

---

## Machine Learning Workflow

```text
Raw Customer Data
        ↓
Exploratory Data Analysis
        ↓
Feature/Target Separation
        ↓
Train-Test Split
        ↓
Feature Standardization
        ↓
Euclidean Distance
        ↓
Manhattan Distance
        ↓
Chebyshev Distance
        ↓
Mahalanobis Distance
        ↓
5-Fold Cross-Validation
        ↓
Distance Metric Comparison
        ↓
GridSearchCV
        ↓
Optimized k-NN Model
        ↓
Test Set Evaluation
        ↓
Confusion Matrix & Classification Report
```

---

## Expected Outcome

The final system provides a k-NN classification model capable of assigning customers to one of five predefined segments based on their purchasing behavior, engagement, and demographic characteristics.

The comparison of distance metrics helps identify how different definitions of customer similarity affect classification performance, while hyperparameter tuning is used to optimize the selected model.

The resulting model can serve as a foundation for customer segmentation and targeted marketing analysis.
