# Weather Prediction with RNN

Project done for Machine Learning - Advanced course.  [Historical Hourly Weather Data 2012-2017](https://www.kaggle.com/datasets/selfishgene/historical-hourly-weather-data/data) dataset was used to traing recurrent neural network.

## Dataset 
Dataset contains 5 years of hourly weather measurements in 36 cities. Weather attributes available are:
- **pressure** - air pressure in hPa,
- **wind speed** - in meters per second,
- **humidity** - relative humidity of air,
- **temperature** - in Kelvin,
- **wind direction** - in degrees: 0 corresponding to N, 90 - E, 190 - S, 270 - W.

## Data preparation
Data was prepared for training - that included removing NaN values, transforming humidity values to dew point and representing wind direction by sine and cosine values. 

Humidity value is given in percentages and is unreliable. At 32 degrees Celsius humidty of 60% feels very uncomfortable, but at 22 degrees it fine.  That's why its distribution doesn't look great to train neural network on.

![download](https://github.com/user-attachments/assets/880bc0df-8680-444c-94f5-281ccc1d60f7)

Dew point describes to which temperature air has to be cooled in order to form dew drops on surrounding surfaces. After transforming, the distribution looks much better.

![download](https://github.com/user-attachments/assets/b15f4828-2779-4241-8735-a20c61cfca9f)

Wind direction was also transformed, because it's values are cyclical - wind direction of 0 and 360 represent same direction, but are on the opposite ends of possible values. Using sine and cosine we managed to avoid that problem.

## Training and comparing results
We trainded few models and compared them. From our results we gathered, that models trained only on one attribute at the time gives more accurate results that model that trained on all of them at once. That disproved our theory that it may be opposite, because of relation of different weather elements to each other.  Here are result comparing temperatures for San Francisco.

![download](https://github.com/user-attachments/assets/0aef9f57-a0a8-4775-9e09-7372a3650799)  
Temperature prediction results from model trained on all attributes.  
Value of errors measured: RMSE=0.2380, MSE=0.0566, MAE=0.1833, R^2=0.9617, Pearson=0.9838, IA=0.9899  


![download](https://github.com/user-attachments/assets/fb9e913f-e44d-43da-abe1-a71897051be5)  
Prediction results from model trained only on temperature.  
Value off errors measured: RMSE=0.2030, MSE=0.0412, MAE=0.1166, R^2=0.9722, Pearson=0.9884, IA=0.9934  

Using model trained on Toronto data for Tel Aviv gave reasonable results, considering how different climates are in those cities.  

![download](https://github.com/user-attachments/assets/170c62a3-faf8-4bcb-bffa-416242f72066)  

## Final thought
There are more result in the notebook to view. This is maybe bit lenghty, but I wanted to show most interesting points.  
Although this was fine exercice to learn, our proffessor pointed out that weather predictions is more tricky than that and has to take into consideration current physical properties of the atmosphere. 





