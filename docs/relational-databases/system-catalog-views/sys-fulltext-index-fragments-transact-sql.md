---
description: sys.fulltext_index_fragments (Transact-SQL)
title: sys. fulltext_index_fragments (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- fulltext_index_fragments
- sys.fulltext_index_fragments_TSQL
- fulltext_index_fragments_TSQL
- sys.fulltext_index_fragments
dev_langs:
- TSQL
helpviewer_keywords:
- full-text indexes [SQL Server], fragments
- full-text indexes [SQL Server], metadata
- troubleshooting [SQL Server], full-text search
- sys.fulltext_index_fragments catalog view
ms.assetid: a82e5018-5d88-45c0-9a47-c251e17a6cdb
author: pmasl
ms.author: pelopes
ms.reviewer: mikeray
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 953bf5145712d81acf0ed193719d290cc2397e43
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88401366"
---
# <a name="sysfulltext_index_fragments-transact-sql"></a>sys.fulltext_index_fragments (Transact-SQL)
[!INCLUDE [SQL Server SQL Database](../../includes/applies-to-version/sql-asdb.md)]

  Ein Volltextindex verwendet interne Tabellen, die als *Volltextindex Fragmente* bezeichnet werden, um die umgekehrten Indexdaten zu speichern. Diese Sicht kann verwendet werden, um die Metadaten zu diesen Fragmenten abzufragen. Diese Sicht enthält eine Zeile für jedes Volltextindexfragment in jeder Tabelle, die einen Volltextindex enthält.  
 
  
|Spaltenname|Datentyp|BESCHREIBUNG|  
|-----------------|---------------|-----------------|  
|table_id|**int**|Objekt-ID der Tabelle, die das Volltextindexfragment enthält.|  
|fragment_object_id|**int**|Objekt-ID der dem Objekt zugeordneten internen Tabelle.|  
|fragment_id|**int**|Logische ID des Volltextindexfragments. Sie ist fragmentübergreifend für diese Tabelle eindeutig.|  
|timestamp|**timestamp**|Der Fragmenterstellung zugeordneter Timestamp. Die Timestamps der aktuelleren Fragmente sind größer als die Timestamps älterer Fragmente.|  
|data_size|**int**|Logische Größe des Fragments in Bytes.|  
|row_count|**int**|Anzahl der einzelnen Zeilen im Fragment.|  
|status|**int**|Status des Fragments, entweder:<br /><br /> 0 = Neu erstellt und noch nicht verwendet<br /><br /> 1 = Während Volltextindexauffüllung oder Zusammenführungen zur Einfügung verwendet<br /><br /> 4 = Beendet. Bereit für Abfrage<br /><br /> 6 = Für Eingabe für Zusammenführung verwendet und bereit für Abfrage<br /><br /> 8 = Zum Löschen markiert. Wird nicht für Abfrage undQuelle der Zusammenführung verwendet.<br /><br /> Der Status 4 oder 6 bedeutet, dass das Fragment Teil des logischen voll Text Indexes ist und abgefragt werden kann. Das heißt, dass es sich *um ein* abfragbares Fragment handelt.|  
  
## <a name="remarks"></a>Bemerkungen  
 Die Katalogsicht sys.fulltext_index_fragments kann verwendet werden, um die Anzahl der Fragmente abzufragen, die ein Volltextindex umfasst. Wenn die Volltextabfrage nur langsam ausgeführt wird, können Sie mit fulltext_index_fragments die Anzahl der abfragbaren Fragmente (Status = 4 oder 6) im Volltextindex wie folgt abfragen:  
  
```  
SELECT table_id, status FROM sys.fulltext_index_fragments  
   WHERE status=4 OR status=6;  
```  
  
 Wenn viele abfragbare Fragmente vorhanden sind, empfiehlt Microsoft die Neuorganisation des Volltextkatalogs, der den Volltextindex zur Zusammenführung der Fragmente enthält. Zum erneuten organisieren eines voll Text Katalogs verwenden Sie [ALTER FULLTEXT CATALOG](../../t-sql/statements/alter-fulltext-catalog-transact-sql.md)*Catalog_Name* reorganisieren. Um z. B. einen Volltextkatalog namens `ftCatalog` in der Datenbank `AdventureWorks2012` neu zu organisieren, geben Sie den folgenden Befehl ein:  
  
```  
USE AdventureWorks2012;  
GO  
ALTER FULLTEXT CATALOG ftCatalog REORGANIZE;  
GO  
```  
  
## <a name="permissions"></a>Berechtigungen  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)]  
  
## <a name="see-also"></a>Weitere Informationen  
 [Katalogsichten für Objekte &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/object-catalog-views-transact-sql.md)   
 [Auffüllen von Volltextindizes](../../relational-databases/search/populate-full-text-indexes.md)  
  
  
