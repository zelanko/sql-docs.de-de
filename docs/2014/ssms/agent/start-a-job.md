---
title: Starten eines Auftrags | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- jobs [SQL Server Agent], starting
- SQL Server Agent jobs, starting
- starting jobs
ms.assetid: cec9f7f7-d0a7-4239-9dc5-a69c011ebaa0
author: stevestein
ms.author: sstein
ms.openlocfilehash: 4d5af895df518a915dacd953331b9139471933aa
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/18/2020
ms.locfileid: "85058667"
---
# <a name="start-a-job"></a>Starten eines Auftrags
  In diesem Thema wird beschrieben, wie ein- [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent-Auftrag in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] mithilfe von [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] , [!INCLUDE[tsql](../../includes/tsql-md.md)] oder SQL Server Management Objects gestartet wird.  
  
 Ein Auftrag ist eine festgelegte Reihe von Aktionen, die der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent ausführt. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent-Aufträge können auf einem lokalen oder mehreren Remoteservern ausgeführt werden.  
  
-   **Vorbereitungen:**  
  
     [Security](#Security)  
  
-   **So starten Sie einen Auftrag an mit**  
  
     [SQL Server Management Studio](#SSMS)  
  
     [Transact-SQL](#TSQL)  
  
     [SQL Server Management Objects](#SMO)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> Vorbereitungen  
  
###  <a name="security"></a><a name="Security"></a> Sicherheit  
 Ausführliche Informationen finden Sie unter [Implementieren der SQL Server-Agent-Sicherheit](implement-sql-server-agent-security.md).  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMS"></a> Verwenden von SQL Server Management Studio  
  
### <a name="to-start-a-job"></a>So starten Sie einen Auftrag  
  
1.  Stellen Sie im **Objekt-Explorer** eine Verbindung mit einer [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]-Instanz her, und erweitern Sie dann die Instanz.  
  
2.  Erweitern Sie **SQL Server-Agent** , und erweitern Sie dann **Aufträge**. Führen Sie, je nachdem, wie der Auftrag gestartet werden soll, eine der folgenden Aktionen aus:  
  
    -   Wenn Sie auf einem einzelnen Server oder einem Zielserver arbeiten oder einen lokalen Serverauftrag auf einem Masterserver ausführen, klicken Sie mit der rechten Maustaste auf den Auftrag, den Sie starten möchten, und klicken Sie dann auf **Auftrag starten**.  
  
    -   Wenn Sie mehrere Aufträge starten möchten, klicken Sie mit der rechten Maustaste auf **Auftragsaktivitätsmonitor**, und klicken Sie dann auf **Auftragsaktivitäten anzeigen**. Im Auftragsaktivitätsmonitor können Sie mehrere Aufträge auswählen. Klicken Sie dazu mit der rechten Maustaste auf die Auswahl, und klicken Sie auf **Aufträge starten**.  
  
    -   Wenn Sie auf einem Masterserver arbeiten und alle Zielserver den Auftrag gleichzeitig ausführen sollen, klicken Sie mit der rechten Maustaste auf den Auftrag, den Sie starten möchten, klicken Sie auf **Auftrag starten**und dann auf **Auf allen Zielservern starten**.  
  
    -   Wenn Sie auf einem Masterserver arbeiten und Zielserver für den Auftrag angeben möchten, klicken Sie mit der rechten Maustaste auf den Auftrag, den Sie starten möchten, klicken Sie auf **Auftrag starten**und dann auf **Auf angegebenen Zielservern starten**. Aktivieren Sie im Dialogfeld **Downloadanweisungen bereitstellen** das Kontrollkästchen **Diese Zielserver** , und wählen Sie dann alle Zielserver aus, auf denen dieser Auftrag ausgeführt werden soll.  
  
##  <a name="using-transact-sql"></a><a name="TSQL"></a> Verwenden von Transact-SQL  
  
### <a name="to-start-a-job"></a>So starten Sie einen Auftrag  
  
1.  Stellen Sie im **Objekt-Explorer** eine Verbindung mit einer [!INCLUDE[ssDE](../../includes/ssde-md.md)]-Instanz her.  
  
2.  Klicken Sie in der Standardleiste auf **Neue Abfrage**.  
  
3.  Kopieren Sie das folgende Beispiel, fügen Sie es in das Abfragefenster ein, und klicken Sie auf **Ausführen**.  
  
    ```sql
    -- starts a job named Weekly Sales Data Backup.    
    USE msdb ;  
    GO  
  
    EXEC dbo.sp_start_job N'Weekly Sales Data Backup' ;  
    GO  
    ```  
  
 Weitere Informationen finden Sie unter [sp_start_job &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-start-job-transact-sql).  
  
##  <a name="using-sql-server-management-objects"></a><a name="SMO"></a>Verwenden von SQL Server Management Objects  

### <a name="to-start-a-job"></a>So starten Sie einen Auftrag
  
 Rufen Sie die `Start`-Methode der `Job`-Klasse in einer Programmiersprache Ihrer Wahl auf, z. B. Visual Basic, Visual C# oder PowerShell. Weitere Informationen finden Sie unter [SQL Server Management Objects (SMO)](https://msdn.microsoft.com/library/ms162169.aspx).  
