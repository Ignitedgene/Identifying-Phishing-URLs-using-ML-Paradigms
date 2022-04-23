# SC1015-Mini-Project
<h2> Introduction </h2> 
  <p align='justify'> Hi Everyone! This is a mini-project for our SC1015 Introduction to Data Science and Machine Learning module at NTU. Our team consists of Eugene Wee, Clare Yeo and Guo Zhiqi. For this project, our team identified the rising trend of phishing attacks and we sought to create a machine learning model to effectively identify which URLs are phishing in nature. We tested out different machine learning models, evaluated them based on classification accuracy, and tried to improve each model's performance.
  </p> 
<b> Our Dataset: </b> https://www.kaggle.com/shashwatwork/web-page-phishing-detection-dataset?select=dataset_phishing.csv

<h2> Overview of Project </h2> 
  <ol>
    <li> Define Problem Statement </li> 
    <li> Data Preparation and Exploratory Data Analysis (EDA) </li> 
    <li> Machine Learning Model Training & Evaluation </li> 
    <li> Model Improvements - Feature Selection & Hyperparameter Tuning </li> 
    <li> Model Comparison </li>
    <li> Model Improvements - Ensembling </li>
    <li> Presentation of Insights/ Recommendation </li> 
    <li> Learning Outcome :D </li> 
  </ol>

## 1. Problem Statement 
  <p align='justify'>  Phishing is a form of fraud in which the attacker learns sensitive information of users by sending as a reputable entity or person in email or other communication channels. URL phishing can lead to usernames, passwords, credit cards, and other personal information being stolen. In fact, the number of phishing scams in Singapore jumped from 16 cases in 2017 to 5,020 in 2022. In light of the growing concern, our group aims to identify important features of phishing URLs and detect phishing URLs using Machine Learning techniques. 
  </p>

## 2. Data Preparation and Exploratory Data Analysis (EDA)
  <p align='justify'> Firstly, we checked the distribution of our dataset and found that there was an equal number of non-phishing and phishing URLs of 5715. We also noticed that there were certain columns with NaN values for phishing URLs, and we deemed these columns as irrelevant. We then removed  these relevant columns which does not contribute to phishing URLs. </p>

> Purpose of Data Preparation: Removing columns which do not contribute to Phishing URLs (Irrelevant)
  <div> 
    <img width="500" height="600" src="/dsai images/Null_values.jpg"> 
    <img width="225" height="125" align = 'top' src="/dsai images/null_cols.jpg">
  </div>
  
<h4> Principle Component Analysis (PCA) </h4>
  <p align='justify'>  Upon analysing our datasets, we realized that the columns represented the clean breakdown of each aspect of URL. We realized that there was a large dimension (87 columns) for the variables. Therefore, we sought to implement Principal Component Analysis (PCA) to reduce the dimensionality of the variables. We used a 95% explained variance for our PCA which reduces the dimensions to 60 components. We plotted the explained variance plot below. </p>

> Purpose of PCA: Outputs variables ordered by greatest influence on our target variable, Phishing (1 or 0). 

  <div> 
    <img width="800" height="350" src="/dsai images/pca.jpg">
  </div> 
  
  <p align='justify'> After running PCA, we analysed the breakdown of each PCA components and assigned names to them based on the input variables. We used this to construct our DecisionTree and better understand the PCA components, which will help with our subsequent analysis. </p>
  
  <div> 
    <img width="800" height="350" src="/dsai images/breakdown.jpg">
  </div>
  
## 3. Machine Learning Model Training & Evaluation 
  <p> We decided to run the following ML models and evaluate their respective performances:
      <ul> 
        <li> Decision Tree Classifier </li>
        <li> Random Forest Classifier </li>
        <li> Logistic Regression Classifier </li> 
      </ul>
  </p> 
  
  <p> During Model Building, we will be running 2 rounds with the following model inputs:
      <ol>
        <li> PCA components (95% explained variance) </li>
        <li> PCA components (95% explained variance)  + Selected variables from Feature Selection </li>
      </ol>

## Round 1

### 3.1. Decision Tree Classifier  
  <p align='justify'> We used trained test split, with a test size of 0.3. Afterwards, we trained the model using a max depth of 3, and plotted its confusion matrix. We evaluated the model's accuracy, precision and F1 score. </p>
 
  <b> - Decision Tree Diagram </b> 
  <div>
    <img width="700" height="400" src="/dsai images/dt.jpg">
  </div> 
  
  <b> - Model Evaluations </b> 
  <div>  
    <img width="350" height="200" src="/dsai images/dt_1.jpg">
    <img width="300" height="200" src="/dsai images/dt_1_cm.jpg">
  </div> 
  
### - Improving the Decision Tree (DT) 
  <p align='justify'> We check if pruning the tree using 2 parameters: Criterion and max_depth, can lead to better accuracy. We run our model using different values for max_depth (from 1 to 30) and visualize its accuracy for each max_depth. </p>
  
> We deem the best parameters to be Criterion = entropy and Max_depth = 7.
  <div>
    <img width="450" height="300" src="/dsai images/gini_entropy.jpg">
  </div>
  
### 3.2. Random Forest Classifier
  <p align='justify'> However, we realised that DecisionTreeClassifier has poor classification accuracy and high False Negative results, therefore we applied RandomForestClassifer which ensembles the majority votes of a multitude of Decision Trees to improve model performance and robustness. </p>
 
  <b> - Model Evaluations </b> 
  <div>
    <img width="350" height="200" src="/dsai images/rfc_1.jpg">
    <img width="300" height="200" src="/dsai images/rfc_1_cm.jpg">
  </div>
  
### 3.3. Logistic Regression Classifier
  <p align='justify'> We conducted Logistics Regression to model the probability of the discrete dependent variable (Phishing) based on the given variables. Logistic Regression assumes a linear relationship between dependent and independent variables, and constructs linear boundaries within the dataset to segment the data. </p>
        
  <b> - Model Evaluations </b> 
  <div>
    <img width="350" height="200" src="/dsai images/dt_1.jpg">
    <img width="300" height="200" src="/dsai images/dt_1_cm.jpg">
  </div> 
  
## 4. Model Improvements - Feature Selection & Hyperparameter Tuning 

### Feature Selection
  <p align='justify'>
    <ul> 
      <li> We achieved good results from using PCA components as our model inputs, but there was still inaccuracies in the model's performance.</li>
      <li> We noticed that certain variables (i.e. google_index, page_rank) were correlated to phishing emails, therefore we sought to use Feature Selection from our original dataset and include them into our model inputs. </li>
    </ul> 
    
  <p align='justify'> From our RandomForestClassifier model, we performed Feature Selection to rank variables based on feature importance, and add the most influential variables to our model inputs. We hypothesized that by adding these weights, we could achieve a better overall prediction accuracy and precision. </p>
  
  <p>This is a horizontal barchart of the top features </p> 
  <div>
    <img width="700" height="470" src="/dsai images/feature_importance.jpg">
  </div>

  <b> - Exploratory Data Analysis for Feature Importance </b> 
    <ul> 
      <li> Analysing the chart for Feature Importance, we conducted EDA on the top 10 variables (Highest Influence on target variable). </li>
      <li> Features like web_traffic & ratio_hyperlinks (int/ ext) do not have a distinct difference to effectively identify phishing URLs, therefore we exclude them from our model inputs. </li>
    </ul> 
  
  <b> - Violin plots of top 10 variables </b>
  <div>
    <img width="700" height=400" src="/dsai images/violin_plot.jpg">
  </div> 
  
### Hyperparameter Tuning - GridSearchCV
  <p align='justify'> We realized that we can tune the hyperparameters of the model to achieve a higher result, therefore we used GridSearchCV which optimizes the parameters for the highest classification accuracy. </p> 
  
> Purpose of GridSearchCV: Tests all possible parameter combinations and returns the best set of parameters using cross-validation method.
    
  <div>
    <img width="450" height=50" src="/dsai images/gridsearchcv.jpg">
  </div>                                                           
                                                                 
## Round 2
  <p align='justify'> For our second model building, we included the selected variables from Feature Selection to the same dataset to test if we can obtain a better performance for our models.   
    </p>      
    
### 4.1. Decision Tree (DT)
  <b> - Model Evaluations </b> 
  <div>
    <img width="350" height="200" src="/dsai images/dt_2.jpg">  
    <img width="300" height="200" src="/dsai images/dt_2_cm.jpg">
  </div> 
  
### 4.2. Random Forest 
  <b> - Model Evaluations </b> 
  <div>
    <img width="350" height="200" src="/dsai images/rfc_2.jpg">  
    <img width="300" height="200" src="/dsai images/rfc_2_cm.jpg">
  </div>  
  
### 4.3. Logistic Regression
  <b> - Model Evaluations </b> 
   <div>
    <img width="350" height="200" src="/dsai images/lr_2.jpg">  
    <img width="300" height="200" src="/dsai images/lr_2_cm.jpg">
  </div>   

## 5. Model Comparison 
  <p align='justify'> After running both rounds of model training for all 3 models, we consolidated our metrics into a dataframe for analysis. Our results are as follows: </p> 
  
   <div>
    <img width="600" height="160" src="/dsai images/consolidated_metrics.jpg">  
  </div> 
  
  <b> Analysis of Model Comparison </b> 
    <ul> 
  <li> Generally across all 3 models, the 2nd round of model training produced better model performances and prediction results</li>
  <li> RandomForestClassifier returned the best classification results. </li>
    </ul> 

## 6. Model Improvements - Ensembling
  <p align='justify'> We also decided to conduct ensembling across the 3 different models using hard voting method, which sums the votes for the class labels from each of the model and predicts the class with the most votes. We also included the results from hyperparameter tuning to improve model performance. </p> 
  
  <b> - Model Evaluations </b> 
  <div>
    <img width="550" height="100" src="/dsai images/ensembling_results.jpg">
  </div> 
  
## 7. Presentation of Insights/ Recommendation 
  <ul>
    <li> We managed to build a model with <b> 95.28% classification accuracy </b> through ensembling of the 3 given models. </li> 
    <li> We also noticed the following patterns for phishing URLs: </li>
      <ol> 
        <li> Indexed by google (google_rank = 1) </li> 
        <li> No hyperlinks (nb_hyperlinks = 0) </li> 
        <li> No "www" within URL (nb_www = 0) </li> 
        <li> Zero or low page rank </li> 
        <li> Relatively new domain_age </li> 
        <li> Presence of phish hints </li> 
        <li> Long URLs with lengthy word path </li>
      </ol> 
  <div>
    <img width="700" height=400" src="/dsai images/violin_plot.jpg">
  </div> 
                                                                   
## 8. Learning Outcome :D 
  <p align='justify'> Through this mini-project, we gained the following learning outcomes: </p>
  <ul> 
    <li> Using PCA to reduce the dimensionality of the dataset and tackle the curse of dimensionality</li>    
    <li> Hyperparameter tuning using GridSearchCV </li>
    <li> Ensembling of different models to obtain the aggregated result to improve model performance. </li>   
   </ul>
   
### THANK YOU!

## References: 
<ol> 
  <li> Web page Phishing Detection Dataset, https://www.kaggle.com/shashwatwork/web-page-phishing-detection-dataset?select=dataset_phishing.csv </li>
  <li> Phishing scams in Singapore rose to 5,020 cases in 2021 from 16 in 2017, https://sg.news.yahoo.com/phishing-scams-singapore-5020-cases-2021-from-16-in-2017-desmond-tan-084615863.html </li>
</ol>
