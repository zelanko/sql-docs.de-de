---
title: MSSQLSERVER_10531 | Microsoft-Dokumentation
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: errors-events
ms.reviewer: ''
ms.suite: sql
ms.technology: supportability
ms.tgt_pltfrm: ''
ms.topic: language-reference
helpviewer_keywords:
- 10531 (Database Engine error)
ms.assetid: bb40e994-231c-44ce-933f-8d767fb2f450
caps.latest.revision: 9
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 832d88857f2e303c99e4611981bd395a655e0c9a
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/04/2018
---
# <a name="mssqlserver10531"></a>MSSQLSERVER_10531
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>Details  
  
|||  
|-|-|  
|Produktname|SQL Server|  
|Ereignis-ID|10531|  
|Ereignisquelle|MSSQLSERVER|  
|Komponente|SQLEngine|  
|Symbolischer Name|PG_NO_ELIGIBLE_STMT|  
|Meldungstext|Die Planhinweisliste '%.*ls' kann nicht aus dem Cache erstellt werden, weil der Benutzer nicht über die erforderlichen Berechtigungen verfügt. Gewähren Sie dem Benutzer, der die Planhinweisliste erstellt, die VIEW SERVER STATE-Berechtigung.|  
  
## <a name="explanation"></a>Erklärung  
Der Benutzer verfügt nicht über die erforderlichen Berechtigungen zum Erstellen der angegebenen Planhinweisliste aus dem Plancache.  
  
## <a name="user-action"></a>Benutzeraktion  
Gewähren Sie dem Benutzer, der die Planhinweisliste erstellt, die Berechtigung „VIEW SERVER STATE“.  
  
## <a name="see-also"></a>Weitere Informationen finden Sie unter  
[Planhinweislisten](~/relational-databases/performance/plan-guides.md)  
[sp_create_plan_guide &#40;Transact-SQL&#41;](~/relational-databases/system-stored-procedures/sp-create-plan-guide-transact-sql.md)  
[sp_create_plan_guide_from_handle &#40;Transact-SQL&#41;](~/relational-databases/system-stored-procedures/sp-create-plan-guide-from-handle-transact-sql.md)  
  
