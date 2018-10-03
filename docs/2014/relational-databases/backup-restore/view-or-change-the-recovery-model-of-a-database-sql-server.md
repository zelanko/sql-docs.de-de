---
title: Anzeigen oder Ändern des Wiederherstellungsmodells einer Datenbank (SQL Server) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
helpviewer_keywords:
- database backups [SQL Server], recovery models
- recovery [SQL Server], recovery model
- backing up databases [SQL Server], recovery models
- recovery models [SQL Server], switching
- recovery models [SQL Server], viewing
- database restores [SQL Server], recovery models
- modifying database recovery models
ms.assetid: 94918d1d-7c10-4be7-bf9f-27e00b003a0f
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 5ef0cb341c0f37f6961eebb759f2a236510044f3
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48097490"
---
# <a name="view-or-change-the-recovery-model-of-a-database-sql-server"></a>Anzeigen oder Ändern des Wiederherstellungsmodells einer Datenbank (SQL Server)
  In diesem Thema wird die Vorgehensweise zum Anzeigen oder Ändern des Wiederherstellungsmodells einer Datenbank in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] mithilfe von [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] oder [!INCLUDE[tsql](../../includes/tsql-md.md)]beschrieben. Ein *Wiederherstellungsmodell* ist eine Datenbankeigenschaft, die steuert, wie Transaktionen protokolliert werden, ob das Transaktionsprotokoll gesichert werden muss (und kann) und welche Arten von Wiederherstellungsvorgängen verfügbar sind. Es stehen drei Wiederherstellungsmodelle zur Verfügung: einfach, vollständig und massenprotokolliert. Für eine Datenbank wird im Allgemeinen das vollständige oder das einfache Wiederherstellungsmodell verwendet. Eine Datenbank kann jederzeit auf ein anderes Wiederherstellungsmodell umgestellt werden. Die **model** -Datenbank legt das Standardwiederherstellungsmodell der neuen Datenbanken fest.  
  
 **In diesem Thema**  
  
-   **Vorbereitungen:**  
  
     [Empfehlungen](#Recommendations)  
  
     [Security](#Security)  
  
-   **Zum Anzeigen oder Ändern des Wiederherstellungsmodells einer Datenbank mit:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
-   **Empfehlungen zur Nachverfolgung:**  [Nach dem Ändern des Wiederherstellungsmodells](#FollowUp)  
  
-   [Verwandte Aufgaben](#RelatedTasks)  
  
##  <a name="BeforeYouBegin"></a> Vorbereitungsmaßnahmen  
  
###  <a name="Recommendations"></a> Empfehlungen  
  
-   Bevor Sie vom vollständigen oder massenprotokollierten Wiederherstellungsmodell umschalten, sichern Sie das Transaktionsprotokoll.  
  
-   Beim massenprotokollierten Modell ist keine Zeitpunktwiederherstellung möglich. Wenn Sie Transaktionen unter dem massenprotokollierten Wiederherstellungsmodell ausführen, für die u. U. eine Wiederherstellung des Transaktionsprotokolls erforderlich ist, besteht für diese Transaktionen die Gefahr eines Datenverlusts. Um die Wiederherstellbarkeit von Daten im Notfall zu maximieren, empfiehlt es sich, nur unter folgenden Bedingungen zum massenprotokollierten Wiederherstellungsmodell zu wechseln:  
  
    -   Benutzer sind in der Datenbank derzeit nicht zulässig.  
  
    -   Alle während der Massenverarbeitung vorgenommenen Änderungen sind wiederherstellbar, ohne dass dazu eine Protokollsicherung erstellt werden muss, z. B. durch erneute Ausführung der Massenprozesse.  
  
     Wenn Sie beide Bedingungen erfüllen, besteht während der Wiederherstellung eines Transaktionsprotokolls, das unter dem massenprotokollierten Wiederherstellungsmodell gesichert wurde, keine Gefahr eines Datenverlusts.  
  
> [!NOTE]  
>  Wenn Sie während eines Massenvorgangs auf das vollständige Wiederherstellungsmodell umstellen, sollten Sie beachten, dass sich die Protokollierung des Massenvorgangs von der minimalen Protokollierung in die vollständige Protokollierung ändert und umgekehrt.  
  
###  <a name="Security"></a> Sicherheit  
  
####  <a name="Permissions"></a> Berechtigungen  
 Erfordert die ALTER-Berechtigung für die Datenbank.  
  
##  <a name="SSMSProcedure"></a> Verwenden von SQL Server Management Studio  
  
#### <a name="to-view-or-change-the-recovery-model"></a>So zeigen Sie das Wiederherstellungsmodell an oder ändern es  
  
1.  Stellen Sie eine Verbindung mit der entsprechenden Instanz von [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]her, und klicken Sie danach im Objekt-Explorer auf den Servernamen, um die Serverstruktur zu erweitern.  
  
2.  Erweitern Sie **Datenbanken**, und wählen Sie je nach Datenbank eine Benutzerdatenbank aus, oder erweitern Sie **Systemdatenbanken** , und wählen Sie eine Systemdatenbank aus.  
  
3.  Klicken Sie mit der rechten Maustaste auf die Datenbank, und klicken Sie dann auf **Eigenschaften**. Das Dialogfeld **Datenbankeigenschaften** wird geöffnet.  
  
4.  Klicken Sie auf der Seite **Seite auswählen** auf **Optionen**.  
  
5.  Das aktuelle Wiederherstellungsmodell wird im Listenfeld **Wiederherstellungsmodell** angezeigt.  
  
6.  Sie können auch zum Wechseln des Wiederherstellungsmodells eine andere Modellliste auswählen. Die Auswahlmöglichkeiten sind **Vollständig**, **Massenprotokolliert**oder **Einfach**.  
  
7.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
##  <a name="TsqlProcedure"></a> Verwenden von Transact-SQL  
  
#### <a name="to-view-the-recovery-model"></a>So zeigen Sie das Wiederherstellungsmodell an  
  
1.  Stellen Sie eine Verbindung mit dem [!INCLUDE[ssDE](../../includes/ssde-md.md)]her.  
  
2.  Klicken Sie in der Standardleiste auf **Neue Abfrage**.  
  
3.  Kopieren Sie das folgende Beispiel, fügen Sie es in das Abfragefenster ein, und klicken Sie auf **Ausführen**. In diesem Beispiel wird gezeigt, wie die [sys.databases](/sql/relational-databases/system-catalog-views/sys-databases-transact-sql) -Katalogsicht abgefragt werden muss, um mehr über das Wiederherstellungsmodell der **model** -Datenbank zu erfahren.  
  
```tsql  
SELECT name, recovery_model_desc  
   FROM sys.databases  
      WHERE name = 'model' ;  
GO  
  
```  
  
#### <a name="to-change-the-recovery-model"></a>So ändern Sie das Wiederherstellungsmodell  
  
1.  Stellen Sie eine Verbindung mit dem [!INCLUDE[ssDE](../../includes/ssde-md.md)]her.  
  
2.  Klicken Sie in der Standardleiste auf **Neue Abfrage**.  
  
3.  Kopieren Sie das folgende Beispiel, fügen Sie es in das Abfragefenster ein, und klicken Sie auf **Ausführen**. In diesem Beispiel wird gezeigt, wie Sie das Wiederherstellungsmodell in der `model` -Datenbank in `FULL` mithilfe der `SET RECOVERY` -Option der [ALTER DATABASE](/sql/t-sql/statements/alter-database-transact-sql-set-options) -Anweisung ändern können.  
  
```tsql  
USE master ;  
ALTER DATABASE model SET RECOVERY FULL ;  
```  
  
##  <a name="FollowUp"></a> Empfehlungen zur nachverfolgung: Nach dem Ändern des Wiederherstellungsmodells  
  
-   **Nach dem Umschalten zwischen dem vollständigen und massenprotokollierten Wiederherstellungsmodell**  
  
    -   Wechseln Sie nach der Ausführung der Massenvorgänge sofort wieder zum vollständigen Wiederherstellungsmodus.  
  
    -   Sichern Sie das Protokoll erneut, nachdem Sie vom massenprotokollierten Wiederherstellungsmodell zurück zum vollständigen Wiederherstellungsmodell gewechselt sind.  
  
        > [!NOTE]  
        >  Ihre Sicherungsstrategie ändert sich nicht. Führen Sie weiterhin regelmäßige Datenbanksicherungen, Protokollsicherungen und differenzielle Sicherungen aus.  
  
-   **Nach dem Umschalten vom einfachen Wiederherstellungsmodell**  
  
    -   Erstellen Sie sofort nach der Umstellung auf das vollständige Wiederherstellungsmodell bzw. das massenprotokollierte Wiederherstellungsmodell eine vollständige oder eine differenzielle Datenbanksicherung, um die Protokollkette zu starten.  
  
        > [!NOTE]  
        >  Die Umstellung auf das vollständige oder das massenprotokollierte Wiederherstellungsmodell wird erst nach der ersten Datensicherung wirksam.  
  
    -   Planen Sie regelmäßige Protokollsicherungen, und aktualisieren Sie dementsprechend Ihren Wiederherstellungsplan.  
  
        > [!IMPORTANT]  
        >  Wenn Sie das Transaktionsprotokoll nicht oft genug sichern, kann das Protokoll so stark vergrößert werden, bis kein Speicherplatz mehr verfügbar ist.  
  
-   **Nach dem Umschalten zum einfachen Wiederherstellungsmodell**  
  
    -   Unterbrechen Sie alle geplanten Aufträge, um das Transaktionsprotokoll zu sichern.  
  
    -   Stellen Sie sicher, dass regelmäßige Datenbanksicherungen stattfinden. Datenbanksicherungen müssen regelmäßig durchgeführt werden, damit Ihre Daten geschützt sind und der inaktive Teil des Transaktionsprotokolls abgeschnitten werden kann.  
  
##  <a name="RelatedTasks"></a> Verwandte Aufgaben  
  
-   [Erstellen einer vollständigen Datenbanksicherung &#40;SQL Server&#41;](create-a-full-database-backup-sql-server.md)  
  
-   [Sichern eines Transaktionsprotokolls &#40;SQL Server&#41;](back-up-a-transaction-log-sql-server.md)  
  
-   [Erstellen eines Auftrags](../../ssms/agent/create-a-job.md)  
  
-   [Disable or Enable a Job](../../ssms/agent/disable-or-enable-a-job.md)  
  
##  <a name="RelatedContent"></a> Verwandte Inhalte  
  
-   [Datenbankwartungspläne](../maintenance-plans/maintenance-plans.md) (in der [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] -Onlinedokumentation)  
  
## <a name="see-also"></a>Siehe auch  
 [Wiederherstellungsmodelle &#40;SQL Server&#41;](recovery-models-sql-server.md)   
 [Das Transaktionsprotokoll &#40;SQL Server&#41;](../logs/the-transaction-log-sql-server.md)   
 [ALTER DATABASE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql)   
 [sys.databases &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-databases-transact-sql)   
 [Wiederherstellungsmodelle &#40;SQL Server&#41;](recovery-models-sql-server.md)  
  
  
