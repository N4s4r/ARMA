# ARMA
## Introduction
Final notebook for the ABData Challenge competition (2022) organized by AGBAR.

We developed a predictive model on water consumption, supported with open data variables and using the fact that consumption is conditioned by external factors.

The motivation behind this project begins with the approach to the water resource crisis. During these lasts years we experienced in Spain a period of drought, much more critical than in the last 5 years; the natural reserves are at 35% of their capacity and the desalination plants have had to start operating at maximum capacity.

With our model we want to help obtain a prediction of water consumption in the near future. Then use these predictions for a better management of the resource, thus saving water. This would mean a beneficial impact both environmentally and economically: not having to depend so much on desalination plants would reduce the economic and also energy costs that these entail.

## Data
Our model, apart from using the data provided by AGBAR, is supported with 4 different types of data: meteorological, socio-economic, demographic and "calendar".
### Meteorological data
The meteorological data comes from the Network of Automatic Meteorological Stations (XEMA), through the Catalan Open Data portal.

The data has been obtained from several stations, each providing different variables, among which we find temperature, humidity, precipitation... (among all the stations, there are more than 500 variables).

The names of these variables show the station code and what is being measured: WT_H_min is the minimum humidity that has been measured at the station with code WT. T indicates temperature and R indicates precipitation (rainfall).

### Socioeconomic data
Among the socio-economic data, we find the gross disposable family income (RBFD) and unemployment.

The RBFD comes from the HERMES program, from the Diputació de Barcelona. We have created the dataset manually, based on the information displayed on the web.

Unemployment also comes from the HERMES program, also created manually.

In addition to the external variables introduced into the model (Temperature, Precipitation, Demographics, etc.), we also considered the price of electricity. However, we observed a radical change in prices throughout the year in 2021, which is not representative of the variation of this factor in the last ten years. Therefore, even though we found a relationship with water consumption, we do not believe that these values were sufficiently representative or reliable to introduce them into the model for predicting future water consumption.
### Demographical data
We use the population of each municipality, provided by the National Statistics Institute (INE), the column that contains the data is called DEMO.

### Calendar data
List of public holidays for each town/city. Also includes weekends. Specifically, we have created 3 columns of binary data 0 (false) and 1 (true): esFinde (if it is Saturday or Sunday), esFestiu (if it is a holiday ie it is on the non-working calendar) and esPont (if it is a Monday or Friday holiday).

## Results
We achieved a global error of 4.89% for commercial consumption, 4.17% for domestic consumption, and 3.15% for industrial consumption. Initially we obtianed an error of 9% using only autoregression, by incorporating external data into our model, we have managed to reduce it to an error below 5%.

Our predictions are tailored, meaning that for each municipality, we have a specific model for predicting consumption in the population, also divided into whether the consumption is domestic, industrial, or commercial. We have chosen to do it this way because consumption patterns in a large city such as Barcelona or L'Hospitalet are very different from those in a small town like El Papiol. Therefore, if we had used a single model for all populations, the predictions would not have been as accurate.

It is worth mentioning that we have taken into account unexpected factors, such as a holiday falling on a Wednesday, a sudden increase in temperatures, long weekends, etc. Thus, our model is robust against these changes and others, allowing it to predict consumption while considering these factors.

We also believe that this project has the potential to be used for forecasting: predicting when consumption will occur today, tomorrow, etc., and using this information to predict consumption a week from now using previous predictions. In this way, long-term predictions could help implement measures to better manage the power used by desalination plants, thereby reducing energy and, most importantly, environmental impact.






