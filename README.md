# A Tale Of Two (The Yen Vs US Dollar)
![image](https://user-images.githubusercontent.com/80294571/130246876-09f679b8-c0e9-41d1-9c36-1e3a9a48e909.png)


This project utilizes Time Series analysis, along with a Linear Regression model to forecast the price of the Japanese Yen vs. the US Dollar. ARMA, ARIMA, and GARCH forecasting models included, also using the decompisition of the Hodrick-Prescott filter. The In-Sample and Out-of-Sample performance metrics used to evaluate Linear Regression model.
The financial departments of large companies often deal with foreign currency transactions while doing international business. As a result, they are always looking for anything that can help them better understand the future direction and risk of various currencies. Hedge funds, too, are keenly interested in anything that will give them a consistent edge in predicting currency movements. 

# Time Series Forecasting:
The Following has been utilized in analysing historical data for the Yen:
1) Hodrick-Prescott Filter
2) ARMA Model
3) ARIMA Model
4) GARCH

#### Steps:
The dataset contained the following data related to the Yen from 1990-2019:
![image](https://user-images.githubusercontent.com/80294571/130248857-42af45c3-c0ef-4bff-977e-0caa85346664.png)

###### Decompisiton Using Hodrick-Prescott Filter:
1.  Apply the Hodrick-Prescott Filter by decomposing the *"Settle"* price into two separate series
2.  Create a dataframe of just the settle price, and add columns for *"Noise" and "Trend"* series
3.  Plot the Settle Price vs. the Trend Price for 2015 to the present

![image](https://user-images.githubusercontent.com/80294571/130249721-4f17bea1-1c8d-432d-af9a-b2cafb4c01bf.png)

#### ARMA Model:
1. Create a series using *"Settle"* price percentage returns, drop any nan's, and then create model
Below are the results of the ARMA model

![image](https://user-images.githubusercontent.com/80294571/130251115-912de563-cb65-480b-92dc-80a5c38cd241.png)

In the above ARMA model, the autoregressive term has a p-value (.42) that is greater than the significance level of 0.05. 

##### To return a plot forecast, use the following code, results listed below code:

*pd.DataFrame(results.forecast(steps=5)[0]).plot(title="5 Day Returns Forecast")*

![image](https://user-images.githubusercontent.com/80294571/130251669-30c21335-8ab6-45e7-9e8b-f07c524985f6.png)

#### ARIMA Model:

![image](https://user-images.githubusercontent.com/80294571/130252489-68bf2489-8248-47e4-8a18-63fb7fbd9141.png)

In the above ARIMA, the autoregressive term has a p-value (.65) that is greater than the significance level of 0.05. With both models showing a p-value higher than 0.05, we can conclude that the coefficient for the autoregressive term is **NOT** statistically significant, and should **NOT** be kept in the model.

#### GARCH Volitality Model:

![image](https://user-images.githubusercontent.com/80294571/130253326-92e6ce3e-d183-424a-a156-fc905658565a.png)


# Files:
1) Time-Series Notebook
2) Linear Regression Notebook
3) Yen Data CSV File

# Linear Regression Forecasting:
1) Data Preparation *(Creating Returns and Lagged Returns and splitting the data into training and testing data)*
2) Fitting a Linear Regression Model.
3) Making predictions using the testing data.
4) Out-of-sample performance.
5) In-sample performance.

### Linear Regression Model:
1. Load Yen futures return data, create a lagged return column using the .shift() function
2. The following dataset was produced
3. Assembled actual y data *(Y_test)* with predicted y data into two columns in a dataframe


![image](https://user-images.githubusercontent.com/80294571/130254123-0ab53017-64b4-45b2-9811-324484b97e06.png)

After splitting into Training and Testing data, I ran the Linear Regression model
Assembled actual y data *(Y_test)* with predicted y data into two columns in a dataframe


### Steps Taken:
1) Decomposition using a Hodrick-Prescott Filter *(Decompose the Settle price into trend and noise)*.
2) Forecasting Returns using an ARMA Model.
3) Forecasting the Settle Price using an ARIMA Model.
4) Forecasting Volatility with GARCH.

## Linear Regression Forecasting:
![image](https://user-images.githubusercontent.com/80294571/127751009-6bc924c5-dd76-4420-b5cc-cd17c1010a6c.png)



## Conclusion:
When partaking in an analysis, I try to find three questions to conclude the findings. This project consisted of the use of *Time Series Analysis*,  with that my first question was Based on my _Time Series Analysis_, ***Would I buy the Yen now?*** For me to conclude my findings, I would first need to ask myself, ***Is the risk of the Yen expected to increase or decrease?***  To come to my conclusion I could therefore use the evaluation based on the model. My final question would be ***Would I feel comfortable using this model for trading?*** 

With this model, *the out-of-sample* data performed slightly better than the *in-sample* data. The out-of-sample had a **Root Mean Squared Error(RMSE)** of ***0.415***, while the in-sample data has a **Root Mean Squared Error(RMSE)** of ***0.596***. With that said, my answer is yes! I would buy the Yen, knowing that the future rate would increase. 

