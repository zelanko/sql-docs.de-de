---
title: Sicherung und-Wiederherstellung – Parallel Data Warehouse | Microsoft-Dokumentation
description: Beschreibt, wie Sie Daten zum Sichern und Wiederherstellen für Parallel Data Warehouse (PDW). Sicherungs-und Wiederherstellungsvorgänge werden für die notfallwiederherstellung verwendet. Sicherung und Wiederherstellung können auch zum Kopieren einer Datenbank von einer Appliance in einer anderen Anwendung verwendet werden.
author: mzaman1
manager: craigg
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 01/19/2019
ms.author: murshedz
ms.reviewer: martinle
ms.openlocfilehash: 0b95d18eb38bbe0012235304747ca80b3dc19a79
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "63200955"
---
# <a name="backup-and-restore"></a>Sichern und Wiederherstellen

Beschreibt, wie Sie Daten zum Sichern und Wiederherstellen für Parallel Data Warehouse (PDW). Sicherungs-und Wiederherstellungsvorgänge werden für die notfallwiederherstellung verwendet. Sicherung und Wiederherstellung können auch zum Kopieren einer Datenbank von einer Appliance in einer anderen Anwendung verwendet werden.  
    
## <a name="BackupRestoreBasics"></a>Grundlagen der sicherungs- und Wiederherstellungsvorgänge

Ein PDW *datenbanksicherung* ist eine Kopie einer Anwendungsdatenbank, in einem Format gespeichert werden, sodass sie zum Wiederherstellen der ursprünglichen Datenbank in einer Anwendung verwendet werden kann.  
  
Eine Sicherung der PDW-Datenbank wird erstellt, mit der [BACKUP DATABASE](../t-sql/statements/backup-database-parallel-data-warehouse.md) t-Sql-Anweisung und formatierte für die Verwendung mit der [RESTORE DATABASE](../t-sql/statements/restore-database-parallel-data-warehouse.md) -Anweisung; Es kann nicht verwendet werden, für andere Zwecke. Die Sicherung kann nur auf einer Appliance mit der gleichen Anzahl oder eine größere Anzahl von Compute-Knoten wiederhergestellt werden.  
  
<!-- MISSING LINKS
The [master database](master-database.md) is a SMP SQL Server database. It is backed up with the BACKUP DATABASE statement. To restore master, use the [Restore the Master Database](configuration-manager-restore-master-database.md) page of the Configuration Manager tool.  
-->
  
PDW verwendet SQL Server-sicherungs-Technologie, um die Appliance Datenbanken sichern und wiederherstellen. SQL Server--Sicherungsoptionen sind vorkonfiguriert, um die sicherungskomprimierung zu verwenden. Sie können keine Sicherungsoptionen wie Komprimierung, Prüfsumme, Blockgröße und Pufferanzahl festlegen.  
  
Datenbanksicherungen werden auf einem oder mehreren Servern sichern, gespeichert, die im eigenen Kundennetzwerk vorhanden sind.  PDW schreibt eine Benutzerdatenbank-Sicherung direkt von den Computeknoten parallel auf einem Sicherungsserver und stellt eine Benutzerdatenbank-Sicherung parallel direkt aus dem backup-Server auf den Computeknoten.  
  
Sicherungen werden auf dem Sicherungsserver als einen Satz von Dateien im Windows-Dateisystem gespeichert. Eine vollständige datenbanksicherung von PDW kann nur mit PDW wiederhergestellt werden. Allerdings können Sie die datenbanksicherungen vom backup-Server an einen anderen Speicherort mithilfe von Standardprozessen für die Sicherung von Windows-Datei archivieren. Weitere Informationen zu backup-Server, finden Sie unter [abrufen und die Konfiguration eines Sicherungsservers](acquire-and-configure-backup-server.md).  
  
## <a name="BackupTypes"></a>Datenbank-Sicherungstypen

Es gibt zwei Arten von Daten, die eine Sicherung erfordern: Benutzerdatenbanken und Systemdatenbanken (z. B. der master-Datenbank). PDW das Transaktionsprotokoll nicht gesichert.  
  
Eine vollständige datenbanksicherung ist eine Sicherung einer gesamten PDW-Datenbank. Dies ist der backup-Standardtyp. Eine vollständige Sicherung einer Benutzerdatenbank schließt Datenbankbenutzer und Datenbankrollen. Eine Sicherung der Master enthält Anmeldungen.  
  
Eine differenzielle Sicherung enthält alle Änderungen seit der letzten vollständigen Sicherung. Eine differenzielle Sicherung nimmt normalerweise weniger Zeit in Anspruch als eine vollständige Sicherung und kann häufiger ausgeführt werden. Wenn mehrere differenzielle Sicherungen auf der gleichen vollständigen Sicherung basieren, enthält jede differenzielle Sicherung alle Änderungen in der vorherigen differenziellen an.  
  
Beispielsweise könnten Sie eine vollständige Sicherung wöchentlich und täglich eine differenzielle Sicherung erstellen. Zum Wiederherstellen der Datenbank, die vollständige Sicherung sowie die letzte muss (falls vorhanden) differenziellen Sicherung wiederhergestellt werden.  
  
Eine differenzielle Sicherung wird nur für Benutzerdatenbanken unterstützt. Eine Sicherung des Masters ist immer eine vollständige Sicherung.  
  
Um das gesamte Gerät zu sichern, müssen Sie eine Sicherung aller Benutzerdatenbanken und eine Sicherung der master-Datenbank ausführen.  
  
## <a name="BackupProc"></a>Sicherungsvorgang der Datenbank

Das folgende Diagramm zeigt den Fluss der Daten während einer datenbanksicherung.  
  
![PDW-Sicherungsverfahren](media/backup-process.png "PDW-Sicherungsverfahren")  
  
Der Sicherungsvorgang funktioniert wie folgt aus:  
  
1.  Benutzer übermittelt eine BACKUP DATABASE-Tsql-Anweisung mit dem Steuerungsknoten.  
  
    -   Die Sicherung ist eine vollständige oder differenzielle Sicherung.  
  
2.  Für die Benutzerdatenbanken erstellt der Steuerelementknoten aus (MPP-Engine) einen verteilte Abfrage-Plan zum Ausführen einer parallelen Datenbank-Sicherung.  
  
3.  Jeder Knoten die Sicherungskopien der Sicherungsdatei aus, den backup-Server mit SQL Server-sicherungs-Funktionalität beteiligt ist.  
  
    -   Jeder Knoten bei der eine Sicherungsdatei zum Sicherungsserver kopiert.  
  
    -   Benutzer, um die datenbanksicherung (vollständige oder differenzielle Sicherung) umfasst, eine Sicherung des Teils der Datenbank auf jeder Compute-Knoten, und eine Sicherung der Datenbankbenutzer und Datenbankrollen gespeichert wird.  
  
4.  Das Gerät führt die Sicherung parallel mit dem InfiniBand-Netzwerk.  
  
    -   PDW führt jede vollständige und differenzielle Sicherung parallel. Allerdings werden mehrere datenbanksicherungen nicht gleichzeitig ausgeführt werden. Jede Sicherung Anforderung muss zuvor gesendeten Sicherungen abgeschlossen warten.  
  
    -   Eine Sicherung der master-Datenbank sichert Daten nur aus den Steuerelementknoten aus. Dieser Sicherungstyp wird seriell ausgeführt.  
  
5.  Eine vollständige datenbanksicherung von PDW ist eine Gruppe von Dateien in ein Verzeichnis an, die sich nicht auf dem Gerät befindet. Der Name des Verzeichnisses wird als ein Netzwerkname Pfad und das Verzeichnis angegeben. Das Verzeichnis kann kein lokaler Pfad sein, und er darf nicht auf dem Gerät sein.  
  
6.  Nach Abschluss die Sicherung können im Windows-Dateisystem Sie das Sicherungsverzeichnis an einen anderen Speicherort kopiert bei Bedarf.  
  
    -   Eine Sicherung kann nur auf eine PDW-Appliance wiederhergestellt werden, die eine Anzahl größere oder gleich der Compute-Knoten enthält.  
  
    -   Sie können nicht den Namen der Sicherung ändern, vor dem Ausführen einer Wiederherstellung. Der Name für das Sicherungsverzeichnis muss es sich um den Namen der den ursprünglichen Namen der Sicherung übereinstimmen. Der ursprüngliche Name der die Sicherung befindet sich in der Datei "Backup.xml" in das Sicherungsverzeichnis. Um eine Datenbank auf einen anderen Namen wiederherstellen möchten, können Sie den neuen Namen in der Restore-Befehl angeben. Beispiel: `RESTORE DATABASE MyDB1 FROM DISK = ꞌ\\10.192.10.10\backups\MyDB2ꞌ`.  
  
## <a name="RestoreModes"></a>Datenbank wiederherstellen-Modi

Eine vollständige datenbankwiederherstellung erstellt die PDW-Datenbank mithilfe der Daten in der datenbanksicherung neu. Die Wiederherstellung der Datenbank erfolgt über eine vollständige Sicherung zuerst wiederhergestellt und anschließend optional eine differenzielle Sicherung wiederherstellen. Die Wiederherstellung der Datenbank enthält die Datenbankbenutzer und Datenbankrollen.  
  
Wiederherstellung nur Header gibt die Headerinformationen für eine Datenbank zurück. Es werden keine Daten an das Gerät wiederhergestellt.  
  
Eine Wiederherstellung der Appliance ist eine Wiederherstellung der gesamten Appliance. Dies umfasst die Wiederherstellung alle Benutzerdatenbanken und der master-Datenbank.  
  
## <a name="RestoreProc"></a>Wiederherstellungsprozess

Das folgende Diagramm zeigt den Fluss der Daten während einer Wiederherstellung der Datenbank.  
  
![Wiederherstellungsprozess](media/restore-process.png "Wiederherstellungsprozess")  
  
## <a name="restoring-to-an-appliance-with-the-same-number-of-compute-nodes"></a>Wiederherstellen auf einer Appliance mit der gleichen Anzahl von Compute-Knoten **  
  
Beim Wiederherstellen von Daten erkennt die Appliance die Anzahl der Compute-Knoten, auf die quellappliance "und" die zielappliance an. Wenn beide Einheiten eine gleiche Anzahl von Compute-Knoten verfügen, funktioniert der Wiederherstellungsvorgang wird wie folgt:  
  
1.  Die datenbanksicherung wiederhergestellt werden, ist verfügbar, in einer Windows-Dateifreigabe auf einem Sicherungsserver nicht zur Appliance gehört. Für eine optimale Leistung wird dieser Server mit der Appliance InfiniBand-Netzwerk verbunden.  
  
2.  Benutzer übermittelt eine [RESTORE DATABASE](../t-sql/statements/restore-database-parallel-data-warehouse.md) Tsql-Anweisung, um den Steuerelementknoten aus.  
  
    -   Die Wiederherstellung ist eine vollständige Wiederherstellung oder eine Header-Wiederherstellung. Die vollständige Wiederherstellung eine vollständige Sicherung wiederhergestellt und anschließend optional eine differenzielle Sicherung wiederhergestellt.  
  
3.  Der steuerknoten (MPP-Engine) erstellt einen verteilte Abfrage-Plan zum Ausführen einer parallelen Datenbank-Wiederherstellung.  
  
    -   SQL-ServerPDW führt die Wiederherstellung einer Benutzerdatenbank parallel. Allerdings werden mehrere datenbanksicherungen und Wiederherstellungen nicht gleichzeitig ausgeführt werden. Die MPP-Engine fügt jede Restore-Anweisung in eine Warteschlange; Sie müssen warten, für die zuvor gesendeten Sicherung und Wiederherstellen von Anforderungen, um den Vorgang abzuschließen.  
  
    -   Eine Wiederherstellung der master-Datenbank wird nur die Daten an den Steuerungsknoten wiederhergestellt. die Wiederherstellung wird seriell ausgeführt.  
  
    -   Eine Wiederherstellung der Headerinformationen ist ein schneller Vorgang und alle Daten zu den COMPUTE- oder Control-Knoten nicht wiederhergestellt. Stattdessen gibt der steuerknoten die Ergebnisse als Ausgabe der Abfrage zurück.  
  
4.  Die Sicherungsdateien erhalten über das Gerät InfiniBand-Netzwerk in der Regel auf den richtigen Compute-Knoten parallel kopiert.  
  
5.  Jeder Compute-Knoten stellt wieder her, die Teil der Benutzerdatenbank. Wenn keines der Wiederherstellung nicht erfolgreich abgeschlossen werden, alle Datenbanken entfernt, und die Wiederherstellung abgeschlossen werden konnte.  
  
## <a name="restoring-to-an-appliance-with-a-larger-number-of-compute-nodes"></a>Wiederherstellen auf einer Appliance mit einer größeren Anzahl von Computeknoten  
  
Beim Wiederherstellen einer Sicherung auf einer Appliance mit einer größeren Anzahl von Computeknoten wächst die Größe der zugeordneten Datenbank entsprechend der Anzahl der Computeknoten.  
  
Beispielsweise erstellt, wenn eine 60-GB-Datenbank von einer 2-Knoten-Einheit (30 GB pro Knoten) in einer Anwendung 6 Knoten wiederherstellen zu können, SQL Server PDW eine 180-GB-Datenbank (6 Knoten mit 30 GB pro Knoten) auf dem Gerät 6 Knoten. SQL Server PDW wird zunächst die Datenbank auf 2 Knoten entsprechend die Quellkonfiguration und verteilt Sie anschließend die Daten auf alle 6 Knoten.  
  
Nach der Umverteilung enthält jeder Computeknoten weniger tatsächliche Daten und mehr freien Speicher als einzelnen Computeknoten auf der kleineren quellappliance. Dank des zusätzlichen Speicherplatzes können Sie der Datenbank weitere Daten hinzufügen. Wenn die wiederhergestellte Datenbank größer ist, als Sie benötigen, können Sie [ALTER DATABASE](../t-sql/statements/alter-database-transact-sql.md?tabs=sqlpdw) zum Verkleinern der Größe der Datenbank.  
  
## <a name="related-tasks"></a>Related Tasks  
  
|Backup- und Restore-Aufgabe|Description|  
|---------------------------|---------------|  
|Bereiten Sie einen Server als Sicherungsserver.|[Erwerb und Konfiguration eines Sicherungsservers](acquire-and-configure-backup-server.md)|  
|Sichern einer Datenbank.|[DATENBANK SICHERN](../t-sql/statements/backup-database-parallel-data-warehouse.md)|  
|Wiederherstellen einer Datenbank.|[RESTORE DATABASE](../t-sql/statements/restore-database-parallel-data-warehouse.md)|    

<!-- MISSING LINKS

|Create a disaster recovery plan.|[Create a Disaster Recovery Plan](create-disaster-recovery-plan.md)|
|Restore the master database.|To restore the master database, use the [Restore the master database](configuration-manager-restore-master-database.md) page in the Configuration Manager tool.| 
|Copy a database from one appliance to another appliance.|[Copy a PDW database to another appliance](copy-pdw-database-to-another-appliance.md).|  
|Monitor backups and restores.|[Monitor backups and restores](monitor-backup-and-restore.md)|  

-->
