---
title: Löschen des Auftragsverlaufsprotokolls | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- jobs [SQL Server Agent], history
- clearing job history log
- logs [SQL Server], jobs
- SQL Server Agent jobs, history
- historical information [SQL Server], jobs
ms.assetid: 34b9398a-c409-4040-8ea1-0deceb18f961
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 5c9bc55a6a5af15d6d21c4d3e7d74e2dc8296e84
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "68211489"
---
# <a name="clear-the-job-history-log"></a>Löschen des Auftragsverlaufsprotokolls
  In diesem Thema wird beschrieben, wie der Inhalt des [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent-Auftragsverlaufprotokolls in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] mithilfe von [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../includes/tsql-md.md)], oder SQL Server Management Objects gelöscht werden kann.  
  
 **In diesem Thema**  
  
-   **Vorbereitungen:**  
  
     [Sicherheit](#Security)  
  
-   **So löschen Sie das Auftragsverlaufsprotokoll mit**  
  
     [SQL Server Management Studio](#SSMS)  
  
     [Transact-SQL](#TSQL)  
  
     [SQL Server Management Objects](#SMO)  
  
##  <a name="BeforeYouBegin"></a> Vorbereitungen  
  
###  <a name="Security"></a> Sicherheit  
 Ausführliche Informationen finden Sie unter [Implementieren der SQL Server-Agent-Sicherheit](implement-sql-server-agent-security.md).  
  
##  <a name="SSMS"></a> Verwendung von SQL Server Management Studio  
  
#### <a name="to-clear-the-job-history-log"></a>So löschen Sie das Auftragsverlaufsprotokoll  
  
1.  Stellen Sie im **Objekt-Explorer** eine Verbindung mit einer Instanz von [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]her, und erweitern Sie dann diese Instanz.  
  
2.  Erweitern Sie **SQL Server-Agent**, und klicken Sie auf **Aufträge**.  
  
3.  Klicken Sie mit der rechten Maustaste auf einen Auftrag, und klicken Sie dann auf **Verlauf anzeigen**.  
  
4.  Wählen Sie im **Protokolldatei-Viewer**den Auftrag aus, dessen Verlauf gelöscht werden soll, und führen Sie dann einen der folgenden Schritte aus:  
  
    -   Klicken Sie auf **Löschen**, und klicken Sie dann im Dialogfeld **Verlauf löschen** auf **Gesamten Verlauf löschen** . Sie können wahlweise den gesamten Auftragsverlauf löschen oder auch nur den Verlauf, der vor einem bestimmten Datum angefallen ist. Soll der gesamte Auftragsverlauf gelöscht werden, klicken Sie auf **Gesamten Verlauf löschen**. Um nur ältere Einträge im Auftragsverlauf zu löschen, klicken Sie auf **Verlauf löschen vor**, und geben Sie das gewünschte Datum an.  
  
    -   Klicken Sie auf **Auftragsstatus** , wenn Sie das Verlaufsprotokoll eines Multiserverauftrags löschen möchten. Klicken Sie auf **Auftrag**und auf einen Auftragsnamen, und klicken Sie dann auf **Remoteauftragsverlauf anzeigen**.  
  
5.  Klicken Sie auf **Löschen**.  
  
##  <a name="TSQL"></a> Verwenden von Transact-SQL  
  
#### <a name="to-clear-the-job-history-log"></a>So löschen Sie das Auftragsverlaufsprotokoll  
  
1.  Stellen Sie im **Objekt-Explorer** eine Verbindung mit einer [!INCLUDE[ssDE](../../includes/ssde-md.md)]-Instanz her.  
  
2.  Klicken Sie in der Standardleiste auf **Neue Abfrage**.  
  
3.  Kopieren Sie das folgende Beispiel, fügen Sie es in das Abfragefenster ein, und klicken Sie auf **Ausführen**.  
  
    ```  
    -- example removes the history for a job named NightlyBackups.  
    USE msdb ;  
    GO  
  
    EXEC dbo.sp_purge_jobhistory  
        @job_name = N'NightlyBackups' ;  
    GO  
    ```  
  
##  <a name="SMO"></a> Verwendung von SQL Server Management Objects  
 **So löschen Sie das Auftragsverlaufsprotokoll**  
  
 Verwenden Sie die `PurgeJobHistory`-Methode der `JobServer`-Klasse in einer Programmiersprache Ihrer Wahl, z. B. Visual Basic, Visual C# oder PowerShell. Weitere Informationen finden Sie unter [SQL Server Management Objects (SMO)](https://msdn.microsoft.com/library/ms162169.aspx).  
  
  
