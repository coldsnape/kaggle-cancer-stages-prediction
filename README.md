# Cancer Stages Classifications - Kaggle

## Author: Danh Nguyen and Daniel Carrera

### Report: Using MicroRNAs to Predict Early-Stage Cancers
### Abstract:
- The goal of our project is to design a model that can predict the presence of various cancers based on the expression of 979 microRNA. Many cancers do not show symptoms in their early and mid stages. Unfortunately, once a person seeks treatment and is diagnosed, the cancer is often in its late stages where survival rates are very low. If cancer can be detected earlier in its progression, then survival rates are much higher and many lives may be saved.
To do this we will be training our model on 3 different classification algorithms: Random Forest, XGB, LGB, and stacked combinations of these models. Our dataset consists of 979 microRNAs and their accompanying levels of expression in extracted body fluids from patients who are healthy and those who have been diagnosed with a type of cancer. Our target is made up of five classes, zero is no cancer and the other four refer to different stages of cancer.

### About the Data
- Our dataset is a combination of 21 datasets from different studies and has 8,302 rows and 979 columns. One of the columns is an I.D. indiciating from which dataset those observations came from, another is our target variable that indicates the presence of cancer, and the remaining columns refer to expression levels of 977 microRNAs. The datasets have different contribution percentages to our overall number of observations with dataset ID 16 contributing the most at over 6.5% of all observations and data set ID 10 contributing the least at a little over 3%. Our target to predict, presence of cancer is very imbalanced and is made up of 5 classes. With class 0 being represented the most at nearly 50% and class 4 being represented the least at less than 0.3%. Each of these classes are unique to its corresponding dataset.
