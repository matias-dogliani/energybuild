# Energy Usage of an office building

Predicting the energy consumption of an office building

### Group : 

* Calixto, Ian 
* Doblas Florido, Maria Angeles
* Dogliani, Matias 
* Nord, Nathan Thomas 

## Data Acquisition 

The [jupyter notebook](https://github.com/matias-dogliani/energybuild/blob/master/DataSet_Weather.ipynb) 
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

### Forecast

For the final prediction of the energy consumption, we use the [OpenWeather - API](https://openweathermap.org/api)
with free access to download an hourly Forecast 4 days data set


## Data pre processing 

### Energy Reading 


#### Outliers and anomalies 

figure of the distribution and the outliers 

We consider our distribution as a normal gaussian distribution. In order to 
find the anomalies we took just 4 standar desviation and the elements outside of this limits are considered outliers. 

To replace this outliers we use the `interpolate` function of pandas package with the `linear` method 

Also we cast the reading values into a int values. For that, firs we had to delete the units string 'KWh' 

### Weather 

In order to have the same timestamps of the weather data and the energy reading we've used `pandas.merge()` function. 
Then, we replace the missing values with the `interpolate` function 


## Model comparision 

### Linear Regression 

### Tree decision regression 

### SVR regressor 


### MLVR neural network 




