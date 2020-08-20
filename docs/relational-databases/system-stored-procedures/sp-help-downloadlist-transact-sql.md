---
description: sp_help_downloadlist (Transact-SQL)
title: sp_help_downloadlist (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_help_downloadlist_TSQL
- sp_help_downloadlist
dev_langs:
- TSQL
helpviewer_keywords:
- sp_help_downloadlist
ms.assetid: 745b265b-86e8-4399-b928-c6969ca1a2c8
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: fb53702ec86f30c81802b95b77c61b71037b402e
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88469392"
---
# <a name="sp_help_downloadlist-transact-sql"></a>sp_help_downloadlist (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Listet alle Zeilen in der **sysdownloadlist** -Systemtabelle für den angegebenen Auftrag oder alle Zeilen auf, wenn kein Auftrag angegeben wird.  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_help_downloadlist { [ @job_id = ] job_id | [ @job_name = ] 'job_name' }   
     [ , [ @operation = ] 'operation' ]   
     [ , [ @object_type = ] 'object_type' ]   
     [ , [ @object_name = ] 'object_name' ]   
     [ , [ @target_server = ] 'target_server' ]   
     [ , [ @has_error = ] has_error ]   
     [ , [ @status = ] status ]   
     [ , [ @date_posted = ] date_posted ]  
```  
  
## <a name="arguments"></a>Argumente  
`[ @job_id = ] job_id` Die ID des Auftrags, für den Informationen zurückgegeben werden sollen. *job_id* ist vom Datentyp **uniqueidentifier**und hat den Standardwert NULL.  
  
`[ @job_name = ] 'job_name'` Der Name des Auftrags. *job_name* ist vom **Datentyp vom Datentyp sysname**und hat den Standardwert NULL.  
  
> [!NOTE]  
>  Es muss entweder *job_id* oder *job_name* angegeben werden, beide Angaben können jedoch nicht angegeben werden.  
  
`[ @operation = ] 'operation'` Der gültige Vorgang für den angegebenen Auftrag. *Operation* ist vom Datentyp **varchar (64)** und hat den Standardwert NULL. die folgenden Werte sind möglich:  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|**Mängel**|Der Server Vorgang, der den Austritt des Zielservers vom Master- **SQLServerAgent** -Dienst anfordert.|  
|**DELETE**|Auftragsvorgang, mit dem ein gesamter Auftrag entfernt wird|  
|**INSERT**|Auftragsvorgang, der einen gesamten Auftrag einfügt oder einen vorhandenen Auftrag aktualisiert. Dieser Vorgang schließt ggf. alle Auftragsschritte und Zeitpläne ein.|  
|**RE-ENLIST**|Servervorgang, der bewirkt, dass der Zielserver die Eintragsinformationen, einschließlich des Abrufintervalls und der Zeitzone, erneut an die Multiserverdomäne sendet. Der Zielserver lädt auch die **MSXOperator** -Details erneut herunter.|  
|**SET-POLL**|Servervorgang, der festlegt, in welchem Intervall (in Sekunden) die Zielserver die Multiserverdomäne abfragen. Wenn angegeben, wird der *Wert* als erforderlicher Intervall Wert interpretiert und kann ein Wert zwischen **10** und **28.800**sein.|  
|**Begonnen**|Auftragsvorgang, der den Start der Auftragsausführung anfordert|  
|**Anzuhalten**|Auftragsvorgang, der das Beenden der Auftragsausführung anfordert|  
|**SYNC-TIME**|Servervorgang, der bewirkt, dass der Zielserver die Systemuhr mit der Multiserverdomäne synchronisiert. Dies ist ein kostenaufwendiger Vorgang und sollte deshalb nur selten und in begrenztem Umfang durchgeführt werden.|  
|**UPDATE**|Auftrags Vorgang, bei dem nur die **sysjobs** -Informationen für einen Auftrag und nicht die Auftrags Schritte oder Zeitpläne aktualisiert werden. Wird automatisch von **sp_update_job**aufgerufen.|  
  
`[ @object_type = ] 'object_type'` Der Objekttyp für den angegebenen Auftrag. *object_type* ist vom Datentyp **varchar (64)** und hat den Standardwert NULL. *object_type* kann entweder "Job" oder "Server" sein. Weitere Informationen zu gültigen *object_type*Werten finden Sie unter [sp_add_category &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-add-category-transact-sql.md).  
  
`[ @object_name = ] 'object_name'` Der Name des Objekts. *object_name* ist vom **Datentyp vom Datentyp sysname**und hat den Standardwert NULL. Wenn *object_type* Auftrag ist, ist *object_name*der Auftrags Name. Wenn *object_type*Server ist, ist *object_name*der Servername.  
  
`[ @target_server = ] 'target_server'` Der Name des Zielservers. *target_server* ist vom Datentyp **nvarchar (128)** und hat den Standardwert NULL.  
  
`[ @has_error = ] has_error` Gibt an, ob der Auftrag Fehler bestätigen soll. *has_error* ist vom Datentyp **tinyint**. der Standardwert ist NULL. der Wert gibt an, dass keine Fehler bestätigt werden sollen. der Wert **1** gibt an, dass alle Fehler bestätigt werden sollen.  
  
`[ @status = ] status` Der Status des Auftrags. *Status* ist vom Datentyp **tinyint**. der Standardwert ist NULL.  
  
`[ @date_posted = ] date_posted` Das Datum und die Uhrzeit, für die alle Einträge, die an oder nach dem angegebenen Datum und der angegebenen Uhrzeit vorgenommen werden, in das Resultset eingeschlossen werden sollen. *date_posted* ist vom **Datentyp DateTime**und hat den Standardwert NULL.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 **0** (Erfolg) oder **1** (Fehler)  
  
## <a name="result-sets"></a>Resultsets  
  
|Spaltenname|Datentyp|BESCHREIBUNG|  
|-----------------|---------------|-----------------|  
|**instance_id**|**int**|Eindeutige, ganzzahlige ID der Anweisung|  
|**source_server**|**nvarchar(30)**|Computername des Servers, vom dem die Anweisung stammt. In [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Version 7,0 ist dies immer der Computername des Master Servers (MSX).|  
|**operation_code**|**nvarchar(4000)**|Vorgangscode für die Anweisung|  
|**object_name**|**sysname**|Objekt, das von der Anweisung betroffen ist|  
|**object_id**|**uniqueidentifier**|ID des Objekts, das von der Anweisung betroffen ist (**job_id** für ein Auftrags Objekt oder 0x00 für ein Server Objekt), oder ein Datenwert, der für die **operation_code**spezifisch ist.|  
|**target_server**|**nvarchar(30)**|Zielserver, der diese Anweisung herunterladen soll|  
|**error_message**|**nvarchar(1024)**|Gegebenenfalls Fehlermeldung vom Zielserver, falls beim Verarbeiten dieser Anweisung ein Problem aufgetreten ist.<br /><br /> Hinweis: jede Fehlermeldung blockiert alle weiteren Downloads durch den Zielserver.|  
|**date_posted**|**datetime**|Datum, an dem die Anweisung für die Tabelle bereitgestellt wurde|  
|**date_downloaded**|**datetime**|Datum, an dem die Anweisung durch den Zielserver heruntergeladen wurde|  
|**status**|**tinyint**|Status des Auftrags:<br /><br /> **0** = Noch nicht heruntergeladen<br /><br /> **1** = erfolgreich heruntergeladen.|  
  
## <a name="permissions"></a>Berechtigungen  
 Die Berechtigungen zum Ausführen dieser Prozedur werden standardmäßig Mitgliedern der festen Server Rolle **sysadmin** zugewiesen.  
  
## <a name="examples"></a>Beispiele  
 Im folgenden Beispiel werden Zeilen in der `sysdownloadlist`-Tabelle für den Auftrag `NightlyBackups` aufgelistet.  
  
```  
USE msdb ;  
GO  
  
EXEC dbo.sp_help_downloadlist  
    @job_name = N'NightlyBackups',  
    @operation = N'UPDATE',   
    @object_type = N'JOB',   
    @object_name = N'NightlyBackups',  
    @target_server = N'SEATTLE2',   
    @has_error = 1,   
    @status = NULL,   
    @date_posted = NULL ;  
GO  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [Gespeicherte Systemprozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
