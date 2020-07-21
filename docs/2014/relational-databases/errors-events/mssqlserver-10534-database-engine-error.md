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
ms.openlocfilehash: 021ef5c5c7980115f5eb25792f4090774d968cef
ms.sourcegitcommit: b57d98e9b2444348f95c83a24b8eea0e6c9da58d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/21/2020
ms.locfileid: "86554125"
---
# <a name="mssqlserver_10534"></a>MSSQLSERVER_10534
    
## <a name="details"></a>Details  
  
|attribute|Wert|  
|-|-|  
|Produktname|SQL Server|  
|Ereignis-ID|10534|  
|Ereignisquelle|MSSQLSERVER|  
|Komponente|SQLEngine|  
|Symbolischer Name|PG_INVALID_PARAMS|  
|Meldungstext|Die Planhinweisliste „%.\*ls“ kann nicht erstellt werden, weil der für `@params` angegebene Wert ungültig ist. Verwenden Sie für den Wert das Format *parameter_name parameter_type*, oder geben Sie NULL an.|  
  
## <a name="explanation"></a>Erklärung  
 Der für `@params` angegebene Wert ist ungültig.  
  
## <a name="user-action"></a>Benutzeraktion  
 Verwenden Sie für den Wert das Format *parameter_name parameter_type*, oder geben Sie NULL an.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Plan Hinweis Listen](../performance/plan-guides.md)   
 [sp_create_plan_guide &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-create-plan-guide-transact-sql)   
 [sp_create_plan_guide_from_handle &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-create-plan-guide-from-handle-transact-sql)  
  
  
