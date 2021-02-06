# RATING AND PARTICIPANTS PREDICTION USING CPD ANALYSIS DATASET
Data Mining Project 
Predicting score ratings using CPD Analysis Dataset

## Table of contents:
* Introduction
* Problem Statement
* Dataset Description
* Hypothesis from dataset
* Exploratory data analysis steps
*
*

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
 
 ### Identifying the summary of a DataFrame. This method prints information about a DataFrame including the index dtype and column dtypes, non-null values and memory usage.
 ![2021-02-07 (2)](https://user-images.githubusercontent.com/77633676/107124112-cad54380-68dc-11eb-9c1e-b709c23a06c5.png)
 
 ### Visualization Using PowerBi
 ![2021-02-07 (3)](https://user-images.githubusercontent.com/77633676/107124304-163c2180-68de-11eb-93af-cb8fd9bdd948.png)
 
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
 Data preprocessing is a data mining technique that involves transforming raw data into an understandable format. Real-world data is often incomplete, inconsistent, and lacking in certain behaviors or trends, and is likely to contain many errors. Data preprocessing is a proven method of resolving such issues.
 
 ## Data Cleaning
 Data cleaning is the process of fixing or removing incorrect, corrupted, incorrectly formatted, duplicate, or incomplete data within a dataset.
 These are the steps in data cleaning :
1)	Select each attributes in the excel file that need to be cleaned. 
2)	Click on Data at the above section and enter filter.
3)	Select the small box at the attributes and it will shows the list of data for each attributes.
4)	Tick the blanks data then click remove data to delete unwanted data in the specific attributes.
5)	Continue the process for the next attributes until the last attributes in the Excel file to ensure the next process is smooth and valid
6)  Remove unimportant attributes that are not actually needed, and don’t fit under the context of the problem we’re trying to solve

### VLOOKUP
There are some purpose that lead us to do the VLOOKUP formula. It is because we need to sort the ‘Latihan’ in the Sheet 2 into each ‘Purata Skor Penilaian Keseluruhan’ in the Sheet 1 that I already renamed as ‘CSkor’. It will automatically construct each of the ‘Tajuk Latihan’ with specific score that given and counted in average. Here the steps that I used to do the VLOOKUP:
1)	Create an attribute in the dataset that we need to have new information.
2)	Then state the VLOOKUP formula at the Formula Bar above the attributes od the dataset.
![2021-02-07 (9)](https://user-images.githubusercontent.com/77633676/107127104-da5d8800-68ee-11eb-9654-e02cca828d55.png)

Besides,  I also that initiative to create an another attributes the classify the score of the events into three classes which are Low, Middle and High. The class is name as ‘Skor Klasifikasi’. The attributes will help us in the Model Performances later on.

![2021-02-07 (11)](https://user-images.githubusercontent.com/77633676/107127220-95862100-68ef-11eb-9e7e-c2bd0f763582.png)

### Change data type
By performing EDA, i found out that majority of the features in the datasets are in objects. So, i need to change it to numerical values. These are the examples on how to changes the data type.

df = df.replace({"Klasifikasi": {"PBP":1,"KAP":2, "CPD":3}})

df = df.replace({"Skor Klasifikasi":  {"High":1,"Middle":2, "Low":3}})

![ssdm](https://user-images.githubusercontent.com/77633676/107126550-8ef5aa80-68eb-11eb-945e-4e995ca1b288.jpeg)

Now, the datasets type are now in numerical.
 ### Splitting datasets into training and test set
I need to split data-set into two separate sets whic is training set and test set for machine learning model. Well here it’s your algorithm model that is going to learn from your data to make predictions. Generally we split the data-set into 70:30 ratio or any other test size. 70 percent data will be taken into train and 30 percent data will be taken into test. However, this splitting can be varies according to the data-set shape and size.

![2021-02-07 (7)](https://user-images.githubusercontent.com/77633676/107126847-3de6b600-68ed-11eb-8e36-24d5553baf21.png)







 
 

 



 

