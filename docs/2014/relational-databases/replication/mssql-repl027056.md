---
title: MSSQL_REPL027056 | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- replication
ms.topic: conceptual
helpviewer_keywords:
- MSSQL_REPL027056 error
ms.assetid: 92d62f3c-b8ae-482e-a348-2e9a8ee9786e
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: a9cdd464be0ae756faf3e66f8ac7e3cf8c1b63ae
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48113790"
---
# <a name="mssqlrepl027056"></a>MSSQL_REPL027056
    
## <a name="message-details"></a>Meldungsdetails  
  
|||  
|-|-|  
|Produktname|SQL Server|  
|Ereignis-ID|27056|  
|Ereignisquelle|MSSQLSERVER|  
|Komponente|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|  
|Symbolischer Name||  
|Meldungstext|Vom Mergeprozess konnte der Generierungsverlauf auf '%1' nicht geändert werden. Führen Sie zur Problembehandlung einen Neustart der Synchronisierung mit ausführlicher Verlaufsprotokollierung aus, und geben Sie eine Ausgabedatei an, in die geschrieben werden soll.|  
  
## <a name="explanation"></a>Erklärung  
 Dieser Fehler wird in der Regel als Folge eine Konflikts in Systemtabellen der Mergereplikation ausgelöst, die extrem groß geworden sind. Meistens entstehen große Systemtabellen aufgrund einer langen Beibehaltungsdauer von Veröffentlichungen, da Metadaten bis zum Ablauf der Beibehaltungsdauer gespeichert werden müssen.  
  
## <a name="user-action"></a>Benutzeraktion  
 **So lösen Sie das Problem:**  
  
1.  Verringern Sie den Wert der Parameter -**DownloadGenerationsPerBatch** und **-UploadGenerationsPerBatch** für den Merge-Agent, damit die Verarbeitung fortgesetzt werden kann und Sie sich der eigentlichen Ursache des Fehlers widmen können. Agentparameter können in den Agentprofilen und in der Befehlszeile angegeben werden. Weitere Informationen finden Sie in den folgenden Themen:  
  
    -   [Arbeiten mit Replikations-Agent-Profilen](agents/replication-agent-profiles.md)  
  
    -   [Anzeigen und Ändern von Befehlszeilenparametern des Replikations-Agents &#40;SQL Server Management Studio&#41;](agents/view-and-modify-replication-agent-command-prompt-parameters.md)  
  
    -   [Replication Agent Executables Concepts](concepts/replication-agent-executables-concepts.md)zugeordnet ist.  
  
2.  Geben Sie die Beibehaltungsdauer für die Veröffentlichung so niedrig wie möglich an. Weitere Informationen finden Sie unter [Subscription Expiration and Deactivation](subscription-expiration-and-deactivation.md).  
  
3.  Als Teil der Wartung für die Mergereplikation überprüfen Sie gelegentlich die Vergrößerung der Systemtabellen, die mit der Mergereplikation verbunden sind: **MSmerge_contents**, **MSmerge_genhistory**, **MSmerge_tombstone**, **MSmerge_current_partition_mappings**und **MSmerge_past_partition_mappings**. Führen Sie eine regelmäßige Neuindizierung dieser Tabellen durch. Weitere Informationen finden Sie unter [Neuorganisieren und Neuerstellen von Indizes](../indexes/indexes.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Fehler- und Ereignisreferenz &#40;Replikation&#41;](errors-and-events-reference-replication.md)  
  
  
