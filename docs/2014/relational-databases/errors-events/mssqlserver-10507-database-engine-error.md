---
title: MSSQLSERVER_10507 | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 10507 (Database Engine error)
ms.assetid: cd83fa81-ac37-4eda-a3c3-17610b051de2
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 810419dede861e7447bfda9d50aea22ce8b2cf53
ms.sourcegitcommit: b57d98e9b2444348f95c83a24b8eea0e6c9da58d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/21/2020
ms.locfileid: "86552385"
---
# <a name="mssqlserver_10507"></a>MSSQLSERVER_10507
    
## <a name="details"></a>Details  
  
|attribute|Wert|  
|-|-|  
|Produktname|SQL Server|  
|Ereignis-ID|10507|  
|Ereignisquelle|MSSQLSERVER|  
|Komponente|SQLEngine|  
|Symbolischer Name|PG_STMT_DOES_NOT_MATCH|  
|Meldungstext|Die Planhinweisliste „%.\*ls“ kann nicht erstellt werden, weil die mit `@stmt` und `@module_or_batch` oder mit `@plan_handle` und `@statement_start_offset` angegebene Anweisung keiner Anweisung im festgelegten Modul oder Batch entspricht. Ändern Sie die Werte, um eine Übereinstimmung mit einer Anweisung im Modul oder Batch herzustellen.|  
  
## <a name="explanation"></a>Erklärung  
 Eine Anweisung im festgelegten Modul oder Batch konnte nicht der angegebenen Anweisung bzw. dem Offsetwert der Anweisung zugeordnet werden.  
  
## <a name="user-action"></a>Benutzeraktion  
 Ändern Sie die angegebenen Parameterwerte, um eine Übereinstimmung mit einer Anweisung im Modul oder Batch herzustellen.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Plan Hinweis Listen](../performance/plan-guides.md)   
 [sp_create_plan_guide &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-create-plan-guide-transact-sql)   
 [sp_create_plan_guide_from_handle &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-create-plan-guide-from-handle-transact-sql)  
  
  
