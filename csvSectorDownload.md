[Overview](MainPage.md)/[Yahoo! Finance APIs](YahooFinanceAPIs.md)/[CSV API](CSVAPI.md)

---


# CSV Sector Download #

How to download informations about all available financial sectors

## Start ##

Start with the default base URL for market quotes download.

**`http://biz.yahoo.com/p/csv/`**

<br></br>

## All Sectors ##

You're only able to download all sector informations.

`http://biz.yahoo.com/p/csv/`**`s_`**

<br></br>

## Sort Property ##

You have different [quote properties](enumMarketQuoteProperties.md) you will download. You can't chose which of them you want to download or not, but you have to set the property the received list is sorted by.

`http://biz.yahoo.com/p/csv/s_`**`coname`**

<br></br>


## Sort Direction ##

Now, you have to set the sort direction of the sorted property.

Up --> "u"

Down --> "d"

`http://biz.yahoo.com/p/csv/s_coname`**`u`**

<br></br>

## Static part ##

Add the following at the end of the URL.

`http://biz.yahoo.com/p/csv/s_conameu`**`.csv`**

<br></br>

## Download ##

[Download](http://biz.yahoo.com/p/csv/s_conameu.csv)