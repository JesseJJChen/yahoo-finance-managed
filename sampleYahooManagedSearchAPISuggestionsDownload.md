[Overview](MainPage.md)/[Documentation](Documentation.md)/[Code Examples](LibraryAppliance.md)/[YahooManaged.Search](sampleYahooManagedSearch.md)/

---


# SuggestionsDownload #
Download suggestions for related or spelling issue

## VB.NET ##
```
    Public Sub Download()
        'Parameters'
        Dim searchText As String = "yahoo"
        Dim searchServer As Server = Server.USA

        'Download'
        Dim dl As New YahooManaged.Search.Diverse.API.SuggestionsDownload
        Dim resp As YahooManaged.Search.Diverse.API.SuggestionsResponse = dl.DownloadRelated(searchText, searchServer)
   
        'Response/Result'
        If resp.Connection.State = YahooManaged.Base.ConnectionState.Success Then
            For Each res As String In resp.Result
                Dim suggestion As String = res
            Next
        End If
    End Sub
```

## C# ##
```
public void Download()
{
	//Parameters'
	string searchText = "yahoo";
	Server searchServer = Server.USA;

	//Download'
	YahooManaged.Search.Diverse.API.SuggestionsDownload dl = new YahooManaged.Search.Diverse.API.SuggestionsDownload();
	YahooManaged.Search.Diverse.API.SuggestionsResponse resp = dl.DownloadRelated(searchText, searchServer);

	//Response/Result'
	if (resp.Connection.State == YahooManaged.Base.ConnectionState.Success) {
		foreach (string res in resp.Result) {
			string suggestion = res;
		}
	}
}
```