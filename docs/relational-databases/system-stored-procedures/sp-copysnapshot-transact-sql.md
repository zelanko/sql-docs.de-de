---
title: Sp_copysnapshot (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_copysnapshot
- sp_copysnapshot_TSQL
helpviewer_keywords:
- sp_copysnapshot
ms.assetid: a012a32f-6f26-45bf-8046-b51cd7fec455
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 429a0c439f5257989e6fb7e85d34a8ea576ad41a
ms.sourcegitcommit: c44014af4d3f821e5d7923c69e8b9fb27aeb1afd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/27/2019
ms.locfileid: "58526992"
---
# <a name="spcopysnapshot-transact-sql"></a>sp_copysnapshot (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Kopiert den momentaufnahmeordner der angegebenen Veröffentlichung in den Ordner aufgeführt, die der **@destination_folder**. Diese gespeicherte Prozedur wird auf dem Verleger für die Veröffentlichungsdatenbank ausgeführt. Diese gespeicherte Prozedur ist zum Kopieren einer Momentaufnahme auf ein Wechselmedium hilfreich, wie z. B. auf eine CD-ROM.  
  
 ![Themenlinksymbol](../../database-engine/configure-windows/media/topic-link.gif "Topic link icon") [Transact-SQL Syntax Conventions (Transact-SQL-Syntaxkonventionen)](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_copysnapshot [ @publication = ] 'publication', [ @destination_folder = ] 'destination_folder' ]  
    [ , [ @subscriber = ] 'subscriber' ]  
    [ , [ @subscriber_db = ] 'subscriber_db' ]  
```  
  
## <a name="arguments"></a>Argumente  
`[ @publication = ] 'publication'` Ist der Name der Veröffentlichung, deren momentaufnahmeinhalt kopiert werden soll. *Veröffentlichung* ist **Sysname**, hat keinen Standardwert.  
  
`[ @destination_folder = ] 'destination_folder'` Ist der Name, der den Ordner, in dem der Inhalt der veröffentlichungsmomentaufnahme kopiert werden soll. *Destination_folder*ist **nvarchar(255)**, hat keinen Standardwert. Die *Destination_folder* kann ein anderen Speicherort wie z. B. auf einem anderen Server, auf einem Netzlaufwerk oder auf Wechselmedien (z. B. CD-ROMs oder Wechseldatenträger) sein.  
  
`[ @subscriber = ] 'subscriber'` Ist der Name des Abonnenten. *Abonnenten* ist vom Datentyp Sysname und hat den Standardwert NULL.  
  
`[ @subscriber_db = ] 'subscriber_db'` Ist der Name der Abonnementdatenbank. *Subscriber_db* ist vom Datentyp Sysname und hat den Standardwert NULL.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 **0** (Erfolg) oder **1** (Fehler)  
  
## <a name="remarks"></a>Hinweise  
 **Sp_copysnapshot** wird in allen Replikationstypen verwendet. Abonnenten, auf denen [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Version 7.0 und früher kann nicht am alternativen momentaufnahmespeicherort verwenden.  
  
## <a name="permissions"></a>Berechtigungen  
 Nur Mitglieder der der **Sysadmin** -Serverrolle sein oder **Db_owner** feste Datenbankrolle können ausführen **Sp_copysnapshot**.  
  
## <a name="see-also"></a>Siehe auch  
 [Alternative Speicherorte für Momentaufnahmeordner](../../relational-databases/replication/snapshot-options.md)   
 [Gespeicherte Systemprozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
