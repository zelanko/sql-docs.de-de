---
title: Sp_post_msx_operation (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sp_post_msx_operation
- sp_post_msx_operation_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_post_msx_operation
ms.assetid: 085deef8-2709-4da9-bb97-9ab32effdacf
caps.latest.revision: 29
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: a1524f9e3f20a774d32c491bc264f2c6c63e7b18
ms.sourcegitcommit: 79d4dc820767f7836720ce26a61097ba5a5f23f2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/16/2018
ms.locfileid: "40395932"
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
 [ **@operation =**] **'***operation***'**  
 Der Typ des Vorgangs für den gesendeten Vorgang. *Vorgang*ist **varchar(64)**, hat keinen Standardwert. Gültigen Operationen hängen von *Object_type*.  
  
|Objekttyp|Vorgang|  
|-----------------|---------------|  
|**JOB**|INSERT<br /><br /> UPDATE<br /><br /> Delete<br /><br /> START<br /><br /> STOP|  
|**SERVER**|RE-ENLIST<br /><br /> DEFECT<br /><br /> SYNC-TIME<br /><br /> SET-POLL|  
|**ZEITPLAN**|INSERT<br /><br /> UPDATE<br /><br /> Delete|  
  
 [ **@object_type =**] **'***object***'**  
 Der Objekttyp, für den eine Operation bereitgestellt werden soll. Gültige Typen sind **Auftrag**, **SERVER**, und **Zeitplan**. *Objekt* ist **varchar(64)**, hat den Standardwert **Auftrag**.  
  
 [ **@job_id =**] *job_id*  
 Die ID des Auftrags, der von dem Vorgang betroffen ist. *Job_id* ist **Uniqueidentifier**, hat keinen Standardwert. **0 x 00** zeigt alle Aufträge. Wenn *Objekt* ist **SERVER**, klicken Sie dann *Job_id*ist nicht erforderlich.  
  
 [ **@specific_target_server =**] **'***target_server***'**  
 Der Name des Zielservers, für den die angegebene Operation zutrifft. Wenn *Job_id* angegeben ist, aber *Target_server* nicht angegeben ist, die Vorgänge werden für alle Auftragsserver des Auftrags bereitgestellt. *Target_server* ist **nvarchar(30)**, hat den Standardwert NULL.  
  
 [  **@value =**] *Wert*  
 Das Abrufintervall in Sekunden. *value* ist vom Datentyp **int**. Der Standardwert ist NULL. Geben Sie diesen Parameter nur, wenn *Vorgang* ist **SET-POLL**.  
  
 [ **@schedule_uid=** ] *schedule_uid*  
 Der eindeutige Bezeichner für den Zeitplan, der von dem Vorgang betroffen ist. *Wert für schedule_uid an* ist **Uniqueidentifier**, hat keinen Standardwert.  
  
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
  
  
