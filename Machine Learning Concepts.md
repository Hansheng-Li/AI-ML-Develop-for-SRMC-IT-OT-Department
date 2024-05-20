# Machine Learning  Concepts

## Overfitting/Underfitting

### Underfitting
- Definition: Model is too simple to capture underlying patterns in the data. Performs poorly on both training and unseen data.
- Indicators:
  - Training and validation error both high.
- Solutions:
  - Use a more complex model.
  - Add more features.

### Overfitting
- Definition: Model becomes too complex and starts to memorize the training data instead of learning generalizable patterns.
- Indicators:
  - Training error significantly lower than validation error.
  - Model performs poorly on new data.
- Solutions:
  - Reduce model complexity.
  - Regularize the model (L1, L2 regularization, dropout, cross-validation).
  - Collect more training data.

## Bias/Variance Trade-Off
- Bias: Difference between predicted value and the true data. High bias can lead to underfitting.
- Variance: Spread of predicted values from the expected value. High variance can lead to overfitting.
- Trade-Off: Balancing low bias and low variance is challenging. The goal is to find the right balance for optimal model performance.

## Preventing Overfitting
- Reduce model complexity.
- Regularize the model (L1, L2 regularization, dropout, cross-validation).
- Early stopping.
- Collect more training data.
- Data augmentation.

## Model Selection
- Evaluation Metrics: Use appropriate metrics to compare models.
- Cross-Validation: Split data into multiple folds, train on different folds, and evaluate average performance.
- Hypothesis Testing: A/B testing.
- Domain Expertise: Leverage knowledge from the domain.

## Regression

### Linear Regression Assumptions
1. Linear relationship between independent (X) and dependent variables (y).
2. Independence of errors.
3. Normality of residuals.
4. Homoscedasticity of errors.
5. No multicollinearity among features.

### Correlated Variables
- Outcome: Unstable coefficient estimates, unreliable significance tests, difficulty interpreting contributions.
- Solutions: Feature selection, ridge regression, PCA.

### Regression Coefficient
- Represents the change in the dependent variable for a one-unit change in the independent variable, holding other variables constant.

### Minimizing Squared Error vs. Maximizing Likelihood
- When Gaussian errors are assumed, minimizing squared error is equivalent to maximizing likelihood.
- For non-Gaussian errors, this relationship might not hold.

### Minimizing Inter-Correlation
- Feature selection, PCA, ridge regression, feature engineering.

### Non-Linear Relationship
- Linear regression may not capture non-linear relationships.
- Solutions: Interaction terms, piecewise linear regression, non-linear regression.

### Interaction Variables
- Capture non-additive effects.
- Improved model fit.
- Context-specific relationships.
- Avoiding omitted variable bias.
- Enhanced interpretability.

## Regularization

### L1 vs. L2 Regularization
- L1: Adds a term of L1 norm (sum of absolute values) of the parameters.
- L2: Adds a term of L2 norm ($||\beta||_2 = (\sum \beta_i^2)^{1/2}$) of the parameters.

### Lasso Regression
- L1 regularization.
- Shrinks coefficients towards zero, useful for feature selection.

### Ridge Regression
- L2 regularization.
- Higher lambda values result in more aggressive shrinkage.

### Why L1 is Sparser than L2
- L1 norm has corners at zero, leading to sparsity. L2 norm is smooth, leading to non-zero coefficients.

### Why Regularization Works
- Introduces penalty term to encourage desirable properties (simplicity, sparsity, smoothness).
- Reduces variance.

### Why Use L1/L2 Regularization
- Mathematical properties and computational simplicity.
- Interpretability.

## Metrics

### Precision and Recall Trade-Off
- Precision: Proportion of positive predictions that are true positives.
- Recall: Proportion of actual positives identified correctly.
- Trade-Off: Improving one may decrease the other. Balance depends on the context and consequences of false positives/negatives.

### Metrics for Imbalanced Labels
- Precision and Recall.
- F1-score.
- AUPRC (Area Under the Precision-Recall Curve).
- ROC curve and AUC.

### Metrics for Classification Problems
- Understand problem specifics, class imbalance, and domain knowledge.
- Use multiple metrics for a comprehensive evaluation.

### Confusion Matrix
- Summarizes performance with true positives, true negatives, false positives, and false negatives.

### True Positive Rate, False Positive Rate, ROC
- True Positive Rate (TPR): Proportion of actual positives correctly classified.
- False Positive Rate (FPR): Proportion of actual negatives incorrectly classified.
- ROC Curve: Plots TPR against FPR at various thresholds.

### AUC
- Represents area under the ROC curve.
- Measures model’s ability to distinguish between positive and negative instances.

### Ranking Metrics
- **Mean Reciprocal Rank (MRR):** Average of reciprocal ranks of first relevant items.
- **Recall@k:** Ratio of relevant items in top k to total relevant items.
- **Precision@k:** Proportion of relevant items in top k.
- **Average Precision (AP):** Average precision across all positions.
- **mAP:** Mean of AP values for each list.
- **nDCG:** Normalized Discounted Cumulative Gain, measures ranking quality considering relevance scores.

### Recommender System Metrics
- **Precision@k:** Proportion of relevant items in top k recommendations.
- **MRR:** Focuses on rank of first relevant item.
- **mAP:** Average of AP values, suitable for binary relevance.
- **nDCG:** Measures ranking quality with non-binary relevance scores.
- **Diversity:** Measures dissimilarity among recommended items.

mAP, MRR, and nDCG are commonly used to measure ranking quality.
# Loss Functions and Related Concepts

## Convexity of Loss Functions
1. **Is using MSE for Logistic Regression a convex problem?**
    - No, it is not convex.

2. **Explanation and Formula for MSE**
    - Mean Square Error (MSE) is calculated as:
        - $$\text{MSE} = \frac{1}{N}\sum_{i=1}^N (Y_i - \hat{Y}_i)^2$$
    - It is the average of the squares of the errors.
    - Used in regression tasks, especially when errors are normally distributed and we want to emphasize larger errors.

3. **Relationship Between Linear Regression and MSE**
    - MSE is the objective function for the Least Squares Method in linear regression.
    - The Least Squares Method finds coefficients that minimize the sum of squared residuals, equivalent to minimizing MSE.

4. **What is Relative Entropy (KL Divergence)?**
    - Relative entropy or Kullback-Leibler (KL) divergence quantifies the difference between two probability distributions.
    - Formula: 
        - $$D_{KL}(P||Q) = \sum_{x \in \mathcal{X}} P(x) \log \left( \frac{P(x)}{Q(x)} \right)$$
    - It is the expectation with respect to distribution \(P\) of the logarithmic difference between probabilities \(P\) and \(Q\).

5. **Logistic Regression Loss**
    - The loss function for logistic regression is the log loss or binary cross-entropy.

6. **Derivation of Logistic Regression Loss**
    - Derived using Maximum Likelihood Estimation (MLE).

7. **SVM Loss Function**
    - SVM aims to find a hyperplane that separates different classes with maximum margin.
    - Uses hinge loss or squared hinge loss.

8. **Why Use Cross Entropy in Multiclass Logistic Regression?**
    - Softmax regression (multinomial logistic regression) handles multiple classes.
    - Cross entropy measures the discrepancy between predicted class probabilities and true class labels, minimizing this loss adjusts model parameters effectively.

9. **Optimization Goal When Splitting Nodes in Decision Trees**
    - Find splits that maximize separation or reduce impurity.
    - Different criteria like Gini impurity, entropy, or information gain are used depending on the algorithm.

10. **What is Log-Loss and When to Use It?**
    - Log loss measures the performance of a classification model by quantifying the discrepancy between predicted probabilities and true class labels.
    - Used in binary and multiclass classification problems.

## Logistic Regression vs SVM

1. **Differences Between Logistic Regression and SVM**
    - **Objective:**
        - Logistic Regression: Models the probability of class membership using a logistic function.
        - SVM: Finds a hyperplane to separate classes with maximum margin.
    - **Decision Boundary:**
        - Logistic Regression: Linear, dividing feature space into two regions.
        - SVM: Linear or non-linear with kernels.
    - **Loss Function:**
        - Logistic Regression: Log loss.
        - SVM: Hinge loss.
    - **Optimization Method:**
        - Logistic Regression: Gradient descent, Newton’s method, or other iterative methods.
        - SVM: Convex optimization techniques like quadratic programming or sequential minimal optimization.
    - **Robustness:**
        - Logistic Regression: Sensitive to outliers.
        - SVM: More robust to outliers due to margin maximization.

## Decision Trees

1. **How Regression/Classification DT Split Nodes**
    - **Regression:**
        - Minimizes variance or the sum of squared differences between predicted and actual values within each node.
    - **Classification:**
        - Maximizes separation or purity between different classes within each node.

2. **Preventing Overfitting in Decision Trees**
    - Pruning.
    - Setting minimum sample requirements for splitting nodes.
    - Feature selection.
    - Ensemble methods.
    - Cross-validation.
    - Maximum depth limitation.
    - Minimum impurity decrease.

## Clustering and EM Algorithm

1. **K-means Clustering**
    - **Algorithm Steps:**
        - **Initialization:** Randomly select k initial centroids.
        - **Assignment:** Assign data points to nearest centroid.
        - **Update:** Recalculate centroids as means of assigned points.
        - **Iteration:** Repeat assignment and update until convergence.
    - **Convergence:** Algorithm converges to a solution.
    - **Local vs Global Optimum:** Sensitive to initial centroid positions, may converge to local optima.
    - **Stopping Criterion:** Convergence of centroids/assignments, max iterations, or threshold on WCSS improvement.
    - **Selecting k:** Use elbow method or silhouette coefficient.

2. **What is the EM Algorithm?**
    - **Overview:**
        - Iterative optimization algorithm for estimating parameters of statistical models with latent variables.
        - **Steps:**
            - **Initialization:** Initial parameter values.
            - **E-step:** Compute expected values of latent variables.
            - **M-step:** Maximize expected log-likelihood.
            - **Iteration:** Repeat E-step and M-step until convergence.
            - **Final Parameter Estimates:** Maximum likelihood or maximum a posteriori estimates.
    - **Applications:** Clustering, mixture models, hidden Markov models, etc.

3. **What is GMM and its Relation to K-means?**
    - **GMM (Gaussian Mixture Model):**
        - Probabilistic model representing data as a combination of Gaussian distributions.
        - **Model Representation:**
            - Component weights, mean vectors, and covariance matrices.
        - **PDF:**
            - Weighted sum of Gaussian PDFs.
        - **Parameter Estimation:** Using EM algorithm.
        - **Applications:** Density estimation, clustering, anomaly detection.
    - **GMM vs K-means:**
        - GMM provides probabilistic soft assignment and accommodates various shapes and orientations.
        - K-means performs hard assignment and assumes spherical clusters with equal variance.
        - Choice depends on data nature and desired cluster characteristics.

