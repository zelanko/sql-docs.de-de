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
ms.openlocfilehash: 0c4468770227fff4915ed701f6973baeee3cc251
ms.sourcegitcommit: b57d98e9b2444348f95c83a24b8eea0e6c9da58d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/21/2020
ms.locfileid: "86552375"
---
# <a name="mssqlserver_10519"></a>MSSQLSERVER_10519
    
## <a name="details"></a>Details  
  
|attribute|Wert|  
|-|-|  
|Produktname|SQL Server|  
|Ereignis-ID|10519|  
|Ereignisquelle|MSSQLSERVER|  
|Komponente|SQLEngine|  
|Symbolischer Name|PG_INCOMPATIBLE_STMT_AND_HINTS|  
|Meldungstext|Die Planhinweisliste „%.\*ls“ kann nicht erstellt werden, weil die in `@hints` festgelegten Hinweise nicht auf die mit `@stmt` oder `@statement_start_offset` angegebene Anweisung angewendet werden können. Vergewissern Sie sich, dass die Hinweise auf die Anweisung angewendet werden können.|  
  
## <a name="explanation"></a>Erklärung  
 Die in `@hints` festgelegten Hinweise können nicht auf die mit `@stmt` oder `@statement_start_offset` angegebene Anweisung angewendet werden.  
  
## <a name="user-action"></a>Benutzeraktion  
 Legen Sie Hinweise fest, die auf die Anweisung angewendet werden können.  
  
## <a name="see-also"></a>Weitere Informationen  
 [sp_create_plan_guide &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-create-plan-guide-transact-sql)   
 [Plan Hinweis Listen](../performance/plan-guides.md)   
 [sp_create_plan_guide_from_handle &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-create-plan-guide-from-handle-transact-sql)  
  
  
