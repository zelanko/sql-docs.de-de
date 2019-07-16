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
ms.openlocfilehash: a0f94fbf686e9b9bd9fd1b6780b298c661ce42f6
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68031007"
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
`[ @artid = ] 'artid'` Der Name der Artikel-ID. *Artid* ist **Int**, hat keinen Standardwert  
  
`[ @article = ] 'article'` Ist der Name des Artikels geschrieben werden sollen. *Artikel* ist **Sysname**, hat keinen Standardwert  
  
`[ @publisher = ] 'publisher'` Ist der Name des Verlegerservers. *Publisher* ist **Sysname**, hat keinen Standardwert.  
  
`[ @publisher_db = ] 'publisher_db'` Ist der Name der Verlegerdatenbank. *Publisher_db* ist **Sysname**, hat keinen Standardwert.  
  
`[ @publication = ] 'publication'` Ist der Name der Veröffentlichung, die ein Skript erstellt werden. *Veröffentlichung* ist **Sysname**, hat keinen Standardwert.  
  
`[ @dest_table = ] _'dest_table'` Ist der Name der Zieltabelle. *Dest_table* ist **Sysname**, hat keinen Standardwert.  
  
 [ **@owner =** ] **"** _Besitzer_ **"**  
 Entspricht dem Eigentümer des Abonnements. *Besitzer* ist **Sysname**, hat keinen Standardwert.  
  
`[ @cft_table = ] 'cft_table'` Der Name des der Konflikttabelle mit verzögertem Update für diesen Artikel. *Cft_table*ist **Sysname**, hat keinen Standardwert.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 **0** (Erfolg) oder **1** (Fehler)  
  
## <a name="remarks"></a>Hinweise  
 **Sp_addqueued_artinfo** wird vom Verteilungs-Agent als Teil der abonnementinitialisierung verwendet. Diese gespeicherte Prozedur wird normalerweise nicht von Benutzern ausgeführt, kann jedoch hilfreich sein, wenn der Benutzer manuell ein Abonnement einrichten muss.  
  
 [Sp_script_synctran_commands](../../relational-databases/system-stored-procedures/sp-script-synctran-commands-transact-sql.md) anstelle von **Sp_addqueued_artinfo**.  
  
## <a name="permissions"></a>Berechtigungen  
 Nur Mitglieder der der **Sysadmin** -Serverrolle sein oder **Db_owner** feste Datenbankrolle können ausführen **Sp_addqueued_artinfo**.  
  
## <a name="see-also"></a>Siehe auch  
 [Updatable Subscriptions for Transactional Replication](../../relational-databases/replication/transactional/updatable-subscriptions-for-transactional-replication.md)   
 [sp_script_synctran_commands &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-script-synctran-commands-transact-sql.md)   
 [MSsubscription_articles &#40;Transact-SQL&#41;](../../relational-databases/system-tables/mssubscription-articles-transact-sql.md)   
 [Gespeicherte Systemprozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
