# Forecasting order volumes for Glovo
The project is simplified to forecasting the number of orders for just one city. This involves two main steps:

* Exploratory Data Analysis (EDA) : Load the file data_BCN.csv, explore and visualize the data. Look for trends, cycles, seasonalities, and any outliers or deviations from established patterns.

* Modelling: Experiment with different models, validating each in a manner that imitates the real problem (i.e., every Sunday forecast all of the upcoming week). Be cautious of data leakage. Evaluate each model on Mean Squared Error (MSE) and Symmetric Mean Absolute Percentage Error (SMAPE) to determine which performs better.

# Step-by-step
1. Feature generation: Features are created that can be used in the EDA, like time, day, day_of_the_week, month, season.
2. Graphs and EDAs: Here we find out certain questions.
+ What time of the day and week has the most order.
<img align="centre" width="500" height="500" src="https://github.com/baksben/Predicting-orders-for-Glovo/blob/main/output.png">
We can see that there seems to be an accumulation of high orders at 21:00 everyday, with the highest day on friday folllowed by saturday. This is around the time people get off work, and might be too late to do some groceries, or cook and want to buy a takeaway.

+ Which month has the most order? which season?
<img align="centre" width="500" height="500" src="https://github.com/baksben/Predicting-orders-for-Glovo/blob/main/output_1.png">
We can clearly see that winter (december to january) has the most orders. People might be too cold and too lazy to go out.

3. Detect for outliers: In this process, we delve into the data to determine the existence of outliers and their potential implications. The presence of outliers doesn't necessarily imply inaccuracies or errors in the data. In our context, it could indicate days with unusually high sales, perhaps due to holidays, discounts, or other special events.
<img align="centre" width="500" height="300" src="https://github.com/baksben/Predicting-orders-for-Glovo/blob/main/output_2.png">
We can see that March, July and August most have either had a crazy amount of sales or a mistake in input.

4. Modelling: Before we do this we could take a further look into how the order changes over time.
<img align="centre" width="500" height="400" src="https://github.com/baksben/Predicting-orders-for-Glovo/blob/main/output_3.png">
Here we can clearly see the trend clearly, around 13:00 we have around 300 orders and at 21:00 we have 300 orders. This happens almost everyday.

+ Stationary check: A p-value below a threshold (such as 5% or 1%) suggests we reject the null hypothesis (stationary), otherwise a p-value above the threshold suggests we fail to reject the null hypothesis (non-stationary).<br>
If;
- p-value > 0.05: Fail to reject the null hypothesis (H0), the data has a unit root and is non-stationary.
- p-value <= 0.05: Reject the null hypothesis (H0), the data does not have a unit root and is stationary.

The result of the analysis shows the test statistic value of -10.4. The more negative this statistic, the more likely we are to reject the null hypothesis (we have a stationary dataset). The p-value also hints at that. 
In our analysis we used SARIMA model. We defined the SARIMA model to try and iterated over the SARIMA orders. After which we predict the next week's order, evaluate and sort our best model based on the best our results as shown below.  
<img align="centre" width="500" height="400" src="https://github.com/baksben/Predicting-orders-for-Glovo/blob/main/output_4.png">

Best Model: SARIMAX_(0, 0, 2)_(1, 0, 1, 24).
MSE: 2352.9623852561895.

Below is the result of our best model.

<img align="centre" width="500" height="400" src="https://github.com/baksben/Predicting-orders-for-Glovo/blob/main/output_5.png">
