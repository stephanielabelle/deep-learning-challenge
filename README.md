# Deep Learning Challenge

## Module 21

### Overview
This repository outlines the development of a neural network model with TensorFlow utilizing data from the nonprofit foundation Alphabet Soup.  The objective of this model is to determine the applicants that will have the best chance of a success if provided with funding.

The csv data is available at ["https://static.bc-edx.com/data/dl-1-2/m21/lms/starter/charity_data.csv"](https://static.bc-edx.com/data/dl-1-2/m21/lms/starter/charity_data.csv).

### Results
Initial neural network model is available in Google colab notebook [AlphabetSoupCharity_ModelCreation.ipynb](AlphabetSoupCharity_ModelCreation.ipynb), and HDF5 named [AlphabetSoupCharity.h5](AlphabetSoupCharity.h5).
Optimized neural network model is available in the file [AlphabetSoupCharity_Optimization.ipynb](AlphabetSoupCharity_Optimization.ipynb), and HDF5 named [AlphabetSoupCharity_Optimization.h5](AlphabetSoupCharity_Optimization.h5).

#### Data Preprocessing (Optimized Model)
- Target (y)= "IS_SUCCESSFUL" column
- Features (X):
  - "APPLICATION_TYPE"
    - consolidated application types with low number of counts into an "Other" category
  - "AFFILIATION" (Industry sector affiliation)
  - "CLASSIFICATION" (Government classification)
  - "USE_CASE"
  - "ORGANIZATION" (type)
  - "STATUS" (active status)
  - "INCOME_AMT" (income class)
  - "ASK_AMT" (function amount requested
  - "NAME_COUNT_BIN"
    - This was constructed from the "NAME" column by binning "NAME" based on counts
- Removed Columns:
  - "EIN" (ID column)
  - "SPECIAL_CONSIDERATIONS"
    - low number of entries with special considerations 
Any columns that had more than 10 unique values were binned at an appropriate cutoff point.
Categorical variables were encoded with Pandas "get_dummies" function.
Preprocessed data was split with Scikit Learn train_test_split to create X_train & y_train for model training, and X_test & y_test to test the model
 
#### Compiling, Training, and Evaluating the Model
Neurons:
- A total of 90 neurons were used for the model based on recommended hyperparameter tuning guidelines of 2-3X as many neurons as input features.
Layers:
- Three layers were utilized.  There was marginally better accuracy of the model with 3 instead of 2.
Activation Fucntions:
- This model utilized 2 different activation functions
  - Layer 1-3, relu was used for easy computation.
  - Layer 4 (output), sigmoid was utilized as it has an output of 0 or 1
Target Performance:
- A target of >75% was achieved post-optimization.
- The model was optimized with the following modification:
  - Binned the "NAME" columns based on number of times an organization has been funded
  - Removed the "SPECIAL_CONSIDERATIONS" column as it did not provide valuable data
  - Increased added a layer and increased the number of neurons so the model can learn more complex relationships
 
#### Summary
The deep learning model to determine the success of projects funded was over 75% accurate.  The model is able to predict project success/failure in 75% of the time.  It would be a useful tool in assessing funding applications.  With further hyperparameter tuning, changes in activation function, and addition of more layers, this model may be able to increase in accuracy and usefulness.    
