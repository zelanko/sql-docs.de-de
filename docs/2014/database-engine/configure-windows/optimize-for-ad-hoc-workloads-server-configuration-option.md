---
title: Für Ad-hoc-Arbeitsauslastungen optimieren (Serverkonfigurationsoption) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- optimize for ad hoc workloads option
ms.assetid: 0972e028-3a8e-454b-a186-e814a1d431f2
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 7edf279b49374823c9083005be9b8d047b003f62
ms.sourcegitcommit: 04dd0620202287869b23cc2fde998a18d3200c66
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/30/2018
ms.locfileid: "52640251"
---
# <a name="optimize-for-ad-hoc-workloads-server-configuration-option"></a>Für Ad-hoc-Arbeitsauslastungen optimieren (Serverkonfigurationsoption)
  Die Option **Optimieren für Ad-hoc-Arbeitsauslastung** wird zum Verbessern der Effizienz des Plancaches für Arbeitsauslastungen verwendet, die viele Ad-hoc-Batches für die einmalige Verwendung enthalten. Wenn diese Option auf 1 festgelegt ist, speichert [!INCLUDE[ssDE](../../includes/ssde-md.md)] statt des vollständigen kompilierten Plans einen kleinen Stub des kompilierten Plans in dem Plancache, wenn ein Batch erstmalig ausgeführt wird. Dadurch wird die Auslastung des Arbeitsspeichers reduziert, indem verhindert wird, dass der Plancache mit kompilierten Plänen gefüllt wird, die nicht wiederverwendet werden.  
  
 Der Stub des kompilierten Plans ermöglicht [!INCLUDE[ssDE](../../includes/ssde-md.md)] zu erkennen, dass dieser Ad-hoc-Batch bereits kompiliert worden ist, jedoch nur ein Stub des kompilierten Plans gespeichert worden ist, sodass [!INCLUDE[ssDE](../../includes/ssde-md.md)] den Batch kompiliert, wenn er erneut aufgerufen (kompiliert oder ausgeführt) wird, dann den Stub des kompilierten Plans aus dem Plancache entfernt und den vollständigen kompilierten Plan zum Plancache hinzufügt.  
  
 Wenn **Optimieren für Ad-hoc-Arbeitsauslastungen** auf 1 festgelegt wird, wirkt sich dies ausschließlich auf neue Pläne aus. Pläne, die sich bereits im Plancache befinden, sind davon nicht betroffen.  
  
 Der Stub des kompilierten Plans ist einer der cacheobjtypes, die von der sys.dm_exec_cached_plans-Katalogsicht angezeigt werden. Er verfügt über einen eindeutigen SQL-Handle und Planhandle. Dem Stub des kompilierten Plans ist kein Ausführungsplan zugeordnet, und die Abfrage des Planhandles gibt keinen XML-Showplan zurück.  
  
 Ablaufverfolgungsflag 8032 setzt die Cachelimitparameter auf die RTM-Einstellung von [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] zurück, die im Allgemeinen einen größeren Cache zulässt. Verwenden Sie diese Einstellung, wenn häufig wiederverwendete Cacheeinträge nicht in den Cache passen, und wenn das Problem mit dem Plancache durch die *Serverkonfigurations-Option Optimierung für Ad-hoc-Arbeitsauslastung* nicht behoben werden konnte.  
  
> [!WARNING]  
>  Ablaufverfolgungsflag 8032 kann die Leistung mindern, wenn große Caches weniger Arbeitsspeicher für andere Arbeitsspeicherconsumer, z. B. den Pufferpool, verfügbar machen.  
  
## <a name="see-also"></a>Siehe auch  
 [sys.dm_exec_cached_plans &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-exec-cached-plans-transact-sql)   
 [Serverkonfigurationsoptionen &#40;SQL Server&#41;](server-configuration-options-sql-server.md)  
  
  
