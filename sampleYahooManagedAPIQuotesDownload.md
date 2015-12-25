[Overview](MainPage.md)/[Documentation](Documentation.md)/[Code Examples](LibraryAppliance.md)/[Finance Namespace](sampleYahooManagedFinance.md)/[Finance.API Namespace](sampleYahooManagedAPI.md)/

---


# QuotesDownload #
Downloading quotes of valid Yahoo! IDs

## VB.NET ##
```
    Public Sub Download()
        'Parameters'
        Dim ids As IEnumerable(Of String) = New String() {"MSFT", "GOOG", "YHOO", "BAS.DE", "ALV.DE", "@^DJI"}
        Dim properties As IEnumerable(Of YahooManaged.Finance.QuoteProperty) = New YahooManaged.Finance.QuoteProperty() _
                                                                                  {YahooManaged.Finance.QuoteProperty.Symbol, _
                                                                                   YahooManaged.Finance.QuoteProperty.Name, _
                                                                                   YahooManaged.Finance.QuoteProperty.LastTradePriceOnly, _
                                                                                   YahooManaged.Finance.QuoteProperty.YearHigh, _
                                                                                   YahooManaged.Finance.QuoteProperty.PreviousClose}
        'Download'
        Dim dl As New YahooManaged.Finance.API.QuotesDownload
        Dim resp As YahooManaged.Finance.API.QuotesResponse = dl.Download(ids, properties)

        'Response/Result'
        If resp.Connection.State = Base.ConnectionState.Success Then
            For Each qd As YahooManaged.Finance.QuoteData In resp.Result
                Dim id As String = qd.ID
                Dim name As String = qd.Name
                Dim lastPrice As Double = qd.LastTradePriceOnly
                Dim yearHigh As Double = CDbl(qd(YahooManaged.Finance.QuoteProperty.YearHigh))
                Dim previousClose As Double = CDbl(qd(YahooManaged.Finance.QuoteProperty.PreviousClose))

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
                "YHOO",
                "BAS.DE",
                "ALV.DE",
                "@^DJI"
        };
            IEnumerable<MaasOne.YahooManaged.Finance.QuoteProperty> properties = new MaasOne.YahooManaged.Finance.QuoteProperty[] {
                MaasOne.YahooManaged.Finance.QuoteProperty.Symbol,
                MaasOne.YahooManaged.Finance.QuoteProperty.Name,
                MaasOne.YahooManaged.Finance.QuoteProperty.LastTradePriceOnly,
                MaasOne.YahooManaged.Finance.QuoteProperty.YearHigh,
                MaasOne.YahooManaged.Finance.QuoteProperty.PreviousClose
        };
          
            //Download
            MaasOne.YahooManaged.Finance.API.QuotesDownload dl = new MaasOne.YahooManaged.Finance.API.QuotesDownload();
            MaasOne.YahooManaged.Finance.API.QuotesResponse resp = dl.Download(ids, properties);

            //Response/Result
            if (resp.Connection.State == MaasOne.Base.ConnectionState.Success)
            {
                foreach (MaasOne.YahooManaged.Finance.QuoteData qd in resp.Result)
                {
                    string id = qd.ID;
                    string name = qd.Name;
                    double lastPrice = qd.LastTradePriceOnly;
                    double yearHigh = Convert.ToDouble(qd[MaasOne.YahooManaged.Finance.QuoteProperty.YearHigh]);
                    double previousClose = Convert.ToDouble(qd[MaasOne.YahooManaged.Finance.QuoteProperty.PreviousClose]);

                }
            }

}
```