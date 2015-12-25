[Overview](MainPage.md)/[Documentation](Documentation.md)/[Code Examples](LibraryAppliance.md)/[Finance Namespace](sampleYahooManagedFinance.md)/[Finance.API Namespace](sampleYahooManagedAPI.md)/

---


# MarketDownload #
Download market overview of sectors, industries and company IDs

## VB.NET ##
```
    Public Sub Download()
        'Parameters'
        Dim sectors As IEnumerable(Of YahooManaged.Finance.Sector) = New YahooManaged.Finance.Sector() {YahooManaged.Finance.Sector.Basic_Materials}

        'Download Sectors'
        Dim dl As New YahooManaged.Finance.API.MarketDownload
        Dim respSectors As YahooManaged.Finance.API.SectorResponse = dl.DownloadSectors(sectors)

        'Response/Result'
        If respSectors.Connection.State = YahooManaged.Base.ConnectionState.Success Then
            For Each sector As YahooManaged.Finance.SectorData In respSectors.Result
                Dim sectorID As YahooManaged.Finance.Sector = sector.ID
                Dim sectorName As String = sector.Name
                Dim industries As List(Of YahooManaged.Finance.IndustryData) = sector.Industries
                Dim industryCount As Integer = industries.Count

                'Download Industries'
                Dim respIndustries As YahooManaged.Finance.API.IndustryResponse = dl.DownloadIndustries(industries)

                'Response/Result'
                If respIndustries.Connection.State = YahooManaged.Base.ConnectionState.Success Then
                    For Each industry As YahooManaged.Finance.IndustryData In respIndustries.Result
                        Dim industryID As Integer = industry.ID
                        Dim industryName As String = industry.Name
                        Dim companies As List(Of YahooManaged.Finance.CompanyInfoData) = industry.Companies
                        Dim companyCount As Integer = companies.Count

                        For Each company As YahooManaged.Finance.CompanyInfoData In companies
                            Dim companyID As String = company.ID
                            Dim companyName As String = company.Name
                            Dim employees As Integer = company.FullTimeEmployees
                            Dim start As Date = company.StartDate
                            Dim industryNameByCompany As String = company.IndustryName

                        Next
                    Next
                End If

            Next
        End If

    End Sub
```

## C# ##
```
public void Download()
{
	//Parameters
	IEnumerable<YahooManaged.Finance.Sector> sectors = new YahooManaged.Finance.Sector[] { YahooManaged.Finance.Sector.Basic_Materials };

	//Download Sectors
	YahooManaged.Finance.API.MarketDownload dl = new YahooManaged.Finance.API.MarketDownload();
	YahooManaged.Finance.API.SectorResponse respSectors = dl.DownloadSectors(sectors);

	//Response/Result
	if (respSectors.Connection.State == YahooManaged.Base.ConnectionState.Success) {
		foreach (YahooManaged.Finance.SectorData sector in respSectors.Result) {
			YahooManaged.Finance.Sector sectorID = sector.ID;
			string sectorName = sector.Name;
			List<YahooManaged.Finance.IndustryData> industries = sector.Industries;
			int industryCount = industries.Count;

			//Download Industries
			YahooManaged.Finance.API.IndustryResponse respIndustries = dl.DownloadIndustries(industries);

			//Response/Result
			if (respIndustries.Connection.State == YahooManaged.Base.ConnectionState.Success) {
				foreach (YahooManaged.Finance.IndustryData industry in respIndustries.Result) {
					int industryID = industry.ID;
					string industryName = industry.Name;
					List<YahooManaged.Finance.CompanyInfoData> companies = industry.Companies;
					int companyCount = companies.Count;

					foreach (YahooManaged.Finance.CompanyInfoData company in companies) {
						string companyID = company.ID;
						string companyName = company.Name;
						int employees = company.FullTimeEmployees;
						System.DateTime start = company.StartDate;
						string industryNameByCompany = company.IndustryName;

					}
				}
			}

		}
	}

}
```