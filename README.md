# deep-learning-challenge

## Overview of the Analysis

The purpose of this analysis is to evaluate the performance of machine learning models, particularly deep learning neural networks, on funding applications to a charity organization. The data contains records of granted applications from various organizations as well as metadata of the specific organizations and an indication of whether or not the funding was used successfully. The goal is to evaluate how well a neural network model can predict if an application for funding will be used successfuly or not if granted.

## Results

* Data Processing

  - The target variable for this model is the "IS_SUCCESSFUL" variable. A binary category denoting whether funding was used successfuly for a granted application.
  
  - The following variables are the feature variables of the model:
    * EIN and NAME—Identification columns
    * APPLICATION_TYPE—Alphabet Soup application type
    * AFFILIATION—Affiliated sector of industry
    * CLASSIFICATION—Government organization classification
    * USE_CASE—Use case for funding
    * ORGANIZATION—Organization type
    * STATUS—Active status
    * INCOME_AMT—Income classification
    * SPECIAL_CONSIDERATIONS—Special considerations for application
    * ASK_AMT—Funding amount requested
    
  - The variable EIN was removed as it is a secondary identification variable for an organization, making it redundant as we already have the NAME variable. SPECIAL_CONSIDERATIONS and STATUS were also removed as they likely did not have much effect on the target outcome.
 
* Compiling, Training, and Evaluating the Model

  - For the model 3 layers were used as 3 layers are enough to model most data. The number of neurons was kept relatively low to reduce computing demand and a sigmoid activation is used for the last layer as this is the best for producing binary classifications:
    * First hidden layer: 7 neurons, relu activation function
    * Second hidden layer: 14 neurons, relu activation function
    * Output layer: 1 neuron, sigmoid activation function

  - Target model performance was achieved
  
  ![Screenshot 2023-05-29 233243](https://github.com/KevinMosweu/deep-learning-challenge/assets/119974799/6cc86d7c-407a-4261-b97d-0328b7c5df54)

  
  - Steps taken to increase model peformance
  
    * Examining the ASK_AMT variable and removing outliers:
    ![Screenshot 2023-05-29 2313291](https://github.com/KevinMosweu/deep-learning-challenge/assets/119974799/bedd25c8-007a-4493-8b4c-a09b60b16065)

    ![Screenshot 2023-05-29 231156](https://github.com/KevinMosweu/deep-learning-challenge/assets/119974799/5972d42a-8eaf-404a-ba59-7d6afdc0699f)
    
    * Keeping the NAME variable and binning any values with a count less than 100 as "Other":
    
    ![Screenshot 2023-05-29 232108](https://github.com/KevinMosweu/deep-learning-challenge/assets/119974799/46d73f5d-b2a0-476b-8bb3-c35f4361f5ba)
    
    * Binning less values from the APPLICATION_TYPE and CLASSIFICATION as "Other":
    
    ![Screenshot 2023-05-29 232339](https://github.com/KevinMosweu/deep-learning-challenge/assets/119974799/69183ff9-d154-44de-9a07-180f5f7318f2)
    
    ![Screenshot 2023-05-29 232410](https://github.com/KevinMosweu/deep-learning-challenge/assets/119974799/d20ee9a9-c9ba-49be-835d-8b0a30f805df)
    
    * Adding less neurons in the model to speed up computing time:
    
    ![Screenshot 2023-05-29 232952](https://github.com/KevinMosweu/deep-learning-challenge/assets/119974799/25a6d118-4f48-4d77-bb39-f0eefd047129)
    
    
* Summary

The target was to achieve over 75% accuracy in classifying applications as as successful or unsuccessful and 77% was reached. The model began at 72% accuracy, keeping more APPLICATION_TYPE and CLASSIFICATION values only showed slight improvement, still within the 72% range, removing outliers in terms of ASK_AMT bumped it up to a further 74% accuracy where it remained until the NAME variable was also included which allowed it to break the 75% mark. However using the NAME variable may result in overfitting and the model may not be able to fairly assess new organizations' applications. Perhaps a better model to tackle this problem would be a Random Forest Model as this are used for binary classifications and allow you to assess the importance of each variable toward the target feature. This would make it easy to eliminate unnecessary variables.



