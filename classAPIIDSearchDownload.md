
---


# IDSearchDownload #
Class for searching for IDs

Namespace [YahooManaged](namespaceYahooManaged.md).[Finance](namespaceYahooManagedFinance.md).[API](namespaceYahooManagedFinanceAPI.md)



<br></br>

---


---

# Instance Members #

---

## Events ##

### AsyncDownloadCompleted ###
Raises if an asynchronous download of searh results completes

**Parameters**
| **Name** | **Type** | **Description** |
|:---------|:---------|:----------------|
| sender   | [Download](classDownload#.md) | The event raising object |
| ea       | [IDSearchDownloadCompletedEventArgs](classIDSearchDownloadCompletedEventArgs#.md) | The results of the asynchronous download |


<br></br>


---

## Properties ##

### Proxy ###
Gets or sets the used Proxy informations.

**Property Type**
| **Type** | **Description** |
|:---------|:----------------|
| [IWebProxy](http://msdn.microsoft.com/en-us/library/system.net.iwebproxy.aspx) | N/A             |

<br></br>
### TextEncoding ###
The used encoding informations

**Property Type**
| **Type** | **Description** |
|:---------|:----------------|
| [Encoding](http://social.msdn.microsoft.com/search/en-us/?query=Encoding) | N/A             |

<br></br>
### Timeout ###
Gets or sets the timeout of the next asynchronous download. If value is 0(zero), the next download wont have a timeout.

**Property Type**
| **Type** | **Description** |
|:---------|:----------------|
| [Integer](http://msdn.microsoft.com/en-us/library/06bkb8w2(VS.80).aspx) | N/A             |

<br></br>
### AsyncDownloadsCount (Readonly) ###
The number of running asynchronous downloads.

**Property Type**
| **Type** | **Description** |
|:---------|:----------------|
| [Integer](http://msdn.microsoft.com/en-us/library/06bkb8w2(VS.80).aspx) | N/A             |

<br></br>
### UserArgs (Readonly) ###
The user arguments of each download process

**Property Type**
| **Type** | **Description** |
|:---------|:----------------|
| [Object()](http://social.msdn.microsoft.com/search/en-us/?query=Object()) | N/A             |

<br></br>


---

## Constructors ##

### New ###
Default constructor

<br></br>


---

## Methods ##

### CancelAsync ###

Cancels a specific running download.

**Parameters**
| **Name** | **Type** | **Description** |
|:---------|:---------|:----------------|
| userArgs | [Object](http://msdn.microsoft.com/en-US/library/system.object.aspx) | The user argument that the download object contains. |

**Return Type**
| **Type** | **Description** |
|:---------|:----------------|
| [Integer](http://msdn.microsoft.com/en-us/library/06bkb8w2(VS.80).aspx) | N/A             |

<br></br>
### CancelAsyncAll ###

Cancels all running downloads.

**Return Type**
| **Type** | **Description** |
|:---------|:----------------|
| [Boolean](http://msdn.microsoft.com/en-us/library/wts33hb3(VS.80).aspx) | N/A             |

<br></br>
### CancelAsyncAt ###

Cancels a specific running download.

**Parameters**
| **Name** | **Type** | **Description** |
|:---------|:---------|:----------------|
| index    | [Integer](http://msdn.microsoft.com/en-us/library/06bkb8w2(VS.80).aspx) | The position of the download process in queue. |

**Return Type**
| **Type** | **Description** |
|:---------|:----------------|
| [Boolean](http://msdn.microsoft.com/en-us/library/wts33hb3(VS.80).aspx) | N/A             |

<br></br>
### Contains ###

Returns the number of download processes with the passed user argument.

**Parameters**
| **Name** | **Type** | **Description** |
|:---------|:---------|:----------------|
| userArgs | [Object](http://msdn.microsoft.com/en-US/library/system.object.aspx) | N/A             |

**Return Type**
| **Type** | **Description** |
|:---------|:----------------|
| [Integer](http://msdn.microsoft.com/en-us/library/06bkb8w2(VS.80).aspx) | N/A             |

<br></br>
### Download ###

N/A

**Parameters**
| **Name** | **Type** | **Description** |
|:---------|:---------|:----------------|
| keyword  | [String](http://msdn.microsoft.com/en-us/library/thwcx436(VS.80).aspx) | N/A             |
| server   | [IDSearchServer](enumIDSearchServer#.md) | N/A             |


**Return Type**
| **Type** | **Description** |
|:---------|:----------------|
| [IDSearchResponse](classIDSearchResponse#.md) | N/A             |

<br></br>
### DownloadAsync ###

N/A

**Parameters**
| **Name** | **Type** | **Description** |
|:---------|:---------|:----------------|
| keyword  | [String](http://msdn.microsoft.com/en-us/library/thwcx436(VS.80).aspx) | N/A             |
| server   | [IDSearchServer](enumIDSearchServer#.md) | N/A             |
| userArgs | [Object](http://msdn.microsoft.com/en-US/library/system.object.aspx) | N/A             |


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
    * [YahooManaged](namespaceYahooManaged.md).[Base](namespaceYahooManagedBase.md).[Download](classDownload#.md)
      * [YahooManaged](namespaceYahooManaged.md).[Base](namespaceYahooManagedBase.md).[DataDownload](classDataDownload#.md)
        * [YahooManaged](namespaceYahooManaged.md).[Finance](namespaceYahooManagedFinance.md).[API](namespaceYahooManagedFinanceAPI.md).[IDSearchDownload](classAPIIDSearchDownload#.md)
<br></br>

[Back to top](classAPIIDSearchDownload#IDSearchDownload.md)