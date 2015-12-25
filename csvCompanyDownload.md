[Overview](MainPage.md)/[Yahoo! Finance APIs](YahooFinanceAPIs.md)/[CSV API](CSVAPI.md)

---


# CSV Company Download #

How to download informations of all company in one industry.

## Start ##

Start with the default base URL for market quotes download.

**`http://biz.yahoo.com/p/csv/`**

<br></br>

## Industy of companies ##

Here you have to set the ID of the industry the received companies are part of.

`http://biz.yahoo.com/p/csv/`**`112`**

<br></br>

## Sort Property ##

You have different [quote properties](enumMarketQuoteProperties.md) you will download. You can't chose which of them you want to download or not, but you have to set the property the received list is sorted by.

`http://biz.yahoo.com/p/csv/112`**`coname`**

<br></br>


## Sort Direction ##

Now, you have to set the sort direction of the sorted property.

Up --> "u"

Down --> "d"

`http://biz.yahoo.com/p/csv/112coname`**`u`**

<br></br>

## Static part ##

At the end add the following to the URL.

`http://biz.yahoo.com/p/csv/112conameu`**`.csv`**

<br></br>

## Download ##

[Download](http://biz.yahoo.com/p/csv/112conameu.csv)