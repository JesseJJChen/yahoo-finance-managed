[Overview](MainPage.md)/[Documentation](Documentation.md)/[Code Examples](LibraryAppliance.md)/[Finance Namespace](sampleYahooManagedFinance.md)/[Screener Namespace](sampleYahooManagedScreener.md)/

---


# StockScreenerDownload #
Downloading Stock Screener criteria values (filtered)

## VB.NET ##
```
    Public Sub Download()
        Dim priceGainLoss As New YahooManaged.Finance.Screener.StockCriterias.PriceGainerLosersCriteria
        priceGainLoss.PercentValues = True
        priceGainLoss.ValueRelativeTo = Screener.StockTradingAbsoluteTimePoint.TodaysOpen
        priceGainLoss.GainOrLoss = Screener.StockPriceChangeDirection.Gain
        priceGainLoss.MinimumValue = 1.5

        Dim dl As New YahooManaged.Finance.Screener.API.StockScreenerDownload
        Dim resp As YahooManaged.Finance.Screener.API.StockScreenerResponse = dl.Download(New YahooManaged.Finance.Screener.StockCriterias.StockCriteriaDefinition() {priceGainLoss})

        For Each res As YahooManaged.Finance.Screener.StockScreenerData In resp.Result
            For Each qProp As YahooManaged.Finance.QuoteProperty In res.ProvidedQuoteProperties
                If res.Values(qProp) IsNot Nothing Then
                    Console.Write(qProp.ToString)
                    Console.Write(": ")
                    Console.WriteLine(res.Values(qProp).ToString)
                End If
            Next
            For Each sProp As YahooManaged.Finance.Screener.StockScreenerProperty In res.ProvidedScreenerProperties
                If res.AdditionalValues(sProp).HasValue Then
                    Console.Write(sProp.ToString)
                    Console.Write(": ")
                    Console.WriteLine(res.AdditionalValues(sProp).ToString)
                End If
            Next

            Console.WriteLine("")
            Console.WriteLine("")
        Next
    End Sub
```

## C# ##
```
public void Download()
{
	YahooManaged.Finance.Screener.StockCriterias.PriceGainerLosersCriteria priceGainLoss = new YahooManaged.Finance.Screener.StockCriterias.PriceGainerLosersCriteria();
	priceGainLoss.PercentValues = true;
	priceGainLoss.ValueRelativeTo = Screener.StockTradingAbsoluteTimePoint.TodaysOpen;
	priceGainLoss.GainOrLoss = Screener.StockPriceChangeDirection.Gain;
	priceGainLoss.MinimumValue = 1.5;

	YahooManaged.Finance.Screener.API.StockScreenerDownload dl = new YahooManaged.Finance.Screener.API.StockScreenerDownload();
	YahooManaged.Finance.Screener.API.StockScreenerResponse resp = dl.Download(new YahooManaged.Finance.Screener.StockCriterias.StockCriteriaDefinition[] { priceGainLoss });

	foreach (YahooManaged.Finance.Screener.StockScreenerData res in resp.Result) {
		foreach (YahooManaged.Finance.QuoteProperty qProp in res.ProvidedQuoteProperties) {
			if (res.Values(qProp) != null) {
				System.Console.Write(qProp.ToString);
				System.Console.Write(": ");
				System.Console.WriteLine(res.Values(qProp).ToString);
			}
		}
		foreach (YahooManaged.Finance.Screener.StockScreenerProperty sProp in res.ProvidedScreenerProperties) {
			if (res.AdditionalValues(sProp).HasValue) {
				System.Console.Write(sProp.ToString);
				System.Console.Write(": ");
				System.Console.WriteLine(res.AdditionalValues(sProp).ToString);
			}
		}

		System.Console.WriteLine("");
		System.Console.WriteLine("");
	}
}
```