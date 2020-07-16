---
title: DBCC PDW_SHOWPARTITIONSTATS (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 07/17/2017
ms.prod: sql
ms.technology: data-warehouse
ms.reviewer: ''
ms.topic: language-reference
dev_langs:
- TSQL
author: pmasl
ms.author: umajay
monikerRange: '>= aps-pdw-2016 || = azure-sqldw-latest || = sqlallproducts-allversions'
ms.openlocfilehash: 4cb7824e3efd5a0d6cca969a790834a4e61968cb
ms.sourcegitcommit: 01297f2487fe017760adcc6db5d1df2c1234abb4
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/09/2020
ms.locfileid: "86196909"
---
# <a name="dbcc-pdw_showpartitionstats-transact-sql"></a>DBCC PDW_SHOWPARTITIONSTATS (Transact-SQL)
[!INCLUDE[applies-to-version/asa-pdw](../../includes/applies-to-version/asa-pdw.md)]

Zeigt die Größe und die Anzahl der Zeilen der einzelnen Partitionen einer Tabelle in einer [!INCLUDE[ssSDW](../../includes/sssdw-md.md)]- oder [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]-Datenbank an.
  
![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Artikellinksymbol") [Transact-SQL-Syntaxkonventionen &#40;Transact-SQL&#41;](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>Syntax  
  
```syntaxsql
Show the partition stats for a table  
DBCC PDW_SHOWPARTITIONSTATS ( " [ database_name . [ schema_name ] . ] | [ schema_name.] table_name  ")  
[;]  
```  
  
## <a name="arguments"></a>Argumente  
 `[ database_name . [ schema_name ] . | schema_name . ] table_name`  
 Der ein-, zwei- oder dreiteilige Name der Tabelle, die angezeigt werden soll.  Bei zwei- oder dreiteiligen Tabellennamen muss der Name in doppelte Anführungszeichen ("") gesetzt werden. Einteilige Tabellennamen müssen nicht unbedingt in Anführungszeichen gesetzt werden.  
  
## <a name="permissions"></a>Berechtigungen
Erfordert die **VIEW SERVER STATE**-Berechtigung.
  
## <a name="result-sets"></a>Resultsets  
In diesem Set sind die Ergebnisse des DBCC-Befehls PDW_SHOWPARTITIONSTATS dargestellt.
  
|Spaltenname|Datentyp|BESCHREIBUNG|  
|-----------------|---------------|-----------------|  
|partition_number|INT|Partitionsnummer.|  
|used_page_count|BIGINT|Gesamtanzahl der für die Daten verwendeten Seiten.|  
|reserved_page_count|BIGINT|Anzahl der für die Partition reservierten Seiten.|  
|row_count|BIGINT|Anzahl der Zeilen in der Partition.|  
|pdw_node_id|INT|Computeknoten für die Daten.|  
|distribution_id|INT|Verteilungs-ID für die Daten.|  
  
## <a name="examples-sssdw-and-sspdw"></a>Beispiele: [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] und [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
### <a name="a-dbcc-pdw_showpartitionstats-basic-syntax-examples"></a>A. Beispiele: grundlegende DBCC-PDW_SHOWEXECUTIONPLAN-Syntax  
In den folgenden Beispielen wird der belegte Speicherplatz und die Zeilen der einzelnen Partitionen der FactInternetSales-Tabelle in der [!INCLUDE[ssawPDW](../../includes/ssawpdw-md.md)]-Datenbank angezeigt.
  
```sql
DBCC PDW_SHOWPARTITIONSTATS ("ssawPDW.dbo.FactInternetSales");  
DBCC PDW_SHOWPARTITIONSTATS ("dbo.FactInternetSales");  
DBCC PDW_SHOWPARTITIONSTATS (FactInternetSales);  
```  
## <a name="see-also"></a>Weitere Informationen
[DBCC PDW_SHOWEXECUTIONPLAN &#40;Transact-SQL&#41;](dbcc-pdw-showexecutionplan-transact-sql.md)  
[DBCC PDW_SHOWSPACEUSED &#40;Transact-SQL&#41;](dbcc-pdw-showspaceused-transact-sql.md)  
 
