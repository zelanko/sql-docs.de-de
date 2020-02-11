---
title: sys. dm_pdw_nodes_exec_query_statistics_xml (Transact-SQL) | Microsoft-Dokumentation
description: Dynamische Verwaltungs Sicht, die den Abfrage Ausführungsplan für in-Flight-Anforderungen zurückgibt. Verwenden Sie diese DMV zum Abrufen von Showplan XML mit vorübergehenden Statistiken.
ms.custom: ''
ms.date: 10/14/2019
ms.prod: sql
ms.technology: data-warehouse
ms.reviewer: ''
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: ''
author: XiaoyuMSFT
ms.author: xiaoyul
monikerRange: =azure-sqldw-latest || = sqlallproducts-allversions
ms.openlocfilehash: 2b12e1a1400ec2d9d4bb85466671cda446511f24
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "73145645"
---
# <a name="dm_pdw_nodes_exec_query_statistics_xml-transact-sql"></a>dm_pdw_nodes_exec_query_statistics_xml (Transact-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-xxx-md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-xxx-md.md)]

Gibt den Abfrage Ausführungsplan für in-Flight-Anforderungen zurück. Verwenden Sie diese DMV zum Abrufen von Showplan XML mit vorübergehenden Statistiken.

## <a name="table-returned"></a>Zurückgegebene Tabelle

|Spaltenname|Datentyp|BESCHREIBUNG|  
|-----------------|---------------|-----------------|
|node_id|**int**|Eindeutige numerische ID, die dem Knoten zugeordnet ist.|
|session_id|**smallint**|ID der Sitzung. Lässt keine NULL-Werte zu.|
|request_id|**int**|ID der Anforderung. Lässt keine NULL-Werte zu.|
|sql_handle|**varbinary (64)**|Ein Token, das den Batch oder die gespeicherte Prozedur eindeutig identifiziert, zu der die Abfrage gehört. NULL-Werte sind zulässig.|
|plan_handle|**varbinary (64)**|Ein Token, das einen Abfrage Ausführungsplan für einen momentan ausgeführten Batch eindeutig identifiziert. NULL-Werte sind zulässig.|
|query_plan|**basi**|Enthält die Showplan-Lauf Zeit Darstellung des Abfrage Ausführungs Plans, der mit *plan_handle* angegeben wird, die partielle Statistiken enthält. Der Showplan liegt im XML-Format vor. Für jeden Batch, der z. B. Ad-hoc- [!INCLUDE[tsql](../../includes/tsql-md.md)] -Anweisungen, Aufrufe von gespeicherten Prozeduren und benutzerdefinierten Funktionen enthält, wird jeweils ein Plan generiert. NULL-Werte sind zulässig.|

## <a name="remarks"></a>Bemerkungen
Die gleichen Hinweise in [sys. dm_exec_query_statistics_xml](https://docs.microsoft.com/sql/relational-databases/system-dynamic-management-views/sys-dm-exec-query-statistics-xml-transact-sql?view=sql-server-ver15) werden angewendet.   

## <a name="permissions"></a>Berechtigungen  
 Erfordert die `VIEW SERVER STATE`-Berechtigung auf dem Server.  

## <a name="see-also"></a>Weitere Informationen  
 [SQL Data Warehouse und parallele Data Warehouse dynamischen Verwaltungs Sichten &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sql-and-parallel-data-warehouse-dynamic-management-views.md)  

 ## <a name="next-steps"></a>Nächste Schritte
 Weitere Hinweise zur Entwicklung finden Sie in der [Entwicklungsübersicht für SQL Data Warehouse](https://docs.microsoft.com/azure/sql-data-warehouse/sql-data-warehouse-overview-develop).

