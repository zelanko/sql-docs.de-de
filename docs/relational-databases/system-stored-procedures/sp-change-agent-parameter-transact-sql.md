---
title: sp_change_agent_parameter (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_change_agent_parameter_TSQL
- sp_change_agent_parameter
helpviewer_keywords:
- sp_change_agent_parameter
ms.assetid: f1fbecc7-e64f-405c-8067-6b38c1f3c0a0
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: f22b2446713274503071e615690aaf7a03fc33d2
ms.sourcegitcommit: 4d3896882c5930248a6e441937c50e8e027d29fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/05/2020
ms.locfileid: "82824832"
---
# <a name="sp_change_agent_parameter-transact-sql"></a>sp_change_agent_parameter (Transact-SQL)
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]

  Ändert einen Parameter eines Replikations-Agentprofils, das in der [MSagent_parameters](../../relational-databases/system-tables/msagent-parameters-transact-sql.md) -Systemtabelle gespeichert ist. Diese gespeicherte Prozedur wird auf dem Verteiler, auf dem der Agent ausgeführt wird, für jede Datenbank ausgeführt.  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_change_agent_parameter [ @profile_id= ] profile_id, [ @parameter_name= ] 'parameter_name', [ @parameter_value= ] 'parameter_value'  
```  
  
## <a name="arguments"></a>Argumente  
`[ @profile_id = ] profile_id,`Die ID des Profils. *profile_id* ist vom Datentyp **int**und hat keinen Standardwert.  
  
`[ @parameter_name = ] 'parameter_name'`Der Name des Parameters. *parameter_name* ist vom **Datentyp vom Datentyp sysname**und hat keinen Standardwert. Bei Systemprofilen hängen die veränderbaren Parameter vom Typ der Momentaufnahme ab. Um herauszufinden, welcher Agenttyp diese *profile_id* darstellt, suchen Sie die Spalte *profile_id* in der Tabelle **MSagent_profiles** , und notieren Sie sich den Wert *agent_type* .  
  
> [!NOTE]  
>  Wenn ein Parameter für eine bestimmte *agent_type*unterstützt, aber nicht im Agentprofil definiert wurde, wird ein Fehler zurückgegeben. Wenn Sie einem Agentprofil einen Parameter hinzufügen möchten, müssen Sie [sp_add_agent_parameter](../../relational-databases/system-stored-procedures/sp-add-agent-parameter-transact-sql.md)ausführen.  
  
 Bei einer Momentaufnahmen-Agent (*agent_type* = **1**), die im Profil definiert ist, können die folgenden Eigenschaften geändert werden:  
  
-   **70er-Abonnenten**  
  
-   **BcpBatchSize**  
  
-   **HistoryVerboseLevel**  
  
-   **LoginTimeout**  
  
-   **MaxBCPThreads**  
  
-   **MaxNetworkOptimization**  
  
-   **Ausgabe**  
  
-   **OutputVerboseLevel**  
  
-   **PacketSize**  
  
-   **QueryTimeout**  
  
-   **StartQueueTimeout**  
  
-   **UsePerArticleContentsView**  
  
 Bei einer Protokolllese-Agent (*agent_type* = **2**), die im Profil definiert ist, können die folgenden Eigenschaften geändert werden:  
  
-   **HistoryVerboseLevel**  
  
-   **LoginTimeout**  
  
-   **MessageInterval**  
  
-   **Ausgabe**  
  
-   **OutputVerboseLevel**  
  
-   **PacketSize**  
  
-   **PollingInterval**  
  
-   **QueryTimeout**  
  
-   **ReadBatchSize**  
  
-   **Read Batch Threshold**  
  
 Bei einer Verteilungs-Agent (*agent_type* = **3**), die im Profil definiert ist, können die folgenden Eigenschaften geändert werden:  
  
-   **BcpBatchSize**  
  
-   **CommitBatchSize**  
  
-   **CommitBatchThreshold**  
  
-   **FileTransferType**  
  
-   **HistoryVerboseLevel**  
  
-   **Keepalivemstinageinterval**  
  
-   **LoginTimeout**  
  
-   **MaxBCPThreads**  
  
-   **MaxDeliveredTransactions**  
  
-   **MessageInterval**  
  
-   **Ausgabe**  
  
-   **OutputVerboseLevel**  
  
-   **PacketSize**  
  
-   **PollingInterval**  
  
-   **QueryTimeout**  
  
-   **QuotedIdentifier**  
  
-   **SkipErrors**  
  
-   **TransactionsPerHistory an**  
  
 Bei einer Merge-Agent (*agent_type* = **4**), die im Profil definiert ist, können die folgenden Eigenschaften geändert werden:  
  
-   **AltSnapshotFolder**  
  
-   **BcpBatchSize**  
  
-   **ChangesPerHistory**  
  
-   **DestThreads**  
  
-   **DownloadGenerationsPerBatch**  
  
-   **Downloadumchangesperbatch**  
  
-   **Downloadschreibchangesperbatch**  
  
-   **DynamicSnapshotLocation**  
  
-   **ExchangeType**  
  
-   **Fastrowcount**  
  
-   **FileTransferType**  
  
-   **GenerationChangeThreshold**  
  
-   **HistoryVerboseLevel**  
  
-   **InputMessageFile**  
  
-   **InteractiveResolution**  
  
-   **InterruptOnMessagePattern**  
  
-   **Keepalivemstinageinterval**  
  
-   **LoginTimeout**  
  
-   **MaxBCPThreads**  
  
-   **MaxDownloadChanges**  
  
-   **MaxUploadChanges**  
  
-   **MetadataRetentionCleanup**  
  
-   **Numdeadlockretries**  
  
-   **Ausgabe**  
  
-   **OutputMessageFile**  
  
-   **OutputVerboseLevel**  
  
-   **PacketSize**  
  
-   **ParallelUploadDownload**  
  
-   **PauseOnMessagePattern**  
  
-   **PauseTime**  
  
-   **PollingInterval**  
  
-   **ProcessMessagesAtPublisher**  
  
-   **ProcessMessagesAtSubscriber**  
  
-   **QueryTimeout**  
  
-   **Queuesizemultiplikator**  
  
-   **SrcThreads**  
  
-   **StartQueueTimeout**  
  
-   **SyncToAlternate**  
  
-   **UploadGenerationsPerBatch**  
  
-   **UploadReadChangesPerBatch**  
  
-   **Uploadschreitechangesperbatch**  
  
-   **UseInprocLoader**  
  
-   **Überprüfen**  
  
-   **ValidateInterval**  
  
 Bei einem Warteschlangenlese-Agent (*agent_type* = **9**), wenn es im Profil definiert ist, können die folgenden Eigenschaften geändert werden:  
  
-   **HistoryVerboseLevel**  
  
-   **LoginTimeout**  
  
-   **Ausgabe**  
  
-   **OutputVerboseLevel**  
  
-   **PollingInterval**  
  
-   **QueryTimeout**  
  
-   **ResolverState**  
  
-   **SQLQueueMode**  
  
 Um zu sehen, welche Parameter für ein bestimmtes Profil definiert wurden, führen Sie **sp_help_agent_profile** aus, und notieren Sie sich die *profile_name* , die dem *profile_id*zugeordnet sind. Führen Sie mit dem entsprechenden *profile_id*als nächstes **sp_help_agent_parameters** mithilfe dieses *profile_id* aus, um die Parameter anzuzeigen, die dem Profil zugeordnet sind. Parameter können einem Profil hinzugefügt werden, indem [sp_add_agent_parameter](../../relational-databases/system-stored-procedures/sp-add-agent-parameter-transact-sql.md)ausgeführt wird.  
  
`[ @parameter_value = ] 'parameter_value'`Der neue Wert des-Parameters. *parameter_value* ist vom Datentyp **nvarchar (255)** und hat keinen Standardwert.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 **0** (Erfolg) oder **1** (Fehler)  
  
## <a name="remarks"></a>Bemerkungen  
 **sp_change_agent_parameter** wird bei allen Replikations Typen verwendet.  
  
## <a name="permissions"></a>Berechtigungen  
 Nur Mitglieder der festen Server Rolle **sysadmin** können **sp_change_agent_parameter**ausführen.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Replikationsagentprofile](../../relational-databases/replication/agents/replication-agent-profiles.md)   
 [Replikations Verteilungs-Agent](../../relational-databases/replication/agents/replication-distribution-agent.md)   
 [Replikations Protokolllese-Agent](../../relational-databases/replication/agents/replication-log-reader-agent.md)   
 [Replikations Merge-Agent](../../relational-databases/replication/agents/replication-merge-agent.md)   
 [Replikations Warteschlangenlese-Agent](../../relational-databases/replication/agents/replication-queue-reader-agent.md)   
 [Replikations Momentaufnahmen-Agent](../../relational-databases/replication/agents/replication-snapshot-agent.md)   
 [sp_add_agent_parameter &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-add-agent-parameter-transact-sql.md)   
 [sp_drop_agent_parameter &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-drop-agent-parameter-transact-sql.md)   
 [sp_help_agent_parameter &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-help-agent-parameter-transact-sql.md)   
 [Gespeicherte Systemprozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
