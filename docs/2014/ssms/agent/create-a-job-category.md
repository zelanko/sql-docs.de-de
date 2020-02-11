---
title: Erstellen einer Auftragskategorie | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- SQL Server Agent jobs, categories
- jobs [SQL Server Agent], categories
- categories [SQL Server Agent jobs]
ms.assetid: e24a6d38-d231-4f64-ab89-2d1ef6f5792c
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 07b942ad64043f93f014a54246b42ef5375ade97
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "72798275"
---
# <a name="create-a-job-category"></a>Erstellen einer Auftragskategorie
  In diesem Thema wird beschrieben, wie Sie eine Auftragskategorie in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] mithilfe von [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../includes/tsql-md.md)] oder [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Management Objects erstellen können.  
  
 
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent stellt integrierte Auftragskategorien bereit, denen Aufträge zugewiesen werden können. Sie können auch eine Auftragskategorie erstellen und diesen Aufträge zuweisen. Auftragskategorien helfen Ihnen dabei, Ihre Aufträge zum einfachen Filtern und Gruppieren zu organisieren. Sie können z. B. alle Aufträge für die Datenbanksicherung in der Datenbankwartungskategorie organisieren. Sie können zudem eigene Auftragskategorien erstellen.  
  
 
  
##  <a name="BeforeYouBegin"></a> Vorbereitungen  
  
###  <a name="Restrictions"></a> Einschränkungen  
 Multiserverkategorien sind nur auf einem Masterserver vorhanden. Auf einem Masterserver ist nur eine Standardauftragskategorie verfügbar: [**Nicht kategorisiert (Multiserver)**]. Beim Herunterladen eines Multiserverauftrags wird seine Kategorie auf dem Zielserver in **Aufträge vom MSX** geändert.  
  
###  <a name="Security"></a> Sicherheit  
 Ausführliche Informationen finden Sie unter [Implementieren der SQL Server-Agent-Sicherheit](implement-sql-server-agent-security.md).  
  
##  <a name="SSMS"></a> Verwenden von SQL Server Management Studio  
  
#### <a name="to-create-a-job-category"></a>So erstellen Sie eine Auftragskategorie  
  
1.  Klicken Sie im **Objekt-Explorer**auf das Pluszeichen, um den Server zu erweitern, auf dem Sie eine Auftragskategorie erstellen möchten.  
  
2.  Klicken Sie auf das Pluszeichen, um **SQL Server-Agent**zu erweitern.  
  
3.  Klicken Sie mit der rechten Maustaste auf den Ordner **Aufträge** , und wählen Sie **Auftragskategorien verwalten**aus.  
  
4.  Klicken Sie im Dialogfeld **Auftrags Kategorien verwalten**_server_name_ auf **Hinzufügen**.  
  
5.  Geben Sie im neuen Dialogfeld **Name** einen Namen für die neue Auftragskategorie ein.  
  
6.  Aktivieren Sie das Kontrollkästchen **Alle Aufträge anzeigen** . Wählen Sie für die neue Kategorie mindestens einen Auftrag aus, indem Sie die Kontrollkästchen der entsprechenden Aufträge aktivieren.  
  
7.  Klicken Sie auf **OK**.  
  
8.  Klicken Sie im Dialogfeld **Auftrags Kategorien verwalten**_server_name_ auf **Aktualisieren** , um sicherzustellen, dass die neue Auftrags Kategorie aktiv ist. Schließen Sie das Dialogfeld, wenn alles normal aussieht.  
  
 Weitere Informationen zu diesen Dialogfeldern finden Sie unter [Auftrags Kategorien: Verwalten von Auftrags Kategorien](job-categories-manage-job-categories.md) und [Auftrags Kategorien Eigenschaften und neuer Auftrags Kategorie](job-categories-properties-new-job-category.md).  

##  <a name="TSQL"></a> Verwenden von Transact-SQL  
  
#### <a name="to-create-a-job-category"></a>So erstellen Sie eine Auftragskategorie  
  
1.  Stellen Sie im **Objekt-Explorer** eine Verbindung mit einer [!INCLUDE[ssDE](../../includes/ssde-md.md)]-Instanz her.  
  
2.  Klicken Sie in der Standardleiste auf **Neue Abfrage**.  
  
3.  Kopieren Sie das folgende Beispiel, fügen Sie es in das Abfragefenster ein, und klicken Sie auf **Ausführen**.  
  
    ```sql
    -- creates a local job category named AdminJobs   
    USE msdb ;  
    GO  
    EXEC dbo.sp_add_category  
        @class=N'JOB',  
        @type=N'LOCAL',  
        @name=N'AdminJobs' ;  
    GO  
    ```  
  
 Weitere Informationen finden Sie unter [sp_add_category &#40;Transact-SQL-&#41;](/sql/relational-databases/system-stored-procedures/sp-add-category-transact-sql).  

##  <a name="SMO"></a>Verwenden von SQL Server Management Objects  
 **So erstellen Sie eine Auftragskategorie**  
  
 Rufen Sie die `JobCategory`-Klasse in einer Programmiersprache Ihrer Wahl auf, z. B. Visual Basic, Visual C# oder PowerShell. Beispielcode hierzu finden Sie unter [Planen von automatischen, administrativen Tasks im SQL Server-Agent](sql-server-agent.md).  
