[Overview](MainPage.md)/[Documentation](Documentation.md)/[Code Examples](LibraryAppliance.md)/

---


# Base.Download #
The base download class of the library

## VB.NET ##
```
   'It is not possible to use only an instance of YahooManaged.Base.Download, '
   'so this example will use QuotesBaseDownload to show the functionality of '
   'YahooManaged.Base.Download class '

    Public Sub Download()
        'Parameters '
        Dim ids As IEnumerable(Of String) = New String() {"MSFT", "GOOG", "YHOO"}

        'Download '
        Dim dl As New YahooManaged.Finance.API.QuotesBaseDownload

        Dim baseDl As YahooManaged.Base.Download = dl
        Dim timeout As Integer = baseDl.Timeout
        Dim proxy As System.Net.IWebProxy = baseDl.Proxy
        Dim asyncDownloadsCount As Integer = baseDl.AsyncDownloadsCount

        Dim managedResp As YahooManaged.Finance.API.QuotesBaseResponse = dl.Download(ids)

        Dim baseResponse As YahooManaged.Base.Response = managedResp

        'Response/Result '
        Dim connection As YahooManaged.Base.ConnectionInfo = baseResponse.Connection
        Dim state As YahooManaged.Base.ConnectionState = connection.State
        Dim exception As System.Net.WebException = connection.Exception
        Dim sizeInBytes As Integer = connection.SizeInBytes
        Dim timeSpan As TimeSpan = connection.TimeSpan
        Dim conTimeout As Integer = connection.Timeout

        Dim baseResult As Object = baseResponse.Result

        Dim managedResult() As YahooManaged.Finance.QuoteBaseData = managedResp.Result

    End Sub


    'AsyncDownload Example'

    Public Class AsyncDownloadArgument
        Public Value As String = String.Empty
        Public Sub New()
        End Sub
        Public Sub New(ByVal val As String)
            Me.Value = val
        End Sub
    End Class

    Public Sub DownloadAsync()
        'Parameters '
        Dim ids As IEnumerable(Of String) = New String() {"MSFT", "GOOG", "YHOO"}
        Dim userArgs As Object = New AsyncDownloadArgument("My User Argument")

        'Download '
        Dim dl As New YahooManaged.Finance.API.QuotesBaseDownload

        AddHandler dl.AsyncDownloadCompleted, AddressOf Me.AsyncDownload_Completed

        dl.DownloadAsync(ids, userArgs)

        Dim asyncDownloadsCount As Integer = dl.AsyncDownloadsCount

        'dl.Contains(userArgs) '
        'dl.CancelAsyncAll() '
        'dl.CancelAsyncAt(2) '
        'dl.CancelAsync(userArgs) '
    End Sub


    Private Sub AsyncDownload_Completed(ByVal sender As YahooManaged.Base.Download, ByVal e As YahooManaged.Finance.API.QuotesBaseDownloadCompletedEventArgs)
        'Response/Result'
        Dim baseDownload As YahooManaged.Base.Download = sender
        Dim managedDownload As YahooManaged.Finance.API.QuotesBaseDownload = CType(baseDownload, YahooManaged.Finance.API.QuotesBaseDownload)

        RemoveHandler managedDownload.AsyncDownloadCompleted, AddressOf Me.AsyncDownload_Completed

        Dim baseEventArgs As YahooManaged.Base.DownloadEventArgs = CType(e, YahooManaged.Base.DownloadEventArgs)
        Dim userArgs As Object = baseEventArgs.UserArgs
        Dim myUserArgs As AsyncDownloadArgument = CType(userArgs, AsyncDownloadArgument)
        Dim myString As String = myUserArgs.Value

        Dim completedEventArgs As YahooManaged.Base.DownloadCompletedEventArgs = CType(baseEventArgs, YahooManaged.Base.DownloadCompletedEventArgs)
        Dim baseResponse As YahooManaged.Base.Response = completedEventArgs.Response

        Dim managedResponse As YahooManaged.Finance.API.QuotesBaseResponse = e.Response

        'Optional managed args '
        Dim requestedIDs() As String = e.IDs

    End Sub
```

## C# ##
```
//It is not possible to use only an instance of YahooManaged.Base.Download, 
//so this example will use QuotesBaseDownload to show the functionality of
//YahooManaged.Base.Download class

public void Download()
{
	//Parameters
	IEnumerable<string> ids = new string[] {
		"MSFT",
		"GOOG",
		"YHOO"
	};

	//Download
	YahooManaged.Finance.API.QuotesBaseDownload dl = new YahooManaged.Finance.API.QuotesBaseDownload();

	YahooManaged.Base.Download baseDl = dl;
	int timeout = baseDl.Timeout;
	System.Net.IWebProxy proxy = baseDl.Proxy;
	int asyncDownloadsCount = baseDl.AsyncDownloadsCount;

	YahooManaged.Finance.API.QuotesBaseResponse managedResp = dl.Download(ids);

	YahooManaged.Base.Response baseResponse = managedResp;

	//Response/Result
	YahooManaged.Base.ConnectionInfo connection = baseResponse.Connection;
	YahooManaged.Base.ConnectionState state = connection.State;
	System.Net.WebException exception = connection.Exception;
	int sizeInBytes = connection.SizeInBytes;
	TimeSpan timeSpan = connection.TimeSpan;
	int conTimeout = connection.Timeout;

	object baseResult = baseResponse.Result;

	YahooManaged.Finance.QuoteBaseData[] managedResult = managedResp.Result;

}



public class AsyncDownloadArgument
{
	public string Value = string.Empty;
	public AsyncDownloadArgument()
	{
	}
	public AsyncDownloadArgument(string val)
	{
		this.Value = val;
	}
}

public void DownloadAsync()
{
	//Parameters
	IEnumerable<string> ids = new string[] {
		"MSFT",
		"GOOG",
		"YHOO"
	};
	object userArgs = new AsyncDownloadArgument("My User Argument");

	//Download
	YahooManaged.Finance.API.QuotesBaseDownload dl = new YahooManaged.Finance.API.QuotesBaseDownload();

	int asyncDownloadsCount = dl.AsyncDownloadsCount;

	//dl.Contains(userArgs)
	//dl.CancelAsyncAll()
	//dl.CancelAsyncAt(2)
	//dl.CancelAsync(userArgs)

	dl.AsyncDownloadCompleted += this.AsyncDownload_Completed;

	dl.DownloadAsync(ids, userArgs);

}


private void AsyncDownload_Completed(YahooManaged.Base.Download sender, YahooManaged.Finance.API.QuotesBaseDownloadCompletedEventArgs e)
{
	System.Text.StringBuilder sb = new System.Text.StringBuilder();
	//Response/Result
	YahooManaged.Base.Download baseDownload = sender;
	YahooManaged.Finance.API.QuotesBaseDownload managedDownload = (YahooManaged.Finance.API.QuotesBaseDownload)baseDownload;

	managedDownload.AsyncDownloadCompleted -= this.AsyncDownload_Completed;

	YahooManaged.Base.DownloadEventArgs baseEventArgs = (YahooManaged.Base.DownloadEventArgs)e;
	object userArgs = baseEventArgs.UserArgs;
	AsyncDownloadArgument myUserArgs = (AsyncDownloadArgument)userArgs;
	string myString = myUserArgs.Value;

	YahooManaged.Base.DownloadCompletedEventArgs completedEventArgs = (YahooManaged.Base.DownloadCompletedEventArgs)baseEventArgs;
	YahooManaged.Base.Response baseResponse = completedEventArgs.Response;

	YahooManaged.Finance.API.QuotesBaseResponse managedResponse = e.Response;

	//Optional managed args
	string[] requestedIDs = e.IDs;

}
```