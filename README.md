# Forecasting order volumes for Glovo
The project is simplified to forecasting the number of orders for just one city. This involves two main steps:

* Exploratory Data Analysis (EDA) : Load the file data_BCN.csv, explore and visualize the data. Look for trends, cycles, seasonalities, and any outliers or deviations from established patterns.

* Modelling: Experiment with different models, validating each in a manner that imitates the real problem (i.e., every Sunday forecast all of the upcoming week). Be cautious of data leakage. Evaluate each model on Mean Squared Error (MSE) and Symmetric Mean Absolute Percentage Error (SMAPE) to determine which performs better.

# Step-by-step
* Feature generation: Features are created that can be used in the EDA, like time, day, day_of_the_week, month, season.
* Graphs and EDAs: Here we find out certain questions.
  - What time of the day and week has the most order.
  
<img align="centre" width="500" height="500" src="https://github.com/baksben/Predicting-orders-for-Glovo/blob/main/output.png">
We can see that there seems to be an accumulation of high orders at 21:00 everyday, with the highest day on friday folllowed by saturday. This is around the time people get off work, and might be too late to do some groceries, or cook and want to buy a takeaway.

  - Which month has the most order? which season?
<img align="centre" width="500" height="500" src="https://github.com/baksben/Predicting-orders-for-Glovo/blob/main/output_1.png">
We can clearly see that winter (december to january) has the most orders. People might be too cold and too lazy to go out. 
