---
title: In master gespeicherte Prozeduren übertragen (Task) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.transfermasterspstask.f1
helpviewer_keywords:
- Transfer Master Stored Procedures task [Integration Services]
ms.assetid: 81702560-48a3-46d1-a469-e41304c7af8e
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 0b7763c8aeffe60c361a9f54ac3c9657653af40a
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48150230"
---
# <a name="transfer-master-stored-procedures-task"></a>In master gespeicherte Prozeduren übertragen (Task)
  Der Task „In 'master' gespeicherte Prozeduren übertragen“ überträgt mindestens eine benutzerdefinierte gespeicherte Prozedur zwischen den **master** -Datenbanken der Instanzen von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Um eine gespeicherte Prozedur von der **master** -Datenbank zu übertragen, muss dbo der Besitzer der gespeicherten Prozedur sein.  
  
 Der Task "In 'master' gespeicherte Prozeduren übertragen" kann zum Übertragen aller gespeicherten Prozeduren oder nur bestimmter gespeicherter Prozeduren konfiguriert werden. Dieser Task kopiert keine gespeicherten Systemprozeduren.  
  
 Die zu übertragenden gespeicherten 'master'-Prozeduren sind eventuell bereits am Ziel vorhanden. Der Task "In 'master' gespeicherte Prozeduren übertragen" kann zur Verarbeitung bereits vorhandener gespeicherter Prozeduren auf folgende Art und Weise konfiguriert werden:  
  
-   Überschreiben bereits vorhandener gespeicherter Prozeduren.  
  
-   Fehlschlagen des Tasks, wenn doppelte gespeicherte Prozeduren vorhanden sind.  
  
-   Überspringen von doppelten gespeicherten Prozeduren.  
  
 Zur Laufzeit stellt der Task "In 'master' gespeicherte Prozeduren übertragen" eine Verbindung mit den Quell- und Zielservern her. Dazu werden die SMO-Verbindungs-Manager verwendet. Die SMO-Verbindungs-Manager werden getrennt vom Task "In 'master' gespeicherte Prozeduren übertragen" konfiguriert. Es wird darauf dann im Task "In 'master' gespeicherte Prozeduren übertragen" verwiesen. Die SMO-Verbindungs-Manager geben den Server- und Authentifizierungsmodus an, der beim Zugriff auf den Server verwendet werden soll. Weitere Informationen finden Sie unter [SMO Connection Manager](../connection-manager/smo-connection-manager.md).  
  
## <a name="transferring-stored-procedures-between-instances-of-sql-server"></a>Übertragen von gespeicherten Prozeduren zwischen den Instanzen von SQL Server  
 Der Task "In 'master' gespeicherte Prozeduren übertragen" unterstützt eine [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Quelle und ein -Ziel.  
  
## <a name="events"></a>Ereignisse  
 Der Task löst ein Informationsereignis aus, das die Anzahl der übertragenen gespeicherten Prozeduren meldet, sowie ein Warnungsereignis, wenn eine gespeicherte Prozedur überschrieben wird.  
  
 Der Task "In 'master' gespeicherte Prozeduren übertragen" meldet keinen schrittweisen Fortschritt der Anmeldeübertragung; er meldet nur 0 % und 100 % der Ausführung.  
  
## <a name="execution-value"></a>Ausführungswert  
 Der Ausführungswert, definiert in der `ExecutionValue` -Eigenschaft des Tasks, gibt die Anzahl der übertragenen gespeicherten Prozeduren zurück. Durch eine benutzerdefinierte Variable zugewiesen der `ExecValueVariable` -Eigenschaft des Tasks Übertragung in Master gespeicherte Prozeduren, Informationen über die gespeicherte Prozedur kann zur Verfügung gestellt werden auf andere Objekte im Paket. Weitere Informationen finden Sie unter [Integration Services-Variablen &#40;SSIS&#41;](../integration-services-ssis-variables.md) und [Verwenden von Variablen in Paketen](../use-variables-in-packages.md).  
  
## <a name="log-entries"></a>Protokolleinträge  
 Der Task "In 'master' gespeicherte Prozeduren übertragen" enthält die folgenden benutzerdefinierten Protokolleinträge:  
  
-   TransferStoredProceduresTaskStartTransferringObjects  Dieser Protokolleintrag meldet, dass die Übertragung begonnen hat. Der Protokolleintrag enthält die Startzeit.  
  
-   TransferSStoredProceduresTaskFinishedTransferringObjects  Dieser Protokolleintrag meldet, dass die Übertragung abgeschlossen ist. Der Protokolleintrag enthält die Beendigungszeit.  
  
 Außerdem wird ein Protokolleintrag für die `OnInformation` -Ereignis meldet die Anzahl der übertragenen gespeicherten Prozeduren und ein Protokolleintrag für die `OnWarning` Ereignis wird für jede gespeicherte Prozedur auf dem Ziel, die überschrieben wird geschrieben.  
  
## <a name="security-and-permissions"></a>Sicherheit und Berechtigungen  
 Der Benutzer muss über die Berechtigung zum Anzeigen der Liste mit gespeicherten Prozeduren in der **master** -Datenbank der Quelle verfügen und Mitglied der sysadmin-Serverrolle sein oder über Berechtigungen zum Erstellen von gespeicherten Prozeduren in der **master** -Datenbank auf dem Zielserver verfügen.  
  
## <a name="configuration-of-the-transfer-master-stored-procedures-task"></a>Konfiguration der Tasks "In 'master' gespeicherte Prozeduren übertragen"  
 Sie können Eigenschaften mit dem [!INCLUDE[ssIS](../../includes/ssis-md.md)] -Designer oder programmgesteuert festlegen.  
  
 Klicken Sie auf eines der folgenden Themen, um Informationen zu den Eigenschaften zu erhalten, die Sie im [!INCLUDE[ssIS](../../includes/ssis-md.md)] -Designer festlegen können:  
  
-   [Task-Editor für Master gespeicherte Prozeduren übertragen &#40;Seite "Allgemein"&#41;](../general-page-of-integration-services-designers-options.md)  
  
-   [Task-Editor für Master gespeicherte Prozeduren übertragen &#40;gespeicherte Prozeduren-Seite&#41;](../transfer-master-stored-procedures-task-editor-stored-procedures-page.md)  
  
-   [Seite Ausdrücke](../expressions/expressions-page.md)  
  
 Klicken Sie auf das folgende Thema, um Informationen zum programmgesteuerten Festlegen dieser Eigenschaften anzuzeigen:  
  
-   <xref:Microsoft.SqlServer.Dts.Tasks.TransferStoredProceduresTask.TransferStoredProceduresTask>  
  
### <a name="configuring-the-transfer-master-stored-procedures-task-programmatically"></a>Programmgesteuertes Konfigurieren des Tasks "In 'master' gespeicherte Prozeduren übertragen"  
  
## <a name="related-tasks"></a>Related Tasks  
 Klicken Sie auf das folgende Thema, um weitere Informationen zum Festlegen dieser Eigenschaften im [!INCLUDE[ssIS](../../includes/ssis-md.md)] -Designer zu erhalten:  
  
-   [Festlegen der Eigenschaften eines Tasks oder Containers](../set-the-properties-of-a-task-or-container.md)  
  
## <a name="see-also"></a>Siehe auch  
 [Task von SQL Server-Objekte übertragen](transfer-sql-server-objects-task.md)   
 [Integration Services-Tasks](integration-services-tasks.md)   
 [Ablaufsteuerung](control-flow.md)  
  
  
