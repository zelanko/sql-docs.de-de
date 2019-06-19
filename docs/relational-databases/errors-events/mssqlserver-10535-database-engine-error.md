---
title: MSSQLSERVER_10535 | Microsoft-Dokumentation
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: language-reference
helpviewer_keywords:
- 10535 (Database Engine error)
ms.assetid: 478fd978-11d9-4155-8329-f599fdbec14b
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 82331fa47dc7d692e7bcae5f9dfe57cd1f2735ed
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "62986016"
---
# <a name="mssqlserver10535"></a>MSSQLSERVER_10535
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>Details  
  
|||  
|-|-|  
|Produktname|SQL Server|  
|Ereignis-ID|10535|  
|Ereignisquelle|MSSQLSERVER|  
|Komponente|SQLEngine|  
|Symbolischer Name|PG_NO_PLAN|  
|Meldungstext|Die Planhinweisliste '%.*ls' kann nicht erstellt werden, weil kein Plan im entsprechenden Plancache für das Planhandle gefunden wurde. Geben Sie ein zwischengespeichertes Planhandle an. Fragen Sie die dynamische sys.dm_exec_query_stats-Verwaltungssicht ab, um eine Liste der zwischengespeicherten Planhandles zu erhalten.|  
  
## <a name="explanation"></a>Erklärung  
Es wurde kein Plan im Plancache gefunden, der dem angegebenen Planhandle entspricht.  
  
## <a name="user-action"></a>Benutzeraktion  
Geben Sie ein zwischengespeichertes Planhandle an. Fragen Sie die dynamische sys.dm_exec_query_stats-Verwaltungssicht ab, um eine Liste der zwischengespeicherten Planhandles zu erhalten.  
  
## <a name="see-also"></a>Weitere Informationen  
[sp_create_plan_guide_from_handle &#40;Transact-SQL&#41;](~/relational-databases/system-stored-procedures/sp-create-plan-guide-from-handle-transact-sql.md)  
[sys.dm_exec_query_stats &#40;Transact-SQL&#41;](~/relational-databases/system-dynamic-management-views/sys-dm-exec-query-stats-transact-sql.md)  
  
