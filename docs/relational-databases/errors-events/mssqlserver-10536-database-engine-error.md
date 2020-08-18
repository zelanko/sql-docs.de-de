---
description: MSSQLSERVER_10536
title: MSSQLSERVER_10536 | Microsoft-Dokumentation
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: language-reference
helpviewer_keywords:
- 10536 (Database Engine error)
ms.assetid: 9f97b41f-0ef8-4ad2-aec0-906a5d7522ba
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: a22480940730da65e3274bd9d2fd6a74d72ae479
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88338036"
---
# <a name="mssqlserver_10536"></a>MSSQLSERVER_10536
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  
## <a name="details"></a>Details  
  
| attribute | Wert |  
| :-------- | :---- |  
|Produktname|SQL Server|  
|Ereignis-ID|10536|  
|Ereignisquelle|MSSQLSERVER|  
|Komponente|SQLEngine|  
|Symbolischer Name|PG_TOO_MANY_STMTS|  
|Meldungstext|Die Planhinweisliste „%.\*ls“ kann nicht erstellt werden, weil der entsprechende Batch bzw. das Modul für das angegebene **\@plan_handle** mehr als 1000 geeignete Anweisungen enthält. Erstellen Sie eine Planhinweisliste für jede Anweisung im Batch oder Modul, und geben Sie dabei einen **statement_start_offset**-Wert für jede Anweisung an.|  
  
## <a name="explanation"></a>Erklärung  
Der entsprechende Batch bzw. das Modul für das angegebene **\@plan_handle** enthält mehr als 1000 geeignete Anweisungen.  
  
## <a name="user-action"></a>Benutzeraktion  
Erstellen Sie eine Planhinweisliste für jede Anweisung im Batch oder Modul, und geben Sie dabei einen **statement_start_offset**-Wert für jede Anweisung an.  
  
## <a name="see-also"></a>Weitere Informationen  
[sp_create_plan_guide &#40;Transact-SQL&#41;](~/relational-databases/system-stored-procedures/sp-create-plan-guide-transact-sql.md)  
[Planhinweislisten](~/relational-databases/performance/plan-guides.md)  
[sp_create_plan_guide_from_handle &#40;Transact-SQL&#41;](~/relational-databases/system-stored-procedures/sp-create-plan-guide-from-handle-transact-sql.md)  
  
