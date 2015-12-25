
---


# DownloadBase (obsolete) #

The base class for every downloader class

DownloadBase can't be used for direct downloading outside the library. You are only able to start a download session with the specialized downloader class with the required parameters. These classes are [OnlineCheck](classOnlineCheck.md), [API.IDSearchDownload](classIDSearchDownload.md), [NonAPI.IDSearchDownload](classIDSearchDownloadNonAPI.md), [ImageDownload](classImageDownload.md), [MarketDownload](classMarketDownload.md), [QuotesDownload](classQuotesDownload.md), [IDListDownload](classIDListDownload.md).
In these classes you always have a Download function and DownloadAsync mehtod. With Download function you will get the query results directly. You're also not able to cancel the synchronous download. With DwonloadAsync method you have to handle the AsyncDownloadCompleted event. This event has also specialized parameters for each downloader class.
If an error occurs the Failure event will raise. This event is an public event of DownloadBase.
It is possible to manage all async downlod sessions and the general download options with DownloadBase. You can set the timeout of the next async download with Timeout property. If you need to use a proxy you have the Proxy propety for that issue. If you want to know how many downlaod are currently running, you can get the number from AsyncDownloadsCount property.
If you want to cancel an async download you can call CancelAsyncAll or CancelAsync with the specified user argument to cancel just a special downlaod session.
You can also call Contains function to proof if any download session has the passed object as user argument.

This example will use the QuotesDownload class

## Download ##
## VB.NET ##
```
Private Sub Download()
    Dim ids() As String = New String() {"MSFT", "GOOG", "YHOO"}
    Dim properties() As YahooFinanceManaged.Enums.QuoteProperty = New YahooFinanceManaged.Enums.QuoteProperty() _
                                                    {YahooFinanceManaged.Enums.QuoteProperty.Name, _
                                                    YahooFinanceManaged.Enums.QuoteProperty.Symbol, _
                                                    YahooFinanceManaged.Enums.QuoteProperty.LastTradePriceOnly}
    Dim server As YahooFinanceManaged.Enums.Server = YahooFinanceManaged.Enums.Server.YQL

    Dim qDl As New YahooFinanceManaged.API.QuotesDownload
    Dim quotes() As YahooFinanceManaged.Data.QuoteData = qDl.Download(ids, properties, server)
End Sub
```

## C# ##
```
private void Download()
{
    string[] ids = new string[] { "MSFT", "GOOG", "YHOO" };
    YahooFinanceManaged.Enums.QuoteProperty[] properties = new YahooFinanceManaged.Enums.QuoteProperty[] { 
                                            YahooFinanceManaged.Enums.QuoteProperty.Name,
                                            YahooFinanceManaged.Enums.QuoteProperty.Symbol, 
                                            YahooFinanceManaged.Enums.QuoteProperty.LastTradePriceOnly };
    YahooFinanceManaged.Enums.Server server = YahooFinanceManaged.Enums.Server.YQL;
    
    YahooFinanceManaged.API.QuotesDownload qDl = new YahooFinanceManaged.API.QuotesDownload();
    YahooFinanceManaged.Data.QuoteData[] quotes = qDl.Download(ids, properties, server);
}
```

## DownloadAsync ##
## VB.NET ##
```
Private Sub StartDownload()
    Dim ids() As String = New String() {"MSFT", "GOOG", "YHOO"}
    Dim properties() As YahooFinanceManaged.Enums.QuoteProperty = New YahooFinanceManaged.Enums.QuoteProperty() _
                                                   {YahooFinanceManaged.Enums.QuoteProperty.Name, _
                                                    YahooFinanceManaged.Enums.QuoteProperty.Symbol, _
                                                    YahooFinanceManaged.Enums.QuoteProperty.LastTradePriceOnly}
    Dim server As YahooFinanceManaged.Enums.Server = YahooFinanceManaged.Enums.Server.YQL

    Dim qDl As New YahooFinanceManaged.API.QuotesDownload
    Dim userArgs As String = "MyUserArgument"
    AddHandler qDl.AsyncDownloadCompleted, AddressOf Me.QuotesDownloadAsync_Completed
    Dim dlBase As YahooFinanceManaged.Base.DownloadBase = qDl
    AddHandler dlBase.Failure, AddressOf Me.QuotesDownloadAsync_Failure
    qDl.DownloadAsync(ids, properties, server, userArgs)
End Sub

Private Sub QuotesDownloadAsync_Completed(ByVal sender As YahooFinanceManaged.Base.DownloadBase, _
            ByVal ea As YahooFinanceManaged.API.QuotesDownloadCompletedEventArgs)
    Dim quotes() As YahooFinanceManaged.Data.QuoteData = ea.Results '...'
    Dim server As YahooFinanceManaged.Enums.Server = ea.Server 'YQL'
    Dim properties() As YahooFinanceManaged.Enums.QuoteProperty = ea.Properties 'Name, Symbol, LastTradePriceOnly'

    Dim baseArgs As YahooFinanceManaged.Base.DownloadEventArgs = ea
    Dim userArgs As Object = baseArgs.UserArgs
    Dim myString As String = userArgs.ToString 'MyUserArgument'
    Dim downloadSize As Integer = baseArgs.SizeInBytes '843'
End Sub
```

## C# ##
```
private void StartDownload()
{
    string[] ids = new string[] { "MSFT", "GOOG", "YHOO" };
    YahooFinanceManaged.Enums.QuoteProperty[] properties = new YahooFinanceManaged.Enums.QuoteProperty[] { 
                                            YahooFinanceManaged.Enums.QuoteProperty.Name,
                                            YahooFinanceManaged.Enums.QuoteProperty.Symbol, 
                                            YahooFinanceManaged.Enums.QuoteProperty.LastTradePriceOnly };
     YahooFinanceManaged.Enums.Server server = YahooFinanceManaged.Enums.Server.YQL;
    
    YahooFinanceManaged.API.QuotesDownload qDl = new YahooFinanceManaged.API.QuotesDownload();
    string userArgs = "MyUserArgument";
    qDl.AsyncDownloadCompleted += this.QuotesDownloadAsync_Completed;
    YahooFinanceManaged.Base.DownloadBase dlBase = qDl;
    dlBase.Failure += this.QuotesDownloadAsync_Failure;
    qDl.DownloadAsync(ids, properties, server, userArgs);
}
private void QuotesDownloadAsync_Completed(YahooFinanceManaged.Base.DownloadBase sender,
             YahooFinanceManaged.API.QuotesDownloadCompletedEventArgs ea)
{
    YahooFinanceManaged.Data.QuoteData[] quotes = ea.Results;
    //...
    YahooFinanceManaged.Enums.Server server = ea.Server;
    //YQL
    YahooFinanceManaged.Enums.QuoteProperty[] properties = ea.Properties;
    //Name, Symbol, LastTradePriceOnly
    
    YahooFinanceManaged.Base.DownloadEventArgs baseArgs = ea;
    object userArgs = baseArgs.UserArgs;
    string myString = userArgs.ToString;
    //MyUserArgument
    int downloadSize = baseArgs.SizeInBytes;
    //843
}

```

## Failure ##
## VB.NET ##
```
Private Sub QuotesDownloadAsync_Failure(ByVal sender As YahooFinanceManaged.Base.DownloadBase, _
            ByVal ea As YahooFinanceManaged.Base.DownloadFailureEventArgs)
    Dim ex As Exception = ea.Exception
    Dim timeoutReached As Boolean = ea.TimeoutReached
    Dim timeout As Integer = ea.Timeout
End Sub
```

## C# ##
```
private void QuotesDownloadAsync_Failure(YahooFinanceManaged.Base.DownloadBase sender, 
             YahooFinanceManaged.Base.DownloadFailureEventArgs ea)
{
    Exception ex = ea.Exception;
    bool timeoutReached = ea.TimeoutReached;
    int timeout = ea.Timeout;
}
```