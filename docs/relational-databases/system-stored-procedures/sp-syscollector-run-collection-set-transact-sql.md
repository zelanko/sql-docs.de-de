---
description: sp_syscollector_run_collection_set (Transact-SQL)
title: sp_syscollector_run_collection_set (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_syscollector_run_collection_set_TSQL
- sp_syscollector_run_collection_set
dev_langs:
- TSQL
helpviewer_keywords:
- sp_syscollector_run_collection_set
- data collector [SQL Server], stored procedures
ms.assetid: 7bbaee48-dfc7-45c0-b11f-c636b6a7e720
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 69ba3790a9b1805eb4d717ad23fa284494ce14af
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88481029"
---
# <a name="sp_syscollector_run_collection_set-transact-sql"></a>sp_syscollector_run_collection_set (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Startet einen Sammlungssatz, wenn der Sammler bereits aktiviert ist und der Sammlungssatz für den Auflistmodus ohne Zwischenspeicherung konfiguriert ist.  
  
> [!NOTE]  
>  Bei dieser Prozedur tritt ein Fehler auf, wenn sie für einen Sammlungssatz ausgeführt wird, der für den Auflistmodus mit Zwischenspeicherung konfiguriert ist.  
  
 sp_syscollector_run_collection_set ermöglicht dem Benutzer die bedarfsgesteuerte Aufnahme von Datenmomentaufnahmen.  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_syscollector_run_collection_set [[ @collection_set_id = ] collection_set_id ]  
          , [[ @name = ] 'name' ]   
```  
  
## <a name="arguments"></a>Argumente  
`[ @collection_set_id = ] collection_set_id` Der eindeutige lokale Bezeichner für den Sammlungs Satz. *collection_set_id* ist vom *Datentyp* **int** und muss über einen Wert verfügen, wenn Name NULL ist.  
  
`[ @name = ] 'name'` Der Name des Sammlungs Satzes. *Name ist vom Datentyp* **vom Datentyp sysname** und muss über einen Wert verfügen, wenn *collection_set_id* NULL ist.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 **0** (Erfolg) oder **1** (Fehler)  
  
## <a name="remarks"></a>Bemerkungen  
 Entweder *collection_set_id* oder *Name* muss einen Wert aufweisen, beide dürfen nicht NULL sein.  
  
 Diese Prozedur startet die Sammlungs-und Uploadaufträge für den angegebenen Sammlungs Satz und startet sofort den Auftrag des Sammlungs-Agents, wenn für den Sammlungs Satz der ** \@ collection_mode** auf einen nicht zwischengespeicherten Wert festgelegt ist (1). Weitere Informationen finden Sie unter [sp_syscollector_create_collection_set &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-syscollector-create-collection-set-transact-sql.md).  
  
 sp_sycollector_run_collection_set kann auch verwendet werden, um einen Sammlungssatz auszuführen, der über keinen Zeitplan verfügt.  
  
## <a name="permissions"></a>Berechtigungen  
 Zum Ausführen dieses Vorgangs ist die Mitgliedschaft in der Daten Bank Rolle **dc_operator** (mit EXECUTE-Berechtigung) erforderlich.  
  
## <a name="example"></a>Beispiel  
 Starten Sie einen Sammlungssatz unter Verwendung des zugehörigen Bezeichners.  
  
```  
USE msdb;  
GO  
EXEC sp_syscollector_run_collection_set @collection_set_id = 1;  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [Gespeicherte System Prozeduren &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)   
 [Datensammlung](../../relational-databases/data-collection/data-collection.md)  
  
  
