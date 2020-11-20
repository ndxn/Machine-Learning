# Neural Networks and Deep Learning

## Overview

Using neural networks and, more specifically, deep learning models, this project is aimed to create a relatively reliable binary classifier on a dataset consisting of numerical and categorical data. The process includes the steps of preprocessing data and then desigining, testing, and evaluating the results of models. Subject data pertained to organizations that received donations from a large corporation for specific projects. Parameters included data describing the recipient organization and the status, whether successful or unsuccessful, of the project. The goal of the analysis was to create a model that predicts, with relative accuracy, the likelihood of successful impleementation of projects funded by corporate donation.

Project goals included:

- Importing, analyzing, cleaning, and preprocesings a “real-world” classification dataset.
- Selecting, designing, and training a binary classification model.
- Optimizing model training and input data to achieve desired model performance.

## Resources

- Data: Data for this project was provided in tabular form as charity_data.csv file
- Software: Python 3.7.7 in Jupyter Notebook 6.0.3 using Pandas, scikit learn, and TensorFlow.

## Data Preprocession

The data from sharity_data.csv was imported into a Jupyter Notebook as a Pandas dataframe. The first step in preprocessing the data was to inspect the datatypes. Non-numerical datatipyes included the fieldS:
- NAME
- APPLICATION_TYPE
- AFFILIATION
- CLASSIFICATION
-  USE_TYPE
- ORGANIZATION
- INCOME_AMT
- SPECIAL_CONSIDERSATIONS

Further exploration was conducted using .nunique(), where the results showing categorical paramters with more than two unique values were known to be non-binary and, thus, in need of coding beyond simply assigning values of 0 and 1.

Non-informative parameters were dropped. Though EIN could be used as an index, for ease of processing, the standard index was used and EIN was dropped. Similarly, NAME was dropped as the name of an organization should not have a statistically significant impact on project success rates.

The categorical parameters APPLICATION_TYPE, CLASSIFICATION, and SPECIAL-CONSIDERATIONS all included a number of unique values that necessitated value binning. The resultant categories were binned to reduce the number of unique values down to between 6 and 17, each category including an "Other" value.

With parameters inspected and binned, the categorical parameters were encoded using One Hot Encoding. The resultant DataFrame had 43 input colums and one, IS_SUCCESSFUL, output column. Following preprocessing, the data was split into the X_train, X_test, y_train, and y_test datasets using the standard StandardScaler ratios.

## Model design and training

The first model was used as a baseline by which all other modifications and optimization strategies were measured. The first model was a simple neural network using only one hidden layer. Three subseq models were build off that model, increasing the number of nodes and/or hidden layers. Additional optimization of the model was conducted at the data level, wherein parameters suspected of being noisy were dropped. For those datasets, the same model parameters were used and the results compared.

Model 1: Neural Network, 1 hidden layer
- Hidden layer 1: Nodes: equal to number of input features, 43; Activation function: reul
- Accuracy: 72.38%

Model 2: Neural Network, 1 hidden layer
- Hidden layer 2: Nodes: equal to three times number of input features, 129; Activation function: relu
- Accuracy: 72.67%

Model 3: Deep Learning Neural Network, 2 hidden layers
- Hidden layer 1: Nodes: equal to two times number of input features, 86; Activation function: relu 
- Hidden layer 2: Nodes: equal to the number of input features, 43; Activation function: relu 
- Accuracy: 72.44%

Model 4: Deep Learning Neural Network, 3 hidden layers
- Hidden layer 1: Nodes: equal to two times number of input features, 86; Activation function: relu 
- Hidden layer 2: Nodes: equal to the number of input features, 43; Activation function: relu 
- Hidden layer 3: Nodes: equal to the integer of half the input features, 21; Activation function: relu 
- Accuracy: 72.29%

The above summary shows that the baseline accuracy as established by a neural network with one hiddein layer and the number of nodes equal to the number of input paramters yielded an unsatisfactory accurcay of 72.38%. The attempts at optimizing the model itself yielded only marginal gains in accuracty. The more complicated neural network had the highest accuracy at 72.67%. However, accuracy of models varied on different runs of the Juypter Notebook, indicating that attempts to optimize the model were not effective.

With the modification of the model yielding disappointing gains in accuracy, the next step in optimizing performance was to modify the input data, using the first model parameters and its results as a baseline for comparison. For these models, the input data had to be scaled and split.

Model 5: Neural Network, 1 hidden layer, dropping SPECIAL_CONSIDERATIONS
- Hidden layer 1: Nodes: equal to number of input features, 43; Activation function: reul
- Accuracy: 72.30%

Model 6: Neural Network, 1 hidden layer, dropping APPLICATION_TYPE
- Hidden layer 1: Nodes: equal to number of input features, 43; Activation function: reul
- Accuracy: 70.58%

Modifying the input parameters had either no appreciable or a negative effect on the accuracy of the neural network.

## Results

The best accuracy for the neural network model came from Model 4, with three hidden layers and nodes ranging from twice the number of inputs, or 86, to approximately half the number of inputs, or 21. All , attempts to optimize both the model and the dataset fell short of the target accuracy rate of 75%. Attempts to modify just the model had accuracy rates all withing the 72% range. Considering the relatively limited descriptive nature of the input parameters, it appears that the lower-than-anticipated accuracy rates will have to suffice.
