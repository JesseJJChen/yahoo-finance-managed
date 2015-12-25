[Overview](MainPage.md)/[Documentation](Documentation.md)/[Code Examples](LibraryAppliance.md)/[Finance Namespace](sampleYahooManagedFinance.md)/[Finance.Support Namespace](sampleYahooManagedSupport.md)/

---


# ExchangeRateCalculator #
Download exchange rate in relation to a currency and calculate the values

## VB.NET ##
```
    Public Sub Download()
        'Parameters'
        Dim baseCurrency As YahooManaged.Finance.Currency = YahooManaged.Finance.Currency.EUR
        Dim dependendCurrencies() As YahooManaged.Finance.Currency = New YahooManaged.Finance.Currency() { _
                                                                            YahooManaged.Finance.Currency.USD, _
                                                                            YahooManaged.Finance.Currency.GBP, _
                                                                            YahooManaged.Finance.Currency.CHF}

        'Download'
        Dim calculator As New YahooManaged.Finance.Support.ExchangeRateCalculator
        Dim proxy As System.Net.IWebProxy = calculator.Proxy
        calculator.Update(baseCurrency, dependendCurrencies)

        'Response/Result'
        If calculator.ExchangeItems IsNot Nothing Then
            For Each exc As YahooManaged.Finance.Support.ExchangeRateData In calculator.ExchangeItems
                Dim baseData As YahooManaged.Finance.QuoteBaseData = exc
                Dim id As String = baseData.ID
                Dim relativeValueTo1 As Double = baseData.LastTradePriceOnly

                Dim currencyID As YahooManaged.Finance.Support.YCurrencyID = exc.CurrencyRelation

            Next
        End If

        Dim result1 As Double = calculator.ConvertCurrency(10, YahooManaged.Finance.Currency.USD, YahooManaged.Finance.Currency.GBP)

        Dim exc1 As YahooManaged.Finance.Support.ExchangeRateData = calculator.ExchangeItems(0)
        Dim exc2 As YahooManaged.Finance.Support.ExchangeRateData = calculator.ExchangeItems(1)
        Dim result2 As Double = YahooManaged.Finance.Support.ExchangeRateCalculator.ConvertCurrency(10, exc1, exc2)

        Dim table As System.Data.DataTable = YahooManaged.Finance.Support.ExchangeRateCalculator.CrossDataTable(calculator.ExchangeItems)

    End Sub
```

## C# ##
```
public void Download()
{
	//Parameters
	YahooManaged.Finance.Currency baseCurrency = YahooManaged.Finance.Currency.EUR;
	YahooManaged.Finance.Currency[] dependendCurrencies = new YahooManaged.Finance.Currency[] {
		YahooManaged.Finance.Currency.USD,
		YahooManaged.Finance.Currency.GBP,
		YahooManaged.Finance.Currency.CHF
	};

	//Download
	YahooManaged.Finance.Support.ExchangeRateCalculator calculator = new YahooManaged.Finance.Support.ExchangeRateCalculator();
	System.Net.IWebProxy proxy = calculator.Proxy;
	calculator.Update(baseCurrency, dependendCurrencies);

	//Response/Result
	if (calculator.ExchangeItems != null) {
		foreach (YahooManaged.Finance.Support.ExchangeRateData exc in calculator.ExchangeItems) {
			YahooManaged.Finance.QuoteBaseData baseData = exc;
			string id = baseData.ID;
			double relativeValueTo1 = baseData.LastTradePriceOnly;

			YahooManaged.Finance.Support.YCurrencyID currencyID = exc.CurrencyRelation;

		}
	}

	double result1 = calculator.ConvertCurrency(10, YahooManaged.Finance.Currency.USD, YahooManaged.Finance.Currency.GBP);

	YahooManaged.Finance.Support.ExchangeRateData exc1 = calculator.ExchangeItems(0);
	YahooManaged.Finance.Support.ExchangeRateData exc2 = calculator.ExchangeItems(1);
	double result2 = YahooManaged.Finance.Support.ExchangeRateCalculator.ConvertCurrency(10, exc1, exc2);

	System.Data.DataTable table = YahooManaged.Finance.Support.ExchangeRateCalculator.CrossDataTable(calculator.ExchangeItems);

}
```