---
title: MSSQLSERVER_10532 | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: supportability
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- 10532 (Database Engine error)
ms.assetid: 01da29ee-bf67-433f-8148-587a7e8d1d76
caps.latest.revision: 10
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: be808412900aed583450824dca873deea4697f40
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/03/2018
ms.locfileid: "37409478"
---
# <a name="mssqlserver10532"></a>MSSQLSERVER_10532
    
## <a name="details"></a>Details  
  
|||  
|-|-|  
|Produktname|SQL Server|  
|Ereignis-ID|10532|  
|Ereignisquelle|MSSQLSERVER|  
|Komponente|SQLEngine|  
|Symbolischer Name|PG_NO_ELIGIBLE_STMT|  
|Meldungstext|Die Planhinweisliste kann nicht erstellt werden kann ' %. \*ls, da der Batch bzw. das Modul angegeben `@plan_handle` enthält keine geeignete Anweisung für eine Planhinweisliste. Geben Sie einen anderen Wert für `@plan_handle` an.|  
  
## <a name="explanation"></a>Erklärung  
 Der mit `@plan_handle` angegebene Batch bzw. das Modul enthält keine geeignete Anweisung für eine Planhinweisliste.  
  
## <a name="user-action"></a>Benutzeraktion  
 Geben Sie einen anderen Wert für `@plan_handle` an.  
  
## <a name="see-also"></a>Siehe auch  
 [Planhinweislisten](../performance/plan-guides.md)   
 [sp_create_plan_guide &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-create-plan-guide-transact-sql)   
 [sp_create_plan_guide_from_handle &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-create-plan-guide-from-handle-transact-sql)  
  
  
