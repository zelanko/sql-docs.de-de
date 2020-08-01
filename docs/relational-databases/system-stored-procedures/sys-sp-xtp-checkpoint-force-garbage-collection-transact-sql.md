---
title: sys. sp_xtp_checkpoint_force_garbage_collection (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 08/02/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.sp_xtp_checkpoint_force_garbage_collection_TSQL
- sys.sp_xtp_checkpoint_force_garbage_collection
dev_langs:
- TSQL
helpviewer_keywords:
- sys.sp_xtp_checkpoint_force_garbage_collection
ms.assetid: 82b35b2b-edbd-44ac-9fc8-80695f2fd1df
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: df25b33677d4494d32bd60bb55b5c60791bcad30
ms.sourcegitcommit: 039fb38c583019b3fd06894160568387a19ba04e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/30/2020
ms.locfileid: "87442413"
---
# <a name="syssp_xtp_checkpoint_force_garbage_collection-transact-sql"></a>sys.sp_xtp_checkpoint_force_garbage_collection (Transact-SQL)
[!INCLUDE[sqlserver](../../includes/applies-to-version/sqlserver.md)]

  Kennzeichnet die Quelldateien, die während des Zusammenführens verwendet werden, mit der Protokollfolgenummer (LSN). Danach werden die Dateien nicht mehr benötigt und können in die Garbage Collection verschoben werden. Außerdem werden die Dateien, deren zugeordnete LSN niedriger ist als der Protokollkürzungspunkt, in die Filestream Garbage Collection verschoben.  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
 
## <a name="syntax"></a>Syntax  
  
```  
sys.sp_xtp_checkpoint_force_garbage_collection [[ @dbname=database_name]  
```  
  
## <a name="arguments"></a>Argumente  
 *database_name*  
 Die Datenbank, für die die Garbage Collection ausgeführt werden soll. Gemäß Standardeinstellung die aktuelle Datenbank.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 0 für Erfolg. Ungleich 0 für Fehler.  
  
## <a name="result-set"></a>Resultset  
 Eine zurückgegebene Zeile enthält die folgenden Informationen:  
  
|Column|BESCHREIBUNG|  
|------------|-----------------|  
|num_collected_items|Gibt die Anzahl der Dateien an, die in die Filestream Garbage Collection verschoben wurden. Diese Dateien verfügen über eine Protokollfolgenummer (LSN), die niedriger ist als die LSN des Protokollkürzungspunkts.|  
|num_marked_for_collection_items|Gibt die Anzahl der Daten-/Änderungsdateien an, deren LSN mit der Protokollblock-ID der Protokollende-LSN aktualisiert wurde.|  
|last_collected_xact_seqno|Gibt die letzte entsprechende LSN zurück, bis zu der die Dateien in die Filestream Garbage Collection verschoben wurden.|  
  
## <a name="permissions"></a>Berechtigungen  
 Erfordert die Berechtigung des Datenbankbesitzers.  
  
## <a name="sample"></a>Beispiel  
  
```  
exec [sys].[sp_xtp_checkpoint_force_garbage_collection] hkdb1  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [Gespeicherte System Prozeduren &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)   
 [In-Memory-OLTP &#40;Arbeitsspeicheroptimierung&#41;](../../relational-databases/in-memory-oltp/in-memory-oltp-in-memory-optimization.md)  
  
  
