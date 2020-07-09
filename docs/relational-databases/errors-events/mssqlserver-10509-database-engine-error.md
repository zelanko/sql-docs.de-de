---
title: MSSQLSERVER_10509 | Microsoft-Dokumentation
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: language-reference
helpviewer_keywords:
- 10509 (Database Engine error)
ms.assetid: e9dd5357-ee3d-420a-9a89-d12ab5404e73
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 3897e0a92083f292ba2edd062536ebdd6bda6c69
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/01/2020
ms.locfileid: "85781510"
---
# <a name="mssqlserver_10509"></a>MSSQLSERVER_10509
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  
## <a name="details"></a>Details  
  
| attribute | Wert |  
| :-------- | :---- |  
|Produktname|SQL Server|  
|Ereignis-ID|10509|  
|Ereignisquelle|MSSQLSERVER|  
|Komponente|SQLEngine|  
|Symbolischer Name|PG_INVALID_STMT|  
|Meldungstext|Die Planhinweisliste '%.\*ls' kann nicht erstellt werden, weil die mit **\@stmt** oder **\@statement_start_offset** angegebene Anweisung einen Syntaxfehler enthält oder für die Planhinweisliste nicht verwendet werden kann. Geben Sie nur eine gültige [!INCLUDE[tsql](../../includes/tsql-md.md)]-Anweisung oder eine gültige Startposition der Anweisung im Batch an. Fragen Sie die Spalte statement_start_offset in der dynamischen sys.dm_exec_query_stats-Verwaltungsfunktion ab, um eine gültige Startposition zu erhalten.|  
  
## <a name="explanation"></a>Erklärung  
Die mit **\@stmt** oder **\@statement_start_offset** angegebene Anweisung enthält einen Syntaxfehler oder kann für die Planhinweisliste nicht verwendet werden.  
  
## <a name="user-action"></a>Benutzeraktion  
Geben Sie nur eine gültige [!INCLUDE[tsql](../../includes/tsql-md.md)]-Anweisung oder eine gültige Startposition der Anweisung im Batch an. Fragen Sie die Spalte statement_start_offset in der dynamischen sys.dm_exec_query_stats-Verwaltungsfunktion ab, um eine gültige Startposition zu erhalten.  
  
## <a name="see-also"></a>Weitere Informationen  
[sp_create_plan_guide &#40;Transact-SQL&#41;](~/relational-databases/system-stored-procedures/sp-create-plan-guide-transact-sql.md)  
[Planhinweislisten](~/relational-databases/performance/plan-guides.md)  
[sys.dm_exec_query_stats &#40;Transact-SQL&#41;](~/relational-databases/system-dynamic-management-views/sys-dm-exec-query-stats-transact-sql.md)  
[sp_create_plan_guide_from_handle &#40;Transact-SQL&#41;](~/relational-databases/system-stored-procedures/sp-create-plan-guide-from-handle-transact-sql.md)  
  
