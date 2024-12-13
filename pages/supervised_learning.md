# Machine Learning :Supervised Learning




# Classification 
## 1- Evaluation metrics 
- accuracy
- confusion matrix
- precision
- recall
- f1-score
- auc- roc

## Skewed datasets
### 1- Error metrics for skewed datasets 
- In classification problems, accuracy alone may not provide a complete picture of how well your model is performing, especially when the data is skewed or imbalanced.
- Here’s how to effectively assess model performance:
#### 1.1- Limitations of Accuracy in Imbalanced Datasets
- Using accuracy as a metric can be misleading in cases of imbalanced datasets.
- For instance, if you have 1% error on a test set, it might seem like your model is performing well. However, in scenarios like rare disease detection, this could be due to data imbalance where we have 1000 samples of class 0 (no disease) and 100 samples of class 1 (disease present).
- In such cases, the accuracy is 99.9% but does not accurately reflect the model’s true performance.

#### 1.2. Alternative Evaluation Metrics
- It’s crucial to use different error metrics to better understand the model’s effectiveness.
- Precision, recall, and confusion matrix are useful tools:
  - Precision focuses on the proportion of correct positive predictions (true positives) among all positive predictions (true positives + false positives).
  - Recall measures the proportion of correct positive predictions (true positives) among all actual positives (true positives + false negatives).
- These metrics help to identify if your model is just predicting 0 all the time or if it’s making meaningful predictions.
- By using precision, recall, and confusion matrix, you can gain a more nuanced understanding of your model’s performance, especially in the context of imbalanced datasets.

### 2- Trading off precision and recall
- In case of logistic regression :
  -  0<f(x)<1
  -  Predict 1 if f(x) ≥ 0.5 ==> 0.7, we predict y=1 (rare disease) only if we are very confident
  -  Predict 0 if f(x) < 0.5 ==> 0.7
  -  Increasing the threshold from 0.5 to 0.7 leads to higher precision and lower recall.
  -  Again, if we increase the threshold we will get more higher precision but in this case we can miss too many cases of rare disease
  -  Decreasing the threshold will result in lower precision and higher recall
  -  To choose the right threshold, it is good to plot precision and recall for different values of the threshold.
  -  Also the right threshold must be chosen by you in most of cases as you understand what you want from the model you are building and how this system will be used.
  -  Your main goal is to choose an algorithm that has good result on both recall and precision and here you can use either average or F1-score.
  -  Calculate the average between precisiona and recall then, pick the algorithm that gives the highest average. ==> However it is not recommended as sometimes it is useless and pick the wrong result
  -  F1-score is a good metric to use to resolve the trade off between precision and recall as it combines both of them.
  -  F1-score in mathematic called the harmonic mean of Precision and Recall
  -  Finally, choose the algorith that has the highest f1-score
 

















  
