---
title: Entfernen der Datenbankspiegelung (SQL Server) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-high-availability
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- database mirroring [SQL Server], removing
- removing database mirroring [SQL Server]
ms.assetid: bbc4d7f7-3bc7-40d6-a822-af195fe7f8c0
caps.latest.revision: 41
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 5770d8caf8db1c2969ec19b75293d6cb43c1e80c
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36050647"
---
# <a name="remove-database-mirroring-sql-server"></a>Entfernen der Datenbankspiegelung (SQL Server)
  In diesem Thema wird beschrieben, wie Sie eine Datenbankspiegelung aus einer Datenbank in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] mit [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] oder [!INCLUDE[tsql](../../includes/tsql-md.md)]entfernen.  Der Datenbankbesitzer kann eine Datenbank-Spiegelungssitzung jederzeit manuell beenden, indem er die Spiegelung von der Datenbank entfernt.  
  
 
  
##  <a name="BeforeYouBegin"></a> Vorbereitungsmaßnahmen  
  
###  <a name="Security"></a> Sicherheit  
  
####  <a name="Permissions"></a> Berechtigungen  
 Erfordert die ALTER-Berechtigung für die Datenbank.  
  
##  <a name="SSMSProcedure"></a> Verwenden von SQL Server Management Studio  
  
#### <a name="to-remove-database-mirroring"></a>So entfernen Sie die Datenbankspiegelung  
  
1.  Stellen Sie während einer Datenbank-Spiegelungssitzung eine Verbindung mit der Prinzipalserverinstanz her, und klicken Sie im Objekt-Explorer auf den Servernamen, um die Serverstruktur zu erweitern.  
  
2.  Erweitern Sie **Datenbanken**, und wählen Sie die Datenbank aus.  
  
3.  Klicken Sie mit der rechten Maustaste auf die Datenbank, wählen Sie **Tasks**aus, und klicken Sie dann auf **Spiegeln**. Dadurch wird die Seite **Spiegelung** im Dialogfeld **Datenbankeigenschaften** geöffnet.  
  
4.  Klicken Sie im Bereich **Seite auswählen** auf **Spiegelung**.  
  
5.  Zum Entfernen der Spiegelung klicken Sie auf **Spiegeln entfernen**. Es wird eine Bestätigungsaufforderung angezeigt. Wenn Sie auf **Ja**klicken, wird die Sitzung beendet, und die Spiegelung wird aus der Datenbank entfernt.  
  
##  <a name="TsqlProcedure"></a> Verwenden von Transact-SQL  
 Zum Entfernen der Datenbankspiegelung verwenden Sie die **Datenbankeigenschaften**. Verwenden Sie die Seite **Spiegelung** im Dialogfeld **Datenbankeigenschaften** .  
  
#### <a name="to-remove-database-mirroring"></a>So entfernen Sie die Datenbankspiegelung  
  
1.  Stellen Sie für einen der Spiegelungspartner eine Verbindung mit dem [!INCLUDE[ssDE](../../includes/ssde-md.md)] her.  
  
2.  Klicken Sie in der Standardleiste auf **Neue Abfrage**.  
  
3.  Führen Sie die folgende [!INCLUDE[tsql](../../includes/tsql-md.md)] -Anweisung aus:  
  
    ```  
    ALTER DATABASE database_name SET PARTNER OFF  
    ```  
  
     wobei *Datenbankname* für die gespiegelte Datenbank steht, deren Sitzung Sie entfernen möchten.  
  
     Im folgenden Beispiel wird die Datenbankspiegelung aus der [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] -Beispieldatenbank entfernt.  
  
    ```  
    ALTER DATABASE AdventureWorks2012 SET PARTNER OFF;  
    ```  
  
##  <a name="FollowUp"></a> Nachverfolgung: Entfernen der Datenbankspiegelung  
  
> [!NOTE]  
>  Weitere Informationen zu den Auswirkungen des Entfernens der Datenbankspiegelung finden Sie unter [Entfernen der Datenbankspiegelung &#40;SQL Server&#41;](database-mirroring-sql-server.md).  
  
-   **Wenn Sie die Datenbankspiegelung erneut starten möchten**  
  
     Vor dem erneuten Starten der Spiegelung müssen alle Protokollsicherungen, die nach dem Entfernen der Spiegelung für die Prinzipaldatenbank erstellt wurden, auf die Spiegeldatenbank angewendet werden.  
  
-   **Wenn Sie die Datenbankspiegelung nicht erneut starten möchten**  
  
     Sie haben auch die Möglichkeit, die frühere Spiegeldatenbank wiederherzustellen. Auf der Serverinstanz, die den Spiegelserver darstellte, können Sie die folgende [!INCLUDE[tsql](../../includes/tsql-md.md)] -Anweisung ausführen:  
  
    ```  
    RESTORE DATABASE database_name WITH RECOVERY;  
    ```  
  
    > [!IMPORTANT]  
    >  Wenn Sie diese Datenbank wiederherstellen, sind zwei voneinander abweichende Datenbanken mit demselben Namen online. Deshalb müssen Sie sicherstellen, dass Clients nur auf eine der beiden zugreifen können (in der Regel die aktuellere Prinzipaldatenbank).  
  
##  <a name="RelatedTasks"></a> Verwandte Aufgaben  
  
-   [Anhalten oder Fortsetzen einer Datenbank-Spiegelungssitzung &#40;SQL Server&#41;](pause-or-resume-a-database-mirroring-session-sql-server.md)  
  
-   [Entfernen des Zeugen aus einer Datenbank-Spiegelungssitzung &#40;SQL Server&#41;](remove-the-witness-from-a-database-mirroring-session-sql-server.md)  
  
-   [Einrichten einer Datenbank-Spiegelungssitzung mithilfe der Windows-Authentifizierung &#40;SQL Server Management Studio&#41;](establish-database-mirroring-session-windows-authentication.md)  
  
-   [Einrichten einer Datenbank-Spiegelungssitzung mithilfe der Windows-Authentifizierung &#40;Transact-SQL&#41;](database-mirroring-establish-session-windows-authentication.md)  
  
-   [Beispiel: Einrichten der Datenbankspiegelung mithilfe von Zertifikaten &#40;SQL Server&#41;](example-setting-up-database-mirroring-using-certificates-transact-sql.md)  
  
## <a name="see-also"></a>Siehe auch  
 [Datenbankspiegelung &#40;SQL Server&#41;](database-mirroring-sql-server.md)   
 [Einrichten der Datenbankspiegelung &#40;SQL Server&#41;](setting-up-database-mirroring-sql-server.md)   
 [AlwaysOn-Verfügbarkeitsgruppen (SQLServer)](../availability-groups/windows/always-on-availability-groups-sql-server.md)  
  
  