# Module-11--Forecasting-Net-Prophet
Prophet Modeling

##dataframes availible in code to download in ipynb file##

**Forecasting Net Prophet**

**Step 1: Find Unusual Patterns in Hourly Google Search Traffic**
The data science manager asks if the Google search traffic for the company links to any financial events at the company. Or, does the search traffic data just present random noise? To answer this question, pick out any unusual patterns in the Google search data for the company, and connect them to the corporate financial events.

To do so, complete the following steps:

Read the search data into a DataFrame, and then slice the data to just the month of May 2020. (During this month, MercadoLibre released its quarterly financial results.) Use hvPlot to visualize the results. Do any unusual patterns exist?

Calculate the total search traffic for the month, and then compare the value to the monthly median across all months. Did the Google search traffic increase during the month that MercadoLibre released its financial results?

![bokeh_plot (3)](https://user-images.githubusercontent.com/117589787/218914629-17f3358f-2759-4270-8504-3b37bfd56c1c.png)


traffic_may_2020  

Search Trends    38181
dtype: int64

median_monthly_traffic

Search Trends    612.0
dtype: float64

**Answer the following question:**

Question: Did the Google search traffic increase during the month that MercadoLibre released its financial results?

Answer: Yes the google search traffic did increase during the month that MercadoLibre relesaed its financials

**Step 2: Mine the Search Traffic Data for Seasonality**

Marketing realizes that they can use the hourly search data, too. If they can track and predict interest in the company and its platform for any time of day, they can focus their marketing efforts around the times that have the most traffic. This will get a greater return on investment (ROI) from their marketing budget.

To that end, you want to mine the search traffic data for predictable seasonal patterns of interest in the company. To do so, complete the following steps:

Group the hourly search data to plot the average traffic by the day of the week (for example, Monday vs. Friday).

Using hvPlot, visualize this traffic as a heatmap, referencing the index.hour as the x-axis and the index.dayofweek as the y-axis. Does any day-of-week effect that you observe concentrate in just a few hours of that day?

Group the search data by the week of the year. Does the search traffic tend to increase during the winter holiday period (weeks 40 through 52)?

![bokeh_plot (4)](https://user-images.githubusercontent.com/117589787/218915016-0bb690f3-596e-427f-8074-7d37b8e6ef92.png)

![bokeh_plot (5)](https://user-images.githubusercontent.com/117589787/218915089-3313fdde-a433-4050-90ef-b15bc30b1fc0.png)

**Answer the following question:**

Question: Does any day-of-week effect that you observe concentrate in just a few hours of that day?

Answer: Yes we can see that in the first 4 days of the week there is the highest concentration of search trends and it happens within the first few hours of those days and within the last few hours of those days, we can see there is very little activity in hours 5-15 of the day.

![bokeh_plot (6)](https://user-images.githubusercontent.com/117589787/218915211-0955a0c3-8538-4a88-9bf1-d95141c3754c.png)

**Answer the following question:**

Question: Does the search traffic tend to increase during the winter holiday period (weeks 40 through 52)?

Answer: Yes we can seee that search traffic tends to inrease during the winter holiday period

**Step 3: Relate the Search Traffic to Stock Price Patterns**

You mention your work on the search traffic data during a meeting with people in the finance group at the company. They want to know if any relationship between the search data and the company stock price exists, and they ask if you can investigate.

To do so, complete the following steps:

Read in and plot the stock price data. Concatenate the stock price data to the search data in a single DataFrame.

Market events emerged during the year of 2020 that many companies found difficult. But, after the initial shock to global financial markets, new customers and revenue increased for e-commerce platforms. Slice the data to just the first half of 2020 (2020-01 to 2020-06 in the DataFrame), and then use hvPlot to plot the data. Do both time series indicate a common trend that’s consistent with this narrative?

Create a new column in the DataFrame named “Lagged Search Trends” that offsets, or shifts, the search traffic by one hour. Create two additional columns:

“Stock Volatility”, which holds an exponentially weighted four-hour rolling average of the company’s stock volatility

“Hourly Stock Return”, which holds the percent change of the company's stock price on an hourly basis

Review the time series correlation, and then answer the following question: Does a predictable relationship exist between the lagged search traffic and the stock volatility or between the lagged search traffic and the stock price returns?

![bokeh_plot (7)](https://user-images.githubusercontent.com/117589787/218915503-589e6f0a-5d63-42fa-9530-81770d6e6477.png)

![bokeh_plot (13)](https://user-images.githubusercontent.com/117589787/218915586-2b84c6e9-656f-4ffe-8eee-bd47bb2dbb04.png)

**Answer the following question:**

Question: Do both time series indicate a common trend that’s consistent with this narrative?

Answer: Yes we can see a weak relationship between the two data sets that as the search trends increase we can see an increase in the close price, but not a very close relationship

##dataframes availible in code to download in ipynb file##

![bokeh_plot (10)](https://user-images.githubusercontent.com/117589787/218916006-ea737514-0f9f-4864-b391-05dc2fea84e0.png)

{	Stock Volatility	Lagged Search Trends	Hourly Stock Return
Stock Volatility	1.000000	-0.118945	0.046723
Lagged Search Trends	-0.118945	1.000000	0.017929
Hourly Stock Return	0.046723	0.017929	1.000000}

**Answer the following question:**
Question: Does a predictable relationship exist between the lagged search traffic and the stock volatility or between the lagged search traffic and the stock price returns?

Answer: # no based on the correlation gives there is not a strong relationship between stock volatility or stock price returns and the lagged search traffic

**Step 4: Create a Time Series Model with Prophet**

Now, you need to produce a time series model that analyzes and forecasts patterns in the hourly search data. To do so, complete the following steps:

Set up the Google search data for a Prophet forecasting model.

After estimating the model, plot the forecast. How's the near-term forecast for the popularity of MercadoLibre?

Plot the individual time series components of the model to answer the following questions:

What time of day exhibits the greatest popularity?

Which day of the week gets the most search traffic?

What's the lowest point for search traffic in the calendar year?

![image](https://user-images.githubusercontent.com/117589787/218917436-55af826e-8917-49f1-b2b0-47c61190b7e4.png)

**Answer the following question:**

Question: How's the near-term forecast for the popularity of MercadoLibre?

Answer: The near term forecast shows that it will be increasing in popularity

![bokeh_plot (11)](https://user-images.githubusercontent.com/117589787/218917523-a61a745d-7de6-44cd-b65d-b6543bbc9867.png)

![image](https://user-images.githubusercontent.com/117589787/218917823-41ff81b7-f50a-41bb-b2ba-2adcfcd95168.png)

**Answer the following questions:**

Question: What time of day exhibits the greatest popularity?

Answer: We can ssee the greatest popularity at the beginning and end of the day

Question: Which day of week gets the most search traffic?

Answer: We see that Tuesday gets the most search traffic

Question: What's the lowest point for search traffic in the calendar year?

Answer: The lowest point for search traffic is in October





