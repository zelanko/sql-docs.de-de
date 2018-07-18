---
title: SQLDescribeParam | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: native-client
ms.tgt_pltfrm: ''
ms.topic: reference
topic_type:
- apiref
helpviewer_keywords:
- SQLDescribeParam function
ms.assetid: 396e74b1-5d08-46dc-b404-2ef2003e4689
caps.latest.revision: 61
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 696ac6b8b364c034f4ab5b091e6764f369d2716a
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/03/2018
ms.locfileid: "37417699"
---
# <a name="sqldescribeparam"></a>SQLDescribeParam
  Um die Parameter von einer SQL-Anweisung beschreiben die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC-Treiber erstellt und führt eine [!INCLUDE[tsql](../../includes/tsql-md.md)] SELECT-Anweisung beim SQLDescribeParam für ein vorbereitetes ODBC-Anweisungshandle aufgerufen wird. Die Metadaten des Resultsets bestimmen die Eigenschaften der Parameter in der vorbereiteten Anweisung. SQLDescribeParam kann jeden Fehlercode zurückgeben, die möglicherweise SQLExecute oder SQLExecDirect zurückgeben.  
  
 Verbesserungen in der Datenbank-Engine ab [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] SQLDescribeParam abrufen genauere Beschreibungen der erwarteten Ergebnisse zu ermöglichen. Diese genaueren Ergebnisse unterscheiden sich möglicherweise aus den Werten, die vom SQLDescribeParam in früheren Versionen von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Weitere Informationen finden Sie unter [Metadatenermittlung](../native-client/features/metadata-discovery.md).  
  
 Ebenfalls neu in [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], *ParameterSizePtr* gibt jetzt einen Wert, der gemäß der Definition für die Größe in Zeichen für die Spalte oder des Ausdrucks der entsprechenden parametermarkierung entspricht der [ODBC Spezifikation](http://go.microsoft.com/fwlink/?LinkId=207044). In früheren Versionen von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client *ParameterSizePtr* möglicherweise der entsprechende Wert von `SQL_DESC_OCTET_LENGTH` für den Typ oder ein irrelevanter spaltengrößenwert, die für einen Typ, der Wert auf SQLBindParameter angegeben wurde von der ignoriert werden sollen (`SQL_INTEGER`, z. B.).  
  
 Der Treiber unterstützt das aufrufende SQLDescribeParam in den folgenden Situationen nicht:  
  
-   Nach dem SQLExecDirect für alle [!INCLUDE[tsql](../../includes/tsql-md.md)] Update- oder DELETE-Anweisungen, die mit der FROM-Klausel.  
  
-   Für eine ODBC- oder [!INCLUDE[tsql](../../includes/tsql-md.md)]-Anweisung, die einen Parameter in einer HAVING-Klausel enthält oder die mit dem Ergebnis einer SUM-Funktion verglichen wird.  
  
-   Für eine ODBC- oder [!INCLUDE[tsql](../../includes/tsql-md.md)]-Anweisung abhängig von einer Unterabfrage, die Parameter enthält.  
  
-   Für ODBC SQL-Anweisungen, die Parametermarkierungen in beiden Ausdrücken eines Vergleichs oder quantifizierten Prädikats enthalten.  
  
-   Für Abfragen, bei denen einer der Parameter ein Parameter für eine Funktion ist.  
  
-   Wenn Kommentare (/ * \*/) in der [!INCLUDE[tsql](../../includes/tsql-md.md)] Befehl.  
  
 Bei der Verarbeitung von Batches von [!INCLUDE[tsql](../../includes/tsql-md.md)] -Anweisungen, die Treiber nicht unterstützt, ist aufrufen SQLDescribeParam für parametermarkierungen in Anweisungen nach der ersten Anweisung im Batch.  
  
 Wenn Sie die Parameter der beschreiben gespeicherte Prozeduren vorbereitet, verwendet SQLDescribeParam die gespeicherten Systemprozedur [Sp_sproc_columns](/sql/relational-databases/system-stored-procedures/sp-sproc-columns-transact-sql) um Parametereigenschaften abzurufen. Sp_sproc_columns kann Daten für gespeicherte Prozeduren innerhalb der aktuellen Benutzerdatenbank melden. Vorbereiten der Name einer vollqualifizierten gespeicherten Prozedur kann SQLDescribeParam über Datenbanken hinweg ausgeführt. Z. B. die gespeicherte Systemprozedur [Sp_who](/sql/relational-databases/system-stored-procedures/sp-who-transact-sql) vorbereitet und in jeder Datenbank wie ausgeführt werden können:  
  
```  
SQLPrepare(hstmt, "{call sp_who(?)}", SQL_NTS);  
```  
  
 SQLDescribeParam ausführen, nach erfolgreicher Vorbereitung eine leere Zeile festgelegt, wenn eine Datenbank mit der Rückgabe jedoch `master`. Der gleiche Aufruf wie folgt vorbereitet bewirkt, dass SQLDescribeParam unabhängig von der aktuellen Benutzerdatenbank erfolgreich ist:  
  
```  
SQLPrepare(hstmt, "{call master..sp_who(?)}", SQL_NTS);  
```  
  
 Bei Datentypen mit umfangreichen Werten den Rückgabewert in *DataTypePtr* ist SQL_VARCHAR, SQL_VARBINARY oder SQL_NVARCHAR. Um anzugeben, dass die Größe des umfangreichen Data Type-Parameters "Unbegrenzt" ist die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC-Treiber legt *ParameterSizePtr* auf 0. Tatsächliche Größenwerte werden für `varchar`-Standardparameter zurückgegeben.  
  
> [!NOTE]  
>  Wenn der Parameter bereits mit einer Maximalgröße für den SQL_VARCHAR-, SQL_VARBINARY- oder SQL_WVARCHAR-Parameter gebunden wurde, wird die gebundene Größe des Parameters und nicht "unbegrenzt" zurückgegeben.  
  
 Um einen Eingabeparameter mit "unbegrenzter" Größe zu binden, muss Data-at-Execution verwendet werden. Es ist nicht möglich, ein Output-Parameter mit "unbegrenzter" Größe zu binden (es ist keine Methode für das streaming von Daten aus einer Output-Parameter, wie z. B. [SQLGetData](sqlgetdata.md) für Resultsets ist).  
  
 Für Ausgabeparameter muss ein Puffer gebunden werden und wenn der Wert zu umfangreich ist, wird der Puffer aufgefüllt und eine SQL_SUCCESS_WITH_INFO-Meldung wird zusammen mit einer Warnung "Zeichenfolgendaten werden rechts abgeschnitten" zurückgegeben. Die abgeschnittenen Daten werden anschließend verworfen.  
  
## <a name="sqldescribeparam-and-table-valued-parameters"></a>SQLDescribeParam und Tabellenwertparameter  
 Eine Anwendung kann die Tabellenwertparameter-Informationen für eine vorbereitete Anweisung mit SQLDescribeParam abrufen. Weitere Informationen finden Sie unter [Tabellenwertparameter Parametermetadaten für vorbereitete Anweisungen](../native-client-odbc-table-valued-parameters/table-valued-parameter-metadata-for-prepared-statements.md).  
  
 Weitere Informationen zu Tabellenwertparametern im Allgemeinen finden Sie unter [Table-Valued Parameters &#40;ODBC&#41;](../native-client-odbc-table-valued-parameters/table-valued-parameters-odbc.md).  
  
## <a name="sqldescribeparam-support-for-enhanced-date-and-time-features"></a>SQLDescribeParam-Unterstützung für erweiterte Funktionen für Datum und Uhrzeit  
 Die für Datums-/Uhrzeittypen zurückgegebenen Werte lauten wie folgt:  
  
||*DataTypePtr*|*ParameterSizePtr*|*DecimalDigitsPtr*|  
|-|-------------------|------------------------|------------------------|  
|DATETIME|SQL_TYPE_TIMESTAMP|23|3|  
|smalldatetime|SQL_TYPE_TIMESTAMP|16|0|  
|date|SQL_TYPE_DATE|10|0|  
|Uhrzeit|SQL_SS_TIME2|8, 10..16|0..7|  
|datetime2|SQL_TYPE_TIMESTAMP|19, 21..27|0..7|  
|datetimeoffset|SQL_SS_TIMESTAMPOFFSET|26, 28..34|0..7|  
  
 Weitere Informationen finden Sie unter [Datums- / Uhrzeitverbesserungen &#40;ODBC&#41;](../native-client-odbc-date-time/date-and-time-improvements-odbc.md).  
  
## <a name="sqldescribeparam-support-for-large-clr-udts"></a>SQLDescribeParam-Unterstützung für große CLR-UDTs  
 `SQLDescribeParam` unterstützt große benutzerdefinierte CLR-Typen (UDTs). Weitere Informationen finden Sie unter [Large CLR User-Defined Typen &#40;ODBC&#41;](../../relational-databases/native-client/odbc/large-clr-user-defined-types-odbc.md).  
  
## <a name="see-also"></a>Siehe auch  
 [SQLDescribeParam-Funktion](http://go.microsoft.com/fwlink/?LinkId=59339)   
 [ODBC-API-Implementierungsdetails](../../relational-databases/native-client-odbc-api/odbc-api-implementation-details.md)  
  
  
