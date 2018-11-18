---
title: Erstellen einer Auftragskategorie | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
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
monikerRange: = azuresqldb-mi-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: 2e0de2004ce2b3e9c91988bfc08fa0fea2074435
ms.sourcegitcommit: 50b60ea99551b688caf0aa2d897029b95e5c01f3
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/15/2018
ms.locfileid: "51701950"
---
# <a name="create-a-job-category"></a>Erstellen einer Auftragskategorie
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]

> [!IMPORTANT]  
> In einer [verwalteten Azure SQL-Datenbank-Instanz](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance) werden die meisten, aber nicht alle, SQL Server-Agent-Features unterstützt. Weitere Informationen finden Sie unter [T-SQL-Unterschiede zwischen einer verwalteten Azure SQL-Datenbank-Instanz und SQL Server](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance-transact-sql-information#sql-server-agent).

In diesem Thema wird beschrieben, wie Sie eine Auftragskategorie in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] mithilfe von [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../includes/tsql-md.md)] oder [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Management Objects erstellen können.  
  
[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent stellt integrierte Auftragskategorien bereit, denen Aufträge zugewiesen werden können. Sie können auch eine Auftragskategorie erstellen und diesen Aufträge zuweisen. Auftragskategorien helfen Ihnen dabei, Ihre Aufträge zum einfachen Filtern und Gruppieren zu organisieren. Sie können z. B. alle Aufträge für die Datenbanksicherung in der Datenbankwartungskategorie organisieren. Sie können zudem eigene Auftragskategorien erstellen.  
  
**In diesem Thema**  
  
-   **Vorbereitungen:**  
  
    [Einschränkungen](#Restrictions)  
  
    [Security](#Security)  
  
-   **So erstellen Sie eine Auftragskategorie mit**  
  
    [SQL Server Management Studio](#SSMS)  
  
    [Transact-SQL](#TSQL)  
  
    [SQL Server Management Objects](#SMO)  
  
## <a name="BeforeYouBegin"></a>Vorbereitungen  
  
### <a name="Restrictions"></a>Einschränkungen  
Multiserverkategorien sind nur auf einem Masterserver vorhanden. Auf einem Masterserver ist nur eine Standardauftragskategorie verfügbar: [**Nicht kategorisiert (Multiserver)**]. Beim Herunterladen eines Multiserverauftrags wird seine Kategorie auf dem Zielserver in **Aufträge vom MSX** geändert.  
  
### <a name="Security"></a>Sicherheit  
Ausführliche Informationen finden Sie unter [Implement SQL Server Agent Security](../../ssms/agent/implement-sql-server-agent-security.md).  
  
## <a name="SSMS"></a>Verwenden von SQL Server Management Studio  
  
#### <a name="to-create-a-job-category"></a>So erstellen Sie eine Auftragskategorie  
  
1.  Klicken Sie im **Objekt-Explorer** auf das Pluszeichen, um den Server zu erweitern, auf dem Sie eine Auftragskategorie erstellen möchten.  
  
2.  Klicken Sie auf das Pluszeichen, um **SQL Server-Agent**zu erweitern.  
  
3.  Klicken Sie mit der rechten Maustaste auf den Ordner **Aufträge** , und wählen Sie **Auftragskategorien verwalten**aus.  
  
4.  Klicken Sie im Dialogfeld **Auftragskategorien verwalten >***Servername*  auf **Hinzufügen**.  
  
5.  Geben Sie im neuen Dialogfeld **Name** einen Namen für die neue Auftragskategorie ein.  
  
6.  Aktivieren Sie das Kontrollkästchen **Alle Aufträge anzeigen** . Wählen Sie für die neue Kategorie mindestens einen Auftrag aus, indem Sie die Kontrollkästchen der entsprechenden Aufträge aktivieren.  
  
7.  Klicken Sie auf **OK**.  
  
8.  Klicken Sie im Dialogfeld **Auftragskategorien verwalten >***Servername* auf **Aktualisieren**, um sicherzustellen, dass die neue Auftragskategorie aktiv ist. Schließen Sie das Dialogfeld, wenn alles normal aussieht.  
  
Weitere Informationen zu diesen Dialogfeldern finden Sie unter [Auftragskategorien – Auftragskategorien verwalten](../../ssms/agent/job-categories-manage-job-categories.md) und [Eigenschaften für neue Auftragskategorie – Neue Auftragskategorie](../../ssms/agent/job-categories-properties-new-job-category.md).  
  
## <a name="TSQL"></a>Verwenden von Transact-SQL  
  
#### <a name="to-create-a-job-category"></a>So erstellen Sie eine Auftragskategorie  
  
1.  Stellen Sie im **Objekt-Explorer** eine Verbindung mit einer [!INCLUDE[ssDE](../../includes/ssde_md.md)]-Instanz her.  
  
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
  
Weitere Informationen finden Sie unter [sp_add_category (Transact-SQL)](https://msdn.microsoft.com/6cca32cd-d941-4378-aed6-a7c90cb7520a).  
  
## <a name="SMO"></a>Verwendung von SQL Server Management Objects  
**So erstellen Sie eine Auftragskategorie**  
  
Rufen Sie die **JobCategory** -Klasse auf, indem Sie eine von Ihnen ausgewählte Programmiersprache, z. B. Visual Basic, Visual C# oder PowerShell verwenden. Beispielcode hierzu finden Sie unter [Planen von automatischen, administrativen Tasks im SQL Server-Agent](../../relational-databases/server-management-objects-smo/tasks/scheduling-automatic-administrative-tasks-in-sql-server-agent.md).  
  
