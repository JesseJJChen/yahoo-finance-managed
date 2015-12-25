[Overview](MainPage.md)/[Documentation](Documentation.md)/[Code Examples](LibraryAppliance.md)/[Search Namespace](sampleYahooManagedSearch.md)/[BOSS Namespace](sampleYahooManagedSearchBOSS.md)/

---


# WebSearchDownload #
Download search results of web search

## VB.NET ##
```
    Public Sub Download()
        'You need to register for Yahoo! BOSS to get an OAuth Consumer Key and Secret'
        Dim consumerKey As String = "..."
        Dim consumerSecret As String = "..."

        Dim dl As New YahooManaged.Search.BOSS.API.SearchDownload
        dl.UniversalOptions.HttpsUsed = False
        dl.UniversalOptions.ConsumerKey = consumerKey

        dl.UniversalOptions.ConsumerSecret = New System.Security.SecureString
        For Each c In consumerSecret
            dl.UniversalOptions.ConsumerSecret.AppendChar(c)
        Next
        dl.UniversalOptions.ConsumerSecret.MakeReadOnly()


        Dim webSearch As New YahooManaged.Search.BOSS.API.WebSearchOptions()
        webSearch.Start = 0
        webSearch.Count = 50

        webSearch.QueryText = "yahoo"

        webSearch.Culture = New YahooManaged.Culture(YahooManaged.Language.de, YahooManaged.Country.DE)
        webSearch.LimitedWeb = True
        webSearch.LanguageInfo = True
        webSearch.SearchMonkey = True
        webSearch.AllowAdultContent = True

        'webSearch.AllowedFileGroups = New YahooManaged.Search.BOSS.FileTypeGroup() {YahooManaged.Search.BOSS.FileTypeGroup.GetNonHtml}'
        'or'
        'webSearch.AllowedFileTypes = New WebFileType() {WebFileType.MsWord, WebFileType.Pdf, WebFileType.Ppt, WebFileType.Text, WebFileType.Xl}'

        webSearch.RestrictedSites.Add(New Uri("http://yahoo.com"))
        webSearch.HtmlTaggedText = False
        webSearch.LongAbstract = True
        webSearch.RestrictedTitle = "(news)OR(finance)"
        webSearch.SearchMonkey = True
        webSearch.LanguageInfo = True

        Dim resp As YahooManaged.Search.BOSS.API.SearchResponse = dl.Download(webSearch)

        If resp.Result.Length = 1 Then
            If resp.Result(0).Type = YahooManaged.Search.BOSS.BossResultType.Web Then
                Dim webContainer As YahooManaged.Search.BOSS.WebSearchResultContainer = CType(resp.Result(0), YahooManaged.Search.BOSS.WebSearchResultContainer)
                Dim start As Integer = webContainer.Start
                Dim count As Integer = webContainer.Count
                Dim total As Long = webContainer.TotalResults

                For Each res As YahooManaged.Search.BOSS.WebSearchResult In webContainer.Results
                    Dim baseResult As YahooManaged.Search.SearchResult = res

                    Dim title As String = baseResult.Title
                    Dim description As String = baseResult.Abstract
                    Dim url As Uri = baseResult.Url
                    Dim clickUrl As Uri = baseResult.ClickUrl

                    Dim displayUrl As String = res.DisplayUrl
                    Dim crawlingDate As Date = res.CrawlingDate
                    Dim language As YahooManaged.Language = res.Language
                    Dim searchMonkeyMicroformatFeed As String = res.SMFeed
                    If res.SMFeed <> String.Empty Then
                        Debug.WriteLine(res.SMFeed)
                    End If
                Next
            End If
        End If

    End Sub
```

## C# ##
```
        public void Download()
        {
            string consumerKey = "...";
            string consumerSecret = "...";

            YahooManaged.Search.BOSS.API.SearchDownload dl = new YahooManaged.Search.BOSS.API.SearchDownload();
            dl.UniversalOptions.HttpsUsed = false;
            dl.UniversalOptions.ConsumerKey = consumerKey;

            dl.UniversalOptions.ConsumerSecret = new System.Security.SecureString();
            foreach (char c_loopVariable in consumerSecret)
            {
                dl.UniversalOptions.ConsumerSecret.AppendChar(c_loopVariable);
            }
            dl.UniversalOptions.ConsumerSecret.MakeReadOnly();


            YahooManaged.Search.BOSS.API.WebSearchOptions webSearch = new YahooManaged.Search.BOSS.API.WebSearchOptions();
            webSearch.Start = 0;
            webSearch.Count = 50;

            webSearch.QueryText = "yahoo";

            webSearch.Culture = new YahooManaged.Culture(YahooManaged.Language.de, YahooManaged.Country.DE);
            webSearch.LimitedWeb = true;
            webSearch.LanguageInfo = true;
            webSearch.SearchMonkey = true;
            webSearch.AllowAdultContent = true;

            //webSearch.AllowedFileGroups = New YahooManaged.Search.BOSS.FileTypeGroup() {YahooManaged.Search.BOSS.FileTypeGroup.GetNonHtml}
            //or 
            //webSearch.AllowedFileTypes = New WebFileType() {WebFileType.MsWord, WebFileType.Pdf, WebFileType.Ppt, WebFileType.Text, WebFileType.Xl}

            webSearch.RestrictedSites.Add(new Uri("http://yahoo.com"));
            webSearch.HtmlTaggedText = false;
            webSearch.LongAbstract = true;
            webSearch.RestrictedTitle = "(news)OR(finance)";
            webSearch.SearchMonkey = true;
            webSearch.LanguageInfo = true;

            YahooManaged.Search.BOSS.API.SearchResponse resp = dl.Download(webSearch);

            if (resp.Result.Length == 1)
            {
                if (resp.Result[0].Type == YahooManaged.Search.BOSS.BossResultType.Web)
                {
                    YahooManaged.Search.BOSS.WebSearchResultContainer webContainer = (YahooManaged.Search.BOSS.WebSearchResultContainer)resp.Result[0];
                    int start = webContainer.Start;
                    int count = webContainer.Count;
                    long total = webContainer.TotalResults;

                    foreach (YahooManaged.Search.BOSS.WebSearchResult res in webContainer.Results)
                    {
                        YahooManaged.Search.SearchResult baseResult = res;

                        string title = baseResult.Title;
                        string description = baseResult.Abstract;
                        Uri url = baseResult.Url;
                        Uri clickUrl = baseResult.ClickUrl;

                        string displayUrl = res.DisplayUrl;
                        System.DateTime crawlingDate = res.CrawlingDate;
                        YahooManaged.Language language = res.Language;
                        string searchMonkeyMicroformatFeed = res.SMFeed;
                        if (res.SMFeed != string.Empty)
                        {
                            Debug.WriteLine(res.SMFeed);
                        }
                    }
                }
            }

        }
```