# Deep Learning Challenge
### Module 21 Challenge
## Background
The nonprofit foundation Alphabet Soup wants a tool that can help it select the applicants for funding with the best chance of success in their ventures. With your knowledge of machine learning and neural networks, you’ll use the features in the provided dataset to create a binary classifier that can predict whether applicants will be successful if funded by Alphabet Soup.

From Alphabet Soup’s business team, you have received a CSV containing more than 34,000 organizations that have received funding from Alphabet Soup over the years. Within this dataset are a number of columns that capture metadata about each organization, such as:

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
* IS_SUCCESSFUL—Was the money used effectively

## Data Preprocessing:
3 questions were posed for this part of the project:
  * What variable(s) are the target(s) for your model? "IS_SUCCESSFUL" is the target for all the models
  * What variable(s) are the features for your model?  All other fields are being used as features unless dropped.
  * What variable(s) should be removed from the input data because they are neither targets nor features? the "EIN" and "NAME" fields were drpped from the data set for the first 2 modeles.  Name was added back for the Optimization Model.
Once the unessary metrics were removed Binning was applied to the "CLASSIFICATION and "APPLICATION TYPE" fields for the models and binning for the "NAME" field was added for the optimization model.

## Compiling, Training, and Evaluating the Model:
Neural Network was used on each model and originally set with 2. For the Optimized model, keras-tuner was used to allow for runninmg 60 nTrials to find the best option to achieve an accuracy over 75%.   the Best accuracy was: 0.7606996893882751

## Summary:
The first model used 2 hidden layers, activation for the hiddemn layers was "relu" and for the output layer was "sigmoid" and came up with Loss: 0.5470668077468872, Accuracy: 0.7306122183799744 this was short of the desired 75% accuracy.  The 2nd Model used 3 hidden layers, activation for the 1st hidden layer remained "relu" all other layers were switched to "sigmoid" producing Loss: 0.5490245819091797, Accuracy: 0.7331778407096863  which is still short of the desired accuracy. After multiple attemps varing the values I used keras_tuner allowing for multiple layers, activation types and epochs to be evaluated automatically making it much faster to identify the best model to use.  This still did not produce the desired 75% accuracy so the next component i looked at was the Features and dropped cells.  By addig back iun the "NAME" field due to the number if records with thge same "NAME" and binning the field to limit the features the results were Loss: 0.5019620656967163, Accuracy: 0.7606996893882751 which meets the desired accuracy of greater than 75%.
In conclusion using keras_tuner sytematically ran through tyhe models with the variables to find the Best one to apply. 
## Acknowledgements
* https://medium.com/ - Understanding Activation Functions and Hidden Layers in Neural Networks
* https://stackoverflow.com/ - number of hidden layer nodes to use
* https://keras.io/keras_tuner/ - training the model using variables so it will check multiple models
* Dallin Whitaker (instructor) - assistance in determining why I was getting a RAM error (due to exceeding 1900 columns when the NAME was kept in the data frame with out binning
