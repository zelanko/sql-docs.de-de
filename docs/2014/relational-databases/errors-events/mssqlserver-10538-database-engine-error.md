---
title: MSSQLSERVER_10538 | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 10538 (Database Engine error)
ms.assetid: 284d19b4-4979-4cbe-a9be-ac1104433c69
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 42588c7fc44dba053f00ff3a206edf22773d1f7f
ms.sourcegitcommit: b57d98e9b2444348f95c83a24b8eea0e6c9da58d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/21/2020
ms.locfileid: "86554075"
---
# <a name="mssqlserver_10538"></a>MSSQLSERVER_10538
    
## <a name="details"></a>Details  
  
|attribute|Wert|  
|-|-|  
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
 [sp_create_plan_guide &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-create-plan-guide-transact-sql)   
 [Plan Hinweis Listen](../performance/plan-guides.md)   
 [sp_create_plan_guide_from_handle &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-create-plan-guide-from-handle-transact-sql)  
  
  
