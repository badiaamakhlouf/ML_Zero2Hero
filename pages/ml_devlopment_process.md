![Badiaa Makhlouf](https://img.shields.io/badge/Author-Badiaa%20Makhlouf-green)
[![LinkedIn](https://img.shields.io/badge/LinkedIn-Profile-blue?logo=linkedin)](https://www.linkedin.com/in/badiaa-m-b77032116/)
[![Follow](https://img.shields.io/github/followers/badiaamakhlouf?label=Follow&style=social)](https://github.com/badiaamakhlouf)
![License](https://img.shields.io/badge/License-GPL--3.0-red)
![Last Updated](https://img.shields.io/badge/last%20updated-July%202024-brightgreen)
![Contributions Welcome](https://img.shields.io/badge/contributions-welcome-orange.svg)
![Maintained](https://img.shields.io/badge/maintained-yes-blue.svg)

# Machine Learning Development Process

- Developing a machine learning (ML) model is an iterative process that often involves repeating certain steps to refine the model and improve its performance. Below are the key stages involved:
  - Choose the architecture
  - Model training
  - Result analysis and interpretation
  - Take the Next Steps
  - Model Deployment
- By embracing this iterative approach, developers can systematically refine their ML models to achieve optimal performance and reliability.


## 1- Choose the architecture 
- First, define the problem to solve: is it classification, regression, or clustering?
- Next, clean the data, analyze it, and preprocess it to extract meaningful insights and assess data quality.
- Data wrangling helps determine if the dataset is sufficient for the task and aids in selecting the feature set for the next steps.
- Then, choose the appropriate model, including hyperparameter tuning, such as selecting the number of clusters in a clustering algorithm or deciding the number of nodes and layers for a neural network.
- Finally, split the data into training and testing sets, or include a validation set if necessary.

## 2- Model training 
- The second step in the ML development process is training the selected model.
- During this step, hyperparameter tuning can be performed using methods like GridSearch to find the optimal parameters.
- Optimizing performance through techniques like gradient descent or other optimization algorithms.
- Achieving good results on the first training attempt is unlikely, making the next step which is result analysis and interpretation is essential.

## 3- Result analysis and interpretation
- During this step, we evaluate diagnostics such as the bias-variance tradeoff and perform error analysis to assess the results.
- Based on the investigation, we determine whether the model's performance is satisfactory or if further improvements are needed.
- Diagnostics guide the next steps, helping us decide whether to accept the current results, add more data, modify features, or adjust the model architecture etc.
- Actually, performing different diagnostics helps to give various guidance on what choices for the model or data, or other parts of the architecture could be most promising to try.

### 3.1- Diagnosing bias and variance 
- It is important to find a good trade off between bias and variance to ensure that our algorithm perform very well.
- For high bias: underfitting, performance is bad on all sets: training, validation and testing (J is high for all)
- For high variance: overfit, performance is good ($J_{train}$ is low )on training but very bad (($J_{train}$ is high))on both validation and testing sets.
- **Note:** $J_{cv}$ is always high than $J_{train}$, only in case of underfitting: $J_{cv}≈J_{train}$
- It is possible to habe high bias with high variance, but still $J_{cv}>>J_{train}$
  
### 3.2- Error analysis 
- For result analysis, start with a bias-variance diagnostic, followed by error analysis in the next round.
- In classification problems, for example:
  - Review misclassified samples or incorrect predictions to understand why the algorithm made mistakes.
  - Group these errors by shared characteristics to identify patterns.
  - If the number of misclassified samples is very high (e.g., 800), randomly sample a subset for review instead of analyzing all samples.
  - Often, a small subset is enough to provide a clear overview without examining every error.
- As mentioned earlier, this analysis helps determine the next steps to improve performance.
- Error analysis is straightforward for tasks humans excel at but more challenging for problems where even human performance is weak, such as predicting which books someone might purchase.

## 4- Taking next steps
Based on the analysis, decide the course of action:
  - Collect additional data.
  - Refine features or engineering techniques.
  - Adjust the model architecture or hyperparameters.
  - Address performance issues like bias or overfitting.
    
### 4.1- Improve Data Quality
- Collect more representative data if feasible.
- Address data imbalances or inconsistencies identified during the analysis.
- However, we still have some limitations, such as situations where acquiring additional data is not possible, slow, or costly.
- If adding more data is possible, prioritize data similar to previously misclassified samples.
- Alternatively, use data augmentation which is a widely used technique for image and audio data, to significantly expand the training set.
- Data augmentation involves modifying existing training examples to generate new ones.
- Example: **Data Augmentation for Images:**
  - Basic techniques include slight rotations, enlarging or shrinking the image, or adjusting contrast which are referred to as distortions.
  - Advanced methods involve more complex transformations, such as random warping of a grid where a letter is written.
- Example: **Data Augmentation for Speech:**
  - Adding background noise, such as sounds from a car or a crowd.
  - Simulating poor audio quality, like that from a bad cellphone connection.
- An important consideration in data augmentation is ensuring that the changes or distortions applied to the data are representative of the noise or distortions could exist in the test set.
- Data synthesis is a technique where entirely new examples are created from scratch, rather than modifying existing ones.
- Synthetic data generation has been widely used in computer vision tasks but less frequently in other applications.
- In conclusion, it’s crucial to carefully engineer the data used by our machine learning system.
- $$ML/AI \ system = Data + Code\ (algorithm/model)$$.
- To enhance the system, you must not only improve the code but also the data.
- Focusing on improving the code is known as a conventional model-centric approach, while focusing on data engineering is referred to as a data-centric approach.

### 4.2- Trasfert learning: using data from a different task
- It is commonly used in applications where insufficient data is available for the current project, particularly in computer vision tasks.
- In such scenarios, there are two options:
    - Train all parameters from scratch: This approach can be ineffective when data is limited.
    - Use transfer learning:
      - Retain the initial layers of a pre-trained neural network, including their parameter values, while replacing the final output layer and its parameters.
      - Apply an optimization algorithm, such as gradient descent or Adam, to fine-tune the model.
      - Utilize the pre-trained parameters as a starting point for optimization.
- If a large dataset is already available, approach 1 (training from scratch) may be a better choice than using transfer learning.
- When using transfer learning:
  - The algorithm starts with parameters in a much better state, requiring only minimal additional learning.
  - The process involves two key steps: supervised pre-training and fine-tuning.
  - **Supervised pre-training:** The model is trained on a very large dataset, such as a million images, typically for a task that is not directly related to the target application.
  - **Fine-tuning:** The pre-trained parameters are further optimized using gradient descent to adjust the weights for the specific task. ==> further train
- Transfer learning allows us to leverage parameters obtained from training on a different application, such as recognizing cats, dogs, cars, or people, to help with tasks as distinct as recognizing handwritten digits.
- **How is this possible?**
  - The early layers of a neural network typically learn generic features, like edges, shapes, corners and textures, which are applicable across a wide range of tasks.
  - By reusing these pre-trained layers, the model benefits from prior learning, even if the target task is significantly different.
  - Fine-tuning the later layers enables the network to specialize for the new task.

## 5- ML project full cycle 
- Here are the list of steps to think about when we build a ML project:
  - Scope project: define the problem and the goal
  - Data collection: define and collect required data
  - Model training : training, error analysis and iterative improvment
  - Deploy in production: deploy, monitor and maintain system
- During model training, if the model performance was very poor so in this case we can go back to step 2 and perform data preprocessing or collect more data.
- Again, in case the deployed model gave some errors during monitoring, we can go back to either data collection step or model training.

## 6- Ethical Considerations in ML Systems
Building machine learning (ML) systems requires careful consideration of ethical implications to ensure fairness, reduce bias, and prevent harm. Below are key guidelines and considerations for an ethical approach:

### 6.1- Prioritize Fairness and Minimize Bias
- The primary goal is to create an ML system that is fair and free from unreasonable bias.
- Unfortunately, some ML systems exhibit unacceptable levels of bias, leading to discriminatory outcomes.
- Examples of Bias in ML Systems:
  - Hiring tools that discriminate against women.
  - Facial recognition systems misidentifying individuals with darker skin as criminals.
  - Biased bank loan approval processes.

### 6.2- Recognize Adverse Use Cases
- ML systems can have harmful applications, including:
  - Deepfakes used to spread misinformation or for malicious purposes.
  - Generating fake content for political or commercial exploitation.
  - Creating harmful products or tools.
 
### 6.3- Engage in Ethical Pre-Build Practices
- Assemble a diverse team to identify potential risks and brainstorm potential harms, especially to vulnerable groups.
- Conduct a literature review of industry standards and ethical guidelines relevant to the application.
- Identify and address ethical challenges early to prevent harm and ensure system reliability.

### 6.4- Audit and Test for Bias
- **Pre-deployment Audits:**
  - After the training phase, evaluate the system for potential bias against specific genders, ethnicities, or other subgroups.
  - Conduct rigorous testing to identify and address any issues before deployment.

- **Post-deployment Monitoring:**
  - Continuously monitor the system for unintended harm or biases.
  - Develop and implement mitigation strategies where necessary.

### 6.5- Prepare a Mitigation Plan
- Develop a contingency plan to address unexpected problems after deployment.
- A simple and effective mitigation strategy is to **roll back to a previously trusted system**.
  - This ensures operations can continue smoothly while issues are resolved.
    
By following these steps, organizations can ensure their ML systems are ethical, reliable, and beneficial for all users.


















































