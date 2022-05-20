# Energy Usage of an office building

**Big Data and Digital Modelling** - Priv.Doz. Dr. techn. Mag. MA MA Gerald Schweiger

Predicting the energy consumption of an office building

[Presentation Slides](https://github.com/matias-dogliani/energybuild/blob/master/Slides/Machine%20Learning%20-%20Energy%20Prediction.pptx.pdf)
[Paper](https://github.com/matias-dogliani/energybuild/blob/master/Energy_consumption_EI.pdf)

### Authors :

* Calixto, Ian
* Doblas Florido, Maria Angeles
* Dogliani, Matias
* Nord, Nathan Thomas

## Model training and testing 

### Datasets 

* [Energy Consumption readings - raw](https://github.com/matias-dogliani/energybuild/blob/master/DataSets/Raw_Building_energy_DataSet.xlsx)

* [Historical Weather - raw](https://github.com/matias-dogliani/energybuild/blob/master/DataSets/Raw_Weather_DataSet.csv)

* [Forecast weather](https://github.com/matias-dogliani/energybuild/blob/master/DataSets/Forecast_WeatherData.csv)

* [Energy Consumption preprocessed + preprocessed weather data](https://github.com/matias-dogliani/energybuild/blob/master/DataSets/PreProcessed_EnergyConsumption_WeatherData.csv)

* [Machine learning features data set](#)

#### Energy consumption dataset used 

![Energy consumption Preprocessed Plot](https://github.com/matias-dogliani/energybuild/blob/master/Imgs/DF_without_anomalies.png) 


#### Historical weather dataset used 

![Historical Weather Plot](https://github.com/matias-dogliani/energybuild/blob/master/Imgs/Weather_year.png)


### Notebooks 

* [WeekDays feature dataset building](https://github.com/matias-dogliani/energybuild/blob/master/Notebooks/DataSet_Days.ipynb)

* [Historical and Forecast weather data set building](https://github.com/matias-dogliani/energybuild/blob/master/Notebooks/DataSet_Weather.ipynb)

* [Energy consumption pre processing](https://github.com/matias-dogliani/energybuild/blob/master/Notebooks/PreProcess_EnergyConsumption.ipynb)

* [Historical and Forecast weathe pre processing](https://github.com/matias-dogliani/energybuild/blob/master/Notebooks/PreProcess_WeatherData.ipynb)

* [Features data set building and ML testing](https://github.com/matias-dogliani/energybuild/blob/master/Notebooks/Training_Testing_model.ipynb)


## Energy consumption prediction 

### 4 days 

![4 days prediction](https://github.com/matias-dogliani/energybuild/blob/master/Imgs/Prediction_Energy_consumption_4days.png) 

### Hourly 

![hourly one day prediction](https://github.com/matias-dogliani/energybuild/blob/master/Imgs/Prediction_EnergyConsumption_daily23_11.png) 


## To short: 

In order to predict the future energy usage of a building using machine learning, a data set of historical energy usage was given. 
This data set had to be **preprocessed**  before it could be useful. The major steps of preprocessing included cleaning the data, analysing the data, and detecting and replacing outliers.
We then determined the inputs of the data for the machine learning model.
Our inputs were **weekdays, holidays, and temperature** and our target variables was **energy usage**. 

Historical weather data corresponding to the time of our data was retrieved via API to interface with our data. 
This weather data was also preprocessed. Next, the model was trained and tested with 4 different models. 

After analysis of each model it was determined that the **Tree Decision Regressor** produced the best results for our use case, yileding an R2 value of 0.89. 
The Tree Decision Regressor was used to forecast the next 4 days of energy usage. 


The 4 day forecast produced results that our group determined to be a reasonable prediction, validating the success of our model. 
