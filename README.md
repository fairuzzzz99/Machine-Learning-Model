# Rating and Participation Prediction 
Data Mining Project 
Predicting score ratings using CPD Analysis Dataset

## Table of contents:
* Introduction
* Problem Statement
* Dataset Description
* Hypothesis from dataset
* Exploratory data analysis steps
* Data Preprocessing
* Descriptive and Predictive Data Mining
* Data Mining Performances Comparison
* Conclusion
* Reflection


## Introduction
Continuing Professional Development (CPD) is a combination of approaches, ideas and techniques that will help you manage your own learning and growth. The focus of CPD is firmly on results – the benefits that professional development can bring you in the real world.


## Problem Statement
From the CPD Analysis, I found out that the rating score given by the participants and number of participants from our CPD activities in 2020 is not achieve target which is High score rate and 10,000 participants. The CPD activities only achieve Middle score and only 5,437 participants. In 2021, the goal to achieve High score rate and 10,000 participants need to be achieve.

## Dataset Description
For this project, I'm using the CPD Analysis Dataset.  CPD Analysis Dataset contains analysis of CPD used in computing rating and participation prediction in UPM. Prediction of the rating are based on the activities held. Prediction of the score rating are based on the classification of activities held and the topic. The raw dataset was in *.xlsx*  format.

## Hypothesis from dataset 
Based on the dataset given, several questions has been made : 
 * Which classification has the lowest score penilaian?
 * Does classification of activities affecting the score rating ?
 * What is the relationship between rating and participants?
 * What is the total participants of every classifications?
 
## Stakeholders
 The stakeholder that involved in CPD Analysis is management and staff(participants). The importance of this project to stakeholdersare:  
 * The management easy to predict the preferences of participants for the next event
 * The management can ollect data and analyze the most preferred activities to improve the rating and gain more participant
 * The management can improvise facilities needed during the activities
 * Participants can easily choose what topic of activity that suitable for them to join
  
## Exploratory Data Analysis Steps 
 Exploratory data analysis or EDA is the first and foremost of all tasks that a dataset goes through. EDA lets us understand the data and thus helping us to prepare it for the upcoming tasks.
  
### Import Dataset
 import pandas as pd
 
 from google.colab import files
 
 uploaded = files.upload()
 
 df = pd.read_excel(io.BytesIO(uploaded['CPD for rpm and colab.xlsx']))
 
### Identifying the summary of a DataFrame. 
 This method prints information about a DataFrame including the index dtype and column dtypes, non-null values and memory usage.
 ![2021-02-07 (2)](https://user-images.githubusercontent.com/77633676/107124112-cad54380-68dc-11eb-9c1e-b709c23a06c5.png)
 
### Visualization Using PowerBI
 ![2021-02-07 (3)](https://user-images.githubusercontent.com/77633676/107124304-163c2180-68de-11eb-93af-cb8fd9bdd948.png)
 
 OBSERVATION
From the first diagram which Jabatan against Skor Penilaian, we can see that Fakulti Perubatan & Sains Kesihatan has the highest overall Skor Penilaian (803.64) while Fakulti  Alam Sekitar has the lowest overall Skor Penilaian (4.62) 

From the second diagram which Average of Jumlah Jam and Tempat Latihan  against Klasifikasi, we can see KAP has the highest Average of Jumlah Jam (37.92 hour ) while PBP has the highest Average of Skor Penilaian (4.79) compared to KAP and CPD.

From the third diagram which Klasifikasi against Skor Penilaian, we can see that PBP has the highest Skor Penilaian which is 4481.95  while KAP has the lowest Skor Penilaian  with 450.17.

From the fourth diagram which Jumlah Jam against Tajuk Latihan & Tempat Latihan , with 81 hours(24.18), KURSUS SISTEM PUTRABLAST V3.8(SIRI-9 FSPM UPMKB) where the Tempat Latihan is MAKMAL D ICT, UPMKB has the highest  Jumlah Jam.

From  the fifth diagram, Skor Penialaian of Klasifikasi (PBP) and Tajuk Latihan (MAJLIS PERASMIAN & ASPIRASI NC SEMPENA BULAN PENDIDIK UPM 2020) is 785.40  which is the highest.
 
### Answers of questions based on visualization
  * Which classification has the lowest score penilaian?
  KAP has the lowest score rating.
  
 * Does classification of activities affecting the score rating ?
  Yes.  Every classification of activities has different score rating.
 
 * What is the relationship between rating and participants?
 Higher participants, higher score given. 
 
 * What is the total participants of every classifications?
 CPD- 287 , KAP- 94 , OLCPD- 3666 , PBP- 937 , PicTL- 453
 
 ## Data pre-processing
 Data preprocessing is a data mining technique that involves transforming raw data into an understandable format. Real-world data is often incomplete, inconsistent, and lacking in certain behaviors or trends, and is likely to contain many errors.  To resolve such issues, data preprocessing must be done.
 
 ### Data Cleaning
 Data cleaning is the process of fixing or removing incorrect, corrupted, incorrectly formatted, duplicate, or incomplete data within a dataset.
 These are the steps in data cleaning :
1)	Select each attributes in the excel file that need to be cleaned. 
2)	Click on Data at the above section and enter filter.
3)	Select the small box at the attributes and it will shows the list of data for each attributes.
4)	Tick the blanks data then click remove data to delete unwanted data in the specific attributes.
5)	Continue the process for the next attributes until the last attributes in the Excel file to ensure the next process is smooth and valid

### Data Integration
Data integration is the merging of data from various sheets into one new sheets. Data integration is performed on the attribute which identifies unique entities. It needs to be done carefully because errors in data integration can produce deviant results and even misleading the action later. 

### Data Selection
The data that from the dataset given is often not all used, therefore I took the initiative to bremove unimportant attributes.

### VLOOKUP
There are some purpose that lead us to do the VLOOKUP formula. It is because we need to sort the ‘Latihan’ in the Sheet 2 into each ‘Purata Skor Penilaian Keseluruhan’ in the Sheet 1 that I already renamed as ‘CSkor’. It will automatically construct each of the ‘Tajuk Latihan’ with specific score that given and counted in average. Here the steps that I used to do the VLOOKUP:
1)	Create an attribute in the dataset that we need to have new information.
2)	Then state the VLOOKUP formula at the Formula Bar above the attributes od the dataset.
![2021-02-07 (9)](https://user-images.githubusercontent.com/77633676/107127104-da5d8800-68ee-11eb-9654-e02cca828d55.png)

Besides,  I also that initiative to create an another attributes the classify the score of the events into three classes which are Low, Middle and High. The class is name as ‘Skor Klasifikasi’. The attributes will help us in the Model Performances later on.

![2021-02-07 (11)](https://user-images.githubusercontent.com/77633676/107127220-95862100-68ef-11eb-9e7e-c2bd0f763582.png)

### Data Transformation
Data is converted or combined into a format suitable for processing in data mining. Some data mining methods require special data formats before they can be applied.
By performing EDA, I found out that the majority of the features in the data set are objects. So, I need to change the data type into numerical values.
These are the example on how I change the data type from object into int:

`df = df.replace({"Klasifikasi":  {"PBP":1,"KAP":2, "CPD":3}})`

`df = df.replace({"Skor Klasifikasi":  {"High":1,"Middle":2, "Low":3}})`

![ssdm](https://user-images.githubusercontent.com/77633676/107126550-8ef5aa80-68eb-11eb-945e-4e995ca1b288.jpeg)

Now, the datasets type are now in numerical.

### Splitting datasets into training and test set
I need to split data-set into two separate sets whic is training set and test set for machine learning model. Well here it’s your algorithm model that is going to learn from your data to make predictions. Generally we split the data-set into 70:30 ratio or any other test size. 70 percent data will be taken into train and 30 percent data will be taken into test. However, this splitting can be varies according to the data-set shape and size.

![2021-02-07 (7)](https://user-images.githubusercontent.com/77633676/107126847-3de6b600-68ed-11eb-8e36-24d5553baf21.png)

## Steps in developing Descriptive and Predictive Data Mining 

### Descriptive Data Mining
A descriptive model describes a system or other entity and its relationship to its environment. It is generally used to help specify and/or understand what the system is, what it does, and how it does it. In this case, i chose clustering as the method of our process and k-means as the data mining model.
These are the steps in developing descriptive data mining solution :
1. Choose the right number of cluster(k) by performing elbow method
2. k-value is obtained by picking the fewest number of clusters that reduces the average distance. After k-value, the graph is almost linear.
3. Once we obtained the k-value, we can visualize the clustering.

For RapidMiner :
![dtree](https://user-images.githubusercontent.com/77633676/107356545-e8d4bb00-6b0b-11eb-801f-f53e16b4ff20.png)
![rforest](https://user-images.githubusercontent.com/77633676/107356765-29cccf80-6b0c-11eb-98d0-ec7a63ddc7e5.png)
On RapidMiner,  I implemented a new things which is Discretize.  I will explain the function of each parameters that I used in the RapidMiner in order to process my decision making.

•Retrieved in RapidMiner is use to input the data folder into the process. We can also use Read parameter but it is slower since it needs to process each time when you fill in the data. However, by using retrieved, you just need to do it once since you already saved the file in the repository in the application.

•	Discretize by Frequency - Discretized by Frequency is for when you want the sort or separate the implement into each of class that you already classified in the Excel and edit the number of bins based on class you stated. 

•	Nominal to Binominal -  Nominal to Binominal operator is used for changing the type of nominal attributes to a binominal type. This operator not only changes the type of selected attributes but it also maps all values of these attributes to binominal values i.e. true and false.

•	Set Role - We using set role to determine the special attributes that we need to count. 

•	Select Attributes - Select attributes is using is mainly for separate the use and unuse attribute in order to calculate the attribute.

•	Split Data - In split data, it will be boxes that we can fill to put ratio of our studies over 1.0. The top box usually 0.7 and below will be 0.3. But in some cases, people also put 0.8 and 0.2. The higher of top box the lower accuracy you can get formulally. 

•	Decision Tree  / Random Forest - Decision tree and Random Forest are the common models that people use to predict things in RapidMiner normally it uses to calculate the classification, the characterized data not numerical.

•	Apply Model - In apply model, it for applied the parameters that we stated behind it. It also have goal to predict the unseen data and to transform data into a pre processing model.

•	Performance - It will make the models compatible and do the generating.


### Predictive Data Mining
Predictive analytics is the process by which information is extracted from existing data sets for determining patterns and predicting the forthcoming trends or outcomes.The methods come under this type of mining category are called classification, time-series analysis and regression. In this case i chose classification as the method for this process.
These are the steps in developing predictive data mining solution :  
1.Load the required libraries.
2.Import and upload file into GoogleColab
3.Load data and read file that has been uploaded
4.Divide given columns into two types of variables dependent(or target variable) and independent variable(or feature variables).
5.Import the required classifier to be used metrics function
6.Print the accuracy of the model (Decision Tree and Random Forest) 

## Data Mining Performance Comparison

### Hyperparameter Tuning
In machine learning, hyperparameter optimization or tuning is the problem of choosing a set of optimal hyperparameters for a learning algorithm. There are 3 common Hyperparameter optimization whuch is Grid Search, Random Search, Bayesian Optimization . With this technique, we simply build a model for each possible combination of all of the hyperparameter values provided, evaluating each model, and selecting the architecture which produces the best results. For example, we would define a list of values to try for both n_estimators and max_depth and a grid search would build a model for each possible combination. The diagram below shows the suggested values after hyperparameter tuning has been done for decision tree model: 

![2021-02-08 (11)](https://user-images.githubusercontent.com/77633676/107240782-43670c00-6a65-11eb-9540-7dff67580691.png)

After the suggested values have been used to obtain new accuracy, we can see that the hyperparameter tuning makes the accuracy increase from 89.27% to 97.18%. Thus, the performance is increasing as well.

## Conclusion

All the model show increase in accuracy after tuning
The best model goes to Decision Tree in predictive data mining with the accuracy of 100% 
We get accuracy 100% because the dataset is overfit and easy to predict 

## Reflections
From this project,I have learned many new thing about data science. I Learn to visualize our hypothesis into interactive visualization. I also experienced in using software tools such PowerBI, Tableau, RapidMiner. Google Colaboratory-Python which i never know about their present. I also realized that Exploratory Data Analysis is a vital step in a data science project. The main pillars of EDA are data cleaning, data preparation, data exploration, and data visualization. I also learn the scope of work of data scientist whcih is not easy at all. It is such an incredible journey throughout the one semester learning Data Mining with Dr Fadhlina and do all the tasks and project. Thank you Dr Fadhlina for all the knowledge and effort in teaching us. 






 
 

 



 

