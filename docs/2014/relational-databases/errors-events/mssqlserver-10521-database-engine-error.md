---
title: MSSQLSERVER_10521 | Microsoft-Dokumentation
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
- 10521 (Database Engine error)
ms.assetid: ba2d7e44-207c-4428-b5f0-c975ac122c0d
caps.latest.revision: 10
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.openlocfilehash: 209496ac8159eb32c36fcded35992cac1e45d6f0
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36148144"
---
# <a name="mssqlserver10521"></a>MSSQLSERVER_10521
    
## <a name="details"></a>Details  
  
|||  
|-|-|  
|Produktname|SQL Server|  
|Ereignis-ID|10521|  
|Ereignisquelle|MSSQLSERVER|  
|Komponente|SQLEngine|  
|Symbolischer Name|PG_PARAM_NEEDED|  
|Meldungstext|Kann nicht erstellt werden Planhinweisliste ' %. \*%.*ls'-Datenbank da `@type` angegeben wurde als '%ls' und den Parameter '%ls' ist NULL. Dieser Typ erfordert einen Wert ungleich NULL für den Parameter. Geben Sie einen Wert ungleich NULL für den Parameter an, oder ändern Sie den Typ in einen Typ, der NULL-Werte für den Parameter zulässt.|  
  
## <a name="explanation"></a>Erklärung  
 Der in `@type` angegebene Typ erfordert einen Wert ungleich NULL für den angegebenen Parameter. Es wurde jedoch ein NULL-Wert angegeben.  
  
## <a name="user-action"></a>Benutzeraktion  
 Geben Sie einen Wert ungleich NULL für den Parameter an, oder ändern Sie den Typ in einen Typ, der NULL-Werte für den Parameter zulässt.  
  
## <a name="see-also"></a>Siehe auch  
 [sp_create_plan_guide &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-create-plan-guide-transact-sql)   
 [Planhinweislisten](../performance/plan-guides.md)   
 [sp_create_plan_guide_from_handle &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-create-plan-guide-from-handle-transact-sql)  
  
  
