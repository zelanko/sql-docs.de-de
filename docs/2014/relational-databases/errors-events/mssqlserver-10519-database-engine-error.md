---
title: MSSQLSERVER_10519 | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 10519 (Database Engine error)
ms.assetid: 3be393a1-b186-41ae-afb9-a3d07ff354bb
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 6bb9c6f7fddc9ba0d4430b42ba5472a59c29e3cf
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "62916235"
---
# <a name="mssqlserver10519"></a>MSSQLSERVER_10519
    
## <a name="details"></a>Details  
  
|||  
|-|-|  
|Produktname|SQL Server|  
|Ereignis-ID|10519|  
|Ereignisquelle|MSSQLSERVER|  
|Komponente|SQLEngine|  
|Symbolischer Name|PG_INCOMPATIBLE_STMT_AND_HINTS|  
|Meldungstext|Die Planhinweisliste kann nicht erstellt werden kann ' %. \*ls, da die Hinweise in angegeben `@hints` nicht auf die durch eine angegebene Anweisung angewendet werden `@stmt` oder `@statement_start_offset`. Vergewissern Sie sich, dass die Hinweise auf die Anweisung angewendet werden können.|  
  
## <a name="explanation"></a>Erklärung  
 Die in `@hints` festgelegten Hinweise können nicht auf die mit `@stmt` oder `@statement_start_offset` angegebene Anweisung angewendet werden.  
  
## <a name="user-action"></a>Benutzeraktion  
 Legen Sie Hinweise fest, die auf die Anweisung angewendet werden können.  
  
## <a name="see-also"></a>Siehe auch  
 [sp_create_plan_guide &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-create-plan-guide-transact-sql)   
 [Planhinweislisten](../performance/plan-guides.md)   
 [sp_create_plan_guide_from_handle &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-create-plan-guide-from-handle-transact-sql)  
  
  
