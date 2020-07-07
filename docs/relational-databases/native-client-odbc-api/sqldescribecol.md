---
title: SQLDescribeCol | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/17/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
apitype: DLLExport
helpviewer_keywords:
- SQLDescribeCol function
ms.assetid: ffbf34c6-8268-434f-829a-82009a6cda59
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: ff762ab39c2d915538dc58d2162175803895f877
ms.sourcegitcommit: f3321ed29d6d8725ba6378d207277a57cb5fe8c2
ms.contentlocale: de-DE
ms.lasthandoff: 07/06/2020
ms.locfileid: "86006609"
---
# <a name="sqldescribecol"></a>SQLDescribeCol
[!INCLUDE[SQL Server Azure SQL Database Synapse Analytics PDW ](../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]

  Bei ausgeführten Anweisungen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] muss der Native Client-ODBC-Treiber den Server nicht Abfragen, um Spalten in einem Resultset zu beschreiben. In diesem Fall verursacht **SQLDescribeCol** keinen Serverroundtrip. Wie [SQLColAttribute](../../relational-databases/native-client-odbc-api/sqlcolattribute.md)und[SQLNumResultCols](../../relational-databases/native-client-odbc-api/sqlnumresultcols.md)wird beim Aufrufen von **SQLDescribeCol** für vorbereitete, aber nicht ausgeführte Anweisungen ein Serverroundtrip generiert.  
  
 Wenn eine [!INCLUDE[tsql](../../includes/tsql-md.md)]-Anweisung oder ein Anweisungsstapel mehrere Resultsets für Zeilen zurückgibt, kann eine Spalte, auf die mit einer Ordnungszahl verwiesen wird, ihren Ursprung in einer separaten Tabelle haben oder auf eine vollständig andere Spalte im Resultset verweisen. **SQLDescribeCol** sollte für jeden Satz aufgerufen werden. Wenn sich das Resultset ändert, sollte die Anwendung Datenwerte vor dem Abrufen von Zeilenergebnissen erneut binden. Weitere Informationen zum Verarbeiten mehrerer Resultsets finden Sie unter [SQLMoreResults](../../relational-databases/native-client-odbc-api/sqlmoreresults.md).  
  
 Spaltenattribute werden nur für das erste Resultset gemeldet, wenn durch einen vorbereiteten Stapel von SQL-Anweisungen mehrere Resultsets erzeugt werden.  
  
 Bei Datentypen mit umfangreichen Werten ist der in *DataTypePtr* zurückgegebene Wert SQL_VARCHAR, SQL_VARBINARY oder SQL_NVARCHAR. Der Wert SQL_SS_LENGTH_UNLIMITED in *ColumnSizePtr* gibt an, dass die Größe unbegrenzt ist.  
  
 Verbesserungen in der Datenbank-Engine, beginnend mit [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] ermöglichen SQLDescribeCol, genauere Beschreibungen der erwarteten Ergebnisse zu erhalten. Diese präziseren Ergebnisse können sich von den Werten unterscheiden, die von SQLDescribeCol in früheren Versionen von zurückgegeben wurden [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Weitere Informationen finden Sie unter [Metadatenermittlung](../../relational-databases/native-client/features/metadata-discovery.md).  
  
## <a name="sqldescribecol-support-for-enhanced-date-and-time-features"></a>SQLDescribeCol-Unterstützung für erweiterte Funktionen für Datum und Uhrzeit  
 Die für Datums-/Uhrzeittypen zurückgegebenen Werte lauten wie folgt:  
  
||*DataTypePtr*|*ColumnSizePtr*|*Decimaldigitsptr*|  
|-|-------------------|---------------------|------------------------|  
|datetime|SQL_TYPE_TIMESTAMP|23|3|  
|smalldatetime|SQL_TYPE_TIMESTAMP|16|0|  
|date|SQL_TYPE_DATE|10|0|  
|time|SQL_SS_TIME2|8, 10..16|0..7|  
|datetime2|SQL_TYPE_TIMESTAMP|19, 21..27|0..7|  
|datetimeoffset|SQL_SS_TIMESTAMPOFFSET|26, 28..34|0..7|  
  
 Weitere Informationen finden Sie unter [Verbesserungen bei Datum und Uhrzeit &#40;ODBC-&#41;](../../relational-databases/native-client-odbc-date-time/date-and-time-improvements-odbc.md).  
  
## <a name="sqldescribecol-support-for-large-clr-udts"></a>SQLDescribeCol-Unterstützung für große CLR-UDTs  
 **SQLDescribeCol** unterstützt große benutzerdefinierte CLR-Typen (UDTs). Weitere Informationen finden Sie unter [große benutzerdefinierte CLR-Typen &#40;ODBC-&#41;](../../relational-databases/native-client/odbc/large-clr-user-defined-types-odbc.md).  
  
## <a name="see-also"></a>Weitere Informationen  
 [SQLDescribeCol-Funktion](https://go.microsoft.com/fwlink/?LinkID=59338)   
 [ODBC API Implementation Details](../../relational-databases/native-client-odbc-api/odbc-api-implementation-details.md)  
  
  
