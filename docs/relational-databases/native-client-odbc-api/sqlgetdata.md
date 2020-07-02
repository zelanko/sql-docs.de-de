---
title: SQLGetData | Microsoft-Dokumentation
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
ms.openlocfilehash: b351ded757bc424b5ae37459ce14fd3f1bd45f73
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/01/2020
ms.locfileid: "85789183"
---
# <a name="sqlgetdata"></a>SQLGetData
[!INCLUDE[SQL Server Azure SQL Database Synapse Analytics PDW ](../../includes/applies-to-version/sql-asdb-asdbmi-asdw-pdw.md)]

  **SQLGetData** wird zum Abrufen von Resultsetdaten ohne Bindungs Spaltenwerte verwendet. **SQLGetData** kann in derselben Spalte nacheinander aufgerufen werden, um große Datenmengen aus einer Spalte mit einem Datentyp vom Typ **Text**, **ntext**oder **Image** abzurufen.  
  
 Es wird nicht vorausgesetzt, dass eine Anwendung Variablen binden muss, um Resultsetdaten abrufen zu können. Die Daten einer beliebigen Spalte können [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] mithilfe von **SQLGetData**vom ODBC-Treiber von Native Client abgerufen werden.  
  
 Der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client-ODBC-Treiber unterstützt nicht die Verwendung von **SQLGetData** , um Daten in der Reihenfolge der Zufalls Spalten abzurufen. Alle ungebundenen Spalten, die mit **SQLGetData** verarbeitet werden, müssen höhere Spalten ordinale aufweisen als die gebundenen Spalten im Resultset. Die Anwendung muss die Daten vom niedrigsten nicht gebundenen ordinalen Spaltenwert zum höchsten Spaltenwert verarbeiten. Der Versuch, Daten aus einer Spalte mit einer niedrigeren Ordnungszahl abzurufen, führt zu einem Fehler. Wenn die Anwendung Servercursor zur Ausgabe von Resultsetzeilen verwendet, kann die Anwendung erneut die aktuelle Zeile abrufen und dann den Wert einer Spalte abrufen. Wenn eine-Anweisung für den standardmäßigen schreibgeschützten Vorwärts Cursor ausgeführt wird, müssen Sie die-Anweisung erneut ausführen, um **SQLGetData**zu sichern.  
  
 Der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client-ODBC-Treiber meldet genau die Länge von **Text**-, **ntext**-und **Image** -Daten, die mithilfe von **SQLGetData**abgerufen wurden. Die Anwendung kann die *StrLen_or_IndPtr* Parameter Rückgabe nutzen, um lange Daten schnell abzurufen.  
  
> [!NOTE]  
>  Bei Typen mit großen Werten werden *StrLen_or_IndPtr* bei der Daten abkürzen SQL_NO_TOTAL zurückgeben.  
  
## <a name="sqlgetdata-support-for-enhanced-date-and-time-features"></a>SQLGetData-Unterstützung für verbesserte Funktionen für Datum/Uhrzeit  
 Ergebnis Spaltenwerte von Datums-/Uhrzeittypen werden wie in [Konvertierungen von SQL in C](../../relational-databases/native-client-odbc-date-time/datetime-data-type-conversions-from-sql-to-c.md)beschrieben konvertiert.  
  
 Weitere Informationen finden Sie unter [Verbesserungen bei Datum und Uhrzeit &#40;ODBC-&#41;](../../relational-databases/native-client-odbc-date-time/date-and-time-improvements-odbc.md).  
  
## <a name="sqlgetdata-support-for-large-clr-udts"></a>SQLGetData-Unterstützung für große CLR-UDTs  
 **SQLGetData** unterstützt große benutzerdefinierte CLR-Typen (UDTs). Weitere Informationen finden Sie unter [große benutzerdefinierte CLR-Typen &#40;ODBC-&#41;](../../relational-databases/native-client/odbc/large-clr-user-defined-types-odbc.md).  
  
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
  
  
