---
title: sp_apply_job_to_targets (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_apply_job_to_targets
- sp_apply_job_to_targets_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_apply_job_to_targets
ms.assetid: 4a3e9173-7e3c-4100-a9ac-2f5d2c60a8b0
author: stevestein
ms.author: sstein
ms.openlocfilehash: 32e9f15dca77a7c99d7d4a9ae314e074876c6274
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "68117811"
---
# <a name="sp_apply_job_to_targets-transact-sql"></a>sp_apply_job_to_targets (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Wendet einen Auftrag auf einen oder mehrere Zielserver oder auf die Zielserver an, die einer oder mehreren Zielservergruppen angehören.  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_apply_job_to_targets { [ @job_id = ] job_id | [ @job_name = ] 'job_name' }  
     [ , [ @target_server_groups = ] 'target_server_groups' ]   
     [ , [ @target_servers = ] 'target_servers' ]   
     [ , [ @operation = ] 'operation' ]   
```  
  
## <a name="arguments"></a>Argumente  
`[ @job_id = ] job_id`Die Auftrags-ID des Auftrags, der auf die angegebenen Zielserver oder Zielserver Gruppen angewendet werden soll. *job_id* ist vom Datentyp **uniqueidentifier**und hat den Standardwert NULL.  
  
`[ @job_name = ] 'job_name'`Der Name des Auftrags, der auf die angegebenen Zielserver oder Zielserver Gruppen angewendet werden soll. *job_name* ist vom **Datentyp vom Datentyp sysname**und hat den Standardwert NULL.  
  
> [!NOTE]  
>  Es muss entweder *job_id* oder *job_name* angegeben werden, beide Angaben können jedoch nicht angegeben werden.  
  
`[ @target_server_groups = ] 'target_server_groups'`Eine durch Trennzeichen getrennte Liste der Zielserver Gruppen, auf die der angegebene Auftrag angewendet werden soll. *target_server_groups* ist vom Datentyp **nvarchar (2048)** und hat den Standardwert NULL.  
  
`[ @target_servers = ] 'target_servers'`Eine durch Trennzeichen getrennte Liste von Ziel Servern, auf die der angegebene Auftrag angewendet werden soll. *target_servers*ist vom Datentyp **nvarchar (2048)** und hat den Standardwert NULL.  
  
`[ @operation = ] 'operation'`Gibt an, ob der angegebene Auftrag auf die angegebenen Zielserver oder Zielserver Gruppen angewendet oder daraus entfernt werden soll. *Operation*ist vom Datentyp **varchar (7)**. der Standardwert ist Apply. Gültige Vorgänge sind **Apply** und **Remove**.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 **0** (Erfolg) oder **1** (Fehler)  
  
## <a name="remarks"></a>Bemerkungen  
 **sp_apply_job_to_targets** bietet eine einfache Möglichkeit zum anwenden (oder entfernen) eines Auftrags von mehreren Ziel Servern und ist eine Alternative zum Aufrufen von **sp_add_jobserver** (oder **sp_delete_jobserver**) für jeden erforderlichen Zielserver.  
  
## <a name="permissions"></a>Berechtigungen  
 Nur Mitglieder der festen Server Rolle **sysadmin** können diese Prozedur ausführen.  
  
## <a name="examples"></a>Beispiele  
 Im folgenden Beispiel wird der zuvor erstellte Auftrag `Backup Customer Information` auf alle Zielserver in der Gruppe `Servers Maintaining Customer Information` angewendet.  
  
```  
USE msdb ;  
GO  
  
EXEC dbo.sp_apply_job_to_targets  
    @job_name = N'Backup Customer Information',  
    @target_server_groups = N'Servers Maintaining Customer Information',   
    @operation = N'APPLY' ;  
GO  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [sp_add_jobserver &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-add-jobserver-transact-sql.md)   
 [sp_delete_jobserver &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-delete-jobserver-transact-sql.md)   
 [sp_remove_job_from_targets &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-remove-job-from-targets-transact-sql.md)   
 [Gespeicherte Systemprozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
