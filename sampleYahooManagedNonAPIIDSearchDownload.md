[Overview](MainPage.md)/[Documentation](Documentation.md)/[Code Examples](LibraryAppliance.md)/[Finance Namespace](sampleYahooManagedFinance.md)/[Finance.NonAPI Namespace](sampleYahooManagedNonAPI.md)/

---


# IDSearchDownload #
Search for valid Yahoo IDs

## VB.NET ##
```
    Public Sub DownloadAsync()
        'Parameters'
        Dim keyword As String = "dow jones"

        Dim options As New YahooManaged.Finance.NonAPI.IDSearchOptions
        With options
            .Start = 0
            .Count = 100
            .Type = YahooManaged.Finance.FinancialSecurityType.Any
            .RankedBy = YahooManaged.Finance.FinancialProperty.Name
            .RankingDirection = ComponentModel.ListSortDirection.Ascending
            .Markets = YahooManaged.Finance.FinancialMarket.AllMarkets
            .ISINIncluded = False
        End With

        'Download'
        Dim dl As New YahooManaged.Finance.NonAPI.IDSearchDownload
        dl.Options = options
        AddHandler dl.AsyncDownloadChanged, AddressOf Me.AsyncDownload_Changed
        AddHandler dl.AsyncDownloadCompleted, AddressOf Me.AsyncDownload_Completed
        dl.DownloadAsync(keyword)

    End Sub

    Private Sub AsyncDownload_Changed(ByVal sender As YahooManaged.Base.Download, ByVal e As YahooManaged.Finance.NonAPI.IDSearchDownloadChangedEventArgs)
        'Response/Result'
        If e.Response.Connection.State = YahooManaged.Base.ConnectionState.Success Then
            For Each res As YahooManaged.Finance.IDSearchResult In e.Response.Result
                Dim id As String = res.ID

            Next
        End If
    End Sub

    Private Sub AsyncDownload_Completed(ByVal sender As YahooManaged.Base.Download, ByVal e As YahooManaged.Finance.NonAPI.IDSearchDownloadCompletedEventArgs)
        'Response/Result'
        If e.Response.Connection.State = YahooManaged.Base.ConnectionState.Success Then
            For Each res As YahooManaged.Finance.IDSearchResult In e.Response.Result
                Dim id As String = res.ID

            Next
        End If
    End Sub
```

## C# ##
```
public void DownloadAsync()
{
	//Parameters
	string keyword = "dow jones";

	YahooManaged.Finance.NonAPI.IDSearchOptions options = new YahooManaged.Finance.NonAPI.IDSearchOptions();
	var _with1 = options;
	_with1.Start = 0;
	_with1.Count = 100;
	_with1.Type = YahooManaged.Finance.FinancialSecurityType.Any;
	_with1.RankedBy = YahooManaged.Finance.FinancialProperty.Name;
	_with1.RankingDirection = System.ComponentModel.ListSortDirection.Ascending;
	_with1.Markets = YahooManaged.Finance.FinancialMarket.AllMarkets;
	_with1.ISINIncluded = false;

	//Download
	YahooManaged.Finance.NonAPI.IDSearchDownload dl = new YahooManaged.Finance.NonAPI.IDSearchDownload();
	dl.Options = options;
	dl.AsyncDownloadChanged += this.AsyncDownload_Changed;
	dl.AsyncDownloadCompleted += this.AsyncDownload_Completed;
	dl.DownloadAsync(keyword);

}

private void AsyncDownload_Changed(YahooManaged.Base.Download sender, YahooManaged.Finance.NonAPI.IDSearchDownloadChangedEventArgs e)
{
	//Response/Result
	if (e.Response.Connection.State == YahooManaged.Base.ConnectionState.Success) {
		foreach (YahooManaged.Finance.IDSearchResult res in e.Response.Result) {
			string id = res.ID;

		}
	}
}

private void AsyncDownload_Completed(YahooManaged.Base.Download sender, YahooManaged.Finance.NonAPI.IDSearchDownloadCompletedEventArgs e)
{
	//Response/Result
	if (e.Response.Connection.State == YahooManaged.Base.ConnectionState.Success) {
		foreach (YahooManaged.Finance.IDSearchResult res in e.Response.Result) {
			string id = res.ID;

		}
	}
}
```