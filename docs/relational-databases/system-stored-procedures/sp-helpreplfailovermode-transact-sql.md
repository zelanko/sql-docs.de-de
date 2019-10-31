---
title: sp_helpreplfailovermode (Transact-SQL) | Microsoft Docs
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
ms.openlocfilehash: 5b9c8322507c78458110f47f579ec333c3e5e7a7
ms.sourcegitcommit: af6f66cc3603b785a7d2d73d7338961a5c76c793
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/30/2019
ms.locfileid: "73142843"
---
# <a name="sp_helpreplfailovermode-transact-sql"></a>sp_helpreplfailovermode (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Zeigt den aktuellen Failovermodus eines Abonnements an. Diese gespeicherte Prozedur wird auf dem Abonnenten für jede Datenbank ausgeführt. For more information about failover modes, see [Updatable Subscriptions for Transactional Replication](../../relational-databases/replication/transactional/updatable-subscriptions-for-transactional-replication.md).  
  
 ![Themenlinksymbol](../../database-engine/configure-windows/media/topic-link.gif "Themenlink (Symbol)") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_helpreplfailovermode [ @publisher= ] 'publisher'   
    [ , [ @publisher_db = ] 'publisher_db' ]   
    [ , [ @publication = ] 'publication' ]   
    [ , [ @failover_mode_id= ] 'failover_mode_id'OUTPUT]   
    [ , [ @failover_mode = ] 'failover_mode'OUTPUT]   
```  
  
## <a name="arguments"></a>Argumente  
`[ @publisher = ] 'publisher'` Is the name of the Publisher that is participating in the update of this Subscriber. *publisher* is **sysname**, with no default. Der Verleger muss bereits für das Veröffentlichen konfiguriert sein.  
  
`[ @publisher_db = ] 'publisher_db'` Is the name of the publication database. *publisher_db* is **sysname**, with no default.  
  
`[ @publication = ] 'publication'` Is the name of the publication that is participating in the update of this Subscriber. *Publication*ist vom **Datentyp vom Datentyp sysname**und hat keinen Standardwert.  
  
`[ @failover_mode_id = ] 'failover_mode_id' OUTPUT` gibt den ganzzahligen Wert des Failovermodus zurück und ist ein **Output** -Parameter. *failover_mode_id* ist vom Datentyp **tinyint** . der Standardwert ist **0**. Sie gibt **0** für sofortiges Aktualisieren und **1** für verzögertes Update über eine Warteschlange zurück.  
  
 [ **\@failover_mode =** ] **Ausgabe von "***failover_mode***"**  
 Gibt den Modus zurück, in dem Datenänderungen auf dem Abonnenten vorgenommen werden. *failover_mode* ist vom Datentyp **nvarchar (10)** und hat den Standardwert NULL. Ist ein **Output** -Parameter.  
  
|value|Description|  
|-----------|-----------------|  
|**unmittelbar**|Sofortiges Update: Auf dem Abonnenten durchgeführte Updates werden sofort an den Verleger weitergegeben, indem ein Zweiphasencommitprotokoll (2PC) verwendet wird.|  
|**Warteschlange**|Verzögertes Update: Auf dem Abonnenten durchgeführte Updates werden in einer Warteschlange gespeichert.|  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 **0** (Erfolg) oder **1** (Fehler)  
  
## <a name="remarks"></a>Bemerkungen  
 **sp_helpreplfailovermode** wird bei der Momentaufnahme-oder Transaktions Replikation verwendet, bei der Abonnements für das sofortige Aktualisieren mit verzögertem Update über eine Warteschlange als Failover aktiviert werden, falls ein Fehler aufgetreten ist.  
  
## <a name="permissions"></a>Berechtigungen  
 Nur Mitglieder der festen Server Rolle **sysadmin** oder der festen Daten Bank Rolle **db_owner** können **sp_helpreplfailovermode**ausführen.  
  
## <a name="see-also"></a>Weitere Informationen finden Sie unter  
 [sp_setreplfailovermode &#40;(Transact-SQL)&#41;](../../relational-databases/system-stored-procedures/sp-setreplfailovermode-transact-sql.md)  
  
  
