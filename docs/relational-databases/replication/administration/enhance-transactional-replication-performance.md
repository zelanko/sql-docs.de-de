---
title: Verbessern der Leistung der Transaktionsreplikation | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- publications [SQL Server replication], design and performance
- performance [SQL Server replication], transactional replication
- designing databases [SQL Server], replication performance
- performance [SQL Server replication], snapshot replication
- snapshot replication [SQL Server], performance
- subscriptions [SQL Server replication], performance considerations
- agents [SQL Server replication], performance
- Distribution Agent, performance
- transactional replication, performance
- Log Reader Agent, performance
ms.assetid: 67084a67-43ff-4065-987a-3b16d1841565
author: MashaMSFT
ms.author: mathoma
monikerRange: =azuresqldb-mi-current||>=sql-server-2014||=sqlallproducts-allversions
ms.openlocfilehash: 2db87395b7170315e14e10db075a4d6ca5721ab3
ms.sourcegitcommit: 728a4fa5a3022c237b68b31724fce441c4e4d0ab
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/03/2019
ms.locfileid: "68768790"
---
# <a name="enhance-transactional-replication-performance"></a>Verbessern der Leistung der Transaktionsreplikation
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]
  Ziehen Sie nach der Erwägung der allgemeinen Leistungstipps, die unter [Enhancing General Replication Performance](../../../relational-databases/replication/administration/enhance-general-replication-performance.md)aufgeführt sind, auch die nachfolgenden Aspekte, die sich speziell auf die Transaktionsreplikation beziehen, in Betracht.  
  
## <a name="database-design"></a>Datenbankentwurf  
  
-   Minimieren Sie den Transaktionsumfang in Ihrem Datenbankentwurf.  
  
     Standardmäßig werden bei der Transaktionsreplikation Änderungen gemäß den Transaktionsgrenzen weitergegeben. Bei Transaktionen geringeren Umfangs ist die Wahrscheinlichkeit geringer, dass der Verteilungs-Agent Transaktionen aufgrund von Netzwerkproblemen erneut übermitteln muss. Wenn der Agent eine Transaktion erneut übermitteln muss, ist der Umfang der gesendeten Daten geringer. 

  
## <a name="distributor-configuration"></a>Konfiguration des Verteilers  
  
-   Konfigurieren Sie den Verteiler auf einem dedizierten Server.  
  
     Durch die Konfiguration eines Remoteverteilers kann der Verarbeitungsaufwand auf dem Verleger reduziert werden. Weitere Informationen finden Sie unter [Configure Distribution](../../../relational-databases/replication/configure-distribution.md).  
  
-   Richten Sie eine angemessene Größe für die Verteilungsdatenbank ein.  
  
     Testen Sie die Replikation unter der typischen Auslastung des Systems, um den Speicherbedarf für Befehle zu ermitteln. Stellen Sie sicher, dass die Datenbank ausreichend Speicherkapazität für Befehle aufweist, um die häufige automatische Vergrößerung zu verhindern. Weitere Informationen zum Ändern der Größe einer Datenbank finden Sie unter [ALTER DATABASE &#40;Transact-SQL&#41;](../../../t-sql/statements/alter-database-transact-sql.md).  
  
## <a name="publication-design"></a>Veröffentlichungsentwurf  
  
-   Replizieren Sie die Ausführung gespeicherter Prozeduren bei der Ausführung von Batchupdates für veröffentlichte Tabellen.  
  
     Wenn Batchupdates vorhanden sind, die gelegentlich eine große Anzahl von Zeilen auf dem Abonnenten betreffen, sollten Sie in Erwägung ziehen, die veröffentlichte Tabelle mithilfe einer gespeicherten Prozedur zu aktualisieren und die Ausführung der gespeicherten Prozedur zu veröffentlichen. Statt ein Update zu übermitteln oder jede betroffene Zeile zu löschen, führt der Verteilungs-Agent dieselbe Prozedur auf dem Abonnenten mit denselben Parameterwerten auf. Weitere Informationen finden Sie unter [Publishing Stored Procedure Execution in Transactional Replication](../../../relational-databases/replication/transactional/publishing-stored-procedure-execution-in-transactional-replication.md).  
  
-   Verteilen Sie Artikel auf mehrere Veröffentlichungen.  
  
     Wenn die Verwendung des [ **-SubscriptionStreams**-Parameters](#subscriptionstreams) nicht möglich ist, ziehen Sie die Erstellung mehrerer Veröffentlichungen in Betracht. Durch das Verteilen von Artikeln auf diese Veröffentlichungen können bei der Replikation Änderungen parallel auf Abonnenten angewendet werden.  
  
## <a name="subscription-considerations"></a>Überlegungen zu Abonnements  
  
-   Wenn Sie auf einem einzigen Verleger über mehrere Veröffentlichungen verfügen, verwenden Sie unabhängige Agents anstelle freigegebener Agents (dies ist die Standardeinstellung im Assistenten für neue Veröffentlichung).  
  
-   Führen Sie Agents fortlaufend statt häufig aus.  
  
     Wenn Sie die Agents für die fortlaufende Ausführung konfigurieren, statt Zeitpläne für die häufige Ausführung (z. B. jede Minute) zu erstellen, führt dies zu einer verbesserten Leistung der Replikation, da der jeweilige Agent nicht gestartet und beendet werden muss. Wenn Sie für den Verteilungs-Agent die fortlaufende Ausführung festlegen, erfolgt die Propagierung von Änderungen auf andere Server, mit denen in der Topologie eine Verbindung besteht, mit geringer Latenzzeit. Weitere Informationen finden Sie in den folgenden Themen:  
  
    -   [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)]: [Angeben von Synchronisierungszeitplänen](../../../relational-databases/replication/specify-synchronization-schedules.md)  
  
## <a name="distribution-agent-and-log-reader-agent-parameters"></a>Parameter für den Verteilungs-Agent und Protokolllese-Agent  
Die Parameter des Agent-Profils werden häufig angepasst, um den Durchsatz des Protokolllese- und Verteilungs-Agents bei OLTP-Systemen mit hohem Datenverkehr zu steigern. 

Mithilfe des Tests wurden die besten Werte zur Verbesserung der Leistung des Protokolllese- und Verteilungs-Agents ermittelt. Dieser Test ergab, dass die Workload ein entscheidender Faktor dafür war, welche Werte in welcher Situation funktionierten. Aus diesem Grund gibt es nicht eine einzige Wertanpassung, die die Leistung für jede Situation verbessert. 

Die Ergebnisse: 
- Für einen *Protokolllese-Agent* mit Workloads kleinerer Transaktionen (weniger als 500 Befehle) kann ein höherer Wert von **ReadBatchSize** den Durchsatz erhöhen. Bei Workloads großer Transaktionen führt eine Änderung dieses Werts jedoch nicht zu einer Leistungssteigerung. 
    - Wenn mehrere Protokolllese-Agents und mehrere Verteilungs-Agents parallel auf demselben Server ausgeführt werden, führt ein höherer Wert von **ReadBatchSize** zu Konflikten in der Verteilungsdatenbank. 
- Für den *Verteilungs-Agent*
    - Die Erhöhung von **CommitBatchSize** kann den Durchsatz verbessern. Der Kompromiss hierbei besteht darin, dass der Verteilungs-Agent im Falle eines Fehlers einen Rollback ausführen und eine größere Anzahl von Transaktionen erneut anwenden muss. 
    - Die Erhöhung des Werts **SubscriptionStreams** trägt zu einem höheren Gesamtdurchsatz des Verteilungs-Agents bei, da mehrere Verbindungen zum Abonnenten mehrere Änderungsbatches parallel anwenden. Abhängig von der Anzahl der Prozessoren und anderen Metadatenbedingungen (wie Primärschlüssel, Fremdschlüssel, einzigartige Einschränkungen und Indizes) kann sich der höhere Wert von „SubscriptionStreams“ jedoch nachteilig auswirken. Kann zudem ein Datenstrom nicht ausgeführt oder committet werden, greift der Verteilungs-Agent auf einen einzelnen Datenstrom zurück, um die nicht erfolgreichen Batches erneut zu verarbeiten.


Weitere Informationen zu diesem Test finden Sie im Blog [Optimizing replication agent profile parameters for better performance](https://blogs.msdn.microsoft.com/sql_server_team/optimizing-replication-agent-profile-parameters-for-better-performance/) (Optimierung der Profilparameter des Replikations-Agents für eine bessere Leistung).


### <a name="log-reader-agent"></a>Protokolllese-Agent

#### <a name="readbatchsize"></a>ReadBatchSize
- Erhöhen Sie den Wert des **-ReadBatchSize** -Parameters für den Protokolllese-Agent.  
  
Der Protokolllese- und der Verteilungs-Agent unterstützen Batchgrößen für Transaktionslese- und Commitoperationen. Die Batchgrößen werden standardmäßig auf 500 Transaktionen festgelegt. Der Protokolllese-Agent liest die angegebene Anzahl von Transaktionen aus dem Protokoll, unabhängig davon, ob sie für die Replikation markiert wurden. Wenn eine große Anzahl von Transaktionen in eine Veröffentlichungsdatenbank geschrieben wird, aber nur ein kleiner Teil dieser Transaktionen für die Replikation markiert wurde, sollten Sie mit dem **-ReadBatchSize**-Parameter die Lesebatchgröße des Protokolllese-Agents steigern. Dieser Parameter gilt nicht für Oracle-Verleger.  

   - Bei Workloads kleinerer Transaktionen (weniger als 500 Befehle) gibt es eine Steigerung bezüglich der Anzahl der pro Sekunde verarbeiteten Befehle, wenn **ReadBatchSize** auf 5000 erhöht wird. 
   - Bei umfangreicheren Workloads (Transaktionen mit 500 bis 1000 Befehlen) hat die Erhöhung von **ReadBatchSize** nur eine geringe Leistungssteigerung zur Folge. Die Erhöhung von **ReadBatchSize** führt bei einer größeren Anzahl der in die Verteilungsdatenbank geschriebenen Transaktionen zu einem Roundtrip. Hierdurch sind die Transaktionen und Befehle für den Verteilungs-Agent länger sichtbar, und es kommt zu einer Wartezeit bis zum Replikationsvorgang.  

#### <a name="pollinginterval"></a>PollingInterval
- Verringern Sie den Wert des **-PollingInterval** -Parameters für den Protokolllese-Agent.  
  
Über den **-PollingInterval** -Parameter wird angegeben, wie oft das Transaktionsprotokoll einer veröffentlichten Datenbank hinsichtlich Transaktionen für die Replikation abgefragt wird. Die Standardeinstellung ist 5 Sekunden. Wenn Sie diesen Wert verringern, wird das Protokoll häufiger abgefragt. Dies kann zu einer geringeren Latenzzeit bei der Übermittlung von Transaktionen von der Veröffentlichungsdatenbank an die Verteilungsdatenbank führen. Sie sollten jedoch um ein Gleichgewicht zwischen einer geringeren Latenzzeit und der erhöhten Last auf dem Server durch häufigeres Abfragen bemüht sein.   
  
#### <a name="maxcmdsintran"></a>MaxCmdsInTran
- Um unbeabsichtigte, einmalige Engpässe zu vermeiden, verwenden Sie den **–MaxCmdsInTran** -Parameter für den Protokolllese-Agent.  
  
Mit dem **–MaxCmdsInTran** -Parameter wird die maximale Anzahl von Anweisungen angegeben, die in einer Transaktion zusammengefasst werden, wenn der Protokollleser Befehle in die Verteilungsdatenbank schreibt. Mithilfe dieses Parameters können der Protokolllese-Agent und der Verteilungs-Agent beim Anwenden von Befehlen auf dem Abonnenten umfangreiche Transaktionen (die aus zahlreichen Befehlen bestehen) auf dem Verleger in mehrere kleinere Transaktionen aufteilen. Durch die Angabe dieses Parameters kommt es auf dem Verteiler möglicherweise zu weniger Konflikten, und die Latenzzeit zwischen Verleger und Abonnent kann reduziert werden. Da die ursprüngliche Transaktion in kleineren Einheiten angewendet wird, kann der Abonnent vor Ende der ursprünglichen Transaktion auf Zeilen einer umfangreichen logischen Verleger-Transaktion zugreifen; dies widerspricht der strikten Unteilbarkeit von Transaktionen. **0**ist der Standardwert, durch den die Transaktionsgrenzen des Verlegers beibehalten werden. Dieser Parameter gilt nicht für Oracle-Verleger.  
  
   > [!WARNING]  
   >  **MaxCmdsInTran** ist nicht auf die dauerhafte Aktivierung ausgelegt. Der Parameter ist als Umgehungslösung für den Fall konzipiert, dass versehentlich eine große Anzahl von DML-Vorgängen in einer einzelnen Transaktion ausgeführt wird (was zu einer verzögerten Verteilung der Befehle führen kann, bis sich die gesamte Transaktion in der Verteilungsdatenbank befindet, Sperren aufrecht erhalten werden usw.). Wenn diese Situation häufiger auftritt, überarbeiten Sie Ihre Anwendungen, und suchen Sie nach Möglichkeiten, die Transaktionsgröße zu verringern.  
  
### <a name="distribution-agent"></a>Verteilungs-Agent

#### <a name="subscriptionstreams"></a>SubscriptionStreams
- Erhöhen Sie den **-SubscriptionStreams**-Parameter für den Verteilungs-Agent.  
  
Durch den **–SubscriptionStreams** -Parameter kann es zu einer deutlichen Steigerung des Replikationsgesamtdurchsatzes kommen. Er ermöglicht es mehreren Verbindungen mit dem Abonnenten, Batches für Änderungen parallel anzuwenden und eine Vielzahl der Transaktionseigenschaften beizubehalten, die bei Verwendung eines Singlethreads vorhanden waren. Wenn eine der Verbindungen oder ein Commit hierfür nicht ausgeführt werden kann, wird der aktuelle Batch von allen Verbindungen verworfen, und der Agent versucht mithilfe eines einzigen Datenstroms, die fehlgeschlagenen Batches zu wiederholen. Vor dem Abschluss dieser Wiederholungsphase kann es auf dem Abonnenten vorübergehend zur Transaktionsinkonsistenzen kommen. Nach dem erfolgreichen Ausführen (Commit) der fehlgeschlagenen Batches wird der Abonnent wieder in einen Zustand der Transaktionskonsistenz versetzt.  
  
Ein Wert für diesen Agentparameter kann angegeben werden, mit der **@subscriptionstreams** von [sp_addsubscription &#40;Transact-SQL&#41;](../../../relational-databases/system-stored-procedures/sp-addsubscription-transact-sql.md).  

Weitere Informationen zum Implementieren von Abonnementdatenströmen finden Sie unter [Navigating SQL replication subscriptionStream setting](https://blogs.msdn.microsoft.com/repltalk/2010/03/01/navigating-sql-replication-subscriptionstreams-setting) (Navigieren in der subscriptionStream-Einstellung für die SQL-Replikation).
  
### <a name="blocking-monitor-thread"></a>Überwachungsthread für Blockierungen

Der Verteilungs-Agent verwaltet einen Überwachungsthread, der Blockierung zwischen Sitzungen erkennt. Wenn dieser Überwachungsthread eine Blockierung zwischen den Sitzungen erkennt, geht der Verteilungs-Agent dazu über, eine Sitzung zu verwenden, um die aktuellen Befehle, die zuvor nicht angewendet werden konnten, erneut anzuwenden.

Der Überwachungsthread kann Blockierungen zwischen Sitzungen des Verteilungs-Agents erkennen. In folgenden Sitzungen werden Blockierungen jedoch nicht von diesem Überwachungsthread erkannt:
- Eine der Sitzungen, bei der eine Blockierung auftritt, ist keine Sitzung des Verteilungs-Agents.
- Eine Sitzung führt zu einem Deadlock und friert die Aktivitäten des Verteilungs-Agents ein.

In dieser Situation koordiniert der Verteilungs-Agent alle Sitzungen, damit ein gemeinsamer Commit ausgeführt wird, sobald die Befehle ausgeführt wurden. Ein Deadlock kann zwischen den Sitzungen auftreten, wenn folgende Bedingungen erfüllt sind:

- Die Blockierung tritt zwischen einer Sitzung des Verteilungs-Agents und einer Sitzung, die nicht vom Verteilungs-Agent stammt, auf.
- Der Verteilungs-Agent wartet, bis alle Sitzungen ihre Befehle ausgeführt haben, bevor alle Sitzungen für einen gemeinsamen Commit koordiniert werden.

Nehmen Sie an, dass Sie den Parameter *SubscriptionStreams* auf 8 festlegen. Sitzung 10 bis 17 sind Sitzungen des Verteilungs-Agents. Sitzung 18 ist keine Sitzung des Verteilungs-Agents. Sitzung 10 wird von Sitzung 18 blockiert, und Sitzung 18 wird von Sitzung 11 blockiert. Darüber hinaus muss ein gemeinsamer Commit für Sitzung 10 und Sitzung 11 ausgeführt werden. Der Verteilungs-Agent kann jedoch aufgrund der Blockierung keinen gemeinsamen Commit für Sitzung 10 und 11 ausführen. Aus diesem Grund kann der Verteilungs-Agent diese acht Sitzungen nicht für einen gemeinsamen Commit koordinieren, bis Sitzung 10 und 11 ihre Befehle ausgeführt haben.

Dieses Beispielszenario führt zu einem Zustand, in dem keine Sitzung ihre Befehle ausführt. Wenn die Zeit erreicht ist, die in der Eigenschaft **QueryTimeout** festgelegt ist, bricht der Verteilungs-Agent alle Sitzungen ab.

> [!Note]
> Der Standardwert von **QueryTimeout** ist 5 Minuten.

Während des Timeoutzeitraums der Abfrage werden Sie Folgendes bei den Leistungsindikatoren des Verteilungs-Agents bemerken: 

- Der Wert des Leistungsindikators **Verteiler: Übermittelte Befehle/Sekunde** beträgt immer 0.
- Der Wert des Leistungsindikators **Verteiler: Übermittelte Transaktionen/Sekunde** beträgt immer 0.
- Der Leistungsindikator **Verteiler: Übermittlungslatenz** meldet einen Anstieg des Werts, bis der Deadlock des Threads behoben ist.

Das Thema „Replication Distribution Agent (Replikationsverteilungs-Agent)“ in der SQL Server-Onlinedokumentation enthält die folgende Beschreibung für den Parameter *SubscriptionStreams*: „Wenn eine der Verbindungen oder ein Commit hierfür nicht ausgeführt werden kann, wird der aktuelle Batch von allen Verbindungen verworfen, und der Agent versucht mithilfe eines einzelnen Datenstroms, die fehlgeschlagenen Batches zu wiederholen.“

Der Verteilungs-Agent verwendet eine Sitzung, um den Batch zu wiederholen, der nicht angewendet werden konnte. Nachdem der Verteilungs-Agent den Batch erfolgreich angewendet hat, verwendet er wieder mehrere Sitzungen, ohne einen Neustart durchzuführen.

#### <a name="commitbatchsize"></a>CommitBatchSize
- Erhöhen Sie den Wert des **-CommitBatchSize** -Parameters für den Verteilungs-Agent.  
  
Das Ausführen (Commit) eines Satzes an Transaktionen führt zu einem bestimmten Verwaltungsaufwand; wenn eine größere Anzahl an Transaktionen mit größerem Zeitabstand ausgeführt werden (Commit), verteilt sich der Verwaltungsaufwand auf einen größeren Datenumfang.  Die Erhöhung von „CommitBatchSize“ (auf bis zu 200) kann die Leistung verbessern, da mehr Transaktionen an den Abonnenten committet werden. Der Vorteil des Verringerns dieses Parameters wird geringer, wenn die Kosten der Anwendung von Änderungen durch andere Faktoren beeinträchtigt werden, beispielsweise der maximalen E/A des Datenträgers, auf dem das Protokoll enthalten ist. Zudem muss folgender Kompromiss beachtet werden: Durch jeden Fehler, der dazu führt, dass der Verteilungs-Agent von vorn beginnt, muss für eine größere Anzahl von Transaktionen ein Rollback ausgeführt sowie die erneute Anwendung vorgenommen werden. Bei unzuverlässigen Netzwerken kann ein geringerer Wert zu weniger Fehler führen, und im Falle eines Fehlers muss das Rollback bzw. die erneute Anwendung für eine geringere Anzahl an Transaktionen ausgeführt werden.  
  

## <a name="see-more"></a>Weitere Informationen
  
[Arbeiten mit Replikations-Agent-Profilen](../../../relational-databases/replication/agents/work-with-replication-agent-profiles.md)  
[Anzeigen und Ändern von Befehlszeilenparametern des Replikations-Agents &#40;SQL Server Management Studio&#41;](../../../relational-databases/replication/agents/view-and-modify-replication-agent-command-prompt-parameters.md)  
[Ausführbare Konzepte für die Programmierung von Replikations-Agent](../../../relational-databases/replication/concepts/replication-agent-executables-concepts.md)  
  
  
