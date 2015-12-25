[Overview](MainPage.md)/[Yahoo! Finance APIs](YahooFinanceAPIs.md)/[CSV API](CSVAPI.md)

---


# CSV Industries Download #

How to download all industry informations of one financial sector.

## Start ##

Start with the default base URL for market quotes download.

**`http://biz.yahoo.com/p/csv/`**

<br></br>

## Sector of Industries ##

Here you have to set the number of the [sector](enumSectors.md). It's the 1-indexed rank by name in the sector list.

`http://biz.yahoo.com/p/csv/`**`1`**

<br></br>

## Sort Property ##

You have different [quote properties](enumMarketQuoteProperties.md) you will download. You can't chose which of them you want to download or not, but you have to set the property the received list is sorted by.

`http://biz.yahoo.com/p/csv/1`**`coname`**

<br></br>


## Sort Direction ##

Now, you have to set the sort direction of the sorted property.

Up --> "u"

Down --> "d"

`http://biz.yahoo.com/p/csv/1coname`**`u`**

<br></br>

## Static part ##

At the end add the following to the URL.

`http://biz.yahoo.com/p/csv/1conameu`**`.csv`**

<br></br>

## Download ##

[Download](http://biz.yahoo.com/p/csv/1conameu.csv)