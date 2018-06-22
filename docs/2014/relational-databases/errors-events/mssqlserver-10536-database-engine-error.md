---
title: MSSQLSERVER_10536 | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- 10536 (Database Engine error)
ms.assetid: 9f97b41f-0ef8-4ad2-aec0-906a5d7522ba
caps.latest.revision: 10
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.openlocfilehash: ffa9509c55632c5f041f060c499be0a8bc7cbf4b
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36047830"
---
# <a name="mssqlserver10536"></a>MSSQLSERVER_10536
    
## <a name="details"></a>Details  
  
|||  
|-|-|  
|Produktname|SQL Server|  
|Ereignis-ID|10536|  
|Ereignisquelle|MSSQLSERVER|  
|Komponente|SQLEngine|  
|Symbolischer Name|PG_TOO_MANY_STMTS|  
|Meldungstext|Kann nicht erstellt werden Planhinweisliste ' %. \*%.*ls'-Datenbank da des Batches oder Moduls, die der angegebenen `@plan_handle` mehr als 1000 geeignete Anweisungen enthält. Erstellen Sie eine Planhinweisliste für jede Anweisung im Batch oder Modul, und geben Sie dabei einen `statement_start_offset`-Wert für jede Anweisung an.|  
  
## <a name="explanation"></a>Erklärung  
 Der entsprechende Batch bzw. das Modul für das angegebene `@plan_handle` enthält mehr als 1000 geeignete Anweisungen.  
  
## <a name="user-action"></a>Benutzeraktion  
 Erstellen Sie eine Planhinweisliste für jede Anweisung im Batch oder Modul, und geben Sie dabei einen `statement_start_offset`-Wert für jede Anweisung an.  
  
## <a name="see-also"></a>Siehe auch  
 [sp_create_plan_guide &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-create-plan-guide-transact-sql)   
 [Planhinweislisten](../performance/plan-guides.md)   
 [sp_create_plan_guide_from_handle &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-create-plan-guide-from-handle-transact-sql)  
  
  
