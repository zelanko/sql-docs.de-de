---
title: MSSQLSERVER_10537 | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- 10537 (Database Engine error)
ms.assetid: 728469a4-6523-4a37-925f-a950d75420fa
caps.latest.revision: 9
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.openlocfilehash: fa03f65b53437bbb1a2585b8a4580a7394f60e7f
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36050821"
---
# <a name="mssqlserver10537"></a>MSSQLSERVER_10537
    
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
  
## <a name="see-also"></a>Siehe auch  
 [sp_create_plan_guide &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-create-plan-guide-transact-sql)   
 [Planhinweislisten](../performance/plan-guides.md)   
 [sp_create_plan_guide_from_handle &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-create-plan-guide-from-handle-transact-sql)  
  
  
