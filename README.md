# Time Series Forecasting and Monte Carlo Simulation on Green Produce Demand and Safety Stock and Re-order point Calculation
## Introduction
This is a project I worked on for my Operations Analytics module in MSc Business Analytics.
In this project, I was tasked to conduct time series forecasting and Monte Carlo simulation analysis on a fictitious dataset of monthly demand for green produce at Tesco with 324 observations. The time series is additive and has a seasonality of 12 months.

Time series plot: 

![image](https://github.com/QuyenThucNguyen/Excel-Demand-Time-Series-Forecasting-and-Monte-Carlo-Simulation-Analysis/assets/125051076/83007509-2fd6-4839-ae7d-e8fe625356dc)

## Approach & Findings:
#### 1. Time series exploration analysis: 
##### Descriptive statistics 

![image](https://github.com/QuyenThucNguyen/Excel-Demand-Time-Series-Forecasting-and-Monte-Carlo-Simulation-Analysis/assets/125051076/c14fb293-198c-4c70-a7d5-eee462f629c7)

##### Decompostion
My worksheet for decomposition (Refer to sheet A2. Decomposition):

![image](https://github.com/QuyenThucNguyen/Excel-Demand-Time-Series-Forecasting-and-Monte-Carlo-Simulation-Analysis/assets/125051076/32f3e51b-64f4-407e-b69f-730632de9d66)

Steps taken:

- Calculate moving average of suitable time periods.
- Calculate Centered Moving Average/Trend (CMA).
- Calculate Detrended Time series.
- Calculate Seasonality Index (Sheet A2.1)
- Calculate Seasonality Profile
- Adjust Seasonality Profile to calculate Seasonality Index, so Sum of SI should be zero.
- Calculate Noise in time series
- Reconstruct Time series with all three Trend, Seasonality and Trend.
- Plot charts of every component of time series.

De-trended time series:

![image](https://github.com/QuyenThucNguyen/Excel-Demand-Time-Series-Forecasting-and-Monte-Carlo-Simulation-Analysis/assets/125051076/b8770434-1e80-488e-9b1d-63aebc11f82c)

Figure shows the detrended time series with a non-linear trend that changes over time. Demand started low but steadily increased from 1992 to 2007, slowed down from 2007 to 2012, and increased significantly from 2014 onward. Simple linear models may not be good forecasters. To capture trend patterns, more advanced nonlinear models like polynomial regression or exponential smoothing may be needed.

Adjusted seasonality factor:

![image](https://github.com/QuyenThucNguyen/Excel-Demand-Time-Series-Forecasting-and-Monte-Carlo-Simulation-Analysis/assets/125051076/f02485c2-42d3-4ff5-a3af-da4064893cdb)

![image](https://github.com/QuyenThucNguyen/Excel-Demand-Time-Series-Forecasting-and-Monte-Carlo-Simulation-Analysis/assets/125051076/98a6b4ce-7162-47b4-a9d7-ebabf84fbe6f)

Noise and Irregularities: 

![image](https://github.com/QuyenThucNguyen/Excel-Demand-Time-Series-Forecasting-and-Monte-Carlo-Simulation-Analysis/assets/125051076/5db8037a-3455-46e2-bad5-2a0676e58030)

Time series reconstruction

![image](https://github.com/QuyenThucNguyen/Excel-Demand-Time-Series-Forecasting-and-Monte-Carlo-Simulation-Analysis/assets/125051076/967fe278-237d-44f3-8d3c-948767fec92d)


#### 2. Model building: 
The models that I was tasked in this coursework were 12-month Moving Average model (MA), Simple Exponential Smoothing (SES), and Linear Exponential Smoothing (LES) (Refer to sheet A3. Model Building).

The dataset was split into a training set (312 observations) and a testing set (12 observations to represent lead time demand for the next 12 months).

##### 12-month MA model:
I built a 12-month MA model with a Trend factor.
First, demand at time t is subtracted from demand at time t+1 to calculate the trend.
Then, the average trend at time t is calculated by averaging total trend values from the second to the t period.
Next, the 12-month MA value at time t is calculated by averaging the 12 previous periods, starting with the thirteenth.
Finally, the model's forecast value at time t+1 is the sum of the average trend and 12-month MA values at t.

Excel Worksheet:

![image](https://github.com/QuyenThucNguyen/Excel-Demand-Time-Series-Forecasting-and-Monte-Carlo-Simulation-Analysis/assets/125051076/ab738a19-726e-4103-9072-e613ea528193)


##### SES model:
Formula: 

![image](https://github.com/QuyenThucNguyen/Excel-Demand-Time-Series-Forecasting-and-Monte-Carlo-Simulation-Analysis/assets/125051076/8c220a42-1804-4ffe-ae10-8850aece48a8)

where F is the forecasted value, D is demand, and α is the smoothing constant with constraints between 0 and 1.
Smoothing parameter choosen is 0.2 (smoothing parameter constraints were 0.1 to 0.3).

Excel worksheet:

![image](https://github.com/QuyenThucNguyen/Excel-Demand-Time-Series-Forecasting-and-Monte-Carlo-Simulation-Analysis/assets/125051076/6b97833e-38da-4efe-bf7d-9713c9093132)

##### LES model:
LES model captures trend and level and is robust to outliers and sudden data changes. It is computationally intensive, requires more data to estimate parameters accurately, and does not consider seasonality.
I used Excel Solver to calculate the optimal α of 0.3 and β of 0.13567 to generate the minimal MAD. For the same reasons as the SES model, smoothing parameter constraints were 0.1 to 0.3

![image](https://github.com/QuyenThucNguyen/Excel-Demand-Time-Series-Forecasting-and-Monte-Carlo-Simulation-Analysis/assets/125051076/75b87124-f36a-4fdd-a022-959debc8f8ce)

#### Forecasted results:
(Refer to sheet A4. Model Forecasting)
##### 12-month MA model

![image](https://github.com/QuyenThucNguyen/Excel-Demand-Time-Series-Forecasting-and-Monte-Carlo-Simulation-Analysis/assets/125051076/46b6430c-2381-434f-b44e-9387b633591e)

##### SES model:

![image](https://github.com/QuyenThucNguyen/Excel-Demand-Time-Series-Forecasting-and-Monte-Carlo-Simulation-Analysis/assets/125051076/6e0183fc-b3da-4ef6-a201-9b0ff11261d8)

##### LES model:

![image](https://github.com/QuyenThucNguyen/Excel-Demand-Time-Series-Forecasting-and-Monte-Carlo-Simulation-Analysis/assets/125051076/33bb4e8a-2945-4bb8-bf1b-4e3acb8accca)


#### 3. Model evaluation & Comparative analysis: 

##### Summary of forecasted values:

![image](https://github.com/QuyenThucNguyen/Excel-Demand-Time-Series-Forecasting-and-Monte-Carlo-Simulation-Analysis/assets/125051076/85feb861-ae2d-4fb3-a2c8-f4d3daeb8629)

##### Performance evaluation and comparison:
The models' performance was evaluated and compared using Measures of accuracy such as ME, MAD, MAPE, MSE, RMSE. (Refer to sheet A4.1. Summary of Error Measures)

![image](https://github.com/QuyenThucNguyen/Excel-Demand-Time-Series-Forecasting-and-Monte-Carlo-Simulation-Analysis/assets/125051076/7dea3a49-983b-4655-b53f-82b8a5f3a92b)

##### Findings: 12-month MA is superior to the other 2 models.
SES and LES models are less accurate, especially in testing. 
SES errors increase over time, while the LES model underpredicts demand in the training set and has a large percentage deviation in the testing set.
The LES model may perform poorly because it ignores seasonality, a key data feature. 
The LES model only captures the trend and smooths data fluctuations with a parameter. 
Without seasonality, the model may not accurately predict demand for each month, resulting in poor out-of-sample performance. 

#### 4. Safety stock and Re-order point calculation:
(Refer to sheet A6. Safety Stock)

Formula used:

![image](https://github.com/QuyenThucNguyen/Excel-Demand-Time-Series-Forecasting-and-Monte-Carlo-Simulation-Analysis/assets/125051076/8c8b1d9b-f59d-4bd7-ac33-1089bd952f49)
Based on the forecasted results of the 12-month MA model, a scenario where a stock-out risk is 3% and a lead time of 12 months, and the assumption of a normal distribution of forecast errors.

The safety stock is then calculated as the product of out-of-sample RMSE of 12-month  MA model, the square root of the 12-month lead time, and z-score, resulting in a safety stock of  approximately 110,530 units. 

Therefore, the re-order point can be calculated as the sum of the expected lead time demand and the safety stock, which is 3,344,642 units. 

![image](https://github.com/QuyenThucNguyen/Excel-Demand-Time-Series-Forecasting-and-Monte-Carlo-Simulation-Analysis/assets/125051076/bc0d8129-daf7-40ee-9ba6-bf8d5095eda6)

#### 5. Monte Carlo Simulation:
The forecast values of the model with the best performance was used for safety stock calculation and for Monte Carlo simulation to estimate lead time demand and profit.

The simulation entails calculating Tesco's expected lead time demand for green produce, given the risks underlying the share of expected lead time demand or production. 

The predicted profitability of the business is also based on the projected selling price and variable cost of production per unit.

Probability, cut-off level and market shares for the simulation:

![image](https://github.com/QuyenThucNguyen/Excel-Demand-Time-Series-Forecasting-and-Monte-Carlo-Simulation-Analysis/assets/125051076/5b1def12-5a7b-4815-897c-272702d68cfd)

Simulation worksheet: 

![image](https://github.com/QuyenThucNguyen/Excel-Demand-Time-Series-Forecasting-and-Monte-Carlo-Simulation-Analysis/assets/125051076/a2f5120d-06b1-410e-9c0f-f17a987b80ae)

In summary, the Monte Carlo simulation results showed that the expected lead-time demand for Tesco’s green produce ranged approximately from 668,929 to 2,675,714 units, with an average of 1,939,892 units. 
The expected profit ranged from £2,341,249 to £9,364,997 with an average of £6,789,623. 
Additionally, the mean production cost calculated was £8,729,515. 
These results suggest that the company can expect to achieve a profitable level of profit with the given re-order point and demand uncertainties. 

## Conclusion: 

### Key takeaways
- Among 3 considered models, 12-month MA outperformed the others.
- Predicted 12-month lead-time demand is 3,234,111 units. 
- To optimise inventory management, the company should maintain 110,530 safety stock units and 3,344,642 re-order points. 
- Monte Carlo simulations estimated an average profit of £6,789,623 with a mean demand of 1,939,892 units.

### Future work:
Consider using Holt-Winters triple exponential smoothing or SARIMA model for demand forecasting due to its ability to capture trend, seasonality and level changes in the time series data. (I will expand my work on this and update).
