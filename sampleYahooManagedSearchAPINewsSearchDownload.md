[Overview](MainPage.md)/[Documentation](Documentation.md)/[Code Examples](LibraryAppliance.md)/[YahooManaged.Search](sampleYahooManagedSearch.md)/

---


# NewsSearchDownload #
Download search results of news search

## VB.NET ##
```
    Public Sub Download()
        'Parameters'
        Dim searchText As String = "yahoo"

        Dim options As New YahooManaged.Search.API.NewsSearchOptions
        Dim bOptions As YahooManaged.Search.API.SearchOptions = options

        bOptions.Start = 0
        bOptions.Count = 10
        bOptions.Culture = New Culture(YahooManaged.Language.en, YahooManaged.Country.US)
        bOptions.HtmlTaggedText = False
        bOptions.StrictLanguage = False

        options.LatestDate = Date.Now
        options.OrderByRelevance = True
        options.TimeSpan = New TimeSpan(7, 0, 0, 0)
       
        'Download'
        Dim dl As New YahooManaged.Search.API.NewsSearchDownload
        dl.Options = options
        Dim resp As YahooManaged.Search.API.NewsSearchResponse = dl.Download(searchText)
        Dim bResp As YahooManaged.Search.API.SearchResponse = resp

        'Response/Result'
        If resp.Connection.State = YahooManaged.Base.ConnectionState.Success Then
            For Each res As YahooManaged.Search.SearchResult In bResp.Result
                Dim title As String = res.Title
                Dim description As String = res.Summary
                Dim url As Uri = res.Url
                Dim clickUrl As Uri = res.ClickUrl

            Next

            For Each res As YahooManaged.Search.NewsSearchResult In resp.Result
                Dim displayUrl As String = res.Language
                Dim linkDate As Date = res.LinkDate
                Dim source As String = res.Source
                Dim sourceUrl As Uri = res.SourceUrl

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

	YahooManaged.Search.API.NewsSearchOptions options = new YahooManaged.Search.API.NewsSearchOptions();
	YahooManaged.Search.API.SearchOptions bOptions = options;

	bOptions.Start = 0;
	bOptions.Count = 10;
	bOptions.Culture = new Culture(YahooManaged.Language.en, YahooManaged.Country.US);
	bOptions.HtmlTaggedText = false;
	bOptions.StrictLanguage = false;

	options.LatestDate = System.DateTime.Now;
	options.OrderByRelevance = true;
	options.TimeSpan = new TimeSpan(7, 0, 0, 0);

	//Download'
	YahooManaged.Search.API.NewsSearchDownload dl = new YahooManaged.Search.API.NewsSearchDownload();
	dl.Options = options;
	YahooManaged.Search.API.NewsSearchResponse resp = dl.Download(searchText);
	YahooManaged.Search.API.SearchResponse bResp = resp;

	//Response/Result'
	if (resp.Connection.State == YahooManaged.Base.ConnectionState.Success) {
		foreach (YahooManaged.Search.SearchResult res in bResp.Result) {
			string title = res.Title;
			string description = res.Summary;
			Uri url = res.Url;
			Uri clickUrl = res.ClickUrl;

		}

		foreach (YahooManaged.Search.NewsSearchResult res in resp.Result) {
			string displayUrl = res.Language;
			System.DateTime linkDate = res.LinkDate;
			string source = res.Source;
			Uri sourceUrl = res.SourceUrl;

		}
	}
}
```