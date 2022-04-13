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
    <li>  Model Improvements - Feature Selection </li> 
    <li> Presentation of Insights/ Recommendation </li> 
    <li> Learning Outcome :D </li> 
  </ul>

<h3> Problem Statement </h3> 
  <p> Phishing is a form of fraud in which the attacker learns sensitive information such as login credentials or account information by sending as a reputable entity or person in email or other communication channels. URL phishing can lead to usernames, passwords, credit cards, and other personal information being stolen. In fact, the number of phishing scams in Singapore jumped from 16 cases in 2017 to 5,020 in 2022. In light of the growing concern towards phishing scams, our group aims to identify important features of phishing URLs and detect phishing URLs using Machine Learning techniques. 
  </p>

<h3> Data Preparation and Exploratory Data Analysis (EDA) </h3> 
  <p> Firstly, we checked the distribution of our dataset and found that there was an equal number of non-phishing and phishing URLs of 5715. <p>
  
    <h4> Exploratory Data Analysis (EDA) </h4>
      <p> Moving on to Data Cleaning, we removed irrelevant columns that does not contribute to phishing URLs. <p>
  
    <h4> Principle Component Analysis (PCA) </h4>
        <p> Upon analysing our datasets, we realized that the columns represented the clean breakdown of each aspect of URL. We realized that there was             a large dimension (87 columns) for the variables. Therefore, we sought to implement Principal Component Analysis (PCA) to reduce the                   dimensionality of the variables. We used a 95% explained variance for our PCA which reduces the dimensions to 60 components <p>
       <ul> 
        <li> Purpose of PCA: </li>
          <p> Outputs variables ordered by greatest influence on our target variable, Phishing (1 or 0). <p>
       </ul> 
      <p> Upon analysing our datasets, we realized that the columns represented the clean breakdown of each aspect of URL. We realized that there was             a large dimension (87 columns) for the variables. Therefore, we sought to implement Principal Component Analysis (PCA) to reduce the                   dimensionality of the variables. We used a 95% explained variance for our PCA which reduces the dimensions to 60 components <p>
  
 
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
        <li> PCA components (Top 15)</li>
        <li> PCA components (Top 15)  + Variables with Feature Importance (Top 5)</li>
      </ol>
 
     <h4> Decision Tree (DT) </h4>
     <h4>  Random Forest </h4>
     <h4>Logistic Regression/ Support Vector Machine (SVM)</h4>
<h3> Model Improvements - Feature Selection </h3> 

<h3> Model Improvements - Ensembling </h3>
  <p> We also decided to conduct ensembling across the 3 different models to obtain better prediction and performance. </p> 

<h3> Presentation of Insights/ Recommendation </h3> 

<h3> Learning Outcome :D </h3> 

<h2> THANK YOU! </h2> 

<h2> References: </h2> 
<ol> 
  <li> Phishing scams in Singapore rose to 5,020 cases in 2021 from 16 in 2017, https://sg.news.yahoo.com/phishing-scams-singapore-5020-cases-2021-from-16-in-2017-desmond-tan-084615863.html </li>
</ol>
