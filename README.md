# Comparing Classifiers

This practical application assignment looks at comparing different classifers in
the context of a targeted marketing campaign. Please see the associated IPython
notebook (Analysis.ipynb) to see the full deatils of the analysis.

## The Business Problem

Targeted marketing increase the return on investment for marketing budgets. Machine
Learning Models can help in this regard by predicting if someone will respond
to marketing by purchasing a good or service. I this example we will fit models
to predict if individuals will subscribe to a term deposit. The resulting predict
will be a binary outcome, 'Yes' or 'No'.

## The Methodology

We fit several different models to find the best predictor. A standard scaler was used on numeric variables and categorical variables were one hot encoded. Below is a list of the models:

- Baseline Classifier: This model simply predicts the majority target class all of the time. It is used as a baseline of comparision as this
  is an imbalanced classification problem.
- Simple Logistic Regression: A simple logistic regression agains all of the descriptive features.
- K Nearest Neighbors Classifer - A KNN classifier is used considering polynomial transformations of the descriptive features, as well as doing grid search across the number of neigbors used.
- Optimized Logistic Classification - In this case we use logistic regression with regularization that has been optimized using grid search across the parameter values of `C`.
- Decision Tree: We then use a decision tree with optimized parameters.
  Optimized parameters include: Min. Impurity Decrease, Max. Depth, Max. Features, Min. Sample Split, Criterion.
- Support Vector Classifier: SVC with some parameter optimization across the parameters C, and the kernel function type.

## Metrics and Results

### Metrics

We looked primarily at two metrics, accuarcy and recall. Accuracy is a very common metric and often facilitates communication around results. As the business is looking to maximize the revenue derived from the targeted marketing campaign, we consider recall with tells us how many term deposit subscribers we predicted correctly of all that subscribed to term deposit.

### Results

The below table show timings, accuracy and recall results for the various models.
As you can see results across the models were strong with even the Baseline model
scoring 88% accuracy on the test set. The optimized logistic regression had the
best accuracy of all of the models.

The recalls were much weaker. The Logistic scored the highest with ~40% recall on the
testing set. SVC was second highest with ~36%.

| Model               | Train Time   |   Train Accuracy |   Train Recall |   Test Accuracy |   Test Recall |
|:--------------------|:-------------|-----------------:|---------------:|----------------:|--------------:|
| Baseline            | 0.000m       |         0.887346 |       0        |        0.887346 |      0        |
| Logistic Regression | 0.035m       |         0.911819 |       0.429023 |        0.911042 |      0.401724 |
| KNN                 | 1.861m       |         0.915833 |       0.39569  |        0.898708 |      0.292241 |
| Logistic Optimized  | 0.053m       |         0.911851 |       0.429885 |        0.911236 |      0.402586 |
| Decision Tree       | 0.350m       |         0.889741 |       0.233046 |        0.888705 |      0.225862 |
| SVC                 | 99.14m       |         0.927001 |       0.479023 |        0.907643 |      0.361207 |

## Conclusions

To support our targeted marketing effort, Optimized Logistic regresion would be the
best model. It showed the best results on both test set accuracy and test set recall.

## Future Steps

If we are further willing to trade off accuracy for better recall results we could
uses threshold on predicted probabilities to further improve the recall,

