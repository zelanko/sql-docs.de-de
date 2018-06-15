---
title: MSSQLSERVER_10537 | Microsoft-Dokumentation
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.suite: sql
ms.technology: supportability
ms.tgt_pltfrm: ''
ms.topic: language-reference
helpviewer_keywords:
- 10537 (Database Engine error)
ms.assetid: 728469a4-6523-4a37-925f-a950d75420fa
caps.latest.revision: 9
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: df5d659e27b936922dccd90a1bb5ae4ddab3c4c6
ms.sourcegitcommit: ee661730fb695774b9c483c3dd0a6c314e17ddf8
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/19/2018
ms.locfileid: "34321291"
---
# <a name="mssqlserver10537"></a>MSSQLSERVER_10537
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>Details  
  
|||  
|-|-|  
|Produktname|SQL Server|  
|Ereignis-ID|10537|  
|Ereignisquelle|MSSQLSERVER|  
|Komponente|SQLEngine|  
|Symbolischer Name|PG_DUP_ENABLED|  
|Meldungstext|Die Planhinweisliste '%.*ls' kann nicht aktiviert werden, weil die aktivierte Planhinweisliste '%.\*ls' denselben Bereich und Startoffsetwert wie die Anweisung enthält. Deaktivieren Sie die vorhandene Planhinweisliste, bevor Sie die angegebene Planhinweisliste aktivieren.|  
  
## <a name="explanation"></a>Erklärung  
Eine vorhandene Planhinweisliste enthält denselben Bereich und Startoffsetwert wie die Anweisung in der angegebenen Planhinweisliste.  
  
## <a name="user-action"></a>Benutzeraktion  
Deaktivieren Sie die vorhandene Planhinweisliste, bevor Sie die angegebene Planhinweisliste aktivieren.  
  
## <a name="see-also"></a>Weitere Informationen finden Sie unter  
[sp_create_plan_guide &#40;Transact-SQL&#41;](~/relational-databases/system-stored-procedures/sp-create-plan-guide-transact-sql.md)  
[Planhinweislisten](~/relational-databases/performance/plan-guides.md)  
[sp_create_plan_guide_from_handle &#40;Transact-SQL&#41;](~/relational-databases/system-stored-procedures/sp-create-plan-guide-from-handle-transact-sql.md)  
  
