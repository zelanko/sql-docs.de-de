---
title: MSSQLSERVER_10538 | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 10538 (Database Engine error)
ms.assetid: 284d19b4-4979-4cbe-a9be-ac1104433c69
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: aa6bce659e20fb80f013539049cc1b99e3e0b4c1
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "62870646"
---
# <a name="mssqlserver10538"></a>MSSQLSERVER_10538
    
## <a name="details"></a>Details  
  
|||  
|-|-|  
|Produktname|SQL Server|  
|Ereignis-ID|10538|  
|Ereignisquelle|MSSQLSERVER|  
|Komponente|SQLEngine|  
|Symbolischer Name|PG_INVALID_PLANGUIDE_HANDLE|  
|Meldungstext|Die Planhinweisliste wurde nicht gefunden, weil die angegebene Planhinweislisten-ID NULL oder ungültig ist oder weil Sie keine Berechtigung für das Objekt besitzen, auf das die Planhinweisliste verweist. Vergewissern Sie sich, dass die Planhinweislisten-ID gültig ist, die aktuelle Sitzung auf den korrekten Datenbankkontext eingestellt ist und Sie entweder die ALTER DATABASE-Berechtigung oder die ALTER-Berechtigung für das Objekt besitzen, auf das die Planhinweisliste verweist.|  
  
## <a name="explanation"></a>Erklärung  
 Die ID der angegebenen Planhinweisliste ist NULL oder ungültig, oder Sie besitzen nicht die Berechtigung für das Objekt, auf das die Planhinweisliste verweist.  
  
## <a name="user-action"></a>Benutzeraktion  
 Vergewissern Sie sich, dass die Planhinweislisten-ID gültig, die aktuelle Sitzung auf den korrekten Datenbankkontext eingestellt ist und Sie die ALTER DATABASE-Berechtigung oder die ALTER-Berechtigung für das Objekt besitzen, auf das die Planhinweisliste verweist.  
  
## <a name="see-also"></a>Siehe auch  
 [sp_create_plan_guide &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-create-plan-guide-transact-sql)   
 [Planhinweislisten](../performance/plan-guides.md)   
 [sp_create_plan_guide_from_handle &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-create-plan-guide-from-handle-transact-sql)  
  
  
