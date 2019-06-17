---
title: MSSQLSERVER_10534 | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 10534 (Database Engine error)
ms.assetid: e65bb118-99d5-4fdb-b1d5-0ec70f0a677b
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: a9a20d1003e8b87179e2690fa35ad44b50894568
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "62870579"
---
# <a name="mssqlserver10534"></a>MSSQLSERVER_10534
    
## <a name="details"></a>Details  
  
|||  
|-|-|  
|Produktname|SQL Server|  
|Ereignis-ID|10534|  
|Ereignisquelle|MSSQLSERVER|  
|Komponente|SQLEngine|  
|Symbolischer Name|PG_INVALID_PARAMS|  
|Meldungstext|Die Planhinweisliste kann nicht erstellt werden kann ' %. \*ls, da der Wert für die angegebene `@params` ist ungültig. Verwenden Sie für den Wert das Format *parameter_name parameter_type*, oder geben Sie NULL an.|  
  
## <a name="explanation"></a>Erklärung  
 Der für `@params` angegebene Wert ist ungültig.  
  
## <a name="user-action"></a>Benutzeraktion  
 Verwenden Sie für den Wert das Format *parameter_name parameter_type*, oder geben Sie NULL an.  
  
## <a name="see-also"></a>Siehe auch  
 [Planhinweislisten](../performance/plan-guides.md)   
 [sp_create_plan_guide &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-create-plan-guide-transact-sql)   
 [sp_create_plan_guide_from_handle &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-create-plan-guide-from-handle-transact-sql)  
  
  
