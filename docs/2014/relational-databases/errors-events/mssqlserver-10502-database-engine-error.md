---
title: MSSQLSERVER_10502 | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: supportability
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- 10502 (Database Engine error)
ms.assetid: 26d9b64d-4299-4b55-92d0-0a32a3688c0a
caps.latest.revision: 9
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 4b91f5564c5f07c39c815fcc3a8e707c5370cebc
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/03/2018
ms.locfileid: "37419259"
---
# <a name="mssqlserver10502"></a>MSSQLSERVER_10502
    
## <a name="details"></a>Details  
  
|||  
|-|-|  
|Produktname|SQL Server|  
|Ereignis-ID|10502|  
|Ereignisquelle|MSSQLSERVER|  
|Komponente|SQLEngine|  
|Symbolischer Name|PG_DUP_FOUND|  
|Meldungstext|Die Planhinweisliste „%.*ls“ kann nicht erstellt werden, weil die mit @stmt und @module_or_batch oder @plan_handle und @statement_start_offset angegebene Anweisung mit der vorhandenen Planhinweisliste „%.\*ls“ in der Datenbank übereinstimmt. Löschen Sie die vorhandene Planhinweisliste, bevor Sie die neue Planhinweisliste erstellen.|  
  
## <a name="explanation"></a>Erklärung  
 Für die angegebene Anweisung ist eine Planhinweisliste vorhanden.  
  
## <a name="user-action"></a>Benutzeraktion  
 Löschen Sie die vorhandene Planhinweisliste, bevor Sie die neue Planhinweisliste erstellen.  
  
## <a name="see-also"></a>Siehe auch  
 [Planhinweislisten](../performance/plan-guides.md)   
 [sp_create_plan_guide &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-create-plan-guide-transact-sql)   
 [sp_create_plan_guide_from_handle &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-create-plan-guide-from-handle-transact-sql)  
  
  
