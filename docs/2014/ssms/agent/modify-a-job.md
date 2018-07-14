---
title: Ändern eines Auftrags | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-cross-instance
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- jobs [SQL Server Agent], modifying
- modifying jobs
- SQL Server Agent jobs, modifying
ms.assetid: dd5e5f20-20c4-4ab9-a19a-db87577dcd43
caps.latest.revision: 31
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 72c4a103243707fa77216b62e9fb8fd3d067307b
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37268196"
---
# <a name="modify-a-job"></a>Ändern eines Auftrags
  In diesem Thema wird beschrieben, wie Sie die Eigenschaften der [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Auftragskategorien in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] mithilfe von [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../includes/tsql-md.md)]oder SQL Server Management Objects ändern können.  
  
 **In diesem Thema**  
  
-   **Vorbereitungen:**   
  
     [Einschränkungen](#Restrictions)  
  
     [Security](#Security)  
  
-   **So ändern Sie einen Auftrag mit**  
  
     [SQL Server Management Studio](#SSMS)  
  
     [Transact-SQL](#TSQL)  
  
     [SQL Server Management Objects](#SMO)  
  
##  <a name="BeforeYouBegin"></a> Vorbereitungsmaßnahmen  
  
###  <a name="Restrictions"></a> Einschränkungen  
 Ein Masterauftrag für den [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent kann nicht gleichzeitig lokale Server und Remoteserver als Ziel haben.  
  
###  <a name="Security"></a> Sicherheit  
 Sie können nur Aufträge ändern, die in Ihrem Besitz sind, es sei denn, Sie sind ein Mitglied der festen Serverrolle **sysadmin** . Ausführliche Informationen finden Sie unter [Implement SQL Server Agent Security](implement-sql-server-agent-security.md).  
  
##  <a name="SSMS"></a> Verwenden von SQL Server Management Studio  
  
#### <a name="to-modify-a-job"></a>So ändern Sie einen Auftrag  
  
1.  Stellen Sie im **Objekt-Explorer** eine Verbindung mit einer Instanz von [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]her, und erweitern Sie dann diese Instanz.  
  
2.  Erweitern Sie **SQL Server-Agent**, erweitern Sie **Aufträge**, klicken Sie mit der rechten Maustaste auf den Auftrag, den Sie ändern möchten, und klicken Sie dann auf **Eigenschaften**.  
  
3.  Aktualisieren Sie im Dialogfeld **Auftragseigenschaften** mithilfe der entsprechenden Seiten die Eigenschaften, die Schritte, den Zeitplan, die Warnungen und die Benachrichtigungen des Auftrags.  
  
##  <a name="TSQL"></a> Verwenden von Transact-SQL  
  
#### <a name="to-modify-a-job"></a>So ändern Sie einen Auftrag  
  
1.  Stellen Sie im Objekt-Explorer eine Verbindung mit einer Instanz von Database Engine (Datenbankmodul) her, und erweitern Sie dann diese Instanz.  
  
2.  Klicken Sie auf der Symbolleiste auf **Neue Abfrage**.  
  
3.  Verwenden Sie im Abfragefenster die folgenden gespeicherten Systemprozeduren, um einen Auftrag zu ändern.  
  
    -   Führen Sie [Sp_update_job &#40;Transact-SQL&#41; ](/sql/relational-databases/system-stored-procedures/sp-update-job-transact-sql) so ändern Sie die Attribute eines Auftrags.  
  
    -   Führen Sie [Sp_update_schedule &#40;Transact-SQL&#41; ](/sql/relational-databases/system-stored-procedures/sp-update-schedule-transact-sql) zum Ändern der Zeitplandetails für eine Auftragsdefinition.  
  
    -   Führen Sie [Sp_add_jobstep &#40;Transact-SQL&#41; ](/sql/relational-databases/system-stored-procedures/sp-add-jobstep-transact-sql) um neue Auftragsschritte hinzuzufügen.  
  
    -   Führen Sie [Sp_update_jobstep &#40;Transact-SQL&#41; ](/sql/relational-databases/system-stored-procedures/sp-update-jobstep-transact-sql) um vorhandene Auftragsschritte zu ändern.  
  
    -   Führen Sie [Sp_delete_jobstep &#40;Transact-SQL&#41; ](/sql/relational-databases/system-stored-procedures/sp-delete-jobstep-transact-sql) um einen Auftragsschritt aus einem Auftrag zu entfernen.  
  
    -   Weitere gespeicherte Prozeduren zum Ändern von SQL Server-Agent-Masteraufträgen:  
  
        -   Führen Sie [Sp_delete_jobserver &#40;Transact-SQL&#41; ](/sql/relational-databases/system-stored-procedures/sp-delete-jobserver-transact-sql) einen mit einem Auftrag momentan verknüpften Server zu löschen.  
  
        -   Führen Sie [Sp_add_jobserver &#40;Transact-SQL&#41; ](/sql/relational-databases/system-stored-procedures/sp-add-jobserver-transact-sql) um einen Server mit dem aktuellen Auftrag zu verknüpfen.  
  
##  <a name="SMO"></a> Verwendung von SQL Server Management Objects  
 **So ändern Sie einen Auftrag**  
  
 Verwenden der `Job` Klasse, indem Sie eine Programmiersprache, die Sie, wie z. B. Visual Basic, Visual c# oder PowerShell auswählen. Weitere Informationen finden Sie unter [SQL Server Management Objects (SMO)](http://msdn.microsoft.com/library/ms162169.aspx).  
  
  
