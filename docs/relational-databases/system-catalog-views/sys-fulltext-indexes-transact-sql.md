---
description: sys.fulltext_indexes (Transact-SQL)
title: sys. fulltext_indexes (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- fulltext_indexes
- fulltext_indexes_TSQL
- sys.fulltext_indexes_TSQL
- sys.fulltext_indexes
dev_langs:
- TSQL
helpviewer_keywords:
- sys.fulltext_indexes catalog view
- full-text indexes [SQL Server], properties
ms.assetid: 7fc10fdc-370f-4927-bba0-b76108a7508e
author: pmasl
ms.author: pelopes
ms.reviewer: mikeray
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 2b57b7f507e5721647ca44b7f75388fc5ce8de57
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88401656"
---
# <a name="sysfulltext_indexes-transact-sql"></a>sys.fulltext_indexes (Transact-SQL)
[!INCLUDE [SQL Server SQL Database](../../includes/applies-to-version/sql-asdb.md)]

  Enthält eine Zeile pro Volltextindex eines Tabellenobjekts.  

|Spaltenname|Datentyp|BESCHREIBUNG|  
|-----------------|---------------|-----------------|  
|**object_id**|**int**|ID des Objekts, zu dem dieser Volltextindex gehört|  
|**unique_index_id**|**int**|ID des entsprechenden eindeutigen Volltextindexes, mit der der Volltextindex den Zeilen zugeordnet wird|  
|**fulltext_catalog_id**|**int**|ID des Volltextkatalogs, in dem der Volltextindex gespeichert ist|  
|**is_enabled**|**bit**|1 = Volltext ist derzeit aktiviert|  
|**change_tracking_state**|**char (1)**|Status der Änderungsnachverfolgung<br /><br /> M = Manual<br /><br /> A = Auto<br /><br /> O = Off|  
|**change_tracking_state_desc**|**nvarchar(60)**|Beschreibung des Status der Änderungsnachverfolgung<br /><br /> MANUAL<br /><br /> AUTO<br /><br /> OFF|  
|**has_crawl_completed**|**bit**|Der letzte Durchforstungsvorgang (Auffüllen), den der Volltextindex abgeschlossen hat.|  
|**crawl_type**|**char (1)**|Typ der aktuellen oder letzten Durchforstung<br /><br /> F = Vollständige Durchforstung<br /><br /> I = Inkrementeller, auf Timestamps basierende Durchforstung<br /><br /> U = Update-Durchforstung auf der Basis von Benachrichtigungen<br /><br /> P = Vollständige Durchforstung ist angehalten|  
|**crawl_type_desc**|**nvarchar(60)**|Beschreibung des aktuellen oder letzten Durchforstungstyps<br /><br /> FULL_CRAWL<br /><br /> INCREMENTAL_CRAWL<br /><br /> UPDATE_CRAWL<br /><br /> PAUSED_FULL_CRAWL|  
|**crawl_start_date**|**datetime**|Start der aktuellen oder letzten Durchforstung<br /><br /> NULL = Kein.|  
|**crawl_end_date**|**datetime**|Ende der aktuellen oder letzten Durchforstung<br /><br /> NULL = Kein.|  
|**incremental_timestamp**|**Binär (8)**|Timestampwert, der für die nächste inkrementelle Durchforstung verwendet wird<br /><br /> NULL = Kein.|  
|**stoplist_id**|**int**|ID der [Stopp Liste](../../relational-databases/search/configure-and-manage-stopwords-and-stoplists-for-full-text-search.md) , die diesem Volltextindex zugeordnet ist.|  
|**data_space_id**|**int**|Dateigruppe, in der sich dieser Volltextindex befindet.|  
|**property_list_id**|**int**|ID der diesem Volltextindex zugeordneten Sucheigenschaftenliste. NULL gibt an, dass dem Volltextindex keine Sucheigenschaftenliste zugeordnet ist. Um weitere Informationen zu dieser Such Eigenschaften Liste zu erhalten, verwenden Sie die [sys. registered_search_property_lists &#40;Transact-SQL-&#41;](../../relational-databases/system-catalog-views/sys-registered-search-property-lists-transact-sql.md) -Katalog Sicht.|  
  
## <a name="permissions"></a>Berechtigungen  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)]  
  
## <a name="examples"></a>Beispiele  
 Im folgenden Beispiel wird ein Volltextindex für die `HumanResources.JobCandidate`-Tabelle der `AdventureWorks2012`-Beispieldatenbank verwendet. Im Beispiel werden die für den Volltextindex verwendete Objekt-ID der Tabelle, die Sucheigenschaftenlisten-ID und die Stopplisten-ID der Stoppliste zurückgegeben.  
  
> [!NOTE]  
>  Das Codebeispiel, in dem dieser Volltextindex erstellt wird, finden Sie im Abschnitt "Beispiele" unter [CREATE FULLTEXT Index &#40;Transact-SQL&#41;](../../t-sql/statements/create-fulltext-index-transact-sql.md).  
  
```  
USE AdventureWorks2012;  
GO  
SELECT object_id, property_list_id, stoplist_id FROM sys.fulltext_indexes  
    where object_id = object_id('HumanResources.JobCandidate');   
GO  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [sys. fulltext_index_fragments &#40;Transact-SQL-&#41;](../../relational-databases/system-catalog-views/sys-fulltext-index-fragments-transact-sql.md)   
 [sys. fulltext_index_columns &#40;Transact-SQL-&#41;](../../relational-databases/system-catalog-views/sys-fulltext-index-columns-transact-sql.md)   
 [sys. fulltext_index_catalog_usages &#40;Transact-SQL-&#41;](../../relational-databases/system-catalog-views/sys-fulltext-index-catalog-usages-transact-sql.md)   
 [Katalogsichten für Objekte &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/object-catalog-views-transact-sql.md)   
 [Katalogsichten &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [Erstellen und Verwalten von Volltextindizes](../../relational-databases/search/create-and-manage-full-text-indexes.md)   
 [DROP FULLTEXT INDEX (Transact-SQL)](../../t-sql/statements/drop-fulltext-index-transact-sql.md)   
 [CREATE FULLTEXT INDEX &#40;Transact-SQL&#41;](../../t-sql/statements/create-fulltext-index-transact-sql.md)   
 [ALTER FULLTEXT INDEX &#40;Transact-SQL&#41;](../../t-sql/statements/alter-fulltext-index-transact-sql.md)  
  
  
