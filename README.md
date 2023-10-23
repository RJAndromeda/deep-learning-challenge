# deep-learning-challenge

Module 21 Challenge - Rhiannyn Geeson

# Step 4: Report

1. **Overview** of the analysis: 

   The purpose of the analysis is to assist the nonprofit foundation Alphabet Soup to select applicants for funding that will have the best change of success. This means building a binary model to predict whether applicants will be successful if funding is awarded by Alphabet Soup

2. **Results**: 

- Data Preprocessing
  - Target Variable was "Is_Successful": whether the project in the historical data was successful or not
  - Features for the **final** model include: 
    - **NAME**—Identification columns
    - **APPLICATION_TYPE**—Alphabet Soup application type
    - **AFFILIATION**—Affiliated sector of industry
    - **CLASSIFICATION**—Government organisation classification
    - **ORGANIZATION**—Organisation type
    - **STATUS**—Active status
    - **INCOME_AMT**—Income classification
    - **SPECIAL_CONSIDERATIONS**—Special considerations for application
    - **ASK_AMT**—Funding amount requested
  - **USE_CASE** was removed, since it did not appear to be a feature relevant to the model. **EIN** was also excluded, since it is neither a target or a feature. In the first model, before optimisation, **NAME** was not considered a feature. This was, however, brought back in when determined relevant for the final model.
- Compiling, Training, and Evaluating the Model
  - The neurons: layer 1 started with 90 neurons, then 30, for the model to perform above 75%. 
  - I tried both 2 and 3 hidden layers, and found that two layers was sufficient and performed marginally better. I chose activation functions 'relu', 'tanh', and 'tanh' again for the activation of the output layer, which performed better in this instance than sigmoid (stronger gradients with tanh than sigmoid). Use of relu  helps to ward against vanishing gradient.
  - I was able to achieve the target model performance upon optimisation.
  - To increase model performance, I:
    - Increased the training epochs to 75
    - Tested different activations, and different orders for the activations
    - Re-introduced the 'Name' column in as a feature (the key to driving the model above 75%)
    - Tested different binning techniques, sticking with binning lower than 1000 for **APPLICATION TYPE** and **CLASSIFICATION**, and also less than 10 for **NAME**. This assisted identifying those applicants who had submitted several times 
    - Tested different levels of hidden nodes for the layers

1. **Summary**: Overall, the optimised model performs to the degree specified. The loss drops gradually from 50% to 44% over 75 epochs, which suggests it is still learning. The model performs on average loss of 45.6%, and an accuracy of 78.3%. The model would assist Alphabet Soup in their assessment of applications, thus it would fulfil its intended function.
1. Other classification models could perform better in this instance, including tree-based algorithms. The data is not too complex, so that the decision tree would not be too complex or deep, and the decision logic is clear throughout the process, which would be easier to explain and show to the assessment board of Alphabet Soup should there be questions regarding how the model works, or if they would like to use the model as part of the decision-making process and would like to audit the results.

**References**

Noted in code, I adapted : umotto's solution  on https://stackoverflow.com/questions/51186330/save-model-weights-at-the-end-of-every-n-epochs), and also referred to https://medium.com/@italojs/saving-your-weights-for-each-epoch-keras-callbacks-b494d9648202 for saving after end of epochs.

I referred to course materials, stackoverflow, TensorFlow.org: https://www.tensorflow.org/guide/keras/serialization_and_saving, https://www.tensorflow.org/model_optimization/guide/pruning/pruning_with_keras 

, and https://wandb.ai/shweta/Activation%20Functions/reports/Activation-Functions-Compared-With-Experiments--VmlldzoxMDQwOTQ#the-parametric-relu-activation-function for more information on relu.