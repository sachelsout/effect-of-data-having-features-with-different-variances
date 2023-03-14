# effect-of-data-having-features-with-different-variances
This repository shows how linear models like Support Vector Machines (SVM) and Logistic Regression (LR) behaves for the data having features with different variances and how we can tackle this issue. 
<h1>What is Variance</h1>

![image](https://user-images.githubusercontent.com/86348193/224968487-a4ff2545-2d9a-443c-926d-7005e91eb0c2.png) <br>
Variance is a measure of how data points differ from the mean. It is a measure of how far a set of data (numbers) are spread out from their mean (average) value. In the variance formula, squared sigma is the variance, summation is summing/looping through all the datapoints, xi is the datapoint, xi_bar is the mean of the datapoints and N is the number of datapoints<br>
<h1>What if data has features with different Variances</h1>

![image](https://user-images.githubusercontent.com/86348193/224969907-e7f20c69-69ab-410e-8c9f-fbcda19cccd5.png) <br>
Consider there are 3 features f1,f2,f3 having different variance values. One of the feature f3 is highly correlated with the ouput label y. Typically, f3 should get highest feature importance amongst all the features. But this does not happen. Due to different variances, the linear models are not able to interpret the feature importances properly.<br>
After using linear models like Logistic Regression and Support Vector Machines, below are the feature importances obtained.<br><br>
<b><ins>For Logistic Regression</b></ins><br>
Feature f1 score is :  11070.275564782807<br>
Feature f2 score is :  -13901.807078828466<br>
Feature f3 score is :  9221.654056354826<br><br>
<b><ins>For SVM</b></ins><br>
Feature f1 score is :  3370.3580271414594<br>
Feature f2 score is :  -12120.653905895764<br>
Feature f3 score is :  10724.13991642756<br><br>
<b><ins> Observation</b></ins><br>
1. In Logistic Regression, Feature 2(f2) with negative sign has the highest value whereas in SVM, Feature 2(f2) with negative sign has the highest value. So, due to different variance of features, we are getting uninterpretable feature importances.<br>
2. Feature 3 should get the highest feature importance as Feature 3 is the most correlated feature to the variable y.(f3 = 0.839060 which is highly correlated) compared to other 2 features(f1 = 0.067172 and f2 = -0.017944)<br>
<h1>Data Standardization to the Rescue</h1>

![image](https://user-images.githubusercontent.com/86348193/224973395-febb40d0-bd20-492e-8015-7e0410d190b9.png)<br>
To tackle the different feature variances porblem, data standardization can be used.<br>
<b>Data Standardization</b> is the statistical technique to center the mean at zero and scale the variance to unit length.<br>
After standardizing the data using sklearn's <b>StandardScaler()</b>, below are the feature importance scores for Logistic Regression and SVM linear models.<br><br>
<b><ins>For Logistic Regression</b></ins><br>
Feature f1 score is :  2.4215865651559607<br>
Feature f2 score is :  4.513194368442512<br>
Feature f3 score is :  13.365047741400916<br><br>
<b><ins>For SVM</b></ins><br>
Feature f1 score is :  -2.7506137522289436<br>
Feature f2 score is :  1.4934906475265775<br>
Feature f3 score is :  12.279421550485994<br><br>
<b><ins> Observation</b></ins><br>
1. After applying Logistic Regression and SVM on standardized(In standardization, mean centering and variance scaling is done((x-μ)/σ),to obtain mean = 0 and std-dev = 1) data, we can see that feature f3 gets highest feature importance value(highest weight).<br>
2. Feature 3 should get the highest feature importance as Feature 3 is the most correlated feature to the variable y.(f3 = 0.839060 which is highly correlated) compared to other 2 features(f1 = 0.067172 and f2 = -0.017944)
