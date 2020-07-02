---
title: Datensammler Sichten (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
dev_langs:
- TSQL
helpviewer_keywords:
- data collector view
- data collector [SQL Server], views
ms.assetid: a005e885-7813-4c7e-b332-b01d9e9d4054
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 91542894eeb00fc6c44e3d824bb7fd857cef8897
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/01/2020
ms.locfileid: "85752991"
---
# <a name="data-collector-views-transact-sql"></a>Sichten des Datensammlers (Transact-SQL)
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Der Datensammler bietet die folgenden Sichten, in denen Informationen zur Konfiguration des Datensammlers, beispielsweise Eigenschaften des Sammlertyps, Sammlungssätze und Elemente in Sammlungssätzen, sowie Ausführungsstatistiken, die bei der Ausführung eines Sammlungssatzes abgerufen werden, angezeigt werden können. Diese Sichten, die sich in der **msdb** -Datenbank befinden, stellen auch eine Abstraktions Ebene für die zugrunde liegenden Tabellen bereit. Diese Abstraktion erhöht die Sicherheit, indem der direkte Zugriff auf die Tabellen verhindert wird, während Änderungen an den Tabellen zugelassen werden, ohne dass zugehörige Anwendungen betroffen sind.  
  
|||  
|-|-|  
|[syscollector_collection_items &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/syscollector-collection-items-transact-sql.md)|[syscollector_collection_sets &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/syscollector-collection-sets-transact-sql.md)|  
|[syscollector_collector_types &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/syscollector-collector-types-transact-sql.md)|[syscollector_config_store &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/syscollector-config-store-transact-sql.md)|  
|[syscollector_execution_log &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/syscollector-execution-log-transact-sql.md)|[syscollector_execution_log_full &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/syscollector-execution-log-full-transact-sql.md)|  
|[syscollector_execution_stats &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/syscollector-execution-stats-transact-sql.md)||  
  
## <a name="see-also"></a>Weitere Informationen  
 [Datensammlung](../../relational-databases/data-collection/data-collection.md)   
 [Gespeicherte Prozeduren für den Datensammler &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/data-collector-stored-procedures-transact-sql.md)  
  
  
