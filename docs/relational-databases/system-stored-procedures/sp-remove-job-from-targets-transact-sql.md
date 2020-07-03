---
title: sp_remove_job_from_targets (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_remove_job_from_targets_TSQL
- sp_remove_job_from_targets
dev_langs:
- TSQL
helpviewer_keywords:
- sp_remove_job_from_targets
ms.assetid: b8171fb1-c11d-4244-8618-a12e28a150ce
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: de4d2686066e10f1eb9f80862241d1d1a47cf6b7
ms.sourcegitcommit: f7ac1976d4bfa224332edd9ef2f4377a4d55a2c9
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2020
ms.locfileid: "85891497"
---
# <a name="sp_remove_job_from_targets-transact-sql"></a>sp_remove_job_from_targets (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Entfernt den angegebenen Auftrag auf den jeweiligen Zielservern oder Zielservergruppen.  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_remove_job_from_targets [ @job_id = ] job_id   
     | [ @job_name = ] 'job_name'   
     [ , [ @target_server_groups = ] 'target_server_groups' ]   
     [ , [ @target_servers = ] 'target_servers' ]  
```  
  
## <a name="arguments"></a>Argumente  
`[ @job_id = ] job_id`Die ID des Auftrags, aus dem die angegebenen Zielserver oder Zielserver Gruppen entfernt werden sollen. Es muss entweder *job_id* oder *job_name* angegeben werden, beide Angaben können jedoch nicht angegeben werden. *job_id* ist vom Datentyp **uniqueidentifier**und hat den Standardwert NULL.  
  
`[ @job_name = ] 'job_name'`Der Name des Auftrags, aus dem die angegebenen Zielserver oder Zielserver Gruppen entfernt werden sollen. Es muss entweder *job_id* oder *job_name* angegeben werden, beide Angaben können jedoch nicht angegeben werden. *job_name* ist vom **Datentyp vom Datentyp sysname**und hat den Standardwert NULL.  
  
`[ @target_server_groups = ] 'target_server_groups'`Eine durch Trennzeichen getrennte Liste der Zielserver Gruppen, die aus dem angegebenen Auftrag entfernt werden sollen. *target_server_groups* ist vom Datentyp **nvarchar (1024)** und hat den Standardwert NULL.  
  
`[ @target_servers = ] 'target_servers'`Eine durch Trennzeichen getrennte Liste von Ziel Servern, die aus dem angegebenen Auftrag entfernt werden sollen. *target_servers* ist vom Datentyp **nvarchar (1024)** und hat den Standardwert NULL.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 **0** (Erfolg) oder **1** (Fehler)  
  
## <a name="permissions"></a>Berechtigungen  
 Die Berechtigungen zum Ausführen dieser Prozedur werden standardmäßig Mitgliedern der festen Server Rolle **sysadmin** zugewiesen.  
  
## <a name="examples"></a>Beispiele  
 Im folgenden Beispiel wird der zuvor erstellte Auftrag `Weekly Sales Backups` aus der Zielservergruppe `Servers Processing Customer Orders` und von den Servern `SEATTLE1` und `SEATTLE2` entfernt.  
  
```  
USE msdb ;  
GO  
  
EXEC dbo.sp_remove_job_from_targets  
    @job_name = N'Weekly Sales Backups',  
    @target_server_groups = N'Servers Processing Customer Orders',   
    @target_servers = N'SEATTLE2,SEATTLE1' ;  
GO  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [sp_apply_job_to_targets &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-apply-job-to-targets-transact-sql.md)   
 [sp_delete_jobserver &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-delete-jobserver-transact-sql.md)   
 [Gespeicherte Systemprozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
