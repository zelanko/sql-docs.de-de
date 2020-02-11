---
title: Aufträge des SQL Server-Agents für Pakete | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- jobs [Integration Services]
- automatic package execution
- scheduling packages [Integration Services]
- SQL Server Agent [Integration Services]
ms.assetid: ecf7a5f9-b8a7-47f1-9ac0-bac07cb89e31
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 7a4b9cd5eaad7b51f7cc3d2a0c73bea3f23fd542
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "62767172"
---
# <a name="sql-server-agent-jobs-for-packages"></a>Aufträge des SQL Server-Agents für Pakete
  Sie können die Ausführung von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] -Paketen automatisieren und planen, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] indem Sie den-Agent verwenden. Sie können Pakete planen, die auf dem [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] -Server bereitgestellt und in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], dem [!INCLUDE[ssIS](../../includes/ssis-md.md)] -Paketspeicher und im Dateisystem gespeichert werden.  
  
## <a name="sections-in-this-topic"></a>Kapitel in diesem Thema  
 Dieses Thema enthält folgende Abschnitte:  
  
-   [Planen von Aufträgen in SQL Server-Agent](#jobs)  
  
-   [Planen von Integration Services Paketen](#packages)  
  
-   [Problembehandlung bei geplanten Paketen](#trouble)  
  
##  <a name="jobs"></a>Planen von Aufträgen in SQL Server-Agent  
 
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent ist ein Dienst, der von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] installiert wird und mit dem Sie Aufgaben durch Ausführen von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent-Aufträgen automatisieren und planen können. Der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent-Dienst muss ausgeführt werden, um die automatische Ausführung von Aufträgen zu ermöglichen. Weitere Informationen finden Sie unter [Configure SQL Server Agent](../../ssms/agent/configure-sql-server-agent.md).  
  
 Der Knoten **SQL Server-Agent** wird im Objekt-Explorer in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] angezeigt, wenn Sie eine Verbindung mit einer Instanz von [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]herstellen.  
  
 Erstellen Sie einen Auftrag im Dialogfeld **Neuer Auftrag** , um eine sich wiederholende Aufgabe zu automatisieren. Weitere Informationen finden Sie unter [Implementieren von Aufträgen](../../ssms/agent/implement-jobs.md).  
  
 Nachdem Sie den Auftrag erstellt haben, müssen Sie mindestens einen Schritt hinzufügen. Ein Auftrag kann mehrere Schritte enthalten, und in jedem Schritt kann eine andere Aufgabe ausgeführt werden. Weitere Informationen finden Sie unter [Manage Job Steps](../../ssms/agent/manage-job-steps.md).  
  
 Nachdem Sie den Auftrag und die Auftragsschritte erstellt haben, können Sie einen Zeitplan zur Ausführung des Auftrags erstellen. Sie können jedoch auch einen ungeplanten Auftrag erstellen und manuell ausführen. Weitere Informationen finden Sie unter [Anlegen und Zuweisen von Zeitplänen zu Aufträgen](../../ssms/agent/create-and-attach-schedules-to-jobs.md).  
  
 Sie können den Auftrag durch Benachrichtigungsoptionen erweitern, z. B. indem Sie einen Operator zum Senden einer E-Mail-Nachricht beim Abschluss des Auftrags festlegen oder Warnungen hinzufügen. Weitere Informationen finden Sie unter [Warnungen](../../ssms/agent/alerts.md).  
  
##  <a name="packages"></a>Planen von Integration Services Paketen  
 Nachdem Sie einen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent-Auftrag erstellt haben, um [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] -Pakete zu planen, müssen Sie mindestens einen Schritt hinzufügen und den Typ des Schrittes als **SQL Server Integration Services-Paket**definieren. Ein Auftrag kann mehrere Schritte enthalten, und in jedem Schritt kann ein anderes Paket ausgeführt werden.  
  
 Das Ausführen eines [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] -Pakets mit einem Auftragsschritt entspricht dem Ausführen eines Pakets mit den Hilfsprogrammen **dtexec** (dtexec.exe) und **DTExecUI** (dtexecui.exe). Anstatt die Laufzeitoptionen für ein Paket jedoch über Befehlszeilenoptionen oder das Dialogfeld **Paketausführungs-Hilfsprogramm** festzulegen, geschieht dies hier mit dem Dialogfeld **Neuer Auftragsschritt** . Weitere Informationen zu den Optionen zum Ausführen eines Pakets finden Sie unter [dtexec Utility](dtexec-utility.md).  
  
 Weitere Informationen finden Sie unter [Planen eines Pakets mit dem SQL Server-Agent](../schedule-a-package-by-using-sql-server-agent.md).  
  
 In der MSDN Library auf der Videohomepage unter [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Vorgehensweise: Automatisieren der Paketausführung mit SQL Server-Agent (SQL Server-Video) [können Sie ein Video abspielen, in dem das Ausführen eines Pakets mit dem](https://go.microsoft.com/fwlink/?LinkId=141771)-Agent veranschaulicht wird.  
  
##  <a name="trouble"></a> Problembehandlung  
 Es kann vorkommen, dass ein Paket durch einen Auftragsschritt des [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agents nicht gestartet werden kann, obwohl das Paket in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] sowie über die Befehlszeile erfolgreich ausgeführt wird. Es gibt einige häufige Ursachen für dieses Problem und mehrere empfohlene Lösungen. Weitere Informationen finden Sie in den folgenden Ressourcen.  
  
-   [!INCLUDE[msCoName](../../includes/msconame-md.md)]Knowledge Base-Artikel: [ein SSIS-Paket wird nicht ausgeführt, wenn Sie das SSIS-Paket aus einem SQL Server-Agent-Auftrags Schritt abrufen](https://support.microsoft.com/kb/918760) .  
  
-   Video [Problembehandlung: Paket Ausführung mit SQL Server-Agent (SQL Server Video)](https://go.microsoft.com/fwlink/?LinkId=141772)in der MSDN Library.  
  
 Nachdem ein Paket durch einen Auftragsschritt des [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agents gestartet wurde, tritt bei der Paketausführung u. U. ein Fehler auf, oder das Paket wird zwar erfolgreich, aber mit unerwarteten Ergebnissen ausgeführt. Diese Probleme können mithilfe der folgenden Tools behandelt werden.  
  
-   Bei Paketen, die in der MSDB-Datenbank von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , im [!INCLUDE[ssIS](../../includes/ssis-md.md)] -Paketspeicher oder in einem Ordner auf dem lokalen Computer gespeichert sind, können Sie neben dem **Protokolldatei-Viewer** alle Protokolle und Debugdumpdateien verwenden, die während der Ausführung des Pakets generiert wurden.  
  
     **Führen Sie die folgenden Schritte aus, um den Protokolldatei-Viewer zu verwenden.**  
  
    1.  Klicken Sie im Objekt-Explorer mit der rechten Maustaste auf den [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent-Auftrag, und klicken Sie dann auf **Verlauf anzeigen**.  
  
    2.  Suchen Sie im Feld **Protokolldateizusammenfassung** die Auftragsausführung, für die in der Spalte **Meldung** die Meldung **Auftragsfehler** angezeigt wird.  
  
    3.  Erweitern Sie den Auftragsknoten, und klicken Sie auf den Auftragsschritt, um im Bereich unter dem Feld **Protokolldateizusammenfassung** Details zur Meldung anzuzeigen.  
  
-   Bei Paketen, die in der SSISDB-Datenbank gespeichert sind, können Sie ebenfalls den **Protokolldatei-Viewer** und alle Protokolle und Debugdumpdateien verwenden, die während der Ausführung des Pakets generiert wurden. Darüber hinaus können Sie die Berichte für den [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] -Server verwenden.  
  
     **Führen Sie die folgenden Schritte aus, um in den Berichten nach Informationen für die Ausführung eines Auftrags zugeordneten Pakets zu suchen.**  
  
    1.  Führen Sie die oben angegebenen Schritte aus, um die Details der Meldung zum Auftragsschritt einzublenden.  
  
    2.  Suchen Sie die Ausführungs-ID, die in der Meldung aufgeführt ist.  
  
    3.  Erweitern Sie den Knoten Integration Services-Katalog im Objekt-Explorer.  
  
    4.  Klicken Sie mit der rechten Maustaste auf SSISDB, zeigen Sie auf Berichte, dann auf Standardberichte, und klicken Sie auf Alle Ausführungen.  
  
    5.  Suchen Sie im Bericht **Alle Ausführungen** die Ausführungs-ID in der Spalte **ID** . Klicken Sie auf **Übersicht**, **Alle Meldungen**oder **Ausführungsleistung** , um Informationen zu dieser Paketausführung anzuzeigen.  
  
         Weitere Informationen zu den Berichten Übersicht, Alle Meldungen und Ausführungsleistung finden Sie unter [Reports for the Integration Services Server](../reports-for-the-integration-services-server.md).  
  
## <a name="external-resources"></a>Externe Ressourcen  
  
-   Knowledge Base-Artikel [Beim Aufrufen aus einem SQL Server-Agentauftragsschritt wird ein SSIS-Paket nicht ausgeführt](https://support.microsoft.com/kb/918760)auf der [!INCLUDE[msCoName](../../includes/msconame-md.md)] -Website  
  
-   Video [Problembehandlung: Paketausführung mit SQL Server-Agent (SQL Server-Video)](https://go.microsoft.com/fwlink/?LinkId=141772)in der MSDN Library  
  
-   Video [Vorgehensweise: Automatisieren der Paketausführung mit dem SQL Server-Agent (SQL Server-Video)](https://go.microsoft.com/fwlink/?LinkId=141771)in der MSDN Library  
  
-   Technischer Artikel [Überprüfen von Aufträgen des SQL Server-Agents mit Windows PowerShell](https://go.microsoft.com/fwlink/?LinkId=165675)auf mssqltips.com  
  
-   Technischer Artikel, [Auto alert for SQL Agent jobs when they are enabled or disabled](https://go.microsoft.com/fwlink/?LinkId=165676), auf mssqltips.com  
  
-   Blogeintrag [Konfigurieren von SQL-Agentaufträgen für das Schreiben in das Windows-Ereignisprotokoll](https://go.microsoft.com/fwlink/?LinkId=220745)auf mssqltips.com  
  
  
