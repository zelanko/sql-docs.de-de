---
title: Erstellen einer Auftragskategorie | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- SQL Server Agent jobs, categories
- jobs [SQL Server Agent], categories
- categories [SQL Server Agent jobs]
ms.assetid: e24a6d38-d231-4f64-ab89-2d1ef6f5792c
caps.latest.revision: 29
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 7ceb4a9b28a75a0937a58e43329789064fe1d336
ms.sourcegitcommit: 8ae6e6618a7e9186aab3c6a37ea43776aa9a382b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/06/2018
ms.locfileid: "43814966"
---
# <a name="create-a-job-category"></a>Erstellen einer Auftragskategorie
  In diesem Thema wird beschrieben, wie Sie eine Auftragskategorie in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] mithilfe von [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../includes/tsql-md.md)] oder [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Management Objects erstellen können.  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent stellt integrierte Auftragskategorien bereit, denen Aufträge zugewiesen werden können. Sie können auch eine Auftragskategorie erstellen und diesen Aufträge zuweisen. Auftragskategorien helfen Ihnen dabei, Ihre Aufträge zum einfachen Filtern und Gruppieren zu organisieren. Sie können z. B. alle Aufträge für die Datenbanksicherung in der Datenbankwartungskategorie organisieren. Sie können zudem eigene Auftragskategorien erstellen.  
  
 
  
##  <a name="BeforeYouBegin"></a> Vorbereitungsmaßnahmen  
  
###  <a name="Restrictions"></a> Einschränkungen  
 Multiserverkategorien sind nur auf einem Masterserver vorhanden. Auf einem Masterserver ist nur eine Standardauftragskategorie verfügbar: [**Nicht kategorisiert (Multiserver)**]. Beim Herunterladen eines Multiserverauftrags wird seine Kategorie auf dem Zielserver in **Aufträge vom MSX** geändert.  
  
###  <a name="Security"></a> Sicherheit  
 Ausführliche Informationen finden Sie unter [Implement SQL Server Agent Security](implement-sql-server-agent-security.md).  
  

  
##  <a name="SSMS"></a> Verwenden von SQL Server Management Studio  
  
#### <a name="to-create-a-job-category"></a>So erstellen Sie eine Auftragskategorie  
  
1.  Klicken Sie im **Objekt-Explorer** auf das Pluszeichen, um den Server zu erweitern, auf dem Sie eine Auftragskategorie erstellen möchten.  
  
2.  Klicken Sie auf das Pluszeichen, um **SQL Server-Agent**zu erweitern.  
  
3.  Klicken Sie mit der rechten Maustaste auf den Ordner **Aufträge** , und wählen Sie **Auftragskategorien verwalten**aus.  
  
4.  Klicken Sie im Dialogfeld **Auftragskategorien verwalten >***Servername*  auf **Hinzufügen**.  
  
5.  Geben Sie im neuen Dialogfeld **Name** einen Namen für die neue Auftragskategorie ein.  
  
6.  Aktivieren Sie das Kontrollkästchen **Alle Aufträge anzeigen** . Wählen Sie für die neue Kategorie mindestens einen Auftrag aus, indem Sie die Kontrollkästchen der entsprechenden Aufträge aktivieren.  
  
7.  Klicken Sie auf **OK**.  
  
8.  Klicken Sie im Dialogfeld **Auftragskategorien verwalten >***Servername* auf **Aktualisieren**, um sicherzustellen, dass die neue Auftragskategorie aktiv ist. Schließen Sie das Dialogfeld, wenn alles normal aussieht.  
  
 Weitere Informationen zu diesen Dialogfeldern finden Sie unter [Auftragskategorien: Auftragskategorien verwalten](job-categories-manage-job-categories.md) und [Eigenschaften und eine neue Auftragskategorie](job-categories-properties-new-job-category.md).  
  
 
  
##  <a name="TSQL"></a> Verwenden von Transact-SQL  
  
#### <a name="to-create-a-job-category"></a>So erstellen Sie eine Auftragskategorie  
  
1.  Stellen Sie im **Objekt-Explorer**eine Verbindung mit einer [!INCLUDE[ssDE](../../includes/ssde-md.md)]-Instanz her.  
  
2.  Klicken Sie in der Standardleiste auf **Neue Abfrage**.  
  
3.  Kopieren Sie das folgende Beispiel, fügen Sie es in das Abfragefenster ein, und klicken Sie auf **Ausführen**.  
  
    ```  
    -- creates a local job category named AdminJobs   
    USE msdb ;  
    GO  
    EXEC dbo.sp_add_category  
        @class=N'JOB',  
        @type=N'LOCAL',  
        @name=N'AdminJobs' ;  
    GO  
    ```  
  
 Weitere Informationen finden Sie unter [Sp_add_category &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-add-category-transact-sql).  
  

  
##  <a name="SMO"></a> Verwendung von SQL Server Management Objects  
 **So erstellen Sie eine Auftragskategorie**  
  
 Rufen Sie die `JobCategory` Klasse, indem Sie eine Programmiersprache, die Sie, wie z. B. Visual Basic, Visual c# oder PowerShell auswählen. Beispielcode hierzu finden Sie unter [Planen von automatischen, administrativen Tasks im SQL Server-Agent](sql-server-agent.md).  
  
 
  
  
