# Energy Usage of an office building

Predicting the energy consumption of an office building

[Presentation Slides](https://github.com/matias-dogliani/energybuild/blob/master/Slides/Machine%20Learning%20-%20Energy%20Prediction.pptx.pdf)

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

In this [jupyter notebook](https://github.com/matias-dogliani/energybuild/blob/master/PreProcess_EnergyConsumption.ipynb) is an step by step explanation of the pre processing 

### Energy Reading 

The distribution of our data: 
![Energy usage: histogram](https://github.com/matias-dogliani/energybuild/blob/master/Imgs/Energy_usage_histogram.png)

Pre processing consisted on: 

* Removing the string unit from the target variable 

* Overview analysis of data with plots 

* Find anomalies 

* Replace the anomalies with NaN values 

* Interpolate the NaN values 


#### Outliers and anomalies 


To detect the anomalies we've used a rule based method. We fixed these rules after a visual analisys of our data. 

We've consider an anomalie the: 

* Negative Values
* Zero Values
* Illogical Values (too high
or too low)

The upper limit was set to 4  of the median value and the lower limit to 0.3 of the median to 0.3 of the median. Both limits, and the median are in the plot  

![Energy Usage: finiding anomalies](https://github.com/matias-dogliani/energybuild/blob/master/Imgs/Energy_usage_year_annotated.png)

Once we've detected the outliers, with use the built-in function `interpolate()` of pandas to **replace** those values. 

### Weather 

We did not implement pre process on our data since we could not find, with visual analisys, any clearly outlier. In further work, we'll implement *gradient detection outlier* 

We did implemented a linear interpolation for the missin values of temperature data.
When we merged the Temperature data frame with the energy consumption data set, we realized that 
some points of temperature were missing (the data wasn't hourly stamped in some ranges). 

To have the same timestamps of the weather data and the energy reading we've used `pandas.merge()` 
function. 
Then, we replace the missing values with the `interpolate` function as we did in the energy consumption dataframe 

## Model comparision 

In this [Jupyter Notebook](https://github.com/matias-dogliani/energybuild/blob/master/Training_Testing_model.ipynb)
the models are trained and test. At last, we used the Tree Decision Regressor (the one which the best result ) 
to predict the energy consumption of 4 days in the future. 

We tried 4 different models. All of them with default hyperparameters 

Missing picture of R2 comparing 
### Linear Regression 

![Linear Reg : scatter plot](https://github.com/matias-dogliani/energybuild/blob/master/Imgs/linear_regression_model.png)


### Tree decision regression 

![Tree decision Reg : scatter plot](https://github.com/matias-dogliani/energybuild/blob/master/Imgs/tree_regressor_model.png)

### SVR regressor 
  
![SVR regressor : scatter plot](https://github.com/matias-dogliani/energybuild/blob/master/Imgs/SVLR_regressor_model.png)

### MLPR neural network 

![MLPR: scatter plot](https://github.com/matias-dogliani/energybuild/blob/master/Imgs/MLPR_regressor_model.png)

### Models' Perfomance 

![Model perfomance](https://github.com/matias-dogliani/energybuild/blob/master/Imgs/Model_perfomance.png)

## Predicting 

We used Tree Decision Regression model to predict the energy consumption up to 4 days in the future 
matching the maximum forecast data with free acces API. 

* Four days predictions
![4 days predictions](https://github.com/matias-dogliani/energybuild/blob/master/Imgs/Energy_consumption_pred_4days.png)

* One day prediction 
![1 day prediction]()
