# Neural Network Model Report

# Overview
The goal of this analysis is to get over 75% accuracy given the following data:

The nonprofit foundation Alphabet Soup wants a tool that can help it select the applicants for funding with the best chance of success in their ventures. With your knowledge of machine learning and neural networks, you’ll use the features in the provided dataset to create a binary classifier that can predict whether applicants will be successful if funded by Alphabet Soup.

From Alphabet Soup’s business team, you have received a CSV containing more than 34,000 organizations that have received funding from Alphabet Soup over the years. Within this dataset are a number of columns that capture metadata about each organization, such as:

EIN and NAME—Identification columns

APPLICATION_TYPE—Alphabet Soup application type

AFFILIATION—Affiliated sector of industry

CLASSIFICATION—Government organization classification

USE_CASE—Use case for funding

ORGANIZATION—Organization type

STATUS—Active status

INCOME_AMT—Income classification

SPECIAL_CONSIDERATIONS—Special considerations for application

ASK_AMT—Funding amount requested

IS_SUCCESSFUL—Was the money used effectively


# Results

*Data Preprocessing

The target variable used is: IS_SUCCESSFUL

![image](https://github.com/hmshoberg/deep-learning-challenge/assets/145800386/bc9518df-894c-47f2-bf6c-a28a3e3c868f)

The features variables for the models are:
APPLICATION_TYPE
AFFILIATION
CLASSIFICATION
USE_CASE
ORGANIZATION
STATUS
INCOME_AMT
SPECIAL_CONSIDERATIONS
ASK_AMT

The variables EIN and Name were removed from the input data because they are neither targets nor features.

*Compiling, Training, and Evaluating the Model

Attempt # 1 :  Two layers with random nodes that I chose simply as a place to start.  I didn't want too few, but also not too many, so I chose numbers based on previous models we'd worked on.

![image-1](https://github.com/hmshoberg/deep-learning-challenge/assets/145800386/ff7c38eb-9f42-47a6-aeb5-f712dc2d9a5c)

It achieved a 72% accuracy, which seemed fairly promising, though not what I wanted.

Attempt # 2 : I decided to use the Hyperparameters option in Keras Tuner to see if that could give me a better accuracy guage. 

![image-2](https://github.com/hmshoberg/deep-learning-challenge/assets/145800386/889696c1-5f4b-407e-b8ca-6c1c6aaf5119)

![image-3](https://github.com/hmshoberg/deep-learning-challenge/assets/145800386/b5b632e8-6cb7-4615-9294-05a47c419495)

There was not a great amount of approvement - only 1% difference, so I went back to the drawing board for a third time and tested with three layers and added a drop layer to see if that would make a difference as a dropout can force a neural network to be less dependent on specific neurons and rely on different combinations of features and neurons. 

Attempt # 3:

![image-5](https://github.com/hmshoberg/deep-learning-challenge/assets/145800386/5a131bed-2dc1-4ecf-a778-869ca38845b7)

With a lack of improvement, I went back to the original data to see if any other variables could be removed and if that would make a difference in the outcome. 

Attempt # 4:

With the Organization variable removed, I used a Hyperparameter model once again as that had a better result earlier, but there was no improvement.

![image-6](https://github.com/hmshoberg/deep-learning-challenge/assets/145800386/101d2c1b-36ee-434a-9d4b-20f0756a28c9)

Attempt # 5 :

For one last attempt, I decided to adjust the original bins, but also look into the possibility of binning the Names or EINs (running either without binning caused a crash when attempting to run due to so much data). I then used three hidden layers with gradually increasing nodes.

![image-7](https://github.com/hmshoberg/deep-learning-challenge/assets/145800386/5b402e8e-5d5f-482f-a8d1-6a4481d13d1e)

![image-8](https://github.com/hmshoberg/deep-learning-challenge/assets/145800386/907b35d8-c6ca-48b1-9358-21a020721f4a)

With this last attempt, an accuracy of approximately 75% was finally achieved.

![image-9](https://github.com/hmshoberg/deep-learning-challenge/assets/145800386/6ffe4b54-7e3d-47e6-963f-5ef5361dfa71)

# Summary
While I was able to finally achieve an accuracy of 75%, it stands to reason that there might be the opportunity to improve this further.  Improving the overall data optimization would be one place to start, but a different classication model such as a Random forest might work as well as our target variable is Yes/No and random forests use Decision Trees and give responses that are often True/False.
