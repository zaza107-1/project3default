# Prediction of cardiovascular diseases using Azure Machine Learning workspace

Our project is about cardiovascular diseases. 
The main object is to create a model with the best accuracy possible as to predict heart diseases.

## Project Set Up and Installation

We are using the Microsoft Azure Machine Learning platform to create some models using the Python SDK platform.
First we load the dataset into our ML workspace.
We are using jupyter notebooks to create all the steps needed to create, register and deploy the models.


## Dataset
We got the heart_failure_clinical_records_dataset from Kaggle.
We have 13 columns with age, blood preasure, anaemia, diabetes, sex, smoking, etc.
We are trying to predict the Death_Event column that has 0 or 1.

### Overview
The idea is to introduce some data of one person with their age, sex, smoking condition, etc and try to predict if we are going to have a death_event.

### Task
We will use the advantages of the AutoML from Azure to obtain the best model to use with our predictions.

### Access
We are accesing the data through our notebook and loading it in our datastore.

## Automated ML
In the AutoML processa, we are doing a Classification regression algorithm with the labeled data.
Our primary metric is 'Accuracy'.
The settings in our AutoML experiment are:
compute_target: we select a compute cluster that already exist or create one new with our specifications
task: we used Classification algorithm
training_data: we select the dataset that we got from kaggle
label_column_name:"DEATH_EVENT" that has 2 different values, 0 or 1
path: we select the project folder
enable_early_stopping= True, 
featurization= 'auto',
debug_log = "automl_errors.log"
"experiment_timeout_minutes": 15,
"max_concurrent_iterations": 5,
"primary_metric" : 'accuracy'

### Results
The best model that we got is a VotingEnsemble model with an accuracy of 0.87299

- AutoML best model:
![](https://github.com/zaza107-1/project3default/blob/branch2/screenshots/autoML_bestmodel.jpg)


- AutoML rundetail widget:
![](https://github.com/zaza107-1/project3default/blob/branch2/screenshots/autoMLrundetailwidget.jpg)

- Voting Ensemble model:
![](https://github.com/zaza107-1/project3default/blob/branch2/screenshots/autoMLrundetailwidget2.jpg)

- AutoML completed run:
![](https://github.com/zaza107-1/project3default/blob/branch2/screenshots/auto_ML_completed2.jpg)

- AutoML models:
![](https://github.com/zaza107-1/project3default/blob/branch2/screenshots/automlmodels.jpg)

- Best run metrics for the voting ensemble model:
![](https://github.com/zaza107-1/project3default/blob/branch2/screenshots/bestautomlmetrics.jpg)


## Hyperparameter Tuning
We used the hyperparameter tuning with a random sampling of parameter C and max_iter and a median stopping policy as the early termination policy.
About the parameter C we used three possible values, 1,10 and 100.
About max_iterations we used 50,100 and 150.

- Here we can see a picture of the two parameters and the range that we used:
![](https://github.com/zaza107-1/project3default/blob/branch2/screenshots/param_sampling.jpg) 

### Results
We found the same accuracy results for all the possible combinations. In the future we should try to change the parameters to see if we can get a better accuracy.
All possible combinations of C and max_iter gave the same accuracy of 0.7575
The best hyperparameter value could be any of the 3 values selected for C and max_iter.

- AutoML model result:
![](https://github.com/zaza107-1/project3default/blob/branch2/screenshots/automlmodels.jpg)

- Hyperparameter model result:
![](https://github.com/zaza107-1/project3default/blob/branch2/screenshots/hyperparameter.jpg)
![](https://github.com/zaza107-1/project3default/blob/branch2/screenshots/hyperparameter2.jpg)


- Hyperparameter best run:
![](https://github.com/zaza107-1/project3default/blob/branch2/screenshots/hyperparameter_best_run.jpg)

- Hyperparameter model child runs:
![](https://github.com/zaza107-1/project3default/blob/branch2/screenshots/hyperparameter_child_runs.jpg)

## Model Deployment
Using the Python SDK and the jupyter notebook we deployed the best_run of the models got through the AutoML process.
First we register the model and then we deploy it.
We got and endpoint with authentication disabled, where we can send a request and retrieve a result of the predicted column Death_event.

- Example of data input:

![](https://github.com/zaza107-1/project3default/blob/branch2/screenshots/example_data_input.jpg)

- Active healthy endpoint:
![](https://github.com/zaza107-1/project3default/blob/branch2/screenshots/healthy_endpoint.jpg)

- Endopoint response (with prediciton of value 1):
![](https://github.com/zaza107-1/project3default/blob/branch2/screenshots/endpoint%20response.jpg)


## How to improve the model
We should try with different values of C and max_iter in the hyperparameter tuning process as to get better results for the Accuracy metric.
We could also try to get a dataset with more observations, as to train better both models to check if we can improve the accuracy with a larger dataset.

## Screen Recording
Here you can find the link with the screen recording of the model working properly.

https://youtu.be/WRmW5INRNLc

