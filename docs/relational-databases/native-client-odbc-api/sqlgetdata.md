---
title: SQLGetData | Microsoft Docs
ms.custom: ''
ms.date: 03/17/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
apitype: DLLExport
helpviewer_keywords:
- SQLGetData function
ms.assetid: 204848be-8787-45b4-816f-a60ac9d56fcf
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 5ebda3de96cbd9a4a1ceadd62093420cc372a169
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81302152"
---
# <a name="sqlgetdata"></a>SQLGetData
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  **SQLGetData** wird verwendet, um Resultsetdaten ohne Bindungsspaltenwerte abzurufen. **SQLGetData** kann nacheinander für dieselbe Spalte aufgerufen werden, um große Datenmengen aus einer Spalte mit einem **Text-,** **ntext-** oder **Bilddatentyp** abzurufen.  
  
 Es wird nicht vorausgesetzt, dass eine Anwendung Variablen binden muss, um Resultsetdaten abrufen zu können. Die Daten einer beliebigen Spalte [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] können mithilfe von **SQLGetData**vom Native Client ODBC-Treiber abgerufen werden.  
  
 Der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] native Client-ODBC-Treiber unterstützt die Verwendung von **SQLGetData** zum Abrufen von Daten in zufälliger Spaltenreihenfolge nicht. Alle ungebundenen Spalten, die mit **SQLGetData** verarbeitet werden, müssen höhere Spaltenordinale als die gebundenen Spalten im Resultset aufweisen. Die Anwendung muss die Daten vom niedrigsten nicht gebundenen ordinalen Spaltenwert zum höchsten Spaltenwert verarbeiten. Der Versuch, Daten aus einer Spalte mit einer niedrigeren Ordnungszahl abzurufen, führt zu einem Fehler. Wenn die Anwendung Servercursor zur Ausgabe von Resultsetzeilen verwendet, kann die Anwendung erneut die aktuelle Zeile abrufen und dann den Wert einer Spalte abrufen. Wenn eine Anweisung auf dem schreibgeschützten Standardcursor ausgeführt wird, müssen Sie die Anweisung erneut ausführen, um **SQLGetData**zu sichern.  
  
 Der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] native Client ODBC-Treiber meldet genau die Länge von **Text-,** **ntext-** und **Bilddaten,** die mit **SQLGetData**abgerufen wurden. Die Anwendung kann die *StrLen_or_IndPtr* Parameterrückgabe sinnvoll nutzen, um lange Daten schnell abzurufen.  
  
> [!NOTE]  
>  Bei großen Werttypen *geben StrLen_or_IndPtr* bei Datenabschneidungen SQL_NO_TOTAL zurück.  
  
## <a name="sqlgetdata-support-for-enhanced-date-and-time-features"></a>SQLGetData-Unterstützung für verbesserte Funktionen für Datum/Uhrzeit  
 Ergebnisspaltenwerte von Datums-/Uhrzeittypen werden wie unter [Konvertierungen von SQL in C](../../relational-databases/native-client-odbc-date-time/datetime-data-type-conversions-from-sql-to-c.md)beschrieben konvertiert.  
  
 Weitere Informationen finden Sie unter [Datums- und Zeitverbesserungen &#40;ODBC&#41;](../../relational-databases/native-client-odbc-date-time/date-and-time-improvements-odbc.md).  
  
## <a name="sqlgetdata-support-for-large-clr-udts"></a>SQLGetData-Unterstützung für große CLR-UDTs  
 **SQLGetData** unterstützt große benutzerdefinierte CLR-Typen (UDTs). Weitere Informationen finden Sie unter [Große benutzerdefinierte CLR-Typen &#40;ODBC&#41;](../../relational-databases/native-client/odbc/large-clr-user-defined-types-odbc.md).  
  
## <a name="example"></a>Beispiel  
  
```  
SQLHDBC     hDbc = NULL;  
SQLHSTMT    hStmt = NULL;  
long        lEmpID;  
PBYTE       pPicture;  
SQLINTEGER  pIndicators[2];  
  
// Get an environment, connection, and so on.  
...  
  
// Get a statement handle and execute a command.  
SQLAllocHandle(SQL_HANDLE_STMT, hDbc, &hStmt);  
  
if (SQLExecDirect(hStmt,  
    (SQLCHAR*) "SELECT EmployeeID, Photo FROM Employees",  
    SQL_NTS) == SQL_ERROR)  
    {  
    // Handle error and return.  
    }  
  
// Retrieve data from row set.  
SQLBindCol(hStmt, 1, SQL_C_LONG, (SQLPOINTER) &lEmpID, sizeof(long),  
    &pIndicators[0]);  
  
while (SQLFetch(hStmt) == SQL_SUCCESS)  
    {  
    cout << "EmployeeID: " << lEmpID << "\n";  
  
    // Call SQLGetData to determine the amount of data that's waiting.  
    if (SQLGetData(hStmt, 2, SQL_C_BINARY, pPicture, 0, &pIndicators[1])  
        == SQL_SUCCESS_WITH_INFO)  
        {  
        cout << "Photo size: " pIndicators[1] << "\n\n";  
  
        // Get all the data at once.  
        pPicture = new BYTE[pIndicators[1]];  
        if (SQLGetData(hStmt, 2, SQL_C_DEFAULT, pPicture,  
            pIndicators[1], &pIndicators[1]) != SQL_SUCCESS)  
            {  
            // Handle error and continue.  
            }  
  
        delete [] pPicture;  
        }  
    else  
        {  
        // Handle error on attempt to get data length.  
        }  
    }  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [SQLGetData-Funktion](https://go.microsoft.com/fwlink/?LinkId=59350)   
 [ODBC API Implementation Details](../../relational-databases/native-client-odbc-api/odbc-api-implementation-details.md)  
  
  
