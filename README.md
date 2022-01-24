# Appliances-Energy-Prediction-Capstone_Project

This project deals with predicting appliances energy consumption of a particular household in Belgium based on the temperature and humidity levels of different rooms in the building and the weather reports in the area over a period of 4.5 months.

The data set is at 10 min for about 4.5 months. The house temperature and humidity conditions were monitored with a ZigBee wireless sensor network. Each wireless node transmitted the temperature and humidity conditions around 3.3 min. Then, the wireless data was averaged for 10 minutes periods. The energy data was logged every 10 minutes with m-bus energy meters. Weather from the nearest airport weather station (Chievres Airport, Belgium) was downloaded from a public data set from Reliable Prognosis (rp5.ru) and merged together with the experimental data sets using the date and time column. Two random variables have been included in the data set for testing the regression models and to filter out non-predictive attributes (parameters).

# Dataset Link

http://archive.ics.uci.edu/ml/datasets/Appliances+energy+prediction

# Dataset Information

Number of instances: 19,735

Number of attributes: 29

# Attribute Information:

date: year-month-day hour:minute:second

T1: Temperature in kitchen area, in Celsius

RH_1: Humidity in kitchen area, in %

T2: Temperature in living room area, in Celsius

RH_2: Humidity in living room area, in %

T3: Temperature in laundry room area

RH_3: Humidity in laundry room area, in %

T4: Temperature in office room, in Celsius

RH_4: Humidity in office room, in %

T5: Temperature in bathroom, in Celsius

RH_5: Humidity in bathroom, in %

T6: Temperature outside the building (north side), in Celsius

RH_6: Humidity outside the building (north side), in %

T7: Temperature in ironing room, in Celsius

RH_7: Humidity in ironing room, in %

T8: Temperature in teenager room 2, in Celsius

RH_8: Humidity in teenager room 2, in %

T9: Temperature in parents’ room, in Celsius

RH_9: Humidity in parents’ room, in %

T_out: Temperature outside (from Chievres weather station), in Celsius

Pressure: (from Chievres weather station), in mm Hg

RH_out: Humidity outside (from Chievres weather station), in %

Wind speed: (from Chievres weather station), in m/s

Visibility: (from Chievres weather station), in km

T_dewpoint: (from Chievres weather station), Â°C

rv1: Random variable 1, non-dimensional

rv2: Random variable 2, non-dimensional

Lights: energy use of light fixtures in the house in Wh

Appliances: energy use in Wh (Target Variable)

Where indicated, hourly data (then interpolated) from the nearest airport weather station (Chievres Airport, Belgium) was downloaded from a public data set from Reliable Prognosis, rp5.ru. Permission was obtained from Reliable Prognosis for the distribution of the 4.5 months of weather data.

# Problem Statement
We should predict Appliance energy consumption for a house based on factors like temperature, humidity & pressure .
 
In order to achieve this, we need to develop a supervised learning model using regression algorithms. Regression algorithms are used as data consist of continuous features and there is no identification of appliances in the dataset.

# Descriptive Statistical Analysis:
Descriptive statistics are brief descriptive coefficients that summarize a given data set, Descriptive statistics are broken down into measures of central tendency and measures of variability (spread). Measures of central tendency include the mean, median, and mode, while measures of variability include standard deviation, variance, minimum and maximum variables.
# Observations (Temp Feature)

![image](https://user-images.githubusercontent.com/60994606/150723884-3e840ef3-3df4-4be5-953b-876de675b633.png)

1.The average outside temperature over a period of 4.5 months is around 7.5 degrees. It ranges from -6 - 28 degrees.

2.While the average temperature inside the building has been around 20 degrees for all the rooms. It ranges from 14 - 30 degrees.

3.This implies Warming appliances have been used to keep the insides of the building warm. There must be some sort of direct correlation between temperature and consumption of energy inside the house.

# Observations (Humidity Features)

![image](https://user-images.githubusercontent.com/60994606/150724092-4e82fc85-00d8-40d9-b68d-653530ed75a8.png)

1.Average humidity outside the building has been higher than the average humidity inside.

2.Average humidity at the weather station is significantly higher compared to outside humidity near the building.

3.Average humidity in the bathroom is significantly higher compared to other rooms due to obvious reasons.

# Heatmap Corelation Between Features:

![image](https://user-images.githubusercontent.com/60994606/150724295-414294eb-4c20-45ba-91a4-d99c64f0be73.png)

 # Observations from Heatmap correlation plot:
a. Features related to temperature Almost all the temperature measures in different rooms are highly linearly correlated with each other. However, there is little to no correlation between temperature features and target variables.

b. Features related to humidity Almost all the humidity measures in different rooms are highly linearly correlated with each other. However, there is little to no correlation between humidity features and target variables.

c. Weather data 

Dewpoint shows a higher correlation with most of the temperature and humidity level features than any other weather parameters. However, its correlation with the target variable is low. Pressure, wind speed, and visibility show little correlation with temperature and humidity features as well as the target variable.

# PCA on Temperature features:

![image](https://user-images.githubusercontent.com/60994606/150724856-e97d79b5-efdd-4955-b5bb-ea196da7244c.png)

First two components seem to explain more than 91 % of variance in data.

# PCA on Humidity features:

![image](https://user-images.githubusercontent.com/60994606/150725079-4bae470b-2ee2-4cb9-8397-505c96607d0a.png)

Similar to temperature first two components seem to explain more than 91 % of variance in data.

# Results:

![image](https://user-images.githubusercontent.com/60994606/150725432-52e3cd4e-cbb0-4362-a289-7e03ca13e96f.png)

# Model Result Trained With PCA Features

![image](https://user-images.githubusercontent.com/60994606/150725457-b321329c-86a1-4005-bc52-6093f9cfe2cf.png)

![image](https://user-images.githubusercontent.com/60994606/150725600-8a989bc4-e286-4a6a-9849-91a5af38a5b0.png)

# Model Result Trained without PCA Features

![image](https://user-images.githubusercontent.com/60994606/150725681-0f2971bf-b61a-4f32-878e-834399bab3b0.png)

# Feature Importances:

![image](https://user-images.githubusercontent.com/60994606/150725757-4ef55905-6a51-47fc-b1ed-aeb1bb15d6b2.png)

Feature Importances With PCA Features

![image](https://user-images.githubusercontent.com/60994606/150725811-49300d53-a8a4-49d8-a8d3-ef956fa571c6.png)

Feature Importances Without PCA Features

# Conclusion:
1. The humidity and temperature feature has little to no linear correlation with the target variable.
2. The time zone of the day plays an important role in deciding the power consumption of appliances.
3. The best Algorithm to use for this dataset is Extra Trees Regressor (tree-based algorithm).
4. PCA helped us to reduce our feature set dimension considerably without affecting the performance of our models significantly.
5. The untuned model was able to explain 75.50% of the variance (R2 score = 0.7550) on the test set, while the tuned model was able to explain 75.84% of the variance (R2 score = 0.7584).
6. The least RMSE score on the test data set is found to be around 0.5 by the Extra trees regressor model, which is considered good compared to other models.
7. Tree-based models are by far the best model while dealing with a data set that has most of its features have
8. no linear correlation with the target variable. For similar reasons, linear
9. models such as linear regression, Ridge, and Lasso perform the worst.


