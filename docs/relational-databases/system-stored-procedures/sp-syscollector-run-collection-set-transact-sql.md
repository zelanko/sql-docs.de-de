---
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
author: stevestein
ms.author: sstein
ms.openlocfilehash: 3807a53921572bbe20b4c459bff34958cbb42001
ms.sourcegitcommit: 43c3d8939f6f7b0ddc493d8e7a643eb7db634535
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/14/2019
ms.locfileid: "72304994"
---
# <a name="sp_syscollector_run_collection_set-transact-sql"></a>sp_syscollector_run_collection_set (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Startet einen Sammlungssatz, wenn der Sammler bereits aktiviert ist und der Sammlungssatz für den Auflistmodus ohne Zwischenspeicherung konfiguriert ist.  
  
> [!NOTE]  
>  Bei dieser Prozedur tritt ein Fehler auf, wenn sie für einen Sammlungssatz ausgeführt wird, der für den Auflistmodus mit Zwischenspeicherung konfiguriert ist.  
  
 sp_syscollector_run_collection_set ermöglicht dem Benutzer die bedarfsgesteuerte Aufnahme von Datenmomentaufnahmen.  
  
 ![Themenlinksymbol](../../database-engine/configure-windows/media/topic-link.gif "Topic link icon") [Transact-SQL Syntax Conventions (Transact-SQL-Syntaxkonventionen)](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_syscollector_run_collection_set [[ @collection_set_id = ] collection_set_id ]  
          , [[ @name = ] 'name' ]   
```  
  
## <a name="arguments"></a>Argumente  
`[ @collection_set_id = ] collection_set_id` ist der eindeutige lokale Bezeichner für den Sammlungs Satz. *collection_set_id* ist vom *Datentyp* **int** und muss über einen Wert verfügen, wenn Name NULL ist.  
  
`[ @name = ] 'name'` ist der Name des Sammlungs Satzes. *Name ist vom Datentyp* **vom Datentyp sysname** und muss über einen Wert verfügen, wenn *collection_set_id* NULL ist.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 **0** (Erfolg) oder **1** (Fehler)  
  
## <a name="remarks"></a>Hinweise  
 Entweder " *collection_set_id* " oder " *Name* " muss einen Wert aufweisen, beide dürfen nicht NULL sein.  
  
 Diese Prozedur startet die Sammlungs-und Uploadaufträge für den angegebenen Sammlungs Satz und startet sofort den Auftrag des Sammlungs-Agents, wenn für den Sammlungs Satz das **\@collection_mode** auf nicht zwischengespeichert (1) festgelegt ist. Weitere Informationen finden Sie unter [sp_syscollector_create_collection_set &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-syscollector-create-collection-set-transact-sql.md).  
  
 sp_sycollector_run_collection_set kann auch verwendet werden, um einen Sammlungssatz auszuführen, der über keinen Zeitplan verfügt.  
  
## <a name="permissions"></a>Berechtigungen  
 Erfordert die Mitgliedschaft in der Daten Bank Rolle **dc_operator** (mit EXECUTE-Berechtigung) zum Ausführen dieser Prozedur.  
  
## <a name="example"></a>Beispiel  
 Starten Sie einen Sammlungssatz unter Verwendung des zugehörigen Bezeichners.  
  
```  
USE msdb;  
GO  
EXEC sp_syscollector_run_collection_set @collection_set_id = 1;  
```  
  
## <a name="see-also"></a>Siehe auch  
 [Gespeicherte Systemprozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)   
 [Datensammlung](../../relational-databases/data-collection/data-collection.md)  
  
  
