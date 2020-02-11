---
title: sp_post_msx_operation (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_post_msx_operation
- sp_post_msx_operation_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_post_msx_operation
ms.assetid: 085deef8-2709-4da9-bb97-9ab32effdacf
author: stevestein
ms.author: sstein
ms.openlocfilehash: 93e9c574346ad57a6947645552616cd8db46fe85
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "68056370"
---
# <a name="sp_post_msx_operation-transact-sql"></a>sp_post_msx_operation (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Fügt Vorgänge (Zeilen) in die **sysdownloadlist** -Systemtabelle ein, damit Zielserver heruntergeladen und ausgeführt werden können.  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_post_msx_operation  
     [ @operation = ] 'operation'  
     [ , [ @object_type = ] 'object' ]   
     { , [ @job_id = ] job_id }   
     [ , [ @specific_target_server = ] 'target_server' ]   
     [ , [ @value = ] value ]  
     [ , [ @schedule_uid = ] schedule_uid ]  
```  
  
## <a name="arguments"></a>Argumente  
`[ @operation = ] 'operation'`Der Typ des Vorgangs für den übermittelten Vorgang. *Operation*ist vom Datentyp **varchar (64)** und hat keinen Standardwert. Gültige Vorgänge sind von *object_type*abhängig.  
  
|Objekttyp|Vorgang|  
|-----------------|---------------|  
|**Auftrag**|INSERT<br /><br /> UPDATE<br /><br /> Delete<br /><br /> START<br /><br /> STOP|  
|**Servers**|RE-ENLIST<br /><br /> DEFECT<br /><br /> SYNC-TIME<br /><br /> SET-POLL|  
|**Vereinbaren**|INSERT<br /><br /> UPDATE<br /><br /> Delete|  
  
`[ @object_type = ] 'object'`Der Typ des Objekts, für das ein Vorgang gepostet werden soll. Gültige Typen sind **Job**, **Server**und **Schedule**. *Objekt* ist vom Datentyp **varchar (64)**. der Standardwert ist **Job**.  
  
`[ @job_id = ] job_id`Die ID des Auftrags, auf den der Vorgang angewendet wird. *job_id* ist vom Datentyp **uniqueidentifier**und hat keinen Standardwert. **0x00** zeigt alle Aufträge an. Wenn *Object* **Server**ist, ist *job_id*nicht erforderlich.  
  
`[ @specific_target_server = ] 'target_server'`Der Name des Zielservers, für den der angegebene Vorgang gilt. Wenn *job_id* angegeben ist, aber *target_server* nicht angegeben ist, werden die Vorgänge für alle Auftrags Server des Auftrags gesendet. *target_server* ist vom Datentyp **nvarchar (30)** und hat den Standardwert NULL.  
  
`[ @value = ] value`Das Abruf Intervall in Sekunden. der Wert ist vom Datentyp **int**und hat den Standard *Wert* NULL. Geben Sie diesen Parameter nur an, wenn der *Vorgang* " **set-** Abruf" ist  
  
`[ @schedule_uid = ] schedule_uid`Der eindeutige Bezeichner für den Zeitplan, auf den der Vorgang angewendet wird. *schedule_uid* ist vom Datentyp **uniqueidentifier**und hat keinen Standardwert.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 **0** (Erfolg) oder **1** (Fehler)  
  
## <a name="result-sets"></a>Resultsets  
 Keine  
  
## <a name="remarks"></a>Bemerkungen  
 **sp_post_msx_operation** müssen von der **msdb** -Datenbank aus ausgeführt werden.  
  
 **sp_post_msx_operation** kann immer sicher aufgerufen werden, da zuerst festgelegt wird, ob es sich bei dem aktuellen Server um einen Multiserver-Microsoft SQL Server Agent handelt. ist dies der Fall, ist das *Objekt*ein Multiserverauftrag.  
  
 Nachdem ein Vorgang gepostet wurde, wird er in der **sysdownloadlist** -Tabelle angezeigt. Wenn ein Auftrag erstellt und bereitgestellt wurde, müssen nachfolgende Änderungen an diesem Auftrag auch an die Zielserver (TSX) übermittelt werden. Dies erreichen Sie auch mithilfe der Downloadliste.  
  
 Die Downloadliste sollte unbedingt mithilfe von SQL Server Management Studio verwaltet werden. Weitere Informationen finden Sie unter [anzeigen oder Ändern von Aufträgen](../../ssms/agent/view-or-modify-jobs.md).  
  
## <a name="permissions"></a>Berechtigungen  
 Zum Ausführen dieser gespeicherten Prozedur muss den Benutzern die festen Server Rolle **sysadmin** erteilt werden.  
  
## <a name="see-also"></a>Weitere Informationen  
 [sp_add_jobserver &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-add-jobserver-transact-sql.md)   
 [sp_delete_job &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-delete-job-transact-sql.md)   
 [sp_delete_jobserver &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-delete-jobserver-transact-sql.md)   
 [sp_delete_targetserver &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-delete-targetserver-transact-sql.md)   
 [sp_resync_targetserver &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-resync-targetserver-transact-sql.md)   
 [sp_start_job &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-start-job-transact-sql.md)   
 [sp_stop_job &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-stop-job-transact-sql.md)   
 [sp_update_job &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-update-job-transact-sql.md)   
 [sp_update_operator &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-update-operator-transact-sql.md)   
 [Gespeicherte Systemprozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
