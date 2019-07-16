---
title: resource_governor_workload_groups (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/16/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.resource_governor_workload_groups
- resource_governor_workload_groups_TSQL
- sys.resource_governor_workload_groups_TSQL
- resource_governor_workload_groups
dev_langs:
- TSQL
helpviewer_keywords:
- sys.resource_governor_workload_groups catalog view
ms.assetid: 619ba4b7-868f-4784-b527-ec1dfd703c4f
author: stevestein
ms.author: sstein
ms.openlocfilehash: d0f80d9ba8f5b5a1e81949d0fb2ea4b1d9bca59d
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "67904445"
---
# <a name="sysresourcegovernorworkloadgroups-transact-sql"></a>sys.resource_governor_workload_groups (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Gibt die gespeicherte Konfiguration der Arbeitsauslastungsgruppen in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] zurück. Jede Arbeitsauslastungsgruppe kann jeweils nur einen Ressourcenpool abonnieren.  
  
|Spaltenname|Datentyp|Beschreibung|  
|-----------------|---------------|-----------------|  
|group_id|**int**|Eindeutige ID der Arbeitsauslastungsgruppe Lässt keine NULL-Werte zu.|  
|NAME|**sysname**|Name der Arbeitsauslastungsgruppe. Lässt keine NULL-Werte zu.|  
|importance|**sysname**|**Hinweis**: Die Wichtigkeit gilt nur für Arbeitsauslastungsgruppen im gleichen Ressourcenpool.<br /><br /> Die relative Wichtigkeit einer Anforderung in dieser Arbeitsauslastungsgruppe. Für die Wichtigkeit sind folgende Einstellungen möglich, wobei MEDIUM die Standardeinstellung ist: NIEDRIG, MITTEL, HOCH.<br /><br /> Lässt keine NULL-Werte zu.|  
|request_max_memory_grant_percent|**int**|Angabe der maximalen Arbeitsspeicherzuweisung in Prozent für eine einzelne Anforderung. Der Standardwert ist 25. Lässt keine NULL-Werte zu.<br /><br /> **Hinweis**: Wenn diese Einstellung höher als 50 Prozent ist, werden es von große Abfragen einzeln nacheinander ausgeführt werden. Es gibt also höheres Risiko einen Out-of-Memory-Fehler während die Abfrage ausgeführt wird.|  
|request_max_cpu_time_sec|**int**|Maximaler CPU-Nutzungsgrenzwert für eine einzelne Anforderung in Sekunden. Der Standardwert 0 bedeutet, dass kein Grenzwert festgelegt ist. Lässt keine NULL-Werte zu.<br /><br /> **Hinweis**: Weitere Informationen finden Sie unter [CPU Threshold Exceeded (Ereignisklasse)](../../relational-databases/event-classes/cpu-threshold-exceeded-event-class.md).|  
|request_memory_grant_timeout_sec|**int**|Timeout für die Arbeitsspeicherzuweisung für eine einzelne Anforderung in Sekunden. Der Standardwert 0 verwendet eine interne Berechnung auf Basis der Abfragekosten. Lässt keine NULL-Werte zu.|  
|max_dop|**int**|Maximaler Grad der Parallelität für die Arbeitsauslastungsgruppe. Der Standardwert 0 verwendet globale Einstellungen. Lässt keine NULL-Werte zu.<br /><br /> **Knoten:** Diese Einstellung überschreibt die Abfrageoption **Maxdop**.|  
|group_max_requests|**int**|Maximale Anzahl gleichzeitiger Anforderungen. Der Standardwert 0 bedeutet, dass kein Grenzwert festgelegt ist. Lässt keine NULL-Werte zu.|  
|pool_id|**int**|ID des Ressourcenpools, den diese Arbeitsauslastungsgruppe verwendet.|  
|external_pool_id|**int**|**Gilt für**: [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] bis [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].<br /><br /> Die ID des externen Ressourcenpools, die diese Arbeitsauslastungsgruppe verwendet.|  
  
## <a name="remarks"></a>Hinweise  
 Die Katalogsicht zeigt die gespeicherten Metadaten an. Überprüfen die Konfiguration im Arbeitsspeicher, verwenden Sie die entsprechende dynamische verwaltungssicht [Sys. dm_resource_governor_workload_groups &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-resource-governor-workload-groups-transact-sql.md).  
  
 Die gespeicherte Konfiguration und die Konfiguration im Arbeitsspeicher können sich unterscheiden, wenn die Konfiguration der Ressourcenkontrolle geändert wurde, die ALTER RESOURCE GOVERNOR RECONFIGURE-Anweisung jedoch nicht angewendet wurde.  
  
## <a name="permissions"></a>Berechtigungen  
 Erfordert die VIEW ANY DEFINITION-Berechtigung, um Inhalte anzuzeigen, und erfordert die CONTROL SERVER-Berechtigung, um Inhalte zu ändern.  
  
## <a name="see-also"></a>Siehe auch  
 [sys.dm_resource_governor_workload_groups &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-resource-governor-workload-groups-transact-sql.md)   
 [Katalogsichten &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [Katalogsichten der Ressourcenkontrolle &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/resource-governor-catalog-views-transact-sql.md)  
  
  
