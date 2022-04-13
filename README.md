# SC1015-Mini-Project
<h2> Introduction </h2> 
  <p> Hi Everyone! This is a mini-project for our SC1015 Introduction to Data Science and Machine Learning module at NTU. Our team consists of Eugene Wee, Clare Yeo and Guo Zhiqi. For this project, our team identified the rising trend of phishing attacks and we sought to create a machine learning model to effectively identify which URLs are phishing in nature. We tested out different machine learning models, evaluated them based on classification accuracy, and tried to improve each model's performance.
  </p> 
<b> Our Dataset: </b> https://www.kaggle.com/shashwatwork/web-page-phishing-detection-dataset?select=dataset_phishing.csv

<h2> Overview of Project </h2> 
  <ul>
    <li> Define Problem Statement </li> 
    <li> Data Preparation and Exploratory Data Analysis (EDA) </li> 
    <li> Machine Learning Model Training & Evaluation </li> 
    <li> Model Improvements - Feature Selection </li> 
    <li> Presentation of Insights/ Recommendation </li> 
    <li> Learning Outcome :D </li> 
  </ul>

<h3> Problem Statement </h3> 
  <p> Phishing is a form of fraud in which the attacker learns sensitive information of users by sending as a reputable entity or person in email or other communication channels. URL phishing can lead to usernames, passwords, credit cards, and other personal information being stolen. In fact, the number of phishing scams in Singapore jumped from 16 cases in 2017 to 5,020 in 2022. In light of the growing concern, our group aims to identify important features of phishing URLs and detect phishing URLs using Machine Learning techniques. 
  </p>

<h3> Data Preparation and Exploratory Data Analysis (EDA) </h3> 
  <p> Firstly, we checked the distribution of our dataset and found that there was an equal number of non-phishing and phishing URLs of 5715. </p>  
<h4> Exploratory Data Analysis (EDA) </h4>
  <p> Moving on to Data Cleaning, we removed irrelevant columns that does not contribute to phishing URLs. </p>
  
<h4> Principle Component Analysis (PCA) </h4>
  <p> Upon analysing our datasets, we realized that the columns represented the clean breakdown of each aspect of URL. We realized that there was             a large dimension (87 columns) for the variables. Therefore, we sought to implement Principal Component Analysis (PCA) to reduce the                   dimensionality of the variables. We used a 95% explained variance for our PCA which reduces the dimensions to 60 components. We plotted the explained variance plot below. </p>
       <ul> 
        <li> Purpose of PCA: Outputs variables ordered by greatest influence on our target variable, Phishing (1 or 0).  </li>
       </ul> 
  
 
<h3> Machine Learning Model Training & Evaluation </h3> 
  <p> We decided to run the following ML models and evaluate their respective performances:
      <ul> 
        <li> Decision Tree (DT) </li>
        <li> Random Forest </li>
        <li> Logistic Regression/ Support Vector Machine (SVM) </li> 
      </ul>
  </p> 
  
  <p> During Model Building, we will be running 2 rounds with the following model inputs:
      <ol>
        <li> PCA components (95% explained variance)</li>
        <li> PCA components (95% explained variance)  + Variables with Feature Importance (TBC)</li>
      </ol>
 
<h4>1. Decision Tree (DT) </h4>
  <p> We used trained test split, with a test size of 0.3. Afterwards, we trained the model using a max depth of 3, and plotted its confusion matrix. We evaluated the model's accuracy, precision and F1 score. </p>
  <p> Below is the trained decision tree. </p>
  
<h4> Improving the Decision Tree (DT) </h4>
  <p>We check if pruning the tree using 2 parameters: Criterion and max_depth, can lead to better accuracy. We run our model using different values for max_depth (from 1 to 30) and visualize its accuracy for each max_depth. </p>
  
  <p> We deem the best parameters to be Criterion = XXX and Max_depth = XXX.</p>


<h4>2. Random Forest </h4>


<h4>3. Logistic Regression/ Support Vector Machine (SVM)</h4>
  <p>We conducted Logistics Regression to model the probability of the discrete dependent variable (Phishing) based on the given variables. 
        
  <b>Limitations of Logistics Regression: </b>
       <ul>
            <li> Constructs linear boundaries, which may not be the case.</li>
            <li> Assumes that independent variables are linearly related to dependent variables. </li>
       </ul>
        However, we realized that it resulted in poor classification accuracy and precision, and decided to try SVM to perform non-linear classification using kernel trick.
       <ul> 
  <li> <b>Purpose of Support Vector Machine (SVM): </b> Finds a hyperplane that best separates the two classes based on statistical approach. </li>
       </ul> 
  
  </p>

<h3> Model Improvements - Feature Selection </h3> 
    <p>
       <ul> 
<li>We achieved good results from using PCA components as our model inputs, but there was still inaccuracies in the model's performance.</li>
<li>We noticed that certain variables (i.e. google_index, page_rank) were correlated to phishing emails, therefore we sought to use Feature Selection from our original dataset and include them into our model inputs.</li>
      </ul> 
    
From our RandomForestClassifier model, we performed Feature Selection to rank variables based on feature importance, and we decided to add the top 5 features into our model inputs. We hypothesized that by adding these weights, we could achieve a better overall prediction accuracy and precision.        </p>
    <p>This is a horizontal barchart of the top features </p>
      
<h4> Exploratory Data Analysis for Feature Importance </h4> 
  <p>Looking at the chart for Feature Importance, we conducted EDA on the top 8 variables (Highest Influence on target variable). </p>
  
  <p> The violin plots of top 8 variables are as shown. (TBC) </p>
  
<h3> Round 2 </h3>

  <p>For our second model building, we included the variables from Feature Selection to test if we can obtain a better performance for our models. </p>      
<h4>1. Decision Tree (DT) </h4>
<h4>2. Random Forest </h4>
<h4>3. Logistic Regression/ Support Vector Machine (SVM) </h4>

<h3> Model Improvements - Ensembling </h3>
  <p> We also decided to conduct ensembling across the 3 different models to obtain better prediction and performance. </p> 
<h4> Model Consolidation & Comparison</h4> 
  <p>After running both rounds of model training for all 3 models, we consolidated the metrics into a dataframe for analysis.  
  
  <b>Deductions from consolidating results:</b>
  </p> 
  
  <ul> 
  <li>Generally across all 3 models, the 2nd round of model training produced better model performances and prediction results</li>
  <li>Support Vector Machine model produced the best result.</li>
        </ul> 
        
<h4> Ensembling ML models </h4>
<p> We then seek to ensemble the 3 ML models using bagging method, where each model learns the error produced by the previous model using a slightly different subset of the training dataset. Bagging reduces variance and minimizes overfitting. </p>


<h3> Presentation of Insights/ Recommendation </h3> 

<h3> Learning Outcome :D </h3> 

<h2> THANK YOU! </h2> 

<h2> References: </h2> 
<ol> 
  <li> Phishing scams in Singapore rose to 5,020 cases in 2021 from 16 in 2017, https://sg.news.yahoo.com/phishing-scams-singapore-5020-cases-2021-from-16-in-2017-desmond-tan-084615863.html </li>
</ol>
