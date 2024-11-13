



## Model evaluation 
### Q- Why model evaluation is essential in model development lifecycle ?
- This steps comes after building your model taking into consideration the model tunning and optimization
- What to do next ?  How to decide which decision to take while building a ml model
Here is some advices :
 - In case you implemented a linear regression model to predcit air quality inside offices, after evaluation using one of the famous metrics such as MSE, MAE etc. you find that you still have some large errors in prediction
 - Here are some solutions :
   - Check Overfitting 
   - Increase training data size
   - Reduce the number of features
   - Try more or new sets of features such as polynomial $x^2, x^3, x_1x_2$
   - Use regularization term
   - Increase or decrease the shrinkage parameter
   - etc.
- Generally, it is important to perform some diagnostic such as running some tests to understand why your model is not performing very well and find the right path to improve the performance of your algorithm.
- Unfortunatelly, diagnostic tests can be too much time consuming but doing it in the right way can be very useful and guide you through the right decision

### Q- How to evaluate your model ?
- In case our model is performing very well on the training data but has extremely poor performance on testing dataset ==> **Overfitting**
- If your model uses a single feature, such as the Occupancy rate then you can plot it: y(indoor air quality) versus x(Occupancy rate).
- If your model uses more than one feature : $x_1, x_2, x_3$ etc. then plotting it, will be critical somehow. 

