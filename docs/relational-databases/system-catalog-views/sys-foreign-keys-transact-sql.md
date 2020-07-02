---
title: sys. foreign_keys (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/15/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- foreign_keys
- sys.foreign_keys
- sys.foreign_keys_TSQL
- foreign_keys_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.foreign_keys catalog view
ms.assetid: e960df1a-13fc-43ee-ba91-34c1b719ac2c
author: CarlRabeler
ms.author: carlrab
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 725af9bc78fd0bd708ecd38c8c37cef629b19e63
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/01/2020
ms.locfileid: "85764761"
---
# <a name="sysforeign_keys-transact-sql"></a>sys.foreign_keys (Transact-SQL)
[!INCLUDE [sql-asdb-asdbmi-asdw-pdw](../../includes/applies-to-version/sql-asdb-asdbmi-asdw-pdw.md)]

  Enthält eine Zeile pro Objekt, bei der es sich um eine FOREIGN KEY-Einschränkung handelt, mit **sys. Object. Type** = F.  
  
|Spaltenname|Datentyp|BESCHREIBUNG|  
|-----------------|---------------|-----------------|  
|**\<Columns inherited from sys.objects>**||Eine Liste der Spalten, die diese Sicht erbt, finden Sie unter [sys. Objects &#40;Transact-SQL-&#41;](../../relational-databases/system-catalog-views/sys-objects-transact-sql.md).|  
|**referenced_object_id**|**int**|ID des Objekts, auf das verwiesen wird.|  
|**key_index_id**|**int**|ID des Schlüsselindexes innerhalb des Objekts, auf das verwiesen wird.|  
|**is_disabled**|**bit**|Die FOREIGN KEY-Einschränkung ist deaktiviert.|  
|**is_not_for_replication**|**bit**|Die FOREIGN KEY-Einschränkung wurde mithilfe der Option NOT FOR REPLICATION erstellt.|  
|**is_not_trusted**|**bit**|Die FOREIGN KEY-Einschränkung wurde nicht vom System überprüft.|  
|**delete_referential_action**|**tinyint**|Die referenzielle Aktion, die für den Fall eines Löschvorgangs für FOREIGN KEY deklariert wurde.<br /><br /> 0 = Keine Aktion<br /><br /> 1 = Überlappend<br /><br /> 2 = NULL festlegen<br /><br /> 3 = Standard festlegen|  
|**delete_referential_action_desc**|**nvarchar(60)**|Beschreibung der referenziellen Aktion, die für den Fall eines Löschvorgangs für FOREIGN KEY deklariert wurde:<br /><br /> NO_ACTION<br /><br /> CASCADE<br /><br /> SET_NULL<br /><br /> SET_DEFAULT|  
|**update_referential_action**|**tinyint**|Die referenzielle Aktion, die für den Fall eines Updatevorgangs für FOREIGN KEY deklariert wurde.<br /><br /> 0 = Keine Aktion<br /><br /> 1 = Überlappend<br /><br /> 2 = NULL festlegen<br /><br /> 3 = Standard festlegen|  
|**update_referential_action_desc**|**nvarchar(60)**|Beschreibung der referenziellen Aktion, die für den Fall eines Updatevorgangs für FOREIGN KEY deklariert wurde:<br /><br /> NO_ACTION<br /><br /> CASCADE<br /><br /> SET_NULL<br /><br /> SET_DEFAULT|  
|**is_system_named**|**bit**|1 = der Name wurde vom System generiert.<br /><br /> 0 = Der Name wurde vom Benutzer angegeben.|  
  
## <a name="permissions"></a>Berechtigungen  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] Weitere Informationen finden Sie unter [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="see-also"></a>Weitere Informationen  
 [Katalog Sichten &#40;Transact-SQL-&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [Objektkatalog Sichten &#40;Transact-SQL-&#41;](../../relational-databases/system-catalog-views/object-catalog-views-transact-sql.md)   
 [FAQ: Abfragen des SQL Server-Systemkatalogs](../../relational-databases/system-catalog-views/querying-the-sql-server-system-catalog-faq.md)  
  
  
