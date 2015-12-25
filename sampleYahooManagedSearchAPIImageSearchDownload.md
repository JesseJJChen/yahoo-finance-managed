[Overview](MainPage.md)/[Documentation](Documentation.md)/[Code Examples](LibraryAppliance.md)/[YahooManaged.Search](sampleYahooManagedSearch.md)/

---


# ImageSearchDownload #
Download search results of image search

## VB.NET ##
```
    Public Sub Download()
        'Parameters'
        Dim searchText As String = "yahoo"

        Dim options As New YahooManaged.Search.API.ImageSearchOptions
        Dim bOptions As YahooManaged.Search.API.SearchOptions = options

        bOptions.Start = 0
        bOptions.Count = 10
        bOptions.Culture = New Culture(YahooManaged.Language.en, YahooManaged.Country.US)
        bOptions.HtmlTaggedText = False
        bOptions.StrictLanguage = False

        options.AllowAdultContent = True
        options.Coloration = YahooManaged.Search.ImageColoration.Color
        options.Format = YahooManaged.Search.ImageFileType.Png
        options.SearchType = YahooManaged.Search.TextSearchType.All

        'Download'
        Dim dl As New YahooManaged.Search.API.ImageSearchDownload
        dl.Options = options
        Dim resp As YahooManaged.Search.API.ImageSearchResponse = dl.Download(searchText)
        Dim bResp As YahooManaged.Search.API.SearchResponse = resp

        'Response/Result'
        If resp.Connection.State = YahooManaged.Base.ConnectionState.Success Then
            For Each res As YahooManaged.Search.SearchResult In bResp.Result
                Dim title As String = res.Title
                Dim description As String = res.Summary
                Dim url As Uri = res.Url
                Dim clickUrl As Uri = res.ClickUrl

            Next

            For Each res As YahooManaged.Search.ImageSearchResult In resp.Result
                Dim displayUrl As String = res.Copyright
                Dim fileFormat As YahooManaged.Search.ImageFileType = res.FileFormat
                Dim fileSize As Long = res.FileSize
                Dim height As Integer = res.Height
                Dim width As Integer = res.Width
                Dim pulisher As String = res.Publisher
                Dim refereUrl As Uri = res.RefererUrl
                Dim restrictions As String = res.Restrictions
                If res.Thumbnail IsNot Nothing Then
                    Dim thumbnail As YahooManaged.Search.Thumbnail = res.Thumbnail
                    Dim tUrl As Uri = thumbnail.Url
                    Dim tHeight As Integer = thumbnail.Height
                    Dim tWidth As Integer = thumbnail.Width

                End If

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

	YahooManaged.Search.API.ImageSearchOptions options = new YahooManaged.Search.API.ImageSearchOptions();
	YahooManaged.Search.API.SearchOptions bOptions = options;

	bOptions.Start = 0;
	bOptions.Count = 10;
	bOptions.Culture = new Culture(YahooManaged.Language.en, YahooManaged.Country.US);
	bOptions.HtmlTaggedText = false;
	bOptions.StrictLanguage = false;

	options.AllowAdultContent = true;
	options.Coloration = YahooManaged.Search.ImageColoration.Color;
	options.Format = YahooManaged.Search.ImageFileType.Png;
	options.SearchType = YahooManaged.Search.TextSearchType.All;

	//Download'
	YahooManaged.Search.API.ImageSearchDownload dl = new YahooManaged.Search.API.ImageSearchDownload();
	dl.Options = options;
	YahooManaged.Search.API.ImageSearchResponse resp = dl.Download(searchText);
	YahooManaged.Search.API.SearchResponse bResp = resp;

	//Response/Result'
	if (resp.Connection.State == YahooManaged.Base.ConnectionState.Success) {
		foreach (YahooManaged.Search.SearchResult res in bResp.Result) {
			string title = res.Title;
			string description = res.Summary;
			Uri url = res.Url;
			Uri clickUrl = res.ClickUrl;

		}

		foreach (YahooManaged.Search.ImageSearchResult res in resp.Result) {
			string displayUrl = res.Copyright;
			YahooManaged.Search.ImageFileType fileFormat = res.FileFormat;
			long fileSize = res.FileSize;
			int height = res.Height;
			int width = res.Width;
			string pulisher = res.Publisher;
			Uri refereUrl = res.RefererUrl;
			string restrictions = res.Restrictions;
			if (res.Thumbnail != null) {
				YahooManaged.Search.Thumbnail thumbnail = res.Thumbnail;
				Uri tUrl = thumbnail.Url;
				int tHeight = thumbnail.Height;
				int tWidth = thumbnail.Width;

			}

		}
	}
}
```