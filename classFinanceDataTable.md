
---


# DataTable #
Class for parsing managed data to and from DataTables

Namespace [YahooManaged](namespaceYahooManaged.md).[Finance](namespaceYahooManagedFinance.md).[ImportExport](namespaceYahooManagedFinanceImportExport.md)



<br></br>

---


---

# Instance Members #

---

## Events ##

There are existing no events.
<br></br>


---

## Properties ##

There are existing no properties.
<br></br>


---

## Constructors ##

### New ###
N/A

<br></br>


---

## Methods ##

### FromHistQuotesData ###

Converts a list of historic quote periods to a System.Data.DataTable

**Parameters**
| **Name** | **Type** | **Description** |
|:---------|:---------|:----------------|
| quotes   | [HistQuoteData()](classHistQuoteData#.md) | The list of historic quote periods |

**Return Type**
| **Type** | **Description** |
|:---------|:----------------|
| [DataTable](http://msdn.microsoft.com/en-us/library/system.data.datatable.aspx) | The converted system.data.DataTable containing the historic quote informations |

<br></br>
### FromQuoteOptions ###

Converts a list of quote values to a System.Data.DataTable

**Parameters**
| **Name** | **Type** | **Description** |
|:---------|:---------|:----------------|
| quotes   | [IEnumerable(Of](http://msdn.microsoft.com/en-us/library/9eekhta0.aspx) [QuoteOptionData)](classQuoteOptionData#.md) | The list of quote values |

**Return Type**
| **Type** | **Description** |
|:---------|:----------------|
| [DataTable](http://msdn.microsoft.com/en-us/library/system.data.datatable.aspx) | The converted system.data.DataTable containing the quote informations |

<br></br>
### FromQuotesBaseData ###

Converts a list of quote values to a system.data.DataTable

**Parameters**
| **Name** | **Type** | **Description** |
|:---------|:---------|:----------------|
| quotes   | [IEnumerable(Of](http://msdn.microsoft.com/en-us/library/9eekhta0.aspx) [QuoteBaseData)](classQuoteBaseData#.md) | The list of quote values |

**Return Type**
| **Type** | **Description** |
|:---------|:----------------|
| [DataTable](http://msdn.microsoft.com/en-us/library/system.data.datatable.aspx) | The converted System.Data.DataTable containing the quote informations |

<br></br>
### FromQuotesData ###

Converts a list of quote values to a System.Data.DataTable

**Parameters**
| **Name** | **Type** | **Description** |
|:---------|:---------|:----------------|
| quotes   | [IEnumerable(Of](http://msdn.microsoft.com/en-us/library/9eekhta0.aspx) [QuoteData)](classQuoteData#.md) | The list of quote values |
| properties | [IEnumerable(Of](http://msdn.microsoft.com/en-us/library/9eekhta0.aspx) [QuoteProperty)](enumQuoteProperty#.md) | The used properties of the items, representing the column headers |

**Return Type**
| **Type** | **Description** |
|:---------|:----------------|
| [DataTable](http://msdn.microsoft.com/en-us/library/system.data.datatable.aspx) | The converted system.data.DataTable containing the quote informations |

<br></br>
### ToHistQuotesData ###

Tries to read a list of historic quote periods from a System.Data.DataTable

**Parameters**
| **Name** | **Type** | **Description** |
|:---------|:---------|:----------------|
| table    | [DataTable](http://msdn.microsoft.com/en-us/library/system.data.datatable.aspx) | The system.data.DataTable with the historic quote periods |

**Return Type**
| **Type** | **Description** |
|:---------|:----------------|
| [HistQuoteData()](classHistQuoteData#.md) | The converted quote periods or Nothing |

<br></br>
### ToQuoteOptions ###

Tries to read a list of quote values from a System.Data.DataTable

**Parameters**
| **Name** | **Type** | **Description** |
|:---------|:---------|:----------------|
| table    | [DataTable](http://msdn.microsoft.com/en-us/library/system.data.datatable.aspx) | The system.data.DataTable with the quote values |

**Return Type**
| **Type** | **Description** |
|:---------|:----------------|
| [QuoteOptionData()](classQuoteOptionData#.md) | The converted quote values or Nothing |

<br></br>
### ToQuotesBaseData ###

Tries to read a list of quote values from a System.Data.DataTable

**Parameters**
| **Name** | **Type** | **Description** |
|:---------|:---------|:----------------|
| table    | [DataTable](http://msdn.microsoft.com/en-us/library/system.data.datatable.aspx) | The System.Data.DataTable with the quote values |

**Return Type**
| **Type** | **Description** |
|:---------|:----------------|
| [QuoteBaseData()](classQuoteBaseData#.md) | The converted quote values or Nothing |

<br></br>
### ToQuotesData ###

Tries to read a list of quote values from a System.Data.DataTable

**Parameters**
| **Name** | **Type** | **Description** |
|:---------|:---------|:----------------|
| table    | [DataTable](http://msdn.microsoft.com/en-us/library/system.data.datatable.aspx) | The system.data.DataTable with the quote values |

**Return Type**
| **Type** | **Description** |
|:---------|:----------------|
| [QuoteData()](classQuoteData#.md) | The converted quote values or Nothing |

<br></br>


---


---

# Static Members #

---

## Events ##

There are existing no events.
<br></br>


---

## Properties ##

There are existing no properties.
<br></br>


---

## Methods ##

There are existing no methods.
<br></br>


---


---

# Remarks #

There are existing no remarks
<br></br>


---


---

# Inheritance #

  * [System](http://msdn.microsoft.com/en-US/library/system.aspx).[Object](http://msdn.microsoft.com/en-US/library/system.object.aspx)
    * [YahooManaged](namespaceYahooManaged.md).[Finance](namespaceYahooManagedFinance.md).[ImportExport](namespaceYahooManagedFinanceImportExport.md).[DataTable](classFinanceDataTable#.md)
<br></br>

[Back to top](classFinanceDataTable#DataTable.md)