[Overview](MainPage.md)/[Yahoo! Finance APIs](YahooFinanceAPIs.md)/[CSV API](CSVAPI.md)

---


# CSV Quotes Download #

How to download quotes data of stocks, indices or currency exchanges

`http://download.finance.yahoo.com/d/quotes.csv?s=`[%40%5EDJI,GOOG](interfaceIID#ID.md)`&f=`[nsl1op](enumQuoteProperty.md)`&e=.csv`

## Start ##

**`http://download.finance.yahoo.com/d/quotes.csv?s=`**

<br></br>

## IDs ##

Now, you have to set the [IDs](interfaceIID#ID.md) you want to receive. Every [stock](classStockID#ID_(Readonly).md), [index](classIndexID#ID_(Readonly).md) or [currency](classCurrencyRelation#ID_(Readonly).md) has their own ID. If you want to get values of more than one ID, separate them with ","


You also have to convert special characters into the correct [URL format](http://www.blooberry.com/indexdot/html/topics/urlencoding.htm)

`http://download.finance.yahoo.com/d/quotes.csv?s=`**`%40%5EDJI,GOOG`**

<br></br>


## Properties ##

For the different property tags look at the [property list](enumQuoteProperty.md). Use the tag `f`.

I will use here the tags of name(n), symbol(s), the latest value(l1), open(o) and the close value of the last trading day(p)

`http://download.finance.yahoo.com/d/quotes.csv?s=%40%5EDJI,GOOG&`**`f=nsl1op`**

<br></br>

## Static part ##

At the end add the following to the URL.

`http://download.finance.yahoo.com/d/quotes.csv?s=%40%5EDJI,GOOG&f=nsl1op`**`&e=.csv`**

<br></br>

## Download ##

[Download](http://download.finance.yahoo.com/d/quotes.csv?s=%40%5EDJI,GOOG&f=nsl1op&e=.csv)

Note: Yahoo! closed the multiple server support. You are able to call a server specific URL, but it will always redirect to USA server (download.finance.yahoo.com).