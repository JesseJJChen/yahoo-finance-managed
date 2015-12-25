[Overview](MainPage.md)/[Documentation](Documentation.md)/[Code Examples](LibraryAppliance.md)/[Finance Namespace](sampleYahooManagedFinance.md)/[Finance.API Namespace](sampleYahooManagedAPI.md)/

---


# MarketQuotesDownload #
Download market quotes of sectors, industires and companies

## VB.NET ##
```
    Public Sub Download()
        'Parameters'
        Dim industryID As Integer = 112

        'Download'
        Dim dl As New YahooManaged.Finance.API.MarketQuotesDownload
        Dim resp As YahooManaged.Finance.API.MarketQuotesResponse = dl.DownloadAllSectorQuotes()

        'Response/Result'
        If resp.Connection.State = YahooManaged.Base.ConnectionState.Success Then
            For Each quote As YahooManaged.Finance.MarketQuoteData In resp.Result
                Dim name As String = quote.Name

            Next
        End If

    End Sub
```

## C# ##
```
public void Download()
{
	//Parameters
	int industryID = 112;

	//Download
	YahooManaged.Finance.API.MarketQuotesDownload dl = new YahooManaged.Finance.API.MarketQuotesDownload();
	YahooManaged.Finance.API.MarketQuotesResponse resp = dl.DownloadAllSectorQuotes();

	//Response/Result
	if (resp.Connection.State == YahooManaged.Base.ConnectionState.Success) {
		foreach (YahooManaged.Finance.MarketQuoteData quote in resp.Result) {
			string name = quote.Name;

		}
	}

}
```