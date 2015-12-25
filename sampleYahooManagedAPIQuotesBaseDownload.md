[Overview](MainPage.md)/[Documentation](Documentation.md)/[Code Examples](LibraryAppliance.md)/[Finance Namespace](sampleYahooManagedFinance.md)/[Finance.API Namespace](sampleYahooManagedAPI.md)/

---


# QuotesBaseDownload #
Downloading basic quotes of valid Yahoo! IDs

## VB.NET ##
```
    Public Sub Download()
        'Parameters'
        Dim ids() As String = New String() {"MSFT", "GOOG", "YHOO", "BAS.DE", "ALV.DE", "@^DJI"}

        'Download'
        Dim dl As New YahooManaged.Finance.API.QuotesBaseDownload
        Dim resp As YahooManaged.Finance.API.QuotesBaseResponse = dl.Download(ids)

        'Response/Result'
        If resp.Connection.State = YahooManaged.Base.ConnectionState.Success Then
            For Each qd As YahooManaged.Finance.QuoteBaseData In resp.Result
                Dim id As String = qd.ID
                Dim lastPrice As Double = qd.LastTradePriceOnly
                Dim change As Double = qd.Change
                Dim changePerc As Double = qd.ChangeInPercent

            Next
        End If

    End Sub
```

## C# ##
```
public void Download()
{
	//Parameters
	string[] ids = new string[] {
		"MSFT",
		"GOOG",
		"YHOO",
		"BAS.DE",
		"ALV.DE",
		"@^DJI"
	};

	//Download
	YahooManaged.Finance.API.QuotesBaseDownload dl = new YahooManaged.Finance.API.QuotesBaseDownload();
	YahooManaged.Finance.API.QuotesBaseResponse resp = dl.Download(ids);

	//Response/Result
	if (resp.Connection.State == YahooManaged.Base.ConnectionState.Success) {
		foreach (YahooManaged.Finance.QuoteBaseData qd in resp.Result) {
			string id = qd.ID;
			double lastPrice = qd.LastTradePriceOnly;
			double change = qd.Change;
			double changePerc = qd.ChangeInPercent;

		}
	}

}
```