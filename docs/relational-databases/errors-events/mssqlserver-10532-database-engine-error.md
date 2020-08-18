---
description: MSSQLSERVER_10532
title: MSSQLSERVER_10532 | Microsoft-Dokumentation
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: language-reference
helpviewer_keywords:
- 10532 (Database Engine error)
ms.assetid: 01da29ee-bf67-433f-8148-587a7e8d1d76
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: cb404a386558bb0fb0906ca3a0bd223a47c044a9
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88338846"
---
# <a name="mssqlserver_10532"></a>MSSQLSERVER_10532
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  
## <a name="details"></a>Details  
  
| attribute | Wert |  
| :-------- | :---- |  
|Produktname|SQL Server|  
|Ereignis-ID|10532|  
|Ereignisquelle|MSSQLSERVER|  
|Komponente|SQLEngine|  
|Symbolischer Name|PG_NO_ELIGIBLE_STMT|  
|Meldungstext|Die Planhinweisliste '%.\*ls' kann nicht erstellt werden, weil der mit **\@plan_handle** angegebene Batch bzw. das Modul keine geeignete Anweisung für eine Planhinweisliste enthält. Geben Sie einen anderen Wert für **\@plan_handle** an.|  
  
## <a name="explanation"></a>Erklärung  
Der mit **\@plan_handle** angegebene Batch bzw. das Modul enthält keine geeignete Anweisung für eine Planhinweisliste.  
  
## <a name="user-action"></a>Benutzeraktion  
Geben Sie einen anderen Wert für **\@plan_handle** an.  
  
## <a name="see-also"></a>Weitere Informationen  
[Planhinweislisten](~/relational-databases/performance/plan-guides.md)  
[sp_create_plan_guide &#40;Transact-SQL&#41;](~/relational-databases/system-stored-procedures/sp-create-plan-guide-transact-sql.md)  
[sp_create_plan_guide_from_handle &#40;Transact-SQL&#41;](~/relational-databases/system-stored-procedures/sp-create-plan-guide-from-handle-transact-sql.md)  
  
