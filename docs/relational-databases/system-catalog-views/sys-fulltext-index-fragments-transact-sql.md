---
title: sys.fulltext_index_fragments (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
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
author: douglaslMS
ms.author: douglasl
manager: craigg
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: dbf3affc922eeddd0b27d15df1177bad30bb185f
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63006128"
---
# <a name="sysfulltextindexfragments-transact-sql"></a>sys.fulltext_index_fragments (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Ein Volltextindex verwendet interne Tabellen, die so genannte *Volltext-indexfragmente* um die umgekehrten Indexdaten zu speichern. Diese Sicht kann verwendet werden, um die Metadaten zu diesen Fragmenten abzufragen. Diese Sicht enthält eine Zeile für jedes Volltextindexfragment in jeder Tabelle, die einen Volltextindex enthält.  
 
  
|Spaltenname|Datentyp|Description|  
|-----------------|---------------|-----------------|  
|table_id|**int**|Objekt-ID der Tabelle, die das Volltextindexfragment enthält.|  
|fragment_object_id|**int**|Objekt-ID der dem Objekt zugeordneten internen Tabelle.|  
|fragment_id|**int**|Logische ID des Volltextindexfragments. Sie ist fragmentübergreifend für diese Tabelle eindeutig.|  
|timestamp|**timestamp**|Der Fragmenterstellung zugeordneter Timestamp. Die Timestamps der aktuelleren Fragmente sind größer als die Timestamps älterer Fragmente.|  
|data_size|**int**|Logische Größe des Fragments in Bytes.|  
|row_count|**int**|Anzahl der einzelnen Zeilen im Fragment.|  
|status|**int**|Status des Fragments, entweder:<br /><br /> 0 = Neu erstellt und noch nicht verwendet<br /><br /> 1 = Während Volltextindexauffüllung oder Zusammenführungen zur Einfügung verwendet<br /><br /> 4 = Beendet. Bereit für Abfrage<br /><br /> 6 = Für Eingabe für Zusammenführung verwendet und bereit für Abfrage<br /><br /> 8 = Zum Löschen markiert. Wird nicht für Abfrage undQuelle der Zusammenführung verwendet.<br /><br /> Status 4 oder 6 bedeutet, dass das Fragment Teil des logischen Volltextindex ist und abgefragt werden kann; Es ist also eine *abfragbare* Fragment.|  
  
## <a name="remarks"></a>Hinweise  
 Die Katalogsicht sys.fulltext_index_fragments kann verwendet werden, um die Anzahl der Fragmente abzufragen, die ein Volltextindex umfasst. Wenn die Volltextabfrage nur langsam ausgeführt wird, können Sie mit fulltext_index_fragments die Anzahl der abfragbaren Fragmente (Status = 4 oder 6) im Volltextindex wie folgt abfragen:  
  
```  
SELECT table_id, status FROM sys.fulltext_index_fragments  
   WHERE status=4 OR status=6;  
```  
  
 Wenn viele abfragbare Fragmente vorhanden sind, empfiehlt Microsoft die Neuorganisation des Volltextkatalogs, der den Volltextindex zur Zusammenführung der Fragmente enthält. So organisieren Sie neu ein Volltextkatalog Verwendung [ALTER FULLTEXT CATALOG](../../t-sql/statements/alter-fulltext-catalog-transact-sql.md)*Catalog_name* neu zu organisieren. Um z. B. einen Volltextkatalog namens `ftCatalog` in der Datenbank `AdventureWorks2012` neu zu organisieren, geben Sie den folgenden Befehl ein:  
  
```  
USE AdventureWorks2012;  
GO  
ALTER FULLTEXT CATALOG ftCatalog REORGANIZE;  
GO  
```  
  
## <a name="permissions"></a>Berechtigungen  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)]  
  
## <a name="see-also"></a>Siehe auch  
 [Katalogsichten für Objekte &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/object-catalog-views-transact-sql.md)   
 [Auffüllen von Volltextindizes](../../relational-databases/search/populate-full-text-indexes.md)  
  
  
