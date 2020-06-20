---
title: Ändern eines Auftrags | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- jobs [SQL Server Agent], modifying
- modifying jobs
- SQL Server Agent jobs, modifying
ms.assetid: dd5e5f20-20c4-4ab9-a19a-db87577dcd43
author: stevestein
ms.author: sstein
ms.openlocfilehash: 0d25830ad119a1f5f344a4dcf318c35bee5f86ca
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/18/2020
ms.locfileid: "85062190"
---
# <a name="modify-a-job"></a>Ändern eines Auftrags
  In diesem Thema wird beschrieben, wie die Eigenschaften von- [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent-Aufträgen in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] mithilfe von [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] , [!INCLUDE[tsql](../../includes/tsql-md.md)] oder SQL Server Management Objects geändert werden.  
  
 **In diesem Thema**  
  
-   **Vorbereitungen:**  
  
     [Einschränkungen](#Restrictions)  
  
     [Security](#Security)  
  
-   **So ändern Sie einen Auftrag mit**  
  
     [SQL Server Management Studio](#SSMS)  
  
     [Transact-SQL](#TSQL)  
  
     [SQL Server Management Objects](#SMO)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> Vorbereitungen  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> Einschränkungen  
 Ein Masterauftrag für den [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent kann nicht gleichzeitig lokale Server und Remoteserver als Ziel haben.  
  
###  <a name="security"></a><a name="Security"></a> Sicherheit  
 Sie können nur Aufträge ändern, die in Ihrem Besitz sind, es sei denn, Sie sind ein Mitglied der festen Serverrolle **sysadmin** . Ausführliche Informationen finden Sie unter [Implementieren der SQL Server-Agent-Sicherheit](implement-sql-server-agent-security.md).  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMS"></a> Verwenden von SQL Server Management Studio  
  
#### <a name="to-modify-a-job"></a>So ändern Sie einen Auftrag  
  
1.  Stellen Sie im **Objekt-Explorer** eine Verbindung mit einer [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]-Instanz her, und erweitern Sie dann die Instanz.  
  
2.  Erweitern Sie **SQL Server-Agent**, erweitern Sie **Aufträge**, klicken Sie mit der rechten Maustaste auf den Auftrag, den Sie ändern möchten, und klicken Sie dann auf **Eigenschaften**.  
  
3.  Aktualisieren Sie im Dialogfeld **Auftragseigenschaften** mithilfe der entsprechenden Seiten die Eigenschaften, die Schritte, den Zeitplan, die Warnungen und die Benachrichtigungen des Auftrags.  
  
##  <a name="using-transact-sql"></a><a name="TSQL"></a> Verwenden von Transact-SQL  
  
#### <a name="to-modify-a-job"></a>So ändern Sie einen Auftrag  
  
1.  Stellen Sie im Objekt-Explorer eine Verbindung mit einer Instanz von Database Engine (Datenbankmodul) her, und erweitern Sie dann diese Instanz.  
  
2.  Klicken Sie auf der Symbolleiste auf **Neue Abfrage**.  
  
3.  Verwenden Sie im Abfragefenster die folgenden gespeicherten Systemprozeduren, um einen Auftrag zu ändern.  
  
    -   Führen Sie [sp_update_job &#40;Transact-SQL-&#41;](/sql/relational-databases/system-stored-procedures/sp-update-job-transact-sql) aus, um die Attribute eines Auftrags zu ändern.  
  
    -   Führen Sie [sp_update_schedule &#40;Transact-SQL-&#41;](/sql/relational-databases/system-stored-procedures/sp-update-schedule-transact-sql) aus, um die Zeit Plan Details für eine Auftrags Definition zu ändern.  
  
    -   Führen Sie [sp_add_jobstep &#40;Transact-SQL-&#41;](/sql/relational-databases/system-stored-procedures/sp-add-jobstep-transact-sql) aus, um neue Auftrags Schritte hinzuzufügen.  
  
    -   Führen Sie [sp_update_jobstep &#40;Transact-SQL-&#41;](/sql/relational-databases/system-stored-procedures/sp-update-jobstep-transact-sql) aus, um bereits vorhandene Auftrags Schritte zu ändern.  
  
    -   Führen Sie [sp_delete_jobstep &#40;Transact-SQL-&#41;](/sql/relational-databases/system-stored-procedures/sp-delete-jobstep-transact-sql) aus, um einen Auftrags Schritt aus einem Auftrag zu entfernen.  
  
    -   Weitere gespeicherte Prozeduren zum Ändern von SQL Server-Agent-Masteraufträgen:  
  
        -   Führen Sie [sp_delete_jobserver &#40;Transact-SQL-&#41;](/sql/relational-databases/system-stored-procedures/sp-delete-jobserver-transact-sql) aus, um einen Server zu löschen, der derzeit einem Auftrag zugeordnet ist.  
  
        -   Führen Sie [sp_add_jobserver &#40;Transact-SQL-&#41;](/sql/relational-databases/system-stored-procedures/sp-add-jobserver-transact-sql) aus, um einen Server mit dem aktuellen Auftrag zu verknüpfen.  
  
##  <a name="using-sql-server-management-objects"></a><a name="SMO"></a>Verwenden von SQL Server Management Objects  
 **So ändern Sie einen Auftrag**  
  
 Verwenden Sie die `Job`-Klasse in einer von Ihnen ausgewählten Programmiersprache, z. B. Visual Basic, Visual C# oder PowerShell. Weitere Informationen finden Sie unter [SQL Server Management Objects (SMO)](https://msdn.microsoft.com/library/ms162169.aspx).  
  
  
