![Badiaa Makhlouf](https://img.shields.io/badge/Author-Badiaa%20Makhlouf-green)
[![LinkedIn](https://img.shields.io/badge/LinkedIn-Profile-blue?logo=linkedin)](https://www.linkedin.com/in/badiaa-m-b77032116/)
[![Follow](https://img.shields.io/github/followers/badiaamakhlouf?label=Follow&style=social)](https://github.com/badiaamakhlouf)
![License](https://img.shields.io/badge/License-MIT-red)
![Last Updated](https://img.shields.io/badge/last%20updated-July%202024-brightgreen)
![Contributions Welcome](https://img.shields.io/badge/contributions-welcome-orange.svg)
![Maintained](https://img.shields.io/badge/maintained-yes-blue.svg)
# Decision trees and tree ensembles 
### 1- What is a decision tree
- Decision trees are versatile models used in supervised learning, applicable to both classification and regression tasks.
- The training set is used to build the decision tree, while the testing set evaluates its performance.
- Decision trees are often viewed as linear models, where:
  - x represents the input features.
  - y (the target) can be either:
    - Continuous (e.g., temperature). ==> Regression tree
    - Categorical (e.g., low, medium, high). ==> Decision tree
- Features (x) can be numeric or categorical and categorical features must be encoded (e.g., one-hot encoding) before being used.
- For any given application, multiple decision tree models can be constructed.
- Choosing the optimal tree involves selecting an algorithm that learns the most appropriate tree from the training data.
- Factors like splitting criteria (e.g., Gini impurity, entropy) and tree depth play a key role in defining the tree’s effectiveness and generalizability.

### 2- Structure of decision tree 
- A decision tree consists of:
  - Root Node: the starting point that represents the first decision based on the dataset.
  - Decision Nodes: intermediate nodes where splits occur based on feature values.
  - Leaf Nodes: terminal nodes that provide the final prediction (a category or value).
  - Depth: is the maximum number of edges from the root node to the farthest leaf node in a decision tree.

### 3- Learning process 
Here is a step by step guide to build a decision tree 
1. Understand the Problem: define the goal (e.g., classification or regression) and understand the dataset and identify the target variable.
2. Prepare the Dataset:
  - Clean the data via handle missing values, outliers, and duplicate data
  - Perform some feature engineering such as select relevant features or encode categorical variables if necessary.
  - Split the dataset into training and testing sets.
3. Choose a Splitting Criterion:
  - For Classification: use metrics like Gini Impurity or Information Gain (Entropy).
  - For Regression: use metrics like Mean Squared Error (MSE) or Variance Reduction.
4. Start with the Root Node: evaluate all features to find the one that best splits the data (i.e., minimizes impurity or maximizes information gain).
5. Iterative Splitting:
- **Recursive Process:** For each child node:
  - Split the data based on the chosen feature and criterion.
  - Repeat the process for each subset.
- **Stop when a condition is met**, such as:
  - Maximum depth is reached.
  - Minimum number of samples per leaf is met.
  - All samples in a node belong to the same class (pure node).
  - Further splits no longer improve the model significantly.
6. Handle Overfitting:
- **Pruning:** remove branches with low significance using techniques like post-pruning or pre-pruning.
- Set constraints such as:
  - Maximum tree depth.
  - Minimum samples per leaf or split.
7. **Validate the Model:** use cross-validation to assess the decision tree’s performance and generalizability.
8. **Test the Tree:**
  - Evaluate the decision tree using unseen test data.
  - Calculate metrics like accuracy, precision, recall (for classification), or RMSE (for regression).

### 4- Key Decisions in Splitting a Decision Tree
When building a decision tree, careful consideration of splitting criteria is essential to ensure the tree is effective, interpretable, and avoids overfitting. Here are the key decisions to address:
#### 4.1- Selecting the Feature to Split On
- How to choose the feature?
  - Prioritize features that maximize purity (homogeneity of data within nodes).
  - Minimize impurity using measures like:
    - Gini Impurity
    - Entropy (used in Information Gain)
      
#### 4.2- Stopping Criteria for Splitting
- When should splitting stop?
  - When a node is 100% pure (all examples belong to a single class).
  - When further splitting would result in the tree exceeding a specified maximum depth.
  - When improvements in the purity score (e.g., Gini, Information Gain) fall below a defined threshold.
  - When the number of examples in a node drops below a minimum threshold (prevents over-segmentation).

#### 4.3- Managing Tree Size to Avoid Overfitting
- Why control tree size?
  - An excessively large tree risks **overfitting**, meaning it performs well on the training data but poorly on unseen data.
  - Techniques to control size:
    - **Pruning:** Remove nodes that add minimal value.
    - Set limits on tree **depth** or **minimum samples per split**.
   
### 5- Decision tree learning
#### 5.1- Measuring purity
- Entropy is a measure of the impurity or uncertainty in a dataset.
- The entropy function is denoted as H(p), where p represents the probability or fraction of examples with a specific characteristic (e.g., temperature > 70°C, or the data corresponds to "dogs").
- If the entropy is high, it indicates that the impurity (or randomness) of the dataset is high, meaning the data is more mixed and less homogeneous.
- Conversely, lower entropy implies greater purity, where examples are more uniform.

#### 5.2- Choosing a split: Information Gain
- Start with all examples at the root node
- To determine which feature to use for splitting at the root node, we calculate the **weighted average of entropy** across all possible splits, not just the raw entropy.
- The feature that results in the largest reduction in entropy is selected for the split.
- This reduction in entropy is known as Information Gain: $Information \ Gain= Entropy_{root} - weighted\ average\ of\ entropy$
- Information Gain serves as a metric to identify the feature that best separates the data and should be used for splitting at each node.
- Information Gain must be calculated for all possible features, then we pick the ones with the highest value
- Split the dataset according to the selected feature and create left and right branches of the tree.
- keep repeating splitting process (on left and right branches) until stoping criteria is met :
  - When a node is 100% one class
  - When splitting a node will result in the tree exceeding a maximum deepth
  - Information Gain from additional splits is less than threshold
  - Number of examples if a node is below a threshold
- This repeatetive process is called recurisive algorithm 

#### 5.3- Features in Decision trees
- Unfortunately, decision trees do not natively handle categorical features; they require all input features to be numerical.
- To address this, encoding techniques such as one-hot encoding can be used to convert categorical features into numerical representations,
 ensuring compatibility with the decision tree model.
- For numerical features, we determine a threshold to split the data, calculate the information gain for each potential threshold,
 and select the threshold that yields the highest information gain.
#### 5.4- Regression Decision tree
- To split data in a regression decision tree, calculate the reduction in variance between the raw data and the data after the split.
- Evaluate all feature options for splitting, select the one with the highest variance reduction, and repeat the process for the left and right nodes until stopping criteria are met.

### 6- Tree ensembles
- A single decision tree can sometimes perform poorly as it is highly sensitive to small changes in the data.
- Using multiple decision trees in an ensemble helps make the algorithm less sensitive and more robust.
- The idea behind tree ensembles is that by combining the outputs of many decision trees through voting, the overall algorithm becomes less influenced by the behavior of any single tree.
- To construct a tree ensemble, a technique called sampling with replacement (bagging) is often used.
- Common algorithms that utilize tree ensembles include Random Forest and XGBoost.

























