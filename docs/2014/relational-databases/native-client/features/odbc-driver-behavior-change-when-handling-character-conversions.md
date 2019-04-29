---
title: ODBC-Treiber-Verhaltensänderung bei der Behandlung von Zeichenkonvertierungen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
ms.assetid: 682a232a-bf89-4849-88a1-95b2fbac1467
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: b7f9562f8594e29c33832c595b9296eaf4f2019b
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63162436"
---
# <a name="odbc-driver-behavior-change-when-handling-character-conversions"></a>Verhaltensänderungen des ODBC-Treibers bei der Behandlung von Zeichenkonvertierungen
  Die [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] Native Client ODBC-Treiber (SQLNCLI11.dll) geändert, wie es der SQL_WCHAR * macht ((NCHAR/nvarchar/nvarchar(max)) und SQL_CHAR\* (CHAR/VARCHAR/NARCHAR(MAX)) Konvertierungen. ODBC-Funktionen wie SQLGetData, SQLBindCol und SQLBindParameter geben bei Verwendung des [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 2012 Native Client-ODBC-Treibers (-4) SQL_NO_TOTAL als Längen-/Indikatorparameter zurück. Von früheren Versionen des [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client-ODBC-Treibers wurde ein Längenwert zurückgegeben, was möglicherweise falsch ist.  
  
## <a name="sqlgetdata-behavior"></a>SQLGetData-Verhalten  
 Bei vielen Windows-Funktionen können Sie die Puffergröße 0 angeben, wobei die zurückgegebene Länge der Größe der zurückgegebenen Daten entspricht. Windows-Programmierer verwenden häufig das folgende Muster:  
  
```  
int iSize = 0;  
BYTE * pBuffer = NULL;  
GetMyFavoriteAPI(pBuffer, &iSize);   // Returns needed size in iSize  
pBuffer = new BYTE[iSize];   // Allocate buffer   
GetMyFavoriteAPI(pBuffer, &iSize);   // Retrieve actual data  
```  
  
 Allerdings **SQLGetData** sollte in diesem Szenario nicht verwendet werden. Das folgende Muster sollte nicht verwendet werden:  
  
```  
// bad  
int iSize = 0;  
WCHAR * pBuffer = NULL;  
SQLGetData(hstmt, SQL_W_CHAR, ...., (SQLPOINTER*)0x1, 0, &iSize);   // Get storage size needed  
pBuffer = new WCHAR[(iSize/sizeof(WCHAR)) + 1];   // Allocate buffer  
SQLGetData(hstmt, SQL_W_CHAR, ...., (SQLPOINTER*)pBuffer, iSize, &iSize);   // Retrieve data  
```  
  
 **SQLGetData** kann nur aufgerufen werden, um Segmente tatsächlicher Daten abzurufen. Mithilfe von **SQLGetData** zum Abrufen der Größe der Daten werden nicht unterstützt.  
  
 Im Folgenden wird veranschaulicht, wie sich der Treiberwechsel bei Verwendung des falschen Musters auswirkt. Von der Anwendung wird eine als Unicode definierte `varchar`-Spalte und -Bindung (SQL_UNICODE/SQL_WCHAR) abgefragt:  
  
 Abfrage:  `select convert(varchar(36), '123')`  
  
```  
SQLGetData(hstmt, SQL_WCHAR, ....., (SQLPOINTER*) 0x1, 0 , &iSize);   // Attempting to determine storage size needed  
```  
  
|[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client-ODBC-Treiberversion|Längen- oder Indikatorergebnis|Description|  
|-----------------------------------------------------------------|---------------------------------|-----------------|  
|[!INCLUDE[ssKilimanjaro](../../../includes/sskilimanjaro-md.md)] Native Client oder früher|6|Der Treiber geht fälschlicherweise davon aus, dass die Konvertierung von CHAR in WCHAR als "Länge * 2" durchgeführt wird.|  
|[!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] Native Client (Version 11.0.2100.60) oder höher|-4 (SQL_NO_TOTAL)|Der Treiber nicht mehr davon aus, dass die Konvertierung von CHAR in WCHAR bzw. WCHAR in CHAR eine (Multiplikation) \*2 oder (Division) / 2 Aktion.<br /><br /> Aufrufen von **SQLGetData** nicht mehr die Länge der erwarteten Konvertierung zurückgegeben. Der Treiber erkennt die Konvertierung in bzw. aus CHAR und WCHAR und gibt anstelle von "*2" oder "/2" das Ergebnis (-4) SQL_NO_TOTAL zurück; dieses Verhalten kann falsch sein.|  
  
 Verwendung **SQLGetData** Segmente der Daten abgerufen. (Dargestellter Pseudocode:)  
  
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
 Abfrage:  `select convert(varchar(36), '1234567890')`  
  
```  
SQLBindCol(... SQL_W_CHAR, ...)   // Only bound a buffer of WCHAR[4] - Expecting String Data Right Truncation behavior  
```  
  
|[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client-ODBC-Treiberversion|Längen- oder Indikatorergebnis|Description|  
|-----------------------------------------------------------------|---------------------------------|-----------------|  
|[!INCLUDE[ssKilimanjaro](../../../includes/sskilimanjaro-md.md)] Native Client oder früher|20|-   **SQLFetch** meldet, dass der Daten auf der rechten Seite abgeschnitten.<br />-Länge ist die Länge der Daten zurückgegeben, nicht was gespeichert wurde (geht davon aus * 2 CHAR in WCHAR-Konvertierung die möglicherweise falsch für Symbole).<br />-Von 123\0 Daten, die im Puffer gespeichert. Der Puffer ist garantiert NULL-terminiert.|  
|[!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] Native Client (Version 11.0.2100.60) oder höher|-4 (SQL_NO_TOTAL)|-   **SQLFetch** meldet, dass der Daten auf der rechten Seite abgeschnitten.<br />-Länge entspricht-4 (SQL_NO_TOTAL) gibt an, weil die übrigen Daten nicht konvertiert wurden.<br />-Data-in im Puffer gespeicherte von 123\0. - Der Puffer ist garantiert NULL-terminiert.|  
  
## <a name="sqlbindparameter-output-parameter-behavior"></a>SQLBindParameter (Verhalten des OUTPUT-Parameters)  
 Abfrage:  `create procedure spTest @p1 varchar(max) OUTPUT`  
  
 `select @p1 = replicate('B', 1234)`  
  
```  
SQLBindParameter(... SQL_W_CHAR, ...)   // Only bind up to first 64 characters  
```  
  
|[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client-ODBC-Treiberversion|Längen- oder Indikatorergebnis|Description|  
|-----------------------------------------------------------------|---------------------------------|-----------------|  
|[!INCLUDE[ssKilimanjaro](../../../includes/sskilimanjaro-md.md)] Native Client oder früher|2468|-   **SQLFetch** gibt keine weiteren Daten verfügbar sind.<br />-   **SQLMoreResults** gibt keine weiteren Daten verfügbar sind.<br />-Länge gibt an, die Größe der Daten vom Server zurückgegebenen, nicht im Puffer gespeichert wird.<br />– Der ursprüngliche Puffer enthält 63 Bytes und einen NULL-Terminator. Der Puffer ist garantiert NULL-terminiert.|  
|[!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] Native Client (Version 11.0.2100.60) oder höher|-4 (SQL_NO_TOTAL)|-   **SQLFetch** gibt keine weiteren Daten verfügbar sind.<br />-   **SQLMoreResults** gibt keine weiteren Daten verfügbar sind.<br />-Länge gibt (-4) SQL_NO_TOTAL, weil die übrigen Daten nicht konvertiert wurden.<br />– Der ursprüngliche Puffer enthält 63 Bytes und einen NULL-Terminator. Der Puffer ist garantiert NULL-terminiert.|  
  
## <a name="performing-char-and-wchar-conversions"></a>Ausführen von CHAR- und WCHAR-Konvertierungen  
 Der [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] Native Client-ODBC-Treiber bietet verschiedene Möglichkeiten zum Durchführen von CHAR- und WCHAR-Konvertierungen. Die Logik ist vergleichbar mit dem Bearbeiten von Blobs (varchar(max), nvarchar(max), …):  
  
-   Daten gespeichert oder in den angegebenen Puffer abgeschnitten werden, bei der Bindung mit **SQLBindCol** oder **SQLBindParameter**.  
  
-   Wenn Sie keine Bindung durchführen, können Sie die Daten in Blöcken abrufen, indem Sie mithilfe von **SQLGetData** und **SQLParamData**.  
  
## <a name="see-also"></a>Siehe auch  
 [SQL Server Native Client-Features](sql-server-native-client-features.md)  
  
  
