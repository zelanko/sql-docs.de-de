---
title: Ausführbare Konzepte für die Programmierung von Replikations-Agents | Microsoft-Dokumentation
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: reference
helpviewer_keywords:
- programming interfaces [SQL Server replication]
- programming [SQL Server replication], agents
- replication [SQL Server], agents and profiles
- agents [SQL Server replication], executables
- command prompt [SQL Server replication]
ms.assetid: cba476df-d4ea-44c9-bb86-81488971e328
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 451b7ca4cc06269f116c62be2ef7f01f0e33abd2
ms.sourcegitcommit: 7aa6beaaf64daf01b0e98e6c63cc22906a77ed04
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/09/2019
ms.locfileid: "54132710"
---
# <a name="replication-agent-executables-concepts"></a>Ausführbare Konzepte für die Programmierung von Replikations-Agents
  Replikations-Agents können wie folgt programmgesteuert kontrolliert werden:  
  
-   Mit den verwalteten Schnittstellen für die Agent-Programmierung im <xref:Microsoft.SqlServer.Replication> Namespace  
  
-   Durch Aufrufen von ausführbaren Dateien von Agents mit einem angegebenen Satz von Parametern von der Eingabeaufforderung aus  
  
 Das direkte Aufrufen von Replikations-Agents von der Eingabeaufforderung aus ermöglicht den programmgesteuerten Zugriff auf Agents vom Befehlszeilenskript in Batchdateien. Wenn ein Agent von der Eingabeaufforderung aus aufgerufen wird, wird er unter dem [!INCLUDE[msCoName](../../../includes/msconame-md.md)]-Windows-Sicherheitskonto des Benutzers ausgeführt, der den Agent aufgerufen oder die Batchdatei gestartet hat.  
  
 Instanzen der folgenden Replikations-Agents können mit ausführbaren Dateien ausgeführt werden.  
  
-   [Replikationsverteilungs-Agent](../agents/replication-distribution-agent.md)  
  
-   [Replikationsprotokolllese-Agent](../agents/replication-log-reader-agent.md)  
  
-   [Replication Merge Agent](../agents/replication-merge-agent.md)  
  
-   [Replication Queue Reader Agent](../agents/replication-queue-reader-agent.md)  
  
-   [Replication Snapshot Agent](../agents/replication-snapshot-agent.md)  
  
 Beim Aufrufen von Replikations-Agents können Sie Leistungsprofile verwenden, um einen definierten Satz von Parametern automatisch an die ausführbare Datei des Agents zu übergeben. Weitere Informationen finden Sie unter [Replication Agent Profiles](../agents/replication-agent-profiles.md).  
  
## <a name="examples"></a>Beispiele  
 Die folgenden Beispiele zeigen, wie Replikations-Agents von der Eingabeaufforderung aus aufgerufen werden. Replikations-Agents können auch mit Replikationsverwaltungsobjekten (Replication Management Objects, RMO) aufgerufen werden. Weitere Informationen finden Sie unter [Synchronisieren von Abonnements](../synchronize-data.md).  
  
> [!NOTE]  
>  Zeilenumbrüche wurden in diesen Beispielen hinzugefügt, um die Lesbarkeit zu verbessern. In einer Batchdatei müssen Befehle in einer einzelnen Zeile stehen.  
  
### <a name="running-the-snapshot-agent"></a>Ausführen des Momentaufnahme-Agents  
 Mit dieser Beispielbatchdatei wird der Momentaufnahme-Agent von der Befehlsaufforderung aus aufgerufen, um eine Momentaufnahme für die **AdvWorksSalesOrdersMerge**-Veröffentlichung zu generieren.  
  
```  
REM -- Declare variables  
SET Publisher=%InstanceName%;  
SET PublicationDB=AdventureWorks2012;   
SET Publication=AdvWorksSalesOrdersMerge;   
  
REM --Start the Snapshot Agent to generate the snapshot for AdvWorksSalesOrdersMerge.  
"C:\Program Files\Microsoft SQL Server\120\COM\SNAPSHOT.EXE" -Publication %Publication%   
-Publisher %Publisher% -Distributor %Publisher% -PublisherDB %PublicationDB%   
-ReplicationType 2 -OutputVerboseLevel 1 -DistributorSecurityMode 1 ;  
  
```  
  
### <a name="running-the-distribution-agent"></a>Ausführen des Verteilungs-Agents  
 Mit dieser Beispielbatchdatei wird der Verteilungs-Agent von der Eingabeaufforderung aus aufgerufen, um Änderungen der **AdvWorksProductTran**-Veröffentlichung kontinuierlich an einen Pushabonnenten zu replizieren.  
  
```  
REM -- Declare the variables.  
SET Publisher=%instancename%;  
SET Subscriber=%instancename%;  
SET PublicationDB=AdventureWorks2012;  
SET SubscriptionDB=AdventureWorks2012Replica;   
SET Publication=AdvWorksProductsTran;  
  
REM -- Start the Distribution Agent with four subscription streams.  
REM -- The following command must be supplied without line breaks.  
"C:\Program Files\Microsoft SQL Server\120\COM\DISTRIB.EXE" -Subscriber %Subscriber%   
-SubscriberDB %SubscriptionDB% -SubscriberSecurityMode 1 -Publication %Publication%   
-Publisher %Publisher% -PublisherDB %PublicationDB% -Distributor %Publisher%   
-DistributorSecurityMode 1 -Continuous -SubscriptionType 0 -SubscriptionStreams 4 ;  
  
```  
  
### <a name="running-the-merge-agent"></a>Ausführen des Merge-Agents  
 Mit dieser Beispielbatchdatei wird der Merge-Agent von der Eingabeaufforderung aus aufgerufen, um ein Pullabonnement für die **AdvWorksSalesOrdersMerge**-Veröffentlichung zu synchronisieren.  
  
```  
REM -- Declare the variables.  
SET Publisher=%instancename%;  
SET Subscriber=%instancename%;  
SET PublicationDB=AdventureWorks2012;  
SET SubscriptionDB=AdventureWorks2012Replica;   
SET Publication=AdvWorksSalesOrdersMerge;  
  
REM --Start the Merge Agent with concurrent upload and download processes.  
REM -- The following command must be supplied without line breaks.  
"C:\Program Files\Microsoft SQL Server\120\COM\REPLMERG.EXE" -Publication %Publication%    
-Publisher %Publisher%  -Subscriber  %Subscriber%  -Distributor %Publisher%    
-PublisherDB %PublicationDB%  -SubscriberDB %SubscriptionDB% -PublisherSecurityMode 1    
-OutputVerboseLevel 2  -SubscriberSecurityMode 1  -SubscriptionType 1 -DistributorSecurityMode 1    
-Validate 3  -ParallelUploadDownload 1 ;  
  
```  
  
  
