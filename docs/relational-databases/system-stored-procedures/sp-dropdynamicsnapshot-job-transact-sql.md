---
title: Sp_dropdynamicsnapshot_job (Transact-SQL) | Microsoft-Dokumentation
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
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: e4612c7b20e448eecbd6c83a3d09d0796dcff542
ms.sourcegitcommit: 7aa6beaaf64daf01b0e98e6c63cc22906a77ed04
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/09/2019
ms.locfileid: "54126260"
---
# <a name="spdropdynamicsnapshotjob-transact-sql"></a>sp_dropdynamicsnapshot_job (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Entfernt einen Auftrag für eine Momentaufnahme gefilterter Daten für eine Veröffentlichung mit parametrisierten Zeilenfiltern. Diese gespeicherte Prozedur wird auf dem Verleger für die Veröffentlichungsdatenbank ausgeführt. Wenn der Auftrag gelöscht wird, wird alle zugehörigen Daten gelöscht, von der [MSdynamicsnapshotjobs](../../relational-databases/system-tables/msdynamicsnapshotjobs-transact-sql.md) -Systemtabelle.  
  
 ![Themenlinksymbol](../../database-engine/configure-windows/media/topic-link.gif "Topic link icon") [Transact-SQL Syntax Conventions (Transact-SQL-Syntaxkonventionen)](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_dropdynamicsnapshot_job [ @publication = ] 'publication'   
    [ , [ @dynamic_snapshot_jobname = ] 'dynamic_snapshot_jobname' ]   
    [ , [ @dynamic_snapshot_jobid = ] 'dynamic_snapshot_jobid' ]   
    [ , [ @ignore_distributor =] ignore_distributor ]  
```  
  
## <a name="arguments"></a>Argumente  
 [  **@publication=**] **"**_Veröffentlichung_**"**  
 Der Name der Veröffentlichung, aus der der Auftrag für die Momentaufnahme gefilterter Daten entfernt wird. *Veröffentlichung* ist **Sysname**, hat keinen Standardwert.  
  
 [ **@dynamic_snapshot_jobname**=] **"**_Dynamic_snapshot_jobname_**"**  
 Der Name des Auftrags für die Momentaufnahme gefilterter Daten, der entfernt wird. *Dynamic_snapshot_jobname*ist vom Datentyp Sysname und ist dies nicht bereitgestellten Standardwerte Auftragsname zugeordneten *Dynamic_snapshot_jobid*.  
  
 [ **@dynamic_snapshot_jobid**=] **"**_Dynamic_snapshot_jobid_**"**  
 Der Bezeichner des Auftrags für die Momentaufnahme gefilterter Daten, der entfernt wird. *Dynamic_snapshot_jobid*ist **Uniqueidentifier**, mit dem Standardwert NULL.  
  
> [!IMPORTANT]  
>  Nur *Dynamic_snapshot_jobid*oder *Dynamic_snapshot_jobname* kann angegeben werden. Wenn Werte nicht, entweder angegeben werden *Dynamic_snapshot_jobid*oder *Dynamic_snapshot_jobname*, werden alle dynamischen Snapshot-Aufträge für die Veröffentlichung entfernt.  
  
 [  **@ignore_distributor =**] *Ignore_distributor*  
 *Ignore_distributor* ist **Bit**, hat den Standardwert **0**. Dieser Parameter kann verwendet werden, um einen Auftrag für eine dynamische Momentaufnahme zu löschen, ohne Cleanuptasks auf dem Verteiler auszuführen.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 **0** (Erfolg) oder **1** (Fehler)  
  
## <a name="remarks"></a>Hinweise  
 **Sp_dropdynamicsnapshot** wird bei der Mergereplikation verwendet.  
  
## <a name="permissions"></a>Berechtigungen  
 Nur Mitglieder der der **Sysadmin** -Serverrolle sein oder **Db_owner** feste Datenbankrolle können ausführen **Sp_dropdynamicsnapshot**.  
  
## <a name="see-also"></a>Siehe auch  
 [Sp_adddynamicsnapshot_job &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-adddynamicsnapshot-job-transact-sql.md)  
  
  
