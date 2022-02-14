# AV_Jobathon_Feb_2022


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
![image](https://user-images.githubusercontent.com/59175345/153957356-ab807a67-f395-4479-9ea8-550a3efbe5aa.png)


The most important predictors are gender, age, and profession. 
Views and followers have very little impact on engagement score which is opposite to the expectations. 
Generally Male are more involved with content and they generate a higher engagement score.  There are specific categories where there is a wide gap between male and female engagement rates. There are specific categories where male and female engagements are similar. 
Young age people are generating more engagement scores and engagement is decreasing as age increases. People between 15 to 25 are most active on online platforms. There are a very low number of people above age 40 available on the platform
Label encoding gives a better result than one_hot_encoding in this case.
Combiming gender, age and profession to create special categories can be a good option which I could have tried.
![image](https://user-images.githubusercontent.com/59175345/153957416-7572b655-758f-41b5-a343-dfd15ede6b32.png)





I executed the decision tree as the first model but it yielded a negative R2 score. 
So I tried multiple models with cross-validation and found Random forest and XGBoost regression models performing better than others. 
Random forest was performing better on test set data than boost. 
SO I used Random forest as the final model. 
Further finetuning opportunities :
Hyper parameter tuning using grid cv search and randomized search
Other ideas if I would have tried if there was more time:
Use of Clustering to create user-categories based on gender, age, profession, and engagement score and use these profiles for further prediction of  test engagement score.

![image](https://user-images.githubusercontent.com/59175345/153957473-b90af42a-6499-499d-b843-a59ab3f9faee.png)

Decision Tree Model view from random Forest :

![image](https://user-images.githubusercontent.com/59175345/153953746-f5361466-8eb1-4951-99bc-1d673a78e02f.png)


Possible exploration if I had more time![image](https://user-images.githubusercontent.com/59175345/153953818-aadfe05e-bb6e-43d1-bb71-63c9f9b26ecf.png)

Use clustering to create user categories based on gender, age, profession, and engagement score and use these as one of predictor
The first thought was that we need to build a recommender system here with the exception that we will stop at predicting engagement score, so my idea would be to develop a recommender system and test the result
![image](https://user-images.githubusercontent.com/59175345/153953843-90b712cb-b0ec-4259-8d8f-e97a7e8c365b.png)


EDA and Other Observations:
![image](https://user-images.githubusercontent.com/59175345/153957689-fd8e12b4-48a4-4265-a453-1de219eff9c5.png)

![image](https://user-images.githubusercontent.com/59175345/153957735-aa20169e-88e0-407f-9c21-7a30a8a09b06.png)

![image](https://user-images.githubusercontent.com/59175345/153957869-fbc04f96-aa20-43f7-85bb-0e5112c4cbaa.png)

![image](https://user-images.githubusercontent.com/59175345/153957914-b1e40e2c-aaab-474c-a711-487ee2e1b1bd.png)

![image](https://user-images.githubusercontent.com/59175345/153957977-1863530f-97c0-461c-b346-8f4371448849.png)

![image](https://user-images.githubusercontent.com/59175345/153958036-5603f20e-33ed-4152-a174-cb49451a86d6.png)

![image](https://user-images.githubusercontent.com/59175345/153958081-8447c74f-d9dd-49db-9d47-f16a3f227b56.png)

![image](https://user-images.githubusercontent.com/59175345/153958123-013128a2-a805-434c-ba0f-c46f8e551310.png)










