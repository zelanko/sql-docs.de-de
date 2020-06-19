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
ms.openlocfilehash: a439b9d5076114d57d5b3bfd317e95911d52fcc3
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/18/2020
ms.locfileid: "85001616"
---
# <a name="write-the-job-status-to-the-windows-application-log"></a>Write the Job Status to the Windows Application Log
  In diesem Thema wird beschrieben, wie der-Agent in so konfiguriert wird, dass [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] der Auftragsstatus mithilfe von [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] , oder SQL Server Management Objects in das Windows-Anwendungs Ereignisprotokoll geschrieben wird [!INCLUDE[tsql](../../includes/tsql-md.md)] .  
  
 Sie stellen sicher, dass Datenbankadministratoren wissen, wann Aufträge fertig gestellt sind und wie oft diese ausgeführt werden. Zu den typischen Auftragsantworten gehören folgende:  
  
-   Benachrichtigen des Operators per E-Mail, Pager oder **NET SEND** -Nachricht. Verwenden Sie eine dieser Auftragsantworten vor allem dann, wenn der Operator weitere Schritte ausführen muss. Wenn beispielsweise ein Sicherungsauftrag erfolgreich ausgeführt wurde, muss der Operator darüber informiert werden, um das Sicherungsband entfernen zu können und an einem sicheren Standort aufbewahren zu lassen.  
  
-   Schreiben einer Ereignismeldung in das Windows-Anwendungsprotokoll. Diese Art der Antwort können Sie nur bei fehlgeschlagenen Aufträgen verwenden.  
  
-   Automatisches Löschen des Auftrags. Verwenden Sie diese Auftragsantwort, wenn Sie sicher sind, dass Sie diesen Auftrag nicht erneut ausführen müssen.  
  
 **In diesem Thema**  
  
-   **Vorbereitungen:**  
  
     [Security](#Security)  
  
-   **So schreiben Sie den Auftragsstatus in das Windows-Anwendungsprotokoll, und zwar mit**  
  
     [SQL Server Management Studio](#SSMS)  
  
     [SQL Server Management Objects](#SMO)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> Vorbereitungen  
  
###  <a name="security"></a><a name="Security"></a> Sicherheit  
 Ausführliche Informationen finden Sie unter [Implementieren der SQL Server-Agent-Sicherheit](implement-sql-server-agent-security.md).  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMS"></a> Verwenden von SQL Server Management Studio  
  
#### <a name="to-write-job-status-to-the-windows-application-log"></a>So schreiben Sie den Auftragsstatus in das Windows-Anwendungsprotokoll  
  
1.  Stellen Sie im **Objekt-Explorer** eine Verbindung mit einer [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]-Instanz her, und erweitern Sie dann die Instanz.  
  
2.  Erweitern Sie **SQL Server-Agent**, erweitern Sie **Aufträge**, klicken Sie mit der rechten Maustaste auf den Auftrag, den Sie bearbeiten möchten, und klicken Sie dann auf **Eigenschaften**.  
  
3.  Wählen Sie die Seite **Benachrichtigungen** aus.  
  
4.  Aktivieren Sie **In Windows-Anwendungsereignisprotokoll schreiben**, und wählen Sie eine der folgenden Optionen aus:  
  
    -   Klicken Sie auf**Bei erfolgreicher Auftragsausführung**, um den Auftragsstatus zu protokollieren, wenn der Auftrag erfolgreich abgeschlossen wurde.  
  
    -   Klicken Sie auf**Bei Auftragsfehler**, um den Auftragsstatus zu protokollieren, wenn der Auftrag nicht erfolgreich abgeschlossen wurde.  
  
    -   Klicken Sie auf**Beim Abschluss des Auftrags** , um den Auftragsstatus unabhängig vom Abschlussstatus zu protokollieren.  
  
##  <a name="using-sql-server-management-objects"></a><a name="SMO"></a>Verwenden von SQL Server Management Objects  

### <a name="to-write-job-status-to-the-windows-application-log"></a>So schreiben Sie den Auftragsstatus in das Windows-Anwendungsprotokoll
  
 Rufen Sie die `EventLogLevel`-Eigenschaft der `Job`-Klasse in einer Programmiersprache Ihrer Wahl auf, z. B. Visual Basic, Visual C# oder PowerShell.  
  
 Im folgenden Codebeispiel wird der Auftrag so festgelegt, dass bei Abschluss der Auftragsausführung ein Betriebssystem-Ereignisprotokolleintrag generiert wird.  
  
```powershell
$srv = new-object Microsoft.SqlServer.Management.Smo.Server("(local)")  
$jb = new-object Microsoft.SqlServer.Management.Smo.Agent.Job($srv.JobServer, "Test Job")  
$jb.EventLogLevel = [Microsoft.SqlServer.Management.Smo.Agent.CompletionAction]::Always  
```  
