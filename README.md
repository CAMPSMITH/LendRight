# LendRight

A predictive machine learning model that assesses credit worthiness of peer-to-peer borrowers. 
Logistic regression models are used to analyze historical borrower data in order to develop a model that can accurately predict loan risk.

---

## Overview of the Analysis

The objective of the analysis was to develop a model that is effective at predicting risky loans.  The inherent challenge in this analysis is that the frequency of risky loans is far less than that of non-risky loans, leading to a significant class imbalance in the available historical dataset.

The model was trained on historical loan data that included loan size, interest rate, borrower income, detch to income ratio, number of accounts, number of derogatory marks, total debt and loan status (aka label) to flag the high risk loans. 

In a cursory examination of the dataset, by using `value_counts` it was observes that the historical dataset consisted of 75,036 loans with a status of 0 (not risky) and 2,500 loans with a status of 1 (high risk loan).

Since the historical loan data included a class label of high risk (loan status = 1) or not high risk (loan status = 0), the approach used was a supervised machine learnign approach.  

Before training models, the data was prepared.  The historical loan data was retrieved.  The data features, e.g. loan size, interest rate, borrower income, detch to income ratio, number of accounts, number of derogatory marks, and total debt were gathered into a dataframe (X).  The associated labels were gathered into a separate dataframe (y).

The data was then split into a training data set and a testing data set.  Separating the dataset is an important part of the process.  Typically, 75% of the dataset is used to create the training dataset.  The remaining 25% is reserved to test the model.  The model will be trained using the training dataset.  

To assess the effectivenss of the model, the model will be used to make predictions on the test data, predicting whether the loans in the testing dataset are high risk (1) or not (0).  The resulting predictions will be compared with the actual classification of the test loans.  The results will can be analyzed to determine the effectiveness of the model.

The model used in this analysis was sklearn's LogisticRegression model.  Initially the model was trained with the original dataset.  In this original model, there was a large imbalance in the classes, far more not hisky loans than high risk loans.

Since a large imbalance was noted, a second model was also assessed.  Prior to training the second model, imblearn's RandomOverSampler was used.  This randomly over sampled the class with the smaller population (high risk loans) in order to make it the same size as the larger class (not high risk loans).  This resulted in a larger training dataset where each class had the same number of records.  The model was trained on this resampled dataset.  

To evauate the effectiveness of each model, a confusion matrix, model accuracy score and the classification report, which provided key metrics such as precision, recall and F1, were produced and analyzed.  

## Results

* Machine Learning Model 1 - original dataset with significant class imbalance:
  * **Accuracy:** 0.952

  | Class | Precision | Recall |
  |-------|-----------|--------|
  |   0   |  1.00     |  0.99  |
  |   1   |  0.85     |  0.91  |

* Machine Learning Model 2 - dataset with random oversampling:
  * **Accuracy:** 0.9937

  | Class | Precision | Recall |
  |-------|-----------|--------|
  |   0   |  1.00     |  1.00  |
  |   1   |  1.00     |  0.91  |


## Summary

After leveraging random oversampling, the accuracy of the model improved to 99.4%, an improvement of 4.2%.

For Class 0, the precision of the model with random oversampling was 100%, indicating that all of the class 0 predictions were indeed actual class 0 items. Recall for class 0 improved to 100%, indicating that the model with random oversampling correctly classified all of the actual class 0 items as class 0.

For Class 1, the precision of the model with random oversampling was also 100%, indicating that all of the class 1 predictions were indeed actual class 1 items, a significant improvement of about 15% over the original model. Recall for class 1 remained 91%, indicating that the model with random oversampling correctly classified 91% of the actual class 1 items as class 1.

The model that leveraged random oversampling was significantly better at correctly predicting high risk loans.  It was also nearly perfect at predicting loans that were not high risk

Since the costs and damages of loans going bad are high, it is extremely important to be able to accurately predict high risk loans.  It is therefore recommended that the model which used random over sampling be used to predict and classify high risk loans.

---

## Technologies

* **Pandas**  - A python library with advanced financial analysis tools.
* **Jupyter Lab** - An IDE used for visualization.
* **anaconda** - A python framework consisting of several tools used in financial analysis, such as Pandas and Jupyter Lab.
* **hvplot** - A set of Python visualization tools used to create compelling, and interactive visualizations.  
* **sklearn** - An open-source Python library offers algorithms and models for building machine models.
* **imbalance-learn** - An open-source Python library complements sklearn and provides tools for handling datasets with significant imbalances in label classes.

---

## Installation Guide
To install imbalanced-learn, execute the following command in your virtual environment prior to starting jupyter lab.
### imbalance-learn
```
conda install -c conda-forge imbalanced-learn
```

### Start Jupyter Lab
Once your conda virtural environment is started with all prerequisites, start Jupyter Lab:
```
jupyter lab
```

---

## Usage
Once Jupyter Lab has started in your browser, select the **crypto_investments.ipynb** notebook from the **Left Sidebar**.  This is the main analytical notebook.

![launch Notebook.ipynb](images/start_notebook.png)


---

## Contributors

*  **Martin Smith** <span>&nbsp;&nbsp;</span> |
<span>&nbsp;&nbsp;</span> *email:* msmith92663@gmail.com <span>&nbsp;&nbsp;</span>|
<span>&nbsp;&nbsp;</span> [<img src="images/LI-In-Bug.png" alt="in" width="20"/>](https://www.linkedin.com/in/smithmartinp/)


---

## License

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE)