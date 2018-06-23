---
title: SQLDescribeCol | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
topic_type:
- apiref
helpviewer_keywords:
- SQLDescribeCol function
ms.assetid: ffbf34c6-8268-434f-829a-82009a6cda59
caps.latest.revision: 40
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: c9c7a2471662efb547d8572ebb78a0a99646c20a
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36060513"
---
# <a name="sqldescribecol"></a>SQLDescribeCol
  Bei ausgeführten Anweisungen geht der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC-Treiber muss nicht zum Abfragen von Server, um Spalten in einem Resultset zu beschreiben. In diesem Fall `SQLDescribeCol` keinen Serverroundtrip herbei. Wie [SQLColAttribute](sqlnumresultcols.md)Aufrufen `SQLDescribeCol` für vorbereitete, aber nicht ausgeführte Anweisungen generiert eine Server-Roundtrip erstellt.  
  
 Wenn eine [!INCLUDE[tsql](../../includes/tsql-md.md)]-Anweisung oder ein Anweisungsstapel mehrere Resultsets für Zeilen zurückgibt, kann eine Spalte, auf die mit einer Ordnungszahl verwiesen wird, ihren Ursprung in einer separaten Tabelle haben oder auf eine vollständig andere Spalte im Resultset verweisen. `SQLDescribeCol` sollte für jede Gruppe aufgerufen werden. Wenn sich das Resultset ändert, sollte die Anwendung Datenwerte vor dem Abrufen von Zeilenergebnissen erneut binden. Finden Sie weitere Informationen zum Arbeiten mit mehreren resultsetergebnissen [SQLMoreResults](sqlmoreresults.md).  
  
 Spaltenattribute werden nur für das erste Resultset gemeldet, wenn durch einen vorbereiteten Stapel von SQL-Anweisungen mehrere Resultsets erzeugt werden.  
  
 Bei Datentypen mit umfangreichen Werten den Wert im zurückgegebenen *DataTypePtr* ist SQL_VARCHAR, SQL_VARBINARY oder SQL_NVARCHAR. Ein Wert von SQL_SS_LENGTH_UNLIMITED in *ColumnSizePtr* gibt an, dass die Größe "Unbegrenzt" ist.  
  
 Verbesserungen im Datenbankmodul ab [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] SQLDescribeCol genauere Beschreibungen der erwarteten Ergebnisse abrufen können. Diese genaueren Ergebnisse unterscheidet sich möglicherweise von der Rückgabewerte SQLDescribeCol in früheren Versionen von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Weitere Informationen finden Sie unter [Metadatenermittlung](../native-client/features/metadata-discovery.md).  
  
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
  
 Weitere Informationen finden Sie unter [Datum und Uhrzeit-Verbesserungen &#40;ODBC&#41;](../native-client-odbc-date-time/date-and-time-improvements-odbc.md).  
  
## <a name="sqldescribecol-support-for-large-clr-udts"></a>SQLDescribeCol-Unterstützung für große CLR-UDTs  
 `SQLDescribeCol` unterstützt große benutzerdefinierte CLR-Typen (UDTs). Weitere Informationen finden Sie unter [Large CLR User-Defined Typen &#40;ODBC&#41;](../native-client/odbc/large-clr-user-defined-types-odbc.md).  
  
## <a name="see-also"></a>Siehe auch  
 [SQLDescribeCol-Funktion](http://go.microsoft.com/fwlink/?LinkID=59338)   
 [ODBC-API-Implementierungsdetails](odbc-api-implementation-details.md)  
  
  