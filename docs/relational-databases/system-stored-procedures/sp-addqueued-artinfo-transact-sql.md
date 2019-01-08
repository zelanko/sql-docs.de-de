---
title: Sp_addqueued_artinfo (Transact-SQL) | Microsoft-Dokumentation
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
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: c326a8e3a5fa2bd95f536d434ff9782952ba70d3
ms.sourcegitcommit: 37310da0565c2792aae43b3855bd3948fd13e044
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/18/2018
ms.locfileid: "53590895"
---
# <a name="spaddqueuedartinfo-transact-sql"></a>sp_addqueued_artinfo (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  
  
> [!IMPORTANT]  
>  Die [Sp_script_synctran_commands](../../relational-databases/system-stored-procedures/sp-script-synctran-commands-transact-sql.md) Prozedur sollte verwendet werden, anstelle von **Sp_addqueued_artinfo**. [Sp_script_synctran_commands](../../relational-databases/system-stored-procedures/sp-script-synctran-commands-transact-sql.md) generiert ein Skript, enthält die **Sp_addqueued_artinfo** und **Sp_addsynctrigger** aufrufen.  
  
 Erstellt die [MSsubscription_articles](../../relational-databases/system-tables/mssubscription-articles-transact-sql.md) Tabelle auf dem Abonnenten, die verwendet wird, um artikelabonnementinformationen (verzögertes Update und sofortiges Aktualisieren mit verzögertem Update über als Failover) nachzuverfolgen. Diese gespeicherte Prozedur wird auf dem Abonnenten für die Abonnementdatenbank ausgeführt.  
  
 ![Themenlinksymbol](../../database-engine/configure-windows/media/topic-link.gif "Topic link icon") [Transact-SQL Syntax Conventions (Transact-SQL-Syntaxkonventionen)](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
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
 [  **@artid=** ] **"**_Artid_**"**  
 Entspricht dem Namen der Artikel-ID. *Artid* ist **Int**, hat keinen Standardwert  
  
 [  **@article=**] **"**_Artikel_**"**  
 Der Name des Artikels, für den ein Skript erstellt werden soll. *Artikel* ist **Sysname**, hat keinen Standardwert  
  
 [  **@publisher=**] **"**_Verleger_**"**  
 Entspricht dem Namen des Verlegerservers. *Publisher* ist **Sysname**, hat keinen Standardwert.  
  
 [  **@publisher_db=**] **"**_Publisher_db_**"**  
 Der Name der Verlegerdatenbank. *Publisher_db* ist **Sysname**, hat keinen Standardwert.  
  
 [  **@publication=**] **"**_Veröffentlichung_**"**  
 Der Name der Veröffentlichung, für die ein Skript erstellt werden soll. *Veröffentlichung* ist **Sysname**, hat keinen Standardwert.  
  
 [  **@dest_table=** ] _' Dest_table_**"**  
 Entspricht dem Namen der Zieltabelle. *Dest_table* ist **Sysname**, hat keinen Standardwert.  
  
 [ **@owner =** ] **"**_Besitzer_**"**  
 Entspricht dem Eigentümer des Abonnements. *Besitzer* ist **Sysname**, hat keinen Standardwert.  
  
 [  **@cft_table=** ] **"**_Cft_table_**"**  
 Entspricht dem Namen der in die Warteschlange aufgenommenen Konflikttabelle für diesen Artikel, die derzeit aktualisiert wird. *Cft_table*ist **Sysname**, hat keinen Standardwert.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 **0** (Erfolg) oder **1** (Fehler)  
  
## <a name="remarks"></a>Hinweise  
 **Sp_addqueued_artinfo** wird vom Verteilungs-Agent als Teil der abonnementinitialisierung verwendet. Diese gespeicherte Prozedur wird normalerweise nicht von Benutzern ausgeführt, kann jedoch hilfreich sein, wenn der Benutzer manuell ein Abonnement einrichten muss.  
  
 [Sp_script_synctran_commands](../../relational-databases/system-stored-procedures/sp-script-synctran-commands-transact-sql.md) anstelle von **Sp_addqueued_artinfo**.  
  
## <a name="permissions"></a>Berechtigungen  
 Nur Mitglieder der der **Sysadmin** -Serverrolle sein oder **Db_owner** feste Datenbankrolle können ausführen **Sp_addqueued_artinfo**.  
  
## <a name="see-also"></a>Siehe auch  
 [Updatable Subscriptions for Transactional Replication](../../relational-databases/replication/transactional/updatable-subscriptions-for-transactional-replication.md)   
 [Sp_script_synctran_commands &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-script-synctran-commands-transact-sql.md)   
 [MSsubscription_articles &#40;Transact-SQL&#41;](../../relational-databases/system-tables/mssubscription-articles-transact-sql.md)   
 [Gespeicherte Systemprozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
