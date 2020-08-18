---
description: MSSQLSERVER_10538
title: MSSQLSERVER_10538 | Microsoft-Dokumentation
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: language-reference
helpviewer_keywords:
- 10538 (Database Engine error)
ms.assetid: 284d19b4-4979-4cbe-a9be-ac1104433c69
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: b938580c448f0073784e58763d35f4a795317c44
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88338196"
---
# <a name="mssqlserver_10538"></a>MSSQLSERVER_10538
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  
## <a name="details"></a>Details  
  
| attribute | Wert |  
| :-------- | :---- |  
|Produktname|SQL Server|  
|Ereignis-ID|10538|  
|Ereignisquelle|MSSQLSERVER|  
|Komponente|SQLEngine|  
|Symbolischer Name|PG_INVALID_PLANGUIDE_HANDLE|  
|Meldungstext|Die Planhinweisliste wurde nicht gefunden, weil die angegebene Planhinweislisten-ID NULL oder ungültig ist oder weil Sie keine Berechtigung für das Objekt besitzen, auf das die Planhinweisliste verweist. Vergewissern Sie sich, dass die Planhinweislisten-ID gültig ist, die aktuelle Sitzung auf den korrekten Datenbankkontext eingestellt ist und Sie entweder die ALTER DATABASE-Berechtigung oder die ALTER-Berechtigung für das Objekt besitzen, auf das die Planhinweisliste verweist.|  
  
## <a name="explanation"></a>Erklärung  
Die ID der angegebenen Planhinweisliste ist NULL oder ungültig, oder Sie besitzen nicht die Berechtigung für das Objekt, auf das die Planhinweisliste verweist.  
  
## <a name="user-action"></a>Benutzeraktion  
Vergewissern Sie sich, dass die Planhinweislisten-ID gültig, die aktuelle Sitzung auf den korrekten Datenbankkontext eingestellt ist und Sie die ALTER DATABASE-Berechtigung oder die ALTER-Berechtigung für das Objekt besitzen, auf das die Planhinweisliste verweist.  
  
## <a name="see-also"></a>Weitere Informationen  
[sp_create_plan_guide &#40;Transact-SQL&#41;](~/relational-databases/system-stored-procedures/sp-create-plan-guide-transact-sql.md)  
[Planhinweislisten](~/relational-databases/performance/plan-guides.md)  
[sp_create_plan_guide_from_handle &#40;Transact-SQL&#41;](~/relational-databases/system-stored-procedures/sp-create-plan-guide-from-handle-transact-sql.md)  
  
