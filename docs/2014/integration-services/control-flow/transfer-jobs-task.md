---
title: Aufträge übertragen (Task) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.transferjobstask.f1
helpviewer_keywords:
- Transfer Jobs task [Integration Services]
ms.assetid: 1bf33885-9c5b-47e4-a549-f5920b66a1de
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 03913242246fcdaf11e9272e827cd8e06951a108
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "62829896"
---
# <a name="transfer-jobs-task"></a>Aufträge übertragen (Task)
  Durch die Task "Aufträge übertragen" werden ein oder mehrere Aufträge des [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agents zwischen Instanzen von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]übertragen.  
  
 Der Task Aufträge übertragen kann so konfiguriert werden, dass alle Aufträge oder nur bestimmte Aufträge übertragen werden. Sie können auch angeben, ob die übertragenen Aufträge auf dem Ziel aktiviert werden sollen.  
  
 Die zu übertragenden Aufträge sind auf dem Ziel möglicherweise schon vorhanden. Es gibt folgende Möglichkeiten, um den Task Aufträge übertragen so zu konfigurieren, dass bereits vorhandene Aufträge behandelt werden:  
  
-   Vorhandene Aufträge werden überschrieben.  
  
-   Der Auftrag erzeugt einen Fehler, wenn doppelte Aufträge vorhanden sind.  
  
-   Doppelte Aufträge werden ausgelassen.  
  
 Zur Laufzeit stellt der Task Aufträge übertragen mithilfe eines oder zweier SMO-Verbindungs-Manager eine Verbindung mit dem Quell- und Zielserver her. Der SMO-Verbindungs-Manager wird unabhängig vom Task Aufträge übertragen konfiguriert, und im Task Aufträge übertragen wird dann darauf verwiesen. Im SMO-Verbindungs-Manager wird der Server sowie der für den Zugriff auf den Server zu verwendende Authentifizierungsmodus angegeben. Weitere Informationen finden Sie unter [SMO Connection Manager](../connection-manager/smo-connection-manager.md).  
  
## <a name="transferring-jobs-between-instances-of-sql-server"></a>Übertragen von Aufträgen zwischen Instanzen von SQL Server  
 Die Task "Aufträge übertragen" unterstützt [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Quellen und -Ziele. Es gibt keinerlei Beschränkungen, welche Version Sie als Quelle oder Ziel verwenden.  
  
## <a name="events"></a>Ereignisse  
 Der Task Aufträge übertragen löst ein Informationsereignis aus, in dem die Anzahl der übertragenen Aufträge angegeben ist, und ein Warnungsereignis, wenn ein Auftrag überschrieben wird. Während der Auftrag übertragen wird, werden keine Angaben zum Fortschritt des Vorgangs gemacht – es wird lediglich 0 % und bei Abschluss 100 % angezeigt.  
  
## <a name="execution-value"></a>Ausführungswert  
 Der in der `ExecutionValue`-Eigenschaft des Tasks definierte Ausführungswert gibt die Anzahl der zu übertragenden Aufträge zurück. Mithilfe einer benutzerdefinierten Variable, die der `ExecValueVariable`-Eigenschaft des Tasks Aufträge übertragen zugewiesen wird, können Informationen zur Auftragsübertragung für andere Objekte des Pakets verfügbar gemacht werden. Weitere Informationen finden Sie unter [Integration Services-Variablen &#40;SSIS&#41;](../integration-services-ssis-variables.md) und [Verwenden von Variablen in Paketen](../use-variables-in-packages.md).  
  
## <a name="log-entries"></a>Protokolleinträge  
 Der Task Aufträge übertragen enthält die folgenden benutzerdefinierten Protokolleinträge:  
  
-   TransferJobsTaskStarTransferringObjects   Dieser Protokolleintrag gibt an, dass die Übertragung gestartet wurde. Der Protokolleintrag enthält die Startzeit.  
  
-   TransferJobsTaskFinishedTransferringObjects    Dieser Protokolleintrag gibt an, dass die Übertragung abgeschlossen wurde. Der Protokolleintrag enthält die Beendigungszeit.  
  
 Außerdem gibt ein Protokolleintrag für das `OnInformation`-Ereignis die Anzahl der übertragenen Aufträge an. Schließlich wird ein Protokolleintrag für das `OnWarning`-Ereignis für jeden auf dem Ziel überschriebenen Auftrag erstellt.  
  
## <a name="security-and-permissions"></a>Sicherheit und Berechtigungen  
 Zum Übertragen von Aufträgen muss der Benutzer sowohl in der Quell- als auch in der Zielinstanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ein Mitglied der festen Serverrolle sysadmin oder einer der festen Datenbankrollen für den [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Agent der msdb-Datenbank sein.  
  
## <a name="configuration-of-the-transfer-jobs-task"></a>Konfiguration des Tasks "Aufträge übertragen"  
 Sie können Eigenschaften mit dem [!INCLUDE[ssIS](../../includes/ssis-md.md)] -Designer oder programmgesteuert festlegen.  
  
 Klicken Sie auf eines der folgenden Themen, um Informationen zu den Eigenschaften zu erhalten, die Sie im [!INCLUDE[ssIS](../../includes/ssis-md.md)] -Designer festlegen können:  
  
-   [Editor für den Task Aufträge übertragen &#40;Seite Allgemein&#41;](../general-page-of-integration-services-designers-options.md)  
  
-   [Editor für den Task Aufträge übertragen &#40;Seite Aufträge&#41;](../transfer-jobs-task-editor-jobs-page.md)  
  
-   [Seite Ausdrücke](../expressions/expressions-page.md)  
  
 Klicken Sie auf folgendes Thema, um weitere Informationen zum programmgesteuerten Festlegen dieser Eigenschaften zu erhalten:  
  
-   <xref:Microsoft.SqlServer.Dts.Tasks.TransferJobsTask.TransferJobsTask>  
  
## <a name="related-tasks"></a>Related Tasks  
 Klicken Sie auf das folgende Thema, um weitere Informationen zum Festlegen dieser Eigenschaften im [!INCLUDE[ssIS](../../includes/ssis-md.md)] -Designer zu erhalten:  
  
-   [Festlegen der Eigenschaften eines Tasks oder Containers](../set-the-properties-of-a-task-or-container.md)  
  
## <a name="see-also"></a>Siehe auch  
 [Integration Services-Tasks](integration-services-tasks.md)   
 [Ablaufsteuerung](control-flow.md)  
  
  
