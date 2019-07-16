---
title: Sp_replmonitorsubscriptionpendingcmds (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_replmonitorsubscriptionpendingcmds_TSQL
- sp_replmonitorsubscriptionpendingcmds
helpviewer_keywords:
- sp_replmonitorsubscriptionpendingcmds
ms.assetid: df5b955a-feb0-4863-9b3b-7f71e9653b3d
author: stevestein
ms.author: sstein
ms.openlocfilehash: 7e6def32ab27560f68902470d0b7add715de665d
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68090010"
---
# <a name="spreplmonitorsubscriptionpendingcmds-transact-sql"></a>sp_replmonitorsubscriptionpendingcmds (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Gibt Informationen zur Anzahl der ausstehenden Befehle für ein Abonnement einer Transaktionsveröffentlichung zurück sowie eine grobe Schätzung, wie viel Zeit ihre Verarbeitung in Anspruch nimmt. Die gespeicherte Prozedur gibt eine Zeile für jedes zurückgegebene Abonnement zurück. Diese gespeicherte Prozedur, die zur Überwachung der Replikation verwendet wird, wird auf dem Verteiler für die Verteilungsdatenbank ausgeführt.  
  
 ![Themenlinksymbol](../../database-engine/configure-windows/media/topic-link.gif "Topic link icon") [Transact-SQL Syntax Conventions (Transact-SQL-Syntaxkonventionen)](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_replmonitorsubscriptionpendingcmds [ @publisher = ] 'publisher'  
        , [ @publisher_db = ] 'publisher_db'  
        , [ @publication = ] 'publication'  
        , [ @subscriber = ] 'subscriber'  
        , [ @subscriber_db = ] 'subscriber_db'   
        , [ @subscription_type = ] subscription_type  
```  
  
## <a name="arguments"></a>Argumente  
`[ @publisher = ] 'publisher'` Ist der Name des Verlegers. *Publisher* ist **Sysname**, hat keinen Standardwert.  
  
`[ @publisher_db = ] 'publisher_db'` Ist der Name der veröffentlichten Datenbank. *Publisher_db* ist **Sysname**, hat keinen Standardwert.  
  
`[ @publication = ] 'publication'` Ist der Name der Veröffentlichung. *Veröffentlichung* ist **Sysname**, hat keinen Standardwert.  
  
`[ @subscriber = ] 'subscriber'` Ist der Name des Abonnenten. *Abonnenten* ist **Sysname**, hat keinen Standardwert.  
  
`[ @subscriber_db = ] 'subscriber_db'` Ist der Name der Abonnementdatenbank. *Subscriber_db* ist **Sysname**, hat keinen Standardwert.  
  
`[ @subscription_type = ] subscription_type` Wenn der Typ des Abonnements. *Publication_type* ist **Int**, hat keinen Standardwert und kann einen der folgenden Werte sein.  
  
|Wert|Description|  
|-----------|-----------------|  
|**0**|Pushabonnement|  
|**1**|Pullabonnement|  
  
## <a name="result-sets"></a>Resultsets  
  
|Spaltenname|Datentyp|Beschreibung|  
|-----------------|---------------|-----------------|  
|**pendingcmdcount**|**int**|Die Anzahl der für das Abonnement ausstehenden Befehle.|  
|**estimatedprocesstime**|**int**|Eine Schätzung der Anzahl von Sekunden, die erforderlich sind, um alle ausstehenden Befehle an den Abonnenten zu übermitteln.|  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 **0** (Erfolg) oder **1** (Fehler)  
  
## <a name="remarks"></a>Hinweise  
 **Sp_replmonitorsubscriptionpendingcmds** wird bei der Transaktionsreplikation verwendet.  
  
## <a name="permissions"></a>Berechtigungen  
 Nur Mitglieder der der **Sysadmin** auf dem Verteiler oder Mitglieder der festen Serverrolle die **Db_owner** -Datenbankrolle in der Verteilungsdatenbank kann ausführen **Sp_ Replmonitorsubscriptionpendingcmds**. Auflisten von Mitglieder der veröffentlichungszugriffsliste für eine Veröffentlichung mit der Verteilungsdatenbank kann **Sp_replmonitorsubscriptionpendingcmds** für ausstehende Befehle für diese Veröffentlichung zurückgegeben.  
  
## <a name="see-also"></a>Siehe auch  
 [Programmgesteuertes Überwachen der Replikation](../../relational-databases/replication/monitor/programmatically-monitor-replication.md)  
  
  
