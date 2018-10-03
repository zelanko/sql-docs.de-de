---
title: resource_governor_resource_pools (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 08/09/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.resource_governor_resource_pools
- resource_governor_resource_pools
- sys.resource_governor_resource_pools_TSQL
- resource_governor_resource_pools_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.resource_governor_resource_pools catalog view
ms.assetid: 56793e9c-aa90-452e-88c6-d9b799239888
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 87392911d8fa393777e1b2d7b9e5bec1c416e939
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47755828"
---
# <a name="sysresourcegovernorresourcepools-transact-sql"></a>sys.resource_governor_resource_pools (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Gibt die gespeicherte Konfiguration der Ressourcenpools in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] zurück. Jede Zeile der Sicht bestimmt die Konfiguration eines Pools.  
  
|Spaltenname|Datentyp|Description|  
|-----------------|---------------|-----------------|  
|pool_id|**int**|Eindeutige ID des Ressourcenpools. Lässt keine NULL-Werte zu.|  
|NAME|**sysname**|Name des Ressourcenpools. Lässt keine NULL-Werte zu.|  
|min_cpu_percent|**int**|Garantierte durchschnittliche CPU-Bandbreite für alle Anforderungen im Ressourcenpool, wenn CPU-Konflikte bestehen. Lässt keine NULL-Werte zu.|  
|max_cpu_percent|**int**|Maximal zulässige durchschnittliche CPU-Bandbreite für alle Anforderungen im Ressourcenpool an, wenn CPU-Konflikte bestehen. Lässt keine NULL-Werte zu.|  
|min_memory_percent|**int**|Garantierte Arbeitsspeichermenge für alle Anforderungen im Ressourcenpool. Dieser Arbeitsspeicher wird nicht mit anderen Ressourcenpools gemeinsam genutzt. Lässt keine NULL-Werte zu.|  
|max_memory_percent|**int**|Prozentsatz des gesamten Serverspeichers, der für Anforderungen in diesem Ressourcenpool verwendet werden kann. Lässt keine NULL-Werte zu. Der geltende Höchstwert hängt von den Pool-Mindestwerten ab. So kann für max_memory_percent beispielsweise 100 festgelegt sein, aber der geltende Höchstwert ist niedriger.|  
|cap_cpu_percent|**int**|**Gilt für**: [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] bis [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].<br /><br /> Feste Obergrenze der CPU-Bandbreite, die allen Anforderungen im Ressourcenpool zugewiesen wird. Beschränkt die maximale CPU-Bandbreite auf die angegebene Stufe. Der zulässige Bereich für den Wert ist 1 bis 100.|  
|min_iops_per_volume|**int**|**Gilt für**: [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] bis [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].<br /><br /> Die minimalen E/A-Vorgänge pro Sekunde (IOPS) pro Volumeeinstellung für diesen Pool. 0 = keine Reservierung. Lässt keine NULL-Werte zu.|  
|max_iops_per_volume|**int**|**Gilt für**: [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] bis [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].<br /><br /> Die maximalen E/A-Vorgänge pro Sekunde (IOPS) pro Volumeeinstellung für diesen Pool. 0 = unbegrenzt. Lässt keine NULL-Werte zu.|  
  
## <a name="remarks"></a>Hinweise  
 Die Katalogsicht zeigt die gespeicherten Metadaten an. Überprüfen die Konfiguration im Arbeitsspeicher, verwenden Sie die entsprechende dynamische verwaltungssicht [Sys. dm_resource_governor_resource_pools &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-resource-governor-resource-pools-transact-sql.md).  
  
## <a name="permissions"></a>Berechtigungen  
 Erfordert die VIEW ANY DEFINITION-Berechtigung, um Inhalte anzuzeigen, und erfordert die CONTROL SERVER-Berechtigung, um Inhalte zu ändern.  
  
## <a name="see-also"></a>Siehe auch  
 [Katalogsichten der Ressourcenkontrolle &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/resource-governor-catalog-views-transact-sql.md)   
 [Sys. dm_resource_governor_resource_pools &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-resource-governor-resource-pools-transact-sql.md)   
 [Resource Governor](../../relational-databases/resource-governor/resource-governor.md)   
 [sys.resource_governor_external_resource_pools &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-resource-governor-external-resource-pools-transact-sql.md)  
  
  
