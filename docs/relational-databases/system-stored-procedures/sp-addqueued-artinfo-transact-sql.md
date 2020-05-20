---
title: sp_addqueued_artinfo (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_addqueued_artinfo
- sp_addqueued_artinfo_TSQL
helpviewer_keywords:
- sp_addqueued_artinfo
ms.assetid: decdb6eb-3dcd-4053-a21d-fd367c3fbafb
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 33769260b25ef3f6127f6f12ac54af07c5951ad1
ms.sourcegitcommit: 4d3896882c5930248a6e441937c50e8e027d29fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/05/2020
ms.locfileid: "82820667"
---
# <a name="sp_addqueued_artinfo-transact-sql"></a>sp_addqueued_artinfo (Transact-SQL)
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]

  
  
> [!IMPORTANT]  
>  Die [sp_script_synctran_commands](../../relational-databases/system-stored-procedures/sp-script-synctran-commands-transact-sql.md) Prozedur sollte anstelle **sp_addqueued_artinfo**verwendet werden. [sp_script_synctran_commands](../../relational-databases/system-stored-procedures/sp-script-synctran-commands-transact-sql.md) generiert ein Skript, das die **sp_addqueued_artinfo** und **sp_addsynctrigger** Aufrufe enthält.  
  
 Erstellt die [MSsubscription_articles](../../relational-databases/system-tables/mssubscription-articles-transact-sql.md) Tabelle auf dem Abonnenten, die zum Nachverfolgen von Artikel Abonnement Informationen (verzögertes Aktualisieren über eine Warteschlange und sofortiges Update mit verzögertem Update als Failover) verwendet wird. Diese gespeicherte Prozedur wird auf dem Abonnenten für die Abonnement Datenbank ausgeführt.  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_addqueued_artinfo [ @artid= ] 'artid'  
        , [ @article= ] 'article'  
        , [ @publisher = ] 'publisher'  
        , [ @publisher_db = ] 'publisher_db'  
        , [ @publication = ] 'publication'  
        , [ @dest_table= ] 'dest_table'  
        , [ @owner = ] 'owner'  
        , [ @cft_table= ] 'cft_table'  
```  
  
## <a name="arguments"></a>Argumente  
`[ @artid = ] 'artid'`Der Name der Artikel-ID. *artid* ist vom Datentyp **int**und hat keinen Standardwert  
  
`[ @article = ] 'article'`Der Name des Artikels, für den ein Skript erstellt werden soll. *Artikel* ist vom **Datentyp vom Datentyp sysname**und hat keinen Standardwert  
  
`[ @publisher = ] 'publisher'`Der Name des Verleger Servers. *Publisher* ist vom **Datentyp vom Datentyp sysname**und hat keinen Standardwert.  
  
`[ @publisher_db = ] 'publisher_db'`Der Name der Verleger Datenbank. *publisher_db* ist vom **Datentyp vom Datentyp sysname**und hat keinen Standardwert.  
  
`[ @publication = ] 'publication'`Der Name der Veröffentlichung, für die ein Skript erstellt werden soll. *Publication* ist vom **Datentyp vom Datentyp sysname**und hat keinen Standardwert.  
  
`[ @dest_table = ] _'dest_table'`Der Name der Ziel Tabelle. *dest_table* ist vom **Datentyp vom Datentyp sysname**und hat keinen Standardwert.  
  
 [** @owner =** ] **'**_Besitzer_**'**  
 Entspricht dem Eigentümer des Abonnements. *Owner* ist vom **Datentyp vom Datentyp sysname**und hat keinen Standardwert.  
  
`[ @cft_table = ] 'cft_table'`Der Name der Konflikt Tabelle mit verzögertem Update über eine Warteschlange für diesen Artikel. *cft_table*ist vom **Datentyp vom Datentyp sysname**und hat keinen Standardwert.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 **0** (Erfolg) oder **1** (Fehler)  
  
## <a name="remarks"></a>Bemerkungen  
 **sp_addqueued_artinfo** wird von der Verteilungs-Agent als Teil der Abonnement Initialisierung verwendet. Diese gespeicherte Prozedur wird normalerweise nicht von Benutzern ausgeführt, kann jedoch hilfreich sein, wenn der Benutzer manuell ein Abonnement einrichten muss.  
  
 [sp_script_synctran_commands](../../relational-databases/system-stored-procedures/sp-script-synctran-commands-transact-sql.md) anstelle **sp_addqueued_artinfo**.  
  
## <a name="permissions"></a>Berechtigungen  
 Nur Mitglieder der festen Server Rolle **sysadmin** oder der festen Daten Bank Rolle **db_owner** können **sp_addqueued_artinfo**ausführen.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Aktualisierbare Abonnements für die Transaktions Replikation](../../relational-databases/replication/transactional/updatable-subscriptions-for-transactional-replication.md)   
 [sp_script_synctran_commands &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-script-synctran-commands-transact-sql.md)   
 [MSsubscription_articles &#40;Transact-SQL-&#41;](../../relational-databases/system-tables/mssubscription-articles-transact-sql.md)   
 [Gespeicherte Systemprozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
