---
title: sp_dropdynamicsnapshot_job (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_dropdynamicsnapshot_job_TSQL
- sp_dropdynamicsnapshot_job
helpviewer_keywords:
- sp_dropdynamicsnapshot_job
ms.assetid: 128e428a-01b3-4062-8c6e-d22d5fa268a9
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 0c9f33c4f50f77ed8ded47b6d7f69a2476f49227
ms.sourcegitcommit: 4d3896882c5930248a6e441937c50e8e027d29fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/05/2020
ms.locfileid: "82830164"
---
# <a name="sp_dropdynamicsnapshot_job-transact-sql"></a>sp_dropdynamicsnapshot_job (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Entfernt einen Auftrag für eine Momentaufnahme gefilterter Daten für eine Veröffentlichung mit parametrisierten Zeilenfiltern. Diese gespeicherte Prozedur wird auf dem Verleger für die Veröffentlichungs Datenbank ausgeführt. Wenn der Auftrag gelöscht wird, werden alle zugehörigen Daten aus der [MSdynamicsnapshotjobs](../../relational-databases/system-tables/msdynamicsnapshotjobs-transact-sql.md) -Systemtabelle gelöscht.  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_dropdynamicsnapshot_job [ @publication = ] 'publication'   
    [ , [ @dynamic_snapshot_jobname = ] 'dynamic_snapshot_jobname' ]   
    [ , [ @dynamic_snapshot_jobid = ] 'dynamic_snapshot_jobid' ]   
    [ , [ @ignore_distributor =] ignore_distributor ]  
```  
  
## <a name="arguments"></a>Argumente  
`[ @publication = ] 'publication'`Der Name der Veröffentlichung, aus der der Auftrag für die Momentaufnahme gefilterter Daten entfernt wird. *Publication* ist vom **Datentyp vom Datentyp sysname**und hat keinen Standardwert.  
  
`[ @dynamic_snapshot_jobname = ] 'dynamic_snapshot_jobname'`Der Name des Auftrags für die Momentaufnahme gefilterter Daten, der entfernt wird. *dynamic_snapshot_jobname*ist vom Datentyp sysname. wenn er nicht angegeben wird, werden standardmäßig alle Auftrags Namen verwendet, die *dynamic_snapshot_jobid*zugeordnet sind.  
  
`[ @dynamic_snapshot_jobid = ] 'dynamic_snapshot_jobid'`Ein Bezeichner für den Auftrag für die Momentaufnahme gefilterter Daten. *dynamic_snapshot_jobid*ist vom Datentyp **uniqueidentifier**und hat den Standardwert NULL.  
  
> [!IMPORTANT]  
>  Es können nur *dynamic_snapshot_jobid*oder *dynamic_snapshot_jobname* angegeben werden. Wenn für *dynamic_snapshot_jobid*oder *dynamic_snapshot_jobname*keine Werte angegeben werden, werden alle Aufträge für die dynamische Momentaufnahme für die Veröffentlichung entfernt.  
  
`[ @ignore_distributor = ] ignore_distributor`*ignore_distributor* ist vom Typ **Bit**. der Standardwert ist **0**. Dieser Parameter kann verwendet werden, um einen Auftrag für eine dynamische Momentaufnahme zu löschen, ohne Cleanuptasks auf dem Verteiler auszuführen.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 **0** (Erfolg) oder **1** (Fehler)  
  
## <a name="remarks"></a>Bemerkungen  
 **sp_dropdynamicsnapshot** wird bei der Mergereplikation verwendet.  
  
## <a name="permissions"></a>Berechtigungen  
 Nur Mitglieder der festen Server Rolle **sysadmin** oder der festen Daten Bank Rolle **db_owner** können **sp_dropdynamicsnapshot**ausführen.  
  
## <a name="see-also"></a>Weitere Informationen  
 [sp_adddynamicsnapshot_job &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-adddynamicsnapshot-job-transact-sql.md)  
  
  
