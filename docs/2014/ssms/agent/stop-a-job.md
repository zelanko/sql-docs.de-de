---
title: Beenden eines Auftrags | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- jobs [SQL Server Agent], stopping
- SQL Server Agent jobs, stopping
- stopping jobs
ms.assetid: 4249328a-24d8-4284-9d1d-7d04ed90e3d7
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 2f2d7a8e7ae1e8e6972f98f50eb52a1b31a7ab70
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48057483"
---
# <a name="stop-a-job"></a>Stop a Job
  In diesem Thema wird das Beenden eines [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent-Auftrags beschrieben. Ein Auftrag ist eine festgelegte Reihe von Aktionen, die der SQL Server-Agent ausführt.  
  
-   **Vorbereitungen:**  ,  
  
     [Einschränkungen](#Restrictions)  
  
     [Security](#Security)  
  
-   **So halten Sie einen Auftrag an mit**  
  
     [SQL Server Management Studio](#SSMS)  
  
     [Transact-SQL](#TSQL)  
  
     [SQL Server Management Objects](#SMO)  
  
##  <a name="BeforeYouBegin"></a> Vorbereitungsmaßnahmen  
  
###  <a name="Restrictions"></a> Einschränkungen  
  
-   Wenn ein Auftrag aktuell einen Schritt des Typs **CmdExec** oder **PowerShell**ausführt, wird der ausgeführte Prozess (z. B. Programm.exe) vorzeitig beendet. Dies kann zu unvorhersehbarem Verhalten führen, so werden z.&nbsp;B. Dateien, die vom Prozess verwendet werden, geöffnet bleiben.  
  
-   Bei einem Multiserverauftrag wird eine STOP-Anweisung für den Auftrag an alle Zielserver des Auftrags gesendet.  
  
###  <a name="Security"></a> Sicherheit  
 Ausführliche Informationen finden Sie unter [Implement SQL Server Agent Security](implement-sql-server-agent-security.md).  
  
##  <a name="SSMS"></a> Verwenden von SQL Server Management Studio  
  
#### <a name="to-stop-a-job"></a>So beenden Sie einen Auftrag  
  
1.  Stellen Sie im **Objekt-Explorer** eine Verbindung mit einer Instanz von [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]her, und erweitern Sie dann diese Instanz.  
  
2.  Erweitern Sie **SQL Server-Agent**, erweitern Sie **Aufträge**, klicken Sie mit der rechten Maustaste auf den zu beendenden Auftrag, und klicken Sie dann auf **Auftrag beenden**.  
  
3.  Wenn Sie mehrere Aufträge beenden möchten, klicken Sie mit der rechten Maustaste auf **Auftragsaktivitätsmonitor**, und klicken Sie dann auf **Auftragsaktivitäten anzeigen**. Wählen Sie im Auftragsaktivitätsmonitor die Aufträge aus, die beendet werden sollen, klicken Sie mit der rechten Maustaste auf Ihre Auswahl, und klicken Sie dann auf **Aufträge beenden**.  
  
##  <a name="TSQL"></a> Verwenden von Transact-SQL  
  
#### <a name="to-stop-a-job"></a>So beenden Sie einen Auftrag  
  
1.  Stellen Sie im **Objekt-Explorer**eine Verbindung mit einer [!INCLUDE[ssDE](../../includes/ssde-md.md)]-Instanz her.  
  
2.  Klicken Sie in der Standardleiste auf **Neue Abfrage**.  
  
3.  Kopieren Sie das folgende Beispiel, fügen Sie es in das Abfragefenster ein, und klicken Sie auf **Ausführen**.  
  
    ```  
    -- stops a job named Weekly Sales Data Backup  
    USE msdb ;  
    GO  
  
    EXEC dbo.sp_stop_job  
        N'Weekly Sales Data Backup' ;  
    GO  
    ```  
  
 Weitere Informationen finden Sie unter [Sp_stop_job &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-stop-job-transact-sql).  
  
##  <a name="SMO"></a> Verwendung von SQL Server Management Objects  
 **So beenden Sie einen Auftrag**  
  
 Rufen Sie die `Stop`-Methode der `Job`-Klasse in einer Programmiersprache Ihrer Wahl auf, z. B. Visual Basic, Visual C# oder PowerShell. Weitere Informationen finden Sie unter [SQL Server Management Objects (SMO)](http://msdn.microsoft.com/library/ms162169.aspx).  
  
  
