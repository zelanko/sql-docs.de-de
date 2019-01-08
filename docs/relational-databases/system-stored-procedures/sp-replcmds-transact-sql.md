---
title: Sp_replcmds (Transact-SQL) | Microsoft-Dokumentation
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
manager: craigg
ms.openlocfilehash: c868fe69df1f3fd34fe0c1f550507e7db7b6c944
ms.sourcegitcommit: ceb7e1b9e29e02bb0c6ca400a36e0fa9cf010fca
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/03/2018
ms.locfileid: "52823424"
---
# <a name="spreplcmds-transact-sql"></a>sp_replcmds (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Mit dieser Prozedur werden die Transaktionsbefehle zurückgegeben, die für die Replikation gekennzeichnet sind. Diese gespeicherte Prozedur wird auf dem Verleger für die Veröffentlichungsdatenbank ausgeführt.  
  
> [!IMPORTANT]  
>  Die **Sp_replcmds** Prozedur sollte nur zur Fehlerbehebung bei der Replikation ausgeführt werden.  
  
 ![Themenlinksymbol](../../database-engine/configure-windows/media/topic-link.gif "Topic link icon") [Transact-SQL Syntax Conventions (Transact-SQL-Syntaxkonventionen)](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_replcmds [ @maxtrans = ] maxtrans  
```  
  
## <a name="arguments"></a>Argumente  
 [  **@maxtrans=**] *Maxtrans*  
 Die Anzahl der Transaktionen, zu denen Informationen zurückgegeben werden sollen. *Maxtrans* ist **Int**, hat den Standardwert **1**, die angibt, dass der nächsten Transaktions, die Verteilung wartet.  
  
## <a name="result-sets"></a>Resultsets  
  
|Spaltenname|Datentyp|Description|  
|-----------------|---------------|-----------------|  
|**Artikel-id**|**int**|Die ID des Artikels.|  
|**verbleiben**|**bit**|Gibt an, ob es sich um einen Teilbefehl handelt.|  
|**Befehl**|**varbinary(1024)**|Der Befehlswert.|  
|**xactid**|**binary(10)**|Transaktions-ID|  
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
  
## <a name="remarks"></a>Hinweise  
 **Sp_replcmds** wird vom Protokollleseprozess bei der Transaktionsreplikation verwendet.  
  
 Replikation behandelt den ersten Client, der ausgeführt wird **Sp_replcmds** innerhalb einer bestimmten Datenbank als Protokollleser.  
  
 Diese Prozedur kann Befehle für mit dem Besitzer qualifizierte Tabellen erstellen oder den Tabellennamen nicht kennzeichnen (Standard). Das Hinzufügen von qualifizierten Tabellennamen ermöglicht die Datenreplikation von Tabellen mit einem bestimmten Besitzer innerhalb einer Datenbank zu Tabellen mit demselben Besitzer in einer anderen Datenbank.  
  
> [!NOTE]  
>  Da der Tabellenname in der Quelldatenbank durch den Besitzernamen qualifiziert wird, muss es sich bei dem Tabellenbesitzer in der Zieldatenbank um den gleichen Besitzernamen handeln.  
  
 Clients, die versuchen, führen Sie **Sp_replcmds** innerhalb derselben Datenbank erhalten den Fehler 18752, bis die Verbindung getrennt wurde. Nachdem die Verbindung getrennt wurde, kann einen anderen Client ausführen **Sp_replcmds**, und wird von der neuen Protokollleser.  
  
 Fehlermeldungsnummer 18759 wird sowohl hinzugefügt der [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Fehlerprotokoll und die [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows-Anwendung zu protokollieren, wenn **Sp_replcmds** kann keinen Textbefehl repliziert werden, da der Textzeiger nicht war in der gleichen Transaktion abgerufen.  
  
## <a name="permissions"></a>Berechtigungen  
 Nur Mitglieder der der **Sysadmin** -Serverrolle sein oder die **Db_owner** feste Datenbankrolle können ausführen **Sp_replcmds**.  
  
## <a name="see-also"></a>Siehe auch  
 [Fehlermeldungen](../../relational-databases/native-client-odbc-error-messages/error-messages.md)   
 [Sp_repldone &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-repldone-transact-sql.md)   
 [Sp_replflush &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-replflush-transact-sql.md)   
 [Sp_repltrans &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-repltrans-transact-sql.md)   
 [Gespeicherte Systemprozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
