---
title: sys. all_views (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.all_views_TSQL
- sys.all_views
- all_views
- all_views_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.all_views catalog view
ms.assetid: d8829213-fce2-41c6-9ab2-aaab5836c941
author: stevestein
ms.author: sstein
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 8931b3885df642fc4fbd076b18c4375a48c2b32b
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "68001310"
---
# <a name="sysall_views-transact-sql"></a>sys.all_views (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Zeigt die Verknüpfung (UNION) aller benutzerdefinierten und Systemsichten an.  
  
|Spaltenname|Datentyp|BESCHREIBUNG|  
|-----------------|---------------|-----------------|  
|**\<geerbte Spalten>**||Eine Liste der Spalten, die diese Sicht erbt, finden Sie unter [sys. Objects &#40;Transact-SQL-&#41;](../../relational-databases/system-catalog-views/sys-objects-transact-sql.md).|  
|**is_replicated**|**bit**|1 = Sicht ist repliziert.|  
|**has_replication_filter**|**bit**|1 = Sicht verfügt über einen Replikationsfilter.|  
|**has_opaque_metadata**|**bit**|1 = VIEW_METADATA-Option wurde für die Sicht angegeben. Weitere Informationen finden Sie unter [CREATE VIEW &#40;Transact-SQL&#41;](../../t-sql/statements/create-view-transact-sql.md).|  
|**has_unchecked_assembly_data**|**bit**|1 = Die Tabelle enthält persistente Daten, die von einer Assembly abhängen, deren Definition bei der letzten ALTER ASSEMBLY-Anweisung geändert wurde. Wird nach dem nächsten erfolgreichen DBCC CHECKDB oder DBCC CHECKTABLE auf 0 zurückgesetzt.|  
|**with_check_option**|**bit**|1 = WITH CHECK OPTION wurde in der Sichtdefinition angegeben.|  
|**is_date_correlation_view**|**bit**|1 = Sicht wurde vom System automatisch zum Speichern von Korrelationsinformationen zwischen datetime-Spalten erstellt. Die Erstellung dieser Ansicht wurde durch Festlegen von DATE_CORRELATION_OPTIMIZATION auf **on**aktiviert.|  
  
## <a name="permissions"></a>Berechtigungen  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] Weitere Informationen finden Sie unter [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="see-also"></a>Weitere Informationen  
 [Objektkatalog Sichten &#40;Transact-SQL-&#41;](../../relational-databases/system-catalog-views/object-catalog-views-transact-sql.md)   
 [Katalogsichten &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [DBCC CHECKDB &#40;Transact-SQL-&#41;](../../t-sql/database-console-commands/dbcc-checkdb-transact-sql.md)   
 [Alter Assembly &#40;Transact-SQL-&#41;](../../t-sql/statements/alter-assembly-transact-sql.md)   
 [DBCC CHECKTABLE &#40;Transact-SQL&#41;](../../t-sql/database-console-commands/dbcc-checktable-transact-sql.md)  
  
  
