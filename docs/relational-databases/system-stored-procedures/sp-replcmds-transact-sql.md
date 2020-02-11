---
title: sp_replcmds (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_replcmds_TSQL
- sp_replcmds
helpviewer_keywords:
- sp_replcmds
ms.assetid: 7e932f80-cc6e-4109-8db4-2b7c8828df73
author: stevestein
ms.author: sstein
ms.openlocfilehash: 3d60de0f459ec1224f6023e8ee848227fdc17ece
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "68771011"
---
# <a name="sp_replcmds-transact-sql"></a>sp_replcmds (Transact-SQL)
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]

  Mit dieser Prozedur werden die Transaktionsbefehle zurückgegeben, die für die Replikation gekennzeichnet sind. Diese gespeicherte Prozedur wird auf dem Verleger für die Veröffentlichungs Datenbank ausgeführt.  
  
> [!IMPORTANT]  
>  Das **sp_replcmds** Verfahren sollte nur ausgeführt werden, um Probleme bei der Replikation zu beheben.  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_replcmds [ @maxtrans = ] maxtrans  
```  
  
## <a name="arguments"></a>Argumente  
`[ @maxtrans = ] maxtrans`Die Anzahl der Transaktionen, für die Informationen zurückgegeben werden sollen. *maxtrans* ist vom Datentyp **int**. der Standardwert ist **1**. dieser gibt die nächste Transaktion an, die auf die Verteilung wartet.  
  
## <a name="result-sets"></a>Resultsets  
  
|Spaltenname|Datentyp|BESCHREIBUNG|  
|-----------------|---------------|-----------------|  
|**Artikel-ID**|**int**|Die ID des Artikels.|  
|**partial_command**|**bit**|Gibt an, ob es sich um einen Teilbefehl handelt.|  
|**s**|**varbinary (1024)**|Der Befehlswert.|  
|**xactid**|**Binär (10)**|Transaktions-ID|  
|**xact_seqno**|**varbinary(16)**|Die Transaktionssequenznummer.|  
|**publication_id**|**int**|Die ID der Veröffentlichung.|  
|**command_id**|**int**|ID des Befehls in [MSrepl_commands](../../relational-databases/system-tables/msrepl-commands-transact-sql.md).|  
|**command_type**|**int**|Der Typ des Befehls.|  
|**originator_srvname**|**sysname**|Server, von dem die Transaktion stammt|  
|**originator_db**|**sysname**|Datenbank, von der die Transaktion stammt|  
|**pkHash**|**int**|Nur interne Verwendung.|  
|**originator_publication_id**|**int**|ID der Veröffentlichung, von der die Transaktion stammt|  
|**originator_db_version**|**int**|Version der Datenbank, von der die Transaktion stammt|  
|**originator_lsn**|**varbinary(16)**|Identifiziert die Protokollfolgenummer (LSN, Log Sequence Number) für den Befehl in der ursprünglichen Veröffentlichung|  
  
## <a name="remarks"></a>Bemerkungen  
 **sp_replcmds** wird vom Protokoll Leseprozess bei der Transaktions Replikation verwendet.  
  
 Bei der Replikation wird der erste Client, der **sp_replcmds** innerhalb einer bestimmten Datenbank ausführt, als Protokoll Leser behandelt.  
  
 Diese Prozedur kann Befehle für mit dem Besitzer qualifizierte Tabellen erstellen oder den Tabellennamen nicht kennzeichnen (Standard). Das Hinzufügen von qualifizierten Tabellennamen ermöglicht die Datenreplikation von Tabellen mit einem bestimmten Besitzer innerhalb einer Datenbank zu Tabellen mit demselben Besitzer in einer anderen Datenbank.  
  
> [!NOTE]  
>  Da der Tabellenname in der Quelldatenbank durch den Besitzernamen qualifiziert wird, muss es sich bei dem Tabellenbesitzer in der Zieldatenbank um den gleichen Besitzernamen handeln.  
  
 Clients, die versuchen, **sp_replcmds** innerhalb derselben Datenbank auszuführen, erhalten den Fehler 18752, bis der erste Client die Verbindung trennt. Nachdem der erste Client die Verbindung getrennt hat, kann ein anderer Client **sp_replcmds**ausführen und zum neuen Protokoll Leser werden.  
  
 Wenn sp_replcmds einen Textbefehl nicht replizieren kann, [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] wird im-Fehler [!INCLUDE[msCoName](../../includes/msconame-md.md)] Protokoll und im Windows **** -Anwendungsprotokoll eine Warnmeldung mit der Nummer 18759 hinzugefügt, da der Text Zeiger nicht in der gleichen Transaktion abgerufen wurde.  
  
## <a name="permissions"></a>Berechtigungen  
 Nur Mitglieder der festen Server Rolle **sysadmin** oder der festen Daten Bank Rolle **db_owner** können **sp_replcmds**ausführen.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Fehlermeldungen](../../relational-databases/native-client-odbc-error-messages/error-messages.md)   
 [sp_repldone &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-repldone-transact-sql.md)   
 [sp_replflush &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-replflush-transact-sql.md)   
 [sp_repltrans &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-repltrans-transact-sql.md)   
 [Gespeicherte Systemprozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
