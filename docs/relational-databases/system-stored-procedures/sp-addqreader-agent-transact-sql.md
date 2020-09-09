---
description: sp_addqreader_agent (Transact-SQL)
title: sp_addqreader_agent (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_addqreader_agent_TSQL
- sp_addqreader_agent
helpviewer_keywords:
- sp_addqreader_agent
ms.assetid: dc9f591a-e67e-4ba8-bf47-defd5eda0822
author: markingmyname
ms.author: maghan
ms.openlocfilehash: dae183ab0f04ac343e7836b852a881341f188325
ms.sourcegitcommit: dd36d1cbe32cd5a65c6638e8f252b0bd8145e165
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/08/2020
ms.locfileid: "89549963"
---
# <a name="sp_addqreader_agent-transact-sql"></a>sp_addqreader_agent (Transact-SQL)
[!INCLUDE [SQL Server SQL MI](../../includes/applies-to-version/sql-asdbmi.md)]

  Fügt einen Warteschlangenlese-Agent für einen bestimmten Verteiler hinzu. Diese gespeicherte Prozedur wird auf dem Verteiler für die Verteilungsdatenbank oder auf dem Verleger für die Veröffentlichungsdatenbank ausgeführt.  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_addqreader_agent [ @job_login = ] 'job_login'  
        , [ @job_password = ] 'job_password'  
    [ , [ @job_name = ] 'job_name'  
    [ , [ @frompublisher = ] frompublisher   
```  
  
## <a name="arguments"></a>Argumente  
`[ @job_login = ] 'job_login'` Der Anmelde Name für das [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows-Konto, unter dem der Agent ausgeführt wird. *job_login* ist vom Datentyp **nvarchar (257)** und hat keinen Standardwert. Das Windows-Konto wird stets für Agent-Verbindungen mit dem Verteiler verwendet.  
  
`[ @job_password = ] 'job_password'` Das Kennwort für das Windows-Konto, unter dem der Agent ausgeführt wird. *job_password* ist vom **Datentyp vom Datentyp sysname**und hat keinen Standardwert.  
  
> [!IMPORTANT]  
>  Speichern Sie keine Authentifizierungsinformationen in Skriptdateien. Für die optimale Sicherheit sollten Anmeldenamen und Kennwörter zur Laufzeit bereitgestellt werden.  
  
`[ @job_name = ] 'job_name'` Der Name eines vorhandenen Agentauftrags. *job_name* ist vom **Datentyp vom Datentyp sysname**und hat den Standardwert NULL. Dieser Parameter wird nur dann angegeben, wenn der Agent mit einem vorhandenen Auftrag anstatt mit einem neu erstellten Auftrag (Standard) erstellt wird.  
  
`[ @frompublisher = ] frompublisher` Gibt an, ob die Prozedur auf dem Verleger ausgeführt wird. *frompublisher* ist vom Typ Bit und hat den Standardwert **0**. Der Wert **1** bedeutet, dass die Prozedur auf dem Verleger für die Veröffentlichungs Datenbank ausgeführt wird.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 „0“ (erfolgreich) oder „1“ (fehlerhaft)  
  
## <a name="remarks"></a>Bemerkungen  
 **sp_addqreader_agent** wird bei der Transaktions Replikation verwendet.  
  
 **sp_addqreader_agent** müssen auf einem Verteiler mindestens einmal ausgeführt werden, der nach [sp_adddistributiondb](../../relational-databases/system-stored-procedures/sp-adddistributiondb-transact-sql.md) , aber vor [sp_addpublication](../../relational-databases/system-stored-procedures/sp-addpublication-transact-sql.md)das verzögerte Update über eine Warteschlange unterstützt.  
  
 Der Warteschlangenlese-Agent Auftrag wird entfernt, wenn Sie [sp_dropdistributiondb](../../relational-databases/system-stored-procedures/sp-dropdistributiondb-transact-sql.md)ausführen.  
  
## <a name="permissions"></a>Berechtigungen  
 Nur Mitglieder der festen Server Rolle **sysadmin** können **sp_addqreader_agent**ausführen.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Aktivieren des Aktualisierens von Abonnements für Transaktions Veröffentlichungen](../../relational-databases/replication/publish/enable-updating-subscriptions-for-transactional-publications.md)   
 [Aktualisieren von Replikationsskripts &#40;Replikationsprogrammierung mit Transact-SQL&#41;](../../relational-databases/replication/administration/upgrade-replication-scripts-replication-transact-sql-programming.md)   
 [Updatable Subscriptions for Transactional Replication](../../relational-databases/replication/transactional/updatable-subscriptions-for-transactional-replication.md)   
 [sp_changeqreader_agent &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-changeqreader-agent-transact-sql.md)   
 [sp_helpqreader_agent &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-helpqreader-agent-transact-sql.md)  
  
  
