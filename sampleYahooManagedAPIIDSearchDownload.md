[Overview](MainPage.md)/[Documentation](Documentation.md)/[Code Examples](LibraryAppliance.md)/[Finance Namespace](sampleYahooManagedFinance.md)/[Finance.API Namespace](sampleYahooManagedAPI.md)/

---


# IDSearchDownload #
Downloading valid Yahoo IDs

## VB.NET ##
```
    Public Sub Download()
        'Parameters'
        Dim keyword As String = "dow jones"
        Dim server As YahooManaged.Finance.IDSearchServer = YahooManaged.Finance.IDSearchServer.DefaultUS

        'Download'
        Dim dl As New YahooManaged.Finance.API.IDSearchDownload
        dl.Server = server
        Dim resp As YahooManaged.Finance.API.IDSearchResponse = dl.Download(keyword)

        'Response/Result'
        If resp.Connection.State = YahooManaged.Base.ConnectionState.Success Then
            For Each res As YahooManaged.Finance.IDSearchResult In resp.Result
                Dim id As String = res.ID
                Dim name As String = res.Name
                Dim type As YahooManaged.Finance.FinancialSecurityType = res.Type
                Dim exchange As String = res.Exchange

            Next
        End If

    End Sub
```

## C# ##
```
public void Download()
{
	//Parameters
	string keyword = "dow jones";
	YahooManaged.Finance.IDSearchServer server = YahooManaged.Finance.IDSearchServer.DefaultUS;

	//Download
	YahooManaged.Finance.API.IDSearchDownload dl = new YahooManaged.Finance.API.IDSearchDownload();
	dl.Server = server;
	YahooManaged.Finance.API.IDSearchResponse resp = dl.Download(keyword);

	//Response/Result
	if (resp.Connection.State == YahooManaged.Base.ConnectionState.Success) {
		foreach (YahooManaged.Finance.IDSearchResult res in resp.Result) {
			string id = res.ID;
			string name = res.Name;
			YahooManaged.Finance.FinancialSecurityType type = res.Type;
			string exchange = res.Exchange;

		}
	}

}
```