[Overview](MainPage.md)/[Documentation](Documentation.md)/[Code Examples](LibraryAppliance.md)/[Finance Namespace](sampleYahooManagedFinance.md)/[Finance.Support Namespace](sampleYahooManagedSupport.md)/

---


# YID #
Using YID for managing valid Yahoo! IDs

## VB.NET ##
```
    Public Sub Test()
        Dim dl As New YahooManaged.Finance.API.IDSearchDownload
        Dim resp As YahooManaged.Finance.API.IDSearchResponse = dl.Download("bas.de")

        If resp.Connection.State = YahooManaged.Base.ConnectionState.Success AndAlso resp.Result.Length > 0 Then
            Dim searchResult As YahooManaged.Finance.IDSearchResult = resp.Result(0)

            Dim id As New YahooManaged.Finance.Support.YID(searchResult)

            Dim iid As YahooManaged.Finance.IID = id

            Dim name As String = id.Name
            Dim idString As String = id.ID
            Dim baseID As String = id.BaseID
            Dim suffix As String = id.Suffix
            Dim type As YahooManaged.Finance.FinancialSecurityType = id.Type

            Dim stockExchange As YahooManaged.Finance.Support.StockExchange = id.StockExchange
            If stockExchange IsNot Nothing Then
                Dim excIdString As String = id.StockExchange.ID
                Dim excName As String = id.StockExchange.Name
                Dim excSuffix As String = id.StockExchange.Suffix
                Dim country As YahooManaged.Country = id.StockExchange.Country
                Dim currency As YahooManaged.Finance.Currency = id.StockExchange.Currency
                Dim isActiveNow As Boolean = id.StockExchange.IsActiveLocal(Date.Now)

            End If

        End If

    End Sub
```

## C# ##
```
public void Test()
{
	YahooManaged.Finance.API.IDSearchDownload dl = new YahooManaged.Finance.API.IDSearchDownload();
	YahooManaged.Finance.API.IDSearchResponse resp = dl.Download("bas.de");

	if (resp.Connection.State == YahooManaged.Base.ConnectionState.Success && resp.Result.Length > 0) {
		YahooManaged.Finance.IDSearchResult searchResult = resp.Result[0];

		YahooManaged.Finance.Support.YID id = new YahooManaged.Finance.Support.YID(searchResult);

		YahooManaged.Finance.IID iid = id;

		string name = id.Name;
		string idString = id.ID;
		string baseID = id.BaseID;
		string suffix = id.Suffix;
		YahooManaged.Finance.FinancialSecurityType type = id.Type;

		YahooManaged.Finance.Support.StockExchange stockExchange = id.StockExchange;
		if (stockExchange != null) {
			string excIdString = id.StockExchange.ID;
			string excName = id.StockExchange.Name;
			string excSuffix = id.StockExchange.Suffix;
			YahooManaged.Country country = id.StockExchange.Country;
			YahooManaged.Finance.Currency currency = id.StockExchange.Currency;
			bool isActiveNow = id.StockExchange.IsActiveLocal(System.DateTime.Now);

		}

	}

}
```