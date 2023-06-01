# Tanzania Water Wells
Predicting the operating condition of water wells in Tanzania based on variaous predictive models.

By: Anat Jacobson 

--- 

### Overview 

This project is based on data on the on the makeup and condition of wells within Tanzania. The data is used to create a predictive model and provide valuable insights into whether a well is in operating or not. This can aid the Tanzanian Government in deciding which wells neeed to be visited first in order to repair and aid in the major water crisis the country is facing.

### Introduction and Busines Case
The problem being faced is that there are thousands of water wells within Tanzania and many of need reparations. This is a major issue within Tanzania since wells are the main water source, so lacking functional wells is a severe threat to livelihood. Water scarcity is also effecting livestock, wild animals, fishing, and other living organisms. Additionally, as you know there has been fast population growth within the country, climate change impacts and expansion of human economic activities put the country under water supply distress. 

The issue here is that inspecting these wells cost a lot of money and takes loads of time that Tanzania does not have. I have created a model with the goal in mind to predict which wells in Tanzania are no longer functional and therefore are the ones that should be visited first and repaired.  


The data for this notebook has been provided by:  Taarifa and Tanzania Ministry of Water through <a href="https://www.drivendata.org/competitions/7/pump-it-up-data-mining-the-water-table/page/23/" >Driven Data</a>.

### Business Understandings

#### Applications
- Tanzanian Goverment can make informed decision when deciding which well to look at to repair next and save money
- Well builders may be able to make better decisions when building and repairing wells  wells to build with parts that don't lead to breakage as much.

#### Data 
The dataset that was worked with after cleaning had over 53K wells in it with data that focused on the geographical information of the well as well as information of water source, payments, quality of water and other important features. 

The predictive measure in this set was whether the well is functional or not, positive being functional. The measure was initially in a seperate dataframe but was merged with the rest of the data to be able to accurately create a model. This cleaning and merging process is explained below. 

A few key metrics taken into account from this dataset were: 

- 5 Different quality groups of water
- 26 regions
- 1.8K funders
- 7 Source types

Additionally, the predictive measure was initailly a tirtiary measure and I changed it to binary that will be explained below as well. 

### Methodology
Because of the many categorical features that can influence well functionality pricing, this project investigates features and their effects through various types of models in an attempt to best predict the well condition. This is done through the use of logistic regression, decision trees and random forest. Our predictor for this model is whether the well is functioning or not, positive class being functional. Our measure for this project will be based on the highest f1 score since for the purposes of this project, we not only care whether the prediction is positive cases but also whether they are accurately positive and whether negative results are accurately negative. 

---

# Modeling!
Now that we have completed exploring that dataset and cleaning we can begin our modelling process. 
### Dummy Model
- We are going to start by creating a dummy model. This will be the model we will be improving upon.
- To start we need to create a test set and a training set for the models. 

confusion_matrix of our dummy model:

Checking f1 score of the dummy model since this is what we will be trying to improve upon for each model as explained earlier. To reiterate, the reason we care about the f1 score in this case is because it includes both the recall and precision score in it and therefore factors in false negatives as well as false positives which is important for the purposes of this business case. 
- F1 Score: 0.7703581317790322
- CV F1 Score: 0.77036 ± 0.00004

### Dealing with Categorical Variables and Scaling Numerics
As noted earlier, we have mostly categorical variables within this data set and will therefore need to deal with them before using them in a model. Additionally, we need to scale our numeric variables if we end up using a logistic regression model.
- We will be scaling numerics through StandardScalar
- We will be dealing with categorical through using OneHotEncoder ('OHE').

These two methods of dealing with variables are going to be implemented through the use of a pipeline for ease of use in each model and to avoid making errors between models. This will help with consistency across all. 

Creating two lists:
- scale: includes only the numeric variables
- cat: includesonly the categorical variables

We can now begin working on models that are not our dummy model. I iterated on multiple models and landed on a final model that is a random forest.
### Final Model
The final model is a random forest tuned with a max depth fo 39 and max_samples of ,5. This model has an F1 score of  .87 when fit the the testing data. I would like to create a grid search with higher level of depth but going to stop here for now. This is going to be used as our final model since is has the highest f1 score! Will now use this model to create predictions and glean insights! For more color on what the prediction look like there is confusion matrix below: 


This was a great improvement from the dummy model since the dummy predicted all wells as functional. This can be seen in the below bar graph of our Dummy f1 score vs our final model score: 

<CYII=" alt="alternatetext">

Although it does not look like the final model improved that much a 10% is actually a major shift when understanding what the dummy model was predicting. We went from not predicting any well as non-functional to accurately predicting 3.3k as non functional. This will be hugely valuable for saving time and money for Tanzania! 

# Feature Importance
Digging a bit more into which feature are important below and where to focus for next steps and the actual well reperations. The features below highlight which ones have the most impact of the prediction modeling. 


As you can see on the bar chart displayed here the top features having the largest impact on the predictability of whether a well is functional or not is:
- population, which makes sense 
- water quality
- the amount of water in the well
- extraction type 

These are important to know about since it could give inference into when fixing well or building new wells. The extraction type in specific could be very benefitcial when looking into fixing the wells for example if the extraction device should be converted to something else like a hand pump instead of relying on gravity which would be another type.  

---

# Conclusion and Next Steps

With this model the government in Tanzania should be able to spend much less money and time looking into individual wells to find out if functional or not and should also be able to glean insights as to maybe how to build and where to place future wells. 

As part of the next steps I would do a deeper dive into a few of these features, particularly the extraction feature. I would do some further tuning of my model as well to increase the f1 score.  Additionally, I would maybe look into other locations in Africa that are facing similar issues and gather data and insights there as well. 

Thank you!

--- 
# For Further information 
Our process is available in this jupyter notebook ("https://github.com/anat-jacobson/Phase_3_Project/blob/main/index.ipynb) or abbreviated in this presentation document ("https://github.com/anat-jacobson/Phase_3_Project/blob/main/AJ_Presentation.pdf)

I am also available on github (anat-jacobson) and via email (anatabigail@gmail.com). Feel free to reach out. 

