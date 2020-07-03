---
title: sp_syscollector_start_collection_set (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 08/09/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_syscollector_start_collection_set_TSQL
- sp_syscollector_start_collection_set
dev_langs:
- TSQL
helpviewer_keywords:
- data collector [SQL Server], stored procedures
- sp_syscollector_start_collection_set
ms.assetid: d8357180-f51e-4681-99f9-0596fe2d2b53
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 56fa6b114d58512f9cdec9c3da2575539af0d03b
ms.sourcegitcommit: f7ac1976d4bfa224332edd9ef2f4377a4d55a2c9
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2020
ms.locfileid: "85892845"
---
# <a name="sp_syscollector_start_collection_set-transact-sql"></a>sp_syscollector_start_collection_set (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Startet einen Sammlungssatz, wenn der Sammler bereits aktiviert ist und der Sammlungssatz nicht ausgeführt wird. Wenn der Collector nicht aktiviert ist, aktivieren Sie den Collector, indem Sie [sp_syscollector_enable_collector](../../relational-databases/system-stored-procedures/sp-syscollector-enable-collector-transact-sql.md) ausführen und dann diese gespeicherte Prozedur verwenden, um einen Sammlungs Satz zu starten.  

  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_syscollector_start_collection_set   
    [ [ @collection_set_id = ] collection_set_id ]  
    , [[ @name = ] 'name' ]   
```  
  
## <a name="arguments"></a>Argumente  
`[ @collection_set_id = ] collection_set_id`Der eindeutige lokale Bezeichner für den Sammlungs Satz. *collection_set_id* ist vom Datentyp **int** und hat den Standardwert NULL. *collection_set_id* muss einen Wert haben, wenn der *Name* NULL ist.  
  
`[ @name = ] 'name'`Der Name des Sammlungs Satzes. *Name ist vom Datentyp* **vom Datentyp sysname** und hat den Standardwert NULL. der *Name* muss einen Wert haben, wenn *collection_set_id* NULL ist.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 **0** (Erfolg) oder **1** (Fehler)  
  
## <a name="remarks"></a>Hinweise  
 sp_syscollector_create_collection_set muss im Kontext der msdb-Systemdatenbank ausgeführt werden, und SQL Server-Agent muss aktiviert sein.  
  
 Bei dieser Prozedur tritt ein Fehler auf, wenn sie für einen Sammlungssatz ohne Zeitplan ausgeführt wird. Wenn der Sammlungs Satz keinen Zeitplan hat (weil der Sammlungs Modus z. b. auf einen nicht zwischengespeicherten festgelegt ist), verwenden Sie die gespeicherte Prozedur [sp_syscollector_run_collection_set](../../relational-databases/system-stored-procedures/sp-syscollector-run-collection-set-transact-sql.md) , um den Sammlungs Satz zu starten.  
  
 Diese Prozedur aktiviert die Sammlungs- und Uploadaufträge für den angegebenen Sammlungssatz und startet umgehend den Auftrag des Sammlungs-Agents, wenn für den Sammlungssatz der zugehörige Sammlungsmodus auf die Zwischenspeicherung (0) festgelegt ist. Weitere Informationen finden Sie unter [sp_syscollector_create_collection_set](../../relational-databases/system-stored-procedures/sp-syscollector-create-collection-set-transact-sql.md).  
  
 Wenn der Sammlungssatz keine Sammelelemente enthält, hat dieser Vorgang keine Auswirkungen. Fehler 14685 wird als Warnung zurückgegeben.  
  
## <a name="permissions"></a>Berechtigungen  
 Damit diese Prozedur ausgeführt werden kann, ist die Mitgliedschaft in der festen Datenbankrolle dc_operator erforderlich. Wenn der Sammlungssatz über kein Proxykonto verfügt, ist die Mitgliedschaft in der festen Serverrolle sysadmin erforderlich.  
  
## <a name="examples"></a>Beispiele  
 Im folgenden Beispiel wird ein Sammlungssatz mithilfe seines Bezeichners gestartet.  
  
```  
USE msdb;  
GO  
EXEC sp_syscollector_start_collection_set @collection_set_id = 1;  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [Gespeicherte Prozeduren für den Datensammler &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/data-collector-stored-procedures-transact-sql.md)   
 [Datensammlung](../../relational-databases/data-collection/data-collection.md)   
 [syscollector_collection_sets &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/syscollector-collection-sets-transact-sql.md)  
  
  
