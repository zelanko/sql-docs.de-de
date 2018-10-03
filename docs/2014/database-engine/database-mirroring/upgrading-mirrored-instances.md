---
title: Minimieren der Ausfallzeit von gespiegelten Datenbanken beim Aktualisieren von Serverinstanzen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- upgrading SQL Server, rolling upgrade of mirrored databases
- database mirroring [SQL Server], upgrading system
- rolling upgrades [SQL Server]
ms.assetid: 0e73bd23-497d-42f1-9e81-8d5314bcd597
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: a0ac6ea9d3437e22a1493c9888ccb75e7996f1c5
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48219860"
---
# <a name="minimize-downtime-for-mirrored-databases-when-upgrading-server-instances"></a>Minimieren der Ausfallzeit von gespiegelten Datenbanken beim Aktualisieren von Serverinstanzen
  Beim Aktualisieren von Serverinstanzen auf [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], Sie können Downtime für jede gespiegelte Datenbank auf ein einzelnes Manuelles Failover reduzieren, indem Sie ein sequenzielles Upgrade ausführen, bekannt als eine *paralleles Upgrade*. Ein paralleles Upgrade bildet einen mehrstufigen Vorgang, bei dem im einfachsten Fall die gegenwärtig als Spiegelserver in einer Spiegelungssitzung verwendete Serverinstanz aktualisiert, dann ein manuelles Failover auf die gespiegelte Datenbank ausgeführt, der vorherige Prinzipalserver aktualisiert und die Spiegelung wiederaufgenommen wird. In der Praxis hängt der genaue Vorgang vom Beriebsmodus und der Anzahl und dem Layout der Spiegelungssitzung auf den zu aktualisierenden Serverinstanzen ab.  
  
> [!NOTE]  
>  Informationen zum Ausführen eines parallelen Upgrades, um ein Servicepack oder Hotfix zu installieren, finden Sie unter [installieren Sie ein Service Pack auf einem System mit minimaler Ausfallzeit für gespiegelte Datenbanken](../install-a-service-pack-on-a-system-with-minimal-downtime-for-mirrored-databases.md).  
  
 **Empfehlungen zur Vorbereitung (bewährte Methoden)**  
  
 Vor dem Start eines parallelen Upgrades sollten Sie Folgendes ausführen:  
  
1.  Führen Sie zu Übungszwecken ein manuelles Failover für mindestens eine der Spiegelungssitzungen aus:  
  
    -   [Manueller Failover für eine Datenbank-Spiegelungssitzung &#40;SQL Server Management Studio&#41;](manually-fail-over-a-database-mirroring-session-sql-server-management-studio.md)  
  
    -   [Manuelles Failover für eine Datenbank-Spiegelungssitzung &#40;Transact-SQL&#41;](manually-fail-over-a-database-mirroring-session-transact-sql.md).  
  
    > [!NOTE]  
    >  Informationen zum Verwalten des potenziellen Datenverlusts finden Sie unter [Rollenwechsel während einer Datenbank-Spiegelungssitzung &#40;SQL Server&#41;](role-switching-during-a-database-mirroring-session-sql-server.md).  
  
2.  Schützen Sie Ihre Daten:  
  
    1.  Führen Sie für jede Prinzipaldatenbank eine vollständige Datenbanksicherung aus:  
  
         [Erstellen einer vollständigen Datenbanksicherung &#40;SQL Server&#41;](../../relational-databases/backup-restore/create-a-full-database-backup-sql-server.md).  
  
    2.  Führen Sie den [DBCC CHECKDB](/sql/t-sql/database-console-commands/dbcc-checkdb-transact-sql)-Befehl für jede Prinzipaldatenbank aus.  
  
 **Phasen eines parallelen Upgrades**  
  
 Die einzelnen Schritte bei einem parallelen Upgrade hängen vom Betriebsmodus der Spiegelungskonfiguration ab. Die grundlegenden Phasen sind jedoch identisch.  
  
> [!NOTE]  
>  Weitere Informationen zu den Betriebsmodi finden Sie unter [Betriebsmodi der Datenbankspiegelung](database-mirroring-operating-modes.md).  
  
 Die folgende Abbildung zeigt ein Flussdiagramm mit den Grundstufen eines parallelen Upgrades für jeden Betriebsmodus. Die entsprechenden Prozeduren finden Sie nach der Abbildung.  
  
 ![Flussdiagramm mit den Schritten eines Upgrades](../media/dbm-rolling-upgrade.gif "Flowchart showing steps of a rolling upgrade")  
  
> [!IMPORTANT]  
>  Eine Serverinstanz kann bei gleichzeitigen Spiegelungssitzungen verschiedene Spiegelungsrollen (Prinzipalserver, Spiegelserver oder Zeuge) ausführen. In diesem Fall müssen Sie den grundlegenden Prozess für das parallele Upgrade entsprechend anpassen. Weitere Informationen finden Sie unter [Rollenwechsel während einer Datenbank-Spiegelungssitzung &#40;SQL Server&#41;](role-switching-during-a-database-mirroring-session-sql-server.md)herunter.  
  
### <a name="to-change-a-session-from-high-performance-mode-to-high-safety-mode"></a>So ändern Sie den Modus einer Sitzung vom Modus für hohe Leistung in den Modus für hohe Sicherheit  
  
1.  Ändern Sie den Betriebsmodus in den Modus für hohe Sicherheit ohne automatisches Failover, wenn sich eine Spiegelungssitzung vor der Ausführung eines parallelen Upgrades im Modus für hohe Leistung befindet.  
  
    > [!IMPORTANT]  
    >  Wenn der Spiegelserver vom Prinzipalserver geografisch entfernt ist, ist ein paralleles Upgrade möglicherweise nicht geeignet.  
  
    -   In [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]: Ändern Sie im Dialogfeld **Datenbankeigenschaften** auf der Seite **Spiegelung** die Option [Betriebsmodus](../../relational-databases/databases/database-properties-mirroring-page.md) in **Hohe Sicherheit ohne automatisches Failover (synchron)** . Informationen über den Zugriff auf diese Seite finden Sie unter [Starten des Assistenten zum Konfigurieren der Sicherheit für die Datenbankspiegelung &#40;SQL Server Management Studio&#41;](start-the-configuring-database-mirroring-security-wizard.md).  
  
    -   In [!INCLUDE[tsql](../../includes/tsql-md.md)]: Legen Sie die Transaktionssicherheit auf FULL fest. Weitere Informationen finden Sie unter [Ändern der Transaktionssicherheit in einer Datenbank-Spiegelungssitzung &#40;Transact-SQL&#41;](change-transaction-safety-in-a-database-mirroring-session-transact-sql.md).  
  
### <a name="to-remove-a-witness-from-a-session"></a>So entfernen Sie einen Zeugen aus einer Sitzung  
  
1.  Wenn ein Zeuge an einer Spiegelungssitzung beteiligt ist, sollte der Zeuge vor der Ausführung eines parallelen Upgrades entfernt werden. Andernfalls hängt die Datenbankverfügbarkeit beim Upgrade der Spiegelserverinstanz von dem Zeugen ab, der weiterhin mit der Prinzipalserverinstanz verbunden bleibt. Nachdem Sie den Zeugen entfernt haben, ist ein Upgrade jederzeit während des parallelen Upgrades ohne Gefahr eines Datenbankausfalls möglich.  
  
    > [!NOTE]  
    >  Weitere Informationen finden Sie unter [Quorum: Auswirkungen eines Zeugen auf die Datenbankverfügbarkeit &#40;Datenbankspiegelung&#41;](quorum-how-a-witness-affects-database-availability-database-mirroring.md).  
  
    -   [Entfernen des Zeugen aus einer Datenbank-Spiegelungssitzung &#40;SQL Server&#41;](remove-the-witness-from-a-database-mirroring-session-sql-server.md)  
  
### <a name="to-perform-the-rolling-upgrade"></a>So führen Sie das parallele Upgrade aus  
  
1.  Zur Minimierung der Ausfallzeit wird Folgendes empfohlen: Starten Sie das parallele Upgrade mit dem Aktualisieren aller Spiegelungspartner, die aktuell als Spiegelserver in allen Spiegelungssitzungen fungieren. Möglicherweise müssen an dieser Stelle mehrere Serverinstanzen aktualisiert werden.  
  
    > [!NOTE]  
    >  Ein Zeuge kann jederzeit während der Ausführung des parallelen Upgrades aktualisiert werden. Wenn beispielsweise eine Serverinstanz in Sitzung 1 als Spiegelserver und in Sitzung 2 als Zeuge fungiert, können Sie die Serverinstanz nun aktualisieren.  
  
     Welche Serverinstanz zuerst aktualisiert wird, hängt von der aktuellen Konfiguration der Spiegelungssitzungen ab, und zwar wie folgt:  
  
    -   Wenn eine Serverinstanz bereits als Spiegelserver in allen Spiegelungssitzungen fungiert, aktualisieren Sie die Serverinstanz auf die neue Version.  
  
    -   Wenn alle Serverinstanzen aktuell als Prinzipalserver in allen Spiegelungssitzungen fungieren, wählen Sie eine Serverinstanz aus, die zuerst aktualisiert werden soll. Führen Sie dann ein manuelles Failover für alle Prinzipaldatenbanken aus, und aktualisieren Sie die Serverinstanz.  
  
     Nach dem Upgrade schließt sich eine Serverinstanz automatisch wieder den zugehörigen Spiegelungssitzungen an.  
  
2.  Warten Sie bei jeder Spiegelungssitzung, deren Serverinstanz gerade aktualisiert wurde, ab, bis die Sitzung synchronisiert ist. Stellen Sie dann eine Verbindung mit der Prinzipalserverinstanz her, und führen Sie manuell ein Failover zur Sitzung aus. Beim Failover wird die aktualisierte Serverinstanz zum Prinzipalserver dieser Sitzung, und der frühere Prinzipalserver wird zum Spiegelserver.  
  
     Ziel dieses Schritts ist es, dass eine andere Serverinstanz zum Spiegelserver in jeder Spiegelungssitzung wird, an der sie als Partner beteiligt ist.  
  
     **Einschränkungen nach einem Failover zu einer aktualisierten Serverinstanz**  
  
     Nach dem Ausführen eines Failovers von einer früheren zu einer [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] -Serverinstanz wird die Datenbanksitzung angehalten. Sie kann erst dann fortgesetzt werden, wenn der andere Partner aktualisiert wurde. Der Prinzipalserver nimmt jedoch nach wie vor Verbindungen an und lässt den Datenzugriff auf die und Änderungen an der Prinzipaldatenbank zu.  
  
    > [!NOTE]  
    >  Damit eine neue Spiegelungssitzung eingerichtet werden kann, muss auf allen Serverinstanzen dieselbe Version von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]ausgeführt werden.  
  
3.  Nach dem Failover, es wird empfohlen, Sie führen die [DBCC CHECKDB](/sql/t-sql/database-console-commands/dbcc-checkdb-transact-sql) Befehl Theprincipal-Datenbank.  
  
4.  Aktualisieren Sie alle Serverinstanzen, die nun als Spiegelserver in allen Spiegelungssitzungen fungieren, in denen sie als Partner beteiligt sind. Möglicherweise müssen an dieser Stelle mehrere Server aktualisiert werden.  
  
    > [!IMPORTANT]  
    >  Es ist möglich, dass in einer komplexen Spiegelungskonfiguration manche Serverinstanz nach wie vor der ursprüngliche Prinzipalserver in mindestens einer Spiegelungssitzung ist. Wiederholen Sie die Schritte 2 bis 4 für diese Serverinstanzen, bis alle beteiligten Instanzen aktualisiert sind.  
  
5.  Setzen Sie die Spiegelungssitzung fort.  
  
    > [!NOTE]  
    >  Ein automatisches Failover ist erst möglich, wenn der Zeuge aktualisiert und der Spiegelungssitzung erneut hinzugefügt wurde.  
  
6.  Aktualisieren Sie die verbleibenden Serverinstanzen, die als Zeuge in allen zugehörigen Spiegelungssitzungen fungieren. Nachdem sich ein aktualisierter Zeuge wieder einer Spiegelungssitzung angeschlossen hat, ist das Ausführen eines automatischen Failovers wieder möglich. Möglicherweise müssen an dieser Stelle mehrere Server aktualisiert werden.  
  
### <a name="to-return-a-session-to-high-performance-mode"></a>So ändern Sie den Modus einer Sitzung wieder in den Modus für hohe Leistung  
  
1.  Sie haben die folgenden Möglichkeiten, um den Modus einer Sitzung wieder in den Modus für hohe Leistung zu ändern:  
  
    -   In [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]: Ändern Sie im Dialogfeld **Datenbankeigenschaften** auf der Seite **Spiegelung** die Option [Betriebsmodus](../../relational-databases/databases/database-properties-mirroring-page.md) in **Hohe Leistung (asynchron)** .  
  
    -   In [!INCLUDE[tsql](../../includes/tsql-md.md)]: Verwenden Sie [ALTER DATABASE](/sql/t-sql/statements/alter-database-transact-sql-database-mirroring), um die Transaktionssicherheit auf OFF festzulegen.  
  
### <a name="to-add-a-witness-back-into-a-mirroring-session"></a>So fügen Sie einen Zeugen einer Spiegelungssitzung erneut hinzu  
  
1.  Im Modus für hohe Sicherheit können Sie den Zeugen in jeder Spiegelungssitzung wiederherstellen.  
  
     **So fügen Sie einen Zeugen wieder hinzu**  
  
    -   [Hinzufügen oder Ersetzen eines Datenbank-Spiegelungszeugen &#40;SQL Server Management Studio&#41;](add-or-replace-a-database-mirroring-witness-sql-server-management-studio.md)  
  
    -   [Hinzufügen eines Zeugen für die Datenbankspiegelung mithilfe der Windows-Authentifizierung &#40;Transact-SQL&#41;](add-a-database-mirroring-witness-using-windows-authentication-transact-sql.md)  
  
## <a name="see-also"></a>Siehe auch  
 [ALTER DATABASE-Datenbankspiegelung &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql-database-mirroring)   
 [BACKUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-transact-sql)   
 [Anzeigen des Status einer gespiegelten Datenbank (SQL Server Management Studio)](view-the-state-of-a-mirrored-database-sql-server-management-studio.md)   
 [Datenbankspiegelung &#40;SQL Server&#41;](database-mirroring-sql-server.md)   
 [Installieren Sie ein Servicepack auf einem System mit minimaler Ausfallzeit von gespiegelten Datenbanken](../install-a-service-pack-on-a-system-with-minimal-downtime-for-mirrored-databases.md)   
 [Rollenwechsel während einer Datenbank-Spiegelungssitzung &#40;SQL Server&#41;](role-switching-during-a-database-mirroring-session-sql-server.md)   
 [Erzwingen des Diensts in einer Datenbank-Spiegelungssitzung (Transact-SQL)](force-service-in-a-database-mirroring-session-transact-sql.md)   
 [Starten des Datenbankspiegelungs-Monitors &#40;SQL Server Management Studio&#41;](start-database-mirroring-monitor-sql-server-management-studio.md)   
 [Database Mirroring Operating Modes](database-mirroring-operating-modes.md)  
  
  
