---
title: Schreiben des Auftragsstatus in das Windows-Anwendungsprotokoll | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- status information [SQL Server], jobs
- SQL Server Agent jobs, status
- writing job status to log
- jobs [SQL Server Agent], status
- logs [SQL Server], jobs
ms.assetid: 3b813702-8f61-40ec-bf3b-ce9deb7e68be
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: ec615911233227c15f43e55125adfd6166cb51e8
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "72783373"
---
# <a name="write-the-job-status-to-the-windows-application-log"></a>Write the Job Status to the Windows Application Log
  In diesem Thema wird beschrieben, [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] wie der [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] -Agent in so konfiguriert wird, dass der Auftragsstatus mithilfe [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]von [!INCLUDE[tsql](../../includes/tsql-md.md)], oder SQL Server Management Objects in das Windows-Anwendungs Ereignisprotokoll geschrieben wird.  
  
 Sie stellen sicher, dass Datenbankadministratoren wissen, wann Aufträge fertig gestellt sind und wie oft diese ausgeführt werden. Zu den typischen Auftragsantworten gehören folgende:  
  
-   Benachrichtigen des Operators per E-Mail, Pager oder **NET SEND** -Nachricht. Verwenden Sie eine dieser Auftragsantworten vor allem dann, wenn der Operator weitere Schritte ausführen muss. Wenn beispielsweise ein Sicherungsauftrag erfolgreich ausgeführt wurde, muss der Operator darüber informiert werden, um das Sicherungsband entfernen zu können und an einem sicheren Standort aufbewahren zu lassen.  
  
-   Schreiben einer Ereignismeldung in das Windows-Anwendungsprotokoll. Diese Art der Antwort können Sie nur bei fehlgeschlagenen Aufträgen verwenden.  
  
-   Automatisches Löschen des Auftrags. Verwenden Sie diese Auftragsantwort, wenn Sie sicher sind, dass Sie diesen Auftrag nicht erneut ausführen müssen.  
  
 **In diesem Thema**  
  
-   **Vorbereitungen:**  
  
     [Sicherheit](#Security)  
  
-   **So schreiben Sie den Auftragsstatus in das Windows-Anwendungsprotokoll mit:**  
  
     [SQL Server Management Studio](#SSMS)  
  
     [SQL Server Management Objects](#SMO)  
  
##  <a name="BeforeYouBegin"></a> Vorbereitungen  
  
###  <a name="Security"></a> Sicherheit  
 Ausführliche Informationen finden Sie unter [Implementieren der SQL Server-Agent-Sicherheit](implement-sql-server-agent-security.md).  
  
##  <a name="SSMS"></a> Verwenden von SQL Server Management Studio  
  
#### <a name="to-write-job-status-to-the-windows-application-log"></a>So schreiben Sie den Auftragsstatus in das Windows-Anwendungsprotokoll  
  
1.  Stellen Sie im **Objekt-Explorer** eine Verbindung mit einer Instanz von [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]her, und erweitern Sie dann diese Instanz.  
  
2.  Erweitern Sie **SQL Server-Agent**, erweitern Sie **Aufträge**, klicken Sie mit der rechten Maustaste auf den Auftrag, den Sie bearbeiten möchten, und klicken Sie dann auf **Eigenschaften**.  
  
3.  Wählen Sie die Seite **Benachrichtigungen** aus.  
  
4.  Aktivieren Sie **In Windows-Anwendungsereignisprotokoll schreiben**, und wählen Sie eine der folgenden Optionen aus:  
  
    -   Klicken Sie auf**Bei erfolgreicher Auftragsausführung**, um den Auftragsstatus zu protokollieren, wenn der Auftrag erfolgreich abgeschlossen wurde.  
  
    -   Klicken Sie auf**Bei Auftragsfehler**, um den Auftragsstatus zu protokollieren, wenn der Auftrag nicht erfolgreich abgeschlossen wurde.  
  
    -   Klicken Sie auf**Beim Abschluss des Auftrags** , um den Auftragsstatus unabhängig vom Abschlussstatus zu protokollieren.  
  
##  <a name="SMO"></a>Verwenden von SQL Server Management Objects  

### <a name="to-write-job-status-to-the-windows-application-log"></a>So schreiben Sie den Auftragsstatus in das Windows-Anwendungsprotokoll
  
 Rufen Sie die `EventLogLevel`-Eigenschaft der `Job`-Klasse in einer Programmiersprache Ihrer Wahl auf, z. B. Visual Basic, Visual C# oder PowerShell.  
  
 Im folgenden Codebeispiel wird der Auftrag so festgelegt, dass bei Abschluss der Auftragsausführung ein Betriebssystem-Ereignisprotokolleintrag generiert wird.  
  
```powershell
$srv = new-object Microsoft.SqlServer.Management.Smo.Server("(local)")  
$jb = new-object Microsoft.SqlServer.Management.Smo.Agent.Job($srv.JobServer, "Test Job")  
$jb.EventLogLevel = [Microsoft.SqlServer.Management.Smo.Agent.CompletionAction]::Always  
```  
