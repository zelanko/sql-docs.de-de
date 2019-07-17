---
title: Sp_helpmergepartition (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_helpmergepartition
- sp_helpmergepartition_TSQL
helpviewer_keywords:
- sp_helpmergepartition
ms.assetid: 184188cc-f519-445d-97ce-aae38f1eb550
author: stevestein
ms.author: sstein
ms.openlocfilehash: 01155b1fb294660c92bfa975bc04de8f748b730f
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68137663"
---
# <a name="sphelpmergepartition-transact-sql"></a>sp_helpmergepartition (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Gibt Partitionsinformationen für die angegebene Mergeveröffentlichung zurück. Diese gespeicherte Prozedur wird auf dem Verleger für jede Datenbank ausgeführt.  
  
 ![Themenlinksymbol](../../database-engine/configure-windows/media/topic-link.gif "Topic link icon") [Transact-SQL Syntax Conventions (Transact-SQL-Syntaxkonventionen)](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_helpmergepartition [ @publication= ] 'publication'   
    [ , [ @suser_sname = ] 'suser_sname' ]  
    [ , [ @host_name = ] 'host_name' ]  
```  
  
## <a name="arguments"></a>Argumente  
`[ @publication = ] 'publication'` Ist der Name der Veröffentlichung. *Veröffentlichung* ist **Sysname**, hat keinen Standardwert.  
  
`[ @suser_sname = ] 'suser_sname'` SUSER_SNAME-Wert, der zum Definieren einer Partitions verwendet wird. *SUSER_SNAME* ist **Sysname**, hat den Standardwert NULL. Geben Sie diesen Parameter an, um das Resultset auf die Partitionen einzuschränken, bei denen SUSER_SNAME zu dem angegebenen Wert aufgelöst wird.  
  
> [!NOTE]  
>  Wenn *Suser_sname* angegeben wird, *Host_name* darf NULL sein.  
  
`[ @host_name = ] 'host_name'` Der HOST_NAME-Wert wird zum Definieren einer Partitions verwendet werden. *HOST_NAME* ist **Sysname**, hat den Standardwert NULL. Geben Sie diesen Parameter an, um das Resultset auf die Partitionen einzuschränken, bei denen HOST_NAME zu dem angegebenen Wert aufgelöst wird.  
  
> [!NOTE]  
>  Wenn *Suser_sname* angegeben wird, *Host_name* darf NULL sein.  
  
## <a name="result-sets"></a>Resultsets  
  
|Spaltenname|Datentyp|Beschreibung|  
|-----------------|---------------|-----------------|  
|**partition**|**int**|Identifiziert die Abonnentenpartition.|  
|**HOST_NAME**|**sysname**|Verwendete Wert beim Erstellen der Partition für ein Abonnement, den Wert des gefiltert wird die [HOST_NAME](../../t-sql/functions/host-name-transact-sql.md) -Funktion beim Abonnenten.|  
|**suser_sname**|**sysname**|Verwendete Wert beim Erstellen der Partition für ein Abonnement, den Wert des gefiltert wird die [SUSER_SNAME](../../t-sql/functions/suser-sname-transact-sql.md) -Funktion beim Abonnenten.|  
|**dynamic_snapshot_location**|**nvarchar(255)**|Speicherort der gefilterten Datenmomentaufnahme für die Abonnentenpartition.|  
|**date_refreshed**|**datetime**|Das Datum, an dem der Momentaufnahmeauftrag zuletzt ausgeführt wurde, um eine gefilterte Datenmomentaufnahme für die Partition zu generieren.|  
|**dynamic_snapshot_jobid**|**uniqueidentifier**|Identifiziert den Auftrag, der die gefilterte Datenmomentaufnahme für eine Partition erstellt.|  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 **0** (Erfolg) oder **1** (Fehler)  
  
## <a name="remarks"></a>Hinweise  
 **Sp_helpmergepartition** wird bei der Mergereplikation verwendet.  
  
## <a name="permissions"></a>Berechtigungen  
 Nur Mitglieder der der **Sysadmin** Serverrolle und die **Db_owner** feste Datenbankrolle können ausführen **Sp_helpmergepartition**.  
  
## <a name="see-also"></a>Siehe auch  
 [sp_addmergepartition &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addmergepartition-transact-sql.md)   
 [sp_dropmergepartition &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-dropmergepartition-transact-sql.md)  
  
  
