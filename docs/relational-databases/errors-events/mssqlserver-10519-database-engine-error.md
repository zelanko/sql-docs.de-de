---
description: MSSQLSERVER_10519
title: MSSQLSERVER_10519 | Microsoft-Dokumentation
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: language-reference
helpviewer_keywords:
- 10519 (Database Engine error)
ms.assetid: 3be393a1-b186-41ae-afb9-a3d07ff354bb
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: dbb694019769896c1af7d461a8c549f1fd7df696
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88338916"
---
# <a name="mssqlserver_10519"></a>MSSQLSERVER_10519
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  
## <a name="details"></a>Details  
  
| attribute | Wert |  
| :-------- | :---- |  
|Produktname|SQL Server|  
|Ereignis-ID|10519|  
|Ereignisquelle|MSSQLSERVER|  
|Komponente|SQLEngine|  
|Symbolischer Name|PG_INCOMPATIBLE_STMT_AND_HINTS|  
|Meldungstext|Die Planhinweisliste '%.\*ls' kann nicht erstellt werden, weil die in **\@hints** festgelegten Hinweise nicht auf die mit **\@stmt** oder **\@statement_start_offset** angegebene Anweisung angewendet werden können. Vergewissern Sie sich, dass die Hinweise auf die Anweisung angewendet werden können.|  
  
## <a name="explanation"></a>Erklärung  
Die in **\@hints** festgelegten Hinweise können nicht auf die mit **\@stmt** oder **\@statement_start_offset** angegebene Anweisung angewendet werden.  
  
## <a name="user-action"></a>Benutzeraktion  
Legen Sie Hinweise fest, die auf die Anweisung angewendet werden können.  
  
## <a name="see-also"></a>Weitere Informationen  
[sp_create_plan_guide &#40;Transact-SQL&#41;](~/relational-databases/system-stored-procedures/sp-create-plan-guide-transact-sql.md)  
[Planhinweislisten](~/relational-databases/performance/plan-guides.md)  
[sp_create_plan_guide_from_handle &#40;Transact-SQL&#41;](~/relational-databases/system-stored-procedures/sp-create-plan-guide-from-handle-transact-sql.md)  
  
