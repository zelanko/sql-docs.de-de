---
title: MSSQLSERVER_10539 | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 10539 (Database Engine error)
ms.assetid: 49c26ff7-18b8-4f07-a087-f45f63463b3b
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 18fafa113002b4a2420ac8784c48451a1d69aa56
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62916065"
---
# <a name="mssqlserver10539"></a>MSSQLSERVER_10539
    
## <a name="details"></a>Details  
  
|||  
|-|-|  
|Produktname|SQL Server|  
|Ereignis-ID|10539|  
|Ereignisquelle|MSSQLSERVER|  
|Komponente|SQLEngine|  
|Symbolischer Name|PG_NO_PLAN_FOR_STMT|  
|Meldungstext|Die Planhinweisliste '%.*ls' kann nicht aus dem Cache erstellt werden, weil kein Abfrageplan für die Anweisung mit dem Startoffset %d verfügbar ist. Dieses Problem kann auftreten, wenn die Anweisung von Datenbankobjekten abhängig ist, die noch nicht erstellt wurden. Stellen Sie sicher, dass alle erforderlichen Datenbankobjekte vorhanden sind, und führen Sie die Anweisung vor dem Erstellen der Planhinweisliste aus.|  
  
## <a name="explanation"></a>Erklärung  
 Im Plancache ist kein Abfrageplan für die Anweisung mit dem angegebenen Startoffset vorhanden.  
  
## <a name="user-action"></a>Benutzeraktion  
 Stellen Sie sicher, dass alle erforderlichen Datenbankobjekte vorhanden sind, und führen Sie die Anweisung vor dem Erstellen der Planhinweisliste aus.  
  
## <a name="see-also"></a>Siehe auch  
 [sp_create_plan_guide_from_handle &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-create-plan-guide-from-handle-transact-sql)  
  
  
