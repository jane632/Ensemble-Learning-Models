# Ensemble-Learning-Models
This is a guide on ensemble techniques in machine learning
Ensemble Techniques in Machine Learning

## Ensemble techniques are powerful methods in machine learning that combine multiple models to improve overall performance. The main goal is to reduce variance, bias, or improve predictions. The most common ensemble techniques are:
**Bagging, Boosting, Random Forest, AdaBoost, and XGBoost.**

### 1. Bagging (Bootstrap Aggregating)

Bagging is short for Bootstrap Aggregating, a technique that improves the stability and accuracy of machine learning models, particularly for high-variance algorithms (like decision trees).

#### How It Works:

* The original dataset is split into multiple subsets using random sampling with replacement (some data points may appear more than once in different subsets).

* Each subset is used to train a separate model independently.

* For classification tasks, majority voting is applied to aggregate predictions.

* For regression tasks, the average (mean) of all model outputs is calculated.

**Example for Binary Classification:**

Consider new test data passed through four models, resulting in predictions: 0, 1, 1, 1.

Using majority voting, the final output is 1 since it appears most frequently.

**Example for Regression:**

Suppose the outputs from four models are: 120, 140, 122, 148.

The final prediction is the average:(120 + 140 + 122 + 148) / 4 = 132.5


## 2.Boosting

### Boosting is an ensemble learning technique that improves model performance by combining multiple weak learners to create a strong learner. The models are trained sequentially, with each new model focusing on correcting the errors made by the previous one.


#### Examples of Boosting Algorithms:

* AdaBoost (Adaptive Boosting): Focuses on misclassified data points by adjusting their weights, making the next model pay more attention to them.

* Gradient Boosting: Optimizes model performance by minimizing the errors through gradient descent techniques.

* XGBoost (Extreme Gradient Boosting): An advanced, optimized version of gradient boosting known for its speed, efficiency, and high performance in competitions.


#### Examples of Bagging (Bootstrap Aggregating):

* Random Forest Classifier: An ensemble of decision trees where the final prediction is based on the majority vote from all trees.

* Random Forest Regressor: Similar to the classifier, but instead of voting, the average of the outputs from all trees is taken to predict continuous values.


## Random Forest 

* The Random Forest Classifier is an ensemble model that consists of multiple decision trees. It is a type of bagging algorithm designed for classification tasks.

##### How It Works:

* Each decision tree is trained on a random subset of the data and features.

* Records and features may be repeated across different trees due to bootstrapping.

* Majority voting is used to determine the final classification—whichever class receives the most votes across all trees becomes the model's output.

**For Regression Tasks:**

* Instead of voting, the model calculates the mean of outputs from all the decision trees to make continuous predictions.

## Adaboost

### How AdaBoost Works
* Initialize Weights

Equal weight for all data points: 

Purpose: Treat all records equally at the start.

* Train the First Weak Learner

Select the best feature using Information Gain, Entropy, or Gini Index.


Build a simple model (e.g., decision stump) and predict outcomes.

* Identify Errors & Calculate Error Rate (ε)

Compare predictions to actual labels.

Error Rate (ε): Sum of weights for misclassified points.

 
*  Update Weights

Increase weights of misclassified records (focus more on them).

Decrease weights of correct records (already learned).

**Correct predictions → lower weight; wrong predictions → higher weight.**

* Repeat & Combine

Train the next model using updated weights.

Final model = weighted sum of all weak learners, with more accurate models having higher influence.


## How XGBoost Works

#### Base Model Creation

* Start with a simple model (Base Model):

This model makes initial predictions, often using a basic approach like predicting the average of the target variable.

* Calculate Residuals:

Residuals represent the errors made by the base model. They are the difference between the actual value and the predicted probability:

**Residual**
   * Residual=Actual Value (Approval)−Predicted Probability

Positive Residual: Model under-predicted (needs adjustment upward).

Negative Residual: Model over-predicted (needs adjustment downward).

* Building the First Decision Tree

 Instead of predicting the original target, the tree now predicts the residuals (the errors).
 
Features Used: You can use any relevant features. For example:

Similarity Index: Measures how similar a data point is to others, which can be useful in classification tasks.
The goal of this decision tree is to learn patterns in the errors to help the model correct itself in the next iteration.

*  Updating Predictions

After building the tree:

The predictions from the tree are added to the original model’s predictions to reduce the error.

**New Prediction=Old Prediction+(η×Tree’s Prediction)**

* Iterative Process

This process of calculating residuals, building trees, and updating predictions continues for multiple iterations.

Each new tree focuses on correcting the mistakes made by the previous trees.
