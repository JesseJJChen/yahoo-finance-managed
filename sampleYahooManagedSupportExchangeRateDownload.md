[Overview](MainPage.md)/[Documentation](Documentation.md)/[Code Examples](LibraryAppliance.md)/[Finance Namespace](sampleYahooManagedFinance.md)/[Finance.Support Namespace](sampleYahooManagedSupport.md)/

---


# ExchangeRateDownload #
Downloading different exchange rate values

## VB.NET ##
```
    Public Sub Download()
        'Parameters'
        'Dim currencyIDs As IEnumerable(Of String) = New String() {"EURUSD=X", "EURGBP=X", "EURCHF=X"}'
        Dim currencyIDs() As YahooManaged.Finance.Support.YCurrencyID = New YahooManaged.Finance.Support.YCurrencyID() { _
                                                                        New YahooManaged.Finance.Support.YCurrencyID("EURUSD=X"), _
                                                                        New YahooManaged.Finance.Support.YCurrencyID(YahooManaged.Finance.Currency.EUR, YahooManaged.Finance.Currency.GBP), _
                                                                        New YahooManaged.Finance.Support.YCurrencyID(YahooManaged.Finance.Currency.EUR, YahooManaged.Finance.Currency.CHF)}
        'Download'
        Dim dl As New YahooManaged.Finance.Support.ExchangeRateDownload
        Dim resp As YahooManaged.Finance.Support.ExchangeRateResponse = dl.Download(currencyIDs)

        'Response/Result'
        If resp.Connection.State = YahooManaged.Base.ConnectionState.Success Then
            For Each exc As YahooManaged.Finance.Support.ExchangeRateData In resp.Result
                Dim baseData As YahooManaged.Finance.QuoteBaseData = exc
                Dim id As String = baseData.ID
                Dim relativeValueTo1 As Double = baseData.LastTradePriceOnly

                Dim currencyID As YahooManaged.Finance.Support.YCurrencyID = exc.CurrencyRelation

            Next
        End If

    End Sub
```

## C# ##
```
public void Download()
{
	//Parameters
	//Dim currencyIDs As IEnumerable(Of String) = New String() {"EURUSD=X", "EURGBP=X", "EURCHF=X"}
	YahooManaged.Finance.Support.YCurrencyID[] currencyIDs = new YahooManaged.Finance.Support.YCurrencyID[] {
		new YahooManaged.Finance.Support.YCurrencyID("EURUSD=X"),
		new YahooManaged.Finance.Support.YCurrencyID(YahooManaged.Finance.Currency.EUR, YahooManaged.Finance.Currency.GBP),
		new YahooManaged.Finance.Support.YCurrencyID(YahooManaged.Finance.Currency.EUR, YahooManaged.Finance.Currency.CHF)
	};
	//Download
	YahooManaged.Finance.Support.ExchangeRateDownload dl = new YahooManaged.Finance.Support.ExchangeRateDownload();
	YahooManaged.Finance.Support.ExchangeRateResponse resp = dl.Download(currencyIDs);

	//Response/Result
	if (resp.Connection.State == YahooManaged.Base.ConnectionState.Success) {
		foreach (YahooManaged.Finance.Support.ExchangeRateData exc in resp.Result) {
			YahooManaged.Finance.QuoteBaseData baseData = exc;
			string id = baseData.ID;
			double relativeValueTo1 = baseData.LastTradePriceOnly;

			YahooManaged.Finance.Support.YCurrencyID currencyID = exc.CurrencyRelation;

		}
	}

}
```