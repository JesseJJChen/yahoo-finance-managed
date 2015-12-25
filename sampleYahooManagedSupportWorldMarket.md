[Overview](MainPage.md)/[Documentation](Documentation.md)/[Code Examples](LibraryAppliance.md)/[Finance Namespace](sampleYahooManagedFinance.md)/[Finance.Support Namespace](sampleYahooManagedSupport.md)/

---


# World Market #

The class for managing world market informations

This class provides the most stock exchange informations
## VB.NET ##
```
For Each se As YahooManaged.Finance.Support.StockExchange In YahooManaged.Finance.Support.WorldMarket.DefaultStockExchanges
    Debug.WriteLine(se.ID)
    '...'
Next

Dim se2 As YahooManaged.Finance.Support.StockExchange = YahooManaged.Finance.Support.WorldMarket.DefaultExchangeBySuffix("bas.de")
If se2 IsNot Nothing Then
    Debug.WriteLine(se2.ID)
    '...'
End If
```

## C# ##
```
foreach (YahooManaged.Finance.Support.StockExchange se in YahooManaged.Finance.Support.WorldMarket.DefaultStockExchanges) {
    Debug.WriteLine(se.ID);
    //...
}

YahooManaged.Finance.Support.StockExchange se2 = YahooManaged.Finance.Support.WorldMarket.DefaultExchangeBySuffix("bas.de");
if (se2 != null) {
    Debug.WriteLine(se2.ID);
    //... 
}
```

And also some index informations
## VB.NET ##
```
Dim index As YahooManaged.Finance.Support.YIndexID = YahooManaged.Finance.Support.WorldMarket.AllIndices(4)
Debug.WriteLine(index.ID)
Debug.WriteLine(index.Name)
Debug.WriteLine(index.Country)
Debug.WriteLine(index.Currency)

Dim se As YahooManaged.Finance.Support.StockExchange = index.StockExchange
Debug.WriteLine(se.ID)
Debug.WriteLine(se.Name)
Debug.WriteLine(se.Country)
Debug.WriteLine(se.IsActiveLocal(Date.Now))
```

## C# ##
```
YahooManaged.Finance.Support.YIndexID index = YahooManaged.Finance.Support.WorldMarket.AllIndices[4];
Debug.WriteLine(index.ID);
Debug.WriteLine(index.Name);
Debug.WriteLine(index.Country);
Debug.WriteLine(index.Currency);
    
YahooManaged.Finance.Support.StockExchange se = index.StockExchange;
Debug.WriteLine(se.ID);
Debug.WriteLine(se.Name);
Debug.WriteLine(se.Country);
Debug.WriteLine(se.IsActiveLocal(System.DateTime.Now));
```