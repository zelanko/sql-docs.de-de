---
title: SQLDescribeCol | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
topic_type:
- apiref
helpviewer_keywords:
- SQLDescribeCol function
ms.assetid: ffbf34c6-8268-434f-829a-82009a6cda59
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 95d367efc0bf3fb3e3a74bd0ba9d48b9d8f25be2
ms.sourcegitcommit: 334cae1925fa5ac6c140e0b2c38c844c477e3ffb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/13/2018
ms.locfileid: "53369842"
---
# <a name="sqldescribecol"></a>SQLDescribeCol
  Bei ausgeführten Anweisungen geht der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC-Treiber muss nicht der Server, um Spalten in einem Resultset zu beschreiben abgefragt werden. In diesem Fall `SQLDescribeCol` bewirkt nicht, dass ein Server-Roundtrip erstellt. Wie [SQLColAttribute](sqlnumresultcols.md), wird beim Aufruf `SQLDescribeCol` für vorbereitete aber nicht ausgeführte Anweisungen ein Server-Roundtrip erstellt.  
  
 Wenn eine [!INCLUDE[tsql](../../includes/tsql-md.md)]-Anweisung oder ein Anweisungsstapel mehrere Resultsets für Zeilen zurückgibt, kann eine Spalte, auf die mit einer Ordnungszahl verwiesen wird, ihren Ursprung in einer separaten Tabelle haben oder auf eine vollständig andere Spalte im Resultset verweisen. `SQLDescribeCol` sollte für jede Gruppe aufgerufen werden. Wenn sich das Resultset ändert, sollte die Anwendung Datenwerte vor dem Abrufen von Zeilenergebnissen erneut binden. Weitere Informationen zum Arbeiten mit mehreren resultsetergebnissen, finden Sie unter [SQLMoreResults](sqlmoreresults.md).  
  
 Spaltenattribute werden nur für das erste Resultset gemeldet, wenn durch einen vorbereiteten Stapel von SQL-Anweisungen mehrere Resultsets erzeugt werden.  
  
 Bei Datentypen mit umfangreichen Werten den Rückgabewert in *DataTypePtr* ist SQL_VARCHAR, SQL_VARBINARY oder SQL_NVARCHAR. Ein Wert von SQL_SS_LENGTH_UNLIMITED in *ColumnSizePtr* gibt an, dass die Größe "Unbegrenzt" ist.  
  
 Verbesserungen in der Datenbank-Engine ab [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] SQLDescribeCol abrufen genauere Beschreibungen der erwarteten Ergebnisse zu ermöglichen. Diese genaueren Ergebnisse unterscheiden sich möglicherweise aus den Werten, die vom SQLDescribeCol in früheren Versionen von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Weitere Informationen finden Sie unter [Metadatenermittlung](../native-client/features/metadata-discovery.md).  
  
## <a name="sqldescribecol-support-for-enhanced-date-and-time-features"></a>SQLDescribeCol-Unterstützung für erweiterte Funktionen für Datum und Uhrzeit  
 Die für Datums-/Uhrzeittypen zurückgegebenen Werte lauten wie folgt:  
  
||*DataTypePtr*|*ColumnSizePtr*|*DecimalDigitsPtr*|  
|-|-------------------|---------------------|------------------------|  
|DATETIME|SQL_TYPE_TIMESTAMP|23|3|  
|smalldatetime|SQL_TYPE_TIMESTAMP|16|0|  
|date|SQL_TYPE_DATE|10|0|  
|Uhrzeit|SQL_SS_TIME2|8, 10..16|0..7|  
|datetime2|SQL_TYPE_TIMESTAMP|19, 21..27|0..7|  
|datetimeoffset|SQL_SS_TIMESTAMPOFFSET|26, 28..34|0..7|  
  
 Weitere Informationen finden Sie unter [Datums- / Uhrzeitverbesserungen &#40;ODBC&#41;](../native-client-odbc-date-time/date-and-time-improvements-odbc.md).  
  
## <a name="sqldescribecol-support-for-large-clr-udts"></a>SQLDescribeCol-Unterstützung für große CLR-UDTs  
 `SQLDescribeCol` unterstützt große benutzerdefinierte CLR-Typen (UDTs). Weitere Informationen finden Sie unter [Large CLR User-Defined Typen &#40;ODBC&#41;](../native-client/odbc/large-clr-user-defined-types-odbc.md).  
  
## <a name="see-also"></a>Siehe auch  
 [SQLDescribeCol-Funktion](https://go.microsoft.com/fwlink/?LinkID=59338)   
 [ODBC-API-Implementierungsdetails](odbc-api-implementation-details.md)  
  
  
