*NOTE:* This file is a template that you can use to create the README for your project. The *TODO* comments below will highlight the information you should be sure to include.

# Your Project Title Here

*TODO:* Write a short introduction to your project.
Our project is about cardiovascular diseases. 
The main object is to create a model with the best accuracy possible as to predict heart diseases.

## Project Set Up and Installation
*OPTIONAL:* If your project has any special installation steps, this is where you should put it. To turn this project into a professional portfolio project, you are encouraged to explain how to set up this project in AzureML.
We are using the Microsoft Azure Machine Learning platform to create some models using the Python SDK platform.
First we load the dataset into our ML workspace.
We are using jupyter notebooks to create all the steps needed to create, register and deploy the models.


## Dataset
We got the heart_failure_clinical_records_dataset from Kaggle.
We have 13 columns with age, blood preasure, anaemia, diabetes, sex, smoking, etc.
We are trying to predict the Death_Event column that has 0 or 1.

### Overview
*TODO*: Explain about the data you are using and where you got it from.
The idea is to introduce some data of one person with their age, sex, smoking condition, etc and try to predict if we are going to have a death_event.

### Task
*TODO*: Explain the task you are going to be solving with this dataset and the features you will be using for it.
We will use the advantages of the AutoML from Azure to obtain the best model to use with our predictions.

### Access
*TODO*: Explain how you are accessing the data in your workspace.
We are accesing the data through our notebook and loading it in our datastore.

## Automated ML
*TODO*: Give an overview of the `automl` settings and configuration you used for this experiment
In the AutoML processa, we are doing a Classification regression algorithm with the labeled data.
Our primary metric will be 'Accuracy'.


### Results
*TODO*: What are the results you got with your automated ML model? What were the parameters of the model? How could you have improved it?
The best model that we got is a VotingEnsemble model with an accuracy of 0.87299

*TODO* Remeber to provide screenshots of the `RunDetails` widget as well as a screenshot of the best model trained with it's parameters.

## Hyperparameter Tuning
*TODO*: What kind of model did you choose for this experiment and why? Give an overview of the types of parameters and their ranges used for the hyperparameter search
We use the hyperparameter tuning with a random sampling of parameter C and max_iter and a median stopping policy as the early termination policy.
About the parameter C we used three possible values, 1,10 and 100.
About max_iterations we used 50,100 and 150.

### Results
*TODO*: What are the results you got with your model? What were the parameters of the model? How could you have improved it?
We found the same accuracy results for all the possible combinations. In the future we should try to change the parameters to see if we can get a better accuracy.

*TODO* Remeber to provide screenshots of the `RunDetails` widget as well as a screenshot of the best model trained with it's parameters.

## Model Deployment
*TODO*: Give an overview of the deployed model and instructions on how to query the endpoint with a sample input.
Using the Python SDK and the jupyter notebook we deployed the best_run of the models got through the AutoML process.
First we register the model and then we deploy it.
We got and endpoint with authentication disabled, where we can send a request and retrieve a result of the predicted column Death_event.

## Screen Recording
Here you can find the link with the screen recording of the model working properly.


