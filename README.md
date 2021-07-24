# DataScience-predicting-house-energy-use-based-on-iot-measurements

## Goal: 

Predicting the energy usage of a house based on Internet Of Things (IoT) measurements of temperature and humidity and weather observations. 

The data set is split into training (75% - 14803 observations, 32 features) and testing data (25% - 4932 observations, 32 features) for the period Jan-2016 - Jun-2016. Those features inlcude Appliances energy consumption,
Light energy consumption, T1 - Temperature in kitchen area, RH1 - Humidity in kitchen area, T2 - Temperature in living room area, RH2 - Humidity in living room area, T3 - Temperature in laundry room area, RH3 - Humidity in laundry room area, T4 - Temperature in office room, RH4 - Humidity in office room, T5 - Temperature in bathroom, RH5 - Humidity in bathroom, T6 - Temperature outside the building
(north side), RH6 - Humidity outside the building, T7 - Temperature in ironing room, RH7 - Humidity in ironing room, T8 - Temperature in teenager room 2, RH8 - Humidity in teenager room 2, T9 - Temperature in parents room, RH9 - Humidity in parents room % 20
To - Temperature outside, Pressure, RHo - Humidity outside, Windspeed, Visibility, Tdewpoint, Random Variable 1 (RV 1, Random Variable 2 (RV 2), Number of seconds from midnight (NSM), Week status, Day of week (Monday, Tuesday. . .
Sunday), Date time stamp.

## This project explores:

- The energy consumption profile shows a high variability over a week period, as well as over 6-month period from Jan-2016 to Jun-2016;

- The data distribution has a long tail;
    
- The median has a value of 60 Wh. The lower whisker has a value of 10 Wh and the upper whisker has a value of 170 Wh. It also shows that the data above the median is more dispersed and that there are several outliers.
    
- The important relationships between temperature and humidity measurements from a wireless network with the energy consumption of appliances in the training set are explored through pair plots. The highest correlations remains between Temperature in kitchen area and Temperature in laundry room area (0.89), Temperature in kitchen area and Temperature in living room area (0.84). These would be useful for building energy modeling, measuring the most representative rooms and that might be helful for the energy prediction of appliances. The relationships between the humidity in each room and the appliances’ consumption are quite clear. Humidity in the kitchen area and Appliances are positively correlated (0.06). This could be explained by higher humidity levels in the zone when cooking and human presence. There is a positive correlation between appliances’ consumption and laundry room humidity of 0.04. This might represent the use of washing machine and/or dryer. Moreover, interestring positive correlations between the energy consumption of appliances and lights (0.19), between appliances and Temperature in living room area(0.12) are also observed. 
    
- Via an hourly heat map, patterns are identified. More specifically, the energy consumption starts to rise around 6.30 am. Then around noon, there are energy load
surges. The energy demand also strongly increases around 6 pm. However, there is no
clear pattern regarding the day of the week.

- A Linear Reression is built to predict the energy usage of a house based on all features. However, this model is not a good model because the RMSE is too high while R2 is very slow. As the residuals are not normally distributed around the horizontal axis, we can tell the relationship between the variables and the energy consumption of appliances is not well represented by the linear model. Similarly, MAE and MAPE, which are other simple metrics representing the absolute value of the difference between the predicted value and the actual value, are high (over 50). This means that an error we can expect from the prediction on an average is big.

- On the other hand, via RFE and RFECV techniques, not only, the optimal number of features is 25, with lights, T1 - Temperature in kitchen area, RH_1 - Humidity in kitchen area, T2 - Temperature in living room area, RH2 - Humidity in living room area, T3 - Temperature in laundry room area, RH3 - Humidity in laundry room area, T7 - Temperature in ironing room, RH7 - Humidity in ironing room, To - Temperature outside, Windspeed, Tdewpoint.

In overall, although the linear model is considered not ideal for predicting the energy usage of a house with high RMSE, MAE, MAPE, and low R2. This can be because of the limitation of this project that the data was obtained from one house and the short length of continuous data. Important information could be found when analyzing several houses, and other relationships can be studied with appliances’ energy consumption in combination with: occupant’s age, number of occupants, ownership of pets, building’s geometry etc. However, via the ranked features from RFECV and the data analysis, we can conclude:
- From a wireless network's data, temperature and humidity measurements from the kitchen, laundry room, living room had the most important contributions. Hence, data from a wireless sensor network that measures humidity and temperature has been proven to increase the prediction accuracy.
- On the other hand, the weather data from the nearby weather station was shown to increase the prediction accuracy. More specifically, pressure, the outdoor temperature, dew point (the temperature the air needs to be cooled to), outdoor relative humidity, wind speed, are important and also quite representative to improve the appliances energy consumption prediction.
