---
title: MSSQLSERVER_10532 | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 10532 (Database Engine error)
ms.assetid: 01da29ee-bf67-433f-8148-587a7e8d1d76
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 26ab34c319eff62737eae337828247fdfd7e901b
ms.sourcegitcommit: f71e523da72019de81a8bd5a0394a62f7f76ea20
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/17/2020
ms.locfileid: "84968140"
---
# <a name="mssqlserver_10532"></a>MSSQLSERVER_10532
    
## <a name="details"></a>Details  
  
|||  
|-|-|  
|Produktname|SQL Server|  
|Ereignis-ID|10532|  
|Ereignisquelle|MSSQLSERVER|  
|Komponente|SQLEngine|  
|Symbolischer Name|PG_NO_ELIGIBLE_STMT|  
|Meldungstext|Die Planhinweisliste „%.\*ls“ kann nicht erstellt werden, weil der mit `@plan_handle` angegebene Batch bzw. das Modul keine geeignete Anweisung für eine Planhinweisliste enthält. Geben Sie einen anderen Wert für `@plan_handle` an.|  
  
## <a name="explanation"></a>Erklärung  
 Der mit `@plan_handle` angegebene Batch bzw. das Modul enthält keine geeignete Anweisung für eine Planhinweisliste.  
  
## <a name="user-action"></a>Benutzeraktion  
 Geben Sie einen anderen Wert für `@plan_handle` an.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Plan Hinweis Listen](../performance/plan-guides.md)   
 [sp_create_plan_guide &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-create-plan-guide-transact-sql)   
 [sp_create_plan_guide_from_handle &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-create-plan-guide-from-handle-transact-sql)  
  
  
