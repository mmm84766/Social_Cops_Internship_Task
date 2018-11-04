# Social-Cops-Internship-assignment
Challenge 1: Agriculture Commodities, Prices &amp; Seasons  Aim: Your team is working on building a variety of insight packs to measure key trends in the Agriculture sector in India. You are presented with a data set around Agriculture and your aim is to understand trends in APMC (Agricultural produce market committee)/mandi price &amp; quantity arrival data for different commodities in Maharashtra.

## 1) To test and filter Outliers
A common way of speeding up a machine learning algorithm is by using Principal Component Analysis (PCA). If your learning algorithm is too slow because the input dimension is too high, then using PCA to speed it up can be a reasonable choice. This is probably the most common application of PCA. Another common application of PCA is for data visualization, as it helps reduce the dimensions of the data by representing the information in many dimensions into one. PCA is effected by scale so you need to scale the features in your data before applying PCA. Use StandardScaler to help you standardize the dataset’s features onto unit scale (mean = 0 and variance = 1) which is a requirement for the optimal representation.
Anomaly detection is the problem of identifying data points that don't conform to expected (normal) behaviour. Unexpected data points are also known as outliers and exceptions etc. Anomaly detection has crucial significance in the wide variety of domains as it provides critical and actionable information. For example, an anomaly in MRI image scan could be an indication of the malignant tumour or anomalous reading from production plant sensor may indicate faulty component.
Simply, anomaly detection is the task of defining a boundary around normal data points so that they can be distinguishable from outliers. But several different factors make this notion of defining normality very challenging. E.g. normal behaviour usually evolve in certain domains and the notion that is considered normal in the present could change in future. Moreover, defining the normal region which separates outliers from normal data points is not straightforward in itself. This calls for using the K-Means clustering algorithm.

![After K-Means](https://github.com/saphal1998/Social-Cops-Internship-assignment/blob/master/images/After%20K-Means.png)
This picture segregates data according to clusters formed hence giving us the outliers

## 2) Understand price fluctuations accounting the seasonal effect
### a. Detect seasonality type (multiplicative or additive) for each cluster of APMC and commodities
A useful abstraction for selecting forecasting methods is to break a time series down into systematic and unsystematic components.
#### Systematic: Components of the time series that have consistency or recurrence and can be described and modeled.
#### Non-Systematic: Components of the time series that cannot be directly modeled.
A given time series is thought to consist of three systematic components including level, trend, seasonality, and one non-    systematic component called noise.
These components are defined as follows:
#### Level: The average value in the series.
#### Trend: The increasing or decreasing value in the series.
#### Seasonality: The repeating short-term cycle in the series.
#### Noise: The random variation in the series.        
Decomposition is primarily used for time series analysis, and as an analysis tool it can be used to inform forecasting models on your problem.It provides a structured way of thinking about a time series forecasting problem, both generally in terms of modeling complexity and specifically in terms of how to best capture each of these components in a given model. Each of these components are something you may need to think about and address during data preparation, model selection, and model tuning. You may address it explicitly in terms of modeling the trend and subtracting it from your data, or implicitly by providing enough history for an algorithm to model a trend if it may exist.You may or may not be able to cleanly or perfectly break down your specific time series as an additive or multiplicative model.
There are methods to automatically decompose a time series.
The statsmodels library provides an implementation of the naive, or classical, decomposition method in a function called seasonal_decompose(). It requires that you specify whether the model is additive or multiplicative. Both will produce a result and you must be careful to be critical when interpreting the result. A review of a plot of the time series and some summary statistics can often be a good start to get an idea of whether your time series problem looks additive or multiplicative. The seasonal_decompose() function returns a result object. The result object contains arrays to access four pieces of data from the decomposition.  
![Trends Using Functions](https://github.com/saphal1998/Social-Cops-Internship-assignment/blob/master/images/Trends%20using%20function.png)
We have plotted the trends of the data (where available) 
### b. De-seasonalise prices for each commodity and APMC according to the detected seasonality type
Seasonal Adjustment with Modeling
We can model the seasonal component directly, then subtract it from the observations.The seasonal component in a given time series is likely a polynomial over a generally fixed period. This can be approximated easily using a curve-fitting method.A dataset can be constructed with the time index of the polynomial as an input, or x-axis, and the observation as the output, or y-axis. Once fit, the model can then be used to calculate a seasonal component for any time index.
![Curve Fitting](https://github.com/saphal1998/Social-Cops-Internship-assignment/blob/master/images/Curve-fitting.png)
We have tried to fit a 4th degree polynomial to the curve here.
![Deseasonalised](https://github.com/saphal1998/Social-Cops-Internship-assignment/blob/master/images/Deseasonalised.png)
After deseasonalising, we get the following graph, notice the scale on the Y-Axis.

### 3)Compare prices in APMC/Mandi with MSP(Minimum Support Price)- raw and deseasonalised
We then just draw plots of the data, wherever nexessary, <br />
![Raw v/s MSP](https://github.com/saphal1998/Social-Cops-Internship-assignment/blob/master/images/Comparing%20raw%20mandi%20and%20MSP%20Prices.png)<br />
This compares the raw and MSP price of a commodity, across various APMC <br />

![Deseasonalised v/s MSP](https://github.com/saphal1998/Social-Cops-Internship-assignment/blob/master/images/Comparing%20Deseasonalised%20Mandi%20and%20MSP.png) <br />
This compares the deseasonalised and MSP price of a commodity, across various APMC


