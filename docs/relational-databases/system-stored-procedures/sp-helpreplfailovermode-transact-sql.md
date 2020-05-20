---
title: sp_helpreplfailovermode (Transact-SQL) | Microsoft-Dokumentation
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
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 93793b697ea2e59f4725cf61d2d3fcec4ebdf579
ms.sourcegitcommit: 4d3896882c5930248a6e441937c50e8e027d29fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/05/2020
ms.locfileid: "82824453"
---
# <a name="sp_helpreplfailovermode-transact-sql"></a>sp_helpreplfailovermode (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Zeigt den aktuellen Failovermodus eines Abonnements an. Diese gespeicherte Prozedur wird auf dem Abonnenten für jede Datenbank ausgeführt. Weitere Informationen zu Failovermodi finden Sie unter [aktualisierbare Abonnements für die Transaktions Replikation](../../relational-databases/replication/transactional/updatable-subscriptions-for-transactional-replication.md).  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_helpreplfailovermode [ @publisher= ] 'publisher'   
    [ , [ @publisher_db = ] 'publisher_db' ]   
    [ , [ @publication = ] 'publication' ]   
    [ , [ @failover_mode_id= ] 'failover_mode_id'OUTPUT]   
    [ , [ @failover_mode = ] 'failover_mode'OUTPUT]   
```  
  
## <a name="arguments"></a>Argumente  
`[ @publisher = ] 'publisher'`Der Name des Verlegers, der am Update dieses Abonnenten teilnimmt. *Publisher* ist vom **Datentyp vom Datentyp sysname**und hat keinen Standardwert. Der Verleger muss bereits für das Veröffentlichen konfiguriert sein.  
  
`[ @publisher_db = ] 'publisher_db'`Der Name der Veröffentlichungs Datenbank. *publisher_db* ist vom **Datentyp vom Datentyp sysname**und hat keinen Standardwert.  
  
`[ @publication = ] 'publication'`Der Name der Veröffentlichung, die an der Aktualisierung dieses Abonnenten teilnimmt. *Publication*ist vom **Datentyp vom Datentyp sysname**und hat keinen Standardwert.  
  
`[ @failover_mode_id = ] 'failover_mode_id' OUTPUT`Gibt den ganzzahligen Wert des Failovermodus zurück und ist ein **Output** -Parameter. *failover_mode_id* ist vom Datentyp **tinyint** . der Standardwert ist **0**. Sie gibt **0** für sofortiges Aktualisieren und **1** für verzögertes Update über eine Warteschlange zurück.  
  
`[ @failover_mode = ] 'failover_mode' OUTPUT`Gibt den Modus zurück, in dem Datenänderungen auf dem Abonnenten vorgenommen werden. *failover_mode* ist vom Datentyp **nvarchar (10)** und hat den Standardwert NULL. Ist ein **Output** -Parameter.  
  
|Wert|BESCHREIBUNG|  
|-----------|-----------------|  
|**unmittelbar**|Sofortiges Update: Auf dem Abonnenten durchgeführte Updates werden sofort an den Verleger weitergegeben, indem ein Zweiphasencommitprotokoll (2PC) verwendet wird.|  
|**Warteschlange**|Verzögertes Update: Auf dem Abonnenten durchgeführte Updates werden in einer Warteschlange gespeichert.|  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 **0** (Erfolg) oder **1** (Fehler)  
  
## <a name="remarks"></a>Bemerkungen  
 **sp_helpreplfailovermode** wird bei der Momentaufnahme-oder Transaktions Replikation verwendet, bei der Abonnements für eine sofortige Aktualisierung mit verzögertem Update über eine Warteschlange als Failover aktiviert sind, falls ein Fehler aufgetreten ist.  
  
## <a name="permissions"></a>Berechtigungen  
 Nur Mitglieder der festen Server Rolle **sysadmin** oder der festen Daten Bank Rolle **db_owner** können **sp_helpreplfailovermode**ausführen.  
  
## <a name="see-also"></a>Weitere Informationen  
 [sp_setreplfailovermode &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-setreplfailovermode-transact-sql.md)  
  
  
