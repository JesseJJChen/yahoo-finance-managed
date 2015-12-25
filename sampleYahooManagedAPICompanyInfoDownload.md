[Overview](MainPage.md)/[Documentation](Documentation.md)/[Code Examples](LibraryAppliance.md)/[Finance Namespace](sampleYahooManagedFinance.md)/[Finance.API Namespace](sampleYahooManagedAPI.md)/

---


# ComapnyInfoDownload #
Downloading basic company information

## VB.NET ##
```
    Public Sub Download()
        'Parameters'
        Dim ids As IEnumerable(Of String) = New String() {"MSFT", "GOOG", "YHOO"}

        'Download'
        Dim dl As New YahooManaged.Finance.API.CompanyInfoDownload
        Dim resp As YahooManaged.Finance.API.CompanyInfoResponse = dl.Download(ids)

        'Response/Result'
        If resp.Connection.State = YahooManaged.Base.ConnectionState.Success Then
            For Each info As YahooManaged.Finance.CompanyInfoData In resp.Result
                Dim id As String = info.ID
                Dim name As String = info.Name
                Dim employees As Integer = info.FullTimeEmployees
                Dim start As Date = info.StartDate
                Dim industry As String = info.IndustryName

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
		"YHOO"
	};

	//Download
	YahooManaged.Finance.API.CompanyInfoDownload dl = new YahooManaged.Finance.API.CompanyInfoDownload();
	YahooManaged.Finance.API.CompanyInfoResponse resp = dl.Download(ids);

	//Response/Result
	if (resp.Connection.State == YahooManaged.Base.ConnectionState.Success) {
		foreach (YahooManaged.Finance.CompanyInfoData info in resp.Result) {
			string id = info.ID;
			string name = info.Name;
			int employees = info.FullTimeEmployees;
			System.DateTime start = info.StartDate;
			string industry = info.IndustryName;

		}
	}

}
```