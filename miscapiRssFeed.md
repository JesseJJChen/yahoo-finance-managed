[Overview](MainPage.md)/[Yahoo! Finance APIs](YahooFinanceAPIs.md)

---


# RSS News Feed #

## Start ##

**`http://feeds.finance.yahoo.com/rss/2.0/headline?s=`**

<br></br>

## ID ##

Now, you have to set the [IDs](interfaceIID#ID_(Readonly).md) you want to receive. Every [stock](classStockID#ID_(Readonly).md), [index](classIndexID#ID_(Readonly).md) or [currency](classCurrencyRelation#ID_(Readonly).md) has their own ID.

You also have to convert special characters into the correct [URL format](http://www.blooberry.com/indexdot/html/topics/urlencoding.htm)

`http://feeds.finance.yahoo.com/rss/2.0/headline?s=`**`%5EDJI`**

<br></br>

## Localization ##

Then you're able to localize the feed results with a language/region.

`http://feeds.finance.yahoo.com/rss/2.0/headline?s=%5EDJI`**`&region=DE&lang=de-DE`**

<br></br>

## Download ##

[Download](http://feeds.finance.yahoo.com/rss/2.0/headline?s=%5EDJI&region=DE&lang=de-DE)