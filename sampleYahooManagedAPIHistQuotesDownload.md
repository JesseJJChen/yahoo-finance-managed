[Overview](MainPage.md)/[Documentation](Documentation.md)/[Code Examples](LibraryAppliance.md)/[Finance Namespace](sampleYahooManagedFinance.md)/[Finance.API Namespace](sampleYahooManagedAPI.md)/

---


# HistQuotesDownload #
Downlading historical quotes

## VB.NET ##
```
    Public Sub Download()
        'Parameters'
        Dim ids As IEnumerable(Of String) = New String() {"MSFT", "GOOG", "YHOO"}
        Dim fromDate As Date = #1/1/2005#
        Dim toDate As Date = Date.Today
        Dim interval As YahooManaged.Finance.HistQuotesInterval = YahooManaged.Finance.HistQuotesInterval.Monthly

        'Download'
        Dim dl As New YahooManaged.Finance.API.HistQuotesDownload
        Dim resp As YahooManaged.Finance.API.HistQuotesResponse = dl.Download(ids, fromDate, toDate, interval)

        'Response/Result'
        If resp.Connection.State = YahooManaged.Base.ConnectionState.Success Then
            For Each qd As YahooManaged.Finance.HistQuotesDataChain In resp.Result
                Dim id As String = qd.ID
                Dim first As YahooManaged.Finance.HistQuoteData = qd(0)
                Dim last As YahooManaged.Finance.HistQuoteData = qd(qd.Count - 1)

            Next
        End If

    End Sub
```

## C# ##
```
public void Download()
{
	//Parameters
	IEnumerable<string> ids = new string[] {
		"MSFT",
		"GOOG",
		"YHOO"
	};
	System.DateTime fromDate = 1/1/2005 12:00:00 AM;
	System.DateTime toDate = System.DateTime.Today;
	YahooManaged.Finance.HistQuotesInterval interval = YahooManaged.Finance.HistQuotesInterval.Monthly;

	//Download
	YahooManaged.Finance.API.HistQuotesDownload dl = new YahooManaged.Finance.API.HistQuotesDownload();
	YahooManaged.Finance.API.HistQuotesResponse resp = dl.Download(ids, fromDate, toDate, interval);

	//Response/Result
	if (resp.Connection.State == YahooManaged.Base.ConnectionState.Success) {
		foreach (YahooManaged.Finance.HistQuotesDataChain qd in resp.Result) {
			string id = qd.ID;
			YahooManaged.Finance.HistQuoteData first = qd[0];
			YahooManaged.Finance.HistQuoteData last = qd[qd.Count - 1];

		}
	}

}
```