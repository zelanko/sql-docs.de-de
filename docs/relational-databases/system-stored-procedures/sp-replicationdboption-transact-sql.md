---
title: sp_replicationdboption (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_replicationdboption_TSQL
- sp_replicationdboption
helpviewer_keywords:
- sp_replicationdboption
ms.assetid: d021864e-3f21-4d1a-89df-6c1086f753bf
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: ac51409db23f4b8eefb3616d5daf5ca43b3ab0f6
ms.sourcegitcommit: 728a4fa5a3022c237b68b31724fce441c4e4d0ab
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/03/2019
ms.locfileid: "68771250"
---
# <a name="spreplicationdboption-transact-sql"></a>sp_replicationdboption (Transact-SQL)
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]

  Legt für die angegebene Datenbank eine Replikationsdatenbankoption fest. Diese gespeicherte Prozedur wird auf dem Verleger oder Abonnenten für jede Datenbank ausgeführt.  
  
 ![Themenlinksymbol](../../database-engine/configure-windows/media/topic-link.gif "Topic link icon") [Transact-SQL Syntax Conventions (Transact-SQL-Syntaxkonventionen)](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_replicationdboption [ @dbname= ] 'db_name'   
        , [ @optname= ] 'optname'   
        , [ @value= ] 'value'   
    [ , [ @ignore_distributor= ] ignore_distributor ]  
    [ , [ @from_scripting = ] from_scripting ]  
```  
  
## <a name="arguments"></a>Argumente  
 **[@dbname=** ] **'***dbname***'**  
 Die Datenbank, für die die Replikationsdatenbankoption festgelegt wird. *db_name* ist vom **Datentyp vom Datentyp sysname**und hat keinen Standardwert.  
  
 **[@optname=** ] **'***optname***'**  
 Die Replikationsdatenbankoption, die aktiviert oder deaktiviert werden soll. *optname* ist vom **Datentyp vom Datentyp sysname**. die folgenden Werte sind möglich:  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|**Zusammenführen der Veröffentlichung**|Die Datenbank kann für die Mergeveröffentlichung verwendet werden.|  
|**publish**|Die Datenbank kann für andere Veröffentlichungstypen verwendet werden.|  
|**subscribe**|Die Datenbank ist eine Abonnementdatenbank.|  
|**Synchronisierung mit Sicherung**|Die Datenbank ist für eine koordinierte Sicherung aktiviert. Weitere Informationen finden Sie unter [aktivieren koordinierter Sicherungen für die Transaktions Replikations &#40;Replikation mit Transact-SQL-Programmierung&#41;](../../relational-databases/replication/administration/enable-coordinated-backups-for-transactional-replication.md).|  
  
`[ @value = ] 'value'`Gibt an, ob die angegebene Replikations Datenbankoption aktiviert oder deaktiviert werden soll. *value* ist vom **Datentyp vom Datentyp sysname**und kann **true** oder **false**sein. Wenn dieser Wert " **false** " und " *optname* " eine **Mergeveröffentlichung**ist, werden die Abonnements für die veröffentlichte Datenbank des Merge ebenfalls gelöscht.  
  
`[ @ignore_distributor = ] ignore_distributor`Gibt an, ob diese gespeicherte Prozedur ausgeführt wird, ohne eine Verbindung mit dem Verteiler herzustellen. *ignore_distributor* ist vom Typ **Bit**. der Standardwert ist **0**. Dies bedeutet, dass der Verteiler mit dem neuen Status der Veröffentlichungs Datenbank verbunden und aktualisiert werden soll. Der Wert **1** sollte nur angegeben werden, wenn auf den Verteiler nicht zugegriffen werden kann und **sp_replicationdboption** zum Deaktivieren der Veröffentlichung verwendet wird.  
  
`[ @from_scripting = ] from_scripting` [!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 **0** (Erfolg) oder **1** (Fehler)  
  
## <a name="remarks"></a>Hinweise  
 **sp_replicationdboption** wird bei der Momentaufnahme-, Transaktions-und Mergereplikation verwendet.  
  
 Diese Prozedur erstellt oder löscht bestimmte Replikationssystemtabellen, Sicherheitskonten usw. in Abhängigkeit von den gegebenen Optionen. Legt das entsprechende Kategoriebit in der **Master. sysdatenbanken** -Systemtabelle fest und erstellt die erforderlichen Systemtabellen.  
  
 Das Veröffentlichen kann nur deaktiviert werden, wenn die Veröffentlichungsdatenbank online ist. Wenn für die Veröffentlichungsdatenbank eine Datenbankmomentaufnahme vorhanden ist, muss diese vor dem Deaktivieren des Veröffentlichens gelöscht werden. Eine Datenbankmomentaufnahme ist eine schreibgeschützte Offlinekopie einer Datenbank und steht nicht in Verbindung mit einer Replikationsmomentaufnahme. Weitere Informationen finden Sie unter [Datenbankmomentaufnahmen &#40;SQL Server&#41;](../../relational-databases/databases/database-snapshots-sql-server.md).  
  
## <a name="permissions"></a>Berechtigungen  
 Nur Mitglieder der festen Server Rolle **sysadmin** können **sp_replicationdboption**ausführen.  
  
## <a name="see-also"></a>Siehe auch  
 [Konfigurieren der Veröffentlichung und der Verteilung](../../relational-databases/replication/configure-publishing-and-distribution.md)   
 [Create a Publication](../../relational-databases/replication/publish/create-a-publication.md)   
 [Löschen einer Veröffentlichung](../../relational-databases/replication/publish/delete-a-publication.md)   
 [Deaktivieren der Veröffentlichung und Verteilung](../../relational-databases/replication/disable-publishing-and-distribution.md)   
 [sys.sysdatabases &#40;Transact-SQL&#41;](../../relational-databases/system-compatibility-views/sys-sysdatabases-transact-sql.md)   
 [Gespeicherte Automatisierungsprozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/replication-stored-procedures-transact-sql.md)  
  
  
