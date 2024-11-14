## Model Evaluation
### Q- Why model evaluation is essential in model development lifecycle ?
- This steps comes after building your model taking into consideration the model tunning and optimization
- What to do next ?  How to decide which decision to take while building a ml model
Here is some advices :
 - In case you implemented a linear regression model to predcit air quality inside offices, after evaluation using one of the famous metrics such as MSE, MAE etc. you find that you still have some large errors in prediction
 - Here are some solutions :
   - Check overfitting 
   - Increase training data size
   - Reduce the number of features
   - Try more or new sets of features such as polynomial $x^2, x^3, x_1x_2$
   - Use regularization term
   - Increase or decrease the shrinkage parameter
   - etc.
- Generally, it is important to perform some diagnostic such as running some tests to understand why your model is not performing very well and find the right path to improve the performance of your algorithm.
- Unfortunatelly, diagnostic tests can be too much time consuming but doing it in the right way can be very useful and guide you through the right decision

### Q- How to evaluate your model ?
- This step comes after splitting the dataset into training (70% to 80%) and testing (30% to 20%), sometimes we use validation set around 10% of our training data.
- Training the model aims to find weights w and b where y=w*x+b, and to minimize the cost function which corresponds to error expression plus a regularization term.
- The evaluation of the model is performed on the testing set via computing the test error but the method of evaluation differs depending on whether the task is classification or regression.
- **Regression:**
  - Evaluation relies on metrics such as Mean Squared Error (MSE) or R². 
  - The MSE or the MAE etc. ==> Without regularization term.
  - In case our model is performing very well on the training data but has extremely poor performance on testing dataset ==> **Overfitting**
  - To understand how your model is doing on the training set, it is possible to calculate the training error.
  - And again it is without the regularization term unlike the cost function you are minimizing to fit the parameters.
  - If your model uses a single feature, such as the Occupancy rate then you can plot it: y(indoor air quality) versus x(Occupancy rate).
  - If your model uses more than one feature : $x_1, x_2, x_3$ etc. Then plotting it, will be critical somehow.

- **Classification:**
  - Evaluation uses metrics like accuracy, precision, recall, F1-score, or AUC (Area Under the Curve).
  - Generally, to evaluate a classification model, it is more robust to evaluate the fraction of the test set and the fraction of train set that have been misclassified

## Model selection 
- It aims to experiment with different algorithms to find the best fit for the data.
- Choosing the best model for a given machine learning application depends on its performance on the testing data.
- Sometimes the model can have good performance on the training data and very poor performance on the testing data ==> overfitting.
- In order to improve the performance of the model during the training phase, it is possible to use a cross-validation set and crosss-validation techniques  
- Several methods can be adopted before selecting the final model, this step is called model tunning and optimization.

### Cross- validation set and techniques
#### Cross- validation set
- Cross validation set aims to split our data as follow : 60% for training, 20% for cross validation and 20 for testing
- It can be called cross-validation set or validation set or development set or dev set.
- Cross validation set is a small portion of data used to check the validity of the model during training.
- In this case we evaluate the next three errors:
  - Training error
  - Cross validation error
  - Test error
- For example, we can train various models on the same dataset:
  - $f_{w,b}(x)  = w_1x +b$ ==> evaluate the validation set error
  - $f_{w,b}(x)  = w_1x + w_2x^2 + b$ ==> evaluate the validation set error
  - $f_{w,b}(x)  = w_1x +w_2x^2+ w_3x^3+ b$ ==> evaluate the validation set error
  - etc.
- For example we can say that the third model, which has d=3 (degree of polynomial) is the best as it gives the lowest validation set error.
- As a next step, we estimate the generalization error using the test set and if we get good performance then, we pick this model as our final model.
- The same approach could be considered to choose the adequate neural network architecture.

#### Cross- validation techniques
- and hence can help preventing model overfitting

## Improve the performance of a Machine learning algorithm
- To decide how to improve the performance of a ml algorithm, it is possible to run some diagnostics.
- Bias and Variance is the most powerful diagnostic.

### Bias and Variance




- Several methods can be used to improve the performance of a machine learning model.
- Each of these techniques can significantly impact the model's overall effectiveness.
- Here are some common approaches:
  - Feature Engineering: Enhance input data by creating new features or refining existing ones.
  - Hyperparameter Tuning: Adjust model parameters to optimize performance.
  - Regularization: Apply techniques like L2 or dropout to prevent overfitting.
  - Ensemble Methods: Combine multiple models to achieve better accuracy.
