[Overview](MainPage.md)/[Documentation](Documentation.md)/[Code Examples](LibraryAppliance.md)/[Search Namespace](sampleYahooManagedSearch.md)/[Diverse Namespace](sampleYahooManagedSearchDiverse.md)/

---


# SiteExplorerDownload #
Download inlinks of a specified website

## VB.NET ##
```
    Public Sub Download()
        Dim url As New Uri("http://www.yahoo.com")

        Dim dl As New YahooManaged.Search.Diverse.API.SiteExplorerDownload
        Dim resp As YahooManaged.Search.Diverse.API.SiteExplorerResponse = dl.DownloadInLinks(url)
        If resp.Connection.State = YahooManaged.Base.ConnectionState.Success Then
            For Each res As YahooManaged.Search.SearchResult In resp.Result
                Debug.WriteLine(res.Title)
                Debug.WriteLine(res.Url.ToString)
            Next
        End If
    End Sub
```

## C# ##
```
    public void Download()
    {
	Uri url = new Uri("http://www.yahoo.com");

	YahooManaged.Search.Diverse.API.SiteExplorerDownload dl = new YahooManaged.Search.Diverse.API.SiteExplorerDownload();
	YahooManaged.Search.Diverse.API.SiteExplorerResponse resp = dl.DownloadInLinks(url);
	if (resp.Connection.State == YahooManaged.Base.ConnectionState.Success) {
		foreach (YahooManaged.Search.SearchResult res in resp.Result) {
			System.Diagnostics.Debug.WriteLine(res.Title);
			System.Diagnostics.Debug.WriteLine(res.Url.ToString);
		}
	}
    }
```