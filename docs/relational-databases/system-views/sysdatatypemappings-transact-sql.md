---
title: sysdatatypeer Mappings (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sysdatatypemappings
- sysdatatypemappings_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sysdatatypemappings view
ms.assetid: 5dfafb70-3e3d-4465-b293-1acff1f855b6
author: stevestein
ms.author: sstein
ms.openlocfilehash: 3d58525ec4bcedc4249466be93628a7c1baa21bc
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "67910138"
---
# <a name="sysdatatypemappings-transact-sql"></a>sysdatatypemappings (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Mit der **sysdatatypemappings** -Sicht wird die Zuordnung zwischen SQL Server-Datentypen und Datentypen eines Nicht-SQL Server-Datenbank-Managementsystems (DBMS) angezeigt. Diese Sicht wird in der **msdb** -Datenbank gespeichert.  
  
|Spaltenname|Datentyp|BESCHREIBUNG|  
|-----------------|---------------|-----------------|  
|**mapping_id**|**int**|Die ID der Datentypzuordnung.|  
|**source_dbms**|**sysname**|Gibt den Namen des DBMS an, aus dem die Datentypen zugeordnet werden, wobei die folgenden Werte möglich sind:<br /><br /> **MSSQLSERVER** = die Quelle ist eine SQL Server Datenbank.<br /><br /> **Oracle** = die Quelle ist eine Oracle-Datenbank.|  
|**source_version**|**sysname**|Gibt die Produktversion des Quell-DBMS an.|  
|**source_type**|**sysname**|Gibt den im Quell-DBMS aufgelisteten Datentyp an.|  
|**source_length_min**|**BIGINT**|Die Mindestlänge des Datentyps im Quell-DBMS, wobei der Wert NULL angibt, dass die Länge nicht verwendet wird.|  
|**source_length_max**|**BIGINT**|Die maximale Länge des Datentyps im Quell-DBMS, wobei der Wert NULL angibt, dass die Länge nicht verwendet wird.|  
|**source_precision_min**|**BIGINT**|Die Mindestgenauigkeit des Datentyps im Quell-DBMS, wobei der Wert NULL angibt, dass die Genauigkeit nicht verwendet wird.|  
|**source_precision_max**|**BIGINT**|Die maximale Genauigkeit des Datentyps im Quell-DBMS, wobei der Wert NULL angibt, dass die Genauigkeit nicht verwendet wird.|  
|**source_scale_min**|**int**|Die Mindestdezimalstellen des Datentyps im Quell-DBMS, wobei der Wert NULL angibt, dass die Dezimalstellen nicht verwendet werden.|  
|**source_scale_max**|**int**|Die maximalen Dezimalstellen des Datentyps im Quell-DBMS, wobei der Wert NULL angibt, dass die Dezimalstellen nicht verwendet werden.|  
|**source_nullable**|**bit**|Gibt an, ob der Zieldatentyp NULL-Werte unterstützt.|  
|**source_createparams**|**int**|Nur interne Verwendung.|  
|**destination_dbms**|**sysname**|Gibt den Namen des Ziel-DBMS an, wobei die folgenden Werte möglich sind:<br /><br /> **MSSQLSERVER** = das Ziel ist eine SQL Server Datenbank.<br /><br /> **Oracle** = das Ziel ist eine Oracle-Datenbank.<br /><br /> **DB2** = das Ziel ist eine IBM DB2-Datenbank.<br /><br /> **Sybase** = das Ziel ist eine Sybase-Datenbank.|  
|**destination_version**|**sysname**|Die Produktversion des Ziel-DBMS.|  
|**destination_type**|**sysname**|Der Datentyp im Ziel-DBMS.|  
|**destination_length**|**BIGINT**|Die Länge des Datentyps im Ziel-DBMS.|  
|**destination_precision**|**BIGINT**|Die Genauigkeit des Datentyps im Ziel-DBMS.|  
|**destination_scale**|**int**|Die Dezimalstellen des Datentyps im Ziel-DBMS.|  
|**destination_nullable**|**bit**|Gibt an, ob der Datentyp im Ziel-DBMS NULL-Werte unterstützt.|  
|**destination_createparams**|**int**|Nur interne Verwendung.|  
|**Datenverlust**|**bit**|Gibt an, ob beim Zuordnen zwischen dem Datentyp des Quell- und Ziel-DBMS Daten verloren gehen.|  
|**is_default**|**bit**|Gibt an, ob standardmäßig die Datentypzuordnung verwendet wird.|  
  
## <a name="see-also"></a>Weitere Informationen  
 [Heterogene Datenbankreplikation](../../relational-databases/replication/non-sql/heterogeneous-database-replication.md)   
 [Replikations Tabellen &#40;Transact-SQL-&#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [Replikations Sichten &#40;Transact-SQL-&#41;](../../relational-databases/system-views/replication-views-transact-sql.md)   
 [sp_helpdatatypemap &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-helpdatatypemap-transact-sql.md)  
  
  
