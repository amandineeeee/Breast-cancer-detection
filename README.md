# Detecting breast cancer using Machine Learning

The aim of this project is to predict the presence or absence of a malignant tumour on the basis of features extracted from images.
This is an application of supervised binary classification in the medical field.

The main challenge is to obtain a reliable and sensitive model, minimising false negatives in particular, so as not to miss a cancer diagnosis.

## Project construction 

The project is constructed as follows:
- loading and exploration of the dataset,
- statistical analysis and visualisation,
- pre-processing of the data,
- training and comparison of several classification models,
- performance evaluation using appropriate metrics,
- analysis of the results and areas for improvement.

## Dataset

The dataset used comes from the Wisconsin Breast Cancer Database.
It contains:
- 569 observations,
- 30 numerical characteristics derived from medical images (texture, symmetry, mean radius, etc.),
- A target variable:
    - M: malignant tumour,
    - B: benign tumour.

The dataset consists of multiple micros (samples) per patient.
A line of the dataset is a micro.
Each patient has several micros, and each micro is associated with a single patient.
Each micro has 150 features plus the associated label malignant or benign and the ID of the patient to which it belongs.
Since each subject in the dataset has multiple micros, we assume that all micros from the same subject have the same label.

## Machine Learning 

### Data pre-processing

Pre-processing includes: 
- checking for missing values,
- removing non-informative columns such as ID,
- normalising the features, 
- encoding the target variable: 
 - M = 1,
 - B = 0.

### Machine Learning models tested 

I tested the following models: 
- Logistic Regression,
- K-Nearest Neighbors (KNN),
- Support Vector Machine (SVM),
- Decision Tree,
- Random Forest, 
- Neural Network.

The hyperparameters were optimised using the `RandomizedSearchCV` method during training.
The best model was selected from the validation set and then its performance was tested on the test set. 
Feature selection was performed to improve model performance and reduce overfitting. 

Finally, to predict a patient’s overall diagnosis, I retrieve all the micros for this patient.
For each of these micros, I predict the class with my chosen model.
Then I take a majority vote on the patient's label.
That's how I get my patient's label.

## Used technologies 

- Python
- Pandas, NumPy
- Scikit-learn
- Matplotlib, Seaborn
- Jupyter Notebook

## Installing dependencies

To install the dependencies, run the following command:

```
pip install -r requirements.txt
```