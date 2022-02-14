# AV_Jobathon_Feb_2022


Problem Statement and Objective![image](https://user-images.githubusercontent.com/59175345/153956594-e883962f-d2a2-4a4b-af44-e729564319d1.png)
Objective
The main objective of the problem is to develop the machine learning approach to predict the engagement score of the video on the user level.

Problem Statement

ABC is an online content sharing platform that enables users to create, upload and share the content in the form of videos. It includes videos from different genres like entertainment, education, sports, technology, and so on. The maximum duration of the video is 10 minutes.
Users can like, comment, and share the videos on the platform. 
Based on the user’s interaction with the videos, an engagement score is assigned to the video with respect to each user. The engagement score defines how engaging the content of the video is. 
Understanding the engagement score of the video improves the user’s interaction with the platform. It defines the type of content that is appealing to the user and engages the larger audience.

![image](https://user-images.githubusercontent.com/59175345/153956629-9e44611b-c1de-4a64-a71f-ef3b7b30c241.png)

![image](https://user-images.githubusercontent.com/59175345/153956656-e58d0968-4a05-4451-b406-e5a93ea0a252.png)



Objective: To build a generic model to predict user engagement score for a video
![image](https://user-images.githubusercontent.com/59175345/153953433-63cbc12c-584e-4c10-bea7-ddafda89acbb.png)

Observations from EDA and Feature engineering:
![image](https://user-images.githubusercontent.com/59175345/153953615-cedc3516-3dcc-45e9-9c80-3f454a687af4.png)

The target ‘engagement_score’ is a continuous variable but most of the predictors are discrete in nature.  Gender, Age, Profession are categorical.
There are no missing values and distribution of data in train and test sets is reasonable.  
The initial idea after understanding of data type suggests a Decision tree algorithm over linear regression due to the nature of predictors.
My approach is to perform label encoding for gender and Profession instead of one-hot encoding.
We will leave user_id, category_id, Video_id, age, followers, and views as it is. It could be a further opportunity to use cardinal encoding using frequency.
Transformation of the target is not suggested as it has values of 0. Although 0 engagement is outliers ( data is left-skewed) it is good to keep them in the model for understanding user interaction variability.  
![image](https://user-images.githubusercontent.com/59175345/153953564-a239a3d5-e610-4f84-9de8-2c1629c007ac.png)


The most important predictors are gender, age, and profession. 
Views and followers have very little impact on engagement score which is opposite to the expectations. 
Generally Male are more involved with content and they generate a higher engagement score.  There are specific categories where there is a wide gap between male and female engagement rates. There are specific categories where male and female engagements are similar. 
Young age people are generating more engagement scores and engagement is decreasing as age increases. People between 15 to 25 are most active on online platforms. There are a very low number of people above age 40 available on the platform
Label encoding gives a better result than one_hot_encoding in this case.
Combiming gender, age and profession to create special categories can be a good option which I could have tried.
![image](https://user-images.githubusercontent.com/59175345/153953657-7dab4424-eafe-4c93-94bd-bde42c5dfa04.png)
![image](https://user-images.githubusercontent.com/59175345/153956782-a43fbb7c-a519-466b-9225-4f85057f7d5d.png)



I executed the decision tree as the first model but it yielded a negative R2 score. 
So I tried multiple models with cross-validation and found Random forest and XGBoost regression models performing better than others. 
Random forest was performing better on test set data than boost. 
SO I used Random forest as the final model. 
Further finetuning opportunities :
Hyper parameter tuning using grid cv search and randomized search
Other ideas if I would have tried if there was more time:
Use of Clustering to create user-categories based on gender, age, profession, and engagement score and use these profiles for further prediction of  test engagement score.

![image](https://user-images.githubusercontent.com/59175345/153953688-948e2b39-2abe-4900-8035-330adde9aaea.png)


![image](https://user-images.githubusercontent.com/59175345/153953746-f5361466-8eb1-4951-99bc-1d673a78e02f.png)


Possible exploration if I had more time![image](https://user-images.githubusercontent.com/59175345/153953818-aadfe05e-bb6e-43d1-bb71-63c9f9b26ecf.png)

Use clustering to create user categories based on gender, age, profession, and engagement score and use these as one of predictor
The first thought was that we need to build a recommender system here with the exception that we will stop at predicting engagement score, so my idea would be to develop a recommender system and test the result
![image](https://user-images.githubusercontent.com/59175345/153953843-90b712cb-b0ec-4259-8d8f-e97a7e8c365b.png)




