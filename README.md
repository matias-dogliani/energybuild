# Energy Usage of an office building

**Big Data and Digital Modelling** - Priv.Doz. Dr. techn. Mag. MA MA Gerald Schweiger

Predicting the energy consumption of an office building

[Presentation Slides](https://github.com/matias-dogliani/energybuild/blob/master/Slides/Machine%20Learning%20-%20Energy%20Prediction.pptx.pdf)
[Paper](#)

### Authors :

* Calixto, Ian
* Doblas Florido, Maria Angeles
* Dogliani, Matias
* Nord, Nathan Thomas


## Model training and testing 

## Energy consumption prediction 

## Conclusion

In order to predict the future energy usage of a building using machine learning, a data set of historical energy usage was given. 
This data set had to be **preprocessed**  before it could be useful. The major steps of preprocessing included cleaning the data, analysing the data, and detecting and replacing outliers.
We then determined the inputs of the data for the machine learning model.
Our inputs were **weekdays, holidays, and temperature** and our target variables was **energy usage**. 


Historical weather data corresponding to the time of our data was retrieved via API to interface with our data. 
This weather data was also preprocessed. Next, the model was trained and tested with 4 different models. 


After analysis of each model it was determined that the **Tree Decision Regressor** produced the best results for our use case, yileding an R2 value of 0.89. 
The Tree Decision Regressor was used to forecast the next 4 days of energy usage. 


The 4 day forecast produced results that our group determined to be a reasonable prediction, validating the success of our model. 
