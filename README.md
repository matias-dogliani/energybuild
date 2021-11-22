# Energy Usage of an office building

Predicting the energy consumption of an office building

### Group : 

* Calixto, Ian 
* Doblas Florido, Maria Angeles
* Dogliani, Matias 
* Nord, Nathan Thomas 

## Data Acquisition 

This [jupyter notebook](https://github.com/matias-dogliani/energybuild/blob/master/DataSet_Weather.ipynb) 
contains all code used to acquire and to save the data frames, and a brief step by step explanation

### Historical Weather Data 

For training and testing the model we use the historical  weather data related to our energy consumption data provided.
We've  use the API provided by [AT-Wetter](http://at-wetter.tk/index.php?men=api)

This API don't need a Key or other autentication. It's located on the AT-Server in `http://at-wetter.tk/api/v1/.` 
and the instruction to use it are in their [website](http://at-wetter.tk/index.php?men=api) 

The data downloaded for the same datapoints of the energy consumptions: 

![Temperature: Yearly](https://github.com/matias-dogliani/energybuild/blob/master/Imgs/Weather_year.png)

### Energy reading 

This dataset was provided by the Professor. 


![Energy usage: yearly](https://github.com/matias-dogliani/energybuild/blob/master/Imgs/Energy_usage_year.png)

### Forecast

For the final prediction of the energy consumption, we use the [OpenWeather - API](https://openweathermap.org/api)
with free access to download an hourly Forecast 4 days data set


## Data pre processing 

### Energy Reading 

The distribution of our data: 
![Energy usage: histogram](https://github.com/matias-dogliani/energybuild/blob/master/Imgs/Energy_usage_histogram.png)


#### Outliers and anomalies 

Explanation pendent..

### Weather 

In order to have the same timestamps of the weather data and the energy reading we've used `pandas.merge()` function. 
Then, we replace the missing values with the `interpolate` function 


## Model comparision 

### Linear Regression 

### Tree decision regression 

### SVR regressor 

### MLVR neural network 


## Predicting 


