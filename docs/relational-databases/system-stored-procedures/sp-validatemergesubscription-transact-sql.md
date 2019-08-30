---
title: sp_validatemergesubscription (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_validatemergesubscription
- sp_validatemergesubscription_TSQL
helpviewer_keywords:
- sp_validatemergesubscription
ms.assetid: d73ad03c-e5b3-4606-a0ee-7d75e12762a6
author: stevestein
ms.author: sstein
ms.openlocfilehash: 3341bf25e43f73143fa1dd0e66add9f4b86c22bb
ms.sourcegitcommit: 5e45cc444cfa0345901ca00ab2262c71ba3fd7c6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/29/2019
ms.locfileid: "70155528"
---
# <a name="sp_validatemergesubscription-transact-sql"></a>sp_validatemergesubscription (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Führt eine Überprüfung für das angegebene Abonnement durch. Diese gespeicherte Prozedur wird auf dem Verleger für die Veröffentlichungs Datenbank ausgeführt.  
  
 ![Themenlinksymbol](../../database-engine/configure-windows/media/topic-link.gif "Topic link icon") [Transact-SQL Syntax Conventions (Transact-SQL-Syntaxkonventionen)](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_validatemergesubscription [@publication=] 'publication'  
        , [ @subscriber = ] 'subscriber'  
        , [ @subscriber_db = ] 'subscriber_db'  
        , [ @level = ] level  
```  
  
## <a name="arguments"></a>Argumente  
 **[\@Veröffentlichung =** ] **'***Veröffentlichung***'**  
 Der Name der Veröffentlichung. *Publication* ist vom **Datentyp vom Datentyp sysname**und hat keinen Standardwert.  
  
`[ @subscriber = ] 'subscriber'`Der Name des Abonnenten. *Subscriber* ist vom **Datentyp vom Datentyp sysname**und hat keinen Standardwert.  
  
`[ @subscriber_db = ] 'subscriber_db'`Der Name der Abonnement Datenbank. *subscriber_db* ist vom **Datentyp vom Datentyp sysname**und hat keinen Standardwert.  
  
`[ @level = ] level`Der Typ der Überprüfung, die durchgeführt werden soll. die Ebene ist vom Datentyp **tinyint**und hat keinen Standard *Wert* . Level kann einen der folgenden Werte haben.  
  
|Level-Wert|Beschreibung|  
|-----------------|-----------------|  
|**1**|Nur Überprüfung der Zeilenanzahl.|  
|**2**|Überprüfung der Zeilenanzahl und der Prüfsumme.|  
|**3**|Überprüfung der Zeilenanzahl und der binären Prüfsumme.|  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 **0** (Erfolg) oder **1** (Fehler)  
  
## <a name="remarks"></a>Hinweise  
 **sp_validatemergesubscription** wird bei der Mergereplikation verwendet.  
  
## <a name="permissions"></a>Berechtigungen  
 Nur Mitglieder der festen Server Rolle **sysadmin** oder der festen Daten Bank Rolle **db_owner** können **sp_validatemergesubscription**ausführen.  
  
## <a name="see-also"></a>Siehe auch  
 [Gespeicherte Replikationsprozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/replication-stored-procedures-transact-sql.md)   
 [Replizierte Daten überprüfen](../../relational-databases/replication/validate-data-at-the-subscriber.md)   
 [sp_validatemergepublication &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-validatemergepublication-transact-sql.md)  
  
  
