---
title: SQLPutData | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/17/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
apitype: DLLExport
helpviewer_keywords:
- SQLPutData function
ms.assetid: d39aaa5b-7fbc-4315-a7f2-5a7787e04f25
author: MightyPen
ms.author: genemi
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 89e694b18dc27a739a7e1f4d1e0950ef08a01570
ms.sourcegitcommit: 856e42f7d5125d094fa84390bc43048808276b57
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/07/2019
ms.locfileid: "73785743"
---
# <a name="sqlputdata"></a>SQLPutData
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  Die folgenden Einschränkungen gelten, wenn SQLPutData zum Senden von mehr als 65.535 Bytes an Daten (für [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Version 4.21 a) oder 400 KB an Daten (für SQL Server Version 6,0 und höher) für eine SQL_LONGVARCHAR (**Text**), SQL_WLONGVARCHAR (**ntext**) oder SQL_LONGVARBINARY (**Image**)-Spalte verwendet wird:  
  
-   Der Parameter, auf den verwiesen wird, kann der *insert_Value* in einer INSERT-Anweisung sein.  
  
-   Der Parameter, auf den verwiesen wird, kann ein *Ausdruck* in der SET-Klausel einer Update-Anweisung sein.  
  
 Das Abbrechen einer Sequenz von SQLPutData-aufrufen, die Daten in Blöcken für einen Server bereitstellen, auf dem [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ausgeführt wird, bewirkt eine partielle Aktualisierung des Spaltenwerts bei Verwendung von Version 6,5 oder früher. Die **Text**-, **ntext**-oder **Image** -Spalte, auf die verwiesen wurde, als SQLCancel aufgerufen wurde, wird auf einen zwischen Platzhalter Wert festgelegt.  
  
> [!NOTE]  
>  Der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB-Treiber unterstützt das Herstellen einer Verbindung mit der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Version 6.5 und niedriger nicht.  
  
## <a name="diagnostics"></a>Diagnose  
 Es gibt einen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client-spezifischen SQLSTATE für SQLPutData:  
  
|SQLSTATE|Fehler|und Beschreibung|  
|--------------|-----------|-----------------|  
|22026|Zeichenfolgendaten, nicht übereinstimmende Länge|Wenn die Länge der zu sendenden Daten in Bytes von einer Anwendung angegeben wurde, z. b. mit SQL_LEN_DATA_AT_EXEC (*n*), wobei *n* größer als 0 ist, muss die Gesamtanzahl der Bytes, die von der Anwendung über SQLPutData angegeben werden, mit der angegebenen Länge identisch sein.|  
  
## <a name="sqlputdata-and-table-valued-parameters"></a>SQLPutData und Tabellenwertparameter  
 SQLPutData wird von einer Anwendung verwendet, wenn eine Variable Zeilen Bindung mit Tabellenwert Parametern verwendet wird. Der *StrLen_Or_Ind* -Parameter gibt an, dass der Treiber zum Sammeln von Daten für die nächste Zeile oder Zeilen von Tabellenwert Parameter-Daten bereit ist, oder dass keine weiteren Zeilen verfügbar sind:  
  
-   Ein Wert größer als 0 gibt an, dass der nächste Satz von Zeilenwerten verfügbar ist.  
  
-   Der Wert 0 gibt an, dass es keine Zeilen mehr gibt, die gesendet werden sollen.  
  
-   Ein Wert unter 0 zeigt einen Fehler an und führt dazu, dass ein Diagnosedatensatz mit SQLState HY090 aufgezeichnet und die Meldung „Ungültige Zeichenfolge oder Pufferlänge“ ausgegeben wird.  
  
 Der *DataPtr* -Parameter wird ignoriert, muss jedoch auf einen Wert festgelegt werden, der nicht NULL ist. Weitere Informationen finden Sie im Abschnitt zur TVP-Variablen-Zeilen Bindung in [Bindung und Datenübertragung von Tabellenwert Parametern und Spaltenwerten](../../relational-databases/native-client-odbc-table-valued-parameters/binding-and-data-transfer-of-table-valued-parameters-and-column-values.md).  
  
 Wenn *StrLen_Or_Ind* einen anderen Wert als SQL_DEFAULT_PARAM oder eine Zahl zwischen 0 und dem SQL_PARAMSET_SIZE (d. h. dem *ColumnSize* -Parameter von SQLBindParameter) aufweist, handelt es sich um einen Fehler. Dieser Fehler bewirkt, dass SQLPutData SQL_ERROR: SQLSTATE=HY090, "Ungültige Zeichenfolge oder Pufferlänge" zurückgibt.  
  
 Weitere Informationen zu Tabellenwert Parametern finden Sie unter [Tabellenwert Parameter &#40;(ODBC&#41;](../../relational-databases/native-client-odbc-table-valued-parameters/table-valued-parameters-odbc.md)).  
  
## <a name="sqlputdata-support-for-enhanced-date-and-time-features"></a>SQLPutData-Unterstützung für verbesserte Funktionen für Datum/Uhrzeit  
 Parameter Werte von Datums-/Uhrzeittypen werden entsprechend der Beschreibung in [Konvertierungen von C in SQL](../../relational-databases/native-client-odbc-date-time/datetime-data-type-conversions-from-c-to-sql.md)konvertiert.  
  
 Weitere Informationen finden Sie unter [Verbesserungen &#40;bei Datum und&#41;Uhrzeit (ODBC](../../relational-databases/native-client-odbc-date-time/date-and-time-improvements-odbc.md)).  
  
## <a name="sqlputdata-support-for-large-clr-udts"></a>SQLPutData-Unterstützung für große CLR-UDTs  
 **SQLPutData** unterstützt große benutzerdefinierte CLR-Typen (UDTs). Weitere Informationen finden Sie unter [große benutzerdefinierte CLR-Typen &#40;(ODBC&#41;](../../relational-databases/native-client/odbc/large-clr-user-defined-types-odbc.md)).  
  
## <a name="see-also"></a>Siehe auch  
 [SQLPutData-Funktion](https://go.microsoft.com/fwlink/?LinkId=59365)   
 [ODBC-API-Implementierungsdetails](../../relational-databases/native-client-odbc-api/odbc-api-implementation-details.md)  
  
  
