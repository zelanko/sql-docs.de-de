---
title: SQLDescribeParam | Microsoft Docs
ms.custom: ''
ms.date: 03/17/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
apitype: DLLExport
helpviewer_keywords:
- SQLDescribeParam function
ms.assetid: 396e74b1-5d08-46dc-b404-2ef2003e4689
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: efe1fdccbef4f5c4a393083f6eb81efee759be5c
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81302580"
---
# <a name="sqldescribeparam"></a>SQLDescribeParam
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  Um die Parameter einer SQL-Anweisung zu beschreiben, erstellt und führt der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] native Client ODBC-Treiber eine [!INCLUDE[tsql](../../includes/tsql-md.md)] SELECT-Anweisung aus, wenn SQLDescribeParam für ein vorbereitetes ODBC-Anweisungshandle aufgerufen wird. Die Metadaten des Resultsets bestimmen die Eigenschaften der Parameter in der vorbereiteten Anweisung. SQLDescribeParam kann jeden Fehlercode zurückgeben, den SQLExecute oder SQLExecDirect zurückgeben kann.  
  
 Verbesserungen im Datenbankmodul, [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] beginnend mit SQLDescribeParam, ermöglichen es SQLDescribeParam, genauere Beschreibungen der erwarteten Ergebnisse zu erhalten. Diese genaueren Ergebnisse können von den Werten abweichen, die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]von SQLDescribeParam in früheren Versionen von zurückgegeben wurden. Weitere Informationen finden Sie unter [Metadatenermittlung](../../relational-databases/native-client/features/metadata-discovery.md).  
  
 Auch neu [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]in *gibt ParameterSizePtr* nun einen Wert zurück, der an der Definition für die Größe der Spalte oder des Ausdrucks der entsprechenden Parametermarkierung gemäß der [ODBC-Spezifikation](https://go.microsoft.com/fwlink/?LinkId=207044)ausgerichtet ist. In früheren [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Versionen von Native Client kann *ParameterSizePtr* der entsprechende Wert **von SQL_DESC_OCTET_LENGTH** für den Typ oder ein irrelevanter Spaltengrößenwert sein, der SQLBindParameter für einen Typ bereitgestellt wurde, dessen Wert ignoriert werden sollte **(z.** B. SQL_INTEGER).  
  
 Der Treiber unterstützt den Aufruf von SQLDescribeParam in den folgenden Situationen nicht:  
  
-   Nach SQLExecDirect [!INCLUDE[tsql](../../includes/tsql-md.md)] für alle UPDATE- oder DELETE-Anweisungen, die die FROM-Klausel enthalten.  
  
-   Für eine ODBC- oder [!INCLUDE[tsql](../../includes/tsql-md.md)]-Anweisung, die einen Parameter in einer HAVING-Klausel enthält oder die mit dem Ergebnis einer SUM-Funktion verglichen wird.  
  
-   Für eine ODBC- oder [!INCLUDE[tsql](../../includes/tsql-md.md)]-Anweisung abhängig von einer Unterabfrage, die Parameter enthält.  
  
-   Für ODBC SQL-Anweisungen, die Parametermarkierungen in beiden Ausdrücken eines Vergleichs oder quantifizierten Prädikats enthalten.  
  
-   Für Abfragen, bei denen einer der Parameter ein Parameter für eine Funktion ist.  
  
-   Wenn der [!INCLUDE[tsql](../../includes/tsql-md.md)] Befehl Kommentare \*(/* /) vorhanden ist.  
  
 Bei der Verarbeitung [!INCLUDE[tsql](../../includes/tsql-md.md)] eines Batches von Anweisungen unterstützt der Treiber auch nicht das Aufrufen von SQLDescribeParam für Parametermarkierungen in Anweisungen nach der ersten Anweisung im Batch.  
  
 Bei der Beschreibung der Parameter vorbereiteter gespeicherter Prozeduren verwendet SQLDescribeParam die gespeicherte Systemprozedur [sp_sproc_columns](../../relational-databases/system-stored-procedures/sp-sproc-columns-transact-sql.md) zum Abrufen von Parametermerkmalen. sp_sproc_columns können Daten für gespeicherte Prozeduren in der aktuellen Benutzerdatenbank melden. Durch das Vorbereiten eines vollqualifizierten gespeicherten Prozedurnamens kann SQLDescribeParam über Datenbanken hinweg ausgeführt werden. Die gespeicherte Systemprozedur [sp_who](../../relational-databases/system-stored-procedures/sp-who-transact-sql.md) kann z. B. in jeder Datenbank wie folgt vorbereitet und ausgeführt werden:  
  
```  
SQLPrepare(hstmt, "{call sp_who(?)}", SQL_NTS);  
```  
  
 Das Ausführen von SQLDescribeParam nach erfolgreicher Vorbereitung gibt einen leeren Zeilensatz zurück, wenn er mit einer Beliebigen Datenbank außer **Master**verbunden ist. Derselbe Aufruf, der wie folgt vorbereitet wird, bewirkt, dass SQLDescribeParam unabhängig von der aktuellen Benutzerdatenbank erfolgreich ist:  
  
```  
SQLPrepare(hstmt, "{call master..sp_who(?)}", SQL_NTS);  
```  
  
 Bei Datentypen mit großem Wert ist der in *DataTypePtr* zurückgegebene Wert SQL_VARCHAR, SQL_VARBINARY oder SQL_NVARCHAR. Um anzugeben, dass die Größe des Datentypparameters mit [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] großem Wert "unbegrenzt" ist, legt der Native Client ODBC-Treiber *ParameterSizePtr* auf 0 fest. Tatsächliche Größenwerte werden für **Standard-Varchar-Parameter** zurückgegeben.  
  
> [!NOTE]  
>  Wenn der Parameter bereits mit einer Maximalgröße für den SQL_VARCHAR-, SQL_VARBINARY- oder SQL_WVARCHAR-Parameter gebunden wurde, wird die gebundene Größe des Parameters und nicht "unbegrenzt" zurückgegeben.  
  
 Um einen Eingabeparameter mit "unbegrenzter" Größe zu binden, muss Data-at-Execution verwendet werden. Es ist nicht möglich, einen Ausgabeparameter "unbegrenzter Größe" zu binden (es gibt keine Methode zum Streamen von Daten aus einem Ausgabeparameter, wie [ES SQLGetData](../../relational-databases/native-client-odbc-api/sqlgetdata.md) für Ergebnismengen tut).  
  
 Für Ausgabeparameter muss ein Puffer gebunden werden und wenn der Wert zu umfangreich ist, wird der Puffer aufgefüllt und eine SQL_SUCCESS_WITH_INFO-Meldung wird zusammen mit einer Warnung "Zeichenfolgendaten werden rechts abgeschnitten" zurückgegeben. Die abgeschnittenen Daten werden anschließend verworfen.  
  
## <a name="sqldescribeparam-and-table-valued-parameters"></a>SQLDescribeParam und Tabellenwertparameter  
 Eine Anwendung kann Parameterinformationen mit Tabellenwert für eine vorbereitete Anweisung mit SQLDescribeParam abrufen. Weitere Informationen finden Sie unter [Tabellenwert-Parametermetadaten für vorbereitete Anweisungen](../../relational-databases/native-client-odbc-table-valued-parameters/table-valued-parameter-metadata-for-prepared-statements.md).  
  
 Weitere Informationen zu Tabellenwertparametern im Allgemeinen finden Sie unter [Tabellenwertparameter &#40;ODBC&#41;](../../relational-databases/native-client-odbc-table-valued-parameters/table-valued-parameters-odbc.md).  
  
## <a name="sqldescribeparam-support-for-enhanced-date-and-time-features"></a>SQLDescribeParam-Unterstützung für erweiterte Funktionen für Datum und Uhrzeit  
 Die für Datums-/Uhrzeittypen zurückgegebenen Werte lauten wie folgt:  
  
||*DataTypePtr*|*ParameterSizePtr*|*DecimalDigitsPtr*|  
|-|-------------------|------------------------|------------------------|  
|datetime|SQL_TYPE_TIMESTAMP|23|3|  
|smalldatetime|SQL_TYPE_TIMESTAMP|16|0|  
|date|SQL_TYPE_DATE|10|0|  
|time|SQL_SS_TIME2|8, 10..16|0..7|  
|datetime2|SQL_TYPE_TIMESTAMP|19, 21..27|0..7|  
|datetimeoffset|SQL_SS_TIMESTAMPOFFSET|26, 28..34|0..7|  
  
 Weitere Informationen finden Sie unter [Datums- und Zeitverbesserungen &#40;ODBC&#41;](../../relational-databases/native-client-odbc-date-time/date-and-time-improvements-odbc.md).  
  
## <a name="sqldescribeparam-support-for-large-clr-udts"></a>SQLDescribeParam-Unterstützung für große CLR-UDTs  
 **SQLDescribeParam** unterstützt große benutzerdefinierte CLR-Typen (UDTs). Weitere Informationen finden Sie unter [Große benutzerdefinierte CLR-Typen &#40;ODBC&#41;](../../relational-databases/native-client/odbc/large-clr-user-defined-types-odbc.md).  
  
## <a name="see-also"></a>Weitere Informationen  
 [SQLDescribeParam-Funktion](https://go.microsoft.com/fwlink/?LinkId=59339)   
 [ODBC API Implementation Details](../../relational-databases/native-client-odbc-api/odbc-api-implementation-details.md)  
  
  
