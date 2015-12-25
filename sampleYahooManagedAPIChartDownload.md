[Overview](MainPage.md)/[Documentation](Documentation.md)/[Code Examples](LibraryAppliance.md)/[Finance Namespace](sampleYahooManagedFinance.md)/[Finance.API Namespace](sampleYahooManagedAPI.md)/

---


# ChartDownload #
Downloading technical analysing charts

## VB.NET ##
```
    Public Sub Download()
        'Parameters'
        Dim id As String = "MSFT"
        Dim options As New YahooManaged.Finance.API.ChartDownloadOptions
        With options
            .Culture = New YahooManaged.Culture(YahooManaged.Language.fr, YahooManaged.Country.FR)

            .ImageSize = YahooManaged.Finance.ChartImageSize.Middle
            .Type = YahooManaged.Finance.ChartType.Line
            .TimeSpan = YahooManaged.Finance.ChartTimeSpan.c3M
            .Scale = YahooManaged.Finance.ChartScale.Logarithmic

            .MovingAverages.Add(YahooManaged.Finance.MovingAverageInterval.m10)
            .ExponentialMovingAverages.Add(YahooManaged.Finance.MovingAverageInterval.m10)
            .TechnicalIndicators.Add(YahooManaged.Finance.TechnicalIndicator.ROC)
            .ComparingIDs.Add("GOOG")
        End With

        'Download'
        Dim dl As New YahooManaged.Finance.API.ChartDownload
        dl.Options = options
        Dim resp As YahooManaged.Base.StreamResponse = dl.Download(id)

        'Response/Result'
        If resp.Connection.State = YahooManaged.Base.ConnectionState.Success Then
            Dim s As System.IO.MemoryStream = resp.Result

        End If

    End Sub

    Public Sub DownloadSimplified()
        'Parameters'
        Dim id As String = "MSFT"
        Dim options As New YahooManaged.Finance.API.ChartDownloadOptions
        With options
            .SimplifiedImage = True
            .Culture = New YahooManaged.Culture(YahooManaged.Language.fr, YahooManaged.Country.FR)
            .ImageWidth = 300
            .ImageHeight = 180
        End With

        'Download'
        Dim dl As New YahooManaged.Finance.API.ChartDownload
        dl.Options = options
        Dim resp As YahooManaged.Base.StreamResponse = dl.Download(id)

        'Response/Result'
        If resp.Connection.State = YahooManaged.Base.ConnectionState.Success Then
            Dim s As System.IO.MemoryStream = resp.Result

        End If
    End Sub
```

## C# ##
```
public void Download()
{
	//Parameters
	string id = "MSFT";
	YahooManaged.Finance.API.ChartDownloadOptions options = new YahooManaged.Finance.API.ChartDownloadOptions();
	options.Culture = new YahooManaged.Culture(YahooManaged.Language.fr, YahooManaged.Country.FR);

	options.ImageSize = YahooManaged.Finance.ChartImageSize.Middle;
	options.Type = YahooManaged.Finance.ChartType.Line;
	options.TimeSpan = YahooManaged.Finance.ChartTimeSpan.c3M;
	options.Scale = YahooManaged.Finance.ChartScale.Logarithmic;

	options.MovingAverages.Add(YahooManaged.Finance.MovingAverageInterval.m10);
	options.ExponentialMovingAverages.Add(YahooManaged.Finance.MovingAverageInterval.m10);
	options.TechnicalIndicators.Add(YahooManaged.Finance.TechnicalIndicator.ROC);
	options.ComparingIDs.Add("GOOG");

	//Download
	YahooManaged.Finance.API.ChartDownload dl = new YahooManaged.Finance.API.ChartDownload();
	dl.Options = options;
	YahooManaged.Base.StreamResponse resp = dl.Download(id);

	//Response/Result
	if (resp.Connection.State == YahooManaged.Base.ConnectionState.Success) {
		System.IO.MemoryStream s = resp.Result;

	}

}

public void DownloadSimplified()
{
	//Parameters
	string id = "MSFT";
	YahooManaged.Finance.API.ChartDownloadOptions options = new YahooManaged.Finance.API.ChartDownloadOptions();
        options.SimplifiedImage = true;
	options.Culture = new YahooManaged.Culture(YahooManaged.Language.fr, YahooManaged.Country.FR);
        options.ImageWidth = 300;
        options.ImageHeight = 180;

	//Download
	YahooManaged.Finance.API.ChartDownload dl = new YahooManaged.Finance.API.ChartDownload();
	dl.Options = options;
	YahooManaged.Base.StreamResponse resp = dl.Download(id);

	//Response/Result
	if (resp.Connection.State == YahooManaged.Base.ConnectionState.Success) {
		System.IO.MemoryStream s = resp.Result;

	}

}
```