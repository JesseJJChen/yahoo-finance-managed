[Overview](MainPage.md)/[Documentation](Documentation.md)/[Code Examples](LibraryAppliance.md)/

---


# RSS.FeedDownload #
RSS feed download class

## VB.NET ##
```
    Public Sub Download()
        'Parameters'
        Dim urls As IEnumerable(Of String) = New String() {"http://finance.yahoo.com/rss/headline?s=yhoo", _
                                                           "http://finance.yahoo.com/rss/headline?s=goog"}

        'Download'
        Dim dl As New YahooManaged.RSS.FeedDownload
        Dim resp As YahooManaged.RSS.FeedResponse = dl.Download(urls)

        'Response/Result'
        If resp.Connection.State = YahooManaged.Base.ConnectionState.Success Then
            For Each feed As YahooManaged.RSS.Feed In resp.Result
                Dim id As String = feed.Title
                Dim description As String = feed.Description

                For Each feedItem As YahooManaged.RSS.FeedItem In feed.Items
                    Dim itemID As String = feedItem.Title
                    Dim itemDescription As String = feedItem.Description

                Next
            Next
        End If

    End Sub
```

## C# ##
```
public void Download()
{
	//Parameters
	IEnumerable<string> urls = new string[] {
		"http://finance.yahoo.com/rss/headline?s=yhoo",
		"http://finance.yahoo.com/rss/headline?s=goog"
	};

	//Download
	YahooManaged.RSS.FeedDownload dl = new YahooManaged.RSS.FeedDownload();
	YahooManaged.RSS.FeedResponse resp = dl.Download(urls);

	//Response/Result
	if (resp.Connection.State == YahooManaged.Base.ConnectionState.Success) {
		foreach (YahooManaged.RSS.Feed feed in resp.Result) {
			string id = feed.Title;
			string description = feed.Description;

			foreach (YahooManaged.RSS.FeedItem feedItem in feed.Items) {
				string itemID = feedItem.Title;
				string itemDescription = feedItem.Description;

			}
		}
	}

}
```