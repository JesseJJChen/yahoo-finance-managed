[Overview](MainPage.md)/[Documentation](Documentation.md)/[Code Examples](LibraryAppliance.md)/[Finance Namespace](sampleYahooManagedFinance.md)/[Finance.Support Namespace](sampleYahooManagedSupport.md)/

---


# YCurrencyID #

The class for managing exchange rate relations

## VB.NET ##
```
Dim id As New YahooManaged.Finance.Support.YCurrencyID(YahooManaged.Finance.Currency.EUR, YahooManaged.Finance.Currency.USD)
Debug.WriteLine(id.ID) 'EURUSD=X'
Debug.WriteLine(id.BaseName) 'Euro'
Debug.WriteLine(id.DepName) 'U.S. Dollar'
Debug.WriteLine(id.DisplayName) 'Euro to U.S. Dollar'

Dim iidInstance As YahooManaged.Finance.IID = id

Dim qDl As New YahooManaged.Finance.API.QuotesDownload
Dim properties() As YahooManaged.Finance.QuoteProperty = New YahooManaged.Finance.QuoteProperty() _
                                                             {YahooManaged.Finance.QuoteProperty.Name, _
                                                              YahooManaged.Finance.QuoteProperty.Symbol, _
                                                              YahooManaged.Finance.QuoteProperty.LastTradePriceOnly}
Dim server As YahooManaged.Server = YahooManaged.Server.YQL
Dim resp As YahooManaged.Finance.API.QuotesResponse = qDl.Download(id.ID, properties, server)
```

## C# ##
```
YahooManaged.Finance.Support.YCurrencyID id = new YahooManaged.Finance.Support.YCurrencyID(YahooManaged.Finance.Currency.EUR, YahooManaged.Finance.Currency.USD);
Debug.WriteLine(id.ID);
//EURUSD=X'
Debug.WriteLine(id.BaseName);
//Euro'
Debug.WriteLine(id.DepName);
//U.S. Dollar'
Debug.WriteLine(id.DisplayName);
//Euro to U.S. Dollar'

YahooManaged.Finance.IID iidInstance = id;

YahooManaged.Finance.API.QuotesDownload qDl = new YahooManaged.Finance.API.QuotesDownload();
YahooManaged.Finance.QuoteProperty[] properties = new YahooManaged.Finance.QuoteProperty[] {
	YahooManaged.Finance.QuoteProperty.Name,
	YahooManaged.Finance.QuoteProperty.Symbol,
	YahooManaged.Finance.QuoteProperty.LastTradePriceOnly
};
YahooManaged.Server server = YahooManaged.Server.YQL;
YahooManaged.Finance.API.QuotesResponse resp = qDl.Download(id.ID, properties, server);
```