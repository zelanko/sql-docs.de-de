---
title: Sp_helpreplfailovermode (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_helpreplfailovermode
- sp_helpreplfailovermode_TSQL
helpviewer_keywords:
- sp_helpreplfailovermode
ms.assetid: d1090e42-6840-4bf6-9aa9-327fd8987ec2
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 19fafb4b3ef3737018aaae21992f0b6a859c7ef3
ms.sourcegitcommit: ceb7e1b9e29e02bb0c6ca400a36e0fa9cf010fca
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/03/2018
ms.locfileid: "52796430"
---
# <a name="sphelpreplfailovermode-transact-sql"></a>sp_helpreplfailovermode (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Zeigt den aktuellen Failovermodus eines Abonnements an. Diese gespeicherte Prozedur wird auf dem Abonnenten für jede Datenbank ausgeführt. Weitere Informationen zu failovermodi finden Sie unter [aktualisierbaren Abonnements für Transaktionsreplikationen](../../relational-databases/replication/transactional/updatable-subscriptions-for-transactional-replication.md).  
  
 ![Themenlinksymbol](../../database-engine/configure-windows/media/topic-link.gif "Topic link icon") [Transact-SQL Syntax Conventions (Transact-SQL-Syntaxkonventionen)](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_helpreplfailovermode [ @publisher= ] 'publisher'   
    [ , [ @publisher_db = ] 'publisher_db' ]   
    [ , [ @publication = ] 'publication' ]   
    [ , [ @failover_mode_id= ] 'failover_mode_id'OUTPUT]   
    [ , [ @failover_mode = ] 'failover_mode'OUTPUT]   
```  
  
## <a name="arguments"></a>Argumente  
 [ **@publisher=**] **'***publisher***'**  
 Der Name des Verlegers, der am Update dieses Abonnenten teilnimmt. *Publisher* ist **Sysname**, hat keinen Standardwert. Der Verleger muss bereits für das Veröffentlichen konfiguriert sein.  
  
 [  **@publisher_db =**] **"***Publisher_db***"**  
 Der Name der Veröffentlichungsdatenbank. *Publisher_db* ist **Sysname**, hat keinen Standardwert.  
  
 [ **@publication=**] **'***publication***'**  
 Der Name der Veröffentlichung, die in das Update dieses Abonnenten einbezogen wird. *Veröffentlichung*ist **Sysname**, hat keinen Standardwert.  
  
 [  **@failover_mode_id=**] **"***Failover_mode_id***' Ausgabe**  
 Gibt den Ganzzahlwert des Failovermodus zurück und ist ein **Ausgabe** Parameter. *Failover_mode_id* ist eine **Tinyint** hat den Standardwert **0**. Es gibt **0** für sofortige Updates und **1** Aktualisierung in der Warteschlange.  
  
 [**@failover_mode=**] **"***Failover_mode***' Ausgabe**  
 Gibt den Modus zurück, in dem Datenänderungen auf dem Abonnenten vorgenommen werden. *Failover_mode* ist eine **nvarchar(10)** hat den Standardwert NULL. Ist ein **Ausgabe** Parameter.  
  
|Wert|Description|  
|-----------|-----------------|  
|**Sofortige**|Sofortiges Update: Auf dem Abonnenten durchgeführte Updates werden sofort an den Verleger weitergegeben, indem ein Zweiphasencommitprotokoll (2PC) verwendet wird.|  
|**In der Warteschlange**|Verzögertes Update: Auf dem Abonnenten durchgeführte Updates werden in einer Warteschlange gespeichert.|  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 **0** (Erfolg) oder **1** (Fehler)  
  
## <a name="remarks"></a>Hinweise  
 **Sp_helpreplfailovermode** wird für die Abonnements für sofortige Updates mit aktiviert sind als Failover bei einem Ausfall in der Warteschlange bei Momentaufnahme- oder Transaktionsreplikation verwendet.  
  
## <a name="permissions"></a>Berechtigungen  
 Nur Mitglieder der der **Sysadmin** -Serverrolle sein oder die **Db_owner** feste Datenbankrolle können ausführen **Sp_helpreplfailovermode**.  
  
## <a name="see-also"></a>Siehe auch  
 [Sp_setreplfailovermode &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-setreplfailovermode-transact-sql.md)  
  
  
