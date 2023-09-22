The way the BigQuery magic function works is you basically enter your query and then it saves the output of the query to a Pandas DataFrame, which we call df. So this here is relatively long complicated query that will give us all of the features we need for our Machine Learning model. Our model will be really simple and that it only has two features as input. The first feature will be the previous day's closing price. Makes sense to me. The second feature, it will be something we call a three-day trend. A three-day trend variable for any given row looks at the previous four days of closing costs. If the closing price on a day is greater than the closing price on the previous day, and we assign a day plus one, otherwise we assign a day minus one. 

If the majority in the past three days consists of positive ones and the three-day trend is set to positive one, otherwise, is at negative one. So we get the data we need by making heavy use of this lag function in SQL. We go into more depth behind this lag function in the BigQuery Machine Learning Lab. For now, let's take this query as is. Let's go ahead and execute it.

The output of our query should be stored in this Pandas DataFrame that we call df. Let's go ahead and use the head command to see the first five rows of the DataFrame.

Next, let's try to get some intuition for this trend underscore three underscored day variable by embedding in the time series above. This series of commands looks at a subset of a full closing price time series from June to July of 2018. So the first plot command contains the closing price as a dotted line. The second plot command shows positive three-day trends as blue dots while the third plot command shows negative three-day trend as red dots. Let's go ahead and execute this cell.

So as expected, when the close values are visually trending downwards, we expect to see a lot of red dots. When the trend is upwards we expect to see more blue dots. In this next cell, we check the size for our dataset.

Next, we go ahead and fit the model on our training data. Since we don't have a lot of data, the training will be pretty fast. This our mix predictions on the testing data, we're going to use this output to gauge how good our model is.

To gauge how good our model is, we'll use two metrics; the Root Mean Squared Error and the variance score. The Root Mean Squared Error attempts to engage on average how far off your prediction is when the truth; the lower the better. The variance score is how correlated your prediction are to the truth; the closer to one the better. Now, getting good values for these metrics doesn't necessarily mean your model is useful. It all depends on the context. In this case, would you be okay with being off by around three points for your closing value prediction? As a sanity check, whenever you build a regression model, I'd like to plot the predictions against the truth like we do in this cell here.

<img width="1180" alt="Screenshot 2023-09-22 at 3 36 52 PM" src="https://github.com/Aditya0709-alt/ds-algo/assets/77115883/7ced448f-d90b-46e2-8e8a-eda3b231fe40">



## Best Fit Line

<img width="1240" alt="Screenshot 2023-09-22 at 3 36 14 PM" src="https://github.com/Aditya0709-alt/ds-algo/assets/77115883/c61767ee-2212-4bad-aaab-8ece08b2c940">
