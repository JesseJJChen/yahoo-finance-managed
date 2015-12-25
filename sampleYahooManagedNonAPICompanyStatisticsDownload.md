
---


# CompanyStatisticsDownload #
Download key statistics of major companies

## VB.NET ##
```
    Public Sub Download()
        Dim sb As New System.Text.StringBuilder
        'Parameters'
        Dim id As String = "GOOG"

        'Download'
        Dim dl As New NonAPI.CompanyStatisticsDownload
        Dim resp As NonAPI.CompanyStatisticResponse = dl.Download(id)

        'Response/Result'
        Dim result As CompanyStatisticsData = resp.Result
        With result
            Debug.WriteLine(.Name)
            Debug.WriteLine(.ID)
            Debug.WriteLine(.Data)
            With .ValuationMeasures
                sb.AppendLine(.EnterpriseValueInMillion.ToString)
                sb.AppendLine(.EnterpriseValueToEBITDA.ToString)
                sb.AppendLine(.MarketCapitalisationInMillion.ToString)
                '...'
            End With
            With .FinancialHighlights
                sb.AppendLine(.GrossProfitInMillion.ToString)
                sb.AppendLine(.EBITDAInMillion.ToString)
                sb.AppendLine(.FiscalYearEnds.ToShortDateString)
                '...'
            End With
            With .TradingInfo
                sb.AppendLine(.DividendDate.ToShortDateString)
                sb.AppendLine(.LastSplitDate.ToShortDateString)
                sb.AppendLine(.LastSplitFactor.ToString)
                sb.AppendLine(.FloatInMillion.ToString)
                '...'
            End With
        End With

        Return sb.ToString
    End Sub
```

## C# ##
```
public void Download()
{
System.Text.StringBuilder sb = new System.Text.StringBuilder();
//Parameters
string id = "GOOG";

//Download
NonAPI.CompanyStatisticsDownload dl = new NonAPI.CompanyStatisticsDownload();
NonAPI.CompanyStatisticResponse resp = dl.Download(id);

//Response/Result
CompanyStatisticsData result = resp.Result;
var _with1 = result;
Debug.WriteLine(_with1.Name);
Debug.WriteLine(_with1.ID);
Debug.WriteLine(_with1.Data);
var _with2 = _with1.ValuationMeasures;
sb.AppendLine(_with2.EnterpriseValueInMillion.ToString());
sb.AppendLine(_with2.EnterpriseValueToEBITDA.ToString());
sb.AppendLine(_with2.MarketCapitalisationInMillion.ToString());
var _with3 = _with1.FinancialHighlights;
//...
sb.AppendLine(_with3.GrossProfitInMillion.ToString());
sb.AppendLine(_with3.EBITDAInMillion.ToString());
sb.AppendLine(_with3.FiscalYearEnds.ToShortDateString());
var _with4 = _with1.TradingInfo;
//...
sb.AppendLine(_with4.DividendDate.ToShortDateString());
sb.AppendLine(_with4.LastSplitDate.ToShortDateString());
sb.AppendLine(_with4.LastSplitFactor.ToString());
sb.AppendLine(_with4.FloatInMillion.ToString());
//...

return sb.ToString();
}
```