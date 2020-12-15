---
description: sys.fulltext_index_columns (Transact-SQL)
title: sys.fulltext_index_columns (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.fulltext_index_columns
- fulltext_index_columns
- sys.fulltext_index_columns_TSQL
- fulltext_index_columns_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- full-text indexes [SQL Server], columns
- sys.fulltext_index_columns catalog view
- full-text indexes [SQL Server], properties
ms.assetid: c34b8625-e53c-4281-ace6-d46230d5cb84
author: pmasl
ms.author: pelopes
ms.reviewer: mikeray
monikerRange: =azuresqldb-current||>=sql-server-2016||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: c514fbfd5d82038995bb6db006a9013c28674202
ms.sourcegitcommit: 1a544cf4dd2720b124c3697d1e62ae7741db757c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/14/2020
ms.locfileid: "97472981"
---
# <a name="sysfulltext_index_columns-transact-sql"></a>sys.fulltext_index_columns (Transact-SQL)

[!INCLUDE [SQL Server SQL Database](../../includes/applies-to-version/sql-asdb.md)]

  Enthält eine Zeile für jede Spalte, die Teil eines Volltextindexes ist.    
 
|Spaltenname|Datentyp|Beschreibung|  
|-----------------|---------------|-----------------|  
|**object_id**|**int**|ID des Objekts, dessen Teil dies ist.|  
|**column_id**|**int**|ID der Spalte, die Teil des Volltextindexes ist.|  
|**type_column_id**|**int**|ID der Typspalte, in der die vom Benutzer bereitgestellte Dokument Dateierweiterung (". doc", ". xls" usw.) des Dokuments in einer bestimmten Zeile gespeichert wird. Die Typspalte wird nur für Spalten angegeben, deren Daten während der Volltextindizierung eine Filterung erfordern. Dieser Wert ist NULL, falls dies nicht verfügbar ist. Weitere Informationen finden Sie unter [Konfigurieren und Verwalten von Filtern für die Suche](../../relational-databases/search/configure-and-manage-filters-for-search.md).|  
|**language_id**|**int**|LCID der Sprache, deren Wörtertrennung zum Indizieren dieser Volltextspalte verwendet wird.<br /><br /> 0 = Neutral.<br /><br /> Weitere Informationen finden Sie unter [sys.fulltext_languages &#40;Transact-SQL-&#41;](../../relational-databases/system-catalog-views/sys-fulltext-languages-transact-sql.md).|  
|**statistical_semantics**|**int**|1 = Für diese Spalte ist die statistische Semantik zusätzlich zur Volltextindizierung aktiviert.|  
  
## <a name="permissions"></a>Berechtigungen  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)]  
  
## <a name="see-also"></a>Weitere Informationen  
 [Katalogsichten für Objekte &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/object-catalog-views-transact-sql.md)   
 [Katalogsichten &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)  
  
  
