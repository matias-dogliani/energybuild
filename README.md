# Energy Usage of an office building

**Big Data and Digital Modelling** - Priv.Doz. Dr. techn. Mag. MA MA Gerald Schweiger

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

For training and testing the model we use historical weather data related to our energy consumption data provided.
We've use the API provided by [AT-Wetter](http://at-wetter.tk/index.php?men=api)

This API doesn't need a Key or other authentication. It is located on the AT-Server in `http://at-wetter.tk/api/v1/.`
and the instructions to use it are in their [website](http://at-wetter.tk/index.php?men=api)

The data downloaded for the same datapoints of the energy consumptions:

![Temperature: Yearly](https://github.com/matias-dogliani/energybuild/blob/master/Imgs/Weather_year.png)

### Energy reading

This dataset was provided by the Professor.


![Energy usage: yearly](https://github.com/matias-dogliani/energybuild/blob/master/Imgs/Energy_usage_year.png)

### Forecast

For the final prediction of the energy consumption, we used the [OpenWeather - API](https://openweathermap.org/api)
with free access to download an hourly Forecast for 4 days


## Data pre processing


### Energy Reading

In this [jupyter notebook](https://github.com/matias-dogliani/energybuild/blob/master/PreProcess_EnergyConsumption.ipynb) is an step by step explanation of the pre processing

Pre-processing consisted of:

* Removing the string unit from the target variable

* Overview analysis of data with plots

* Find anomalies

* Replace the anomalies with NaN values

* Interpolate the NaN values

The distribution of our data:
![Energy usage: histogram](https://github.com/matias-dogliani/energybuild/blob/master/Imgs/Energy_usage_histogram.png)

#### Outliers and anomalies

The first step in determining the outliers was to determine the distribution of the data, particularly if it was Gaussian.

![Energy Usage: histogram gaussian](https://github.com/matias-dogliani/energybuild/blob/6162874ae86ef0e9ff237c859536721e82ba2ff8/Imgs/Energy_usage_histogram_gaussian.png)

As shown in the aboven histogram comparison to a normal distribution, our data was determined to have a non-normal distribution. Therefore, we could not use a standard deviation method to detect anamolies.

Rather, we used a **rule-based method**. We fixed these rules after a visual analisys of our data, as well as real world understanding of the data measurements.

We have defined outliers as:

* Negative Values
* Zero Values
* Illogical Values (too high
or too low)

We defined illogical values with upper and lower limits. The upper limit was set to 4 of the median and the lower limit to 0.3 of the median. Both limits, and the median are in the plot  

![Energy Usage: finding anomalies](https://github.com/matias-dogliani/energybuild/blob/master/Imgs/Energy_usage_year_annotated.png)

Once we've detected the outliers, we use the built-in function `interpolate()` of pandas to **replace** those values.


### Week days and holidays

In this [Jupyter Notebook](https://github.com/matias-dogliani/energybuild/blob/master/DataSet_Days.ipynb) there's a deeper explanation and the step by step code.

In order to identify the week days, first we had to give a numerical value from 0 to 6 for each day of the week (0 for Monday and 6 for Sunday).

We need to have the same difference between consecutive days so it is necessary to use a **cyclical function**.

* First, we normalized the week days (0-6) between 0 and 2π.

* After this, we used the sin and the cosine function in all our normalized values
  (we used sin and cosine so every day of the week would have a unique combination).
  We used these two values as input variables.

If we plot each combination of sin and cosine value, we observe that it is a cyclical function **with the same distance between consecutives points**
(the points represent the days of the week).

![WeekDays plot](https://github.com/matias-dogliani/energybuild/blob/master/Imgs/weekdays.png)


* To acquire the holidays data set we had to install and import the holidays package.


* After this, we assigned a **1 to the holidays and a 0 to the regular days**.
  We used this information (zeros and ones) as another imput.

### Weather

We did not implement pre-process on our data since we could not find, with visual analysis, any clear outlier. For a more detailed detection of outliers in further work, we can implement *gradient detection outlier*

We implemented a linear interpolation for the missing values of temperature data.
When we merged the Temperature data frame with the energy consumption data set, we realized that
some points of temperature were missing (the data wasn't hourly stamped in some ranges).

To have the same timestamps of the weather data and the energy reading we've used `pandas.merge()`
function.
Then, we replace the missing values with the `interpolate` function as we did in the energy consumption dataframe

## Model comparision

In this [Jupyter Notebook](https://github.com/matias-dogliani/energybuild/blob/master/Training_Testing_model.ipynb)
the models are trained and test. Lastly, we used the Tree Decision Regressor (the one with the best result )
to predict the energy consumption for 4 days in the future.

We tried 4 different models, all of them with default hyperparameters

### Linear Regression

![Linear Reg : scatter plot](https://github.com/matias-dogliani/energybuild/blob/master/Imgs/linear_regression_model.png)


### Tree decision regression

![Tree decision Reg : scatter plot](https://github.com/matias-dogliani/energybuild/blob/master/Imgs/tree_regressor_model.png)

### SVR regressor
 
![SVR regressor : scatter plot](https://github.com/matias-dogliani/energybuild/blob/master/Imgs/SVLR_regressor_model.png)

### MLPR neural network

![MLPR: scatter plot](https://github.com/matias-dogliani/energybuild/blob/master/Imgs/MLPR_regressor_model.png)

### Models' Perfomance

We choose the model with the best perfomance for our use case based on these perfmonace measurements: 

* $`R^2`$ : Coefficient of determination. Represents the proportion of the variance in the dependent variable 
that the independent variables (our inputs variables) explain collectively. It's a measure that indicates how well 
our model fit.  

* $`MAE`$ : Mean Absolute Error. Represents the **average**  of the **absolute difference**  between the actual and predicted values 

* $`RMS`$ : Root Mean Squared Error. Represents the standard deviation of residuals.  

[source](https://medium.com/analytics-vidhya/mae-mse-rmse-coefficient-of-determination-adjusted-r-squared-which-metric-is-better-cd0326a5697e)

![Model perfomance](https://github.com/matias-dogliani/energybuild/blob/master/Imgs/Model_perfomance.png)

## Prediction

[Jupyter Notebook](https://github.com/matias-dogliani/energybuild/blob/master/Training_Testing_model.ipynb)

We used Tree Decision Regression model to predict the energy consumption up to 4 days in the future,
matching the maximum forecast data with the free access API.

* Four day predictions
![4 days predictions](https://github.com/matias-dogliani/energybuild/blob/master/Imgs/Prediction_Energy_consumption_4days.png)

* One day prediction
![1 day prediction](https://github.com/matias-dogliani/energybuild/blob/master/Imgs/Prediction_EnergyConsumption_daily23_11.png)

## Conclusion

In order to predict the future energy usage of a building using machine learning, a data set of historical energy usage was given. 
This data set had to be **preprocessed**  before it could be useful. The major steps of preprocessing included cleaning the data, analysing the data, and detecting and replacing outliers.
We then determined the inputs of the data for the machine learning model.
Our inputs were **energy usage, weekdays, holidays, and weather.**


Historical weather data corresponding to the time of our data was retrieved via API to interface with our data. 
This weather data was also preprocessed. Next, the model was trained and tested with 4 different models. 


After analysis of each model it was determined that the **Tree Decision Regressor** produced the best results for our use case, yileding an R2 value of 0.89. 
The Tree Decision Regressor was used to forecast the next 4 days of energy usage. 


The 4 day forecast produced results that our group determined to be a reasonable prediction, validating the success of our model. 
