# Cancer Stages Classifications - Kaggle

## Author: Danh Nguyen and Daniel Carrera

### Report: Using MicroRNAs to Predict Early-Stage Cancers
### Abstract:
- The goal of our project is to design a model that can predict the presence of various cancers based on the expression of 979 microRNA. Many cancers do not show symptoms in their early and mid stages. Unfortunately, once a person seeks treatment and is diagnosed, the cancer is often in its late stages where survival rates are very low. If cancer can be detected earlier in its progression, then survival rates are much higher and many lives may be saved.
To do this we will be training our model on 3 different classification algorithms: Random Forest, XGB, LGB, and stacked combinations of these models. Our dataset consists of 979 microRNAs and their accompanying levels of expression in extracted body fluids from patients who are healthy and those who have been diagnosed with a type of cancer. Our target is made up of five classes, zero is no cancer and the other four refer to different stages of cancer.

### About the Data
- Our dataset is a combination of 21 datasets from different studies and has 8,302 rows and 979 columns. One of the columns is an I.D. indiciating from which dataset those observations came from, another is our target variable that indicates the presence of cancer, and the remaining columns refer to expression levels of 977 microRNAs. The datasets have different contribution percentages to our overall number of observations with dataset ID 16 contributing the most at over 6.5% of all observations and data set ID 10 contributing the least at a little over 3%. Our target to predict, presence of cancer is very imbalanced and is made up of 5 classes. With class 0 being represented the most at nearly 50% and class 4 being represented the least at less than 0.3%. Each of these classes are unique to its corresponding dataset. There are no null values in our dataset. And the expression levels of each microRNA seems to have already been standardized to a range between 0 and 1.

[Data Pattern](data.png)

### Feature Engineering and ML Methods
- First, to deal with the issue of our imbalanced targets, we employed over-sampling methods. We did this two ways: 1) we up-sampled all of the targets to reach the majority’s level of representation. What this meant is that each target now had equal representation, see figure below to the left. 2) we employed up-sampling on only the most minority class, which was target 4, see figure below to the right. What this meant though is that the very few observations of target 4 were now highly duplicated until they matched the frequency of the majority class.
Since these “new” observations were all the same observation, our model would not garner much information from them due to a lack of variance.
To deal with the issue of high dimensionality, we used PCA (principal components analysis) to capture just the features that contained 95% of the variance of our dataset. This reduced the number of features from 979 to 693.
Given that our dataset is in a tabular format we decided to go with tree methods and apply Random Forest, XGB, and LGB models and then adjusted hyperparameters for optimal performance, which we will speak to in the next section. A few things we noticed were that most models when applied to the original data all resulted in accuracies that hovered around 70%. When we applied them to the over-sampled datasets we saw that these models over-fit on the training data, which makes sense considering that these over-sampled contained several duplicated observations and is not very representative of the real target distributions. We saw that PCA did help somewhat in improving our accuracies as our model had slightly less features to consider, shaving off a little of the overfitting.
In the end, our two model choices were an LGBM model+PCA and an XGBT model+PCA. Next, we will speak to the hyperparameters we chose.

### Hyperparameter Tuning
- For each of our two final models, we used sklearn’s RandomizedSearchCV that searched 40 random combinations from a wide range of values for specified parameters and returned the best model’s parameter values. The parameters we had to consider were the number of trees, he maximum features considered on splits, the minimum samples allowed per lead, learning rate, and the maximum depth of the decision trees. For our XGBT model, the best parameters were 500 trees and a learning rate of 0.001, this gave a validation accuracy of about 83%. For our LGBM model the best parameters were 800 decision trees at depths of 500. We applied this to our dataset after applying PCA and received a validation accuracy of about 85%. When submitted to Kaggle, the test accuracy was about 71%, so there was definitely some overfitting still going on.

### Statement of responsibility:
Daniel and Danh are both equally responsible for all aspects of this project.
