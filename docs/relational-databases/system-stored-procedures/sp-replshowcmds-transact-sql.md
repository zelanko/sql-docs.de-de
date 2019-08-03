---
title: sp_replshowcmds (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_replshowcmds
- sp_replshowcmds_TSQL
helpviewer_keywords:
- sp_replshowcmds
ms.assetid: 199f5a74-e08e-4d02-a33c-b8ab0db20f44
author: stevestein
ms.author: sstein
ms.openlocfilehash: 96a32ea04fc53f1a0bf3a842a5e68cde5586ac29
ms.sourcegitcommit: 728a4fa5a3022c237b68b31724fce441c4e4d0ab
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/03/2019
ms.locfileid: "68770880"
---
# <a name="spreplshowcmds-transact-sql"></a>sp_replshowcmds (Transact-SQL)
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]

  Gibt die Befehle für Transaktionen, die für die Replikation in lesbarem Format markiert sind, zurück. **sp_replshowcmds** kann nur ausgeführt werden, wenn Clientverbindungen (einschließlich der aktuellen Verbindung) keine replizierten Transaktionen aus dem Protokoll lesen. Diese gespeicherte Prozedur wird auf dem Verleger für die Veröffentlichungs Datenbank ausgeführt.  
  
 ![Themenlinksymbol](../../database-engine/configure-windows/media/topic-link.gif "Topic link icon") [Transact-SQL Syntax Conventions (Transact-SQL-Syntaxkonventionen)](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_replshowcmds [ @maxtrans = ] maxtrans  
```  
  
## <a name="arguments"></a>Argumente  
`[ @maxtrans = ] maxtrans`Die Anzahl der Transaktionen, für die Informationen zurückgegeben werden sollen. *maxtrans* ist vom Datentyp **int**und hat den Standardwert **1**, womit die maximale Anzahl von Transaktionen angegeben wird , für die die Replikation aussteht  
  
## <a name="result-sets"></a>Resultsets  
 **sp_replshowcmds** ist eine Diagnose Prozedur, die Informationen über die Veröffentlichungs Datenbank zurückgibt, von der Sie ausgeführt wird.  
  
|Spaltenname|Datentyp|Beschreibung|  
|-----------------|---------------|-----------------|  
|**xact_seqno**|**binary(10)**|Sequenznummer des Befehls.|  
|**originator_id**|**int**|ID des Befehls Erstellers, immer **0**.|  
|**publisher_database_id**|**int**|ID der Verleger Datenbank, immer **0**.|  
|**article_id**|**int**|ID des Artikels.|  
|**type**|**int**|Der Typ des Befehls.|  
|**Befehl**|**nvarchar(1024)**|[!INCLUDE[tsql](../../includes/tsql-md.md)]s.|  
  
## <a name="remarks"></a>Hinweise  
 **sp_replshowcmds** wird bei der Transaktions Replikation verwendet.  
  
 Mit **sp_replshowcmds**können Sie Transaktionen anzeigen, die derzeit nicht verteilt sind (die im Transaktionsprotokoll verbleibenden Transaktionen, die nicht an den Verteiler gesendet wurden).  
  
 Clients, auf denen **sp_replshowcmds** und **sp_replcmds** innerhalb derselben Datenbank ausgeführt werden, erhalten den Fehler 18752.  
  
 Um diesen Fehler zu vermeiden, muss der erste Client die Verbindung trennen oder die Rolle des Clients, da der Protokoll Leser durch Ausführen von **sp_replflush**freigegeben werden muss. Nachdem alle Clients vom Protokoll Leser getrennt wurden, kann **sp_replshowcmds** erfolgreich ausgeführt werden.  
  
> [!NOTE]  
>  **sp_replshowcmds** sollte nur ausgeführt werden, um Probleme bei der Replikation zu beheben.  
  
## <a name="permissions"></a>Berechtigungen  
 Nur Mitglieder der festen Server Rolle **sysadmin** oder der festen Daten Bank Rolle **db_owner** können **sp_replshowcmds**ausführen.  
  
## <a name="see-also"></a>Siehe auch  
 [Fehlermeldungen](../../relational-databases/native-client-odbc-error-messages/error-messages.md)   
 [sp_replcmds &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-replcmds-transact-sql.md)   
 [sp_repldone &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-repldone-transact-sql.md)   
 [sp_replflush &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-replflush-transact-sql.md)   
 [sp_repltrans &#40;(Transact-SQL)&#41;](../../relational-databases/system-stored-procedures/sp-repltrans-transact-sql.md)   
 [Gespeicherte Systemprozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
