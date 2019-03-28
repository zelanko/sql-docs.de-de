---
title: Sp_dropmergepullsubscription (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_dropmergepullsubscription
- sp_dropmergepullsubscription_TSQL
helpviewer_keywords:
- sp_dropmergepullsubscription
ms.assetid: 9301dd80-72f7-4adb-9b13-87e7f9114248
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: f15e5104c03e271b72f6b61dc40077aabdea4e76
ms.sourcegitcommit: c44014af4d3f821e5d7923c69e8b9fb27aeb1afd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/27/2019
ms.locfileid: "58526502"
---
# <a name="spdropmergepullsubscription-transact-sql"></a>sp_dropmergepullsubscription (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Löscht ein Mergepullabonnement. Diese gespeicherte Prozedur wird auf dem Abonnenten für die Abonnementdatenbank ausgeführt.  
  
 ![Themenlinksymbol](../../database-engine/configure-windows/media/topic-link.gif "Topic link icon") [Transact-SQL Syntax Conventions (Transact-SQL-Syntaxkonventionen)](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_dropmergepullsubscription [ @publication= ] 'publication'   
        , [ @publisher= ] 'publisher'   
        , [ @publisher_db= ] 'publisher_db'   
    [ , [ @reserved= ] 'reserved' ]  
```  
  
## <a name="arguments"></a>Argumente  
`[ @publication = ] 'publication'` Ist der Name der Veröffentlichung. *Veröffentlichung* ist **Sysname**, hat den Standardwert NULL. Dieser Parameter ist erforderlich. Geben Sie den Wert **alle** um Abonnements für alle Veröffentlichungen zu entfernen.  
  
`[ @publisher = ] 'publisher'` Ist der Name des Verlegers. *Publisher*ist **Sysname**, hat den Standardwert NULL. Dieser Parameter ist erforderlich.  
  
`[ @publisher_db = ] 'publisher_db'` Ist der Name der Verlegerdatenbank. *Publisher_db*ist **Sysname**, hat den Standardwert NULL. Dieser Parameter ist erforderlich.  
  
`[ @reserved = ] 'reserved'` ist für die zukünftige Verwendung reserviert. *reservierte* ist **Bit**, hat den Standardwert **0**.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 **0** (Erfolg) oder **1** (Fehler)  
  
## <a name="remarks"></a>Hinweise  
 **Sp_dropmergepullsubscription** wird bei der Mergereplikation verwendet.  
  
 **Sp_dropmergepullsubscription** fällt der Merge-Agent für dieses Mergepullabonnement, obwohl der Merge-Agent nicht in erstellt wird **Sp_addmergepullsubscription**.  
  
## <a name="example"></a>Beispiel  
 [!code-sql[HowTo#sp_dropmergepullsubscription](../../relational-databases/replication/codesnippet/tsql/sp-dropmergepullsubscrip_1.sql)]  
  
## <a name="permissions"></a>Berechtigungen  
 Nur Mitglieder der **Sysadmin** feste Serverrolle oder der Benutzer, der das Mergepullabonnement erstellt kann ausführen **Sp_dropmergepullsubscription**. Die **Db_owner** festen Datenbankrolle kann nur zum Ausführen **Sp_dropmergepullsubscription** , wenn der Benutzer, der das Mergepullabonnement erstellt hat, die dieser Rolle gehört.  
  
## <a name="see-also"></a>Siehe auch  
 [Löschen eines Pullabonnements](../../relational-databases/replication/delete-a-pull-subscription.md)   
 [sp_addmergepullsubscription &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addmergepullsubscription-transact-sql.md)   
 [sp_changemergepullsubscription &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-changemergepullsubscription-transact-sql.md)   
 [sp_dropmergesubscription &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-dropmergesubscription-transact-sql.md)   
 [sp_helpmergepullsubscription &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helpmergepullsubscription-transact-sql.md)  
  
  
