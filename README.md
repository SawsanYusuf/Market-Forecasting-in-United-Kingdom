# Market Forecasting in the United Kingdom


In this project, we developed a model to forecast volatility on the London Stock Exchange. Firstly, we explored stock data for two companies using the AlphaVantage stock API. Next, we utilized the data to calculate volatility and establish a Garch model to predict it.

To begin with, we extracted data from the AlphaVantage API programmatically using an HTTP request. We used the request library and discovered that we get back a response containing a status code and things like JSON with the actual information up from there. We then transformed that JSON into a data frame. Finally, we compiled everything into a single "get daily" function where we can take input from the user - the ticker they want and the number of observations they need - and return a data frame.

Then, we began creating our data module, which is everything we needed to get stock data, store it in a database, and then retrieve it from that database. We started with our AlphaVantage API class and converted our "get daily" function into a method. Additionally, in the data module, we developed our SQL repository class, which had an "insert table" method for getting data into the database and a "read table" method for getting data out from the database.

When constructing all of these methods and classes, we employed test-driven development, where we used assert statements to determine whether our methods were functioning correctly.

Subsequently, we analyzed the closing price of our two stocks - TESCO and HSBC Holdings plc. We discovered that the closing prices differed significantly between the two. HSBC Holdings was much higher, while TESCO was significantly lower, making it impossible to compare. To overcome this, we created a new column called "returns," which represents the percent change of that stock every day. We observed that HSBC had smaller returns, whereas TESCO's returns were much broader, indicating a more volatile stock.

Volatility is another significant aspect of finance and a vital component of developing investment strategies. Therefore, we built the classes required to manipulate and store our stock data. We began by developing a wrangle data function, which assists us in retrieving stock data from our database and calculating the returns column. After that, we examined the returns for Ambushes Cement and on Energy to gain a better understanding of what volatility is. We concluded that volatility is the standard deviation of the returns of a stock. We also looked at volatility in a conditional sense - how it changes over time as it moves across time, or in an unconditional sense where we plot it out in a histogram, considering standard deviation.

Next, we constructed our Garch model to predict TESCO's volatility. Finally, we created a clean prediction function to format our model's predictions. We transformed our wide data frame into a dictionary that we can utilize in our application.
