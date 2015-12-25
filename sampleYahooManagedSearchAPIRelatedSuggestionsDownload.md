[Overview](MainPage.md)/[Documentation](Documentation.md)/[Code Examples](LibraryAppliance.md)/[Search Namespace](sampleYahooManagedSearch.md)/[Diverse Namespace](sampleYahooManagedSearchDiverse.md)/

---


# RelatedSuggestionsDownload #
Download related suggestions for a keyword

## VB.NET ##
```
    Public Sub Download()
        Dim keyword As String = "yahoo"
        Dim server As YahooManaged.Server = YahooManaged.Server.USA

        Dim dl As New YahooManaged.Search.Diverse.API.RelatedSuggestionsDownload
        Dim resp As YahooManaged.Search.Diverse.API.SuggestionsResponse = dl.Download(keyword, server)
        If resp.Connection.State = Base.ConnectionState.Success Then
            For Each res As String In resp.Result
                Debug.WriteLine(res)
            Next
        End If
    End Sub
```

## C# ##
```
    public void Download()
    {
	string keyword = "yahoo";
	YahooManaged.Server server = YahooManaged.Server.USA;

	YahooManaged.Search.Diverse.API.RelatedSuggestionsDownload dl = new YahooManaged.Search.Diverse.API.RelatedSuggestionsDownload();
	YahooManaged.Search.Diverse.API.SuggestionsResponse resp = dl.Download(keyword, server);
	if (resp.Connection.State == Base.ConnectionState.Success) {
		foreach (string res in resp.Result) {
			Debug.WriteLine(res);
		}
	}
    }
```