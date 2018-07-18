---
title: MSSQLSERVER_10521 | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: supportability
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- 10521 (Database Engine error)
ms.assetid: ba2d7e44-207c-4428-b5f0-c975ac122c0d
caps.latest.revision: 10
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 18d823ff21a38c3eeee8df725c9a38172080d40e
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/03/2018
ms.locfileid: "37421079"
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
|Meldungstext|Die Planhinweisliste kann nicht erstellt werden kann ' %. \*ls da `@type` angegeben wurde '%ls' und der Parameter '%ls' ist NULL. Dieser Typ erfordert einen Wert ungleich NULL für den Parameter. Geben Sie einen Wert ungleich NULL für den Parameter an, oder ändern Sie den Typ in einen Typ, der NULL-Werte für den Parameter zulässt.|  
  
## <a name="explanation"></a>Erklärung  
 Der in `@type` angegebene Typ erfordert einen Wert ungleich NULL für den angegebenen Parameter. Es wurde jedoch ein NULL-Wert angegeben.  
  
## <a name="user-action"></a>Benutzeraktion  
 Geben Sie einen Wert ungleich NULL für den Parameter an, oder ändern Sie den Typ in einen Typ, der NULL-Werte für den Parameter zulässt.  
  
## <a name="see-also"></a>Siehe auch  
 [sp_create_plan_guide &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-create-plan-guide-transact-sql)   
 [Planhinweislisten](../performance/plan-guides.md)   
 [sp_create_plan_guide_from_handle &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-create-plan-guide-from-handle-transact-sql)  
  
  
