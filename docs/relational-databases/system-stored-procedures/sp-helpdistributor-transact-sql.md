---
title: sp_helpdistributor (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_helpdistributor_TSQL
- sp_helpdistributor
helpviewer_keywords:
- sp_helpdistributor
ms.assetid: 37b0983e-3b69-4f0f-977e-20efce0a0b97
author: stevestein
ms.author: sstein
ms.openlocfilehash: 8333e805c50f4b8084f8463877c361917097b547
ms.sourcegitcommit: a97d551b252b76a33606348082068ebd6f2c4c8c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/06/2019
ms.locfileid: "70745384"
---
# <a name="sp_helpdistributor-transact-sql"></a>sp_helpdistributor (Transact-SQL)
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]

  Listet Informationen zum Verteiler, zur Verteilungs Datenbank, zum Arbeitsverzeichnis und [!INCLUDE[msCoName](../../includes/msconame-md.md)] zum Benutzerkonto des- [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agents. Diese gespeicherte Prozedur wird beim Verleger mit der Veröffentlichungsdatenbank oder einer anderen Datenbank ausgeführt.  
  
 ![Themenlinksymbol](../../database-engine/configure-windows/media/topic-link.gif "Topic link icon") [Transact-SQL Syntax Conventions (Transact-SQL-Syntaxkonventionen)](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_helpdistributor [ [ @distributor= ] 'distributor' OUTPUT ]  
    [ , [ @distribdb= ] 'distribdb' OUTPUT ]  
    [ , [ @directory= ] 'directory' OUTPUT ]  
    [ , [ @account= ] 'account' OUTPUT ]  
    [ , [ @min_distretention= ] min_distretention OUTPUT ]  
    [ , [ @max_distretention= ] max_distretention OUTPUT ]  
    [ , [ @history_retention= ] history_retention OUTPUT ]  
    [ , [ @history_cleanupagent= ] 'history_cleanupagent' OUTPUT ]  
    [ , [ @distrib_cleanupagent = ] 'distrib_cleanupagent' OUTPUT ]  
    [ , [ @publisher = ] 'publisher' ]   
    [ , [ @local = ] 'local' ]  
    [ , [ @rpcsrvname= ] 'rpcsrvname' OUTPUT ]  
    [ , [ @publisher_type = ] 'publisher_type' OUTPUT ]  
```  
  
## <a name="arguments"></a>Argumente  
`[ @distributor = ] 'distributor' OUTPUT`Der Name des Verteilers. Distributor ist vom **Datentyp vom Datentyp sysname**. der **%** Standardwert ist. Dies ist der einzige Wert, der ein Resultset zurückgibt.  
  
`[ @distribdb = ] 'distribdb' OUTPUT`Der Name der Verteilungs Datenbank. *Verteil BDB* ist vom **Datentyp vom Datentyp sysname**. der **%** Standardwert ist. Dies ist der einzige Wert, der ein Resultset zurückgibt.  
  
`[ @directory = ] 'directory' OUTPUT`Das Arbeitsverzeichnis. Das *Verzeichnis* ist vom Datentyp **nvarchar (255)** . **%** der Standardwert ist. Dies ist der einzige Wert, der ein Resultset zurückgibt.  
  
`[ @account = ] 'account' OUTPUT`Ist das [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows-Benutzerkonto. Das *Konto*ist vom **%** Datentyp **nvarchar (255)** . der Standardwert ist. Dies ist der einzige Wert, der ein Resultset zurückgibt.  
  
`[ @min_distretention = ] _min_distretentionOUTPUT`Die minimale Beibehaltungs Dauer für die Verteilung (in Stunden). *min_distretention* ist vom Datentyp **int**und hat den Standardwert **-1**.  
  
`[ @max_distretention = ] _max_distretentionOUTPUT`Die maximale Beibehaltungs Dauer für die Verteilung (in Stunden). *max_distretention* ist vom Datentyp **int**und hat den Standardwert **-1**.  
  
`[ @history_retention = ] _history_retentionOUTPUT`Die Beibehaltungs Dauer für den Verlauf (in Stunden). *history_retention* ist vom Datentyp **int**und hat den Standardwert **-1**.  
  
`[ @history_cleanupagent = ] 'history_cleanupagent' OUTPUT`Der Name des Verlaufscleanup-Agents. *history_cleanupagent* ist vom Datentyp **nvarchar (100)** . der **%** Standardwert ist. Dies ist der einzige Wert, der ein Resultset zurückgibt.  
  
`[ @distrib_cleanupagent = ] 'distrib_cleanupagent' OUTPUT`Der Name des Verteilungscleanup-Agents. *distrib_cleanupagent* ist vom Datentyp **nvarchar (100)** . der **%** Standardwert ist. Dies ist der einzige Wert, der ein Resultset zurückgibt.  
  
`[ @publisher = ] 'publisher'`Der Name des Verlegers. *Publisher* ist vom **Datentyp vom Datentyp sysname**und hat den Standardwert NULL.  
  
`[ @local = ] 'local'`Gibt an [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , ob lokale Server Werte erhalten soll. *local* ist vom Datentyp **nvarchar (5)** und hat den Standardwert NULL.  
  
`[ @rpcsrvname = ] 'rpcsrvname' OUTPUT`Der Name des Servers, der Remote Prozedur Aufrufe ausgibt. *rpcsrvname* ist vom **%** Datentyp **vom Datentyp sysname**. der Standardwert ist. Dies ist der einzige Wert, der ein Resultset zurückgibt.  
  
`[ @publisher_type = ] 'publisher_type' OUTPUT`Der Verlegertyp des Verlegers. *publisher_type* ist vom **Datentyp vom Datentyp sysname**. der **%** Standardwert ist. Dies ist der einzige Wert, der ein Resultset zurückgibt.  
  
## <a name="result-sets"></a>Resultsets  
  
|Spaltenname|Datentyp|Beschreibung|  
|-----------------|---------------|-----------------|  
|**distributor**|**sysname**|Name des Verteilers.|  
|**Verteilungs Datenbank**|**sysname**|Der Name der Verteilungsdatenbank.|  
|**befinden**|**nvarchar(255)**|Name des Arbeitsverzeichnisses.|  
|**account**|**nvarchar(255)**|Name des Windows-Benutzerkontos.|  
|**Min. Verteil b Aufbewahrung**|**int**|Minimale Beibehaltungsdauer für die Verteilung.|  
|**maximale Verteilung von Verteil b**|**int**|Maximale Beibehaltungsdauer für die Verteilung.|  
|**Verlaufs Beibehaltung**|**int**|Aufbewahrungdauer für Verlauf.|  
|**Agent für Verlaufs Bereinigungs**|**nvarchar (100)**|Der Name des Verlaufscleanup-Agents.|  
|**verteilungscleanupagent**|**nvarchar (100)**|Der Name des Verteilungscleanup-Agents.|  
|**RPC-Servername**|**sysname**|Name des lokalen Verteilers oder Remoteverteilers.|  
|**RPC-Anmelde Name**|**sysname**|Anmeldename, der für Remoteprozeduraufrufe an den Remoteverteiler verwendet wird.|  
|**Verlegertyp**|**sysname**|Typ des Verlegers; kann einer der folgenden sein:<br /><br /> **MSSQLSERVER**<br /><br /> **ORAKEL**<br /><br /> **ORACLE-GATEWAY**|  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 **0** (Erfolg) oder **1** (Fehler)  
  
## <a name="remarks"></a>Hinweise  
 **sp_helpdistributor** wird für alle Replikations Typen verwendet.  
  
 Wenn beim Ausführen von **sp_helpdistributor**ein oder mehrere Ausgabeparameter angegeben werden, werden allen Ausgabeparametern, die auf NULL festgelegt sind, beim Beenden Werte zugewiesen, und es wird kein Resultset zurückgegeben. Wenn keine Ausgabeparameter angegeben werden, wird ein Resultset zurückgegeben.  
  
## <a name="permissions"></a>Berechtigungen  
 Die folgenden Resultsetspalten oder Ausgabeparameter werden an Mitglieder der festen Server Rolle **sysadmin** auf dem Verleger und der festen Daten Bank Rolle **db_owner** in der Veröffentlichungs Datenbank zurückgegeben:  
  
|Resultsetspalte|Output-Parameter|  
|-----------------------|----------------------|  
|account|**\@Ziehen**|  
|min distrib retention|**\@min_distretention**|  
|max distrib retention|**\@max_distretention**|  
|history retention|**\@history_retention**|  
|history cleanup agent|**\@history_cleanupagent**|  
|distribution cleanup agent|**\@distrib_cleanupagent**|  
|rpc login name|none|  
  
 Die folgende Resultsetspalte wird an Benutzer in der Veröffentlichungszugriffsliste für eine Veröffentlichung beim Verteiler zurückgegeben:  
  
-   directory  
  
 Die folgenden Resultsetspalten werden an alle Benutzer zurückgegeben.  
  
|Resultsetspalte|Output-Parameter|  
|-----------------------|----------------------|  
|distributor|**\@Verleih**|  
|distribution database|**\@Verteil DB**|  
|rpc server name|**\@rpcsrvname**|  
|publisher type|**\@publisher_type**|  
  
## <a name="see-also"></a>Siehe auch  
 [Anzeigen und Ändern der Verteiler- und Verlegereigenschaften](../../relational-databases/replication/view-and-modify-distributor-and-publisher-properties.md)   
 [sp_adddistpublisher &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-adddistpublisher-transact-sql.md)   
 [sp_dropdistpublisher &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-dropdistpublisher-transact-sql.md)  
  
  
