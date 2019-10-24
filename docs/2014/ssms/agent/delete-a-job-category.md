---
title: Löschen einer Auftragskategorie | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- SQL Server Agent jobs, categories
- deleting job category
- jobs [SQL Server Agent], categories
- categories [SQL Server Agent jobs]
- removing job category
ms.assetid: 47a7640b-20b3-4639-ab37-b6fc73575e6c
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 9bb392991afbb3707fafdb18a28cc3de53f97c78
ms.sourcegitcommit: a165052c789a327a3a7202872669ce039bd9e495
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/22/2019
ms.locfileid: "72783203"
---
# <a name="delete-a-job-category"></a>Löschen einer Auftragskategorie
  In diesem Thema wird beschrieben, wie Sie eine [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent-Auftragskategorie in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] mithilfe von [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../includes/tsql-md.md)] oder SQL Server Management Objects löschen können.  
  
 Auftragskategorien helfen Ihnen dabei, Ihre Aufträge zum einfachen Filtern und Gruppieren zu organisieren. Sie können z. B. alle Aufträge für die Datenbanksicherung in der Datenbankwartungskategorie organisieren.  

##  <a name="BeforeYouBegin"></a> Vorbereitungsmaßnahmen  
  
###  <a name="Restrictions"></a> Einschränkungen  
 Wenn Sie eine benutzerdefinierte Auftragskategorie löschen, werden sie von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] aufgefordert, die Aufträge neu zuzuweisen, die in einer anderen Auftragskategorie zugewiesen wurden. Sie können nur benutzerdefinierte Auftragskategorien löschen.  
  
###  <a name="Security"></a> Security  
 Ausführliche Informationen finden Sie unter [Implementieren der SQL Server-Agent-Sicherheit](implement-sql-server-agent-security.md).  

##  <a name="SSMS"></a> Verwenden von SQL Server Management Studio  
  
### <a name="to-delete-a-job-category"></a>So löschen Sie eine Auftragskategorie  
  
1.  Klicken Sie im **Objekt-Explorer**auf das Pluszeichen, um den Server zu erweitern, auf dem Sie eine Auftragskategorie löschen möchten.  
  
2.  Klicken Sie auf das Pluszeichen, um **SQL Server-Agent**zu erweitern.  
  
3.  Klicken Sie mit der rechten Maustaste auf den Ordner **Aufträge** , und wählen Sie **Auftragskategorien verwalten**aus.  
  
4.  Klicken Sie im _server_name_-Dialogfeld **Auftragskategorien verwalten** auf die zu löschende Auftragskategorie.  
  
5.  Klicken Sie auf **Löschen**.  
  
6.  Klicken Sie im Dialogfeld **Auftragskategorien** auf **Ja**.  
  
7.  Schließen Sie das Dialogfeld **Auftragskategorien verwalten -** _Servername_ .  
  
##  <a name="TSQL"></a> Verwenden von Transact-SQL  
  
### <a name="to-delete-a-job-category"></a>So löschen Sie eine Auftragskategorie  
  
1.  Stellen Sie im **Objekt-Explorer** eine Verbindung mit einer [!INCLUDE[ssDE](../../includes/ssde-md.md)]-Instanz her.  
  
2.  Klicken Sie in der Standardleiste auf **Neue Abfrage**.  
  
3.  Kopieren Sie das folgende Beispiel, fügen Sie es in das Abfragefenster ein, und klicken Sie auf **Ausführen**.  
  
    ```sql
    -- deletes the job category named AdminJobs.  
    USE msdb ;  
    GO   
    EXEC dbo.sp_delete_category  
        @name = N'AdminJobs',  
        @class = N'JOB' ;  
    GO  
    ```  
  
 Weitere Informationen finden Sie unter [sp_delete_category &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-delete-category-transact-sql).  

  
##  <a name="SMO"></a>Verwenden von SQL Server Management Objects  

### <a name="to-delete-a-job-category"></a>So löschen Sie eine Auftragskategorie
  
 Rufen Sie die `JobCategory`-Klasse in einer Programmiersprache Ihrer Wahl auf, z. B. Visual Basic, Visual C# oder PowerShell.  
