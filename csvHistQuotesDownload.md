[Overview](MainPage.md)/[Yahoo! Finance APIs](YahooFinanceAPIs.md)/[CSV API](CSVAPI.md)

---


# CSV Historical Quotes Download #

`http://ichart.yahoo.com/table.csv?s=`[BAS.DE](interfaceIID#ID_(Readonly).md)[&a=0&b=1&c=2000](csvHistQuotesDownload#From_Date.md) [&d=0&e=31&f=2010](csvHistQuotesDownload#To_Date.md)`&g=`[w](enumHistQuotesInterval.md)`&ignore=.csv`

How to download historical quotes data of a stock or index

## Start ##

Start with the default base URL for historical quotes download.

**`http://ichart.yahoo.com/table.csv?s=`**

<br></br>

## ID ##

Now, you have to set the [ID](interfaceIID#ID.md) of the stock or index you want to receive. Every [stock](classStockID#ID_(Readonly).md) or [index](classIndexID#ID_(Readonly).md) has their own ID.

You also have to convert special characters into the correct [URL format](http://www.blooberry.com/indexdot/html/topics/urlencoding.htm)

You are **not** able to download historical quotes of several stocks or indices.

You are **not** able to download historical quotes of currency exchange rates.

`http://ichart.yahoo.com/table.csv?s=`**`GOOG`**

<br></br>

## From Date ##

In this example I will download the quotes from 15/3/2000 until 31/1/2010.

At first you have to add the number of the month minus 1.

`http://ichart.yahoo.com/table.csv?s=GOOG`**`&a=2`**

Then add the number of the day.

`http://ichart.yahoo.com/table.csv?s=GOOG&a=0`**`&b=15`**

At last add the year.

`http://ichart.yahoo.com/table.csv?s=GOOG&a=0&b=1`**`&c=2000`**

<br></br>

## To Date ##

Adding the "To Date" data is nearly the same.

Month minus 1.

`http://ichart.yahoo.com/table.csv?s=GOOG&a=0&b=1&c=2000`**`&d=0`**

Day.

`http://ichart.yahoo.com/table.csv?s=GOOG&a=0&b=1&c=2000&d=0`**`&e=31`**

And the Year.

`http://ichart.yahoo.com/table.csv?s=GOOG&a=0&b=1&c=2000&d=0&e=31`**`&f=2010`**

<br></br>

## Interval ##

Now you have to add the interval of the [trading periods](enumHistQuotesInterval.md).

`http://ichart.yahoo.com/table.csv?s=GOOG&a=0&b=1&c=2000&d=0&e=31&f=2010`**`&g=w`**

<br></br>

## Static part ##

At the end add the following to the URL.

`http://ichart.yahoo.com/table.csv?s=GOOG&a=0&b=1&c=2000&d=0&e=31&f=2010&g=w`**&`ignore=.csv`**

<br></br>

## Download ##

[Download](http://ichart.yahoo.com/table.csv?s=GOOG&a=0&b=1&c=2000&d=0&e=31&f=2010&g=w&ignore=.csv)