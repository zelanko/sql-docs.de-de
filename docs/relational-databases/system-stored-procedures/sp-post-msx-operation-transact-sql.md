---
title: Sp_post_msx_operation (Transact-SQL) | Microsoft-Dokumentation
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
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68056370"
---
# <a name="sppostmsxoperation-transact-sql"></a>sp_post_msx_operation (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Fügt der Operationen (Zeilen) in der **Sysdownloadlist** Systemtabelle für die Zielserver zum Herunterladen und ausführen.  
  
 ![Themenlinksymbol](../../database-engine/configure-windows/media/topic-link.gif "Topic link icon") [Transact-SQL Syntax Conventions (Transact-SQL-Syntaxkonventionen)](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
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
`[ @operation = ] 'operation'` Der Typ des Vorgangs für den gesendeten Vorgang. *Vorgang*ist **varchar(64)** , hat keinen Standardwert. Gültigen Operationen hängen von *Object_type*.  
  
|Objekttyp|Vorgang|  
|-----------------|---------------|  
|**JOB**|INSERT<br /><br /> UPDATE<br /><br /> DELETE<br /><br /> START<br /><br /> STOP|  
|**SERVER**|RE-ENLIST<br /><br /> DEFECT<br /><br /> SYNC-TIME<br /><br /> SET-POLL|  
|**ZEITPLAN**|INSERT<br /><br /> UPDATE<br /><br /> DELETE|  
  
`[ @object_type = ] 'object'` Der Typ des Objekts, für das eine Operation bereitgestellt. Gültige Typen sind **Auftrag**, **SERVER**, und **Zeitplan**. *Objekt* ist **varchar(64)** , hat den Standardwert **Auftrag**.  
  
`[ @job_id = ] job_id` Die Auftrags-ID des Auftrags für den die Operation zutrifft. *Job_id* ist **Uniqueidentifier**, hat keinen Standardwert. **0 x 00** zeigt alle Aufträge. Wenn *Objekt* ist **SERVER**, klicken Sie dann *Job_id*ist nicht erforderlich.  
  
`[ @specific_target_server = ] 'target_server'` Der Name des Zielservers für die die angegebene Operation zutrifft. Wenn *Job_id* angegeben ist, aber *Target_server* nicht angegeben ist, die Vorgänge werden für alle Auftragsserver des Auftrags bereitgestellt. *Target_server* ist **nvarchar(30)** , hat den Standardwert NULL.  
  
`[ @value = ] value` Das Abrufintervall in Sekunden. *value* ist vom Datentyp **int**. Der Standardwert ist NULL. Geben Sie diesen Parameter nur, wenn *Vorgang* ist **SET-POLL**.  
  
`[ @schedule_uid = ] schedule_uid` Der eindeutige Bezeichner für den Zeitplan für den die Operation zutrifft. *Wert für schedule_uid an* ist **Uniqueidentifier**, hat keinen Standardwert.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 **0** (Erfolg) oder **1** (Fehler)  
  
## <a name="result-sets"></a>Resultsets  
 None  
  
## <a name="remarks"></a>Hinweise  
 **Sp_post_msx_operation** muss ausgeführt werden, aus der **Msdb** Datenbank.  
  
 **Sp_post_msx_operation** kann stets problemlos aufgerufen werden, weil zunächst ermittelt wird, wenn der aktuelle Server ein multiserver Microsoft SQL Server-Agent ist und wenn Ja, ob *Objekt*ein Multiserverauftrag ist.  
  
 Nachdem ein Vorgang gesendet wurde, wird Sie der **Sysdownloadlist** Tabelle. Wenn ein Auftrag erstellt und bereitgestellt wurde, müssen nachfolgende Änderungen an diesem Auftrag auch an die Zielserver (TSX) übermittelt werden. Dies erreichen Sie auch mithilfe der Downloadliste.  
  
 Die Downloadliste sollte unbedingt mithilfe von SQL Server Management Studio verwaltet werden. Weitere Informationen finden Sie unter [anzeigen oder Ändern von Aufträgen](../../ssms/agent/view-or-modify-jobs.md).  
  
## <a name="permissions"></a>Berechtigungen  
 Um diese gespeicherte Prozedur auszuführen, müssen Benutzer gewährt werden die **Sysadmin** -Serverrolle sein.  
  
## <a name="see-also"></a>Siehe auch  
 [sp_add_jobserver &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-add-jobserver-transact-sql.md)   
 [sp_delete_job &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-delete-job-transact-sql.md)   
 [sp_delete_jobserver &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-delete-jobserver-transact-sql.md)   
 [sp_delete_targetserver &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-delete-targetserver-transact-sql.md)   
 [sp_resync_targetserver &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-resync-targetserver-transact-sql.md)   
 [sp_start_job &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-start-job-transact-sql.md)   
 [sp_stop_job &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-stop-job-transact-sql.md)   
 [sp_update_job &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-update-job-transact-sql.md)   
 [sp_update_operator &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-update-operator-transact-sql.md)   
 [Gespeicherte Systemprozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
