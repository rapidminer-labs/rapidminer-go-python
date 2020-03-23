# rapidminer-go-python
rapidminer-go-python is a Rapidminer python package, that has some API functions which interacts with the RapidMiner server for training and scoring models

## 1. Prerequisite
   Install rapidminer-go-python package by running the following command in conda or your preferred python environment      
    
    pip install rapidminer-go-python
    
## 2. API Functions
There are two parts to the Prediction process:

1. Training the dataset
2. Scoring the dataset (Predicting)

### Training 
RapidMiner provides it's users with flexibility in training a dataset, 

The user can use 'quick_automodel' function in the rapidminer-go-python package in order to quickly train the models.

The user can also use the following functions in order to build a training of his desired settings 

|Function|Definition|
|:--------|----------|
|rapidDataFrameToJson(dataframe) | takes dataframe as input and converts it to a json format and returns the json| 
|convert_json_to_dataframe(inputJson) | takes json as input and returns back a dataframe result|
|upload_json(input_json, analysis_name) | takes a jsonformat of input data and a analysis name for future reference. This function uploads the file in RapidMiner Server and returns a Data ID number|
|create_modeling_task(dataId) |  creates a modeling task with the Data ID passed in the parameter and returns a modelingTaskID|
|set_label(modelingTaskID, LABEL_ATTRIBUTE) | To set the target label in the given training file, takes in modelingtaskid and the label attribute name as input|
|set_class_interest(modelingTaskID, highvalue, lowvalue) | Takes in modelingtaskid, high and low values in order to set high and low values |
|set_cost_matrix(modelingTaskID, userDefinedCostMatrix) | Takes in modelingtaskid, and user defined cost_matrix and sets it for model training|
|start_execution(modelingTaskID) | Starts the process of training with different models|
|get_execution_result(modelingTaskID) | Gets the result on training each model|
|resultPerformancePercentageView(selection_criteria) | Pass the selection criteria to get the result attributes like precision, specificy, error, sensitivity of each model.|
|rapidDataFrameNormalizer(input_DataFrame) | pass the dataframe in the rapidDataFrameNormalizer function to convert all the numbers from string format to number format and removes the % to make it available for plotting|
|plotBarGraph(input_DataFrame, x-axis, y-axis, color segmentation, y-axis max val, width, height) | Takes in the parameters like the dataframe which has the values to be plotted, x and y axis of attributes in the df to be plotted a number from 0 to 20 in order to segment the color of bargraph, what is the max value of the yaxis attribute, width and height of the graph to plot a colourful bar graph.|
|get_data_info(dataID) | provides a json response of info about the file mentioned in the dataID|
|update_models(modTaskId, to_disable) | pass the modeltaskID and the models to be disabled from the training process before starting the execution|
|determine_best_model(selection_criteria,max_min_crietria_selector)| on passing the selection criteria and whether the min value or max value to be considered as best value passed on to the function, the function returns the name of best model|
|deploy_model(modelingTaskID, model)| on passing the modelingtaskid and the model to be deployed, the function returns the deploymentID which has to be used during predicting/scoring|

### Scoring
|Function|Definition|
|:--------|----------|
|score(inputScoreData, deploymentID) | on passing the data file to be predicted and the deploymentID the function returns the list of prediction results|

### Possible values for Selection Criteria
The determine_best_model function has selection_criteria and max_min_crietria_selector parameters which has the following possible values 

For selection_criteria please use the following possible keys.

|Key|Definition|
|:--------|----------|
|jupyter_interactive| only for jupyter notebook|
|performance_accuracy| To get the accuracy value|
|performance_classification_error | To get the classification_error value|
|performance_sensitivity | To get the sensitivity value |
|performance_AUC | To get the AUc value|
|performance_specificity | To get the specificity value|
|performance_precision | To get the precision value|
|performance_recall | To get the recall value|
|performance_f_measure | To get the fmeasure value|
|gain_modelOutCome | To get the modelOutCome value|
|gain_bestClassOutCome | To get the bestClassOutcome Value|
|gain_finalGain | To get the final Gain value|

For selection_criteria max_min_crietria_selector use 'max' or 'min' as key.

## 3. Example:
Please refer to the 'interactiveScript_deals.ipynb'(jupyter notebook) file under the examples folder of rapidminer-go-python project.

You can use it on the jupyter notebook provided in the partner server (Rapidminer GO) directly without any need for setting up the environment.


