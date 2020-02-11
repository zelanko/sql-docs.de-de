---
title: MSSQL_REPL027056 | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- MSSQL_REPL027056 error
ms.assetid: 92d62f3c-b8ae-482e-a348-2e9a8ee9786e
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: fd6f1d63b0de5e8ce0fda7ab4fbc727c70f67bbd
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "63022736"
---
# <a name="mssql_repl027056"></a>MSSQL_REPL027056
    
## <a name="message-details"></a>Meldungsdetails  
  
|||  
|-|-|  
|Produktname|SQL Server|  
|Ereignis-ID|27056|  
|Ereignisquelle|MSSQLSERVER|  
|Komponente|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|  
|Symbolischer Name||  
|Meldungstext|Vom Mergeprozess konnte der Generierungsverlauf auf '%1' nicht geändert werden. Führen Sie zur Problembehandlung einen Neustart der Synchronisierung mit ausführlicher Verlaufsprotokollierung aus, und geben Sie eine Ausgabedatei an, in die geschrieben werden soll.|  
  
## <a name="explanation"></a>Erklärung  
 Dieser Fehler wird in der Regel als Folge eine Konflikts in Systemtabellen der Mergereplikation ausgelöst, die extrem groß geworden sind. Meistens entstehen große Systemtabellen aufgrund einer langen Beibehaltungsdauer von Veröffentlichungen, da Metadaten bis zum Ablauf der Beibehaltungsdauer gespeichert werden müssen.  
  
## <a name="user-action"></a>Benutzeraktion  
 **So lösen Sie das Problem:**  
  
1.  Verringern Sie den Wert der Parameter -**DownloadGenerationsPerBatch** und **-UploadGenerationsPerBatch** für den Merge-Agent, damit die Verarbeitung fortgesetzt werden kann und Sie sich der eigentlichen Ursache des Fehlers widmen können. Agentparameter können in den Agentprofilen und in der Befehlszeile angegeben werden. Weitere Informationen finden Sie unter  
  
    -   [Arbeiten mit Replikations-Agent-Profilen](agents/replication-agent-profiles.md)  
  
    -   [Anzeigen und Ändern von Befehlszeilenparametern des Replikations-Agents &#40;SQL Server Management Studio&#41;](agents/view-and-modify-replication-agent-command-prompt-parameters.md)  
  
    -   [Replication Agent Executables Concepts](concepts/replication-agent-executables-concepts.md)zugeordnet ist.  
  
2.  Geben Sie die Beibehaltungsdauer für die Veröffentlichung so niedrig wie möglich an. Weitere Informationen finden Sie unter [Subscription Expiration and Deactivation](subscription-expiration-and-deactivation.md).  
  
3.  Als Teil der Wartung für die Mergereplikation überprüfen Sie gelegentlich die Vergrößerung der Systemtabellen, die mit der Mergereplikation verbunden sind: **MSmerge_contents**, **MSmerge_genhistory**, **MSmerge_tombstone**, **MSmerge_current_partition_mappings**und **MSmerge_past_partition_mappings**. Führen Sie eine regelmäßige Neuindizierung dieser Tabellen durch. Weitere Informationen finden Sie unter [Neuorganisieren und Neuerstellen von Indizes](../indexes/indexes.md).  
  
## <a name="see-also"></a>Weitere Informationen  
 [Fehler- und Ereignisreferenz &#40;Replikation&#41;](errors-and-events-reference-replication.md)  
  
  
