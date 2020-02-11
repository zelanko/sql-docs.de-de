---
title: ODBC-Änderungs Behandlung bei char-Konvertierungen
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
ms.assetid: 682a232a-bf89-4849-88a1-95b2fbac1467
author: MightyPen
ms.author: genemi
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 4d82fb6a00de4a18d25df84a69c18f094b9a3e53
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "75258710"
---
# <a name="odbc-driver-behavior-change-when-handling-character-conversions"></a>Verhaltensänderungen des ODBC-Treibers bei der Behandlung von Zeichenkonvertierungen
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  Der [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] Native Client-ODBC-Treiber (SQLNCLI11. dll) hat geändert, wie er SQL_WCHAR * (nchar/nvarchar/nvarchar (max))\* und SQL_CHAR (char/varchar/narchar (max))-Konvertierungen verwendet. ODBC-Funktionen wie SQLGetData, SQLBindCol und SQLBindParameter geben bei Verwendung des [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 2012 Native Client-ODBC-Treibers (-4) SQL_NO_TOTAL als Längen-/Indikatorparameter zurück. Von früheren Versionen des [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client-ODBC-Treibers wurde ein Längenwert zurückgegeben, was möglicherweise falsch ist.  
  
## <a name="sqlgetdata-behavior"></a>SQLGetData-Verhalten  
 Bei vielen Windows-Funktionen können Sie die Puffergröße 0 angeben, wobei die zurückgegebene Länge der Größe der zurückgegebenen Daten entspricht. Windows-Programmierer verwenden häufig das folgende Muster:  
  
```  
int iSize = 0;  
BYTE * pBuffer = NULL;  
GetMyFavoriteAPI(pBuffer, &iSize);   // Returns needed size in iSize  
pBuffer = new BYTE[iSize];   // Allocate buffer   
GetMyFavoriteAPI(pBuffer, &iSize);   // Retrieve actual data  
```  
  
 **SQLGetData** sollte in diesem Szenario jedoch nicht verwendet werden. Das folgende Muster sollte nicht verwendet werden:  
  
```  
// bad  
int iSize = 0;  
WCHAR * pBuffer = NULL;  
SQLGetData(hstmt, SQL_W_CHAR, ...., (SQLPOINTER*)0x1, 0, &iSize);   // Get storage size needed  
pBuffer = new WCHAR[(iSize/sizeof(WCHAR)) + 1];   // Allocate buffer  
SQLGetData(hstmt, SQL_W_CHAR, ...., (SQLPOINTER*)pBuffer, iSize, &iSize);   // Retrieve data  
```  
  
 **SQLGetData** kann nur aufgerufen werden, um Segmente von tatsächlichen Daten abzurufen. Die Verwendung von **SQLGetData** , um die Größe der Daten zu erhalten, wird nicht unterstützt.  
  
 Im Folgenden wird veranschaulicht, wie sich der Treiberwechsel bei Verwendung des falschen Musters auswirkt. Diese Anwendung fragt eine **varchar** -Spalte ab und bindet sie als Unicode (SQL_UNICODE/SQL_WCHAR) ein:  
  
 Such`select convert(varchar(36), '123')`  
  
```  
SQLGetData(hstmt, SQL_WCHAR, ....., (SQLPOINTER*) 0x1, 0 , &iSize);   // Attempting to determine storage size needed  
```  
  
|
  [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client-ODBC-Treiberversion|Längen- oder Indikatorergebnis|BESCHREIBUNG|  
|-----------------------------------------------------------------|---------------------------------|-----------------|  
|
  [!INCLUDE[ssKilimanjaro](../../../includes/sskilimanjaro-md.md)] Native Client oder früher|6|Der Treiber geht fälschlicherweise davon aus, dass die Konvertierung von CHAR in WCHAR als "Länge * 2" durchgeführt wird.|  
|
  [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] Native Client (Version 11.0.2100.60) oder höher|-4 (SQL_NO_TOTAL)|Der Treiber geht nicht mehr davon aus, dass die Umstellung von Char in WCHAR oder wchar in Char eine \*(Multiplikation) 2 oder (dividieren)/2-Aktion ist.<br /><br /> Durch den Aufruf von **SQLGetData** wird die Länge der erwarteten Konvertierung nicht mehr zurückgegeben. Der Treiber erkennt die Konvertierung in bzw. aus CHAR und WCHAR und gibt anstelle von "*2" oder "/2" das Ergebnis (-4) SQL_NO_TOTAL zurück; dieses Verhalten kann falsch sein.|  
  
 Verwenden Sie **SQLGetData** , um die Segmente der Daten abzurufen. (Dargestellter Pseudocode:)  
  
```  
while( (SQL_SUCCESS or SQL_SUCCESS_WITH_INFO) == SQLFetch(...) ) {  
   SQLNumCols(...iTotalCols...)  
   for(int iCol = 1; iCol < iTotalCols; iCol++) {  
      WCHAR* pBufOrig, pBuffer = new WCHAR[100];  
      SQLGetData(.... iCol ... pBuffer, 100, &iSize);   // Get original chunk  
      while(NOT ALL DATA RETREIVED (SQL_NO_TOTAL, ...) ) {  
         pBuffer += 50;   // Advance buffer for data retrieved  
         // May need to realloc the buffer when you reach current size  
         SQLGetData(.... iCol ... pBuffer, 100, &iSize);   // Get next chunk  
      }  
   }  
}  
```  
  
## <a name="sqlbindcol-behavior"></a>SQLBindCol-Verhalten  
 Such`select convert(varchar(36), '1234567890')`  
  
```  
SQLBindCol(... SQL_W_CHAR, ...)   // Only bound a buffer of WCHAR[4] - Expecting String Data Right Truncation behavior  
```  
  
|
  [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client-ODBC-Treiberversion|Längen- oder Indikatorergebnis|BESCHREIBUNG|  
|-----------------------------------------------------------------|---------------------------------|-----------------|  
|
  [!INCLUDE[ssKilimanjaro](../../../includes/sskilimanjaro-md.md)] Native Client oder früher|20|**SQLFetch** meldet, dass auf der rechten Seite der Daten abgeschnitten wird.<br /><br /> Die Länge entspricht der Länge der zurückgegebenen Daten und nicht der Größe der gespeicherten Daten (dabei wird die Konvertierung von CHAR in WCHAR mit Multiplikation (*2) vorausgesetzt, was für Symbole u. U. falsch ist).<br /><br /> Die im Puffer gespeicherten Daten sind 123 \ 0. Der Puffer ist garantiert NULL-terminiert.|  
|
  [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] Native Client (Version 11.0.2100.60) oder höher|-4 (SQL_NO_TOTAL)|**SQLFetch** meldet, dass auf der rechten Seite der Daten abgeschnitten wird.<br /><br /> Die Länge entspricht -4 (SQL_NO_TOTAL), weil die übrigen Daten nicht konvertiert wurden.<br /><br /> Die im Puffer gespeicherten Daten haben eine Größe von 123\0. - Der Puffer ist garantiert NULL-terminiert.|  
  
## <a name="sqlbindparameter-output-parameter-behavior"></a>SQLBindParameter (Verhalten des OUTPUT-Parameters)  
 Such`create procedure spTest @p1 varchar(max) OUTPUT`  
  
 `select @p1 = replicate('B', 1234)`  
  
```  
SQLBindParameter(... SQL_W_CHAR, ...)   // Only bind up to first 64 characters  
```  
  
|
  [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client-ODBC-Treiberversion|Längen- oder Indikatorergebnis|BESCHREIBUNG|  
|-----------------------------------------------------------------|---------------------------------|-----------------|  
|
  [!INCLUDE[ssKilimanjaro](../../../includes/sskilimanjaro-md.md)] Native Client oder früher|2.468|**SQLFetch** gibt keine weiteren verfügbaren Daten zurück.<br /><br /> **SQLMoreResults** gibt keine weiteren verfügbaren Daten zurück.<br /><br /> Die Länge gibt die Größe der vom Server zurückgegebenen, nicht jedoch die Größe der im Puffer gespeicherten Daten an.<br /><br /> Der ursprüngliche Puffer enthält 63 Bytes und einen NULL-Terminator. Der Puffer ist garantiert NULL-terminiert.|  
|
  [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] Native Client (Version 11.0.2100.60) oder höher|-4 (SQL_NO_TOTAL)|**SQLFetch** gibt keine weiteren verfügbaren Daten zurück.<br /><br /> **SQLMoreResults** gibt keine weiteren verfügbaren Daten zurück.<br /><br /> Die Länge entspricht (-4) SQL_NO_TOTAL, weil die übrigen Daten nicht konvertiert wurden.<br /><br /> Der ursprüngliche Puffer enthält 63 Bytes und einen NULL-Terminator. Der Puffer ist garantiert NULL-terminiert.|  
  
## <a name="performing-char-and-wchar-conversions"></a>Ausführen von CHAR- und WCHAR-Konvertierungen  
 Der [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] Native Client-ODBC-Treiber bietet verschiedene Möglichkeiten zum Durchführen von CHAR- und WCHAR-Konvertierungen. Die Logik ähnelt der Bearbeitung von blobzeichen (varchar (max), nvarchar (max),...):  
  
-   Daten werden bei der Bindung mit **SQLBindCol** oder **SQLBindParameter**in den angegebenen Puffer gespeichert oder abgeschnitten.  
  
-   Wenn Sie keine Bindung durchführen, können Sie die Daten in Blöcken mithilfe von **SQLGetData** und **SQLParamData**abrufen.  
  
## <a name="see-also"></a>Weitere Informationen  
 [SQL Server Native Client-Funktionen](../../../relational-databases/native-client/features/sql-server-native-client-features.md)  
  
  
