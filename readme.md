# Project overview
Energy is used daily for phones, computers, washing machines, heaters and a vast array of appliances.
Our dependence on electricity makes it critical to accurately predict how much we will need to generate on any given day.
Hence, our project aims to correlate and model temperature's effect on energy demand.
We will begin by importing and cleaning our two datasets, before analysing the data integrity and creating visualisations to intuitively highlight the impact several variables have on Australia's net energy usage.
These visualisations aim to show not only energy and temperature but yearly trends, seasonal shifts and other potential anomalies.
After this we create a basic timeseries model, to evaluate precisely how well we're able to measure energy demand on a day-to-day basis.
This report will conclude with a summary of our results (including the significance of different independent and extraneous variables) and a series of suggestions on how our work can be improved going forwards.

To help achieve these results we will use a range of technical and statistical tools.
We heavily rely on Python and its associated libraries (largely Pandas for data cleaning and management, Numpy for numerical calculations, MatPlotLib for graphs and Scikit learn for machine learning modelling).

# Supplied data
Our weather data is collected from the Bureau of Meteorology's (BOM) Automatic Weather Stations and energy data from The Australian Energy Market Operator (AEMO).
The data comes in the form of a series of CSVs containing measurements every 30 minutes.
The weather data contains precipitation (mm), temperature (°C), relative humidity (%), wind speed (km/h), wind direction (° true), maximum wind gust speed (km/h), pressure (hPa) and whether manual/automatic measurements were taken.
It is quite common for there to be multiple features (columns) with nearly identical data (i.e. different forms of temperature or pressure).
Energy data provides total demand and an RRP (energy price).

The large portion of this data will be processed to eliminate any present trends, biases or inconsistencies. Yet, not all the provided data from BOM and AEMO are relevant (so many columns are removed).

# Project structure
This document provides a brief overview of this project and its achievements, however for more detail please look through the relevant notebooks:
1. [Data cleaning](src/Data.ipynb)
2. [Visualisation and statistics](src/Graphs%20and%20Stats.ipynb)
3. [Modelling](src/Modelling.ipynb)

To run the code, go through each notebook in order.

# Conclusions
## Ability to model data
From the graphs above we have seen that most states (apart from Tasmania) have largely predictable energy patterns throughout most of the year.
Our success with small decision trees (with information on temperature and seasons) show that there is a direct relationship between temperature, time (within a year) and energy demand.
However, attempts to model Australian energy usage through just temperature have been futile, suggesting that there are several other variables at play.
These likely include the increase in population per state, summer holidays, travel and more (INCLUDE MORE).

The graphs of the fit show that Tasmania (along with South Australia, but to a slightly lesser extent) was significantly harder to model than the other states (also shown in the cross-validation score of ~40%).
This could potentially be because there is less data for Tasmania than the other states.

## Recommendations
There are several improvements which could improve predictability.
The first would be to obtain data which describes large trends.
Although we were successfully able to separate yearly trends from seasonality, this is not quite as effective as being able (with data) to forecast these trends.
There are several features which would help, the first is population data.
The number of Australian's alive dictates how many people will be using power.
The second is technological advances which reduce or increase overall energy usage.
This would be difficult, and may not seem relevant, however over the years appliances like heaters, fridges and more have become far more efficient (meaning greater temperature may not result in as great an increase in energy as before).

Data cleaning for the temperature was particularly difficult, and so there are several improvements which can be made (both to the cleaning procedure and collection procedure).
The temperature data has large amounts of missing data, which limits the information which our model was capable of using.
A good portion of this would be largely irrelevant (as shown by the correlation table in the graphing section) and was easily overcome through using other columns of data, however, some of it would still likely be useful.
One particular example is completely missing quality estimates.
This would allow predicts of when measures were faulty and so not reliable (which may improve model performance).
With both the temperature and energy dataset being substantially large, a large number of CSV files is quite impractical.
Hence, a database or other efficient data structure would likely yield faster and less error-prone data importing.