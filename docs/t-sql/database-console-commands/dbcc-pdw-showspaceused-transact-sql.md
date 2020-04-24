---
title: DBCC PDW_SHOWSPACEUSED (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 07/17/2017
ms.prod: sql
ms.technology: data-warehouse
ms.reviewer: ''
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: 73f598cf-b02a-4dba-8d89-9fc0b55a12b8
author: pmasl
ms.author: umajay
monikerRange: '>= aps-pdw-2016 || = azure-sqldw-latest || = sqlallproducts-allversions'
ms.openlocfilehash: a4b05ff7d7d112b585f28543b204d80455721806
ms.sourcegitcommit: 8ffc23126609b1cbe2f6820f9a823c5850205372
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/17/2020
ms.locfileid: "81632355"
---
# <a name="dbcc-pdw_showspaceused-transact-sql"></a>DBCC PDW_SHOWSPACEUSED (Transact-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md.md)]

Zeigt die Anzahl von Reihen, den reservierten Speicherplatz und den durch eine bestimmte Tabelle oder durch alle Tabellen in einer [!INCLUDE[ssSDW](../../includes/sssdw-md.md)]- oder [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]-Datenbank belegten Speicherplatz an.
  
![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen &#40;Transact-SQL&#41;](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>Syntax  
  
```syntaxsql
-- Show the space used for all user tables and system tables in the current database  
DBCC PDW_SHOWSPACEUSED  
[;]  
  
-- Show the space used for a table  
DBCC PDW_SHOWSPACEUSED ( " [ database_name . [ schema_name ] . ] | [ schema_name .] table_name  " )  
[;]  
```  
  
## <a name="arguments"></a>Argumente  
 `[ database_name . [ schema_name ] . | schema_name . ] table_name`  
 Der ein-, zwei- oder dreiteilige Name der Tabelle, die angezeigt werden soll. Bei zwei- oder dreiteiligen Tabellennamen muss der Name in doppelte Anführungszeichen ("") gesetzt werden. Einteilige Tabellennamen müssen nicht unbedingt in Anführungszeichen gesetzt werden. Wenn kein Tabellenname angegeben wird, werden die Informationen für die aktuelle Datenbank angezeigt.  
  
## <a name="permissions"></a>Berechtigungen  
Erfordert die VIEW SERVER STATE-Berechtigung.
  
## <a name="result-sets"></a>Resultsets  
Im Folgenden wird das Resultset für alle Tabellen aufgeführt.
  
|Column|Datentyp|BESCHREIBUNG|  
|------------|---------------|-----------------|  
|reserved_space|BIGINT|Insgesamt durch die Datenbank belegter Speicherplatz in KB.|  
|data_space|BIGINT|Durch die Daten belegter Speicherplatz in KB.|  
|index_space|BIGINT|Durch die Daten belegter Speicherplatz in KB.|  
|unused_space|BIGINT|Speicherplatz in KB, der zum reservierten Speicherplatz gehört und nicht verwendet wird.|  
|pdw_node_id|INT|Computeknoten, der für die Daten verwendet wird.|  
  
Im Folgenden wird das Resultset für eine Tabelle aufgeführt.
  
|Column|Datentyp|BESCHREIBUNG|Range|  
|------------|---------------|-----------------|-----------|  
|rows|BIGINT|Anzahl von Zeilen.||  
|reserved_space|BIGINT|Gesamtspeicherplatz in KB, der für das Objekt reserviert ist.||  
|data_space|BIGINT|Durch die Daten belegter Speicherplatz in KB.||  
|index_space|BIGINT|Durch die Daten belegter Speicherplatz in KB.||  
|unused_space|BIGINT|Speicherplatz in KB, der zum reservierten Speicherplatz gehört und nicht verwendet wird.||  
|pdw_node_id|INT|Computeknoten, der zum Erstellen von Berichten zum Speicherplatz verwendet wird.||  
|distribution_id|INT|Verteilung, die zum Erstellen von Berichten zum Speicherplatz verwendet wird.|Der Wert für replizierte Tabellen ist –1.|  
  
## <a name="examples-sssdw-and-sspdw"></a>Beispiele: [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] und [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
### <a name="a-dbcc-pdw_showspaceused-basic-syntax"></a>A. Grundlegende DBCC-PDW_SHOWSPACEUSED-Syntax  
Das folgende Beispiel zeigt verschiedene Möglichkeiten zum Anzeigen der Anzahl von Reihen, des reservierten Speicherplatzes und des Speicherplatzes, der durch die FactInternetSales-Tabellen in der [!INCLUDE[ssawPDW](../../includes/ssawpdw-md.md)]-Datenbank belegt ist.
  
```sql
-- Uses AdventureWorks  
  
DBCC PDW_SHOWSPACEUSED ( "AdventureWorksPDW2012.dbo.FactInternetSales" );  
DBCC PDW_SHOWSPACEUSED ( "AdventureWorksPDW2012..FactInternetSales" );  
DBCC PDW_SHOWSPACEUSED ( "dbo.FactInternetSales" );  
DBCC PDW_SHOWSPACEUSED ( FactInternetSales );  
```  
  
### <a name="b-show-the-disk-space-used-by-all-tables-in-the-current-database"></a>B. Anzeigen des durch alle Tabellen in der aktuellen Datenbank belegten Speicherplatzes  
 Das folgende Beispiel zeigt den Speicherplatz, der reserviert und durch sämtliche Benutzer- und Systemtabellen in der [!INCLUDE[ssawPDW](../../includes/ssawpdw-md.md)]-Datenbank belegt ist.  
  
```sql
-- Uses AdventureWorks  
  
DBCC PDW_SHOWSPACEUSED;  
```  
 ## <a name="see-also"></a>Weitere Informationen
[DBCC PDW_SHOWEXECUTIONPLAN &#40;Transact-SQL&#41;](dbcc-pdw-showexecutionplan-transact-sql.md)  
[DBCC PDW_SHOWPARTITIONSTATS &#40;Transact-SQL&#41;](dbcc-pdw-showpartitionstats-transact-sql.md)

  
