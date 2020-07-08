---
title: sys. dm_exec_valid_use_hints (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/17/2016
ms.prod: sql
ms.reviewer: ''
ms.technology: system-objects
ms.topic: conceptual
f1_keywords:
- sys.dm_exec_valid_use_hints
- sys.dm_exec_valid_use_hints_TSQL
- dm_exec_valid_use_hints
- dm_exec_valid_use_hints_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_exec_valid_use_hints management view
ms.assetid: 65d50589-39c2-4046-92b6-0c4587d8c593
author: pmasl
ms.author: pelopes
ms.openlocfilehash: 5bcc9db1f2ff0b4395a68025e54b719dc25c31cd
ms.sourcegitcommit: 703968b86a111111a82ef66bb7467dbf68126051
ms.contentlocale: de-DE
ms.lasthandoff: 07/07/2020
ms.locfileid: "86053461"
---
# <a name="sysdm_exec_valid_use_hints-transact-sql"></a>sys. dm_exec_valid_use_hints (Transact-SQL)
[!INCLUDE [sqlserver2016](../../includes/applies-to-version/sqlserver2016.md)]

Gibt [use Hint](../../t-sql/queries/hints-transact-sql-query.md#use_hint) -unterstützte Hinweis Namen zurück. Sie listet einen Hinweis Namen pro Zeile auf.  
  
Verwenden Sie diese DMV, um die Liste aller unterstützten Hinweise unter der use Hint-Notation anzuzeigen.  
  
|Spaltenname|Datentyp|BESCHREIBUNG|  
|-----------------|---------------|-----------------|  
|name|**sysname**|Der Name des Hinweises.|

Beschreibungen der einzelnen Hinweise finden Sie unter [Abfrage Hinweise](../../t-sql/queries/hints-transact-sql-query.md#use_hint) .

Eingeführt in [!INCLUDE[ssSQL15_md](../../includes/sssql15-md.md)] SP1.
  
## <a name="see-also"></a>Weitere Informationen  
    
 [Dynamische Verwaltungs Sichten und Funktionen &#40;Transact-SQL-&#41;](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)   
 [Dynamische Verwaltungs Sichten im Zusammenhang mit der Datenbank &#40;Transact-SQL-&#41;](../../relational-databases/system-dynamic-management-views/database-related-dynamic-management-views-transact-sql.md)  

