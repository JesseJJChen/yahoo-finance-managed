
---


# IDListDownload #
Downloading alphatical list of valid Yahoo! IDs

## VB.NET ##
```
    Public Sub Download()
        'Parameters'
        Dim server As YahooManaged.Server = YahooManaged.Server.Germany
        Dim country As YahooManaged.Country = YahooManaged.Country.DE

        'Download'
        Dim dl As New YahooManaged.Finance.NonAPI.IDListDownload
        Dim rangeResp As YahooManaged.Finance.NonAPI.IDListRangeResponse = dl.DownloadListRange(country, server)

        'Response/Result'
        If rangeResp.Connection.State = YahooManaged.Base.ConnectionState.Success Then
            For Each r As YahooManaged.Finance.IDListRangeData In rangeResp.Result
                '4'
                'A'
                'B'
                'C'
                'D'
                '...'

            Next

            Dim range As YahooManaged.Finance.IDListRangeData = rangeResp.Result(1) 'A'
            Dim subResp As YahooManaged.Finance.NonAPI.IDListSubRangeResponse = dl.DownloadListSubRange(range)
            If subResp.Connection.State = YahooManaged.Base.ConnectionState.Success Then
                For Each sr As YahooManaged.Finance.IDListSubRangeData In subResp.Result
                    'A - AD'
                    'AD - AL'
                    'AL - AS'
                    'AT - AZ'

                Next

                Dim subRange As YahooManaged.Finance.IDListSubRangeData = subResp.Result(0) 'A - AD'
                Dim idResp As YahooManaged.Finance.API.IDSearchResponse = dl.DownloadCompanyList(subRange)
                If idResp.Connection.State = YahooManaged.Base.ConnectionState.Success Then
                    For Each res As YahooManaged.Finance.IDSearchResult In idResp.Result
                        'LUMG.DE'
                        'ASEG.D'
                        'AAQG.DE'
                        'ARLG.DE'
                        'ENMG.DE'
                        '...'

                    Next
                End If

            End If
        End If

    End Sub

```

## C# ##
```
public void Download()
{
	//Parameters
	YahooManaged.Server server = YahooManaged.Server.Germany;
	YahooManaged.Country country = YahooManaged.Country.DE;

	//Download
	YahooManaged.Finance.NonAPI.IDListDownload dl = new YahooManaged.Finance.NonAPI.IDListDownload();
	YahooManaged.Finance.NonAPI.IDListRangeResponse rangeResp = dl.DownloadListRange(country, server);

	//Response/Result
	if (rangeResp.Connection.State == YahooManaged.Base.ConnectionState.Success) {
		foreach (YahooManaged.Finance.IDListRangeData r in rangeResp.Result) {
			//4'
			//A'
			//B'
			//C'
			//D'
			//...'

		}

		YahooManaged.Finance.IDListRangeData range = rangeResp.Result(1);
		//A'
		YahooManaged.Finance.NonAPI.IDListSubRangeResponse subResp = dl.DownloadListSubRange(range);
		if (subResp.Connection.State == YahooManaged.Base.ConnectionState.Success) {
			foreach (YahooManaged.Finance.IDListSubRangeData sr in subResp.Result) {
				//A - AD'
				//AD - AL'
				//AL - AS'
				//AT - AZ'

			}

			YahooManaged.Finance.IDListSubRangeData subRange = subResp.Result(0);
			//A - AD'
			YahooManaged.Finance.API.IDSearchResponse idResp = dl.DownloadCompanyList(subRange);
			if (idResp.Connection.State == YahooManaged.Base.ConnectionState.Success) {
				foreach (YahooManaged.Finance.IDSearchResult res in idResp.Result) {
					//LUMG.DE'
					//ASEG.D'
					//AAQG.DE'
					//ARLG.DE'
					//ENMG.DE'
					//...'

				}
			}

		}
	}

}
```