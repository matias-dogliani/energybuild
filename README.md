# Energy Usage of an office building

Predicting the energy consumption of an office building

#Group : 

* Calixto, Ian 
* Doblas Florido, Maria Angeles
* Dogliani, Matias 
* Nord, Nathan Thomas 

## Data Acquisition 

### Historical Weather Data 

Website, API explanation 

### Energy reading 

### Forecast

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







