
---


# WeatherFeedDownload #
Download weather forecast feeds

## VB.NET ##
```
    Public Sub Download()
        Dim countOptions As New YahooManaged.ResultCountOptions
        countOptions.Start = 0
        countOptions.Count = 10
        Dim searchString As String = "berlin"
        Dim metricValues As Boolean = True

        Dim dl As New YahooManaged.Weather.API.WeatherFeedDownload
        Dim resp As YahooManaged.Weather.API.WeatherFeedResponse = dl.Download(searchString, metricValues, countOptions)

        If resp.Connection.State = Base.ConnectionState.Success Then
            For Each res As YahooManaged.RSS.Feed In resp.Result
                Dim title As String = res.Title
                Dim description As String = res.Description
                Dim link As Uri = res.Link
                '...'

                Dim item As YahooManaged.RSS.FeedItem = res.Items(0)
                Dim iTitle As String = item.Title
                Dim iDescription As String = item.Description
                '...'

            Next

            For Each res As YahooManaged.Weather.WeatherFeed In resp.Result
                Dim sunrise As DateTime = res.Astronomy.Sunrise
                Dim sunset As DateTime = res.Astronomy.Sunset
                Dim pressure As Double = res.Atmosphere.Pressure
                Dim distanceUnit As YahooManaged.Weather.DistanceUnit = res.DistanceUnit
                Dim temperatureUnit As YahooManaged.Weather.DegreesUnit = res.TemperatureUnit
                '...'

                Dim item = CType(res.Items(0), YahooManaged.Weather.WeatherFeedItem)
                Dim temperature As Integer = item.ActualCondition.Temperature
                Dim conditionType As YahooManaged.Weather.ConditionType = item.ActualCondition.Type
                Dim geo As String = item.Coordinates.Latitude.ToString & ";" & item.Coordinates.Longitude.ToString
                '...'

                Dim forecast As YahooManaged.Weather.Forecast = item.ForecastConditions(0)
                Dim fDate As Date = forecast.ForecastDate
                Dim tempHigh As Integer = forecast.HighTemperature
                Dim tempLow As Integer = forecast.LowTemperature
                Dim fConditionType As YahooManaged.Weather.ConditionType = forecast.Type
                '...'

            Next
        End If
    End Sub
```

## C# ##
```
public void Download()
{
	YahooManaged.ResultCountOptions countOptions = new YahooManaged.ResultCountOptions();
	countOptions.Start = 0;
	countOptions.Count = 10;
	string searchString = "berlin";
	bool metricValues = true;

	YahooManaged.Weather.API.WeatherFeedDownload dl = new YahooManaged.Weather.API.WeatherFeedDownload();
	YahooManaged.Weather.API.WeatherFeedResponse resp = dl.Download(searchString, metricValues, countOptions);

	if (resp.Connection.State == Base.ConnectionState.Success) {
		foreach (YahooManaged.RSS.Feed res in resp.Result) {
			string title = res.Title;
			string description = res.Description;
			Uri link = res.Link;
			//...

			YahooManaged.RSS.FeedItem item = res.Items(0);
			string iTitle = item.Title;
			string iDescription = item.Description;
			//...

		}

		foreach (YahooManaged.Weather.WeatherFeed res in resp.Result) {
			DateTime sunrise = res.Astronomy.Sunrise;
			DateTime sunset = res.Astronomy.Sunset;
			double pressure = res.Atmosphere.Pressure;
			YahooManaged.Weather.DistanceUnit distanceUnit = res.DistanceUnit;
			YahooManaged.Weather.DegreesUnit temperatureUnit = res.TemperatureUnit;
			//...

			dynamic item = (YahooManaged.Weather.WeatherFeedItem)res.Items(0);
			int temperature = item.ActualCondition.Temperature;
			YahooManaged.Weather.ConditionType conditionType = item.ActualCondition.Type;
			string geo = item.Coordinates.Latitude.ToString + ";" + item.Coordinates.Longitude.ToString;
			//...

			YahooManaged.Weather.Forecast forecast = item.ForecastConditions(0);
			System.DateTime fDate = forecast.ForecastDate;
			int tempHigh = forecast.HighTemperature;
			int tempLow = forecast.LowTemperature;
			YahooManaged.Weather.ConditionType fConditionType = forecast.Type;
			//...

		}
	}
}
```