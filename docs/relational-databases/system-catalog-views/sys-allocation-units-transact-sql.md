---
title: Sys. allocation_units (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.allocation_units_TSQL
- sys.allocation_units
- allocation_units_TSQL
- allocation_units
dev_langs:
- TSQL
helpviewer_keywords:
- sys.allocation_units catalog view
ms.assetid: ec9de780-68fd-4551-b70b-2d3ab3709b3e
author: stevestein
ms.author: sstein
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 73ee5d7ac8bd512b69cc187f9860b9e7f2c38a78
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68001294"
---
# <a name="sysallocationunits-transact-sql"></a>sys.allocation_units (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Enthält eine Zeile für jede Zuordnungseinheit in der Datenbank.  
  
|Spaltenname|Datentyp|Beschreibung|  
|-----------------|---------------|-----------------|  
|allocation_unit_id|**bigint**|ID der Zuordnungseinheit. Ist innerhalb einer Datenbank eindeutig.|  
|Typ|**tinyint**|Typ der Zuordnungseinheit:<br /><br /> 0 = Gelöscht<br /><br /> 1 = Daten in Zeilen (alle Datentypen mit Ausnahme von LOB-Datentypen)<br /><br /> 2 = LOB-Daten (Large Object) (**text**, **ntext**, **image**, **xml**, große Werttypen und benutzerdefinierte CLR-Typen)<br /><br /> 3 = Zeilenüberlaufdaten|  
|type_desc|**nvarchar(60)**|Beschreibung des Typs der Zuordnungseinheit:<br /><br /> **GELÖSCHT**<br /><br /> **IN_ROW_DATA**<br /><br /> **LOB_DATA**<br /><br /> **ROW_OVERFLOW_DATA**|  
|container_id|**bigint**|ID des Speichercontainers, der der Zuordnungseinheit zugeordnet ist.<br /><br /> Wenn Typ = 1 oder 3, Container_id hobt_id =.<br /><br /> Wenn Typ 2, und klicken Sie dann auf Container_id = partition_id.<br /><br /> 0 = Für die verzögerte Löschung gekennzeichnete Zuordnungseinheit|  
|data_space_id|**int**|ID der Dateigruppe, in der sich diese Zuordnungseinheit befindet.|  
|total_pages|**bigint**|Gesamtanzahl der Seiten, die von dieser Zuordnungseinheit zugeordnet oder reserviert wurden.|  
|used_pages|**bigint**|Gesamtanzahl der tatsächlich verwendeten Seiten.|  
|data_pages|**bigint**|Anzahl verwendeter Seiten, die über Folgendes verfügen:<br /><br /> Daten in Zeilen<br /><br /> LOB-Daten<br /><br /> Zeilenüberlaufdaten<br /><br /> <br /><br /> Beachten Sie, die der zurückgegebene Wert schließt interne Indexseiten und zuordnungsverwaltungsseiten aus.|  
  
> [!NOTE]  
>  Wenn Sie große Indizes löschen oder neu erstellen bzw. wenn Sie große Tabellen löschen oder abschneiden, verzögert [!INCLUDE[ssDE](../../includes/ssde-md.md)] die Aufhebung der aktuellen Seitenzuordnungen sowie die zugehörigen Sperren, bis für die Transaktion ein Commit ausgeführt wird. Bei verzögerten Löschvorgängen wird der zugeordnete Speicherplatz nicht sofort freigegeben. Aus diesem Grund können die von Sys. allocation_units sofort nach dem Löschen oder Abschneiden eines großen Objekts zurückgegebenen Werte nicht den tatsächlich verfügbaren Speicherplatz wider.  
  
## <a name="permissions"></a>Berechtigungen  
 Erfordert die Mitgliedschaft in der **public** -Rolle. Weitere Informationen finden Sie unter [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="see-also"></a>Siehe auch  
 [sys.partitions &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-partitions-transact-sql.md)   
 [Katalogsichten für Objekte &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/object-catalog-views-transact-sql.md)   
 [Katalogsichten &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)  
  
  
