---
title: Sichern und Wiederherstellen von Systemdatenbanken (SQL Server) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
helpviewer_keywords:
- system databases [SQL Server], backing up and restoring
- restoring system databases [SQL Server]
- backing up [SQL Server], system databases
- database backups [SQL Server], system databases
- servers [SQL Server], backup
ms.assetid: aef0c4fa-ba67-413d-9359-1a67682fdaab
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 0259f14bb814fd4157af95e4ce92f462d1fab68a
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "62877267"
---
# <a name="back-up-and-restore-of-system-databases-sql-server"></a>Sichern und Wiederherstellen von Systemdatenbanken (SQL Server)
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] verwendet eine Reihe von Datenbanken auf Systemebene – die*Systemdatenbanken*, die für den Betrieb einer Serverinstanz von entscheidender Bedeutung sind. Einige der Systemdatenbanken müssen nach jedem wichtigen Update gesichert werden. Zu den Systemdatenbanken, die immer gesichert werden müssen, zählen **msdb**, **master**und **model**. Wenn eine Datenbank die Replikation auf der Serverinstanz verwendet, ist eine **distribution** -Systemdatenbank vorhanden, die Sie ebenfalls sichern müssen. Mit Sicherungen dieser Systemdatenbanken können Sie das [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -System bei einem Systemfehler wiederherstellen, beispielsweise beim einem Ausfall einer Festplatte.  
  
 In der folgenden Tabelle werden alle Systemdatenbanken zusammengefasst.  
  
|Systemdatenbank|Description|Sicherungen erforderlich?|Wiederherstellungsmodell|Kommentare|  
|---------------------|-----------------|---------------------------|--------------------|--------------|  
|[master](../databases/master-database.md)|In dieser Datenbank werden alle Informationen auf Systemebene für ein S [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -System aufgezeichnet.|Ja|Einfach|Sichern Sie die **master** -Datenbank so oft wie für Ihre Unternehmensanforderungen erforderlich, um die Daten ausreichend zu schützen. Wir empfehlen einen regelmäßigen Sicherungszeitplan, den Sie durch eine zusätzliche Sicherung nach umfangreicheren Updates ergänzen können.|  
|[model](../databases/model-database.md)|Die Vorlage für alle Datenbanken, die für die Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]erstellt werden.|Ja|Vom Benutzer konfigurierbar<sup>1</sup>|Sichern Sie **model** nur, wenn dies für Ihre Unternehmensanforderungen erforderlich ist, beispielsweise unmittelbar nach dem Anpassen der entsprechenden Datenbankoptionen.<br /><br /> **Bewährte Methode:** Es wird empfohlen, dass Sie nach Bedarf ausschließlich vollständige Datenbanksicherungen von **model**erstellen. Da **model** klein ist und sich nur selten ändert, ist die Sicherung des Protokolls nicht notwendig.|  
|[msdb](../databases/msdb-database.md)|Die Datenbank, die vom [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent zum Planen von Warnungen und Aufträgen sowie und zum Aufzeichnen von Operatoren verwendet wird. **msdb** enthält außerdem Verlaufstabellen, z. B. zu Sicherung und Wiederherstellung.|Ja|Einfach (Standard)|Sichern Sie die **msdb** -Datenbank bei jeder Aktualisierung.|  
|[Resource](../databases/resource-database.md) (RDB)|Eine schreibgeschützte Datenbank mit Kopien aller Systemobjekte, die mitgeliefert werden mit [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|Nein|-|Die **Resource** -Datenbank befindet sich in der Datei mssqlsystemresource.mdf, die ausschließlich Code enthält. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] kann die **Resource** -Datenbank daher nicht sichern.<br /><br /> Hinweis: Sie können eine dateibasierte oder eine datenträgerbasierte Sicherung der Datei mssqlsystemresource.mdf ausführen, indem Sie die Datei behandeln, als handele es sich um eine Binärdatei (.exe)-Datei, statt als Datenbankdatei. Sie können diese Sicherungen allerdings nicht mit einer [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Wiederherstellung wiederherstellen. Die Wiederherstellung einer Sicherungskopie von mssqlsystemresource.mdf kann nur manuell erfolgen. Achten Sie darauf, die aktuelle **Resource** -Datenbank nicht durch eine veraltete oder potenziell unsichere Version zu überschreiben.|  
|[tempdb](../databases/tempdb-database.md)|Ein Arbeitsbereich zum Speichern temporärer Resultsets oder Zwischenresultsets. Diese Datenbank wird jedes Mal neu erstellt, wenn eine Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] gestartet wird. Wenn die Serverinstanz heruntergefahren wird, werden alle in **tempdb** enthaltenen Daten dauerhaft gelöscht.|Nein|Einfach|Die **tempdb** -Systemdatenbank kann nicht gesichert werden.|  
|[Verteilung konfigurieren](../replication/configure-distribution.md)|Diese Datenbank ist nur vorhanden, wenn der Server als Replikationsverteiler konfiguriert wurde. In dieser Datenbank werden Metadaten und Verlaufsdaten für alle Replikationstypen sowie Transaktionen für die Transaktionsreplikation gespeichert.|Ja|Einfach|Informationen, wann die **distribution** -Datenbank gesichert werden sollte, finden Sie unter [Sichern und Wiederherstellen von replizierten Datenbanken](../replication/administration/back-up-and-restore-replicated-databases.md).|  
  
 <sup>1</sup> aktuellen Wiederherstellungsmodell des Modells finden Sie unter [anzeigen oder Ändern des Wiederherstellungsmodells einer Datenbank &#40;SQL Server&#41; ](view-or-change-the-recovery-model-of-a-database-sql-server.md) oder [sys.databases &#40;Transact-SQL&#41; ](/sql/relational-databases/system-catalog-views/sys-databases-transact-sql).  
  
## <a name="limitations-on-restoring-system-databases"></a>Einschränkungen beim Wiederherstellen von Systemdatenbanken  
  
-   Systemdatenbanken können nur aus Sicherungen wiederhergestellt werden, die für die derzeit von der Serverinstanz aufgeführte Version von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] erstellt wurden. Um beispielsweise eine Systemdatenbank auf einer Serverinstanz wiederherstellen, die ausgeführt wird, auf [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] SP1.  
  
-   Die Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] muss ausgeführt werden, um eine Datenbank wiederherstellen zu können. Zum Starten einer Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] muss der Zugriff auf die **master** -Datenbank möglich sein, und die Datenbank muss zumindest teilweise verwendet werden können. Wenn **master** nicht mehr verwendet werden kann, gibt es mehrere Methoden, um sie in einen verwendbaren Zustand zurückzuversetzen:  
  
    -   Wiederherstellen der **master** -Datenbank von einer aktuellen Datenbanksicherung.  
  
         Wenn Sie die Serverinstanz starten können, sollten Sie in der Lage sein, **master** aus einer vollständigen Datenbanksicherung wiederherzustellen.  
  
    -   Vollständige Neuerstellung der **master** -Datenbank.  
  
         Falls ernsthafte Schäden an der **master** -Datenbank das Starten von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]verhindern, müssen Sie die **master**-Datenbank neu erstellen. Weitere Informationen finden Sie unter [Neuerstellen von Systemdatenbanken](../databases/system-databases.md).  
  
        > [!IMPORTANT]  
        >  Beim Neuerstellen der **master** -Datenbank werden alle Systemdatenbanken neu erstellt.  
  
-   Probleme beim Wiederherstellen der Modelldatenbank können es in einigen Fällen erforderlich machen, dass die Systemdatenbanken neu erstellt oder die MDF- und LDF-Dateien für die Modelldatenbank ersetzt werden. Weitere Informationen finden Sie unter [Neuerstellen von Systemdatenbanken](../databases/system-databases.md).  
  
##  <a name="RelatedTasks"></a> Verwandte Aufgaben  
  
-   [Erstellen einer vollständigen Datenbanksicherung &#40;SQL Server&#41;](create-a-full-database-backup-sql-server.md)  
  
-   [Vollständige Datenbankwiederherstellungen &#40;einfaches Wiederherstellungsmodell&#41;](complete-database-restores-simple-recovery-model.md)  
  
-   [Wiederherstellen der master-Datenbank &#40;Transact-SQL&#41;](restore-the-master-database-transact-sql.md)  
  
-   [Anzeigen oder Ändern des Wiederherstellungsmodells einer Datenbank &#40;SQL Server&#41;](view-or-change-the-recovery-model-of-a-database-sql-server.md)  
  
-   [Verschieben von Systemdatenbanken](../databases/move-system-databases.md)  
  
## <a name="see-also"></a>Siehe auch  
 [Verteilungsdatenbank](../../relational-databases/replication/distribution-database.md)   
 [master-Datenbank](../databases/master-database.md)   
 [msdb-Datenbank](../databases/msdb-database.md)   
 [model-Datenbank](../databases/model-database.md)   
 [Ressourcendatenbank](../databases/resource-database.md)   
 [tempdb-Datenbank](../databases/tempdb-database.md)  
  
  
