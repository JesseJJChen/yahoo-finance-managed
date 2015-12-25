[Overview](MainPage.md)/[Yahoo! Finance APIs](YahooFinanceAPIs.md)

---


# Chart Download #

How to download technical analysing charts of a stock, index or currency exchange.

## Start ##

**`http://chart.finance.yahoo.com/z?`**

<br></br>

## ID ##

Now, you have to set the [IDs](interfaceIID#ID.md) you want to receive. Every [stock](classStockID#ID_(Readonly).md), [index](classIndexID#ID_(Readonly).md) or [currency](classCurrencyRelation#ID_(Readonly).md) has their own ID.

You also have to convert special characters into the correct [URL format](http://www.blooberry.com/indexdot/html/topics/urlencoding.htm)

Add to the end `s=` and the ID.

`http://chart.finance.yahoo.com/z?`**`s=GOOG`**

<br></br>

## Time span ##

After that you have to assign the size of the [investigated period](enumChartTimeSpan.md).

Add to the end `&t=` and the time span tag.

`http://chart.finance.yahoo.com/z?s=GOOG`**`&t=6m`**

<br></br>

## Type ##

Now, add to the end `&q=` and the [chart type](enumChartType.md) tag.

`http://chart.finance.yahoo.com/z?s=GOOG&t=6m`**`&q=l`**

<br></br>

## Scale ##

For defining the scaling type just add `&l=` and the [chart scale](enumChartScale.md) tag.

Here you only have to describe, if logarithmic scaling is **On** or **Off**.

`http://chart.finance.yahoo.com/z?s=GOOG&t=6m&q=l`**`&l=on`**

<br></br>

## Size ##

Add to the end `&z=` and the [chart size](enumChartImageSize.md) tag of middle or large.

`http://chart.finance.yahoo.com/z?s=GOOG&t=6m&q=l&l=on`**`&z=l`**

<br></br>

## Moving Average Indicator ##

Here you can declare the moving average intervals.

If you have more than one seperate them with "`,`".

Add to the end `&p=` and for each interval "`m`" and the [interval](enumMovingAverageInterval.md) tag.

`http://chart.finance.yahoo.com/z?s=GOOG&t=6m&q=l&l=on&z=l`**`&p=m50,m200`**

<br></br>

## Exponential Moving Average Indicator ##

Here you can declare the exponential moving average intervals. It's nearly the same indicator like moving average, but its values are calculated with the [standard deviation](http://mathworld.wolfram.com/StandardDeviation.html).

If you have more than one seperate them with "`,`".

If you **didn't declare** a moving average interval one step before, add to the end "`&p=`" and for each interval "`e`" and the [interval](enumMovingAverageInterval.md) tag.

`http://chart.finance.yahoo.com/z?s=GOOG&t=6m&q=l&l=on&z=l`**`&p=e50,e200`**

If you did, just add the comma seperated tags.

`http://chart.finance.yahoo.com/z?s=GOOG&t=6m&q=l&l=on&z=l&p=m50`**`,e200`**

<br></br>

## Technical Indicators 1 ##

Here you can declare the first part of technical indicators.

If you have more than one seperate them with "`,`".

It's the same rule like with exponential moving average.

This part is valid for the following indicators:

  * Bollinger\_Bands

  * Parabolic\_SAR

  * Splits

  * Volume

If you **didn't declare** a moving or exponential moving average interval one or two steps before, add to the end "`&p=`" and for each indicator the [indicator](enumTechnicalIndicator.md) tag.

`http://chart.finance.yahoo.com/z?s=GOOG&t=6m&q=l&l=on&z=l`**`&p=v,b`**

If you did, just add the comma seperated tags.

`http://chart.finance.yahoo.com/z?s=GOOG&t=6m&q=l&l=on&z=l&p=m50,e200`**`,v`**

<br></br>

## Technical Indicators 2 ##

Here you can declare the second part of technical indicators.

If you have more than one seperate them with "`,`".

This part is valid for the following indicators:

  * MACD

  * MFI

  * ROC

  * RSI

  * Slow\_Stoch

  * Fast\_Stoch

  * Vol\_MA

  * W\_R

Add to the end of the URL "`&a=`" and for each [indicator](enumTechnicalIndicator.md) the tag.

`http://chart.finance.yahoo.com/z?s=GOOG&t=6m&q=l&l=on&z=l&p=m50,e200,v`**`&a=p12,p`**

<br></br>


## Comparing IDs ##

Lastly you are able to declare the the IDs of different stocks or indices that will be compared with the base ID of this image.

If you compare the stocks or indices, the image will display the chart scaling in relative values in percent, not absolute in any currency unit.

Comparing currency exchanges is also possible.

If you have more than one seperate them with "`,`".

You also have to convert special characters into the correct [URL format](http://www.blooberry.com/indexdot/html/topics/urlencoding.htm)

Add to the end of the URL "`&c=`" and for each [stock](classStockID#ID_(Readonly).md), [index](classIndexID#ID.md) or currency the ID.

`http://chart.finance.yahoo.com/z?s=GOOG&t=6m&q=l&l=on&z=l&p=m50,e200,v&a=p12,p`**`&c=%5EDJI,EURUSD=X`**

<br></br>

## Culture ##

Add to the end `&region=` and the culture tag of a country of your choice.

`http://chart.finance.yahoo.com/z?s=GOOG&t=6m&q=l&l=on&z=l&p=m50,e200,v&a=p12,p&c=%5EDJI,EURUSD=X`**`&region=DE`**

Also add to the end of URL `&lang=` and a language/country of your choice.

`http://chart.finance.yahoo.com/z?s=GOOG&t=6m&q=l&l=on&z=l&p=m50,e200,v&a=p12,p&c=%5EDJI,EURUSD=X&region=DE`**`&lang=de-DE`**

<br></br>


## Download ##

[Download](http://chart.finance.yahoo.com/z?s=GOOG&t=6m&q=l&l=on&z=l&p=m50,e200,v&a=p12,p&c=%5EDJI,EURUSD=X&region=de&lang=de-DE)