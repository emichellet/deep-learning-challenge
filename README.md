# Deep Learning Challenge
- Module 21 Challenge

## Neural Network Model Report
### Overview
---
A tool was created for the nonprofit foundation, Alphabet Soup, to help with optimization of selecting clients for funding (for those with the best chance of success in their ventures). With my knowledge of machine learning and neural networks, I have utilized features in the provided data set to create a classifier which can predict whether applicants can be successful if they were funded by Alphabet Soup. A target was set to 75% accuracy for the model. A CSV was retrieved from the nonprofit which contained over 34,000 organizations that have received funding from Alphabet Soup over the years. The dataset included the following columns: 
    - EIN and NAME—Identification columns
    - APPLICATION_TYPE—Alphabet Soup application type
    - AFFILIATION—Affiliated sector of industry
    - CLASSIFICATION—Government organization classification
    - USE_CASE—Use case for funding
    - ORGANIZATION—Organization type
    - STATUS—Active status
    - INCOME_AMT—Income classification
    - SPECIAL_CONSIDERATIONS—Special considerations for application
    - ASK_AMT—Funding amount requested
    - IS_SUCCESSFUL—Was the money used effectively

### Results 
1. Data Preprocessing
    - Data was checked for null and duplicated values
        - *EIN* and *NAME* -- identification columns were removed from the input data because they are neither targets nor features
        - A cutoff point was created to bin "rare" categorical variables together in a new value, other 'Other' for both 'CLASSIFICATION' and 'APPLICATION_TYPE'
        - Categorical data was converted to numeric with pd.get_dummies and a split of the preprocessed data into features and target arrays was made. It was then split into training and testing datasets
        - Target variable for the model: 'IS_SUCCESSFUL'
        - Feature variables for the model:
            - APPLICATION_TYPE
            - AFFILIATION
            - CLASSIFICATION
            - USE_CASE
            - ORGANIZATION
            - STATUS
            - INCOME_AMT
            - SPECIAL_CONSIDERATIONS
            - ASK_AMT

2. Compiling, Training, and Evaluating the Model
    The first model was build with the following parameters (little computation):
    - 2 hidden layers with 80, 30 neurons split (the input (node) feature was 43, 80 was chosen as the first layer as it is almost double the input_feature). With an hidden layer activation function of relu as this our go to for first model.
    - Output node is 1 as it was binary classifier model with only one output: was the funding application succesfull yes or no. And an output layer activation of sigmoid as the model output is binary classification between 0 and 1.
    - A third hidden layer was added because model prediction turned out to be less then 75%.

3. Optimize the model
    Went forth and used an automated model optimizer to get most accurate model possible by creating method that creates a 'keras' Sequential model using the 'keras-tuner library' with hyperparameters options.
    - The best model from the keras tuner method achieved 73% prediction accuracy using a sigmoid activation function with input node of 46, 6 hidden layers at a 51, 81, 71, 6, 41, 91 neurons split and 100 training epochs. 

### Summary 
The final automatically optimized neural network trained model from the keras tuner method achieved 80% prediction accuracy with a 0.45 loss, using a sigmoid activation function with input node of 76; 5 hidden layers at a 16, 21, 26, 11, 21, neurons split and 50 training epochs. Performing better than the non automized model. Keeping the Name column was crucial in achieving and and going beyond the target. This shows the importance of the shape of your datasets before you preprocess it.

---
## Instructions
# Step 1: Preprocess the Data
- Using your knowledge of Pandas and scikit-learn’s StandardScaler(), you’ll need to preprocess the dataset. This step prepares you for Step 2, where you'll compile, train, and evaluate the neural network model.

- Start by uploading the starter file to Google Colab, then using the information we provided in the Challenge files, follow the instructions to complete the preprocessing steps.

    1. Read in the charity_data.csv to a Pandas DataFrame, and be sure to identify the following in your dataset:
        - What variable(s) are the target(s) for your model?
        - What variable(s) are the feature(s) for your model?
    2. Drop the EIN and NAME columns.
    3. Determine the number of unique values for each column.
    4. For columns that have more than 10 unique values, determine the number of data points for each unique value.
    5. Use the number of data points for each unique value to pick a cutoff point to bin "rare" categorical variables together in a new value, Other, and then check if the binning was successful.
    6. Use pd.get_dummies() to encode categorical variables.
    7. Split the preprocessed data into a features array, X, and a target array, y. Use these arrays and the train_test_split function to split the data into training and testing datasets.
    8. Scale the training and testing features datasets by creating a StandardScaler instance, fitting it to the training data, then using the transform function.

# Step 2: Compile, Train, and Evaluate the Model
- Using your knowledge of TensorFlow, you’ll design a neural network, or deep learning model, to create a binary classification model that can predict if an Alphabet Soup-funded organization will be successful based on the features in the dataset. You’ll need to think about how many inputs there are before determining the number of neurons and layers in your model. Once you’ve completed that step, you’ll compile, train, and evaluate your binary classification model to calculate the model’s loss and accuracy.

    1. Continue using the file in Google Colab in which you performed the preprocessing steps from Step 1.
    2. Create a neural network model by assigning the number of input features and nodes for each layer using TensorFlow and Keras.
    3. Create the first hidden layer and choose an appropriate activation function.
    4. If necessary, add a second hidden layer with an appropriate activation function.
    5. Create an output layer with an appropriate activation function.
    6. Check the structure of the model.
    7. Compile and train the model.
    8. Create a callback that saves the model's weights every five epochs.
    9. Evaluate the model using the test data to determine the loss and accuracy.
    10. Save and export your results to an HDF5 file. Name the file AlphabetSoupCharity.h5.

# Step 3: Optimize the Model
- Using your knowledge of TensorFlow, optimize your model to achieve a target predictive accuracy higher than 75%.

- Use any or all of the following methods to optimize your model:
    - Adjust the input data to ensure that no variables or outliers are causing confusion in the model, such as:
    - Dropping more or fewer columns.
    - Creating more bins for rare occurrences in columns.
    - Increasing or decreasing the number of values for each bin.
    - Add more neurons to a hidden layer.
    - Add more hidden layers.
    - Use different activation functions for the hidden layers.
    - Add or reduce the number of epochs to the training regimen.
        - Note: If you make at least three attempts at optimizing your model, you will not lose points if your model does not achieve target performance.
    
    1. Create a new Google Colab file and name it AlphabetSoupCharity_Optimization.ipynb.
    2. Import your dependencies and read in the charity_data.csv to a Pandas DataFrame.
    3. Preprocess the dataset as you did in Step 1. Be sure to adjust for any modifications that came out of optimizing the model.
    4. Design a neural network model, and be sure to adjust for modifications that will optimize the model to achieve higher than 75% accuracy.
    5. Save and export your results to an HDF5 file. Name the file AlphabetSoupCharity_Optimization.h5.

# Step 4: Write a Report on the Neural Network Model
- For this part of the assignment, you’ll write a report on the performance of the deep learning model you created for Alphabet Soup.
- The report should contain the following:

    1. Overview of the analysis: Explain the purpose of this analysis.

    2. Results: Using bulleted lists and images to support your answers, address the following questions:
        - Data Preprocessing
            - What variable(s) are the target(s) for your model?
            - What variable(s) are the features for your model?
            - What variable(s) should be removed from the input data because they are neither targets nor features?
        - Compiling, Training, and Evaluating the Model
            - How many neurons, layers, and activation functions did you select for your neural network model, and why?
            - Were you able to achieve the target model performance?
            - What steps did you take in your attempts to increase model performance?
    3. Summary: Summarize the overall results of the deep learning model. Include a recommendation for how a different model could solve this classification problem, and then explain your recommendation.

# Step 5: Copy Files Into Your Repository
- Now that you're finished with your analysis in Google Colab, you need to get your files into your repository for final submission.
-Download your Colab notebooks to your computer.
- Move them into your Deep Learning Challenge directory in your local repository.
- Push the added files to GitHub.