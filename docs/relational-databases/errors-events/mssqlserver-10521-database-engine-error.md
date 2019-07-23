---
title: MSSQLSERVER_10521 | Microsoft-Dokumentation
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: language-reference
helpviewer_keywords:
- 10521 (Database Engine error)
ms.assetid: ba2d7e44-207c-4428-b5f0-c975ac122c0d
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: f86922211e670cb59b4541071e9e7d7f67302bc9
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68068156"
---
# <a name="mssqlserver10521"></a>MSSQLSERVER_10521
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>Details  
  
|||  
|-|-|  
|Produktname|SQL Server|  
|Ereignis-ID|10521|  
|Ereignisquelle|MSSQLSERVER|  
|Komponente|SQLEngine|  
|Symbolischer Name|PG_PARAM_NEEDED|  
|Meldungstext|Die Planhinweisliste „%.\*ls“ kann nicht erstellt werden, weil **@type** als „%ls“ angegeben wurde und der „%ls“-Parameter NULL ist. Dieser Typ erfordert einen Wert ungleich NULL für den Parameter. Geben Sie einen Wert ungleich NULL für den Parameter an, oder ändern Sie den Typ in einen Typ, der NULL-Werte für den Parameter zulässt.|  
  
## <a name="explanation"></a>Erklärung  
Der in **@type** angegebene Typ erfordert einen Wert ungleich NULL für den angegebenen Parameter. Es wurde jedoch ein NULL-Wert angegeben.  
  
## <a name="user-action"></a>Benutzeraktion  
Geben Sie einen Wert ungleich NULL für den Parameter an, oder ändern Sie den Typ in einen Typ, der NULL-Werte für den Parameter zulässt.  
  
## <a name="see-also"></a>Weitere Informationen  
[sp_create_plan_guide &#40;Transact-SQL&#41;](~/relational-databases/system-stored-procedures/sp-create-plan-guide-transact-sql.md)  
[Planhinweislisten](~/relational-databases/performance/plan-guides.md)  
[sp_create_plan_guide_from_handle &#40;Transact-SQL&#41;](~/relational-databases/system-stored-procedures/sp-create-plan-guide-from-handle-transact-sql.md)  
  
