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
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "63067767"
---
# <a name="sqldescribecol"></a>SQLDescribeCol
  Bei ausgeführten Anweisungen muss [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] der Native Client-ODBC-Treiber den Server nicht Abfragen, um Spalten in einem Resultset zu beschreiben. In diesem Fall verursacht `SQLDescribeCol` keinen Serverroundtrip. Wie [SQLColAttribute](sqlnumresultcols.md)generiert der `SQLDescribeCol` Aufruf von für vorbereitete, aber nicht ausgeführte Anweisungen einen Serverroundtrip.  
  
 Wenn eine [!INCLUDE[tsql](../../includes/tsql-md.md)]-Anweisung oder ein Anweisungsstapel mehrere Resultsets für Zeilen zurückgibt, kann eine Spalte, auf die mit einer Ordnungszahl verwiesen wird, ihren Ursprung in einer separaten Tabelle haben oder auf eine vollständig andere Spalte im Resultset verweisen. `SQLDescribeCol`muss für jeden Satz aufgerufen werden. Wenn sich das Resultset ändert, sollte die Anwendung Datenwerte vor dem Abrufen von Zeilenergebnissen erneut binden. Weitere Informationen zum Verarbeiten mehrerer Resultsets finden Sie unter [SQLMoreResults](sqlmoreresults.md).  
  
 Spaltenattribute werden nur für das erste Resultset gemeldet, wenn durch einen vorbereiteten Stapel von SQL-Anweisungen mehrere Resultsets erzeugt werden.  
  
 Bei Datentypen mit umfangreichen Werten ist der in *DataTypePtr* zurückgegebene Wert SQL_VARCHAR, SQL_VARBINARY oder SQL_NVARCHAR. Der Wert SQL_SS_LENGTH_UNLIMITED in *ColumnSizePtr* gibt an, dass die Größe unbegrenzt ist.  
  
 Verbesserungen in der Datenbank- [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] Engine, beginnend mit ermöglichen SQLDescribeCol, genauere Beschreibungen der erwarteten Ergebnisse zu erhalten. Diese präziseren Ergebnisse können sich von den Werten unterscheiden, die von SQLDescribeCol in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]früheren Versionen von zurückgegeben wurden. Weitere Informationen finden Sie unter [metadatenermittlung](../native-client/features/metadata-discovery.md).  
  
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
  
 Weitere Informationen finden Sie unter [Verbesserungen bei Datum und Uhrzeit &#40;ODBC-&#41;](../native-client-odbc-date-time/date-and-time-improvements-odbc.md).  
  
## <a name="sqldescribecol-support-for-large-clr-udts"></a>SQLDescribeCol-Unterstützung für große CLR-UDTs  
 
  `SQLDescribeCol` unterstützt große benutzerdefinierte CLR-Typen (UDTs). Weitere Informationen finden Sie unter [große benutzerdefinierte CLR-Typen &#40;ODBC-&#41;](../native-client/odbc/large-clr-user-defined-types-odbc.md).  
  
## <a name="see-also"></a>Weitere Informationen  
 [SQLDescribeCol-Funktion](https://go.microsoft.com/fwlink/?LinkID=59338)   
 [ODBC API Implementation Details](odbc-api-implementation-details.md)  
  
  
